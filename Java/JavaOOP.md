
![img](https://gitee.com/duchaochen/pythonnote/raw/master/img/%E9%9D%A2%E8%AF%95%E9%A2%98%E9%A2%98%E5%B0%81%E9%9D%A2-new.png)

# JavaOOP面试题

### 1、什么是B/S架构？什么是C/S架构

1. B/S(Browser/Server)，浏览器/服务器程序
2. C/S(Client/Server)，客户端/服务端，桌面应用程序

### 2、Java都有那些开发平台？

1. JAVA SE：主要用在客户端开发

2. JAVA EE：主要用在web应用程序开发

3. JAVA ME：主要用在嵌入式应用程序开发

   

### 3、什么是JDK？什么是JRE?

1. JDK：java development kit：java开发工具包，是开发人员所需要安装的环境

2. JRE：java runtime environment：java运行环境，java程序运行所需要安装的环境

   

### 4、Java语言有哪些特点

1. 简单易学、有丰富的类库

2. 面向对象（Java最重要的特性，让程序耦合度更低，内聚性更高）

3. 与平台无关性（JVM是Java跨平台使用的根本）

4. 可靠安全

5. 支持多线程

   

### 5、面向对象和面向过程的区别

1. 面向过程：

   一种较早的编程思想，顾名思义就是该思想是站着过程的角度思考问题，强调的就是功能行为，功能的执行过程，即先后顺序，而每一个功能我们都使用函数（类似于方法）把这些步骤一步一步实现。使用的时候依次调用函数就可以了。

2. 面向对象： 一种基于面向过程的新编程思想，顾名思义就是该思想是站在对象的角度思考问题，我们把多个功能合理放到不同对象里，强调的是具备某些功能的对象。 

   具备某种功能的实体，称为对象。面向对象最小的程序单元是：类。面向对象更加符合常规的思维方式，稳定性好，可重用性强，易于开发大型软件产品，有良好的可维护性。 

   在软件工程上，面向对象可以使工程更加模块化，实现更低的耦合和更高的内聚。

   

### 6、什么是数据结构？

​	计算机保存，组织数据的方式



### 7、Java的数据结构有那些？

​	1.线性表（ArrayList） 	2.链表（LinkedList） 	3.栈（Stack） 	4.队列（Queue） 	5.图（Map） 	6.树（Tree）



### 8、什么是OOP?

​	面向对象编程



### 9、类与对象的关系?

​	类是对象的抽象，对象是类的具体，类是对象的模板，对象是类的实例



### 10、Java中有几种数据类型

​	整形：byte,short,int,long 	浮点型：float,double 	字符型：char 	布尔型：boolean



### 11、标识符的命名规则。

1. 标识符的含义：

   是指在程序中，我们自己定义的内容，譬如，类的名字，方法名称以及变量名称等等，都是标识符。

2. 命名规则：（硬性要求）

   标识符可以包含英文字母，0-9的数字，$以及_

   标识符不能以数字开头

   标识符不是关键字

3. 命名规范：（非硬性要求）

   类名规范：首字符大写，后面每个单词首字母大写（大驼峰式）。

   变量名规范：首字母小写，后面每个单词首字母大写（小驼峰式）。

   方法名规范：同变量名。



### 12、instanceof关键字的作用

instanceof 严格来说是Java中的一个双目运算符，用来测试一个对象是否为一个类的实例，用法为：

```
boolean result = obj instanceof Class
```

其中 obj 为一个对象，Class 表示一个类或者一个接口，当 obj 为 Class 的对象，或者是其直接或

间接子类，或者是其接口的实现类，结果result 都返回 true，否则返回false。

注意：编译器会检查 obj 是否能转换成右边的class类型，如果不能转换则直接报错，如果不能确定

类型，则通过编译，具体看运行时定。

```
inti=0;

System.out.println(i instanceof Integer);//编译不通过i必须是引用类型，不能是基本类型

System.out.println(i instanceof Object);//编译不通过

Integer integer=newInteger(1);

System.out.println(integer instanceof Integer);//true
//false,在JavaSE规范中对instanceof运算符的规定就是：如果obj为null，那么将返回false。
System.out.println(nullinstanceofObject);
```



### 13、什么是隐式转换，什么是显式转换

显示转换就是类型强转，把一个大类型的数据强制赋值给小类型的数据；隐式转换就是大范围的变量能够接受小范围的数据；隐式转换和显式转换其实就是自动类型转换和强制类型转换。



### 14、Char类型能不能转成int类型？能不能转化成string类型，能不能转成double类型

​	Char在java中也是比较特殊的类型，它的int值从1开始，一共有2的16次方个数据；

​	Char<int<long<float<double；Char类型可以隐式转成int,double类型，但是不能隐式转换成string；如果char类

​	型转成byte，short类型的时候，需要强转。



### 15、什么是拆装箱？

1. 装箱就是自动将基本数据类型转换为包装器类型（int-->Integer）；调用方法：Integer的

   **valueOf(int)** **方法**

   拆箱就是自动将包装器类型转换为基本数据类型（Integer-->int）。调用方法：Integer的intValue方 法

   在Java SE5之前，如果要生成一个数值为10的Integer对象，必须这样进行：

   ```
   Integer i = new Integer(10); 
   ```

   而在从Java SE5开始就提供了自动装箱的特性，如果要生成一个数值为10的Integer对象，只需要这

   样就可以了：

   ```
   Integer i = 10; 
   ```

   面试题**1**： 以下代码会输出什么？

   ```
   public class Main { 
   ```

   ```
   
   ```

   ```
       public static void main(String[] args) { 
   ```

   ```
   
   ```

   ```
           Integer i1 = 100; 
   ```

   ```
   
   ```

   ```
           Integer i2 = 100; 
   ```

   ```
   
   ```

   ```
           Integer i3 = 200; 
   ```

   ```
   
   ```

   ```
           Integer i4 = 200; 
   ```

   ```
   
   ```

   ```
           System.out.println(i1==i2); 
   ```

   ```
   
   ```

   ```
           System.out.println(i3==i4); 
   ```

   ```
   
   ```

   ```
       } 
   ```

   ```
   }
   ```

   结果：

   ```
   true
   ```

   ```
   
   ```

   ```
   false
   ```

   

### 16、Java中的包装类都是那些？

​	byte：Byte，short：Short，int：Integer，long：Long，float：Float，double：Double，char：Character ，boolean：Boolean



### 17、一个java类中包含那些内容？

​	属性、方法、内部类、构造方法、代码块。



### 18、那针对浮点型数据运算出现的误差的问题，你怎么解决？

​	使用Bigdecimal类进行浮点型数据的运算



### 19、面向对象的特征有哪些方面?

抽象:

抽象是将一类对象的共同特征总结出来构造类的过程, 包括数据抽象和行为抽象两方面。抽象只关注对象有哪些属

性和行为,并不关注这些行为的细节是什么。

继承:

继承是从已有类得到继承信息创建新类的过程.提供继承信息的类被称为父类(超类、基类) ;得到继承信息的类被称

为子类(派生类)。继承让变化中的软件系统有了一定的延续性 ,同时继承也是封装程序中可变因素的重要手段(如果

不能理解请阅读阎宏博土的《Java 与模式》或《设计模式精解》中.关于桥梁模式的部分)。

封装：

通常认为封装是把数据和操作数据的方法绑定起来，对数据的访问 

只能通过已定义的接口。面向对象的本质就是将现实世界描绘成一系列完全自 

治、封闭的对象。我们在类中编写的方法就是对实现细节的一种封装；我们编写 

一个类就是对数据和数据操作的封装。可以说，封装就是隐藏一切可隐藏的东西， 

只向外界提供最简单的编程接口（可以想想普通洗衣机和全自动洗衣机的差别， 

明显全自动洗衣机封装更好因此操作起来更简单；我们现在使用的智能手机也是 

封装得足够好的，因为几个按键就搞定了所有的事情）。

多态性：

多态性是指允许不同子类型的对象对同一消息作出不同的响应。 

简单的说就是用同样的对象引用调用同样的方法但是做了不同的事情。多态性分 

为编译时的多态性和运行时的多态性。如果将对象的方法视为对象向外界提供的 

服务，那么运行时的多态性可以解释为：当 A 系统访问 B 系统提供的服务时，B 

系统有多种提供服务的方式，但一切对 A 系统来说都是透明的（就像电动剃须 

刀是 A 系统，它的供电系统是 B 系统，B 系统可以使用电池供电或者用交流电， 

甚至还有可能是太阳能，A 系统只会通过 B 类对象调用供电的方法，但并不知道 

供电系统的底层实现是什么，究竟通过何种方式获得了动力）。方法重载 

（overload）实现的是编译时的多态性（也称为前绑定），而方法重写（override） 

实现的是运行时的多态性（也称为后绑定）。运行时的多态是面向对象最精髓的 

东西，要实现多态需要做两件事：1). 方法重写（子类继承父类并重写父类中已 

有的或抽象的方法）；2). 对象造型（用父类型引用引用子类型对象，这样同样 

的引用调用同样的方法就会根据子类对象的不同而表现出不同的行为）。



### 20、**访问修饰符 public,private,protected,以及不写（默认）** 时的区别？

| 修饰符    | 当前类 | 同 包 | 子 类 | 其他包 |
| --------- | ------ | ----- | ----- | ------ |
| public    | 能     | 能    | 能    | 能     |
| protected | 能     | 能    | 能    | 不能   |
| default   | 能     | 能    | 不能  | 不能   |
| private   | 能     | 不能  | 不能  | 不能   |

类的成员不写访问修饰时默认为 default。默认对于同一个包中的其他类相当于公 开（public），对于不是同一个包中的其他类相当于私有（private）。受保护 （protected）对子类相当于公开，对不是同一包中的没有父子关系的类相当于私 有。Java 中，外部类的修饰符只能是 public 或默认，类的成员（包括内部类）的 修饰符可以是以上四种。



### 21、String 是最基本的数据类型吗？

不是。Java 中的基本数据类型只有 8 个：byte、short、int、long、float、double、 char、boolean；除了基本类型（primitive type），剩下的都是引用类型（reference type），Java 5 以后引入的枚举类型也算是一种比较特殊的引用类型。



### 22、**float f=3.4;是否正确？**

答:不正确。3.4 是双精度数，将双精度型（double）赋值给浮点型（float）属于 下转型（down-casting，也称为窄化）会造成精度损失，因此需要强制类型转换 float f =(float)3.4; 或者写成 float f =3.4F;。



### 23、**short s1 = 1; s1 = s1 + 1;有错吗?short s1 = 1; s1 += 1;** 有错吗？

对于 short s1 = 1; s1 = s1 + 1;由于 1 是 int 类型，因此 s1+1 运算结果也是 int 型，需要强制转换类型才能赋值给 short 型。而 short s1 = 1; s1 += 1;可以正确 编译，因为 s1+= 1;相当于 s1 = (short)(s1 + 1);其中有隐含的强制类型转换。



### 24、**重载和重写的区别**

**重写\****(Override)**

从字面上看，重写就是 重新写一遍的意思。其实就是在子类中把父类本身有的方法重新写一遍。子类继承了父类

原有的方法，但有时子类并不想原封不动的继承父类中的某个方法，所以在方法名，参数列表，返回类型(除过子

类中方法的返回值是父类中方法返回值的子类时)都相同的情况下， 对方法体进行修改或重写，这就是重写。但要

注意子类函数的访问修饰权限不能少于父类的。



```
public class Father { 

    public static void main(String[] args) { 

        // TODO Auto-generated method stub 

        Son s = new Son(); 

        s.sayHello(); 

    }

    public void sayHello() { 

        System.out.println("Hello"); 
    } 
}

class Son extends Father{ 

    @Override 

    public void sayHello() { 

        // TODO Auto-generated method stub 

        System.out.println("hello by "); 

    } 

}
```



原因： 在某个范围内的整型数值的个数是有限的，而浮点数却不是。

**重写 总结：**

1.发生在父类与子类之间

2.方法名，参数列表，返回类型（除过子类中方法的返回类型是父类中返回类型的子类）必须相同

3.访问修饰符的限制一定要大于被重写方法的访问修饰符（public>protected>default>private)

4.重写方法一定不能抛出新的检查异常或者比被重写方法申明更加宽泛的检查型异常



**重载（Overload）**

在一个类中，同名的方法如果有不同的参数列表（**参数类型不同、参数个数不同甚至是参数顺序不同**）

则视为重载。同时，重载对返回类型没有要求，可以相同也可以不同，但**不能通过返回类型是否相同来**

**判断重载**。 

```
public class Father {

    public static void main(String[] args) { 

        // TODO Auto-generated method stub 

        Father s = new Father(); 

        s.sayHello(); 

        s.sayHello("wintershii"); 

      }

    public void sayHello() { 

        System.out.println("Hello"); 

    }

    public void sayHello(String name) { 

        System.out.println("Hello" + " " + name); 

    } 

}
```

**重载总结：**

1.重载Overload是一个类中多态性的一种表现

2.重载要求同名方法的参数列表不同(参数类型，参数个数甚至是参数顺序)

3.重载的时候，返回值类型可以相同也可以不相同。无法以返回型别作为重载函数的区分标准



### 25、equals与==的区别

**==：**

== 比较的是变量(栈)内存中存放的对象的(堆)内存地址，用来判断两个对象的地址是否相同，即是否是

指相同一个对象。比较的是真正意义上的指针操作。

1、比较的是操作符两端的操作数是否是同一个对象。

2、两边的操作数必须是同一类型的（可以是父子类之间）才能编译通过。

3、比较的是地址，如果是具体的阿拉伯数字的比较，值相等则为true，如：

int a=10 与 long b=10L 与 double c=10.0都是相同的（为true），因为他们都指向地址为10的堆。



**equals：**

equals用来比较的是两个对象的内容是否相等，由于所有的类都是继承自java.lang.Object类的，所以

适用于所有对象，如果没有对该方法进行覆盖的话，调用的仍然是Object类中的方法，而Object中的

equals方法返回的却是==的判断。



**总结：**

所有比较是否相等时，都是用equals 并且在对常量相比较时，把常量写在前面，因为使用object的

equals  object可能为null  则空指针

在阿里的代码规范中只使用equals ，阿里插件默认会识别，并可以快速修改，推荐安装阿里插件来排

查老代码使用“==”，替换成equals



### 36、++i与i++的区别

i++：先赋值，后计算 ++i：先计算，后赋值



### 37、程序的结构有那些？

```
顺序结构
选择结构
循环结构
```



### 38、数组实例化有几种方式？

静态实例化：创建数组的时候已经指定数组中的元素,

```
int [] a= new int[]{ 1 , 3 , 3}
```

动态实例化：实例化数组的时候，只指定了数组程度，数组中所有元素都是数组类型的默认值



### 39、Java中各种数据默认值

Byte,short,int,long默认是都是0

Boolean默认值是false

Char类型的默认值是’’

Float与double类型的默认是0.0

对象类型的默认值是null



### 40、Java常用包有那些？

```
Java.lang
Java.io
Java.sql
Java.util
Java.awt
Java.net
Java.math
```



### 41、Object类常用方法有那些？

```
Equals
Hashcode
toString
wait
notify
clone
getClass
```



### 42、java中有没有指针？

有指针，但是隐藏了，开发人员无法直接操作指针，由jvm来操作指针



### 43、java中是值传递引用传递？

理论上说，java都是引用传递，对于基本数据类型，传递是值的副本，而不是值本身。对于对象类型，传递是对象的引用，当在一个方法操作操作参数的时候，其实操作的是引用所指向的对象。



### 44、实例化数组后，能不能改变数组长度呢？

不能，数组一旦实例化，它的长度就是固定的



### 45、假设数组内有5个元素，如果对数组进行反序，该如何做？

创建一个新数组，从后到前循环遍历每个元素，将取出的元素依次顺序放入新数组中



### 46、形参与实参区别

**实参(argument)：**

 全称为"实际参数"是在调用时传递给函数的参数. 实参可以是常量、变量、表达式、函数等， 无论实参是何种类型的量，在进行函数调用时，它们都必须具有确定的值， 以便把这些值传送给形参。 因此应预先用赋值，输入等办法使实参获得确定值。    

**形参(parameter)：**

全称为"形式参数" 由于它不是实际存在变量，所以又称虚拟变量。是在定义函数名和函数体的时候使用的参数,目的是用来接收调用该函数时传入的参数.在调用函数时，实参将赋值给形参。因而，必须注意实参的个数，类型应与形参一一对应，并且实参必须要有确定的值。



形参出现在**函数定义**中，在整个函数体内都可以使用， 离开该函数则不能使用。

实参出现在**主调函数中，进入被调函数后，实参变量也不能使用**。 

形参和实参的功能是作数据传送。发生函数调用时， **主调函数把实参的值传送给被调函数的形参从而实现主调函数向被调函数的数据传送**。

1.形参变量只有在被调用时才分配内存单元，**在调用结束时，** **即刻释放所分配的内存单元**。因此，形参只有在函数内部有效。 函数调用结束返回

主调函数后则不能再使用该形参变量。 

2.实参可以是常量、变量、表达式、函数等， 无论实参是何种类型的量，在进行函数调用时，它们都必须具有确定的值， 以便把这些值传送给形

参。 因此应预先用赋值，输入等办法使实参获得确定值。 

3.实参和形参在数量上，类型上，顺序上应严格一致， 否则会发生“类型不匹配”的错误。 

4.**函数调用中发生的数据传送是单向的**。 即只能把实参的值传送给形参，而不能把形参的值反向地传送给实参。 因此在函数调用过程中，形参的值

发生改变，而实参中的值不会变化。

5.当形参和实参不是指针类型时，在该函数运行时，**形参和实参是不同的变量，他们在内存中位于不同的位置，形参将实参的内容复制一份，在该**

**函数运行结束的时候形参被释放，而实参内容不会改变**。

而**如果函数的参数是指针类型变量**,**在调用该函数的过程中，传给函数的是实参的地址，在函数体内部使用的也是实参的地址，即使用的就是实参**

**本身**。所以在函数体内部可以改变实参的值。



### 47、构造方法能不能显式调用？

不能，构造方法当成普通方法调用，只有在创建对象的时候它才会被系统调用



### 48、什么是方法重载？

方法的重载就是在同一个类中允许同时存在一个以上的同名方法，只要它们的参数个数或者类型不同即可。在这种情况下，该方法就叫被重载了，这个过程称为方法的重载（override）



### 49、构造方法能不能重写？能不能重载？

可以重载，但不能重写。



### 50、内部类与静态内部类的区别？

静态内部类相对与外部类是独立存在的，在静态内部类中无法直接访问外部类中变量、方法。如果要访问的话，必须要new一个外部类的对象，使用new出来的对象来访问。但是可以直接访问静态的变量、调用静态的方法；

普通内部类作为外部类一个成员而存在，在普通内部类中可以直接访问外部类属性，调用外部类的方法。

如果外部类要访问内部类的属性或者调用内部类的方法，必须要创建一个内部类的对象，使用该对象访问属性或者调用方法。

如果其他的类要访问普通内部类的属性或者调用普通内部类的方法，必须要在外部类中创建一个普通内部类的对象作为一个属性，外同类可以通过该属性调用普通内部类的方法或者访问普通内部类的属性

如果其他的类要访问静态内部类的属性或者调用静态内部类的方法，直接创建一个静态内部类对象即可。



### 51、Static关键字有什么作用？

Static可以修饰内部类、方法、变量、代码块

Static修饰的类是静态内部类

Static修饰的方法是静态方法，表示该方法属于当前类的，而不属于某个对象的，静态方法也不能被重写，可以直接使用类名来调用。在static方法中不能使用this或者super关键字。

Static修饰变量是静态变量或者叫类变量，静态变量被所有实例所共享，不会依赖于对象。静态变量在内存中只有一份拷贝，在JVM加载类的时候，只为静态分配一次内存。

Static修饰的代码块叫静态代码块，通常用来做程序优化的。静态代码块中的代码在整个类加载的时候只会执行一次。静态代码块可以有多个，如果有多个，按照先后顺序依次执行。



### 52、final在java中的作用，有哪些用法?

final也是很多面试喜欢问的地方,但我觉得这个问题很无聊,通常能回答下以下5点就不错了: 

1. 被fifinal修饰的类不可以被继承
2. 被fifinal修饰的方法不可以被重写
3. 被fifinal修饰的变量不可以被改变.如果修饰引用,那么表示引用不可变,引用指向的内容可变. 
4. 被fifinal修饰的方法,JVM会尝试将其内联,以提高运行效率
5. 被fifinal修饰的常量,在编译阶段会存入常量池中.

除此之外,编译器对fifinal域要遵守的两个重排序规则更好:

在构造函数内对一个fifinal域的写入,与随后把这个被构造对象的引用赋值给一个引用变量,这两个操作之间不能重排序

初次读一个包含fifinal域的对象的引用,与随后初次读这个fifinal域,这两个操作之间不能重排序



### 53、StringString StringBuffffer **和** **StringBuilder** 的区别是什么？

String是只读字符串，它并不是基本数据类型，而是一个对象。从底层源码来看是一个fifinal类型的字符

数组，所引用的字符串不能被改变，一经定义，无法再增删改。每次对String的操作都会生成新的

String对象

```
private final char value[]; 
```

每次+操作 ： 隐式在堆上new了一个跟原字符串相同的StringBuilder对象，再调用append方法 拼接

+后面的字符。



StringBuffer与StringBuilder都继承了AbstractStringBulder类，而AbtractStringBuilder又实现了CharSequence接口，两个类都是用来进行字符串操作的。

在做字符串拼接修改删除替换时，效率比string更高。

StringBuffer是线程安全的，Stringbuilder是非线程安全的。所以Stringbuilder比stringbuffer效率更高，StringBuffer的方法大多都加了synchronized关键字



### 54、String str=”aaa”,与String str=new String(“aaa”)一样吗？

一共有两个引用，三个对象。因为”aa”与”bb”都是常量，常量的值不能改变，当执行字符串拼接时候，会创建一个新的常量是” aabbb”,有将其存到常量池中。



### 55、讲下java中的math类有那些常用方法？

Pow()：幂运算 Sqrt()：平方根 Round()：四舍五入 Abs()：求绝对值 Random()：生成一个0-1的随机数，包括0不包括1



### 56、String类的常用方法有那些？

charAt：返回指定索引处的字符 indexOf()：返回指定字符的索引 replace()：字符串替换 trim()：去除字符串两端空白 split()：分割字符串，返回一个分割后的字符串数组 getBytes()：返回字符串的byte类型数组 length()：返回字符串长度 toLowerCase()：将字符串转成小写字母 toUpperCase()：将字符串转成大写字符 substring()：截取字符串 format()：格式化字符串 equals()：字符串比较



### 57、Java中的继承是单继承还是多继承

Java中既有单继承，又有多继承。对于java类来说只能有一个父类，对于接口来说可以同时继承多个接口



### 58、Super与this表示什么？

Super表示当前类的父类对象 This表示当前类的对象



### 59、普通类与抽象类有什么区别？

普通类不能包含抽象方法，抽象类可以包含抽象方法 抽象类不能直接实例化，普通类可以直接实例化



### 60、什么是接口？为什么需要接口？

接口就是某个事物对外提供的一些功能的声明，是一种特殊的java类，接口弥补了java单继承的缺点



### 61、接口有什么特点？

接口中声明全是public static final修饰的常量 接口中所有方法都是抽象方法 接口是没有构造方法的 接口也不能直接实例化 接口可以多继承



### 62、抽象类和接口的区别?

抽象类：

1. 抽象方法，只有行为的概念，没有具体的行为实现。使用abstract关键字修饰，没有方法体。子类必须重写这些抽象方法。
2. 包含抽象方法的类，一定是抽象类。
3. 抽象类只能被继承，一个类只能继承一个抽象类。

接口：

1. 全部的方法都是抽象方法，属性都是常量
2. 不能实例化，可以定义变量。
3. 接口变量可以引用具体实现类的实例
4. 接口只能被实现，一个具体类实现接口，必须实现全部的抽象方法
5. 接口之间可以多实现
6. 一个具体类可以实现多个接口，实现多继承现象



### 63、**Hashcode**的作用

java的集合有两类，一类是List，还有一类是Set。前者有序可重复，后者无序不重复。当我们在set中插入的时候怎么判断是否已经存在该元素呢，可以通过equals方法。但是如果元素太多，用这样的方法就会比较满。



于是有人发明了哈希算法来提高集合中查找元素的效率。 这种方式将集合分成若干个存储区域，每个对象可以计算出一个哈希码，可以将哈希码分组，每组分别对应某个存储区域，根据一个对象的哈希码就可以确定该对象应该存储的那个区域。

 hashCode方法可以这样理解：它返回的就是根据对象的内存地址换算出的一个值。这样一来，当集合要添加新的元素时，先调用这个元素的hashCode方法，就一下子能定位到它应该放置的物理位置上。如果这个位置上没有元素，它就可以直接存储在这个位置上，不用再进行任何比较了；如果这个位置上已经有元素了，就调用它的equals方法与新元素进行比较，相同的话就不存了，不相同就散列其它的地址。这样一来实际调用equals方法的次数就大大降低了，几乎只需要一两次。



### 64、 Java的四种引用，强弱软虚

**强引用**

强引用是平常中使用最多的引用，强引用在程序内存不足（OOM）的时候也不会被回收，使用方式：

```
String str = new String("str"); 
```

**软引用**

软引用在程序内存不足时，会被回收，使用方式：

```
// 注意：wrf这个引用也是强引用，它是指向SoftReference这个对象的， 

// 这里的软引用指的是指向new String("str")的引用，也就是SoftReference类中T 

SoftReference<String> wrf = new SoftReference<String>(new String("str")); 
```

可用场景： 创建缓存的时候，创建的对象放进缓存中，当内存不足时，JVM就会回收早先创建的对象。

**弱引用**

弱引用就是只要JVM垃圾回收器发现了它，就会将之回收，使用方式：

```
WeakReference<String>wrf=newWeakReference<String>(str);
```

**可用场景：**Java源码中的java.util.WeakHashMap中的key就是使用弱引用，我的理解就是，

一旦我不需要某个引用，JVM会自动帮我处理它，这样我就不需要做其它操作。

**虚引用**

虚引用的回收机制跟弱引用差不多，但是它被回收之前，会被放入ReferenceQueue中。注意哦，其它引用是被JVM回收后才被传入ReferenceQueue中的。由于这个机制，所以虚引用大多被用于引用销毁前的处理工作。还有就是，虚引用创建的时候，必须带有ReferenceQueue，使用

例子：

```
PhantomReference<String>prf=newPhantomReference<String>(new 

String("str"),newReferenceQueue<>());
```

可用场景： 对象销毁前的一些操作，比如说资源释放等。** Object.finalize() 虽然也可以做这类动作，但是这个方式即不安全又低效

**上诉所说的几类引用，都是指对象本身的引用，而不是指** Reference **的四个子类的引用**

**(** SoftReference 等)。



### 65、Java创建对象有几种方式？

java中提供了以下四种创建对象的方式:

1. new创建新对象
2. 通过反射机制
3. 采用clone机制
4. 通过序列化机制



### 66、有没有可能两个不相等的对象有相同的hashcode

有可能.在产生hash冲突时,两个不相等的对象就会有相同的 hashcode 值.当hash冲突产生时,一般有以

下几种方式来处理:

1. 拉链法:每个哈希表节点都有一个next指针,多个哈希表节点可以用next指针构成一个单向链表，被分配到同一个索引上的多个节点可以用这个单向链表进行存储.

2. 开放定址法:一旦发生了冲突,就去寻找下一个空的散列地址,只要散列表足够大,空的散列地址总能找到,并将记录存入

3. 再哈希:又叫双哈希法,有多个不同的Hash函数.当发生冲突时,使用第二个,第三个….等哈希函数计算地址,直到无冲突.

   

### 67、拷贝和浅拷贝的区别是什么?

**浅拷贝:**

被复制对象的所有变量都含有与原来的对象相同的值,而所有的对其他对象的引用仍然指向原来的对象.换言之,浅拷贝仅仅复制所考虑的对象,而不复制它所引用的对象.



**深拷贝:**

被复制对象的所有变量都含有与原来的对象相同的值.而那些引用其他对象的变量将指向被复制过的新对象.而不再是原有的那些被引用的对象.换言之.深拷贝把要复制的对象所引用的对象都复制了一遍. 



### 68、static都有哪些用法?

所有的人都知道static关键字这两个基本的用法:静态变量和静态方法.也就是被static所修饰的变量/方法都属于类的静态资源,类实例所共享.

除了静态变量和静态方法之外,static也用于静态块,多用于初始化操作：

```
public calss PreCache{ 

    static{ 

    //执行相关操作 

    } 

}
```

此外static也多用于修饰内部类,此时称之为静态内部类.

最后一种用法就是静态导包,即 import static .import static是在JDK 1.5之后引入的新特性,可以用来指定导入某个类中的静态资源,并且不需要使用类名,可以直接使用资源名,比如:



```
import static java.lang.Math.*; 

public class Test{ 

    public static void main(String[] args){ 

        //System.out.println(Math.sin(20));传统做法 

        System.out.println(sin(20)); 

    } 

}
```



### 69、a=a+b与a+=b有什么区别吗?

+= 操作符会进行隐式自动类型转换,此处a+=b隐式的将加操作的结果类型强制转换为持有结果的类型, 而a=a+b则不会自动进行类型转换.如：

```
byte a = 127; 

byte b = 127; 

b = a + b; // 报编译错误:cannot convert from int to byte 

b += a; 
```

以下代码是否有错,有的话怎么改？

```
short s1= 1; 

s1 = s1 + 1; 
```

有错误.short类型在进行运算时会自动提升为int类型,也就是说 s1+1 的运算结果是int类型,而s1是short

类型,此时编译器会报错.

正确写法：

```
short s1= 1; 

s1 += 1;
```

+=操作符会对右边的表达式结果强转匹配左边的数据类型,所以没错.



### 70、final、finalize()、finally

**性质不同**

1. final为关键字；
2. finalize()为方法；
3. finally为区块标志，用于try语句中；



**作用**

1. final为用于标识常量的关键字，final标识的关键字存储在常量池中（在这里final常量的具体用法将在下面进行介绍）；

2. finalize()方法在Object中进行了定义，用于在对象“消失”时，由JVM进行调用用于对对象进行垃圾回收，类似于C++中的析构函数；用户自定义时，用于释放对象占用的资源（比如进行I/0操作）；

3. finally{}用于标识代码块，与try{}进行配合，不论try中的代码执行完或没有执行完（这里指有异常），该代码块之中的程序必定会进行；

   

### 71、JDBC操作的步骤

加载数据库驱动类 打开数据库连接 执行sql语句 处理返回结果 关闭资源



### 72、在使用jdbc的时候，如何防止出现sql注入的问题。

使用PreparedStatement类，而不是使用Statement类



### 73、怎么在JDBC内调用一个存储过程

使用CallableStatement



### 74、是否了解连接池，使用连接池有什么好处？

数据库连接是非常消耗资源的，影响到程序的性能指标。连接池是用来分配、管理、释放数据库连接的，可以使应用程序重复使用同一个数据库连接，而不是每次都创建一个新的数据库连接。通过释放空闲时间较长的数据库连接避免数据库因为创建太多的连接而造成的连接遗漏问题，提高了程序性能。



### 75、你所了解的数据源技术有那些？使用数据源有什么好处？

Dbcp,c3p0等，用的最多还是c3p0，因为c3p0比dbcp更加稳定，安全；通过配置文件的形式来维护数据库信息，而不是通过硬编码。当连接的数据库信息发生改变时，不需要再更改程序代码就实现了数据库信息的更新。



### 76、&和&&的区别

&是位运算符。&&是布尔逻辑运算符，在进行逻辑判断时用&处理的前面为false后面的内容仍需处理，用&&处理的前面为false不再处理后面的内容。



### 77、静态内部类如何定义

定义在类内部的静态类，就是静态内部类。

```
public class Out {

     private static int a;

     private int b;

     public static class Inner {

         public void print() {

         System.out.println(a);

         }

     } 

}
```



1. 静态内部类可以访问外部类所有的静态变量和方法，即使是 private 的也一样。
2. 静态内部类和一般类一致，可以定义静态变量、方法，构造方法等。
3. 其它类使用静态内部类需要使用“外部类.静态内部类”方式，如下所示：Out.Inner inner = new Out.Inner();inner.print();
4. Java集合类HashMap内部就有一个静态内部类Entry。Entry是HashMap存放元素的抽象，HashMap 内部维护 Entry 数组用了存放元素，但是 Entry 对使用者是透明的。像这种和外部类关系密切的，且不依赖外部类实例的，都可以使用静态内部类。



### 78、什么是成员内部类

定义在类内部的非静态类，就是成员内部类。成员内部类不能定义静态方法和变量（final修饰的除外）。这是因为成员内部类是非静态的，类初始化的时候先初始化静态成员，如果允许成员内部类定义静态变量，那么成员内部类的静态变量初始化顺序是有歧义的。实例：

```
 public class Out {

     private static int a;

     private int b;

     public class Inner {

         public void print() {

             System.out.println(a);

             System.out.println(b);

         }

     } 

}
```



### 79、Static Nested Class 和 Inner Class的不同

 Nested Class （一般是C++的说法），Inner Class (一般是JAVA的说法)。Java内部类与C++嵌套类最大的不同就在于是否有指向外部的引用上。注： 静态内部类（Inner Class）意味着1创建一个static内部类的对象，不需要一个外部类对象，2不能从一个static内部类的一个对象访问一个外部类对象



### 80、什么时候用assert

 assertion(断言)在软件开发中是一种常用的调试方式，很多开发语言中都支持这种机制。在实现中，assertion就是在程序中的一条语句，它对一个boolean表达式进行检查，一个正确程序必须保证这个boolean表达式的值为true；如果该值为false，说明程序已经处于不正确的状态下，系统将给出警告或退出。一般来说，assertion用于保证程序最基本、关键的正确性。assertion检查通常在开发和测试时开启。为了提高性能，在软件发布后，assertion检查通常是关闭的



### 81、**Java有没有goto**

 java中的保留字，现在没有在java中使用



### 82、**数组有没有length()这个方法? String有没有length()这个方法**

数组没有length()这个方法，有length的属性。String有有length()这个方法



### 83、**用最有效率的方法算出2乘以8等於几**

 2 << 3



### 84、**float型float f=3.4是否正确?**

不正确。精度不准确,应该用强制类型转换，如下所示：float f=(float)3.4



### 85、**排序都有哪几种方法？请列举**

排序的方法有：插入排序（直接插入排序、希尔排序），交换排序（冒泡排序、快速排序），选择排序（直接选择排序、堆排序），归并排序，分配排序（箱排序、基数排序）快速排序的伪代码。/ /使用快速排序方法对a[ 0 :n- 1 ]排序从a[ 0 :n- 1 ]中选择一个元素作为m i d d l e，该元素为支点把余下的元素分割为两段left 和r i g h t，使得l e f t中的元素都小于等于支点，而right 中的元素都大于等于支点递归地使用快速排序方法对left 进行排序递归地使用快速排序方法对right 进行排序所得结果为l e f t + m i d d l e + r i g h t



### 86、**静态变量和实例变量的区别？**

 static i = 10; //常量 class A a; a.i =10;//可变



### 87、**说出一些常用的类，包，接口，请各举5个**

常用的类：BufferedReader BufferedWriter FileReader FileWirter String Integer常用的包：java.lang java.awt java.io java.util java.sql常用的接口：Remote List Map Document NodeList



### 88、a.hashCode() 有什么用？与 a.equals(b) 有什么关系？  

hashCode() 方法是相应对象整型的 hash 值。它常用于基于 hash 的集合类，如 Hashtable、HashMap、LinkedHashMap 等等。它与 equals() 方法关系特别紧密。根据 Java 规范，两个使用 equal() 方法来判断相等的对象，必须具有相同的 hash code。  



### 89、Java 中的编译期常量是什么？使用它又什么风险？  

公共静态不可变（public static final ）变量也就是我们所说的编译期常量，这里的 public 可选的。实际上这些变量在编译时会被替换掉，因为编译器知道这些变量的值，并且知道这些变量在运行时不能改变。这种方式存在的一个问题是你使用了一个内部的或第三方库中的公有编译时常量，但是这个值后面被其他人改变了，但是你的客户端仍然在使用老的值，甚至你已经部署了一个新的 jar。为了避免这种情况，当你在更新依赖 JAR 文件时，确保重新编译你的程序  



### 90、在 Java 中，如何跳出当前的多重嵌套循环？  

在最外层循环前加一个标记如 A，然后用 break A;可以跳出多重循环。（Java 中支持带标签的 break 和 continue 语句，作用有点类似于 C 和 C++中的 goto 语句，但是就像要避免使用 goto 一样，应该避免使用带标签的 break 和 continue，因为它不会让你的程序变得更优雅，很多时候甚至有相反的作用，所以这种语法其实不知道更好）  



### 91、构造器（constructor）是否可被重写（override）？  

构造器不能被继承，因此不能被重写，但可以被重载。  



### 92、两个对象值相同(x.equals(y) == true)，但却可有不同的hash code，这句话对不对？  

不对，如果两个对象 x 和 y 满足 x.equals(y) == true，它们的哈希码（hash code）应当相同。Java 对于 eqauls 方法和 hashCode 方法是这样规定的：

(1)如果两个 对象相同（equals 方法返回 true），那么它们的 hashCode 值一定要相同；

(2)如果两个对象的 hashCode 相同，它们并不一定相同。当然，你未必要按照要求去做，但是如果你违背了上述原则就会发现在使用容器时，相同的对象可以出现在 Set 集合中，同时增加新元素的效率会大大下降（对于使用哈希存储的系统，如果哈希码频繁的冲突将会造成存取性能急剧下降）。  



### 93、是否可以继承 String 类？  

String 类是 final 类，不可以被继承，继承 String 本身就是一个错误的行为，对 String 类型最好的重用方式是关 联关系（Has-A）和依赖关系（Use-A）而不是继承关系（Is-A）。  



### 94、当一个对象被当作参数传递到一个方法后，此方法可改变这个对象的属性，并可返回变化后的结果，那么这里到底是值传递还是引用传递？  

是值传递。Java 语言的方法调用只支持参数的值传递。当一个对象实例作为一个参数被传递到方法中时，参数的值就是对该对象的引用。对象的属性可以在被调用过程中被改变，但对对象引用的改变是不会影响到调用者的。C++和 C#中可以通过传引用或传输出参数来改变传入的参数的值。在 C#中可以编写如下所示的代码，但是在 Java 中却做不到。  

```
using System;
namespace CS01 {
    class Program {
        public static void swap(ref int x, ref int y) {
            int temp = x;
            x = y;
            y = temp;
        } p
        ublic static void Main (string[] args) {
            int a = 5, b = 10;
            swap (ref a, ref b);
// a = 10, b = 5;
            Console.WriteLine ("a = {0}, b = {1}", a, b);
        }
    }
}
```

说明：Java 中没有传引用实在是非常的不方便，这一点在 Java 8 中仍然没有得到改进，正是如此在 Java 编写的代码中才会出现大量的 Wrapper 类（将需要通过方法调用修改的引用置于一个 Wrapper 类中，再将 Wrapper 对象传入方法），这样的做法只会让代码变得臃肿，尤其是让从 C 和 C++转型为 Java 程序员的开发者无法容忍。  



### 95、String 和 StringBuilder、StringBuffer 的区别？  

Java 平台提供了两种类型的字符串：String 和 StringBuffer/StringBuilder，它们可以储存和操作字符串。其中 String 是只读字符串，也就意味着 String 引用的字符串内容是不能被改变的。而 StringBuffer/StringBuilder 类表示的字符串对象可以直接进行修改。StringBuilder 是 Java 5 中引入的，它和 StringBuffer 的方法完全相同，区别在于它是在单线程环境下使用的，因为它的所有方面都没有被synchronized 修饰，因此它的效率也比 StringBuffer 要高。  



### 96、重载（Overload）和重写（Override）的区别。重载的方法能否根据返回类型进行区分？  

方法的重载和重写都是实现多态的方式，区别在于前者实现的是编译时的多态性，而后者实现的是运行时的多态性。重载发生在一个类中，同名的方法如果有不同的参数列表（参数类型不同、参数个数不同或者二者都不同）则视为重载；重写发生在子类与父类之间，重写要求子类被重写方法与父类被重写方法有相同的返回类型，比父类被重写方法更好访问，不能比父类被重写方法声明更多的异常（里氏代换原则）。重载对返回类型没有特殊的要求。  



### 97、char 型变量中能不能存贮一个中文汉字，为什么？  

char 类型可以存储一个中文汉字，因为 Java 中使用的编码是 Unicode（不选择任何特定的编码，直接使用字符在字符集中的编号，这是统一的唯一方法），一个 char 类型占 2 个字节（16 比特），所以放一个中文是没问题的。  



**补充：**使用 Unicode 意味着字符在 JVM 内部和外部有不同的表现形式，在 JVM内部都是 Unicode，当这个字符被从 JVM 内部转移到外部时（例如存入文件系统中），需要进行编码转换。所以 Java 中有字节流和字符流，以及在字符流和字节流之间进行转换的转换流，如 InputStreamReader 和 OutputStreamReader，这两个类是字节流和字符流之间的适配器类，承担了编码转换的任务；对于 C 程序员来说，要完成这样的编码转换恐怕要依赖于 union（联合体/共用体）共享内存的特征来实现了。  



### 98、抽象类（abstract class）和接口（interface）有什么异同  ？

抽象类和接口都不能够实例化，但可以定义抽象类和接口类型的引用。一个类如果继承了某个抽象类或者实现了某个接口都需要对其中的抽象方法全部进行实现，否则该类仍然需要被声明为抽象类。接口比抽象类更加抽象，因为抽象类中可以定义构造器，可以有抽象方法和具体方法，而接口中不能定义构造器而且其中的方法全部都是抽象方法。抽象类中的成员可以是 private、默认、protected、public 的，而接口中的成员全都是 public 的。抽象类中可以定义成员变量，而接口中定义的成员变量实际上都是常量。有抽象方法的类必须被声明为抽象类，而抽象类未必要有抽象方法。



### 99、静态嵌套类(Static Nested Class)和内部类（Inner Class）的不同？  

Static Nested Class 是被声明为静态（static）的内部类，它可以不依赖于外部类实例被实例化。而通常的内部类需要在外部类实例化后才能实例化，其语法看起来挺诡异的，如下所示  

```
/**
* 扑克类（一副扑克）
* @author 骆昊
*/
public class Poker {
    private static String[] suites = {"黑桃", "红桃", "草花", "方块"};
    private static int[] faces = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13};
    private Card[] cards;
    /**
    * 构造器
    * */
    public Poker() {
        cards = new Card[52];
        for(int i = 0; i < suites.length; i++) {
            for(int j = 0; j < faces.length; j++) {
                cards[i * 13 + j] = new Card(suites[i], faces[j]);
            }
        }
    } 
    /**
    * 洗牌 （随机乱序）
    * */
    public void shuffle() {
        for(int i = 0, len = cards.length; i < len; i++) {
            int index = (int) (Math.random() * len);
            Card temp = cards[index];
            cards[index] = cards[i];
            cards[i] = temp;
        }
    } 
    /**
    * 发牌
    * @param index 发牌的位置
    * */
    public Card deal(int index) {
        return cards[index];
    } 
    /**
    * 卡片类（一张扑克）
    * [内部类]
    * @author 骆昊
    * */
    public class Card {
        private String suite; // 花色
        private int face; // 点数
        public Card(String suite, int face) {
            this.suite = suite;
            this.face = face;
        } 
        @Override
        public String toString() {
            String faceStr = "";
            switch(face) {
                case 1: faceStr = "A"; break;
                case 11: faceStr = "J"; break;
                case 12: faceStr = "Q"; break;
                case 13: faceStr = "K"; break;
                default: faceStr = String.valueOf(face);
            } return suite + faceStr;
        }
    }
}

//测试类
class PokerTest {
    public static void main(String[] args) {
        Poker poker = new Poker();
        poker.shuffle(); // 洗牌
        Poker.Card c1 = poker.deal(0); // 发第一张牌
        // 对于非静态内部类 Card
        // 只有通过其外部类 Poker 对象才能创建 Card 对象
        Poker.Card c2 = poker.new Card("红心", 1); // 自己创建一张牌
        System.out.println(c1); // 洗牌后的第一张
        System.out.println(c2); // 打印: 红心 A
    }
}
```



### 100、Java 中会存在内存泄漏吗，请简单描述。  

理论 上 Java 因为 有垃 圾回 收机 制（ GC）不 会存 在内 存泄 露问 题（ 这也 是 Java 被广泛 使用 于服 务器 端编 程的 一个 重要 原因 ）； 然而 在实 际开 发中 ，可 能会 存在 无用但 可达 的对 象，这些 对象 不能 被 GC 回收 ，因此 也会 导致 内存 泄露 的发 生 。



例 如Hibernate 的 Session（ 一级 缓存 ）中的 对象 属于 持久 态，垃圾 回收 器是 不会 回收这些 对象 的，然而 这些 对象 中可 能存 在无 用的 垃圾 对象 ，如果 不及 时关 闭（close）或清 空（ flush）一 级缓 存就 可能 导致 内存 泄露 。下 面例 子中 的代 码也 会导 致内 存泄露  

```
import java.util.Arrays;
import java.util.EmptyStackException;
public class MyStack<T> {
    private T[] elements;
    private int size = 0;
    private static final int INIT_CAPACITY = 16;
    public MyStack() {
        elements = (T[]) new Object[INIT_CAPACITY];
    } 
    public void push(T elem) {
        ensureCapacity();
        elements[size++] = elem;
    } 
    public T pop() {
        if(size == 0)
            throw new EmptyStackException();
        return elements[--size];
    } 
    private void ensureCapacity() {
        if(elements.length == size) {
            elements = Arrays.copyOf(elements, 2 * size + 1);
        }
    }
}
```

上面的代码实现了一个栈（先进后出（FILO））结构，乍看之下似乎没有什么明显的问题，它甚至可以通过你编写的各种单元测试。然而其中的 pop 方法却存在内存泄露的问题，当我们用 pop 方法弹出栈中的对象时，该对象不会被当作垃圾回收，即使使用栈的程序不再引用这些对象，因为栈内部维护着对这些对象的过期引用（obsolete reference）。在支持垃圾回收的语言中，内存泄露是很隐蔽的，这种内存泄露其实就是无意识的对象保持。如果一个对象引用被无意识的保留起来了，那么垃圾回收器不会处理这个对象，也不会处理该对象引用的其他对象，即使这样的对象只有少数几个，也可能会导致很多的对象被排除在垃圾回收之外，从而对性能造成重大影响，极端情况下会引发 Disk Paging（物理内存与硬盘的虚拟内存交换数据），甚至造成 OutOfMemoryError。  



### 101、抽象的（abstract）方法是否可同时是静态的（static）,是否可同时是本地方法（native），是否可同时被 synchronized修饰？  

都不能。抽象方法需要子类重写，而静态的方法是无法被重写的，因此二者是矛盾的。本地方法是由本地代码（如 C 代码）实现的方法，而抽象方法是没有实现的，也是矛盾的。synchronized 和方法的实现细节有关，抽象方法不涉及实现细节，因此也是相互矛盾的。  



### 102、是否可以从一个静态（static）方法内部发出对非静态（non-static）方法的调用？  

不可以，静态方法只能访问静态成员，因为非静态方法的调用要先创建对象，在调用静态方法时可能对象并没有被初始化。  



### 103、如何实现对象克隆？  

有两种方式： 1). 实现 Cloneable 接口并重写 Object 类中的 clone()方法； 2). 实现 Serializable 接口，通过对象的序列化和反序列化实现克隆，可以实现真 正的深度克隆，代码如下。  

```
import java.io.ByteArrayInputStream;
import java.io.ByteArrayOutputStream;
import java.io.ObjectInputStream;
import java.io.ObjectOutputStream;
import java.io.Serializable;
public class MyUtil {
    private MyUtil() {
        throw new AssertionError();
    } 
    @SuppressWarnings("unchecked")
    public static <T extends Serializable> T clone(T obj) throws
    Exception {
        ByteArrayOutputStream bout = new ByteArrayOutputStream();
        ObjectOutputStream oos = new ObjectOutputStream(bout);
        oos.writeObject(obj);
        ByteArrayInputStream bin = new
        ByteArrayInputStream(bout.toByteArray());
        ObjectInputStream ois = new ObjectInputStream(bin);
        return (T) ois.readObject();
// 说明：调用 ByteArrayInputStream 或 ByteArrayOutputStream对象的 close 方法没有任何意义
// 这两个基于内存的流只要垃圾回收器清理对象就能够释放资源，这一点不同于对外部资源（如文件流）的释放
    }
}


```

测试代码：

```
import java.io.Serializable;
class Person implements Serializable {
    private static final long serialVersionUID = -9102017020286042305L;
    private String name; // 姓名
    private int age; // 年龄
    private Car car; // 座驾
    public Person(String name, int age, Car car) {
        this.name = name;
        this.age = age;
        this.car = car;
    } 
    public String getName() {
        return name;
    } 
    public void setName(String name) {
        this.name = name;
    } 
    public int getAge() {
        return age;
    } 
    public void setAge(int age) {
        this.age = age;
    } 
    public Car getCar() {
        return car;
    } 
    public void setCar(Car car) {
        this.car = car;
    } 
    @Override
    public String toString() {
        return "Person [name=" + name + ", age=" + age + ", car=" +
        car + "]";
    }
}
class Car implements Serializable {
    private static final long serialVersionUID = -5713945027627603702L;
    private String brand; // 品牌
    private int maxSpeed; // 最高时速
    public Car(String brand, int maxSpeed) {
        this.brand = brand;
        this.maxSpeed = maxSpeed;
    } 
    public String getBrand() {
        return brand;
    } 
    public void setBrand(String brand) {
        this.brand = brand;
    } 
    public int getMaxSpeed() {
        return maxSpeed;
    } 
    public void setMaxSpeed(int maxSpeed) {
        this.maxSpeed = maxSpeed;
    } 
    @Override
    public String toString() {
        return "Car [brand=" + brand + ", maxSpeed=" + maxSpeed +
        "]";
    }
} 
class CloneTest {
    public static void main(String[] args) {
        try {
                Person p1 = new Person("Hao LUO", 33, new Car("Benz",
                    300));
                Person p2 = MyUtil.clone(p1); // 深度克隆
                p2.getCar().setBrand("BYD");
                // 修改克隆的 Person 对象 p2 关联的汽车对象的品牌属性
                // 原来的 Person 对象 p1 关联的汽车不会受到任何影响
                // 因为在克隆 Person 对象时其关联的汽车对象也被克隆了
                System.out.println(p1);
            } catch (Exception e) {
                e.printStackTrace();
            }
    }
}
```

**注意：**基于 序列 化和 反序 列化 实现 的克 隆不 仅仅 是深 度克 隆， 更重 要的 是通 过泛型限 定， 可以 检查 出要 克隆 的对 象是 否支 持序 列化 ，这 项检 查是 编译 器完 成的 ，不是 在运 行时 抛出 异常 ，这种 是方 案明 显优 于使 用 Object 类的 clone 方法 克隆 对象。 让问 题在 编译 的时 候暴 露出 来总 是好 过把 问题 留到 运行 时。  



### 104、接口是否可继承（extends）接口？抽象类是否可实现（implements）接口？抽象类是否可继承具体类（concreteclass）？  

接 口 可 以 继 承 接 口 ， 而 且 支 持 多 重 继 承 。 抽 象 类 可 以 实 现 (implements)接 口 ， 抽 象 类 可 继 承 具 体 类 也 可 以 继 承 抽 象 类 。  



### 105、一个”.java”源文件中是否可以包含多个类（不是内部类）？有什么限制？  

可以，但一个源文件中最多只能有一个公开类（public class）而且文件名必须和公开类的类名完全保持一致。  



### 106、Anonymous Inner Class(匿名内部类)是否可以继承其它类？是否可以实现接口？  

可以继承其他类或实现其他接口，在 Swing 编程和 Android 开发中常用此方式来实现事件监听和回调。  



### 107、内部类可以引用它的包含类（外部类）的成员吗？有没有什么限制？

一个内部类对象可以访问创建它的外部类对象的成员，包括私有成员。



### 108、Java 中的 final 关键字有哪些用法？  

(1)修饰类：表示该类不能被继承；

(2)修饰方法：表示方法不能被重写；

(3)修饰变量：表示变量只能一次赋值以后值不能被修改（常量）。  



# Java集合/泛型面试题

### 1、ArrayList和linkedList的区别

Array(数组）是基于索引**(index)**的数据结构，它使用索引在数组中搜索和读取数据是很快的。

Array获取数据的时间复杂度是O(1),但是要删除数据却是开销很大，因为这需要重排数组中的所有数据, 

(因为删除数据以后, 需要把后面所有的数据前移)

**缺点:** 数组初始化必须指定初始化的长度, 否则报错

例如:

```
int[] a = new int[4];//推荐使用int[] 这种方式初始化 

int c[] = {23,43,56,78};//长度：4，索引范围：[0,3]
```

List—是一个有序的集合，可以包含重复的元素，提供了按索引访问的方式，它继承Collection。

List有两个重要的实现类：ArrayList和LinkedList

ArrayList: 可以看作是能够自动增长容量的数组

ArrayList的toArray方法返回一个数组

ArrayList的asList方法返回一个列表

ArrayList底层的实现是Array, 数组扩容实现

LinkList是一个双链表,在添加和删除元素时具有比ArrayList更好的性能.但在get与set方面弱于

ArrayList.当然,这些对比都是指数据量很大或者操作很频繁。



### 2、 **HashMap**和**HashTable**的区别

**1、两者父类不同**

HashMap是继承自AbstractMap类，而Hashtable是继承自Dictionary类。不过它们都实现了同时实现

了map、Cloneable（可复制）、Serializable（可序列化）这三个接口。

**2、对外提供的接口不同**

Hashtable比HashMap多提供了elments() 和contains() 两个方法。

 elments() 方法继承自Hashtable的父类Dictionnary。elements() 方法用于返回此Hashtable中的

value的枚举。

contains()方法判断该Hashtable是否包含传入的value。它的作用与containsValue()一致。事实上，

contansValue() 就只是调用了一下contains() 方法。

**3、对null的支持不同**

Hashtable：key和value都不能为null。

HashMap：key可以为null，但是这样的key只能有一个，因为必须保证key的唯一性；可以有多个key

值对应的value为null。 

**4、安全性不同**

HashMap是线程不安全的，在多线程并发的环境下，可能会产生死锁等问题，因此需要开发人员自己

处理多线程的安全问题。

Hashtable是线程安全的，它的每个方法上都有synchronized 关键字，因此可直接用于多线程中。

虽然HashMap是线程不安全的，但是它的效率远远高于Hashtable，这样设计是合理的，因为大部分的

使用场景都是单线程。当需要多线程操作的时候可以使用线程安全的ConcurrentHashMap。

ConcurrentHashMap虽然也是线程安全的，但是它的效率比Hashtable要高好多倍。因为

ConcurrentHashMap使用了分段锁，并不对整个数据进行锁定。

**5、初始容量大小和每次扩充容量大小不同**

**6、计算hash值的方法不同**



### 3、**Collection包结构，与Collections的区别**

Collection是集合类的上级接口，子接口有 Set、List、LinkedList、ArrayList、Vector、Stack、Set；

Collections是集合类的一个帮助类， 它包含有各种有关集合操作的静态多态方法，用于实现对各种集

合的搜索、排序、线程安全化等操作。此类不能实例化，就像一个工具类，服务于Java的Collection框

架。

### 4、泛型常用特点 （待补充）

泛型是Java SE 1.5之后的特性， 《Java 核心技术》中对泛型的定义是：

> “泛型” 意味着编写的代码可以被不同类型的对象所重用。

 “泛型”，顾名思义，“泛指的类型”。我们提供了泛指的概念，但具体执行的时候却可以有具体的规则来约束，比如我们用的非常多的ArrayList就是个泛型类，ArrayList作为集合可以存放各种元素，如Integer, String，自定义的各种类型等，但在我们使用的时候通过具体的规则来约束，如我们可以约束集合中只存放Integer类型的元素，如

```
List<Integer> iniData = new ArrayList<>()
```

**使用泛型的好处？**

以集合来举例，使用泛型的好处是我们不必因为添加元素类型的不同而定义不同类型的集合，如整型集

合类，浮点型集合类，字符串集合类，我们可以定义一个集合来存放整型、浮点型，字符串型数据，而

这并不是最重要的，因为我们只要把底层存储设置了Object即可，添加的数据全部都可向上转型为

Object。 更重要的是我们可以通过规则按照自己的想法控制存储的数据类型。



### 5、说说List,Set,Map三者的区别

**List(对付顺序的好帮手)：** List接口存储一组不唯一（可以有多个元素引用相同的对象），有序的

对象

**Set(注重独一无二的性质):**不允许重复的集合。不会有多个元素引用相同的对象。

**Map(用Key来搜索的专):** 使用键值对存储。Map会维护与Key有关联的值。两个Key可以引用相

同的对象，但Key不能重复，典型的Key是String类型，但也可以是任何对象。



### 6、Array与ArrayList有什么不一样？

Array与ArrayList都是用来存储数据的集合。ArrayList底层是使用数组实现的，但是arrayList对数组进行了封装和功能扩展，拥有许多原生数组没有的一些功能。我们可以理解成ArrayList是Array的一个升级版。



### 7、Map有什么特点

以键值对存储数据 元素存储循序是无序的 不允许出现重复键



### 8、集合类存放于 Java.util 包中， 主要有几 种接口

主要包含set(集）、 list(列表包含 Queue）和 map(映射)。  

1. Collection： Collection 是集合 List、 Set、 Queue 的最基本的接口。
2. Iterator：迭代器，可以通过迭代器遍历集合中的数据
3. Map：是映射表的基础接口    

![img](https://gitee.com/duchaochen/pythonnote/raw/master/img/20200408/1-1.png)

### 9、什么是list接口

Java 的 List 是非常常用的数据类型。 List 是有序的 Collection。 Java List 一共三个实现类： 分别是 ArrayList、 Vector 和 LinkedList 。

list接口结构图

![img](https://gitee.com/duchaochen/pythonnote/raw/master/img/20200408/1-2.png)

### 10、说说ArrayList（数组）  

ArrayList 是最常用的 List 实现类，内部是通过数组实现的，它允许对元素进行快速随机访问。数 组的缺点是每个元素之间不能有间隔， 当数组大小不满足时需要增加存储能力，就要将已经有数 组的数据复制到新的存储空间中。 当从 ArrayList 的中间位置插入或者删除元素时，需要对数组进 行复制、移动、代价比较高。因此，它适合随机查找和遍历，不适合插入和删除。  



### 11、Vector（ 数组实现、 线程同步）  

Vector 与 ArrayList 一样，也是通过数组实现的，不同的是它支持线程的同步，即某一时刻只有一 个线程能够写 Vector，避免多线程同时写而引起的不一致性，但实现同步需要很高的花费，因此， 访问它比访问 ArrayList 慢  。



### 12、说说LinkList（链表）  

LinkedList 是用链表结构存储数据的，很适合数据的动态插入和删除，随机访问和遍历速度比较 慢。另外，他还提供了 List 接口中没有定义的方法，专门用于操作表头和表尾元素，可以当作堆 栈、队列和双向队列使用  



### 13、什么Set集合

Set 注重独一无二的性质,该体系集合用于存储无序(存入和取出的顺序不一定相同)元素， 值不能重 复。对象的相等性本质是对象 hashCode 值（java 是依据对象的内存地址计算出的此序号） 判断 的， 如果想要让两个不同的对象视为相等的，就必须覆盖 Object 的 hashCode 方法和 equals 方 法。  

set结构结构图

![img](https://gitee.com/duchaochen/pythonnote/raw/master/img/20200408/1-3.png)

![img](https://gitee.com/duchaochen/pythonnote/raw/master/img/20200408/1-3.png)



### 14、HashSet（ Hash 表）  

哈希表边存放的是哈希值。 HashSet 存储元素的顺序并不是按照存入时的顺序（和 List 显然不 同） 而是按照哈希值来存的所以取数据也是按照哈希值取得。元素的哈希值是通过元素的 hashcode 方法来获取的, HashSet 首先判断两个元素的哈希值，如果哈希值一样，接着会比较 equals 方法 如果 equls 结果为 true ， HashSet 就视为同一个元素。如果 equals 为 false 就不是 同一个元素。 哈希值相同 equals 为 false 的元素是怎么存储呢,就是在同样的哈希值下顺延（可以认为哈希值相 同的元素放在一个哈希桶中）。也就是哈希一样的存一列。 如图 1 表示 hashCode 值不相同的情 况； 图 2 表示 hashCode 值相同，但 equals 不相同的情况。  

![img](https://gitee.com/duchaochen/pythonnote/raw/master/img/20200408/1-4.png)

HashSet 通过 hashCode 值来确定元素在内存中的位置。 一个 hashCode 位置上可以存放多个元 素。  



### 15、什么是TreeSet（二叉树）  

1. TreeSet()是使用二叉树的原理对新 add()的对象按照指定的顺序排序（升序、降序），每增 加一个对象都会进行排序，将对象插入的二叉树指定的位置。 
2. Integer 和 String 对象都可以进行默认的 TreeSet 排序，而自定义类的对象是不可以的， 自 己定义的类必须实现 Comparable 接口，并且覆写相应的 compareTo()函数，才可以正常使 用。
3. 在覆写 compare()函数时，要返回相应的值才能使 TreeSet 按照一定的规则来排序
4. 比较此对象与指定对象的顺序。如果该对象小于、等于或大于指定对象，则分别返回负整 数、零或正整数  



### 16、说说LinkHashSet（ HashSet+LinkedHashMap）  

对于 LinkedHashSet 而言，它继承与 HashSet、又基于 LinkedHashMap 来实现的。 LinkedHashSet 底层使用 LinkedHashMap 来保存所有元素，它继承与 HashSet，其所有的方法 操作上又与 HashSet 相同，因此 LinkedHashSet 的实现上非常简单，只提供了四个构造方法，并 通过传递一个标识参数，调用父类的构造器，底层构造一个 LinkedHashMap 来实现，在相关操 作上与父类 HashSet 的操作相同，直接调用父类 HashSet 的方法即可。  



### 17、HashMap（数组+链表+红黑树）  

HashMap 根据键的 hashCode 值存储数据，大多数情况下可以直接定位到它的值，因而具有很快 的访问速度，但遍历顺序却是不确定的。 HashMap 最多只允许一条记录的键为 null，允许多条记 录的值为 null。 HashMap 非线程安全，即任一时刻可以有多个线程同时写 HashMap，可能会导 致数据的不一致。如果需要满足线程安全，可以用 Collections 的 synchronizedMap 方法使 HashMap 具有线程安全的能力，或者使用 ConcurrentHashMap。 我们用下面这张图来介绍 HashMap 的结构。  

![img](https://gitee.com/duchaochen/pythonnote/raw/master/img/20200408/1-5.png)

大方向上， HashMap 里面是一个数组，然后数组中每个元素是一个单向链表。上图中，每个绿色 的实体是嵌套类 Entry 的实例， Entry 包含四个属性： key, value, hash 值和用于单向链表的 next。

1. capacity：当前数组容量，始终保持 2^n，可以扩容，扩容后数组大小为当前的 2 倍。
2. oadFactor：负载因子，默认为 0.75。  
3. threshold：扩容的阈值，等于 capacity * loadFactor  



Java8 对 HashMap 进行了一些修改， 最大的不同就是利用了红黑树，所以其由 数组+链表+红黑 树 组成。 根据 Java7 HashMap 的介绍，我们知道，查找的时候，根据 hash 值我们能够快速定位到数组的 具体下标，但是之后的话， 需要顺着链表一个个比较下去才能找到我们需要的，时间复杂度取决 于链表的长度，为 O(n)。为了降低这部分的开销，在 Java8 中， 当链表中的元素超过了 8 个以后， 会将链表转换为红黑树，在这些位置进行查找的时候可以降低时间复杂度为 O(logN)。  

![img](https://gitee.com/duchaochen/pythonnote/raw/master/img/20200408/1-6.png)

### 18、说说ConcurrentHashMap  

**Segment 段**  

ConcurrentHashMap 和 HashMap 思路是差不多的，但是因为它支持并发操作，所以要复杂一 些。整个 ConcurrentHashMap 由一个个 Segment 组成， Segment 代表”部分“或”一段“的 意思，所以很多地方都会将其描述为分段锁。注意，行文中，我很多地方用了“槽”来代表一个 segment。  

**线程安全（Segment 继承 ReentrantLock 加锁）**  

简单理解就是， ConcurrentHashMap 是一个 Segment 数组， Segment 通过继承 ReentrantLock 来进行加锁，所以每次需要加锁的操作锁住的是一个 segment，这样只要保证每 个 Segment 是线程安全的，也就实现了全局的线程安全  

![img](https://gitee.com/duchaochen/pythonnote/raw/master/img/20200408/1-7.png)

**并行度（默认 16）**  

concurrencyLevel：并行级别、并发数、 Segment 数，怎么翻译不重要，理解它。默认是 16， 也就是说 ConcurrentHashMap 有 16 个 Segments，所以理论上， 这个时候，最多可以同时支 持 16 个线程并发写，只要它们的操作分别分布在不同的 Segment 上。这个值可以在初始化的时 候设置为其他值，但是一旦初始化以后，它是不可以扩容的。再具体到每个 Segment 内部，其实 每个 Segment 很像之前介绍的 HashMap，不过它要保证线程安全，所以处理起来要麻烦些。  

**Java8 实现 （引入了红黑树）**  

Java8 对 ConcurrentHashMap 进行了比较大的改动,Java8 也引入了红黑树。  

![img](https://gitee.com/duchaochen/pythonnote/raw/master/img/20200408/1-8.png)

### 19、HashTable（线程安全）  

Hashtable 是遗留类，很多映射的常用功能与 HashMap 类似，不同的是它承自 Dictionary 类， 并且是线程安全的，任一时间只有一个线程能写 Hashtable，并发性不如 ConcurrentHashMap， 因为 ConcurrentHashMap 引入了分段锁。 Hashtable 不建议在新代码中使用，不需要线程安全 的场合可以用 HashMap 替换，需要线程安全的场合可以用 ConcurrentHashMap 替换  



### 20、TreeMap（可排序）  

TreeMap 实现 SortedMap 接口，能够把它保存的记录根据键排序，默认是按键值的升序排序， 也可以指定排序的比较器，当用 Iterator 遍历 TreeMap 时，得到的记录是排过序的。 如果使用排序的映射，建议使用 TreeMap。 在使用 TreeMap 时， key 必须实现 Comparable 接口或者在构造 TreeMap 传入自定义的 Comparator，否则会在运行时抛出 java.lang.ClassCastException 类型的异常。 参考： https://www.ibm.com/developerworks/cn/java/j-lo-tree/index.html  

### 21、LinkHashMap（记录插入顺序）  

LinkedHashMap 是 HashMap 的一个子类，保存了记录的插入顺序，在用 Iterator 遍历 LinkedHashMap 时，先得到的记录肯定是先插入的，也可以在构造时带参数，按照访问次序排序。 参考 1： http://www.importnew.com/28263.html 参考 2： http://www.importnew.com/20386.html#comment-648123  



### 22、泛型类<T>  

泛型类的声明和非泛型类的声明类似，除了在类名后面添加了类型参数声明部分。和泛型方法一样，泛型类的类型参数声明部分也包含一个或多个类型参数，参数间用逗号隔开。一个泛型参数，也被称为一个类型变量，是用于指定一个泛型类型名称的标识符。因为他们接受一个或多个参数，这些类被称为参数化的类或参数化的类型。  

```
public class Box<T> {
    private T t;
    public void add(T t) {
        this.t = t;
    }
    public T get() {
        return t;
    }
}
```



### 23、类型通配符?  

类 型 通 配 符 一 般 是 使 用 ? 代 替 具 体 的 类 型 参 数 。 例 如 List<?> 在 逻 辑 上 是List<String>,List<Integer> 等所有 List<具体类型实参>的父类。  



### 24、类型擦除  

Java 中的泛型基本上都是在编译器这个层次来实现的。在生成的 Java 字节代码中是不包含泛型中的类型信息的。使用泛型的时候加上的类型参数，会被编译器在编译的时候去掉。这个过程就称为类型擦除。

如在代码中定义的 List<Object>和 List<String>等类型，在编译之后都会变成 List。 JVM 看到的只是 List，而由泛型附加的类型信息对 JVM 来说是不可见的。

类型擦除的基本过程也比较简单，首先是找到用来替换类型参数的具体类。这个具体类一般是 Object。如果指定了类型参数的上界的话，则使用这个上界。把代码中的类型参数都替换成具体的类。  



![img](https://gitee.com/duchaochen/pythonnote/raw/master/img/%E9%9D%A2%E8%AF%95%E9%A2%98%E9%A2%98%E5%B0%81%E9%9D%A2-new.png)



# Java异常面试题

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



![img](https://gitee.com/duchaochen/pythonnote/raw/master/img/%E9%9D%A2%E8%AF%95%E9%A2%98%E9%A2%98%E5%B0%81%E9%9D%A2-new.png)



# Java中的IO与NIO面试题

### 1、**Java** **中** **IO** 流？

**Java** **中** **IO** 流分为几种?

1. 按照流的流向分，可以分为输入流和输出流；
2. 按照操作单元划分，可以划分为字节流和字符流；
3. 按照流的角色划分为节点流和处理流。

Java Io 流共涉及 40 多个类，这些类看上去很杂乱，但实际上很有规则，而且彼此之间存在非常紧密的

联系， Java I0 流的 40 多个类都是从如下 4 个抽象类基类中派生出来的。

1. InputStream/Reader: 所有的输入流的基类，前者是字节输入流，后者是字符输入流。
2. OutputStream/Writer: 所有输出流的基类，前者是字节输出流，后者是字符输出流。



### 2、 **Java IO与 NIO的区别**

NIO即New IO，这个库是在JDK1.4中才引入的。NIO和IO有相同的作用和目的，但实现方式不同，NIO 主要用到的是块，所以NIO的效率要比IO高很多。在Java API中提供了两套NIO，一套是针对标准输入输出NIO，另一套就是网络编程NIO。



### 3、常用io类有那些

```
File
FileInputSteam，FileOutputStream
BufferInputStream，BufferedOutputSream
PrintWrite
FileReader，FileWriter
BufferReader，BufferedWriter
ObjectInputStream，ObjectOutputSream
```



### 4、字节流与字符流的区别

以字节为单位输入输出数据，字节流按照8位传输 以字符为单位输入输出数据，字符流按照16位传输



### 5、阻塞 IO 模型  

最传统的一种 IO 模型，即在读写数据过程中会发生阻塞现象。当用户线程发出 IO 请求之后，内核会去查看数据是否就绪，如果没有就绪就会等待数据就绪，而用户线程就会处于阻塞状态，用户线程交出 CPU。当数据就绪之后，内核会将数据拷贝到用户线程，并返回结果给用户线程，用 户线程才解除 block 状态。典型的阻塞 IO 模型的例子为： data = socket.read();如果数据没有就绪，就会一直阻塞在 read 方法  



### 6、非阻塞 IO 模型  

当用户线程发起一个 read 操作后，并不需要等待，而是马上就得到了一个结果。 如果结果是一个error 时，它就知道数据还没有准备好，于是它可以再次发送 read 操作。一旦内核中的数据准备好了，并且又再次收到了用户线程的请求，那么它马上就将数据拷贝到了用户线程，然后返回。所以事实上，在非阻塞 IO 模型中，用户线程需要不断地询问内核数据是否就绪，也就说非阻塞 IO不会交出 CPU，而会一直占用 CPU。 典型的非阻塞 IO 模型一般如下：  

```
while(true){
    data = socket.read();
    if(data!= error){
        //处理数据
        break;
    }
}
```

但是对于非阻塞 IO 就有一个非常严重的问题， 在 while 循环中需要不断地去询问内核数据是否就绪，这样会导致 CPU 占用率非常高，因此一般情况下很少使用 while 循环这种方式来读取数据。  



### 7、多路复用 IO 模型  

多路复用 IO 模型是目前使用得比较多的模型。 Java NIO 实际上就是多路复用 IO。在多路复用 IO模型中，会有一个线程不断去轮询多个 socket 的状态，只有当 socket 真正有读写事件时，才真正调用实际的 IO 读写操作。因为在多路复用 IO 模型中，只需要使用一个线程就可以管理多个socket，系统不需要建立新的进程或者线程，也不必维护这些线程和进程，并且只有在真正有socket 读写事件进行时，才会使用 IO 资源，所以它大大减少了资源占用。在 Java NIO 中，是通过 selector.select()去查询每个通道是否有到达事件，如果没有事件，则一直阻塞在那里，因此这种方式会导致用户线程的阻塞。多路复用 IO 模式，通过一个线程就可以管理多个 socket，只有当 socket 真正有读写事件发生才会占用资源来进行实际的读写操作。因此，多路复用 IO 比较适合连接数比较多的情况。  

另外多路复用 IO 为何比非阻塞 IO 模型的效率高是因为在非阻塞 IO 中，不断地询问 socket 状态时通过用户线程去进行的，而在多路复用 IO 中，轮询每个 socket 状态是内核在进行的，这个效率要比用户线程要高的多。  

不过要注意的是，多路复用 IO 模型是通过轮询的方式来检测是否有事件到达，并且对到达的事件 逐一进行响应。因此对于多路复用 IO 模型来说， 一旦事件响应体很大，那么就会导致后续的事件 迟迟得不到处理，并且会影响新的事件轮询。  



### 8、信号驱动 IO 模型  

在信号驱动 IO 模型中，当用户线程发起一个 IO 请求操作，会给对应的 socket 注册一个信号函数，然后用户线程会继续执行，当内核数据就绪时会发送一个信号给用户线程，用户线程接收到信号之后，便在信号函数中调用 IO 读写操作来进行实际的 IO 请求操作。  



### 9、异步 IO 模型  

异步 IO 模型才是最理想的 IO 模型，在异步 IO 模型中，当用户线程发起 read 操作之后，立刻就可以开始去做其它的事。而另一方面，从内核的角度，当它受到一个 asynchronous read 之后，它会立刻返回，说明 read 请求已经成功发起了，因此不会对用户线程产生任何 block。然后，内核会等待数据准备完成，然后将数据拷贝到用户线程，当这一切都完成之后，内核会给用户线程发送一个信号，告诉它 read 操作完成了。也就说用户线程完全不需要实际的整个 IO 操作是如何进行的， 只需要先发起一个请求，当接收内核返回的成功信号时表示 IO 操作已经完成，可以直接去使用数据了。  



也就说在异步 IO 模型中， IO 操作的两个阶段都不会阻塞用户线程，这两个阶段都是由内核自动完成，然后发送一个信号告知用户线程操作已完成。用户线程中不需要再次调用 IO 函数进行具体的读写。这点是和信号驱动模型有所不同的，在信号驱动模型中，当用户线程接收到信号表示数据已经就绪，然后需要用户线程调用 IO 函数进行实际的读写操作；而在异步 IO 模型中，收到信号表示 IO 操作已经完成，不需要再在用户线程中调用 IO 函数进行实际的读写操作。  

注意，异步 IO 是需要操作系统的底层支持，在 Java 7 中，提供了 Asynchronous IO。 更多参考： http://www.importnew.com/19816.html  



### 10、JAVA NIO  

NIO 主要有三大核心部分： Channel(通道)， Buffer(缓冲区), Selector。传统 IO 基于字节流和字符流进行操作， 而 NIO 基于 Channel 和 Buffer(缓冲区)进行操作，数据总是从通道读取到缓冲区中，或者从缓冲区写入到通道中。 Selector(选择区)用于监听多个通道的事件（比如：连接打开，数据到达）。因此，单个线程可以监听多个数据通道。  NIO 和传统 IO 之间第一个最大的区别是， IO 是面向流的， NIO 是面向缓冲区的。  



### 11、NIO 的缓冲区  

Java IO 面向流意味着每次从流中读一个或多个字节，直至读取所有字节，它们没有被缓存在任何地方。此外，它不能前后移动流中的数据。如果需要前后移动从流中读取的数据， 需要先将它缓存到一个缓冲区。 NIO 的缓冲导向方法不同。数据读取到一个它稍后处理的缓冲区，需要时可在缓冲区中前后移动。这就增加了处理过程中的灵活性。但是，还需要检查是否该缓冲区中包含所有您需要处理的数据。而且，需确保当更多的数据读入缓冲区时，不要覆盖缓冲区里尚未处理的数据。  



### 12、NIO 的非阻塞  

IO 的各种流是阻塞的。这意味着，当一个线程调用 read() 或 write()时，该线程被阻塞，直到有一些数据被读取，或数据完全写入。该线程在此期间不能再干任何事情了。 NIO 的非阻塞模式，使一个线程从某通道发送请求读取数据，但是它仅能得到目前可用的数据，如果目前没有数据可用时，就什么都不会获取。而不是保持线程阻塞，所以直至数据变的可以读取之前，该线程可以继续做其他的事情。 非阻塞写也是如此。一个线程请求写入一些数据到某通道，但不需要等待它完全写入，这个线程同时可以去做别的事情。 线程通常将非阻塞 IO 的空闲时间用于在其它通道上执行 IO 操作，所以一个单独的线程现在可以管理多个输入和输出通道（channel）。  



### 13、Channel  

首先说一下 Channel，国内大多翻译成“通道”。 Channel 和 IO 中的 Stream(流)是差不多一个等级的。 只不过 Stream 是单向的，譬如： InputStream, OutputStream， 而 Channel 是双向的，既可以用来进行读操作，又可以用来进行写操作。NIO 中的 Channel 的主要实现有：

1. FileChannel
2. DatagramChannel
3. SocketChannel
4. ServerSocketChannel 这里看名字就可以猜出个所以然来：分别可以对应文件 IO、 UDP 和 TCP（Server 和 Client）。 下面演示的案例基本上就是围绕这 4 个类型的 Channel 进行陈述的。



### 14、Buffer  

Buffer，故名思意， 缓冲区，实际上是一个容器，是一个连续数组。 Channel 提供从文件、网络读取数据的渠道，但是读取或写入的数据都必须经由 Buffer。  

![img](https://gitee.com/duchaochen/pythonnote/raw/master/img/20200408/1-14.png)



上面的图描述了从一个客户端向服务端发送数据，然后服务端接收数据的过程。客户端发送数据时，必须先将数据存入 Buffer 中，然后将 Buffer 中的内容写入通道。服务端这边接收数据必须通过 Channel 将数据读入到 Buffer 中，然后再从 Buffer 中取出数据来处理。

在 NIO 中， Buffer 是一个顶层父类，它是一个抽象类，常用的 Buffer 的子类有：ByteBuffer、 IntBuffer、 CharBuffer、 LongBuffer、 DoubleBuffer、 FloatBuffer、ShortBuffer  



### 15、Selector  

Selector 类是 NIO 的核心类， Selector 能够检测多个注册的通道上是否有事件发生，如果有事件发生，便获取事件然后针对每个事件进行相应的响应处理。这样一来，只是用一个单线程就可以管理多个通道，也就是管理多个连接。这样使得只有在连接真正有读写事件发生时，才会调用函数来进行读写，就大大地减少了系统开销，并且不必为每个连接都创建一个线程，不用去维护多个线程，并且避免了多线程之间的上下文切换导致的开销。  



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

```
Person p=new Person();

Class clazz=p.getClass();
```

**调用某个类的** **class** **属性来获取该类对应的** **Class** 对象

```
Class clazz=Person.class;
```

**使用** **Class** **类中的** **forName()**静态方法(最安全/性能最好)

```
Class clazz=Class.forName("类的全路径"); (最常用)
```

当我们获得了想要操作的类的 Class 对象后，可以通过 Class 类中的方法获取并查看该类中的方法

和属性。

```
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

```
 //获取 Person 类的 Class 对象

 Class clazz=Class.forName("reflection.Person"); 

 //使用.newInstane 方法创建对象

 Person p=(Person) clazz.newInstance();

//获取构造方法并创建对象

 Constructor c=clazz.getDeclaredConstructor(String.class,String.class,int.class);

 //创建对象并设置属性13/04/2018 

 Person p1=(Person) c.newInstance("李四","男",20);
```



![img](https://gitee.com/duchaochen/pythonnote/raw/master/img/%E9%9D%A2%E8%AF%95%E9%A2%98%E9%A2%98%E5%B0%81%E9%9D%A2-new.png)



# Java序列化面试题

### 1、**什么是java序列化，如何实现java序列化？**

序列化就是一种用来处理对象流的机制，所谓对象流也就是将对象的内容进行流化。可以对流化后的对象进行读写操作，也可将流化后的对象传输于网络之间。序列化是为了解决在对对象流进行读写操作时所引发的问题。序列化的实现：将需要被序列化的类实现Serializable接口，该接口没有需要实现的方法，implements Serializable只是为了标注该对象是可被序列化的，然后使用一个输出流(如：FileOutputStream)来构造一个ObjectOutputStream(对象流)对象，接着，使用ObjectOutputStream对象的writeObject(Object obj)方法就可以将参数为obj的对象写出(即保存其状态)，要恢复的话则用输入流。



### 2、保存(持久化)对象及其状态到内存或者磁盘

Java 平台允许我们在内存中创建可复用的 Java 对象，但一般情况下，只有当 JVM 处于运行时，这些对象才可能存在，即，这些对象的生命周期不会比 JVM 的生命周期更长。 但在现实应用中，就可能要求在JVM停止运行之后能够保存(持久化)指定的对象，并在将来重新读取被保存的对象。Java 对象序列化就能够帮助我们实现该功能。



### 3、序列化对象以字节数组保持-静态成员不保存

使用 Java 对象序列化， 在保存对象时，会把其状态保存为一组字节，在未来， 再将这些字节组装成对象。必须注意地是， 对象序列化保存的是对象的”状态”，即它的成员变量。由此可知，对象序列化不会关注类中的静态变量。  



### 4、序列化用户远程对象传输

除了在持久化对象时会用到对象序列化之外，当使用 RMI(远程方法调用)，或在网络中传递对象时，都会用到对象序列化。 Java序列化API为处理对象序列化提供了一个标准机制，该API简单易用。



### 5、Serializable 实现序列化

在 Java 中， 只要一个类实现了 java.io.Serializable 接口，那么它就可以被序列化。ObjectOutputStream 和 ObjectInputStream 对对象进行序列化及反序列化通过 ObjectOutputStream 和 ObjectInputStream 对对象进行序列化及反序列化。



### 6、writeObject 和 readObject 自定义序列化策略

在类中增加 writeObject 和 readObject 方法可以实现自定义序列化策略。



### 7、序列化 ID

虚拟机是否允许反序列化，不仅取决于类路径和功能代码是否一致，一个非常重要的一点是两个类的序列化 ID 是否一致（就是 private static final long serialVersionUID  



### 8、序列化并不保存静态变量

序列化子父类说明 要想将父类对象也序列化，就需要让父类也实现 Serializable 接口。  



### 9、Transient 关键字阻止该变量被序列化到文件中

1. 在变量声明前加上 Transient 关键字，可以阻止该变量被序列化到文件中，在被反序列 化后， transient 变量的值被设为初始值，如 int 型的是 0，对象型的是 null。

2. 服务器端给客户端发送序列化对象数据，对象中有一些数据是敏感的，比如密码字符串 等，希望对该密码字段在序列化时，进行加密，而客户端如果拥有解密的密钥，只有在 客户端进行反序列化时，才可以对密码进行读取，这样可以一定程度保证序列化对象的 数据安全。

   

### 10、序列化（深 clone 一中实现）  

在 Java 语言里深复制一个对象，常常可以先使对象实现 Serializable 接口，然后把对象（实际上只是对象的一个拷贝）写到一个流里，再从流里读出来，便可以重建对象。  



![img](https://gitee.com/duchaochen/pythonnote/raw/master/img/%E9%9D%A2%E8%AF%95%E9%A2%98%E9%A2%98%E5%B0%81%E9%9D%A2-new.png)



# Java注解面试题

### 1、4种标准元注解是哪四种？

元注解的作用是负责注解其他注解。 Java5.0 定义了 4 个标准的 meta-annotation 类型，它们被用来提供对其它 annotation 类型作说明。



**@Target** **修饰的对象范围**

@Target说明了Annotation所修饰的对象范围： Annotation可被用于 packages、types（类、接口、枚举、Annotation 类型）、类型成员（方法、构造方法、成员变量、枚举值）、方法参数和本地变量（如循环变量、catch 参数）。在 Annotation 类型的声明中使用了 target 可更加明晰其修饰的目标



**@Retention** **定义 被保留的时间长短**

Retention 定义了该 Annotation 被保留的时间长短：表示需要在什么级别保存注解信息，用于描述注解的生命周期（即：被描述的注解在什么范围内有效），取值（RetentionPoicy）由：

1. SOURCE:在源文件中有效（即源文件保留）
2. CLASS:在 class 文件中有效（即 class 保留）
3. RUNTIME:在运行时有效（即运行时保留）
4. 

**@Documented 描述-javadoc**

@ Documented 用于描述其它类型的 annotation 应该被作为被标注的程序成员的公共 API，因

此可以被例如 javadoc 此类的工具文档化。



**@Inherited** **阐述了某个被标注的类型是被继承的**

@Inherited 元注解是一个标记注解，@Inherited 阐述了某个被标注的类型是被继承的。如果一

个使用了@Inherited 修饰的 annotation 类型被用于一个 class，则这个 annotation 将被用于该

class 的子类。



### 2、注解是什么？

Annotation（注解）是 Java 提供的一种对元程序中元素关联信息和元数据（metadata）的途径和方法。 Annatation(注解)是一个接口，程序可以通过反射来获取指定程序中元素的 Annotation对象，然后通过该 Annotation 对象来获取注解中的元数据信息。   