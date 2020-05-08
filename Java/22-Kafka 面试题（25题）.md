![](https://gitee.com/duchaochen/pythonnote/raw/master/img/面试题题封面-new.png)



# Kafka 面试题

### 1、Kafka 是什么  

Kafka 是一种高吞吐量、分布式、基于发布/订阅的消息系统，最初由 LinkedIn 公司开发，使用Scala 语言编写，目前是 Apache 的开源项目。

1. broker： Kafka 服务器，负责消息存储和转发
2. topic：消息类别， Kafka 按照 topic 来分类消息
3. partition： topic 的分区，一个 topic 可以包含多个 partition， topic 消息保存在各个partition 上
4. offset：消息在日志中的位置，可以理解是消息在 partition 上的偏移量，也是代表该消息的唯一序号
5. Producer：消息生产者
6. Consumer：消息消费者
7. Consumer Group：消费者分组，每个 Consumer 必须属于一个 group
8. Zookeeper：保存着集群 broker、 topic、 partition 等 meta 数据；另外，还负责 broker 故障发现， partition leader 选举，负载均衡等功能

![](https://gitee.com/duchaochen/pythonnote/raw/master/img/20200411/2-32.png)

### 2、partition 的数据文件（offset， MessageSize， data）  

partition 中的每条 Message 包含了以下三个属性： offset， MessageSize， data， 其中 offset 表示 Message 在这个 partition 中的偏移量， offset 不是该 Message 在 partition 数据文件中的实际存储位置，而是逻辑上一个值，它唯一确定了 partition 中的一条 Message，可以认为 offset 是partition 中 Message 的 id； MessageSize 表示消息内容 data 的大小； data 为 Message 的具体内容。   



### 3、数据文件分段 segment（顺序读写、分段命令、二分查找）  

Kafka 为每个分段后的数据文件建立了索引文件，文件名与数据文件的名字是一样的，只是文件扩展名为.index。 index 文件中并没有为数据文件中的每条 Message 建立索引，而是采用了稀疏存储的方式，每隔一定字节的数据建立一条索引。这样避免了索引文件占用过多的空间，从而可以将索引文件保留在内存中。   

![](https://gitee.com/duchaochen/pythonnote/raw/master/img/20200411/3-1.png)

### 4、负载均衡（partition 会均衡分布到不同 broker 上）  

由于消息 topic 由多个 partition 组成， 且 partition 会均衡分布到不同 broker 上，因此，为了有效利用 broker 集群的性能，提高消息的吞吐量， producer 可以通过随机或者 hash 等方式，将消息平均发送到多个 partition 上，以实现负载均衡。  

![](https://gitee.com/duchaochen/pythonnote/raw/master/img/20200411/3-2.png)



### 5、批量发送  

是提高消息吞吐量重要的方式， Producer 端可以在内存中合并多条消息后， 以一次请求的方式发送了批量的消息给 broker，从而大大减少 broker 存储消息的 IO 操作次数。但也一定程度上影响了消息的实时性，相当于以时延代价，换取更好的吞吐量。  



### 6、压缩（GZIP 或 Snappy）  

Producer 端可以通过 GZIP 或 Snappy 格式对消息集合进行压缩。 Producer 端进行压缩之后，在Consumer 端需进行解压。压缩的好处就是减少传输的数据量，减轻对网络传输的压力，在对大数据处理上，瓶颈往往体现在网络上而不是 CPU（压缩和解压会耗掉部分 CPU 资源）。  



### 7、消费者设计  

![](https://gitee.com/duchaochen/pythonnote/raw/master/img/20200411/3-3.png)



### 8、Consumer Group  

同一 Consumer Group 中的多个 Consumer 实例，不同时消费同一个 partition，等效于队列模式。 partition 内消息是有序的， Consumer 通过 pull 方式消费消息。 Kafka 不删除已消费的消息对于 partition，顺序读写磁盘数据，以时间复杂度 O(1)方式提供消息持久化能力。  



### 9、如何获取 topic 主题的列表  

bin/kafka-topics.sh --list --zookeeper localhost:2181  



### 10、生产者和消费者的命令行是什么？  

生产者在主题上发布消息：

```shell
bin/kafka-console-producer.sh --broker-list 192.168.43.49:9092 --topic
Hello-Kafa
```

注意这里的 IP 是 server.properties 中的 listeners 的配置。接下来每个新行就是输入一条新消息。
消费者接受消息：

```shell
bin/kafka-console-consumer.sh --zookeeper localhost:2181 --topic
Hello-Kafka --from-beginning
```



### 11、consumer 是推还是拉？

Kafka 最初考虑的问题是，customer 应该从 brokes 拉取消息还是 brokers 将消息推送到 consumer，也就是 pull 还 push。在这方面，Kafka 遵循了一种大部分消息系统共同的传统的设计：producer 将消息推送到 broker，consumer 从broker 拉取消息。

一些消息系统比如 Scribe 和 Apache Flume 采用了 push 模式，将消息推送到下游的 consumer。这样做有好处也有坏处：由 broker 决定消息推送的速率，对于不同消费速率的 consumer 就不太好处理了。消息系统都致力于让 consumer 以最大的速率最快速的消费消息，但不幸的是，push 模式下，当 broker 推送的速率远大于 consumer 消费的速率时，consumer 恐怕就要崩溃了。最终 Kafka 还是选取了传统的 pull 模式。  

Pull 模式的另外一个好处是 consumer 可以自主决定是否批量的从 broker 拉取数据。Push 模式必须在不知道下游 consumer 消费能力和消费策略的情况下决定是立即推送每条消息还是缓存之后批量推送。如果为了避免 consumer 崩溃而采用较低的推送速率，将可能导致一次只推送较少的消息而造成浪费。Pull 模式下，
consumer 就可以根据自己的消费能力去决定这些策略。

Pull 有个缺点是，如果 broker 没有可供消费的消息，将导致 consumer 不断在循环中轮询，直到新消息到 t 达。为了避免这点，Kafka 有个参数可以让 consumer阻塞知道新消息到达(当然也可以阻塞知道消息的数量达到某个特定的量这样就可以批量发送)。  



### 12、讲讲 kafka 维护消费状态跟踪的方法  

大部分消息系统在 broker 端的维护消息被消费的记录：一个消息被分发到consumer 后 broker 就马上进行标记或者等待 customer 的通知后进行标记。这样也可以在消息在消费后立马就删除以减少空间占用。

但是这样会不会有什么问题呢？如果一条消息发送出去之后就立即被标记为消费过的，一旦 consumer 处理消息时失败了（比如程序崩溃）消息就丢失了。为了解决这个问题，很多消息系统提供了另外一个个功能：当消息被发送出去之后仅仅被标记为已发送状态，当接到 consumer 已经消费成功的通知后才标记为已被消费的状态。这虽然解决了消息丢失的问题，但产生了新问题，首先如果 consumer处理消息成功了但是向 broker 发送响应时失败了，这条消息将被消费两次。第二个问题时，broker 必须维护每条消息的状态，并且每次都要先锁住消息然后更改状态然后释放锁。这样麻烦又来了，且不说要维护大量的状态数据，比如如果消息发送出去但没有收到消费成功的通知，这条消息将一直处于被锁定的状态，Kafka 采用了不同的策略。Topic 被分成了若干分区，每个分区在同一时间只被一个 consumer 消费。这意味着每个分区被消费的消息在日志中的位置仅仅是一个简单的整数：offset。这样就很容易标记每个分区消费状态就很容易了，仅仅需要一个整数而已。这样消费状态的跟踪就很简单了。这带来了另外一个好处：consumer 可以把 offset 调成一个较老的值，去重新消费老的消息。这对传统的消息系统来说看起来有些不可思议，但确实是非常有用的，谁规定了一条消息只能被消费一次呢？  



### 13、讲一下主从同步

https://blog.csdn.net/honglei915/article/details/37565289



### 14、为什么需要消息系统，mysql 不能满足需求吗？

**1.解耦：**
允许你独立的扩展或修改两边的处理过程，只要确保它们遵守同样的接口约束。

**2.冗余：**
消息队列把数据进行持久化直到它们已经被完全处理，通过这一方式规避了数据丢失风险。许多消息队列所采用的”插入-获取-删除”范式中，在把一个消息从队列中删除之前，需要你的处理系统明确的指出该消息已经被处理完毕，从而确保你的数据被安全的保存直到你使用完毕。

**3.扩展性：**
因为消息队列解耦了你的处理过程，所以增大消息入队和处理的频率是很容易的，只要另外增加处理过程即可。    

**4.灵活性 & 峰值处理能力：** 

在访问量剧增的情况下，应用仍然需要继续发挥作用，但是这样的突发流量并不常见。如果为以能处理这类峰值访问为标准来投入资源随时待命无疑是巨大的浪费。使用消息队列能够使关键组件顶住突发的访问压力，而不会因为突发的超负荷的请求而完全崩溃。

**5.可恢复性：**
系统的一部分组件失效时，不会影响到整个系统。消息队列降低了进程间的耦合度，所以即使一个处理消息的进程挂掉，加入队列中的消息仍然可以在系统恢复后被处理。

**6.顺序保证：**
在大多使用场景下，数据处理的顺序都很重要。大部分消息队列本来就是排序的，并且能保证数据会按照特定的顺序来处理。（Kafka 保证一个 Partition 内的消息的有序性）

**7.缓冲：**
有助于控制和优化数据流经过系统的速度，解决生产消息和消费消息的处理速度不一致的情况。

**8.异步通信：**
很多时候，用户不想也不需要立即处理消息。消息队列提供了异步处理机制，允许用户把一个消息放入队列，但并不立即处理它。想向队列中放入多少消息就放多少，然后在需要的时候再去处理它们。   



### 15、Zookeeper 对于 Kafka 的作用是什么？  

Zookeeper 是一个开放源码的、高性能的协调服务，它用于 Kafka 的分布式应用。Zookeeper 主要用于在集群中不同节点之间进行通信

在 Kafka 中，它被用于提交偏移量，因此如果节点在任何情况下都失败了，它都可以从之前提交的偏移量中获取
除此之外，它还执行其他活动，如: leader 检测、分布式同步、配置管理、识别新节点何时离开或连接、集群、节点实时状态等等。  

16、数据传输的事务定义有哪三种？
和 MQTT 的事务定义一样都是 3 种。
（1）最多一次: 消息不会被重复发送，最多被传输一次，但也有可能一次不传输
（2）最少一次: 消息不会被漏发送，最少被传输一次，但也有可能被重复传输.
（3）精确的一次（Exactly once）: 不会漏传输也不会重复传输,每个消息都传输被一次而且仅仅被传输一次，这是大家所期望的  



### 16、Kafka 判断一个节点是否还活着有那两个条件？

（1）节点必须可以维护和 ZooKeeper 的连接，Zookeeper 通过心跳机制检查每个节点的连接
（2）如果节点是个 follower,他必须能及时的同步 leader 的写操作，延时不能太久  



### 17、Kafka 与传统 MQ 消息系统之间有三个关键区别

(1).Kafka 持久化日志，这些日志可以被重复读取和无限期保留
(2).Kafka 是一个分布式系统：它以集群的方式运行，可以灵活伸缩，在内部通过复制数据提升容错能力和高可用性
(3).Kafka 支持实时的流式处理  



### 18、讲一讲 kafka 的 ack 的三种机制

request.required.acks 有三个值 0 1 -1(all)
0:生产者不会等待 broker 的 ack，这个延迟最低但是存储的保证最弱当 server 挂掉的时候就会丢数据。
1：服务端会等待 ack 值 leader 副本确认接收到消息后发送 ack 但是如果 leader挂掉后他不确保是否复制完成新 leader 也会导致数据丢失。
-1(all)：服务端会等所有的 follower 的副本受到数据后才会受到 leader 发出的ack，这样数据不会丢失  



### 19、消费者如何不自动提交偏移量，由应用提交？

将 auto.commit.offset 设为 false，然后在处理一批消息后 commitSync() 或者异步提交 commitAsync()
即：  

```java
ConsumerRecords<> records = consumer.poll();
for (ConsumerRecord<> record : records){
。。。
tyr{
consumer.commitSync()
} 。
。。
}
```

### 20、消费者故障，出现活锁问题如何解决？  

出现 “活锁 ” 的情 况， 是它 持续 的发 送心 跳， 但是 没有 处理 。为 了预 防消 费者 在这种 情况 下一 直持 有分 区，我们 使用 max.poll.interval.ms 活跃 检测 机制 。 在此基础 上， 如果 你调 用的 poll 的频 率大 于最 大间 隔， 则客 户端 将主 动地 离开 组， 以便其 他消 费者 接管 该分 区。 发生 这种 情况 时， 你会 看到 offset 提交 失败 （调 用commitSync（） 引发 的 CommitFailedException）。 这是 一种 安全 机制 ，保 障只有 活动 成员 能够 提交 offset。所 以要 留在 组中 ，你 必须 持续 调用 poll。  

消费者提供两个配置设置来控制 poll 循环：
max.poll.interval.ms：增大 poll 的间 隔 ，可以 为消 费者 提供 更多 的时 间去 处理 返回的 消息（调用 poll(long)返回 的消 息，通常 返回 的消 息都 是一 批）。缺点 是此 值越大 将会 延迟 组重 新平 衡。

max.poll.records：此 设置 限制 每次 调用 poll 返回 的消 息数 ，这 样可 以更 容易 的预测 每次 poll 间隔 要处 理的 最大 值。通过 调整 此值 ，可以 减少 poll 间隔 ，减少 重新平 衡分 组的



对于 消息 处理 时间 不可 预测 地的 情况 ，这些 选项 是不 够的 。 处理 这种 情况 的推 荐方法 是将 消息 处理 移到 另一 个线 程中 ，让消 费者 继续 调用 poll。 但是 必须 注意 确保已 提交 的 offset 不超 过实 际位 置。 另外 ，你 必须 禁用 自动 提交 ，并 只有 在线 程完成 处理 后才 为记 录手 动提 交偏 移量（取决 于你 ）。 还要 注意 ，你需 要 pause 暂停分 区， 不会 从 poll 接收 到新 消息 ，让 线程 处理 完之 前返 回的 消息 （如 果你 的处理能 力比 拉取 消息 的慢 ，那 创建 新线 程将 导致 你机 器内 存溢 出） 。  



### 21、如何控制消费的位置

kafka 使用 seek(TopicPartition, long)指定新的消费位置。用于查找服务器保留的最早和最新的 offset 的特殊的方法也可用（seekToBeginning(Collection) 和seekToEnd(Collection)）  



### 22、kafka 分布式（不是单机）的情况下，如何保证消息的顺序消费?

Kafka 分布式的单位是 partition，同一个 partition 用一个 write ahead log 组织，所以可以保证 FIFO 的顺序。不同 partition 之间不能保证顺序。但是绝大多数用户都可以通过 message key 来定义，因为同一个 key 的 Message 可以保证只发送到同一个 partition。

Kafka 中发送 1 条消息的时候，可以指定(topic, partition, key) 3 个参数。partiton 和 key 是可选的。如果你指定了 partition，那就是所有消息发往同 1个 partition，就是有序的。并且在消费端，Kafka 保证，1 个 partition 只能被1 个 consumer 消费。或者你指定 key（比如 order id），具有同 1 个 key 的所有消息，会发往同 1 个 partition。  



### 23、kafka 的高可用机制是什么？  

这个问题比较系统，回答出 kafka 的系统特点，leader 和 follower 的关系，消息读写的顺序即可。
https://www.cnblogs.com/qingyunzong/p/9004703.html  

https://www.tuicool.com/articles/BNRza2E
https://yq.aliyun.com/articles/64703  



### 24、kafka 如何减少数据丢失  

https://www.cnblogs.com/huxi2b/p/6056364.html  



### 25、kafka 如何不消费重复数据？比如扣款，我们不能重复的扣。  

其实还是得结合业务来思考，我这里给几个思路：
比如你拿个数据要写库，你先根据主键查一下，如果这数据都有了，你就别插入了，update 一下好吧。

比如你是写 Redis，那没问题了，反正每次都是 set，天然幂等性。
比如你不是上面两个场景，那做的稍微复杂一点，你需要让生产者发送每条数据的时候，里面加一个全局唯一的 id，类似订单 id 之类的东西，然后你这里消费到了之后，先根据这个 id 去比如 Redis 里查一下，之前消费过吗？如果没有消费过，你就处理，然后这个 id 写 Redis。如果消费过了，那你就别处理了，保证别重复处理相同的消息即可。

比如基于数据库的唯一键来保证重复数据不会重复插入多条。因为有唯一键约束了，重复数据插入只会报错，不会导致数据库中出现脏数据  



![](https://gitee.com/duchaochen/pythonnote/raw/master/img/面试题题封面-new.png)

