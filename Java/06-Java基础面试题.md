![img](https://gitee.com/duchaochen/pythonnote/raw/master/img/%E9%9D%A2%E8%AF%95%E9%A2%98%E9%A2%98%E5%B0%81%E9%9D%A2-new.png)



# Java反射面试题

### 1、除了使用new创建对象之外，还可以用什么方法创建对象？

使用Java反射可以创建对象!



### 2、Java反射创建对象效率高还是通过new创建对象的效率高？

通过new创建对象的效率比较高。通过反射时，先找查找类资源，使用类加载器创建，过程比较繁琐，所以效率较低



### 3、java反射的作用

反射机制是在运行时，对于任意一个类，都能够知道这个类的所有属性和方法；对于任意个对象，都能够调用它的任意一个方法。在java中，只要给定类的名字，就可以通过反射机制来获得类的所有信息。

> 这种动态获取的信息以及动态调用对象的方法的功能称为Java语言的反射机制。



### 4、哪里会用到反射机制？

jdbc就是典型的反射

```
Class.forName('com.mysql.jdbc.Driver.class');//加载MySQL的驱动类
```

这就是反射。如hibernate，struts等框架使用反射实现的。



### 5、反射的实现方式：

第一步：获取Class对象，有4中方法：

1）Class.forName(“类的路径”)； 

2）类名.class

3）对象名.getClass()

4）基本类型的包装类，可以调用包装类的Type属性来获得该包装类的Class对象



### 6、实现Java反射的类：

1）Class：表示正在运行的Java应用程序中的类和接口

注意： 所有获取对象的信息都需要Class类来实现。

2）Field：提供有关类和接口的属性信息，以及对它的动态访问权限。

3）Constructor：提供关于类的单个构造方法的信息以及它的访问权限

4）Method：提供类或接口中某个方法的信息



### 7、反射机制的优缺点：

**优点：**

1）能够运行时动态获取类的实例，提高灵活性；

2）与动态编译结合

**缺点：**

1）使用反射性能较低，需要解析字节码，将内存中的对象进行解析。

解决方案：

1、通过setAccessible(true)关闭JDK的安全检查来提升反射速度；

2、多次创建一个类的实例时，有缓存会快很多

3、ReflflectASM工具类，通过字节码生成的方式加快反射速度

2）相对不安全，破坏了封装性（因为通过反射可以获得私有方法和属性）



### 8、Java 反射 API

**反射** **API** **用来生成** **JVM** **中的类、接口或则对象的信息。**

1. Class 类：反射的核心类，可以获取类的属性，方法等信息。
2. Field 类：Java.lang.reflec 包中的类，表示类的成员变量，可以用来获取和设置类之中的属性

值。

1. Method 类： Java.lang.reflec 包中的类，表示类的方法，它可以用来获取类中的方法信息或

者执行方法。

1. Constructor 类： Java.lang.reflec 包中的类，表示类的构造方法。



### 9、**反射使用步骤（获取 Class 对象、调用对象方法）**

1. 获取想要操作的类的 Class 对象，他是反射的核心，通过 Class 对象我们可以任意调用类的方法。
2. 调用 Class 类中的方法，既就是反射的使用阶段。
3. 使用反射 API 来操作这些信息。



### 10、获取 Class 对象有几种方法

**调用某个对象的** **getClass()方法**

```java
Person p=new Person();

Class clazz=p.getClass();
```

**调用某个类的** **class** **属性来获取该类对应的** **Class** 对象

```java
Class clazz=Person.class;
```

**使用** **Class** **类中的** **forName()**静态方法(最安全/性能最好)

```java
Class clazz=Class.forName("类的全路径"); (最常用)
```

当我们获得了想要操作的类的 Class 对象后，可以通过 Class 类中的方法获取并查看该类中的方法

和属性。

```java
//获取 Person 类的 Class 对象

 Class clazz=Class.forName("reflection.Person");
//获取 Person 类的所有方法信息
 Method[] method=clazz.getDeclaredMethods();
 for(Method m:method){
    System.out.println(m.toString());
 }
 //获取 Person 类的所有成员属性信息
 Field[] field=clazz.getDeclaredFields();
 for(Field f:field){
    System.out.println(f.toString());
 }
 //获取 Person 类的所有构造方法信息
 Constructor[] constructor=clazz.getDeclaredConstructors();
 for(Constructor c:constructor){
    System.out.println(c.toString());
 }
```



### 11、利用反射动态创建对象实例

**Class** **对象的** **newInstance()**

1. 使用 Class 对象的 newInstance()方法来创建该 Class 对象对应类的实例，但是这种方法要求

该 Class 对象对应的类有默认的空构造器。

**调用** **Constructor** **对象的** **newInstance()**

1. 先使用 Class 对象获取指定的 Constructor 对象，再调用 Constructor 对象的 newInstance()

方法来创建 Class 对象对应类的实例,通过这种方法可以选定构造方法创建实例。

```java
 //获取 Person 类的 Class 对象

 Class clazz=Class.forName("reflection.Person"); 

 //使用.newInstane 方法创建对象

 Person p=(Person) clazz.newInstance();

//获取构造方法并创建对象

 Constructor c=clazz.getDeclaredConstructor(String.class,String.class,int.class);

 //创建对象并设置属性13/04/2018 

 Person p1=(Person) c.newInstance("李四","男",20);
```



# Java异常

### 1、Java中异常分为哪两种？

编译时异常 运行时异常



### 2、异常的处理机制有几种？

异常捕捉：try…catch…finally，异常抛出：throws。



### 3、如何自定义一个异常

继承一个异常类，通常是RumtimeException或者Exception



### 4、try catch fifinally，try里有return，finally还执行么？

执行，并且finally的执行早于try里面的return

结论：

1、不管有木有出现异常，finally块中代码都会执行；

2、当try和catch中有return时，finally仍然会执行；

3、finally是在return后面的表达式运算后执行的（此时并没有返回运算后的值，而是先把要返回的值保存起来，管finally中的代码怎么样，返回的值都不会改变，任然是之前保存的值），所以函数返回值是在finally执行前确定的；

4、finally中最好不要包含return，否则程序会提前退出，返回值不是try或catch中保存的返回值。



### 5、 Excption与Error包结构

Java可抛出(Throwable)的结构分为三种类型：被检查的异常(CheckedException)，运行时异常

(RuntimeException)，错误(Error)。

**1、运行时异常**

定义:RuntimeException及其子类都被称为运行时异常。

特点:Java编译器不会检查它。也就是说，当程序中可能出现这类异常时，倘若既"没有通过throws声明抛出它"，也"没有用try-catch语句捕获它"，还是会编译通过。例如，除数为零时产生的ArithmeticException异常，数组越界时产生的IndexOutOfBoundsException异常，fail-fast机制产生的ConcurrentModi?cationException异常（java.util包下面的所有的集合类都是快速失败的，“快速失败”也就是fail-fast，它是Java集合的一种错误检测机制。当多个线程对集合进行结构上的改变的操作时，有可能会产生fail-fast机制。记住是有可能，而不是一定。例如：假设存在两个线程（线程1、线程

2），线程1通过Iterator在遍历集合A中的元素，在某个时候线程2修改了集合A的结构（是结构上面的修改，而不是简单的修改集合元素的内容），那么这个时候程序就会抛出ConcurrentModi?cationException 异常，从而产生fail-fast机制，这个错叫并发修改异常。Fail-safe，java.util.concurrent包下面的所有的类都是安全失败的，在遍历过程中，如果已经遍历的数组上的内容变化了，迭代器不会抛出ConcurrentModi?cationException异常。如果未遍历的数组上的内容发生了变化，则有可能反映到迭代过程中。这就是ConcurrentHashMap迭代器弱一致的表现。ConcurrentHashMap的弱一致性主要是为了提升效率，是一致性与效率之间的一种权衡。要成为强一致性，就得到处使用锁，甚至是全局锁，这就与Hashtable和同步的HashMap一样了。）等，都属于运行时异常。

常见的五种运行时异常：

ClassCastException（类转换异常）

IndexOutOfBoundsException（数组越界）

NullPointerException（空指针异常）

ArrayStoreException（数据存储异常，操作数组是类型不一致）

Bu?erOver?owException



**2、被检查异常**

定义:Exception类本身，以及Exception的子类中除了"运行时异常"之外的其它子类都属于被检查异常。特点 : Java编译器会检查它。此类异常，要么通过throws进行声明抛出，要么通过try-catch进行捕获处理，否则不能通过编译。例如，CloneNotSupportedException就属于被检查异常。当通过clone()接口去克隆一个对象，而该对象对应的类没有实现Cloneable接口，就会抛出CloneNotSupportedException异常。被检查异常通常都是可以恢复的。

如：

IOException

FileNotFoundException

SQLException

被检查的异常适用于那些不是因程序引起的错误情况，比如：读取文件时文件不存在引发的FileNotFoundException 。然而，不被检查的异常通常都是由于糟糕的编程引起的，比如：在对象引用时没有确保对象非空而引起的 NullPointerException 。



**3、错误**

定义 : Error类及其子类。

特点 : 和运行时异常一样，编译器也不会对错误进行检查。当资源不足、约束失败、或是其它程序无法继续运行的条件发生时，就产生错误。程序本身无法修复这些错误的。例如，VirtualMachineError就属于错误。出现这种错误会导致程序终止运行。OutOfMemoryError、ThreadDeath。

Java虚拟机规范规定JVM的内存分为了好几块，比如堆，栈，程序计数器，方法区等



### 6、Thow与thorws区别

**位置不同**

1. throws 用在函数上，后面跟的是异常类，可以跟多个；而 throw 用在函数内，后面跟的

是异常对象。

**功能不同：**

1. throws 用来声明异常，让调用者只知道该功能可能出现的问题，可以给出预先的处理方

式；throw 抛出具体的问题对象，执行到 throw，功能就已经结束了，跳转到调用者，并

将具体的问题对象抛给调用者。也就是说 throw 语句独立存在时，下面不要定义其他语

句，因为执行不到。

1. throws 表示出现异常的一种可能性，并不一定会发生这些异常；throw 则是抛出了异常，

执行 throw 则一定抛出了某种异常对象。

1. 两者都是消极处理异常的方式，只是抛出或者可能抛出异常，但是不会由函数去处理异

常，真正的处理异常由函数的上层调用处理。



### 7、Error与Exception区别？

Error和Exception都是java错误处理机制的一部分，都继承了Throwable类。

Exception表示的异常，异常可以通过程序来捕捉，或者优化程序来避免。

Error表示的是系统错误，不能通过程序来进行错误处理。



### 8、**error和exception有什么区别**

 error 表示恢复不是不可能但很困难的情况下的一种严重问题。比如说内存溢出。不可能指望程序能处理这样的情况 exception 表示一种设计或实现问题。也就是说，它表示如果程序运行正常，从不会发生的情况