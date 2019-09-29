## 欢迎光临我的github主页

我将在接下来的时间内将我的一些个人学习进度与成果展示在该页面中

### 一些笔记

```markdown
一、JAVA
--------------------- 

（java源文件的后缀名是.java。源文件通过jvm虚拟机编译后会生成二进制字节码文件，后缀是.class）
1.在Java中，可以将一个类定义在另一个类里面或者一个方法里边，这样的类称为内部类，广泛意义上的内部类一般包括四种：成员内部类，局部内部类，匿名内部类，静态内部类 。
类的成员不写访问修饰时默认为default。默认对于同一个包中的其他类相当于公开（public），对于不是同一个包中的其他类相当于私有（private）。受保护（protected）对子类相当于公开，对不是同一包中的没有父子关系的类相当于私有。Java中，外部类的修饰符只能是public或默认，类的成员（包括内部类）的修饰符可以是以上四种。

Static Nested Class是被声明为静态（static）的内部类，它可以不依赖于外部类实例被实例化。而通常的内部类需要在外部类实例化后才能实例化

1).成员内部类

（1）该类像是外部类的一个成员，可以无条件的访问外部类的所有成员属性和成员方法（包括private成员和静态成员）；

（2）成员内部类拥有与外部类同名的成员变量时，会发生隐藏现象，即默认情况下访问的是成员内部类中的成员。如果要访问外部类中的成员，需要以下形式访问：【外部类.this.成员变量  或  外部类.this.成员方法】；

（3）在外部类中如果要访问成员内部类的成员，必须先创建一个成员内部类的对象，再通过指向这个对象的引用来访问；

（4）成员内部类是依附外部类而存在的，也就是说，如果要创建成员内部类的对象，前提是必须存在一个外部类的对象；

（5）内部类可以拥有private访问权限、protected访问权限、public访问权限及包访问权限。如果成员内部类用private修饰，则只能在外部类的内部访问；如果用public修饰，则任何地方都能访问；如果用protected修饰，则只能在同一个包下或者继承外部类的情况下访问；如果是默认访问权限，则只能在同一个包下访问。外部类只能被public和包访问两种权限修饰。

2).局部内部类

（1）局部内部类是定义在一个方法或者一个作用域里面的类，它和成员内部类的区别在于局部内部类的访问仅限于方法内或者该作用域内；

（2）局部内部类就像是方法里面的一个局部变量一样，是不能有public、protected、private以及static修饰符的。

3).匿名内部类

（1）一般使用匿名内部类的方法来编写事件监听代码；

（2）匿名内部类是不能有访问修饰符和static修饰符的；

（3）匿名内部类是唯一一种没有构造器的类；

（4）匿名内部类用于继承其他类或是实现接口，并不需要增加额外的方法，只是对继承方法的实现或是重写。

4).内部静态类

（1）静态内部类是不需要依赖于外部类的，这点和类的静态成员属性有点类似；

（2）不能使用外部类的非static成员变量或者方法。

2.java对象初始化顺序
先说结论：

父类静态代码块，父类静态成员变量（同级，按代码顺序执行）
子类静态代码块，子类静态成员变量（同级，按代码顺序执行）
父类普通代码块，父类普通成员变量（同级，按代码顺序执行）
父类构造方法
子类普通代码块，子类普通成员变量（同级，按代码顺序执行）
子类构造方法
注意点：

静态内容只在类加载时执行一次，之后不再执行。
默认调用父类的无参构造方法，可以在子类构造方法中利用super指定调用父类的哪个构造方法。

3.重写和重载的区别
重载： 发生在同一个类中，方法名必须相同，参数类型不同、个数不同、顺序不同，方法返回值和访问修饰符可以 不同，发生在编译时。   
重写： 发生在父子类中，方法名、参数列表必须相同，返回值范围小于等于父类，抛出的异常范围小于等于父类， 访问修饰符范围大于等于父类；如果父类方法访问修饰符为 private 则子类就不能重写该方法。 

4.ﬁnal关键字主要用在三个地方：变量、方法、类。
1）. 对于一个ﬁnal变量，如果是基本数据类型的变量，则其数值一旦在初始化之后便不能更改；如果是引用类型的 变量，则在对其初始化之后便不能再让其指向另一个对象。 
2）. 当用ﬁnal修饰一个类时，表明这个类不能被继承。ﬁnal类中的所有成员方法都会被隐式地指定为ﬁnal方法。
3）. 使用ﬁnal方法的原因有两个。第一个原因是把方法锁定，以防任何继承类修改它的含义；第二个原因是效率。 在早期的Java实现版本中，会将ﬁnal方法转为内嵌调用。但是如果方法过于庞大，可能看不到内嵌调用带来的 任何性能提升（现在的Java版本已经不需要使用ﬁnal方法进行这些优化了）。类中所有的private方法都隐式地 指定为ﬁanl。 

5.Object类是一个特殊的类，是所有类的父类。它主要提供了以下11个方法：
public final native Class<?> getClass()//native方法，用于返回当前运行时对象的Class对象，使用了 final关键字修饰，故不允许子类重写。
public native int hashCode() //native方法，用于返回对象的哈希码，主要使用在哈希表中，比如JDK中的 HashMap。 
public boolean equals(Object obj)//用于比较2个对象的内存地址是否相等，String类对该方法进行了重写用户 比较字符串的值是否相等。
protected native Object clone() throws CloneNotSupportedException//naitive方法，用于创建并返回 当前对象的一份拷贝。一般情况下，对于任何对象 x，表达式 x.clone() != x 为true，x.clone().getClass() == x.getClass() 为true。Object本身没有实现Cloneable接口，所以不重写clone方法并且进行调用的话会发生 CloneNotSupportedException异常。
public String toString()//返回类的名字@实例的哈希码的16进制的字符串。建议Object所有的子类都重写这个方 法。
public final native void notify()//native方法，并且不能重写。唤醒一个在此对象监视器上等待的线程(监视 器相当于就是锁的概念)。如果有多个线程在等待只会任意唤醒一个。
public final native void notifyAll()//native方法，并且不能重写。跟notify一样，唯一的区别就是会唤醒 在此对象监视器上等待的所有线程，而不是一个线程。
public final native void wait(long timeout) throws InterruptedException//native方法，并且不能 重写。暂停线程的执行。注意：sleep方法没有释放锁，而wait方法释放了锁 。timeout是等待时间。
public final void wait(long timeout, int nanos) throws InterruptedException//多了nanos参数， 这个参数表示额外时间（以毫微秒为单位，范围是 0-999999）。 所以超时的时间还需要加上nanos毫秒。
public final void wait() throws InterruptedException//跟之前的2个wait方法一样，只不过该方法一直等 待，没有超时时间这个概念
protected void finalize() throws Throwable { }//实例被垃圾回收器回收的时候触发的操作

6.异常
在 Java 中，所有的异常都有一个共同的祖先java.lang包中的 Throwable类。Throwable： 有两个重要的子类： Exception（异常） 和 Error（错误） ，二者都是 Java 异常处理的重要子类，各自都包含大量子类。 Error（错误）:是程序无法处理的错误，表示运行应用程序中较严重问题。大多数错误与代码编写者执行的操作无 关，而表示代码运行时 JVM（Java 虚拟机）出现的问题。例如，Java虚拟机运行错误（Virtual MachineError），当 JVM 不再有继续执行操作所需的内存资源时，将出现 OutOfMemoryError。这些异常发生时，Java虚拟机（JVM）一 般会选择线程终止。
这些错误表示故障发生于虚拟机自身、或者发生在虚拟机试图执行应用时，如Java虚拟机运行错误（Virtual MachineError）、类定义错误（NoClassDefFoundError）等。这些错误是不可查的，因为它们在应用程序的控制和 处理能力之 外，而且绝大多数是程序运行时不允许出现的状况。对于设计合理的应用程序来说，即使确实发生了错 误，本质上也不应该试图去处理它所引起的异常状况。在 Java中，错误通过Error的子类描述。 Exception（异常）:是程序本身可以处理的异常。Exception 类有一个重要的子类 RuntimeException。 RuntimeException 异常由Java虚拟机抛出。NullPointerException（要访问的变量没有引用任何对象时，抛出该 异常）、ArithmeticException（算术运算异常，一个整数除以0时，抛出该异常）和 ArrayIndexOutOfBoundsException （下标越界异常）。
注意：异常和错误的区别：异常能被程序本身可以处理，错误是无法处理。
Throwable类常用方法 public string getMessage():返回异常发生时的详细信息 public string toString():返回异常发生时的简要描述 public string getLocalizedMessage():返回异常对象的本地化信息。使用Throwable的子类覆盖这个方法，可 以声称本地化信息。如果子类没有覆盖该方法，则该方法返回的信息与getMessage（）返回的结果相同 public void printStackTrace():在控制台上打印Throwable对象封装的异常信息
异常处理总结
try 块：用于捕获异常。其后可接零个或多个catch块，如果没有catch块，则必须跟一个ﬁnally块。
catch 块：用于处理try捕获到的异常。 ﬁnally 块：无论是否捕获或处理异常，ﬁnally块里的语句都会被执行。当在try块或catch块中遇到return语句 时，ﬁnally语句块将在方法返回之前被执行。 在以下4种特殊情况下，ﬁnally块不会被执行：
1. 在ﬁnally语句块中发生了异常。 2. 在前面的代码中用了System.exit()退出程序。 3. 程序所在的线程死亡。 4. 关闭CPU

7.接口和抽象类的区别是什么 
1）. 接口的方法默认是 public，所有方法在接口中不能有实现(Java 8 开始接口方法可以有默认实现），抽象类可以 有非抽象的方法 
2）. 接口中的实例变量默认是 ﬁnal 类型的，而抽象类中则不一定 
3）. 一个类可以实现多个接口，但多只能实现一个抽象类 
4）. 一个类实现接口的话要实现接口的所有方法，而抽象类不一定 
5）. 接口不能用 new 实例化，但可以声明，但是必须引用一个实现该接口的对象 从设计层面来说，抽象是对类的抽 象，是一种模板设计，接口是行为的抽象，是一种行为的规范。
备注:在JDK8中，接口也可以定义静态方法，可以直接用接口名调用。实现类和实现是不可以调用的。如果同时实现 两个接口，接口中定义了一样的默认方法，必须重写，不然会报错。

8.用键盘输入常用的的两种方法 
Scanner input = new Scanner(System.in); String s  = input.nextLine(); input.close();
BufferedReader input = new BufferedReader(new InputStreamReader(System.in)); String s = input.readLine(); 

9.Collection 
1. List 
Arraylist： Object数组 Vector： Object数组 LinkedList： 双向链表(JDK1.6之前为循环链表，JDK1.7取消了循环) 
2. Set 
HashSet（无序，唯一）: 基于 HashMap 实现的，底层采用 HashMap 来保存元素 LinkedHashSet： LinkedHashSet 继承与 HashSet，并且其内部是通过 LinkedHashMap 来实现的。有点类 似于我们之前说的LinkedHashMap 其内部是基于 Hashmap 实现一样，不过还是有一点点区别的。 TreeSet（有序，唯一）： 红黑树(自平衡的排序二叉树。) 
Map 
HashMap： JDK1.8之前HashMap由数组+链表组成的，数组是HashMap的主体，链表则是主要为了解决哈希 冲突而存在的（“拉链法”解决冲突）.JDK1.8以后在解决哈希冲突时有了较大的变化，当链表长度大于阈值（默 认为8）时，将链表转化为红黑树，以减少搜索时间 
LinkedHashMap: LinkedHashMap 继承自 HashMap，所以它的底层仍然是基于拉链式散列结构即由数组和 链表或红黑树组成。另外，LinkedHashMap 在上面结构的基础上，增加了一条双向链表，使得上面的结构可以 保持键值对的插入顺序。同时通过对链表进行相应的操作，实现了访问顺序相关逻辑。 
HashTable: 数组+链表组成的，数组是 HashMap 的主体，链表则是主要为了解决哈希冲突而存在的 
TreeMap: 红黑树（自平衡的排序二叉树）

10.面向对象的特征： 
- 抽象：抽象是将一类对象的共同特征总结出来构造类的过程，包括数据抽象和行为抽象两方面。抽象只关注对象有哪些属性和行为，并不关注这些行为的细节是什么。 
- 继承：继承是从已有类得到继承信息创建新类的过程。提供继承信息的类被称为父类（超类、基类）；得到继承信息的类被称为子类（派生类）。继承让变化中的软件系统有了一定的延续性，同时继承也是封装程序中可变因素的重要手段（如果不能理解请阅读阎宏博士的《Java与模式》或《设计模式精解》中关于桥梁模式的部分）。 
- 封装：通常认为封装是把数据和操作数据的方法绑定起来，对数据的访问只能通过已定义的接口。面向对象的本质就是将现实世界描绘成一系列完全自治、封闭的对象。我们在类中编写的方法就是对实现细节的一种封装；我们编写一个类就是对数据和数据操作的封装。可以说，封装就是隐藏一切可隐藏的东西，只向外界提供最简单的编程接口（可以想想普通洗衣机和全自动洗衣机的差别，明显全自动洗衣机封装更好因此操作起来更简单；我们现在使用的智能手机也是封装得足够好的，因为几个按键就搞定了所有的事情）。 
- 多态性：多态性是指允许不同子类型的对象对同一消息作出不同的响应。简单的说就是用同样的对象引用调用同样的方法但是做了不同的事情。

二、JAVA多线程
--------------------- 

1.悲观锁和乐观锁
乐观锁
 总是认为不会产生并发问题，每次去取数据的时候总认为不会有其他线程对数据进行修改，因此不会上锁，但是在更新时会判断其他线程在这之前有没有对数据进行修改，一般会使用版本号机制或CAS操作实现。
 version方式：一般是在数据表中加上一个数据版本号version字段，表示数据被修改的次数，当数据被修改时，version值会加一。当线程A要更新数据值时，在读取数据的同时也会读取version值，在提交更新时，若刚才读取到的version值为当前数据库中的version值相等时才更新，否则重试更新操作，直到更新成功。
核心SQL代码：
update table set x=x+1, version=version+1 where id=#{id} and version=#{version};  
 CAS操作方式：即compare and swap 或者 compare and set，涉及到三个操作数，数据所在的内存值，预期值，新值。当需要更新时，判断当前内存值与之前取到的值是否相等，若相等，则用新值更新，若失败则重试，一般情况下是一个自旋操作，即不断的重试。

悲观锁
 总是假设最坏的情况，每次取数据时都认为其他线程会修改，所以都会加锁（读锁、写锁、行锁等），当其他线程想要访问数据时，都需要阻塞挂起。可以依靠数据库实现，如行锁、读锁和写锁等，都是在操作之前加锁，在Java中，synchronized的思想也是悲观锁。
 
2.synchronized  
synchronized关键字解决的是多个线程之间访问资源的同步性，synchronized关键字可以保证被它修饰的方法或者 代码块在任意时刻只能有一个线程执行。
JDK1.6 对锁的实现引入了大量的优化，如偏向锁、轻量级锁、自旋锁、适应性自旋锁、锁消除、锁粗化等技术来减 少锁操作的开销。
锁主要存在四种状态，依次是：无锁状态、偏向锁状态、轻量级锁状态、重量级锁状态，他们会随着竞争的激烈而逐 渐升级。注意锁可以升级不可降级，这种策略是为了提高获得锁和释放锁的效率。

修饰实例方法，作用于当前对象实例加锁，进入同步代码前要获得当前对象实例的锁 

修饰静态方法，作用于当前类对象加锁，进入同步代码前要获得当前类对象的锁 。也就是给当前类加锁，会作用于类的所有对象实例，因为静态成员不属于任何一个实例对象，是类成员（ static 表明这是该类的一个静态 资源，不管new了多少个对象，只有一份，所以对该类的所有对象都加了锁）。所以如果一个线程A调用一个实 例对象的非静态 synchronized 方法，而线程B需要调用这个实例对象所属类的静态 synchronized 方法，是允 许的，不会发生互斥现象，因为访问静态 synchronized 方法占用的锁是当前类的锁，而访问非静态 synchronized 方法占用的锁是当前实例对象锁。

修饰代码块，指定加锁对象，对给定对象加锁，进入同步代码库前要获得给定对象的锁。 和 synchronized 方 法一样，synchronized(this)代码块也是锁定当前对象的。synchronized 关键字加到 static 静态方法和 synchronized(class)代码块上都是是给 Class 类上锁。这里再提一下：synchronized关键字加到非 static 静态 方法上是给对象实例上锁。另外需要注意的是：尽量不要使用 synchronized(String a) 因为JVM中，字符串常量池具有缓冲功能！
 
3.synchronized和ReenTrantLock 的区别 
① 两者都是可重入锁
两者都是可重入锁。“可重入锁”概念是：自己可以再次获取自己的内部锁。比如一个线程获得了某个对象的锁，此时 这个对象锁还没有释放，当其再次想要获取这个对象的锁的时候还是可以获取的，如果不可锁重入的话，就会造成死 锁。同一个线程每次获取锁，锁的计数器都自增1，所以要等到锁的计数器下降为0时才能释放锁。 
② synchronized 依赖于 JVM 而 ReenTrantLock 依赖于 API synchronized 是依赖于 JVM 实现的，前面我们也讲到了 虚拟机团队在 JDK1.6 为 synchronized 关键字进行了很多 优化，但是这些优化都是在虚拟机层面实现的，并没有直接暴露给我们。ReenTrantLock 是 JDK 层面实现的（也就 是 API 层面，需要 lock() 和 unlock 方法配合 try/ﬁnally 语句块来完成），所以我们可以通过查看它的源代码，来看 它是如何实现的。
③ ReenTrantLock 比 synchronized 增加了一些高级功能 相比synchronized，ReenTrantLock增加了一些高级功能。主要来说主要有三点：①等待可中断；②可实现公平锁； 
③可实现选择性通知（锁可以绑定多个条件）
ReenTrantLock提供了一种能够中断等待锁的线程的机制，通过lock.lockInterruptibly()来实现这个机制。也 就是说正在等待的线程可以选择放弃等待，改为处理其他事情。 ReenTrantLock可以指定是公平锁还是非公平锁。而synchronized只能是非公平锁。所谓的公平锁就是先等 待的线程先获得锁。 ReenTrantLock默认情况是非公平的，可以通过 ReenTrantLock类的 ReentrantLock(boolean fair) 构造方法来制定是否是公平的。 synchronized关键字与wait()和notify/notifyAll()方法相结合可以实现等待/通知机制，ReentrantLock类当然也 可以实现，但是需要借助于Condition接口与newCondition() 方法。Condition是JDK1.5之后才有的，它具有很 好的灵活性，比如可以实现多路通知功能也就是在一个Lock对象中可以创建多个Condition实例（即对象监视 器），线程对象可以注册在指定的Condition中，从而可以有选择性的进行线程通知，在调度线程上更加灵 活。 在使用notify/notifyAll()方法进行通知时，被通知的线程是由 JVM 选择的，用ReentrantLock类结合 Condition实例可以实现“选择性通知” ，这个功能非常重要，而且是Condition接口默认提供的。而 synchronized关键字就相当于整个Lock对象中只有一个Condition实例，所有的线程都注册在它一个身上。如果 执行notifyAll()方法的话就会通知所有处于等待状态的线程这样会造成很大的效率问题，而Condition实例的 signalAll()方法 只会唤醒注册在该Condition实例中的所有等待线程。 如果你想使用上述功能，那么选择ReenTrantLock是一个不错的选择。
④ 性能已不是选择标准 
 
4.synchronized 关键字和 volatile 关键字的区别 
在当前 的 Java 内存模型下，线程可以把变量保存本地内存（比如机器的寄存器）中，而不是直接在主存中进行读写。这就 可能造成一个线程在主存中修改了一个变量的值，而另外一个线程还继续使用它在寄存器中的变量值的拷贝，造成数 据的不一致。
volatile 关键字的主要作用就是保证变量的可见性然后还有一个作用是防止指令重排序。
synchronized关键字和volatile关键字比较 volatile关键字是线程同步的轻量级实现，所以volatile性能肯定比synchronized关键字要好。
但是volatile关 键字只能用于变量而synchronized关键字可以修饰方法以及代码块。synchronized关键字在JavaSE1.6之后进 行了主要包括为了减少获得锁和释放锁带来的性能消耗而引入的偏向锁和轻量级锁以及其它各种优化之后执行 效率有了显著提升，实际开发中使用 synchronized 关键字的场景还是更多一些。 
多线程访问volatile关键字不会发生阻塞，而synchronized关键字可能会发生阻塞 volatile关键字能保证数据的可见性，但不能保证数据的原子性。synchronized关键字两者都能保证。 volatile关键字主要用于解决变量在多个线程之间的可见性，而 synchronized关键字解决的是多个线程之间访 问资源的同步性。 

5. 实现Runnable接口和Callable接口的区别 
如果想让线程池执行任务的话需要实现的Runnable接口或Callable接口。 Runnable接口或Callable接口实现类都可 以被ThreadPoolExecutor或ScheduledThreadPoolExecutor执行。两者的区别在于 Runnable 接口不会返回结果但 是 Callable 接口可以返回结果。

6.执行execute()方法和submit()方法的区别是什么呢？ 
1) execute() 方法用于提交不需要返回值的任务，所以无法判断任务是否被线程池执行成功与否；
2)submit()方法用于提交需要返回值的任务。线程池会返回一个future类型的对象，通过这个future对象可以判断 任务是否执行成功，并且可以通过future的get()方法来获取返回值，get()方法会阻塞当前线程直到任务完成，而使用 get（long timeout，TimeUnit unit）方法则会阻塞当前线程一段时间后立即返回，这时候有可能任务没有执行完。

7.Atomic
基本类型
使用原子的方式更新基本类型
AtomicInteger：整形原子类 AtomicLong：长整型原子类 AtomicBoolean ：布尔型原子类
数组类型
使用原子的方式更新数组里的某个元素
AtomicIntegerArray：整形数组原子类 AtomicLongArray：长整形数组原子类 AtomicReferenceArray ：引用类型数组原子类
引用类型
AtomicReference：引用类型原子类 AtomicStampedRerence：原子更新引用类型里的字段原子类 AtomicMarkableReference ：原子更新带有标记位的引用类型
对象的属性修改类型
AtomicIntegerFieldUpdater:原子更新整形字段的更新器
AtomicLongFieldUpdater：原子更新长整形字段的更新器 AtomicStampedReference ：原子更新带有版本号的引用类型。该类将整数值与引用关联起来，可用于解决原 子的更新数据和数据的版本号，可以解决使用 CAS 进行原子更新时可能出现的 ABA 问题。 
AtomicInteger 类主要利用 CAS (compare and swap) + volatile 和 native 方法来保证原子操作，从而避免 synchronized 的高开销，执行效率大为提升。 CAS的原理是拿期望的值和原本的一个值作比较，如果相同则更新成新的值。UnSafe 类的 objectFieldOﬀset() 方法 是一个本地方法，这个方法是用来拿到“原来的值”的内存地址，返回值是 valueOﬀset。另外 value 是一个volatile变 量，在内存中可见，因此 JVM 可以保证任何时刻任何线程总能拿到该变量的新值。

8.AQS
AQS是一个用来构建锁和同步器的框架，使用AQS能简单且高效地构造出应用广泛的大量的同步器，比如我们提到的 ReentrantLock，Semaphore，其他的诸如ReentrantReadWriteLock，SynchronousQueue，FutureTask等等皆是基于AQS的。当然，我们自己也能利用AQS非常轻松容易地构造出符合我们自己需求的同步器。

AQS核心思想是，如果被请求的共享资源空闲，则将当前请求资源的线程设置为有效的工作线程，并且将共享资源设 置为锁定状态。如果被请求的共享资源被占用，那么就需要一套线程阻塞等待以及被唤醒时锁分配的机制，这个机制 AQS是用CLH队列锁实现的，即将暂时获取不到锁的线程加入到队列中。

AQS定义两种资源共享方式 Exclusive（独占）：只有一个线程能执行，如ReentrantLock。又可分为公平锁和非公平锁： 公平锁：按照线程在队列中的排队顺序，先到者先拿到锁 非公平锁：当线程要获取锁时，无视队列顺序直接去抢锁，谁抢到就是谁的 Share（共享）：多个线程可同时执行，如Semaphore/CountDownLatch。Semaphore、 CountDownLatCh、 CyclicBarrier、ReadWriteLock 我们都会在后面讲到。 

三、JAVA虚拟机
--------------------- 

1.内存区域
线程隔离
1）程序计数器
当前线程所执行的字节码的行号指示器。
2）java虚拟机栈
生命周期与线程相同，描述的是java方法执行的内存模型，方法执行时会创建一个栈帧，
3）本地方法栈
与虚拟机栈发挥作用相似，但是为虚拟机用到的native方法服务。

线程共享
4）java堆
存放对象实例，是垃圾收集器管理的主要区域，也被称作GC区，Java堆中可以被细分为：新生代和老年代；再细致一点的有Eden空间、From Survivor空间、To Survivor空间等。 年轻代是所有新对象产生的地方。当年轻代内存空间被用完时，这时就会触发垃圾回收。这个垃圾回收叫做Minor GC。 
老年代内存里包含了长期存活的对象和经过多次Minor GC后依然存活下来的对象。通常会在老年代内存被占满时进行垃圾回收。老年代的垃圾收集叫做Major GC。这里注意，发生在老年代的垃圾收集也有人叫Full GC，这两个术语目前还没有正式的定义。但我更倾向于说永久代的垃圾收集是Full GC。
一个新的HashMap对象会被放到eden空间，当eden空间满了的时候，MinorGC就会执行,任何存活的对象，都从eden空间复制到“to” survivor空间，任何在“from” survivor空间里面的存活对象也会被复制到“to” survivor。MinorGC结束的时候，eden空间和“from” survivor空间都是空的，“to” survivor空间里面存储存活的对象，然后，在下次MinorGC的时候，两个survivor空间交换他们的标签，现在是空的“from” survivor标记成为“to”，“to” survivor标记为“from”。因此，在MinorGC结束的时候，eden空间是空的，两个survivor空间中的一个是空的。

- 伊甸园（Eden）：这是对象最初诞生的区域，并且对大多数对象来说，这里是它们唯一存在过的区域。 
- 幸存者乐园（Survivor）：从伊甸园幸存下来的对象会被挪到这里。 
- 终身颐养园（Tenured）：这是足够老的幸存对象的归宿。年轻代收集（Minor-GC）过程是不会触及这个地方的。当年轻代收集不能把对象放进终身颐养园时，就会触发一次完全收集（Major-GC），这里可能还会牵扯到压缩，以便为大对象腾出足够的空间。

5）方法区
存储已被虚拟机加载的类信息、常量、静态变量、即时编译器编译后的代码等数据。
运行时常量池是方法区的一部分。Class文件（也就是.java文件编译后生成的字节码.class文件）中除了有类的版本、字段、方法、接口等描述信息外，还有一项信息是常量池（Constant Pool Table）,用于存放编译期生成的各种字面量和符号引用（）。这部分内容将在类加载后进入方法区的运行时常量池中存放。
运行时常量池在JDK1.7被移到Java堆中

2.虚拟机垃圾收集器
Serial收集器 
单线程收集器，收集时会暂停所有工作线程（我们将这件事情称之为Stop The World，下称STW），使用复制收集算法，虚拟机运行在Client模式时的默认新生代收集器。 
ParNew收集器 
ParNew 收集器就是Serial的多线程版本，除了使用多条收集线程外，其余行为包括算法、STW、对象分配规则、回收策略等都与Serial收集器一摸一样。对 应的这种收集器是虚拟机运行在Server模式的默认新生代收集器，在单CPU的环境中，ParNew收集器并不会比Serial收集器有更好的效果。 
Parallel Scavenge收集器 
Parallel Scavenge收集器（下称PS收集器）也是一个多线程收集器，也是使用复制算法，但它的对象分配规则与回收策略都与ParNew收集器有所不同，它是 以吞吐量最大化（即GC时间占总运行时间最小）为目标的收集器实现，它允许较长时间的STW换取总吞吐量最大化。 
Serial Old收集器 
Serial Old是单线程收集器，使用标记－整理算法，是老年代的收集器，上面三种都是使用在新生代收集器。 
Parallel Old收集器 
老年代版本吞吐量优先收集器，使用多线程和标记－整理算法，JVM 1.6提供，在此之前，新生代使用了PS收集器的话，老年代除Serial Old外别无选择，因为PS无法与CMS收集器配合工作。 
CMS（Concurrent Mark Sweep）收集器 
CMS 是一种以最短停顿时间为目标的收集器，使用CMS并不能达到GC效率最高（总体GC时间最小），但它能尽可能降低GC时服务的停顿时间，这一点对于实时或 者高交互性应用（譬如证券交易）来说至关重要，这类应用对于长时间STW一般是不可容忍的。CMS收集器使用的是标记－清除算法，也就是说它在运行期间会 产生空间碎片，所以虚拟机提供了参数开启CMS收集结束后再进行一次内存压缩。 

3.类加载的机制 
加载
类加载指的是将class文件读入内存，并为之创建一个java.lang.Class对象，即程序中使用任何类时，系统都会为之建立一个java.lang.Class对象，系统中所有的类都是java.lang.Class的实例。
类的加载由类加载器完成，JVM提供的类加载器叫做系统类加载器，此外还可以通过继承ClassLoader基类来自定义类加载器。
通常可以用如下几种方式加载类的二进制数据：
从本地文件系统加载class文件。
从JAR包中加载class文件，如JAR包的数据库启驱动类。
通过网络加载class文件。
把一个Java源文件动态编译并执行加载。

连接
连接阶段负责把类的二进制数据合并到JRE中，其又可分为如下三个阶段：
验证：确保加载的类信息符合JVM规范，无安全方面的问题。
准备：为类的静态Field分配内存，并设置初始值。
解析：将类的二进制数据中的符号引用替换成直接引用。

初始化
该阶段主要是对静态Field进行初始化，在Java类中对静态Field指定初始值有两种方式：
声明时即指定初始值，如static int a = 5；
使用静态代码块为静态Field指定初始值，如：static{    b = 5;    } 
JVM初始化一个类包含如下几个步骤：
假如这个类还没有被加载和连接，则程序先加载并连接该类。
假如该类的直接父类还没有被初始化，则先初始化其直接父类。
假如类中有初始化语句，则系统依次执行这些初始化语句。
所以JVM总是最先初始化java.lang.Object类。

类初始化的时机（对类进行主动引用时）：
创建类的实例时（new、反射、反序列化）。
调用某个类的静态方法时。
使用某个类或接口的静态Field或对该Field赋值时。
使用反射来强制创建某个类或接口对应的java.lang.Class对象，如Class.forName("Person")
初始化某个类的子类时，此时该子类的所有父类都会被初始化。

4.双亲代理机制
是什么：双亲代理机制，是代理机模式中的一种，我们在加载一个类的时候，首先得到该类信息的是最底层的类加载器，“应用程序类加载器”，该加载器得到类“名称”（我在这里的理解就是类名）后不会立即加载，而是上抛给其parent，就这样一层层的上抛，当上抛至“引导类加载器”时如果该加载器中有和其一样的类名，则该类直接加载“自己”的该类到堆区，如果“引导加载器”中不存在与该类相同类类名，则一层层向下抛，如果在那一层发现与其相同的类名，则直接加载“该类加载器中的这个类”到堆区，如果直至应用程序类加载器还没有发现与该类同名的类，则抛出异常（注意：我们自己定义的类，在应用程序类加载器中都能找到相同的类名）；
作用：试想一下，你自己定义了一个java.lang.String类，那么你让Java核心库中了（java.lang.String）怎么办？你会把核心库中的String类覆盖掉吗？这当然时不现实的。Java核心库中的类是不可被覆盖的，也就是说，双亲代理机制，保护了Java中自带的类（不仅仅是Java核心库中的类）。也就是说，你可定义一个java.lang.String类，但是你永远都用不了该类，因为该类存在于Java核心库中（rt.jar）而引导加载器负责加载该类，所以你不论怎么调用，它到加载的时Java核心库中的String类。

5.垃圾回收算法
标记-清除算法
最基础的收集算法是“标记-清除”算法，算法分为“标记”和“清除”两个阶段：首先标记出所需要回收的对象，在标记完成后统一回收所有被标记的对象。
复制算法
为了解决效率问题，可以将内存按容量大小划分为大小相等的两块，每次只使用其中的一块。当这一块的内存用完了，就将还存活着的对象复制到另外一块上面，然后再把已经使用过的内存空间一次性清理掉，这就是“复制”算法。
标记-整理算法
复制算法在对象存活率较高时就要进行较多的复制操作，效率将会变低。特别在老年代，老年代一般不能直接选用这种算法，因此有人提出了另外一种“标记-整理”算法，标记过程仍然和“标记-清除”算法一样，但后续步骤不是直接对可回收对象进行整理，而是让所有存活的对象向一端移动，然后直接清理掉边界以外的内存。
分代收集除算法
当前商业虚拟机的垃圾收集都采用“分代收集”算法。一般将Java堆分成新生代和老年代，然后根绝各个年代的特点采用适当的手机算法。在新生代采用“复制”算法，在老年代采用“标记-清理”或“标记-整理”算法。 
Minor GC 是清理年轻代。
Major GC 是清理永久代。
Full  GC 是清理整个堆空间—包括年轻代和永久代。

四、数据结构和算法
--------------------- 

1.Queue 
什么是队列 
队列是数据结构中比较重要的一种类型，它支持 FIFO，尾部添加、头部删除（先进队列的元素先出队列），跟我们 生活中的排队类似。 队列的种类 
单队列（单队列就是常见的队列, 每次添加元素时，都是添加到队尾，存在“假溢出”的问题也就是明明有位置却 不能添加的情况） 循环队列（避免了“假溢出”的问题） Java 集合框架中的队列 Queue 
Java 集合中的 Queue 继承自 Collection 接口 ，Deque, LinkedList, PriorityQueue, BlockingQueue 等类都实现了 它。 Queue 用来存放 等待处理元素 的集合，这种场景一般用于缓冲、并发访问。 除了继承 Collection 接口的一些 方法，Queue 还添加了额外的 添加、删除、查询操作。  
boolean add(E e); // 添加元素到队列中，相当于进入队尾排队。  
boolean offer(E e);  //添加元素到队列中，相当于进入队尾排队.  
E remove(); //移除队头元素  
E poll();  //移除队头元素  
E element(); //获取但不移除队列头的元素  
E peek();  //获取但不移除队列头的元素  
offer，add 区别：
一些队列有大小限制，因此如果想在一个满的队列中加入一个新项，多出的项就会被拒绝。
这时新的 offer 方法就可以起作用了。它不是对调用 add() 方法抛出一个 unchecked 异常，而只是得到由 offer() 返回的 false。

poll，remove 区别：
remove() 和 poll() 方法都是从队列中删除第一个元素。remove() 的行为与 Collection 接口的版本相似， 但是新的 poll() 方法在用空集合调用时不是抛出异常，只是返回 null。因此新的方法更适合容易出现异常条件的情况。

peek，element区别：
element() 和 peek() 用于在队列的头部查询元素。与 remove() 方法类似，在队列为空时， element() 抛出一个异常，而 peek() 返回 null。


2.Set 
什么是 Set 
Set 继承于 Collection 接口，是一个不允许出现重复元素，并且无序的集合，主要 HashSet 和 TreeSet 两大实现 类。
在判断重复元素的时候，Set 集合会调用 hashCode()和 equal()方法来实现。 补充：有序集合与无序集合说明 
有序集合：集合里的元素可以根据 key 或 index 访问 (List、Map) 
无序集合：集合里的元素只能遍历。（Set） HashSet 和 TreeSet 底层数据结构 
HashSet 是哈希表结构，主要利用 HashMap 的 key 来存储元素，计算插入元素的 hashCode 来获取元素在集合中 的位置；
TreeSet 是红黑树结构，每一个元素都是树中的一个节点，插入的元素都会进行排序；
set
set是一个接口,一般实现类用HashSet

boolean    add(E e)
如果 set 中尚未存在指定的元素，则添加此元素（可选操作）。    
boolean    addAll(Collection<? extends E> c)
如果 set 中没有指定 collection 中的所有元素，则将其添加到此 set 中（可选操作）。    
void    clear()
移除此 set 中的所有元素（可选操作）。    
boolean    contains(Object o)
如果 set 包含指定的元素，则返回 true。    
boolean    containsAll(Collection<?> c)
如果此 set 包含指定 collection 的所有元素，则返回 true。    
boolean    equals(Object o)
比较指定对象与此 set 的相等性。    
int    hashCode()
返回 set 的哈希码值。    
boolean    isEmpty()
如果 set 不包含元素，则返回 true。    
Iterator<E>    iterator()
返回在此 set 中的元素上进行迭代的迭代器。    
boolean    remove(Object o)
如果 set 中存在指定的元素，则将其移除（可选操作）。    
boolean    removeAll(Collection<?> c)
移除 set 中那些包含在指定 collection 中的元素（可选操作）。    
boolean    retainAll(Collection<?> c)
仅保留 set 中那些包含在指定 collection 中的元素（可选操作）。    
int    size()
返回 set 中的元素数（其容量）。    
Object[]    toArray()
返回一个包含 set 中所有元素的数组。    
<T> T[]    toArray(T[] a)
返回一个包含此 set 
中所有元素的数组；返回数组的运行时类型是指定数组的类型。



3.List 
什么是List 
在 List 中，用户可以精确控制列表中每个元素的插入位置，另外用户可以通过整数索引（列表中的位置）访问元素， 并搜索列表中的元素。 与 Set 不同，List 通常允许重复的元素。 另外 List 是有序集合而 Set 是无序集合。 List的常见实现类 
ArrayList 是一个数组队列，相当于动态数组。它由数组实现，随机访问效率高，随机插入、随机删除效率低。 LinkedList 是一个双向链表。它也可以被当作堆栈、队列或双端队列进行操作。LinkedList随机访问效率低，但随机 插入、随机删除效率高。
Vector 是矢量队列，和ArrayList一样，它也是一个动态数组，由数组实现。但是ArrayList是非线程安全的，而 Vector是线程安全的。 Stack 是栈，它继承于Vector。它的特性是：先进后出(FILO, First In Last Out)。


list
        List list = new ArrayList();
        list.add("a");// 向集合中追加元素
        list.add(1, "b");// 向集合的制定位置中追加元素
        list.addAll(list);// 向集合追加一个collection，只可追加collection，由于java不提供collection的实现，由它的下级接口来实现
        list.addAll(4, list);// 与上述含义相同， “4”意为追加元素所放的位置
        int i = list.size();// 长度
        System.out.println(i);
        list.get(0);// 根据元素下标来取集合中的元素
        list.remove(7);// 根据集合中元素下标位置来删除元素
        // 此方法是用来比较的，与equals比较相似，现在list的元素中有[a, b, a, b, a, b, a],来和"a,b,c"比较会返回false，
        // 但是注意再用来比较String字符串的时候会进行局部的比较，两组字符串部分相同的情况下会返回true
        list.contains("a,b,c");
        //为了将List转为数组，JDK提供了toArray
        //实现方式一：
        String [] array=(String[]) list.toArray(new String[list.size()]);
        for(String arrays: array) {
            System.out.println(arrays);
        }
        //方式二：
        String [] arr=new String [list.size()];
        list.toArray(arr);
        for(String arrs: arr) {
            System.out.println(arrs);
        }
        //在集合中判断是否为空 ，不空返回false，空会返回true，常常会与null！=list来共同判定集合是否为空，
        //null！=list和list.isempty最大的区别是：一个人要喝水，前者判断是否有水杯，后者判断的是水杯是否有水
        System.out.println(list.isEmpty());//false
        System.out.println(null!=list);//true
        //该方法去比较两个对象时，首先先去判断两个对象是否具有相同的地址，如果是同一个对象的引用，则直接放回true；如果地址不一样，
        //则证明不是引用同一个对象，接下来就是挨个去比较两个字符串对象的内容是否一致，完全相等返回true，否则false。
        //这里会涉及到hashcode相关内容，我会单独开一篇来介绍
        list.equals(arr);//false
        //在集合中查找元素 ，"a"如果有 ,返回所查找元素的下标,如果不存在则返回-1
        list.indexOf("a");
        //打印集合元素
        //方式一：
        Iterator it=list.iterator();
        while(it.hasNext()) {
            String string=(String) it.next();
            System.out.println(string);
        }
        //方式二：
        for (Object o:list) {
            System.out.println(o);
        }
        //方式三：
        for(int s=0;s<list.size();s++) {
            System.out.println(list.get(s));
        }
        //将list释放，元素清空，且无返回值
        list.clear();
        System.out.println(list);
Stack
boolean empty() 
测试堆栈是否为空。
Object peek( )
查看堆栈顶部的对象，但不从堆栈中移除它。
Object pop( )
移除堆栈顶部的对象，并作为此函数的值返回该对象。
Object push(Object element)
把项压入堆栈顶部。
int search(Object element)
返回对象在堆栈中的位置，以 1 为基数。



4.树 
二叉树 
(1)完全二叉树——若设二叉树的高度为h，除第 h 层外，其它各层 (1～h-1) 的结点数都达到大个数，第h层有 叶子结点，并且叶子结点都是从左到右依次排布，这就是完全二叉树。 (2)满二叉树——除了叶结点外每一个结点都有左右子叶且叶子结点都处在底层的二叉树。 (3)平衡二叉树——平衡二叉树又被称为AVL树（区别于AVL算法），它是一棵二叉排序树，且具有以下性质：它 是一棵空树或它的左右两个子树的高度差的绝对值不超过1，并且左右两个子树都是一棵平衡二叉树。
完全二叉树 
叶节点只能出现在下层和次下层，并且下面一层的结点都集中在该层左边的若干位置的二叉树 
满二叉树 
一个二叉树，如果每一个层的结点数都达到大值，则这个二叉树就是满二叉树。也就是说， 如果一个二叉树的层数为K，且结点总数是(2^k) -1 ，则它就是满二叉树。 
堆 
数据结构之堆的定义 堆是具有以下性质的完全二叉树：每个结点的值都大于或等于其左右孩子结点的值，称为大顶堆；或者每个结 点的值都小于或等于其左右孩子结点的值，称为小顶堆 
二叉查找树（BST） 
二叉查找树的特点： 1. 若任意节点的左子树不空，则左子树上所有结点的 值均小于它的根结点的值； 2. 若任意节点的右子树不空，则右子树上所有结点的值均大于它的根结点的值； 3. 任意节点的左、右子树也分别为二叉查找树。 4. 没有键值相等的节点（no duplicate nodes）。 5 平衡二叉树（Self-balancing binary search tree） 
平衡二叉树（平衡二叉树的常用实现方法有红黑树、AVL、替罪羊树、Treap、伸展树等） 
红黑树 
红黑树特点: 1. 每个节点非红即黑； 2. 根节点总是黑色的； 3. 每个叶子节点都是黑色的空节点（NIL节点）； 4. 如果节点是红色的，则它的子节点必须是黑色的（反之不一定）； 5. 从根节点到叶节点或空子节点的每条路径，必须包含相同数目的黑色节点（即相同的黑色高度） 红黑树的应用： TreeMap、TreeSet以及JDK1.8之后的HashMap底层都用到了红黑树。 为什么要用红黑树 简单来说红黑树就是为了解决二叉查找树的缺陷，因为二叉查找树在某些情况下会退化成一个线性结构。
B-，B+，B*树 
B-树（或B树）是一种平衡的多路查找(又称排序)树，在文件系统中有所应用。主要用作文件的索引。其中的B 就表示平衡(Balance) 
1. B+ 树的叶子节点链表结构相比于 B- 树便于扫库，和范围检索。 
2. B+树支持range-query(区间查询)非常方便，而B树不支持。这是数据库选用B+树的主要原因。 3. B*树 是B+树的变体，B*树分配新结点的概率比B+树要低，空间使用率更高； 
LSM 树 
B+树大的性能问题是会产生大量的随机IO 为了克服B+树的弱点，HBase引入了LSM树的概念，即Log-Structured Merge-Trees。

排序算法
https://www.cnblogs.com/onepixel/articles/7674659.html

5.Map
void clear( )
 从此映射中移除所有映射关系（可选操作）。
boolean containsKey(Object k)
如果此映射包含指定键的映射关系，则返回 true。
boolean containsValue(Object v)
如果此映射将一个或多个键映射到指定值，则返回 true。
Set entrySet( )
返回此映射中包含的映射关系的 Set 视图。
boolean equals(Object obj)
比较指定的对象与此映射是否相等。
Object get(Object k)
返回指定键所映射的值；如果此映射不包含该键的映射关系，则返回 null。
int hashCode( )
返回此映射的哈希码值。
boolean isEmpty( )
如果此映射未包含键-值映射关系，则返回 true。
Set keySet( )
返回此映射中包含的键的 Set 视图。
Object put(Object k, Object v)
将指定的值与此映射中的指定键关联（可选操作）。
void putAll(Map m)
从指定映射中将所有映射关系复制到此映射中（可选操作）。
Object remove(Object k)
如果存在一个键的映射关系，则将其从此映射中移除（可选操作）。
int size( )
返回此映射中的键-值映射关系数。
Collection values( )
返回此映射中包含的值的 Collection 视图。



五、Spring
--------------------- 
				       
1.Spring 事务中的隔离级别 
TransactionDeﬁnition 接口中定义了五个表示隔离级别的常量： 
TransactionDeﬁnition.ISOLATION_DEFAULT: 使用后端数据库默认的隔离级别，Mysql 默认采用的 REPEATABLE_READ(可重复读)隔离级别 Oracle 默认采用的 READ_COMMITTED隔离级别. 
TransactionDeﬁnition.ISOLATION_READ_UNCOMMITTED（读/写不提交）: 低的隔离级别，允许读取尚未提交的数据变 更，可能会导致脏读、幻读或不可重复读 TransactionDeﬁnition.ISOLATION_READ_COMMITTED（读/写提交）: 允许读取并发事务已经提交的数据，可以阻止脏 读，但是幻读或不可重复读仍有可能发生 TransactionDeﬁnition.ISOLATION_REPEATABLE_READ（可重复读）: 对同一字段的多次读取结果都是一致的，除非数据 是被本身事务自己所修改，可以阻止脏读和不可重复读，但幻读仍有可能发生。 
TransactionDeﬁnition.ISOLATION_SERIALIZABLE（序列化）: 高的隔离级别，完全服从ACID的隔离级别。所有的事 务依次逐个执行，这样事务之间就完全不可能产生干扰，也就是说，该级别可以防止脏读、不可重复读以及幻 读。但是这将严重影响程序的性能。通常情况下也不会用到该级别。 

2.Spring 事务中的事务传播行为 
支持当前事务的情况：
TransactionDeﬁnition.PROPAGATION_REQUIRED（要求）： 如果当前存在事务，则加入该事务；如果当前没有事 务，则创建一个新的事务。 TransactionDeﬁnition.PROPAGATION_SUPPORTS（支持）： 如果当前存在事务，则加入该事务；如果当前没有事 务，则以非事务的方式继续运行。 TransactionDeﬁnition.PROPAGATION_MANDATORY（强制性的）： 如果当前存在事务，则加入该事务；如果当前没有 事务，则抛出异常。（mandatory：强制性）
不支持当前事务的情况：
TransactionDeﬁnition.PROPAGATION_REQUIRES_NEW： 创建一个新的事务，如果当前存在事务，则把当 前事务挂起。 TransactionDeﬁnition.PROPAGATION_NOT_SUPPORTED： 以非事务方式运行，如果当前存在事务，则把 当前事务挂起。 TransactionDeﬁnition.PROPAGATION_NEVER： 以非事务方式运行，如果当前存在事务，则抛出异常。
其他情况：
TransactionDeﬁnition.PROPAGATION_NESTED（嵌套的）： 如果当前存在事务，则创建一个事务作为当前事务的嵌套 事务来运行；如果当前没有事务，则该取值等价于TransactionDeﬁnition.PROPAGATION_REQUIRED。 

3.AOP
AOP思想的实现一般都是基于 代理模式 ，在JAVA中一般采用JDK动态代理模式，但是我们都知道，JDK动态代理模式 只能代理接口而不能代理类。因此，Spring AOP 会这样子来进行切换，因为Spring AOP 同时支持 CGLIB、 ASPECTJ、JDK动态代理。
如果目标对象的实现类实现了接口，Spring AOP 将会采用 JDK 动态代理来生成 AOP 代理类； 如果目标对象的实现类没有实现接口，Spring AOP 将会采用 CGLIB 来生成 AOP 代理类——不过这个选择过程 对开发者完全透明、开发者也无需关心。

4.IOC
生命周期执行的过程如下:
1) spring对bean进行实例化,默认bean是单例
2) spring对bean进行依赖注入
3) 如果bean实现了BeanNameAware接口,spring将bean的id传给setBeanName()方法
4) 如果bean实现了BeanFactoryAware接口,spring将调用setBeanFactory方法,将BeanFactory实例传进来
5) 如果bean实现了ApplicationContextAware()接口,spring将调用setApplicationContext()方法将应用上下文的引用传入
6) 如果bean实现了BeanPostProcessor接口,spring将调用它们的postProcessBeforeInitialization接口方法（开始实例化）
7) 如果bean实现了InitializingBean接口,spring将调用它们的afterPropertiesSet接口方法,类似的如果bean使用了init-method属性声明了初始化方法,改方法也会被调用
x)自定义初始化
8) 如果bean实现了BeanPostProcessor接口,spring将调用它们的postProcessAfterInitialization接口方法（实例化完成）
9) 此时bean已经准备就绪,可以被应用程序使用了,他们将一直驻留在应用上下文中,直到该应用上下文被销毁
10) 若bean实现了DisposableBean接口,spring将调用它的distroy()接口方法。同样的,如果bean使用了destroy-method属性声明了销毁方法,则该方法被调用
y)自定义销毁

六、SpringBoot
---------------------
1.Spring Boot 是 Spring 开源组织下的子项目，是 Spring 组件一站式解决方案，主要是简化了使用 Spring 的难度，简省了繁重的配置，提供了各种启动器，开发者能快速上手，内置了 Tomcat/ Jetty 等容器。

Spring Boot 的核心配置文件是 application 和 bootstrap 配置文件。
application 配置文件这个容易理解，主要用于 Spring Boot 项目的自动化配置。
bootstrap 配置文件有以下几个应用场景。
使用 Spring Cloud Config 配置中心时，这时需要在 bootstrap 配置文件中添加连接到配置中心的配置属性来加载外部配置中心的配置信息；
一些固定的不能被覆盖的属性；
一些加密/解密的场景；

注解
启动类上面的注解是@SpringBootApplication，它也是 Spring Boot 的核心注解，主要组合包含了以下 3 个注解：

@SpringBootConfiguration：组合了 @Configuration 注解，实现配置文件的功能。
@EnableAutoConfiguration：打开自动配置的功能，也可以关闭某个自动配置的选项，如关闭数据源自动配置功能：@SpringBootApplication(exclude = { DataSourceAutoConfiguration.class })。
@ComponentScan：Spring组件扫描。

2.运行 Spring Boot 的方式

1）打包用命令或者放到容器中运行

2）用 Maven/ Gradle 插件运行

3）直接执行 main 方法运行

七、设计模式
--------------------- 
				       
1.六大原则
1）开闭原则（Open Close Principle）
开闭原则的意思是：对扩展开放，对修改关闭。在程序需要进行拓展的时候，不能去修改原有的代码，实现一个热插拔的效果。简言之，是为了使程序的扩展性好，易于维护和升级。想要达到这样的效果，我们需要使用接口和抽象类，后面的具体设计中我们会提到这点。
2）里氏代换原则（Liskov Substitution Principle）
里氏代换原则是面向对象设计的基本原则之一。 里氏代换原则中说，任何基类可以出现的地方，子类一定可以出现。LSP 是继承复用的基石，只有当派生类可以替换掉基类，且软件单位的功能不受到影响时，基类才能真正被复用，而派生类也能够在基类的基础上增加新的行为。里氏代换原则是对开闭原则的补充。实现开闭原则的关键步骤就是抽象化，而基类与子类的继承关系就是抽象化的具体实现，所以里氏代换原则是对实现抽象化的具体步骤的规范。
3）依赖倒转原则（Dependence Inversion Principle）
这个原则是开闭原则的基础，具体内容：针对接口编程，依赖于抽象而不依赖于具体。
4）接口隔离原则（Interface Segregation Principle）
这个原则的意思是：使用多个隔离的接口，比使用单个接口要好。它还有另外一个意思是：降低类之间的耦合度。由此可见，其实设计模式就是从大型软件架构出发、便于升级和维护的软件设计思想，它强调降低依赖，降低耦合。
5）迪米特法则，又称最少知道原则（Demeter Principle）
最少知道原则是指：一个实体应当尽量少地与其他实体之间发生相互作用，使得系统功能模块相对独立。
6）合成复用原则（Composite Reuse Principle）
合成复用原则是指：尽量使用合成/聚合的方式，而不是使用继承。

2.单例模式
//懒汉式单例类.在第一次调用的时候实例化自己 
public class Singleton {
    private Singleton() {}
    private static Singleton single=null;
    //静态工厂方法 
    public static Singleton getInstance() {
         if (single == null) {  
             single = new Singleton();
         }  
        return single;
    }
}
//饿汉式单例类.在类初始化时，已经自行实例化 
public class Singleton1 {
    private Singleton1() {}
    private static final Singleton1 single = new Singleton1();
    //静态工厂方法 
    public static Singleton1 getInstance() {
        return single;
    }
}
//双重锁模式
public class Singleton {
    private Singleton() {}
    private static Singleton singleton=null;
    //静态工厂方法 
    public static Singleton getInstance() {
        if (singleton == null) { 
            //这里运行一些耗时的代码，则不包含于synchronized同步块中，提高效率
            synchronized (Singleton.class) {  
               if (singleton == null) {//因同步快只包含了建立实例的代码，则应再加入一个查空判断，故称双重锁 
                  singleton = new Singleton(); 
               }  
            }  
        }  
        return singleton;
    }
}


3.工厂模式
工厂模式（Factory Pattern）是 Java 中最常用的设计模式之一。这种类型的设计模式属于创建型模式，它提供了一种创建对象的最佳方式。
在工厂模式中，我们在创建对象时不会对客户端暴露创建逻辑，并且是通过使用一个共同的接口来指向新创建的对象。

4.抽象工厂模式
抽象工厂模式（Abstract Factory Pattern）是围绕一个超级工厂创建其他工厂。该超级工厂又称为其他工厂的工厂。这种类型的设计模式属于创建型模式，它提供了一种创建对象的最佳方式。
在抽象工厂模式中，接口是负责创建一个相关对象的工厂，不需要显式指定它们的类。每个生成的工厂都能按照工厂模式提供对象。

5.代理模式
在代理模式（Proxy Pattern）中，一个类代表另一个类的功能。这种类型的设计模式属于结构型模式。
在代理模式中，我们创建具有现有对象的对象，以便向外界提供功能接口。

6.观察者模式
当对象间存在一对多关系时，则使用观察者模式（Observer Pattern）。比如，当一个对象被修改时，则会自动通知它的依赖对象。观察者模式属于行为型模式。

7.模板模式
接口--抽象类---实现类   定义一个操作中算法的骨架。

Java Web开发的Model 1和Model 2分别指的是什么？ 
Model 1是以页面为中心的Java Web开发，使用JSP+JavaBean技术将页面显示逻辑和业务逻辑处理分开，JSP实现页面显示，JavaBean对象用来保存数据和实现业务逻辑。Model 2是基于MVC（模型-视图-控制器，Model-View-Controller）架构模式的开发模型，实现了模型和视图的彻底分离，利于团队开发和代码复用，如下图所示。


八、计算机网络
--------------------- 

从上往下，应用层，报文。传输层，报文段。网络层，数据报，链路层，帧，物理层比特流

物理层：通过媒介传输比特,确定机械及电气规范（比特Bit）

数据链路层：将比特组装成帧和点到点的传递（帧Frame）

网络层：负责数据包从源到宿的传递和网际互连（包PackeT）

传输层：提供端到端的可靠报文传递和错误恢复（段Segment）

会话层：建立、管理和终止会话（会话协议数据单元SPDU）

表示层：对数据进行翻译、加密和压缩（表示协议数据单元PPDU）

应用层：允许访问OSI环境的手段（应用协议数据单元APDU）

1.OSI七层模型：
物理层：数模转换与模数转换
数据链路层：物理寻址，比特流转换为逻辑电路。保证物理层的传输安全和减少错漏
网络层：分组传输，路由选择。承载数据链路层大而多的网络
传输层：分割数据，保证数据有效到达对端。将网络层过大的数据进行分割和差错
会话层：管理应用程序间通信。自动处理封装前4层的协议
表示层：压缩解压缩。使传输数据能在各个平台使用
应用层：统一协议

2.TCP/IP：
链路层：等
网络层：IP、ICMP、RIP
传输层：TCP、UDP
应用层：HTTP、FTP、NDS等

3.TCP、UDP 协议的区别
UDP 在传送数据之前不需要先建立连接，远地主机在收到 UDP 报文后，不需要给出任何确认。虽然 UDP 不提供可 靠交付，但在某些情况下 UDP 确是一种有效的工作方式（一般用于即时通信），比如： QQ 语音、 QQ 视频 、直 播等等
TCP 提供面向连接的服务。在传送数据之前必须先建立连接，数据传送结束后要释放连接。 TCP 不提供广播或多播 服务。由于 TCP 要提供可靠的，面向连接的运输服务（TCP的可靠体现在TCP在传递数据之前，会有三次握手来建立 连接，而且在数据传递时，有确认、窗口、重传、拥塞控制机制，在数据传完后，还会断开连接用来节约系统资 源），这一难以避免增加了许多开销，如确认，流量控制，计时器以及连接管理等。这不仅使协议数据单元的首部增 大很多，还要占用许多处理机资源。TCP 一般用于文件传输、发送和接收邮件、远程登录等场景。 

4.在浏览器中输入url地址 ->> 显示主页的过程

DNS协议：获取域名对应IP
TCP协议：与服务器建立TCP连接
IP协议：建立TCP连接时，需发送数据，在网络层使用IP协议
OPSF协议：IP数据包在路由器之间传播时，路由选择使用OPSF协议
ARP协议：路由器与服务器通信时，需将IP地址转换成MAC地址，使用ARP协议
HTTP协议：TCP连接建立完成后，使用HTTP协议访问网络

总体来说分为以下几个过程: 1. DNS解析 2. TCP连接 3. 发送HTTP请求 4. 服务器处理请求并返回HTTP报文 5. 浏览器解析渲染页面 6. 连接结束

5. HTTP长连接、短连接 
在HTTP/1.0中默认使用短连接。也就是说，客户端和服务器每进行一次HTTP操作，就建立一次连接，任务结束就中 断连接。当客户端浏览器访问的某个HTML或其他类型的Web页中包含有其他的Web资源（如JavaScript文件、图像 文件、CSS文件等），每遇到这样一个Web资源，浏览器就会重新建立一个HTTP会话。 而从HTTP/1.1起，默认使用长连接，用以保持连接特性。使用长连接的HTTP协议，会在响应头加入这行代码：Connection:keep-alive
在使用长连接的情况下，当一个网页打开完成后，客户端和服务器之间用于传输HTTP数据的TCP连接不会关闭，客 户端再次访问这个服务器时，会继续使用这一条已经建立的连接。Keep-Alive不会永久保持连接，它有一个保持时 间，可以在不同的服务器软件（如Apache）中设定这个时间。实现长连接需要客户端和服务端都支持长连接。
HTTP协议的长连接和短连接，实质上是TCP协议的长连接和短连接。 

6.三次握手( SYN,证明发送方到接收方的通道没有问题;ACK,证明接收方到发送方的通道没有问题）
SYN=1 , seq=x
SYN=1 , ACK=1 , seq=y , ack=x+1
ACK=1 , seq=x+1 , ack=y+1

为什么要三次握手?
三次握手的目的是建立可靠的通信信道，说到通讯，简单来说就是数据的发送与接收，而三次握手最主要的目的就是 双方确认自己与对方的发送与接收是正常的。
第一次握手：Client 什么都不能确认；Server 确认了对方发送正常 
第二次握手：Client 确认了：自己发送、接收正常，对方发送、接收正常；Server 确认了：自己接收正常，对方发 送正常
第三次握手：Client 确认了：自己发送、接收正常，对方发送、接收正常；Server 确认了：自己发送、接收正常， 对方发送接收正常
所以三次握手就能确认双发收发功能都正常，缺一不可。


7.四次挥手（是两次确认断开的过程）

FIN=1,seq=u
ACK=1,seq=v,ack=u+1

间隔时间将剩余的数据发送，发送量为w-v

FIN=1,ACK=1,seq=w,ack=u+1
ACK=1,seq=u+1,ack=w+1

为什么要四次挥手？
任何一方都可以在数据传送结束后发出连接释放的通知，待对方确认后进入半关闭状态。当另一方也没有数据再发送 的时候，则发出连接释放通知，对方确认后就完全关闭了TCP连接。
举个例子：A 和 B 打电话，通话即将结束后，A 说“我没啥要说的了”，B回答“我知道了”，但是 B 可能还会有要说的 话，A 不能要求 B 跟着自己的节奏结束通话，于是 B 可能又巴拉巴拉说了一通，后 B 说“我说完了”，A 回答“知道 了”，这样通话才算结束。

8.网络应用的模式及其特点。 
典型的网络应用模式大致有三类：B/S、C/S、P2P。其中B代表浏览器（Browser）、C代表客户端（Client）、S代表服务器（Server），P2P是对等模式，不区分客户端和服务器。
B/S应用模式中可以视为特殊的C/S应用模式，只是将C/S应用模式中的特殊的客户端换成了浏览器，因为几乎所有的系统上都有浏览器，那么只要打开浏览器就可以使用应用，没有安装、配置、升级客户端所带来的各种开销。
P2P应用模式中，成千上万台彼此连接的计算机都处于对等的地位，整个网络一般来说不依赖专用的集中服务器。网络中的每一台计算机既能充当网络服务的请求者，又对其它计算机的请求作出响应，提供资源和服务。通常这些资源和服务包括：信息的共享和交换、计算资源（如CPU的共享）、存储共享（如缓存和磁盘空间的使用）等，这种应用模式最大的阻力安全性、版本等问题，目前有很多应用都混合使用了多种应用模型，最常见的网络视频应用，它几乎把三种模式都用上了。

补充：要跟"电子商务模式"区分开，因为有很多人被问到这个问题的时候马上想到的是B2B（如阿里巴巴）、B2C（如当当、亚马逊、京东）、C2C（如淘宝、拍拍）、C2B（如威客）、O2O（如美团、饿了么）。对于这类问题，可以去百度上面科普一下。

9.Web Service（Web服务） 
从表面上看，Web Service就是一个应用程序，它向外界暴露出一个能够通过Web进行调用的API。这就是说，你能够用编程的方法透明的调用这个应用程序，不需要了解它的任何细节，跟你使用的编程语言也没有关系。例如可以创建一个提供天气预报的Web Service，那么无论你用哪种编程语言开发的应用都可以通过调用它的API并传入城市信息来获得该城市的天气预报。之所以称之为Web Service，是因为它基于HTTP协议传输数据，这使得运行在不同机器上的不同应用无须借助附加的、专门的第三方软件或硬件，就可相互交换数据或集成。

补充：这里必须要提及的一个概念是SOA（Service-Oriented Architecture，面向服务的架构），SOA是一种思想，它将应用程序的不同功能单元通过中立的契约联系起来，独立于硬件平台、操作系统和编程语言，使得各种形式的功能单元能够更好的集成。显然，Web Service是SOA的一种较好的解决方案，它更多的是一种标准，而不是一种具体的技术。

10.SOAP、WSDL、UDDI。  
- SOAP：简单对象访问协议（Simple Object Access Protocol），是Web Service中交换数据的一种协议规范。 
- WSDL：Web服务描述语言（Web Service Description Language），它描述了Web服务的公共接口。这是一个基于XML的关于如何与Web服务通讯和使用的服务描述；也就是描述与目录中列出的Web服务进行交互时需要绑定的协议和信息格式。通常采用抽象语言描述该服务支持的操作和信息，使用的时候再将实际的网络协议和信息格式绑定给该服务。 
- UDDI：统一描述、发现和集成（Universal Description, Discovery and Integration），它是一个基于XML的跨平台的描述规范，可以使世界范围内的企业在互联网上发布自己所提供的服务。简单的说，UDDI是访问各种WSDL的一个门面（可以参考设计模式中的门面模式）。


九、MySql
--------------------- 
	
1.：MyISAM与InnoDB
1）count运算上的区别：因为MyISAM缓存有表meta-data（行数等），因此在做COUNT时对于一个结构很好 的查询是不需要消耗多少资源的。而对于InnoDB来说，则没有这种缓存。 
2）是否支持事务和崩溃后的安全恢复： MyISAM 强调的是性能，每次查询具有原子性,其执行数度比InnoDB类型 更快，但是不提供事务支持。但是InnoDB 提供事务支持事务，外部键等高级数据库功能。 具有事务 (commit)、回滚(rollback)和崩溃修复能力(crash recovery capabilities)的事务安全(transaction-safe (ACID compliant))型表。 
3）是否支持外键： MyISAM不支持，而InnoDB支持。 
MyISAM更适合读密集的表，而InnoDB更适合写密集的的表。 在数据库做主从分离的情况下，经常选择MyISAM作 为主库的存储引擎。 一般来说，如果需要事务支持，并且有较高的并发读取频率(MyISAM的表锁的粒度太大，所以 当该表写并发量较高时，要等待的查询就会很多了)，InnoDB是不错的选择。如果你的数据量很大（MyISAM支持压 缩特性可以减少磁盘的空间占用），而且不需要支持事务时，MyISAM是好的选择。 

2.事物的特性(ACID）
1）原子性： 事务是小的执行单位，不允许分割。事务的原子性确保动作要么全部完成，要么完全不起作用；
2）一致性： 执行事务前后，数据保持一致，多个事务对同一个数据读取的结果是相同的； 
3）隔离性： 并发访问数据库时，一个用户的事务不被其他事务所干扰，各并发事务之间数据库是独立的； 
4）持久性: 一个事务被提交之后。它对数据库中数据的改变是持久的，即使数据库发生故障也不应该对其有任何影 响。
事务并发的问题：（不可重复读的重点是修改，幻读的重点在于新增或者删除。）
脏读（Dirty read）: 当一个事务正在访问数据并且对数据进行了修改，而这种修改还没有提交到数据库中，这 时另外一个事务也访问了这个数据，然后使用了这个数据。因为这个数据是还没有提交的数据，那么另外一个 事务读到的这个数据是“脏数据”，依据“脏数据”所做的操作可能是不正确的。 
丢失修改（Lost to modify）: 指在一个事务读取一个数据时，另外一个事务也访问了该数据，那么在第一个事 务中修改了这个数据后，第二个事务也修改了这个数据。这样第一个事务内的修改结果就被丢失，因此称为丢失修改。 例如：事务1读取某表中的数据A=20，事务2也读取A=20，事务1修改A=A-1，事务2也修改A=A-1， 终结果A=19，事务1的修改被丢失。
不可重复读（Unrepeatableread）: 指在一个事务内多次读同一数据。在这个事务还没有结束时，另一个事务 也访问该数据。那么，在第一个事务中的两次读数据之间，由于第二个事务的修改导致第一个事务两次读取的 数据可能不太一样。这就发生了在一个事务内两次读到的数据是不一样的情况，因此称为不可重复读。 
幻读（Phantom read）: 幻读与不可重复读类似。它发生在一个事务（T1）读取了几行数据，接着另一个并发事务（T2）插入了一些数据时。在随后的查询中，第一个事务（T1）就会发现多了一些原本不存在的记录，就 好像发生了幻觉一样，所以称为幻读。

3.隔离级别（MySQL InnoDB 存储引擎的默认支持的隔离级别是 REPEATABLE-READ（可重读））
READ-UNCOMMITTED(读取未提交)：最低的隔离级别，允许读取尚未提交的数据变更，可能会导致脏读、幻读或不可重复读 
READ-COMMITTED(读取已提交): 允许读取并发事务已经提交的数据，可以阻止脏读，但是幻读或不可重复读 仍有可能发生 
REPEATABLE-READ（可重复读）: 对同一字段的多次读取结果都是一致的，除非数据是被本身事务自己所修 改，可以阻止脏读和不可重复读，但幻读仍有可能发生。 SERIALIZABLE(可串行化): 高的隔离级别，完全服从ACID的隔离级别。所有的事务依次逐个执行，这样事务 之间就完全不可能产生干扰，也就是说，该级别可以防止脏读、不可重复读以及幻读。
需要注意的是：与 SQL 标准不同的地方在于InnoDB 存储引擎在 REPEATABLE-READ（可重读）事务隔离级别 下使用的是Next-Key Lock 锁算法，因此可以避免幻读的产生，这与其他数据库系统(如 SQL Server)是不同的。所以 说InnoDB 存储引擎的默认支持的隔离级别是 REPEATABLE-READ（可重读） 已经可以完全保证事务的隔离性要 求，即达到了 SQL标准的SERIALIZABLE(可串行化)隔离级别。 因为隔离级别越低，事务请求的锁越少，所以大部分数据库系统的隔离级别都是READ-COMMITTED(读取提交内 容):，但是你要知道的是InnoDB 存储引擎默认使用 REPEATABLE-READ（可重读）并不会有任何性能损失。
InnoDB 存储引擎在 分布式事务 的情况下一般会用到SERIALIZABLE(可串行化)隔离级别。 

4.SQL调优
慢日志定位慢查询SQL
使用explain分析该SQL
修改SQL或尽量让SQL走索引

5.索引
无索引时查询过程：
1）. 定位到记录所在的页:需要遍历双向链表，找到所在的页 
2）. 从所在的页内中查找相应的记录:由于不是根据主键查询，只能遍历所在页的单链表了 
有索引时：通过 “目录” 就可以很快地定位到对应的页 
底层结构采用二叉查找树，B树，B+树，主要为B+树

SELECT b.runoob_author, SUM(b.runoob_count) AS COUNT 
FROM runoob_tbl a , tcount_tbl b 
WHERE a.runoob_author = b.runoob_author
GROUP BY runoob_author 
HAVING COUNT > 20;
	
SELECT b.runoob_author, SUM(b.runoob_count) AS COUNT 
FROM runoob_tbl a JOIN tcount_tbl b 
ON a.runoob_author = b.runoob_author
GROUP BY runoob_author 
HAVING COUNT > 20;
	
十、Redis
--------------------- 
	
1. redis 简介 
简单来说 redis 就是一个数据库，不过与传统数据库不同的是 redis 的数据是存在内存中的，所以存写速度非常快， 因此 redis 被广泛应用于缓存方向。另外，redis 也经常用来做分布式锁。redis 提供了多种数据类型来支持不同的业 务场景。除此之外，redis 支持事务 、持久化、LUA脚本、LRU驱动事件、多种集群方案。 

2.为什么要用 redis /为什么要用缓存 
高性能：
假如用户第一次访问数据库中的某些数据。这个过程会比较慢，因为是从硬盘上读取的。将该用户访问的数据存在数缓存中，这样下一次再访问这些数据的时候就可以直接从缓存中获取了。操作缓存就是直接操作内存，所以速度相当快。如果数据库中的对应数据改变的之后，同步改变缓存中相应的数据即可
高并发：
直接操作缓存能够承受的请求是远远大于直接访问数据库的，所以我们可以考虑把数据库中的部分数据转移到缓存中去，这样用户的一部分请求会直接到缓存这里而不用经过数据库。

3.常用数据类型
1）String 
常用命令: set,get,decr,incr,mget 等。 String数据结构是简单的key-value类型，value其实不仅可以是String，也可以是数字。 常规key-value缓存应用； 常规计数：微博数，粉丝数等。 
2）Hash 
常用命令： hget,hset,hgetall 等。
Hash 是一个 string 类型的 ﬁeld 和 value 的映射表，hash 特别适合用于存储对象，后续操作的时候，你可以直接仅 仅修改这个对象中的某个字段的值。 比如我们可以Hash数据结构来存储用户信息，商品信息等等。比如下面我就用 hash 类型存放了我本人的一些信息：
3）List 
常用命令: lpush,rpush,lpop,rpop,lrange等
key=JavaUser293847 value={  “id”: 1,  “name”: “SnailClimb”,  “age”: 22,  “location”: “Wuhan, Hubei” }
list 就是链表，Redis list 的应用场景非常多，也是Redis重要的数据结构之一，比如微博的关注列表，粉丝列表， 消息列表等功能都可以用Redis的 list 结构来实现。 Redis list 的实现为一个双向链表，即可以支持反向查找和遍历，更方便操作，不过带来了部分额外的内存开销。
另外可以通过 lrange 命令，就是从某个元素开始读取多少个元素，可以基于 list 实现分页查询，这个很棒的一个功 能，基于 redis 实现简单的高性能分页，可以做类似微博那种下拉不断分页的东西（一页一页的往下走），性能高。 
4）Set 
常用命令： sadd,spop,smembers,sunion 等 set 对外提供的功能与list类似是一个列表的功能，特殊之处在于 set 是可以自动排重的。
当你需要存储一个列表数据，又不希望出现重复数据时，set是一个很好的选择，并且set提供了判断某个成员是否在 一个set集合内的重要接口，这个也是list所不能提供的。可以基于 set 轻易实现交集、并集、差集的操作。 比如：在微博应用中，可以将一个用户所有的关注人存在一个集合中，将其所有粉丝存在一个集合。Redis可以非常 方便的实现如共同关注、共同粉丝、共同喜好等功能。这个过程也就是求交集的过程，具体命令如下：
5）Sorted Set 
常用命令： zadd,zrange,zrem,zcard等 和set相比，sorted set增加了一个权重参数score，使得集合中的元素能够按score进行有序排列。
举例： 在直播系统中，实时排行信息包含直播间在线用户列表，各种礼物排行榜，弹幕消息（可以理解为按消息维 度的消息排行榜）等信息，适合使用 Redis 中的 SortedSet 结构进行存储。 

4.删除。
定期删除：redis默认是每隔 100ms 就随机抽取一些设置了过期时间的key，检查其是否过期，如果过期就删 除。注意这里是随机抽取的。为什么要随机呢？你想一想假如 redis 存了几十万个 key ，每隔100ms就遍历所 有的设置过期时间的 key 的话，就会给 CPU 带来很大的负载！ 
惰性删除 ：定期删除可能会导致很多过期 key 到了时间并没有被删除掉。所以就有了惰性删除。假如你的过期 key，靠定期删除没有被删除掉，还停留在内存里，除非你的系统去查一下那个 key，才会被redis给删除掉。这 就是所谓的惰性删除，也是够懒的哈！

5.Redis的一种持久化方式叫快照（snapshotting，RDB）,另一种方式是只追加文件（append-only ﬁle,AOF）
Redis创建快照之后，可以对快照进行 备份，可以将快照复制到其他服务器从而创建具有相同数据的服务器副本（Redis主从结构，主要用来提高Redis性 能），还可以将快照留在原地以便重启服务器的时候使用。
开启AOF持久化后每执行一条会更改Redis中的数据的命令，Redis就会将该命令写入硬盘中的AOF文件。AOF文件的 保存位置和RDB文件的位置相同，都是通过dir参数设置的，默认的文件名是appendonly.aof。

十一、Dubbo
--------------------- 
	
1.Apache Dubbo (incubating) |ˈdʌbəʊ| 是一款高性能、轻量级的开源Java RPC 框架，它提供了三大核心能力：面向 接口的远程方法调用，智能容错和负载均衡，以及服务自动注册和发现。简单来说 Dubbo 是一个分布式服务框架， 致力于提供高性能和透明化的RPC远程服务调用方案，以及SOA服务治理方案。 Dubbo 目前已经有接近 23k 的 Star ，Dubbo的Github 地址：https://github.com/apache/incubator-dubbo 。 另 外，在开源中国举行的2018年度受欢迎中国开源软件这个活动的评选中，Dubbo 更是凭借其超高人气仅次于 vue.js 和 ECharts 获得第三名的好成绩。
Dubbo 是由阿里开源，后来加入了 Apache 。正式由于 Dubbo 的出现，才使得越来越多的公司开始使用以及接受分 布式架构

2.作用
1）负载均衡——同一个服务部署在不同的机器时该调用那一台机器上的服务 
2）服务调用链路生成——随着系统的发展，服务越来越多，服务间依赖关系变得错踪复杂，甚至分不清哪个应用要在哪个应用之前启动，架构师都不能完整的描述应用的架构关系。Dubbo 可以为我们解决服务之间互相是如何调用的。 
3）服务访问压力以及时长统计、资源调度和治理——基于访问压力实时管理集群容量，提高集群利用率。 
4）服务降级——某个服务挂掉之后调用备用服务

3.分布式
分布式或者说 SOA 分布式重要的就是面向服务，说简单的分布式就是我们把整个系统拆分成不同的服务然后将这些 服务放在不同的服务器上减轻单体服务的压力提高并发量和性能。比如电商系统可以简单地拆分成订单系统、商品系 统、登录系统等等，拆分之后的每个服务可以部署在不同的机器上，如果某一个服务的访问量比较大的话也可以将这 个服务同时部署在多台机器上。 
从开发角度来讲单体应用的代码都集中在一起，而分布式系统的代码根据业务被拆分。所以，每个团队可以负责一个 服务的开发，这样提升了开发效率。另外，代码根据业务拆分之后更加便于维护和扩展。
另外，我觉得将系统拆分成分布式之后不光便于系统扩展和维护，更能提高整个系统的性能

4.dubbo的健壮性表现： 
1）监控中心宕掉不影响使用，只是丢失部分采样数据 
2）数据库宕掉后，注册中心仍能通过缓存提供服务列表查询，但不能注册新服务 
3）注册中心对等集群，任意一台宕掉后，将自动切换到另一台 
4）注册中心全部宕掉后，服务提供者和服务消费者仍能通过本地缓存通讯 
5）服务提供者无状态，任意一台宕掉后，不影响使用 
6）服务提供者全部宕掉后，服务消费者应用将无法使用，并无限次重连等待服务提供者恢复

十二、消息队列
--------------------- 
1.我们可以把消息队列比作是一个存放消息的容器，当我们需要使用消息的时候可以取出消息供自己使用。消息队列是分布式系统中重要的组件，使用消息队列主要是为了通过异步处理提高系统性能和削峰、降低系统耦合性。目前使用较多的消息队列有ActiveMQ，RabbitMQ，Kafka，RocketMQ，我们后面会一一对比这些消息队列。  另外，我们知道队列 Queue 是一种先进先出的数据结构，所以消费消息时也是按照顺序来消费的。比如生产者发送消息1,2,3...对于消费者就会按照1,2,3...的顺序来消费。但是偶尔也会出现消息被消费的顺序不对的情况，比如某个消息消费失败又或者一个 queue 多个consumer 也会导致消息被消费的顺序不对，我们一定要保证消息被消费的顺序正确。
除了上面说的消息消费顺序的问题，使用消息队列，我们还要考虑如何保证消息不被重复消费？如何保证消息的 可靠性传输（如何处理消息丢失的问题）？......等等问题。所以说使用消息队列也不是十全十美的，使用它也会让系 统可用性降低、复杂度提高，另外需要我们保障一致性等问题。

2.为什么要用消息队列
1)通过异步处理提高系统性能（削峰、减少响应所需时间)
2)降低系统耦合性

3.JMS（JAVA Message Service,java消息服务）是java的消息服务，JMS的客户端之间可以通过JMS服务进行异步的 消息传输。JMS（JAVA Message Service,Java消息服务）API是一个消息服务的标准或者说是规范，允许应用程序 组件基于JavaEE平台创建、发送、接收和读取消息。它使分布式通信耦合度更低，消息服务更加可靠以及异步性。 ActiveMQ 就是基于 JMS 规范实现的。 

4.AMQP，即Advanced Message Queuing Protocol,一个提供统一消息服务的应用层标准 高级消息队列协议（二 进制应用层协议），是应用层协议的一个开放标准,为面向消息的中间件设计，兼容 JMS。基于此协议的客户端与消 息中间件可传递消息，并不受客户端/中间件同产品，不同的开发语言等条件的限制。
RabbitMQ 就是基于 AMQP 协议实现的。 
总结：
AMQP 为消息定义了线路层（wire-level protocol）的协议，而JMS所定义的是API规范。在 Java 体系中，多个 client均可以通过JMS进行交互，不需要应用修改代码，但是其对跨平台的支持较差。而AMQP天然具有跨平 台、跨语言特性。 JMS 支持TextMessage、MapMessage 等复杂的消息类型；而 AMQP 仅支持 byte[] 消息类型（复杂的类型可 序列化后发送）。 由于Exchange 提供的路由算法，AMQP可以提供多样化的路由方式来传递消息到消息队列，而 JMS 仅支持 队 列 和 主题/订阅 方式两种。 

十三、Linux
--------------------- 

1.在Linux操作系统中，所有被操作系统管理的资源，例如网络接口卡、磁盘驱动器、打印机、输入输出设备、普通文件或是目录都被看作是一个文件。
也就是说在LINUX系统中有一个重要的概念：一切都是文件。其实这是UNIX哲学的一个体现，而Linux是重写UNIX而 来，所以这个概念也就传承了下来。在UNIX系统中，把一切资源都看作是文件，包括硬件设备。UNIX系统把每个硬件都看成是一个文件，通常称为设备文件，这样用户就可以用读写文件的方式实现对硬件的访问。

2.常见目录说明：
/bin： 存放二进制可执行文件(ls,cat,mkdir等)，常用命令一般都在这里； 
/etc： 存放系统管理和配置文件； 
/home： 存放所有用户文件的根目录，是用户主目录的基点，比如用户user的主目录就是/home/user，可以 用~user表示； 
/usr ： 用于存放系统应用程序； 
/opt： 额外安装的可选应用程序包所放置的位置。一般情况下，我们可以把tomcat等都安装到这里； 
/proc： 虚拟文件系统目录，是系统内存的映射。可直接访问这个目录来获取系统信息； 
/root： 超级用户（系统管理员）的主目录（特权阶级^o^）； 
/sbin: 存放二进制可执行文件，只有root才能访问。这里存放的是系统管理员使用的系统级别的管理命令和程 序。如ifconﬁg等； 
/dev： 用于存放设备文件； 
/mnt： 系统管理员安装临时文件系统的安装点，系统提供这个目录是让用户临时挂载其他的文件系统； 
/boot： 存放用于系统引导时使用的各种文件； 
/lib ： 存放着和系统运行相关的库文件 ； 
/tmp： 用于存放各种临时文件，是公用的临时文件存储点； 
/var： 用于存放运行时需要改变数据的文件，也是某些大文件的溢出区，比方说各种服务的日志文件（系统启 动日志等。）等； 
/lost+found： 这个目录平时是空的，系统非正常关机而留下“无家可归”的文件（windows下叫什么.chk）就在 这里。 

3常用命令.
目录切换命令
cd usr ： 切换到该目录下usr目录 
cd ..（或cd../）： 切换到上一层目录 
cd / ： 切换到系统根目录 
cd ~ ： 切换到用户主目录 
cd -： 切换到上一个所在目录

目录的操作命令（增删改查）
1. mkdir 目录名称： 增加目录
2. ls或者ll （ll是ls -l的缩写，ll命令以看到该目录下的所有目录和文件的详细信息）：查看目录信息 
3. find 目录 参数： 寻找目录（查） 
4. mv 目录名称 新目录名称： 修改目录的名称（改） 注意：mv的语法不仅可以对目录进行重命名而且也可以对各种文件，压缩包等进行 重命名的操作。mv命令用 来对文件或目录重新命名，或者将文件从一个目录移到另一个目录中。后面会介绍到mv命令的另一个用法。 
5. mv 目录名称 目录的新位置： 移动目录的位置---剪切（改） 注意：mv语法不仅可以对目录进行剪切操作，对文件和压缩包等都可执行剪切操作。另外mv与cp的结果不 同，mv好像文件“搬家”，文件个数并未增加。而cp对文件进行复制，文件个数增加了。 
6. cp -r 目录名称 目录拷贝的目标位置： 拷贝目录（改），-r代表递归拷贝 注意：cp命令不仅可以拷贝目录还可以拷贝文件，压缩包等，拷贝文件和压缩包时不 用写-r递归 
7. rm [-rf] 目录: 删除目录（删） 注意：rm不仅可以删除目录，也可以删除其他文件或压缩包，为了增强大家的记忆， 无论删除任何目录或文 件，都直接使用 rm -rf 目录/文件/压缩包

文件的操作命令（增删改查）
1. touch 文件名称: 文件的创建（增） 
2. cat/more/less/tail 文件名称 文件的查看（查） cat ： 只能显示后一屏内容 more ： 可以显示百分比，回车可以向下一行， 空格可以向下一页，q可以退出查看 less ： 可以使用键盘上的PgUp和PgDn向上 和向下翻页，q结束查看 tail-10 ： 查看文件的后10行，Ctrl+C结束 注意：命令 tail -f 文件 可以对某个文件进行动态监控，例如tomcat的日志文件， 会随着程序的运行，日志会变 化，可以使用tail -f catalina-2016-11-11.log 监控 文 件的变化 
3. vim 文件： 修改文件的内容（改） vim编辑器是Linux中的强大组件，是vi编辑器的加强版，vim编辑器的命令和快捷方式有很多，但此处不一一阐 述，大家也无需研究的很透彻，使用vim编辑修改文件的方式基本会使用就可以了。 在实际开发中，使用vim编辑器主要作用就是修改配置文件，下面是一般步骤： vim 文件------>进入文件----->命令模式------>按i进入编辑模式----->编辑文件 ------->按Esc进入底行模式----->输 入:wq/q! （输入wq代表写入内容并退出，即保存；输入q!代表强制退出不保存。） 
4. rm -rf 文件： 删除文件（删） 同目录删除：熟记 rm -rf 文件 即可

压缩文件的操作命令
1）打包并压缩文件： Linux中的打包文件一般是以.tar结尾的，压缩的命令一般是以.gz结尾的。 而一般情况下打包和压缩是一起进行的，打包并压缩后的文件的后名一般.tar.gz。 命令： 
tar -zcvf 打包压缩后的 文件名 要打包压缩的文件 其中：
z：调用gzip压缩命令进行压缩 
c：打包文件
v：显示运行过程 
f：指定文件名
比如：加入test目录下有三个文件分别是 :aaa.txt bbb.txt ccc.txt,如果我们要打包test目录并指定压缩后的压缩包名 称为test.tar.gz可以使用命令： tar -zcvf test.tar.gz aaa.txt bbb.txt ccc.txt 或： tar -zcvf test.tar.gz /test/

2）解压压缩包：
命令：tar [-xvf] 压缩文件 其中：x：代表解压
示例：
1 将/test下的test.tar.gz解压到当前目录下可以使用命令： tar -xvf test.tar.gz
2 将/test下的test.tar.gz解压到根目录/usr下: tar -xvf xxx.tar.gz -C /usr （- C代表指定解压的位置）
其他常用命令
pwd ： 显示当前所在位置 grep 要搜索的字符串 要搜索的文件 
--color ： 搜索命令，--color代表高亮显示 
ps -ef / ps aux ： 这两个命令都是查看当前系统正在运行进程，两者的区别是展示格式不同。如果想要查看 特定的进程可以使用这样的格式： 
ps aux|grep redis （查看包括redis字符串的进程） 注意：如果直接用ps（（Process Status））命令，会显示所有进程的状态，通常结合grep命令查看某进程的 状态。 
kill -9 进程的pid ： 杀死进程（-9 表示强制终止。） 先用ps查找进程，然后用kill杀掉 网络通信命令： 查看当前系统的网卡信息：
ifconﬁg 查看与某台机器的连接情况：
ping 查看当前系统的端口使用：
netstat -an shutdown ： shutdown -h now ： 指定现在立即关机；
shutdown +5 "System will shutdown after 5 minutes" :指定5分钟后关机，同时送出警告信息给登入用户。 
reboot ： reboot ： 重开机。 
reboot -w ： 做个重开机的模拟（只有纪录并不会真的重开机）。

4.Make
./configure 是用来检测你的安装平台的目标特征的。比如它会检测你是不是有CC或GCC，并不是需要CC或GCC，它是个shell脚本。
make 是用来编译的，它从Makefile中读取指令，然后编译。
make install是用来安装的，它也从Makefile中读取指令，安装到指定的位置。
-k:它的作用是让make命令在发现错误时仍然继续执行，而不是在检测到第一个错误时就停下来。 
-n:它的作用是让make命令输出将要执行的操作步骤，而不真正执行这些操作 
-f :它的作用是告诉make命令将哪个文件作为makefile文件。如果未使用这个选项，标准版本的make 

5.127.0.0.1是回送地址，可以测试本地TCP/IP协议是否可用；
10.0.0.1是内部地址，与172.15.*.*-172.31.*.*    
192.168.*.*一样，内部网用的地址，不会出现在公网Internet上；
250.0.0.1百度查询，当时分配IP地址时，留了一部分做实验用。
三者的共同点都是不会出现在Internet上，都是比较特殊的那一部分IP地址。
	
`````````


### 下一阶段的学习方向

学习java互联网开发相关知识（已完成）

学习设计模式、java多线程开发、java虚拟机（已完成）

巩固计算机网络、数据库、Linux、服务器架构等相关知识（正在进行）

学习并搭建一个SSM框架的项目（已完成）
    利用ajax实现前后端分离，前端使用angularJS后端使用SpringMVC进行数据交互
    利用Session实现身份验证，利用Cookies实现免密登录
    利用websocket及JavaScript轮询共同实现实时通知功能 

学习并搭建一个SpringBoot项目（已完成）
    利用springboot集成mybatis，redis进行开发
    进行两次MD5加密，防止http数据泄露与彩虹表破解
    利用Result类与统一异常处理统一返回数据格式
    利用远程Redis与cookies实现分布式session       
    利用validator实现注解开发校验功能
    //利用thymeleafViewResolver静态化页面并缓存进redis中，提高性能（将一些可以摘出的验证步骤至于redis中，提高效率）
    利用html+ajax实现前后端分离
    使用rabbitmq接收消息并放置于消息队列中，再依次进行Sql操作，提高效率
    利用java图形生成功能在服务端生成验证图片，并将验证结果存储于redis中，完成验证功能
    建立拦截器完成限流防刷
    
进一步巩固SSM相关的知识并以此搭建一个博客

搭建一个SpringCould项目

### BUG记录

目前的多数BUG来自于jar包的引用错误和最初设计业务时的逻辑错误，引以为戒。


xml均报错“Referenced file contains errors (http://mybatis.org/dtd/mybatis/mybatis-3-config.dtd)”
在mapping下的xml文件中将http://mybatis.org/dtd/mybatis-3-mapper.dtd替换成http://www.mybatis.org/dtd/mybatis-3-mapper.dtd,报错解决。

SpringBoot内置hibernate执行插入语句报错 SQL Error: 1062, SQLState: 23000，
设置其他索引错误，导致非主键相同也无法插入，反而变成更改。

实现java接口@Override报错
因为使用maven创建项目的原因，maven默认的jdk版本为1.5是不支持接口实现时使用@Override注解的

controller中普通请求被thymeleaf拦截，报错显示找不到页面
Whitelabel Error Page
This application has no explicit mapping for /error, so you are seeing this as a fallback.
忘记使用@ResponseBody

连接远程服务器redis Jedis连接失败 Could not get a resource from the pool] with root cause
远程服务器防火墙设置6397端口可以连入

浮点数不能用来表示精确的值，如货币,可以使用整数以分为单位表示
因为二进制只能表示2的n次方的数，n可以取负值，3.3无法用2的n次方的数组合计算出来，所以无法精确表示：3.3=1*2+1*1+0*1/2+1*1/4+0*1/8+0*1/16+1*1/32+...
其中分式的分母只能是2的倍数(二进制所限)，3.3的二进制表示是11.01001.....
有些数比如1/3就无法精确计算，只能无限逼近

使用ctrl  +  F  搜索页面内内容
springboot使用thymeleaf无法加载静态资源
由原来继承WebMvcConfigurationSupport 现需要改成：实现WebMvcConfigurer 

为了应对在SpringBoot中的高并发及优化访问速度，我们一般会把页面上的数据查询出来，然后放到redis中进行缓存。减少数据库的压力。

在SpringBoot 1.X的版本中
SpringWebContext ctx=new SpringWebContext(request,response,request.getServletContext(),request.getLocale(),model.asMap(),applicationContext);
thymeleafViewResolver.getTemplateEngine().process(“goodlist”, ctx);
但在SpringBoot 2.0中，就无法找到SpringWebContext了,改为
WebContext ctx = new WebContext(request, response, request.getServletContext(), request.getLocale(), model.asMap());
html = thymeleafViewResolver.getTemplateEngine().process(“goodlist”, ctx);

Linux下启动rabbitmq报错:./rabbitmq-server: line 80: erl: command not found
在linux的/etc/profile环境下添加如下两行代码:（PATH是要根据自己的安装路径来确定）
#set erlang environment 
export PATH=$PATH:/usr/local/erlang20/bin
#set rabbitmq environment 
export PATH=$PATH:/usr/local/rabbitmq/sbin
然后输入下面的代码使profile文件修改生效
source /etc/profile

erlang安装失败
应配置环境yum -y install gcc glibc-devel make ncurses-devel openssl-devel xmlto perl wget

spring.resources.cache-period spring.resources.chain.gzipped作废解决办法
换成spring.resources.cache.period和 spring.resources.chain.compressed用

SpringBoot集成rabbitmq错误:org.springframework.amqp.AmqpConnectException: java.net.ConnectException的解决办法
用户使用的是guest,而guest只能默认只能连接本机IP(也就是127.0.0.1)，而192.168.220.128是虚拟机的ip，所以会报org.springframework.amqp.AmqpConnectException: java.net.ConnectException: Connection refused: connect
解决方法：就是修改rabbitmq的配置文件rabbitmq.config 增加一行代码[{rabbit,[{loopback_users,[]}]}]
也可以
#添加用户
#./rabbitmqctl add_user 账号 密码
./rabbitmqctl add_user admin admin
#分配用户标签(admin为要赋予administrator权限的刚创建的那个账号的名字)
./rabbitmqctl set_user_tags admin administrator
#设置权限<即开启远程访问>(如果需要远程连接,例如java项目中需要调用mq,则一定要配置,否则无法连接到mq,admin为要赋予远程访问权限的刚创建的那个账号的名字,必须运行着rabbitmq此命令才能执行)
./rabbitmqctl set_permissions -p "/" admin ".*" ".*" ".*" 

rabbitmq莫名退出的问题解决
正确的启动方式：rabbitmq-server  -detached

spring依赖注入是基于动态代理实现的，所以不能自己注入自己的内容，会形成循环调用
例如 
@service
class a{	
@Autowired
B b;
@Bean
B bfactory(){ return new B();}	
}

Illegal overloaded getter method with ambiguous type for property报错
以上问题是因为mybatis内部在进行Java反射的时候出现的问题，那么为什么会出现，因为Java会把Boolean类型的getter方法默认为is打头的或者是get打头的
public Integer getTradeType() 和
public boolean isTradeType() 同时存在
类似以上的方法存在，那么就要注意了，把boolean 的isTradeType方法重命名一下，如换成typeOfTradeType这样就好了，Java在反射的时候就不会区分不清是什么属性。

mysql新建order表，相关操作均报错。。。。order为sql关键词。。。。注意检查相关事项

### 问题总结

```markdown
一、JAVA部分
1.接口中默认修饰变量属性用：public static final；而默认方法的修饰符是：public abstract
例：public interface IService {
String NAME="default";
}等价public static final String NAME=”default”;
解：
public：因为接口必然是要被实现的，如果不是public，这个属性就没有意义了；
static：因为如果不是static（在内存中只有一份），那么由于每个类可以继承多个接口，那就会出现重名的情况；
final：这是为了体现java的开闭原则，因为接口是一种模板，既然是模板，那就对修改关闭，对扩展开放。

2.String 不是最基本的数据类型 
Java中的基本数据类型只有8个：byte、short、int、long、float、double、char、boolean；除了基本类型（primitive type），剩下的都是引用类型（reference type），Java 5以后引入的枚举类型也算是一种比较特殊的引用类型。

3. += 中有隐含的强制类型转换
  short s1 = 1; s1 = s1 + 1;报错
  short s1 = 1; s1 += 1;不报错 
对于short s1 = 1; s1 = s1 + 1;由于1是int类型，因此s1+1运算结果也是int 型，需要强制转换类型才能赋值给short型。而short s1 = 1; s1 += 1;可以正确编译，因为s1+= 1;相当于s1 = (short)(s1 + 1);其中有隐含的强制类型转换。


4.      Integer a = new Integer(3);
        Integer b = 3;              // 将3自动装箱成Integer类型
        int c = 3;
        System.out.println(a == b); // false 两个引用没有引用同一对象
        System.out.println(a == c); // true a自动拆箱成int类型再和c比较
        
        Integer f1 = 100, f2 = 100, f3 = 150, f4 = 150;

        System.out.println(f1 == f2); // true 如果整型字面量的值在-128到127之间，那么不会new新的Integer对象，而是直接引用常量池中的Integer对象
        System.out.println(f3 == f4); // false

5.&和&&的区别 
&运算符有两种用法：(1)按位与；(2)逻辑与。&&运算符是短路与运算。逻辑与跟短路与的差别是非常巨大的，虽然二者都要求运算符左右两端的布尔值都是true整个表达式的值才是true。
&&之所以称为短路运算是因为，如果&&左边的表达式的值是false，右边的表达式会被直接短路掉，不会进行运算。很多时候我们可能都需要用&&而不是&，例如在验证用户登录时判定用户名不是null而且不是空字符串，应当写为：username != null &&!username.equals("")，二者的顺序不能交换，更不能用&运算符，因为第一个条件如果不成立，根本不能进行字符串的equals比较，否则会产生NullPointerException异常。注意：逻辑或运算符（|）和短路或运算符（||）的差别也是如此。

6.解释内存中的栈(stack)、堆(heap)和方法区(method area)的用法。 
通常我们定义一个基本数据类型的变量，一个对象的引用，还有就是函数调用的现场保存都使用JVM中的栈空间；而通过new关键字和构造器创建的对象则放在堆空间，堆是垃圾收集器管理的主要区域，由于现在的垃圾收集器都采用分代收集算法，所以堆空间还可以细分为新生代和老生代，再具体一点可以分为Eden、Survivor（又可分为From Survivor和To Survivor）、Tenured；方法区和堆都是各个线程共享的内存区域，用于存储已经被JVM加载的类信息、常量、静态变量、JIT编译器编译后的代码等数据；程序中的字面量（literal）如直接书写的100、"hello"和常量都是放在常量池中，常量池是方法区的一部分。栈空间操作起来最快但是栈很小，通常大量的对象都是放在堆空间，栈和堆的大小都可以通过JVM的启动参数来进行调整，栈空间用光了会引发StackOverflowError，而堆和常量池空间不足则会引发OutOfMemoryError。

String str = new String("hello");
上面的语句中变量str放在栈上，用new创建出来的字符串对象放在堆上，而"hello"这个字面量是放在方法区的。

补充1：较新版本的Java（从Java 6的某个更新开始）中，由于JIT编译器的发展和"逃逸分析"技术的逐渐成熟，栈上分配、标量替换等优化技术使得对象一定分配在堆上这件事情已经变得不那么绝对了。
补充2：运行时常量池相当于Class文件常量池具有动态性，Java语言并不要求常量一定只有编译期间才能产生，运行期间也可以将新的常量放入池中，String类的intern()方法

7.Math.round(11.5) 等于多少？Math.round(-11.5)等于多少？ 
	答：Math.round(11.5)的返回值是12，Math.round(-11.5)的返回值是-11。四舍五入的原理是在参数上加0.5然后进行下取整。
	
8.用最有效率的方法计算2乘以8？ 
	答： 2 << 3（左移3位相当于乘以2的3次方，右移3位相当于除以2的3次方）。
	补充：我们为编写的类重写hashCode方法时，可能会看到如下所示的代码，其实我们不太理解为什么要使用这样的乘法运算来产生哈希码（散列码），而且为什么这个数是个素数，为什么通常选择31这个数？前两个问题的答案你可以自己百度一下，选择31是因为可以用移位和减法运算来代替乘法，从而得到更好的性能。说到这里你可能已经想到了：31 * num 等价于(num << 5) - num，左移5位相当于乘以2的5次方再减去自身就相当于乘以31，现在的VM都能自动完成这个优化。
	
9.switch 是否能作用在byte 上，是否能作用在long 上，是否能作用在String上？ 
	答：在Java 5以前，switch(expr)中，expr只能是byte、short、char、int。从Java 5开始，Java中引入了枚举类型，expr也可以是enum类型，从Java 7开始，expr还可以是字符串（String），但是长整型（long）在目前所有的版本中都是不可以的。
	
10.重载（Overload）和重写（Override）的区别。重载的方法能否根据返回类型进行区分？ 
	答：方法的重载和重写都是实现多态的方式，区别在于前者实现的是“编译时”的多态性，而后者实现的是“运行时”的多态性。重载发生在一个类中，同名的方法如果有不同的参数列表（参数类型不同、参数个数不同或者二者都不同）则视为重载；重写发生在子类与父类之间，重写要求子类被重写方法与父类被重写方法有相同的返回类型，比父类被重写方法更好访问，不能比父类被重写方法声明更多的异常（里氏代换原则）。重载对返回类型没有特殊的要求。
	
11.当一个对象被当作参数传递到一个方法后，此方法可改变这个对象的属性，并可返回变化后的结果，是值传递。
	Java语言的方法调用只支持参数的值传递。当一个对象实例作为一个参数被传递到方法中时，参数的值就是对该对象的引用。对象的属性可以在被调用过程中被改变，但对对象引用的改变是不会影响到调用者的。
	
12.码
	原码
	原码，顾名思义就是现实生活中表示的码，原来的码。其中最高位为符号位，0代表正数，1代表负数
	以8位二进制为例
	[+1]原 = 0000 0001
	[-1]原 = 1000 0001
	进而，8位二进制可表示[1111 1111, 0111 1111]，即[-127, 127]
	
	反码  
	正数的反码，就是其本身
	负数的反码，就是在原码的基础上，符号为不变，其余各位取反
	[+1] = [0000 0001]原 = [0000 0001]反
	[-1] = [1000 0001]原 = [1111 1110]反  
	计算技巧：-1 的反码 为 -126，-2的反码为-125。是不是有感觉了，数字部分就是127-i
	
	补码
	正数的补码，就是其本身
	负数的补码，就是在原码的基础上，符号位不变，其余各位取反后+1，即反码+1 
	[+1] = [0000 0001]原 = [0000 0001]反 = [0000 0001]补
	[-1] = [1000 0001]原 = [1111 1110]反 = [1111 1111]补  
	此外，[1000 0000]补   代表-128，所以用补码表示的区间为[-128, 127]
	计算技巧：-1 的补码为 -127，-2的补码为-126，数字部分就是128-i
	
13.类加载器
	JVM中类的装载是由类加载器（ClassLoader）和它的子类来实现的，Java中的类加载器是一个重要的Java运行时系统组件，它负责在运行时查找和装入类文件中的类。 
	Bootstrap：一般用本地代码实现，负责加载JVM基础核心类库（rt.jar）；
	Extension：从java.ext.dirs系统属性所指定的目录中加载类库，它的父加载器是Bootstrap；
	System：又叫应用类加载器，其父类是Extension。它是应用最广泛的类加载器。它从环境变量classpath或者系统属性java.class.path所指定的目录中记载类，是用户自定义加载器的默认父加载器。
	
14.抽象类（abstract class）和接口（interface）有什么异同？ 
	答：抽象类和接口都不能够实例化，但可以定义抽象类和接口类型的引用。一个类如果继承了某个抽象类或者实现了某个接口都需要对其中的抽象方法全部进行实现，否则该类仍然需要被声明为抽象类。接口比抽象类更加抽象，因为抽象类中可以定义构造器，可以有抽象方法和具体方法，而接口中不能定义构造器而且其中的方法全部都是抽象方法。抽象类中的成员可以是private、默认、protected、public的，而接口中的成员全都是public的。抽象类中可以定义成员变量，而接口中定义的成员变量实际上都是常量。有抽象方法的类必须被声明为抽象类，而抽象类未必要有抽象方法。
	
15.抽象的（abstract）方法是否可同时是静态的（static）,是否可同时是本地方法（native），是否可同时被synchronized修饰？ 
	答：都不能。抽象方法需要子类重写，而静态的方法是无法被重写的，因此二者是矛盾的。本地方法是由本地代码（如C代码）实现的方法，而抽象方法是没有实现的，也是矛盾的。synchronized和方法的实现细节有关，抽象方法不涉及实现细节，因此也是相互矛盾的。
	
16.是否可以从一个静态（static）方法内部发出对非静态（non-static）方法的调用？ 
	答：不可以，静态方法只能访问静态成员，因为非静态方法的调用要先创建对象，在调用静态方法时可能对象并没有被初始化。
	
17.String s = new String("xyz");创建了几个字符串对象？ 
	答：两个对象，一个是静态区的"xyz"，一个是用new创建在堆上的对象。
	
18.一个".java"源文件中是否可以包含多个类（不是内部类）？有什么限制？ 
	答：可以，但一个源文件中最多只能有一个公开类（public class）而且文件名必须和公开类的类名完全保持一致。
	
19.Anonymous Inner Class(匿名内部类)是否可以继承其它类？是否可以实现接口？ 
	答：可以继承其他类或实现其他接口，在Swing编程和Android开发中常用此方式来实现事件监听和回调。
	
20、数据类型之间的转换： 
	- 如何将字符串转换为基本数据类型？ 
	- 如何将基本数据类型转换为字符串？ 
答： 
	- 调用基本数据类型对应的包装类中的方法parseXXX(String)或valueOf(String)即可返回相应基本类型； 
	- 一种方法是将基本数据类型与空字符串（""）连接（+）即可获得其所对应的字符串；另一种方法是调用String 类中的valueOf()方法返回相应字符串
	
21、如何实现字符串的反转及替换？ 
答：方法很多，可以自己写实现也可以使用String或StringBuffer/StringBuilder中的方法。有一道很常见的面试题是用递归实现字符串反转，代码如下所示：
	
	    public static String reverse(String originStr) {
	        if(originStr == null || originStr.length() <= 1) 
	            return originStr;
	        return reverse(originStr.substring(1)) + originStr.charAt(0);
	    }
	
22、怎样将GB2312编码的字符串转换为ISO-8859-1编码的字符串？ 
	答：代码如下所示：
	String s1 = "你好";
	String s2 = new String(s1.getBytes("GB2312"), "ISO-8859-1");
	
23.MD5加密的简单用法(互联网开发中应使用两次MD5，一次在浏览器，一次在客户端，因为http在网络上传输是不安全的，也能防止彩虹表)
	import org.apache.commons.codec.digest.DigestUtils;  DigestUtils.md5Hex(src);
	
24.日期和时间
	// Java 8
	        LocalDateTime dt = LocalDateTime.now();
	        System.out.println(dt.getYear());
	        System.out.println(dt.getMonthValue());     // 1 - 12
	        System.out.println(dt.getDayOfMonth());
	        System.out.println(dt.getHour());
	        System.out.println(dt.getMinute());
	        System.out.println(dt.getSecond());
	以下方法均可获得该毫秒数。
	        Calendar.getInstance().getTimeInMillis();
	        System.currentTimeMillis();
	        Clock.systemDefaultZone().millis(); // Java 8
	格式化日期
	        // Java 8
	        DateTimeFormatter newFormatter = DateTimeFormatter.ofPattern("yyyy/MM/dd");
	        LocalDate date2 = LocalDate.now();
	        System.out.println(date2.format(newFormatter));
	
25.比较一下Java和JavaSciprt。 
	答：JavaScript 与Java是两个公司开发的不同的两个产品。Java 是原Sun Microsystems公司推出的面向对象的程序设计语言，特别适合于互联网应用程序开发；而JavaScript是Netscape公司的产品，为了扩展Netscape浏览器的功能而开发的一种可以嵌入Web页面中运行的基于对象和事件驱动的解释性语言。JavaScript的前身是LiveScript；而Java的前身是Oak语言。 
	下面对两种语言间的异同作如下比较： 
	- 基于对象和面向对象：Java是一种真正的面向对象的语言，即使是开发简单的程序，必须设计对象；JavaScript是种脚本语言，它可以用来制作与网络无关的，与用户交互作用的复杂软件。它是一种基于对象（Object-Based）和事件驱动（Event-Driven）的编程语言，因而它本身提供了非常丰富的内部对象供设计人员使用。 
	- 解释和编译：Java的源代码在执行之前，必须经过编译。JavaScript是一种解释性编程语言，其源代码不需经过编译，由浏览器解释执行。（目前的浏览器几乎都使用了JIT（即时编译）技术来提升JavaScript的运行效率） 
	- 强类型变量和类型弱变量：Java采用强类型变量检查，即所有变量在编译之前必须作声明；JavaScript中变量是弱类型的，甚至在使用变量前可以不作声明，JavaScript的解释器在运行时检查推断其数据类型。
	
26.44、什么时候用断言（assert）？ 
	答：断言在软件开发中是一种常用的调试方式，很多开发语言中都支持这种机制。一般来说，断言用于保证程序最基本、关键的正确性。断言检查通常在开发和测试时开启。为了保证程序的执行效率，在软件发布后断言检查通常是关闭的。断言是一个包含布尔表达式的语句，在执行这个语句时假定该表达式为true；如果表达式的值为false，那么系统会报告一个AssertionError。断言的使用如下面的代码所示：
	
	assert(a > 0); // throws an AssertionError if a <= 0
	
27.列出一些你常见的运行时异常？ 
	答： 
	- ArithmeticException（算术异常） 
	- ClassCastException （类转换异常） 
	- IllegalArgumentException （非法参数异常） 
	- IndexOutOfBoundsException （下标越界异常） 
	- NullPointerException （空指针异常） 
	- SecurityException （安全异常）
	
28.Thread类的sleep()方法和对象的wait()方法都可以让线程暂停执行，它们有什么区别? 
	答：sleep()方法（休眠）是线程类（Thread）的静态方法，调用此方法会让当前线程暂停执行指定的时间，将执行机会（CPU）让给其他线程，但是对象的锁依然保持，因此休眠时间结束后会自动恢复（线程回到就绪状态，请参考第66题中的线程状态转换图）。wait()是Object类的方法，调用对象的wait()方法导致当前线程放弃对象的锁（线程暂停执行），进入对象的等待池（wait pool），只有调用对象的notify()方法（或notifyAll()方法）时才能唤醒等待池中的线程进入等锁池（lock pool），如果线程重新获得对象的锁就可以进入就绪状态。
	
	补充：可能不少人对什么是进程，什么是线程还比较模糊，对于为什么需要多线程编程也不是特别理解。简单的说：进程是具有一定独立功能的程序关于某个数据集合上的一次运行活动，是操作系统进行资源分配和调度的一个独立单位；线程是进程的一个实体，是CPU调度和分派的基本单位，是比进程更小的能独立运行的基本单位。线程的划分尺度小于进程，这使得多线程程序的并发性高；进程在执行时通常拥有独立的内存单元，而线程之间可以共享内存。使用多线程的编程通常能够带来更好的性能和用户体验，但是多线程的程序对于其他程序是不友好的，因为它可能占用了更多的CPU资源。当然，也不是线程越多，程序的性能就越好，因为线程之间的调度和切换也会浪费CPU时间。时下很时髦的Node.js就采用了单线程异步I/O的工作模式。
	
29.线程的sleep()方法和yield()方法有什么区别？ 
	答： 
	① sleep()方法给其他线程运行机会时不考虑线程的优先级，因此会给低优先级的线程以运行的机会；yield()方法只会给相同优先级或更高优先级的线程以运行的机会； 
	② 线程执行sleep()方法后转入阻塞（blocked）状态，而执行yield()方法后转入就绪（ready）状态； 
	③ sleep()方法声明抛出InterruptedException，而yield()方法没有声明任何异常； 
	④ sleep()方法比yield()方法（跟操作系统CPU调度相关）具有更好的可移植性。
	- wait()：使一个线程处于等待（阻塞）状态，并且释放所持有的对象的锁； 
	- sleep()：使一个正在运行的线程处于睡眠状态，是一个静态方法，调用此方法要处理InterruptedException异常； 
	- notify()：唤醒一个处于等待状态的线程，当然在调用此方法的时候，并不能确切的唤醒某一个等待状态的线程，而是由JVM确定唤醒哪个线程，而且与优先级无关； 
	- notityAll()：唤醒所有处于等待状态的线程，该方法并不是将对象的锁给所有线程，而是让它们竞争，只有获得锁的线程才能进入就绪状态；
	
	
30、当一个线程进入一个对象的synchronized方法A之后，其它线程是否可进入此对象的synchronized方法B？ 
	答：不能。其它线程只能访问该对象的非同步方法，同步方法则不能进入。因为非静态方法上的synchronized修饰符要求执行方法时要获得对象的锁，如果已经进入A方法说明对象锁已经被取走，那么试图进入B方法的线程就只能在等锁池（注意不是等待池哦）中等待对象的锁。

31.举例说明同步和异步。 
答：如果系统中存在临界资源（资源数量少于竞争资源的线程数量的资源），例如正在写的数据以后可能被另一个线程读到，或者正在读的数据可能已经被另一个线程写过了，那么这些数据就必须进行同步存取（数据库操作中的排他锁就是最好的例子）。当应用程序在对象上调用了一个需要花费很长时间来执行的方法，并且不希望让程序等待方法的返回时，就应该使用异步编程，在很多情况下采用异步途径往往更有效率。事实上，所谓的同步就是指阻塞式操作，而异步就是非阻塞式操作。

32.启动一个线程是调用run()还是start()方法？ 
答：启动一个线程是调用start()方法，使线程所代表的虚拟处理机处于可运行状态，这意味着它可以由JVM 调度并执行，这并不意味着线程就会立即运行。run()方法是线程启动后要进行回调（callback）的方法。

33.简述synchronized 和java.util.concurrent.locks.Lock的异同？ 
答：Lock是Java 5以后引入的新的API，和关键字synchronized相比主要相同点：Lock 能完成synchronized所实现的所有功能；主要不同点：Lock有比synchronized更精确的线程语义和更好的性能，而且不强制性的要求一定要获得锁。synchronized会自动释放锁，而Lock一定要求程序员手工释放，并且最好在finally 块中释放（这是释放外部资源的最好的地方）

34.XML文档定义有几种形式？它们之间有何本质区别？解析XML文档有哪几种方式？ 
答：XML文档定义分为DTD和Schema两种形式，二者都是对XML语法的约束，其本质区别在于Schema本身也是一个XML文件，可以被XML解析器解析，而且可以为XML承载的数据定义类型，约束能力较之DTD更强大。对XML的解析主要有DOM（文档对象模型，Document Object Model）、SAX（Simple API for XML）和StAX（Java 6中引入的新的解析XML的方式，Streaming API for XML），其中DOM处理大型文件时其性能下降的非常厉害，这个问题是由DOM树结构占用的内存较多造成的，而且DOM解析方式必须在解析文件之前把整个文档装入内存，适合对XML的随机访问（典型的用空间换取时间的策略）；SAX是事件驱动型的XML解析方式，它顺序读取XML文件，不需要一次全部装载整个文件。当遇到像文件开头，文档结束，或者标签开头与标签结束时，它会触发一个事件，用户通过事件回调代码来处理XML文件，适合对XML的顺序访问；顾名思义，StAX把重点放在流上，实际上StAX与其他解析方式的本质区别就在于应用程序能够把XML作为一个事件流来处理。将XML作为一组事件来处理的想法并不新颖（SAX就是这样做的），但不同之处在于StAX允许应用程序代码把这些事件逐个拉出来，而不用提供在解析器方便时从解析器中接收事件的处理程序。
在项目中哪些地方用到了XML
答：XML的主要作用有两个方面：数据交换和信息配置。在做数据交换时，XML将数据用标签组装成起来，然后压缩打包加密后通过网络传送给接收者，接收解密与解压缩后再从XML文件中还原相关信息进行处理，XML曾经是异构系统间交换数据的事实标准，但此项功能几乎已经被JSON（JavaScript Object Notation）取而代之。当然，目前很多软件仍然使用XML来存储配置信息，我们在很多项目中通常也会将作为配置信息的硬代码写在XML文件中，Java的很多框架也是这么做的，而且这些框架都选择了dom4j作为处理XML的工具，因为Sun公司的官方API实在不怎么好用。

35.JDBC
加载驱动。
    Class.forName("oracle.jdbc.driver.OracleDriver");
创建连接。
    Connection con = DriverManager.getConnection("jdbc:oracle:thin:@localhost:1521:orcl", "scott", "tiger");
创建语句。
    PreparedStatement ps = con.prepareStatement("select * from emp where sal between ? and ?");
    ps.setInt(1, 1000);
    ps.setInt(2, 3000);
执行语句。
    ResultSet rs = ps.executeQuery();
处理结果。
    while(rs.next()) {
        System.out.println(rs.getInt("empno") + " - " + rs.getString("ename"));
    }
关闭资源。
    finally {
        if(con != null) {
            try {
                con.close();
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
    }

事物：
Connection提供了事务处理的方法，通过调用setAutoCommit(false)可以设置手动提交事务；当事务完成后用commit()显式提交事务；如果在事务处理过程中发生异常则通过rollback()进行事务回滚。除此之外，从JDBC 3.0中还引入了Savepoint（保存点）的概念，允许通过代码设置保存点并让事务回滚到指定的保存点。 


36.什么是DAO模式？ 
DAO（Data Access Object）顾名思义是一个为数据库或其他持久化机制提供了抽象接口的对象，在不暴露底层持久化方案实现细节的前提下提供了各种数据访问操作。在实际的开发中，应该将所有对数据源的访问操作进行抽象化后封装在一个公共API中。用程序设计语言来说，就是建立一个接口，接口中定义了此应用程序中将会用到的所有事务方法。在这个应用程序中，当需要和数据源进行交互的时候则使用这个接口，并且编写一个单独的类来实现这个接口，在逻辑上该类对应一个特定的数据存储。DAO模式实际上包含了两个模式，一是Data Accessor（数据访问器），二是Data Object（数据对象），前者要解决如何访问数据的问题，而后者要解决的是如何用对象封装数据。

37.反射
- 方法1：通过类对象调用newInstance()方法，例如：String.class.newInstance() 
- 方法2：通过类对象的getConstructor()或getDeclaredConstructor()方法获得构造器（Constructor）对象并调用其newInstance()方法创建对象，例如：String.class.getConstructor(String.class).newInstance("Hello");

通过反射获取和设置对象私有字段的值
Class<?> clazz = target.getClass();
Field f = clazz.getDeclaredField(str);
f.setAccessible(true);
f.get(target);
f.set(target, value);

通过反射调用对象方法
String str = "hello";
Method m = str.getClass().getMethod("toUpperCase");
m.invoke(str); 

38.UML 
UML是统一建模语言（Unified Modeling Language）的缩写，它发表于1997年，综合了当时已经存在的面向对象的建模语言、方法和过程，是一个支持模型化和软件系统开发的图形化语言，为软件开发的所有阶段提供模型化和可视化支持。使用UML可以帮助沟通与交流，辅助应用设计和文档的生成，还能够阐释系统的结构和行为。

39.排序算法
    冒泡
    @Override
    public <T extends Comparable<T>> void sort(T[] list) {
        boolean swapped = true;
        for (int i = 1, len = list.length; i < len && swapped; ++i) {
            swapped = false;
            for (int j = 0; j < len - i; ++j) {
                if (list[j].compareTo(list[j + 1]) > 0) {
                    T temp = list[j];
                    list[j] = list[j + 1];
                    list[j + 1] = temp;
                    swapped = true;
                }
            }
        }
    }

    折半查找
   public static <T extends Comparable<T>> int binarySearch(T[] x, T key) {
      return binarySearch(x, 0, x.length- 1, key);
   }

   // 使用循环实现的二分查找
   public static <T> int binarySearch(T[] x, T key, Comparator<T> comp) {
      int low = 0;
      int high = x.length - 1;
      while (low <= high) {
          int mid = (low + high) >>> 1;
          int cmp = comp.compare(x[mid], key);
          if (cmp < 0) {
            low= mid + 1;
          }
          else if (cmp > 0) {
            high= mid - 1;
          }
          else {
            return mid;
          }
      }
      return -1;
   }

   // 使用递归实现的二分查找
   private static<T extends Comparable<T>> int binarySearch(T[] x, int low, int high, T key) {
      if(low <= high) {
        int mid = low + ((high -low) >> 1);
        if(key.compareTo(x[mid])== 0) {
           return mid;
        }
        else if(key.compareTo(x[mid])< 0) {
           return binarySearch(x,low, mid - 1, key);
        }
        else {
           return binarySearch(x,mid + 1, high, key);
        }
      }
      return -1;
   }

40.Servlet
Servlet接口定义了5个方法，其中前三个方法与Servlet生命周期相关： 
- void init(ServletConfig config) throws ServletException 
- void service(ServletRequest req, ServletResponse resp) throws ServletException, java.io.IOException 
- void destory() 
- java.lang.String getServletInfo() 
- ServletConfig getServletConfig()
Web容器加载Servlet并将其实例化后，Servlet生命周期开始，容器运行其init()方法进行Servlet的初始化；请求到达时调用Servlet的service()方法，service()方法会根据需要调用与请求对应的doGet或doPost等方法；当服务器关闭或项目被卸载时服务器会将Servlet实例销毁，此时会调用Servlet的destroy()方法。
					 
转发（forward）和重定向（redirect）的区别？ 
forward是容器中控制权的转向，是服务器请求资源，服务器直接访问目标地址的URL，把那个URL 的响应内容读取过来，然后把这些内容再发给浏览器，浏览器根本不知道服务器发送的内容是从哪儿来的，所以它的地址栏中还是原来的地址。redirect就是服务器端根据逻辑，发送一个状态码，告诉浏览器重新去请求那个地址，因此从浏览器的地址栏中可以看到跳转后的链接地址，很明显redirect无法访问到服务器保护起来资源，但是可以从一个网站redirect到其他网站。forward更加高效，所以在满足需要时尽量使用forward（通过调用RequestDispatcher对象的forward()方法，该对象可以通过ServletRequest对象的getRequestDispatcher()方法获得），并且这样也有助于隐藏实际的链接；在有些情况下，比如需要访问一个其它服务器上的资源，则必须使用重定向（通过HttpServletResponse对象调用其sendRedirect()方法实现）。

get和post请求的区别？  
①get请求用来从服务器上获得资源，而post是用来向服务器提交数据； 
②get将表单中数据按照name=value的形式，添加到action 所指向的URL 后面，并且两者使用"?"连接，而各个变量之间使用"&"连接；post是将表单中的数据放在HTTP协议的请求头或消息体中，传递到action所指向URL； 
③get传输的数据要受到URL长度限制（1024字节）；而post可以传输大量的数据，上传文件通常要使用post方式； 
④使用get时参数会显示在地址栏上，如果这些数据不是敏感数据，那么可以使用get；对于敏感数据还是应用使用post； 
⑤get使用MIME类型application/x-www-form-urlencoded的URL编码（也叫百分号编码）文本的格式传递参数，保证被传送的参数由遵循规范的文本组成，例如一个空格的编码是"%20"。

41.静态化页面（页面缓存）
@Autowired
ThymeleafViewResolver thymeleafViewResolver;

@RequestMapping(value="/to_list", produces="text/html")
@ResponseBody					 
String html = //从Redis获取静态页面
if(!StringUtils.isEmpty(html)) {
   return html;
}					 
//如果Redis获取不到页面，则页面过期或第一次加载页面，需要手动渲染					 
WebContext ctx = new WebContext(request,response,
request.getServletContext(),request.getLocale(), model.asMap());
html = thymeleafViewResolver.getTemplateEngine().process("goods_list", ctx);
if(!StringUtils.isEmpty(html)) {
    //将生成的静态页面存储至redis中
}
return html
静态化页面则不再返回html页面，而是返回具体数据，将页面内容静态置于服务器中，通过AJAX实时获取返回内容
					 
					 
42.对象缓存（需注意，更新对象信息时也要更新缓存对象，否则会出现缓存不一致的现象）
//从redis中取缓存对象
MiaoshaUser user = redisService.get(MiaoshaUserKey.getById, ""+id, MiaoshaUser.class);
if(user != null) {
	return user;
}
//若redis中没有缓存对象，取数据库数据生成对象，并存储在缓存中
user = miaoshaUserDao.getById(id);
if(user != null) {
	redisService.set(MiaoshaUserKey.getById, ""+id, user);
}
return user;					 
service中若要操作其他表则应引入其他service而不能引入其他Dao否则，无法同步缓存
					 
43.常见的静态资源优化手段（并发的瓶颈是数据库，有效的方法是使用缓存）
 js/css压缩，减少流量
 整合js/css减少连接数					 
 webpack打包前端资源			
					 
CDN的全称是Content Delivery Network，即内容分发网络。其基本思路是尽可能避开互联网上有可能影响数据传输速度和稳定性的瓶颈和环节，使内容传输的更快、更稳定。通过在网络各处放置节点服务器所构成的在现有的互联网基础之上的一层智能虚拟网络，CDN系统能够实时地根据网络流量和各节点的连接、负载状况以及到用户的距离和响应时间等综合信息将用户的请求重新导向离用户最近的服务节点上。其目的是使用户可就近取得所需内容，解决 Internet网络拥挤的状况，提高用户访问网站的响应速度。
					 
44.常用的Web服务器 
Unix和Linux平台下使用最广泛的免费HTTP服务器是Apache服务器，而Windows平台的服务器通常使用IIS作为Web服务器。选择Web服务器应考虑的因素有：性能、安全性、日志和统计、虚拟主机、代理服务器、缓冲服务和集成应用程序等。下面是对常见服务器的简介： 
- IIS：Microsoft的Web服务器产品，全称是Internet Information Services。IIS是允许在公共Intranet或Internet上发布信息的Web服务器。IIS是目前最流行的Web服务器产品之一，很多著名的网站都是建立在IIS的平台上。IIS提供了一个图形界面的管理工具，称为Internet服务管理器，可用于监视配置和控制Internet服务。IIS是一种Web服务组件，其中包括Web服务器、FTP服务器、NNTP服务器和SMTP服务器，分别用于网页浏览、文件传输、新闻服务和邮件发送等方面，它使得在网络（包括互联网和局域网）上发布信息成了一件很容易的事。它提供ISAPI(Intranet Server API）作为扩展Web服务器功能的编程接口；同时，它还提供一个Internet数据库连接器，可以实现对数据库的查询和更新。 
- Kangle：Kangle Web服务器是一款跨平台、功能强大、安全稳定、易操作的高性能Web服务器和反向代理服务器软件。此外，Kangle也是一款专为做虚拟主机研发的Web服务器。实现虚拟主机独立进程、独立身份运行。用户之间安全隔离，一个用户出问题不影响其他用户。支持PHP、ASP、ASP.NET、Java、Ruby等多种动态开发语言。 
- WebSphere：WebSphere Application Server是功能完善、开放的Web应用程序服务器，是IBM电子商务计划的核心部分，它是基于Java的应用环境，用于建立、部署和管理Internet和Intranet Web应用程序，适应各种Web应用程序服务器的需要。 
- WebLogic：WebLogic Server是一款多功能、基于标准的Web应用服务器，为企业构建企业应用提供了坚实的基础。针对各种应用开发、关键性任务的部署，各种系统和数据库的集成、跨Internet协作等Weblogic都提供了相应的支持。由于它具有全面的功能、对开放标准的遵从性、多层架构、支持基于组件的开发等优势，很多公司的企业级应用都选择它来作为开发和部署的环境。WebLogic Server在使应用服务器成为企业应用架构的基础方面一直处于领先地位，为构建集成化的企业级应用提供了稳固的基础。 
- Apache：目前Apache仍然是世界上用得最多的Web服务器，其市场占有率很长时间都保持在60%以上（目前的市场份额约40%左右）。世界上很多著名的网站都是Apache的产物，它的成功之处主要在于它的源代码开放、有一支强大的开发团队、支持跨平台的应用（可以运行在几乎所有的Unix、Windows、Linux系统平台上）以及它的可移植性等方面。 
- Tomcat：Tomcat是一个开放源代码、运行Servlet和JSP的容器。Tomcat实现了Servlet和JSP规范。此外，Tomcat还实现了Apache-Jakarta规范而且比绝大多数商业应用软件服务器要好，因此目前也有不少的Web服务器都选择了Tomcat。 
- Nginx：读作"engine x"，是一个高性能的HTTP和反向代理服务器，也是一个IMAP/POP3/SMTP代理服务器。 Nginx是由Igor Sysoev为俄罗斯访问量第二的Rambler站点开发的，第一个公开版本0.1.0发布于2004年10月4日。其将源代码以类BSD许可证的形式发布，因它的稳定性、丰富的功能集、示例配置文件和低系统资源的消耗而闻名。在2014年下半年，Nginx的市场份额达到了14%

45.会话跟踪的技术 
由于HTTP协议本身是无状态的，服务器为了区分不同的用户，就需要对用户会话进行跟踪，简单的说就是为用户进行登记，为用户分配唯一的ID，下一次用户在请求中包含此ID，服务器据此判断到底是哪一个用户。 
①URL 重写：在URL中添加用户会话的信息作为请求的参数，或者将唯一的会话ID添加到URL结尾以标识一个会话。 
②设置表单隐藏域：将和会话跟踪相关的字段添加到隐式表单域中，这些信息不会在浏览器中显示但是提交表单时会提交给服务器。 
这两种方式很难处理跨越多个页面的信息传递，因为如果每次都要修改URL或在页面中添加隐式表单域来存储用户会话相关信息，事情将变得非常麻烦。 
③cookie：cookie有两种，一种是基于窗口的，浏览器窗口关闭后，cookie就没有了；另一种是将信息存储在一个临时文件中，并设置存在的时间。当用户通过浏览器和服务器建立一次会话后，会话ID就会随响应信息返回存储在基于窗口的cookie中，那就意味着只要浏览器没有关闭，会话没有超时，下一次请求时这个会话ID又会提交给服务器让服务器识别用户身份。会话中可以为用户保存信息。会话对象是在服务器内存中的，而基于窗口的cookie是在客户端内存中的。如果浏览器禁用了cookie，那么就需要通过下面两种方式进行会话跟踪。当然，在使用cookie时要注意几点：首先不要在cookie中存放敏感信息；其次cookie存储的数据量有限（4k），不能将过多的内容存储cookie中；再者浏览器通常只允许一个站点最多存放20个cookie。当然，和用户会话相关的其他信息（除了会话ID）也可以存在cookie方便进行会话跟踪。 
④HttpSession：在所有会话跟踪技术中，HttpSession对象是最强大也是功能最多的。当一个用户第一次访问某个网站时会自动创建HttpSession，每个用户可以访问他自己的HttpSession。可以通过HttpServletRequest对象的getSession方法获得HttpSession，通过HttpSession的setAttribute方法可以将一个值放在HttpSession中，通过调用HttpSession对象的getAttribute方法，同时传入属性名就可以获取保存在HttpSession中的对象。与上面三种方式不同的是，HttpSession放在服务器的内存中，因此不要将过大的对象放在里面，即使目前的Servlet容器可以在内存将满时将HttpSession中的对象移到其他存储设备中，但是这样势必影响性能。添加到HttpSession中的值可以是任意Java对象，这个对象最好实现了Serializable接口，这样Servlet容器在必要的时候可以将其序列化到文件中，否则在序列化时就会出现异常。

46.过滤器与监听器
web.xml用于配置Web应用的相关信息，如：监听器（listener）、过滤器（filter）、 Servlet、相关参数、会话超时时间、安全验证方式、错误页面等				 					 
对Web应用来说，过滤器是一个驻留在服务器端的Web组件，它可以截取客户端和服务器之间的请求与响应信息，并对这些信息进行过滤。
常见的过滤器用途主要包括：对用户请求进行统一认证、对用户的访问请求进行记录和审核、对用户发送的数据进行过滤或替换、转换图象格式、对响应内容进行压缩以减少传输量、对请求或响应进行加解密处理、触发资源访问事件、对XML的输出应用XSLT等。					 
@WebFilter(urlPatterns = { "*" },initParams = {@WebInitParam(name="encoding", value="utf-8")})
public class CodingFilter implements Filter {
    private String defaultEncoding = "utf-8";

    @Override
    public void destroy() {
    }

    @Override
    public void doFilter(ServletRequest req, ServletResponse resp,
            FilterChain chain) throws IOException, ServletException {
        req.setCharacterEncoding(defaultEncoding);
        resp.setCharacterEncoding(defaultEncoding);
        chain.doFilter(req, resp);
    }

    @Override
    public void init(FilterConfig config) throws ServletException {
        String encoding = config.getInitParameter("encoding");
        if (encoding != null) {
            defaultEncoding = encoding;
        }
    }
}
监听器的作用和用法
答：Java Web开发中的监听器（listener）就是application、session、request三个对象创建、销毁或者往其中添加修改删除属性时自动执行代码的功能组件，如下所示： 
①ServletContextListener：对Servlet上下文的创建和销毁进行监听。 
②ServletContextAttributeListener：监听Servlet上下文属性的添加、删除和替换。 
③HttpSessionListener：对Session的创建和销毁进行监听。

补充：session的销毁有两种情况：1). session超时（可以在web.xml中通过<session-config>/<session-timeout>标签配置超时时间）；2). 通过调用session对象的invalidate()方法使session失效。

④HttpSessionAttributeListener：对Session对象中属性的添加、删除和替换进行监听。 
⑤ServletRequestListener：对请求对象的初始化和销毁进行监听。 
⑥ServletRequestAttributeListener：对请求对象属性的添加、删除和替换进行监听。

47.servlet与文件上传
Servlet是一个特殊的Java程序，它运行于服务器的JVM中，能够依靠服务器的支持向浏览器提供显示内容。JSP本质上是Servlet的一种简易形式，JSP会被服务器处理成一个类似于Servlet的Java程序，可以简化页面内容的生成。Servlet和JSP最主要的不同点在于，Servlet的应用逻辑是在Java文件中，并且完全从表示层中的HTML分离开来。而JSP的情况是Java和HTML可以组合成一个扩展名为.jsp的文件。有人说，Servlet就是在Java中写HTML，而JSP就是在HTML中写Java代码，当然这个说法是很片面且不够准确的。JSP侧重于视图，Servlet更侧重于控制逻辑，在MVC架构模式中，JSP适合充当视图（view）而Servlet适合充当控制器（controller）。
servlet异步处理
	// 开启Tomcat异步Servlet支持
        req.setAttribute("org.apache.catalina.ASYNC_SUPPORTED", true);

        final AsyncContext ctx = req.startAsync();  // 启动异步处理的上下文
        // ctx.setTimeout(30000);
        ctx.start(new Runnable() {

            @Override
            public void run() {
                // 在此处添加异步处理的代码

                ctx.complete();
            }
        });
servlet文件上传
@WebServlet("/UploadServlet")
@MultipartConfig
public class UploadServlet extends HttpServlet {
    private static final long serialVersionUID = 1L;

    protected void doPost(HttpServletRequest request,
            HttpServletResponse response) throws ServletException, IOException {
        // 可以用request.getPart()方法获得名为photo的上传附件
        // 也可以用request.getParts()获得所有上传附件（多文件上传）
        // 然后通过循环分别处理每一个上传的文件
        Part part = request.getPart("photo");
        if (part != null && part.getSubmittedFileName().length() > 0) {
            // 用ServletContext对象的getRealPath()方法获得上传文件夹的绝对路径
            String savePath = request.getServletContext().getRealPath("/upload");
            // Servlet 3.1规范中可以用Part对象的getSubmittedFileName()方法获得上传的文件名
            // 更好的做法是为上传的文件进行重命名（避免同名文件的相互覆盖）
            part.write(savePath + "/" + part.getSubmittedFileName());
            request.setAttribute("hint", "Upload Successfully!");
        } else {
            request.setAttribute("hint", "Upload failed!");
        }
        // 跳转回到上传页面
        request.getRequestDispatcher("index.jsp").forward(request, response);
    }

}

48.Mybatis
ORM
对象关系映射（Object-Relational Mapping，简称ORM）是一种为了解决程序的面向对象模型与数据库的关系模型互不匹配问题的技术；简单的说，ORM是通过使用描述对象和数据库之间映射的元数据（在Java中可以用XML或者是注解），将程序中的对象自动持久化到关系数据库中或者将关系数据库表中的行转换成Java对象，其本质上就是将数据从一种形式转换到另外一种形式。
持久层设计的目标包括： 
- 数据存储逻辑的分离，提供抽象化的数据访问接口。 
- 数据访问底层实现的分离，可以在不修改代码的情况下切换底层实现。 
- 资源管理和调度的分离，在数据访问层实现统一的资源调度（如缓存机制）。 
- 数据抽象，提供更面向对象的数据操作。
持久层框架有： 
- Hibernate 
- MyBatis 
- TopLink 
- Guzz 
- jOOQ 
- Spring Data 
- ActiveJDBC
	
MyBatis中使用#和$书写占位符有什么区别？ 
#将传入的数据都当成一个字符串，会对传入的数据自动加上引号；$将传入的数据直接显示生成在SQL中。注意：使用$占位符可能会导致SQL注射攻击，能用#的地方就不要使用$，写order by子句的时候应该用$而不是#。
MyBatis中命名空间（namespace）的作用。 
在大型项目中，可能存在大量的SQL语句，这时候为每个SQL语句起一个唯一的标识（ID）就变得并不容易了。为了解决这个问题，在MyBatis中，可以为每个映射文件起一个唯一的命名空间，这样定义在这个映射文件中的每个SQL语句就成了定义在这个命名空间中的一个ID。只要我们能够保证每个命名空间中这个ID是唯一的，即使在不同映射文件中的语句ID相同，也不会再产生冲突了。
MyBatis中的动态SQL是什么意思？ 
答：对于一些复杂的查询，我们可能会指定多个查询条件，但是这些条件可能存在也可能不存在，例如在58同城上面找房子，我们可能会指定面积、楼层和所在位置来查找房源，也可能会指定面积、价格、户型和所在位置来查找房源，此时就需要根据用户指定的条件动态生成SQL语句。如果不使用持久层框架我们可能需要自己拼装SQL语句，还好MyBatis提供了动态SQL的功能来解决这个问题。MyBatis中用于实现动态SQL的元素主要有： 
- if 
- choose / when / otherwise 
- trim 
- where 
- set 
- foreach
下面是映射文件的片段。
    <select id="foo" parameterType="Blog" resultType="Blog">
        select * from t_blog where 1 = 1
        <if test="title != null">
            and title = #{title}
        </if>
        <if test="content != null">
            and content = #{content}
        </if>
        <if test="owner != null">
            and owner = #{owner}
        </if>
   </select>

    <select id="foo" parameterType="Blog" resultType="Blog">
        select * from t_blog where 1 = 1 
        <choose>
            <when test="title != null">
                and title = #{title}
            </when>
            <when test="content != null">
                and content = #{content}
            </when>
            <otherwise>
                and owner = "owner1"
            </otherwise>
        </choose>
    </select>

    <select id="bar" resultType="Blog">
        select * from t_blog where id in
        <foreach collection="array" index="index" 
            item="item" open="(" separator="," close=")">
            #{item}
        </foreach>
    </select>
IoC和DI？DI是如何实现的？ 
答：IoC叫控制反转，是Inversion of Control的缩写，DI（Dependency Injection）叫依赖注入，是对IoC更简单的诠释。控制反转是把传统上由程序代码直接操控的对象的调用权交给容器，通过容器来实现对象组件的装配和管理。所谓的"控制反转"就是对组件对象控制权的转移，从程序代码本身转移到了外部容器，由容器来创建对象并管理对象之间的依赖关系。IoC体现了好莱坞原则 - "Don’t call me, we will call you"。依赖注入的基本原则是应用组件不应该负责查找资源或者其他依赖的协作对象。配置对象的工作应该由容器负责，查找资源的逻辑应该从应用组件的代码中抽取出来，交给容器来完成。DI是对IoC更准确的描述，即组件之间的依赖关系由容器在运行期决定，形象的来说，即由容器动态的将某种依赖关系注入到组件之中。

依赖注入可以通过setter方法注入（设值注入）、构造器注入和接口注入三种方式来实现，Spring支持setter注入和构造器注入，通常使用构造器注入来注入必须的依赖关系，对于可选的依赖关系，则setter注入是更好的选择，setter注入需要类提供无参构造器或者无参的静态工厂方法来创建对象。

49.Spring
Spring MVC的工作原理
① 客户端的所有请求都交给前端控制器DispatcherServlet来处理，它会负责调用系统的其他模块来真正处理用户的请求。 
② DispatcherServlet收到请求后，将根据请求的信息（包括URL、HTTP协议方法、请求头、请求参数、Cookie等）以及HandlerMapping的配置找到处理该请求的Handler（任何一个对象都可以作为请求的Handler）。 
③在这个地方Spring会通过HandlerAdapter对该处理器进行封装。 
④ HandlerAdapter是一个适配器，它用统一的接口对各种Handler中的方法进行调用。 
⑤ Handler完成对用户请求的处理后，会返回一个ModelAndView对象给DispatcherServlet，ModelAndView顾名思义，包含了数据模型以及相应的视图的信息。 
⑥ ModelAndView的视图是逻辑视图，DispatcherServlet还要借助ViewResolver完成从逻辑视图到真实视图对象的解析工作。 
⑦ 当得到真正的视图对象后，DispatcherServlet会利用视图对象对模型数据进行渲染。 
⑧ 客户端得到响应，可能是一个普通的HTML页面，也可以是XML或JSON字符串，还可以是一张图片或者一个PDF文件。

Spring中Bean的作用域？ 
在Spring的早期版本中，仅有两个作用域：singleton和prototype，前者表示Bean以单例的方式存在；后者表示每次从容器中调用Bean时，都会返回一个新的实例，prototype通常翻译为原型。
补充：设计模式中的创建型模式中也有一个原型模式，原型模式也是一个常用的模式，例如做一个室内设计软件，所有的素材都在工具箱中，而每次从工具箱中取出的都是素材对象的一个原型，可以通过对象克隆来实现原型模式。
singleton            在spring IOC容器中仅存在一个Bean实例,Bean以单实例的方式存在.

prototype            每次从容器中调用Bean时,都返回一个新的实例,即每次调用getBean()时,相当于执行new XxxBean()的操作.

request               每次HTTP请求都会创建一个新的Bean,该作用域仅适用于webApplicationContext环境.

session               同一个HTTP session共享一个Bean,不同HTTP session使用不同的Bean,该作用域仅适用于webApplicationContext环境.

globalSession   同一个全局session共享一个Bean,一般用于portlet应用环境,该作用域仅适用于webApplicationContext环境. 

在低版本的spring中,由于只有两个Bean作用域,所以采用singleton="true|false"的配置方式,spring2.0为了向后兼容,依旧支持这种配置方式.不过,spring2.0推荐采用新的配置方式:scope="<作用域类型>"
说明：单例模式和原型模式都是重要的设计模式。一般情况下，无状态或状态不可变的类适合使用单例模式。在传统开发中，由于DAO持有Connection这个非线程安全对象因而没有使用单例模式；但在Spring环境下，所有DAO类对可以采用单例模式，因为Spring利用AOP和Java API中的ThreadLocal对非线程安全的对象进行了特殊处理。
ThreadLocal为解决多线程程序的并发问题提供了一种新的思路。ThreadLocal，顾名思义是线程的一个本地化对象，当工作于多线程中的对象使用ThreadLocal维护变量时，ThreadLocal为每个使用该变量的线程分配一个独立的变量副本，所以每一个线程都可以独立的改变自己的副本，而不影响其他线程所对应的副本。从线程的角度看，这个变量就像是线程的本地变量。
ThreadLocal在多线程中是线程安全的，原因是在每个线程中，都维持着自己私有的变量threadLocals
ThreadLocal类非常简单好用，只有四个方法，能用上的也就是下面三个方法： 
- void set(T value)：设置当前线程的线程局部变量的值。 
- T get()：获得当前线程所对应的线程局部变量的值。 
- void remove()：删除当前线程中线程局部变量的值。

Spring框架中Bean的生命周期
① Spring IoC容器找到关于Bean的定义并实例化该Bean。 
② Spring IoC容器对Bean进行依赖注入。 
③ 如果Bean实现了BeanNameAware接口，则将该Bean的id传给setBeanName方法。 
④ 如果Bean实现了BeanFactoryAware接口，则将BeanFactory对象传给setBeanFactory方法。 
⑤ 如果Bean实现了BeanPostProcessor接口，则调用其postProcessBeforeInitialization方法。 
⑥ 如果Bean实现了InitializingBean接口，则调用其afterPropertySet方法。 
⑦ 如果有和Bean关联的BeanPostProcessors对象，则这些对象的postProcessAfterInitialization方法被调用。 
⑧ 当销毁Bean实例时，如果Bean实现了DisposableBean接口，则调用其destroy方法。	
	
AOP（面向切面编程）
AOP（Aspect-Oriented Programming）指一种程序设计范型，该范型以一种称为切面（aspect）的语言构造为基础，切面是一种新的模块化机制，用来描述分散在对象、类或方法中的横切关注点（crosscutting concern）。
"横切关注"是会影响到整个应用程序的关注功能，它跟正常的业务逻辑是正交的，没有必然的联系，但是几乎所有的业务逻辑都会涉及到这些关注功能。通常，事务、日志、安全性等关注就是应用中的横切关注功能。
a. 连接点（Joinpoint）：程序执行的某个特定位置（如：某个方法调用前、调用后，方法抛出异常后）。一个类或一段程序代码拥有一些具有边界性质的特定点，这些代码中的特定点就是连接点。Spring仅支持方法的连接点。 
b. 切点（Pointcut）：如果连接点相当于数据中的记录，那么切点相当于查询条件，一个切点可以匹配多个连接点。Spring AOP的规则解析引擎负责解析切点所设定的查询条件，找到对应的连接点。 
c. 增强（Advice）：增强是织入到目标类连接点上的一段程序代码。Spring提供的增强接口都是带方位名的，如：BeforeAdvice、AfterReturningAdvice、ThrowsAdvice等。很多资料上将增强译为“通知”，这明显是个词不达意的翻译，让很多程序员困惑了许久。
d. 引介（Introduction）：引介是一种特殊的增强，它为类添加一些属性和方法。这样，即使一个业务类原本没有实现某个接口，通过引介功能，可以动态的未该业务类添加接口的实现逻辑，让业务类成为这个接口的实现类。 
e. 织入（Weaving）：织入是将增强添加到目标类具体连接点上的过程，AOP有三种织入方式：①编译期织入：需要特殊的Java编译期（例如AspectJ的ajc）；②装载期织入：要求使用特殊的类加载器，在装载类的时候对类进行增强；③运行时织入：在运行时为目标类生成代理实现增强。Spring采用了动态代理的方式实现了运行时织入，而AspectJ采用了编译期织入和装载期织入的方式。 
f. 切面（Aspect）：切面是由切点和增强（引介）组成的，它包括了对横切关注功能的定义，也包括了对连接点的定义。

Spring中自动装配
- no：不进行自动装配，手动设置Bean的依赖关系。 
- byName：根据Bean的名字进行自动装配。 
- byType：根据Bean的类型进行自动装配。 
- constructor：类似于byType，不过是应用于构造器的参数，如果正好有一个Bean与构造器的参数类型相同则可以自动装配，否则会导致错误。 
- autodetect：如果有默认的构造器，则通过constructor的方式进行自动装配，否则使用byType的方式进行自动装配。
限制
- 如果使用了构造器注入或者setter注入，那么将覆盖自动装配的依赖关系。 
- 基本数据类型的值、字符串字面量、类字面量无法使用自动装配来注入。 
- 优先考虑使用显式的装配来进行更精确的依赖注入而不是使用自动装配。
	
Spring中如何使用注解来配置Bean？有哪些相关的注解？ 
在Spring配置文件中增加如下配置：
<context:component-scan base-package="org.example"/>
然后可以用@Component、@Controller、@Service、@Repository注解来标注需要由Spring IoC容器进行对象托管的类。这几个注解没有本质区别，只不过@Controller通常用于控制器，@Service通常用于业务逻辑类，@Repository通常用于仓储类（例如我们的DAO实现类），普通的类用@Component来标注。
要使用Spring MVC需要在Web项目配置文件中配置其前端控制器DispatcherServlet，如下所示：
<web-app>

    <servlet>
        <servlet-name>example</servlet-name>
        <servlet-class>
            org.springframework.web.servlet.DispatcherServlet
        </servlet-class>
        <load-on-startup>1</load-on-startup>
    </servlet>

    <servlet-mapping>
        <servlet-name>example</servlet-name>
        <url-pattern>*.html</url-pattern>
    </servlet-mapping>

</web-app>
如果需要在Web项目中使用Spring的IoC容器，可以在Web项目配置文件web.xml中做出如下配置：
<context-param>
    <param-name>contextConfigLocation</param-name>
    <param-value>classpath:applicationContext.xml</param-value>
</context-param>

<listener>
    <listener-class>
        org.springframework.web.context.ContextLoaderListener
    </listener-class>
</listener>

DBCP配置：
<bean id="dataSource"
        class="org.apache.commons.dbcp.BasicDataSource" destroy-method="close">
    <property name="driverClassName" value="${jdbc.driverClassName}"/>
    <property name="url" value="${jdbc.url}"/>
    <property name="username" value="${jdbc.username}"/>
    <property name="password" value="${jdbc.password}"/>
</bean>
<context:property-placeholder location="jdbc.properties"/>

C3P0配置：
<bean id="dataSource"
        class="com.mchange.v2.c3p0.ComboPooledDataSource" destroy-method="close">
    <property name="driverClass" value="${jdbc.driverClassName}"/>
    <property name="jdbcUrl" value="${jdbc.url}"/>
    <property name="user" value="${jdbc.username}"/>
    <property name="password" value="${jdbc.password}"/>
</bean>
<context:property-placeholder location="jdbc.properties"/>

Spring支持编程式事务管理和声明式事务管理。许多Spring框架的用户选择声明式事务管理，因为这种方式和应用程序的关联较少，因此更加符合轻量级容器的概念。声明式事务管理要优于编程式事务管理，尽管在灵活性方面它弱于编程式事务管理，因为编程式事务允许你通过代码控制业务。
事务分为全局事务和局部事务。全局事务由应用服务器管理，需要底层服务器JTA支持（如WebLogic、WildFly等）。局部事务和底层采用的持久化方案有关，例如使用JDBC进行持久化时，需要使用Connetion对象来操作事务；而采用Hibernate进行持久化时，需要使用Session对象来操作事务。

使用Spring框架的原因
- 非侵入式：支持基于POJO的编程模式，不强制性的要求实现Spring框架中的接口或继承Spring框架中的类。 
- IoC容器：IoC容器帮助应用程序管理对象以及对象之间的依赖关系，对象之间的依赖关系如果发生了改变只需要修改配置文件而不是修改代码，因为代码的修改可能意味着项目的重新构建和完整的回归测试。有了IoC容器，程序员再也不需要自己编写工厂、单例，这一点特别符合Spring的精神"不要重复的发明轮子"。 
- AOP（面向切面编程）：将所有的横切关注功能封装到切面（aspect）中，通过配置的方式将横切关注功能动态添加到目标代码上，进一步实现了业务逻辑和系统服务之间的分离。另一方面，有了AOP程序员可以省去很多自己写代理类的工作。 
- MVC：Spring的MVC框架是非常优秀的，从各个方面都可以甩Struts 2几条街，为Web表示层提供了更好的解决方案。 
- 事务管理：Spring以宽广的胸怀接纳多种持久层技术，并且为其提供了声明式的事务管理，在不需要任何一行代码的情况下就能够完成事务管理。 
- 其他：选择Spring框架的原因还远不止于此，Spring为Java企业级开发提供了一站式选择，你可以在需要的时候使用它的部分和全部，更重要的是，你甚至可以在感觉不到Spring存在的情况下，在你的项目中使用Spring提供的各种优秀的功能。
	
50.互联网开发
大型网站在架构上应当考虑哪些问题 
- 分层：分层是处理任何复杂系统最常见的手段之一，将系统横向切分成若干个层面，每个层面只承担单一的职责，然后通过下层为上层提供的基础设施和服务以及上层对下层的调用来形成一个完整的复杂的系统。计算机网络的开放系统互联参考模型（OSI/RM）和Internet的TCP/IP模型都是分层结构，大型网站的软件系统也可以使用分层的理念将其分为持久层（提供数据存储和访问服务）、业务层（处理业务逻辑，系统中最核心的部分）和表示层（系统交互、视图展示）。需要指出的是：（1）分层是逻辑上的划分，在物理上可以位于同一设备上也可以在不同的设备上部署不同的功能模块，这样可以使用更多的计算资源来应对用户的并发访问；（2）层与层之间应当有清晰的边界，这样分层才有意义，才更利于软件的开发和维护。 
- 分割：分割是对软件的纵向切分。我们可以将大型网站的不同功能和服务分割开，形成高内聚低耦合的功能模块（单元）。在设计初期可以做一个粗粒度的分割，将网站分割为若干个功能模块，后期还可以进一步对每个模块进行细粒度的分割，这样一方面有助于软件的开发和维护，另一方面有助于分布式的部署，提供网站的并发处理能力和功能的扩展。 
- 分布式：除了上面提到的内容，网站的静态资源（JavaScript、CSS、图片等）也可以采用独立分布式部署并采用独立的域名，这样可以减轻应用服务器的负载压力，也使得浏览器对资源的加载更快。数据的存取也应该是分布式的，传统的商业级关系型数据库产品基本上都支持分布式部署，而新生的NoSQL产品几乎都是分布式的。当然，网站后台的业务处理也要使用分布式技术，例如查询索引的构建、数据分析等，这些业务计算规模庞大，可以使用Hadoop以及MapReduce分布式计算框架来处理。 
- 集群：集群使得有更多的服务器提供相同的服务，可以更好的提供对并发的支持。 
- 缓存：所谓缓存就是用空间换取时间的技术，将数据尽可能放在距离计算最近的位置。使用缓存是网站优化的第一定律。我们通常说的CDN、反向代理、热点数据都是对缓存技术的使用。 
- 异步：异步是实现软件实体之间解耦合的又一重要手段。异步架构是典型的生产者消费者模式，二者之间没有直接的调用关系，只要保持数据结构不变，彼此功能实现可以随意变化而不互相影响，这对网站的扩展非常有利。使用异步处理还可以提高系统可用性，加快网站的响应速度（用Ajax加载数据就是一种异步技术），同时还可以起到削峰作用（应对瞬时高并发）。&quot；能推迟处理的都要推迟处理"是网站优化的第二定律，而异步是践行网站优化第二定律的重要手段。 
- 冗余：各种服务器都要提供相应的冗余服务器以便在某台或某些服务器宕机时还能保证网站可以正常工作，同时也提供了灾难恢复的可能性。冗余是网站高可用性的重要保证。

网站前端优化的技术  
① 浏览器访问优化： 
- 减少HTTP请求数量：合并CSS、合并JavaScript、合并图片（CSS Sprite） 
- 使用浏览器缓存：通过设置HTTP响应头中的Cache-Control和Expires属性，将CSS、JavaScript、图片等在浏览器中缓存，当这些静态资源需要更新时，可以更新HTML文件中的引用来让浏览器重新请求新的资源 
- 启用压缩 
- CSS前置，JavaScript后置 
- 减少Cookie传输 
② CDN加速：CDN（Content Distribute Network）的本质仍然是缓存，将数据缓存在离用户最近的地方，CDN通常部署在网络运营商的机房，不仅可以提升响应速度，还可以减少应用服务器的压力。当然，CDN缓存的通常都是静态资源。 
③ 反向代理：反向代理相当于应用服务器的一个门面，可以保护网站的安全性，也可以实现负载均衡的功能，当然最重要的是它缓存了用户访问的热点资源，可以直接从反向代理将某些内容返回给用户浏览器。

应用服务器优化技术
① 分布式缓存：缓存的本质就是内存中的哈希表，如果设计一个优质的哈希函数，那么理论上哈希表读写的渐近时间复杂度为O(1)。缓存主要用来存放那些读写比很高、变化很少的数据，这样应用程序读取数据时先到缓存中读取，如果没有或者数据已经失效再去访问数据库或文件系统，并根据拟定的规则将数据写入缓存。对网站数据的访问也符合二八定律（Pareto分布，幂律分布），即80%的访问都集中在20%的数据上，如果能够将这20%的数据缓存起来，那么系统的性能将得到显著的改善。当然，使用缓存需要解决以下几个问题： 
- 频繁修改的数据； 
- 数据不一致与脏读； 
- 缓存雪崩（可以采用分布式缓存服务器集群加以解决，memcached是广泛采用的解决方案）； 
- 缓存预热； 
- 缓存穿透（恶意持续请求不存在的数据）。 
② 异步操作：可以使用消息队列将调用异步化，通过异步处理将短时间高并发产生的事件消息存储在消息队列中，从而起到削峰作用。电商网站在进行促销活动时，可以将用户的订单请求存入消息队列，这样可以抵御大量的并发订单请求对系统和数据库的冲击。目前，绝大多数的电商网站即便不进行促销活动，订单系统都采用了消息队列来处理。 
③ 使用集群。 
④ 代码优化： 
- 多线程：基于Java的Web开发基本上都通过多线程的方式响应用户的并发请求，使用多线程技术在编程上要解决线程安全问题，主要可以考虑以下几个方面：A. 将对象设计为无状态对象（这和面向对象的编程观点是矛盾的，在面向对象的世界中被视为不良设计），这样就不会存在并发访问时对象状态不一致的问题。B. 在方法内部创建对象，这样对象由进入方法的线程创建，不会出现多个线程访问同一对象的问题。使用ThreadLocal将对象与线程绑定也是很好的做法，这一点在前面已经探讨过了。C. 对资源进行并发访问时应当使用合理的锁机制。 
- 非阻塞I/O： 使用单线程和非阻塞I/O是目前公认的比多线程的方式更能充分发挥服务器性能的应用模式，基于Node.js构建的服务器就采用了这样的方式。Java在JDK 1.4中就引入了NIO（Non-blocking I/O）,在Servlet 3规范中又引入了异步Servlet的概念，这些都为在服务器端采用非阻塞I/O提供了必要的基础。 
- 资源复用：资源复用主要有两种方式，一是单例，二是对象池，我们使用的数据库连接池、线程池都是对象池化技术，这是典型的用空间换取时间的策略，另一方面也实现对资源的复用，从而避免了不必要的创建和释放资源所带来的开销。
	
网络安全 
- XSS（Cross Site Script，跨站脚本攻击）是向网页中注入恶意脚本在用户浏览网页时在用户浏览器中执行恶意脚本的攻击方式。跨站脚本攻击分有两种形式：反射型攻击（诱使用户点击一个嵌入恶意脚本的链接以达到攻击的目标，目前有很多攻击者利用论坛、微博发布含有恶意脚本的URL就属于这种方式）和持久型攻击（将恶意脚本提交到被攻击网站的数据库中，用户浏览网页时，恶意脚本从数据库中被加载到页面执行，QQ邮箱的早期版本就曾经被利用作为持久型跨站脚本攻击的平台）。XSS虽然不是什么新鲜玩意，但是攻击的手法却不断翻新，防范XSS主要有两方面：消毒（对危险字符进行转义）和HttpOnly（防范XSS攻击者窃取Cookie数据）。 
- SQL注入攻击是注入攻击最常见的形式（此外还有OS注入攻击（Struts 2的高危漏洞就是通过OGNL实施OS注入攻击导致的）），当服务器使用请求参数构造SQL语句时，恶意的SQL被嵌入到SQL中交给数据库执行。SQL注入攻击需要攻击者对数据库结构有所了解才能进行，攻击者想要获得表结构有多种方式：（1）如果使用开源系统搭建网站，数据库结构也是公开的（目前有很多现成的系统可以直接搭建论坛，电商网站，虽然方便快捷但是风险是必须要认真评估的）；（2）错误回显（如果将服务器的错误信息直接显示在页面上，攻击者可以通过非法参数引发页面错误从而通过错误信息了解数据库结构，Web应用应当设置友好的错误页，一方面符合最小惊讶原则，一方面屏蔽掉可能给系统带来危险的错误回显信息）；（3）盲注。防范SQL注入攻击也可以采用消毒的方式，通过正则表达式对请求参数进行验证，此外，参数绑定也是很好的手段，这样恶意的SQL会被当做SQL的参数而不是命令被执行，JDBC中的PreparedStatement就是支持参数绑定的语句对象，从性能和安全性上都明显优于Statement。 
- CSRF攻击（Cross Site Request Forgery，跨站请求伪造）是攻击者通过跨站请求，以合法的用户身份进行非法操作（如转账或发帖等）。CSRF的原理是利用浏览器的Cookie或服务器的Session，盗取用户身份，其原理如下图所示。防范CSRF的主要手段是识别请求者的身份，主要有以下几种方式：（1）在表单中添加令牌（token）；（2）验证码；（3）检查请求头中的Referer（前面提到防图片盗链接也是用的这种方式）。令牌和验证都具有一次消费性的特征，因此在原理上一致的，但是验证码是一种糟糕的用户体验，不是必要的情况下不要轻易使用验证码，目前很多网站的做法是如果在短时间内多次提交一个表单未获得成功后才要求提供验证码，这样会获得较好的用户体验。

	
`````````  

### 个人总结

1.Java基础部分：

![image](https://github.com/caojiyuan-31/ganmuren.github.com/blob/master/size.jpg)

"SnailClimb".equals(str);//防止空值使用equals抛出抛出空指针异常

Objects.equals(str1,str2);//可以比较双空值

自动封装时 当数值在-128 ~127时，会将创建的 Integer 对象缓存起来，当下次再出现该数值时，直接从缓存中取出对应的Integer对象。
【强制】所有的 POJO 类属性必须使用包装数据类型。
【强制】RPC 方法的返回值和参数必须使用包装数据类型。
【推荐】所有的局部变量使用基本数据类型。

浮点值精度丢失问题（因为计算机是通过二进制操作的，10进制转换成2进制的时候小数位精度会丢失）
浮点数之间的等值判断，基本数据类型不能用==来比较，包装数据类型不能用 equals 来判断。
使用 BigDecimal 来定义浮点数的值并运算来保证精度（推荐使用BigDecimal(String) ，使用BigDecimal(double)仍会精度丢失 ）
BigDecimal中add()加，subtract()减，multiply()乘，divide()除，setScale()保留小数

文件内容修改（通过获取输入流再逐行写入输出流）
try{
BufferedReader in = new BufferedReader(new FileReader("in.txt"));
BufferedWriter out = new BufferedWriter(new FileWriter("out.txt"));
String s = null;
while((s = in.readLine()) != null){
out.write(s);
out.newLine();
}
out.flush();
in.close();
out.close();
}catch(IOException e){
e.printStackTrace();
}

ArrayList初始大小10，扩容机制是满值后1.5倍扩容，hashmap初始大小是16，扩容机制是达到负载时2倍扩容
Arrays.asList()将数组转换为集合后,底层其实还是数组（警告：不要在 foreach 循环里进行元素的 remove/add 操作）
正确的转换方法
1）List list = new ArrayList<>(Arrays.asList("a", "b", "c"))
2）Integer [] myArray = { 1, 2, 3 };
List myList = Arrays.stream(myArray).collect(Collectors.toList());
//基本类型也可以实现转换（依赖boxed的装箱操作）
3）int [] myArray2 = { 1, 2, 3 };
List myList = Arrays.stream(myArray2).boxed().collect(Collectors.toList());

Collections提供以下方法对List进行排序操作
void reverse(List list)：反转
void shuffle(List list),随机排序
void sort(List list),按自然排序的升序排序
void sort(List list, Comparator c);定制排序，由Comparator控制排序逻辑
void swap(List list, int i , int j),交换两个索引位置的元素
void rotate(List list, int distance),旋转。当distance为正数时，将list后distance个元素整体移到前面。当distance为负数时，将 list的前distance个元素整体移到后面。


n.额外添加
1）哈夫曼树和哈夫曼编码  
构造过程中 选取两棵根结点权值最小的树作为左右子树构造一棵新的二叉树,且置新的二叉树的根结点的权值为左右子树根结点的权值之和.
![image](https://github.com/caojiyuan-31/ganmuren.github.com/blob/master/Huffman.jpg)
