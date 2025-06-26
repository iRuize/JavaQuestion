<style>

body {
  counter-reset: h1; 
}

h1 {
    text-align: center;
    font-size: 30px !important;
    counter-reset: h2;
}

h2 {
    font-size: 26px !important;
    counter-reset: h3;
}

h3 {
    font-size: 22px !important;
    text-indent: 1em;
    counter-reset: h4;
}

h4 {
    font-size: 18px !important;
    text-indent: 3em;
    counter-reset: h5;
}

h5 {
    font-size: 14px !important;
    text-indent: 5em;
    counter-reset: h6;
}

h6 {
    font-size: 12px !important;
    text-indent: 8em;
    counter-reset: h7;
}
/* 标题自定义编号 */
h1:before {
  counter-increment: h1;
  content: counter(h1) ". ";
}
h2:before {
  counter-increment: h2;
  content: counter(h1) "." counter(h2) ". ";
}
h3:before {
  counter-increment: h3;
  content: counter(h1) "." counter(h2) "." counter(h3) ". ";
}
h4:before {
  counter-increment: h4;
  content: counter(h1) "." counter(h2) "." counter(h3) "." counter(h4) ". ";
}
h5:before {
  counter-increment: h5;
  content: counter(h1) "." counter(h2) "." counter(h3) "." counter(h4) "." counter(h5) ". ";
}
h6:before {
  counter-increment: h6;
  content: counter(h1) "." counter(h2) "." counter(h3) "." counter(h4) "." counter(h5) "." counter(h6) ". ";
}

/* 正文格式 */
span.article-text{
    display: block;
    font-size: 16px;
    text-indent: 2em;
}
</style>
# 起言
## 目录划分

<span>开始之前先梳理一下思路，目前学习过的东西已经很多了，把这些“八股文”简单的划分一下。</span>

- Java通识
  - Java的基本数据类型
  - 函数修饰符
  - 集合
  - 多线程
  - 异常
  - JVM虚拟机
    - 类加载
- 数据库
  - Mysql
  - Redis
  - MongoDB
- Spring
  - SpringMVC（简略）
  - SpringBoot
  - SpringCloud
- 常用的中间件
  - 消息队列
    - RabbitMQ
    - Kafka
  - 注册中心
    - Nacos
    - Dubbo
  - 搜索中间件
    - Elasticsearch
  - 网关
    - Gateway
    - Nginx
- 设计模式
  - 创建型
  - 结构型
  - 行为型
- 工具
  - Maven
  - Git
  - Jenkins
- 其他提升
  - 数据结构
  - 算法
# Java通识
## Java的基本数据类型
<span  class="article-text">Java的基本数据类型有四种：整数类型、浮点类型、字符类型、布尔类型。</span>

1. 整数类型：byte（1字节）、short（2字节）、int（4字节）、long（8字节）
2. 浮点类型：float (4字节)、double (8字节)
3. 字符类型：char (2字节)
4. 布尔类型：boolean (1字节)

## JDK和JRE的区别
<span class="article-text">JDK全称是Java Development Kit，是Java开发工具包，包含了JRE和编译器javac，调试器jdb，和打包工具jar。</span>

<span class="article-text">JRE全称是Java Runtime Environment，是Java运行环境，包含了JVM和Java核心类库。</span>

## 面向对象
<span class="article-text">面向对象是一种编程范式，将现实世界的物体抽象为对象，对象具有自己的属性以及行为（方法），通过对象之间的交互来实现系统的功能，具有很高的灵活性以及可扩展性</span>

## Java三大特性：封装，继承，多态
<span class="article-text">封装：是指将数据和操作数据的代码封装在一起，对外提供接口，隐藏内部的实现细节，使得外部代码只能通过接口来访问数据，从而实现信息的隐藏和保护。</span>

<span class="article-text">继承：是指一个类可以从另一个类继承其属性和方法，从而扩展自己的功能。</span>

<span class="article-text">多态：同一个接口表现出的不同行为。多态又划分为编译时多态以及运行时多态。</span>

### 编译时多态
<span class="article-text">编译时多态是指在编译阶段就确定了方法的调用对象，根据调用对象不同，选择不同的方法执行。在Java中编译时多态主要是方法重载，在源代码编译成字节码文件的时候，编译器会根据方法签名来选择调用哪个方法。</span>

### 运行时多态
<span class="article-text">运行时多态是指在运行阶段才确定方法的调用对象，根据调用对象不同，选择不同的方法执行。</span>

```java
class Animal{
    void sound(){
        System.out.println("Animal sound");
    }
}

class Dog extends Animal{
    void sound(){
        System.out.println("Dog sound");
    }
}

class Main{
    public static void main(String[] args){
        Animal dog1 = new Dog();
        Dog dog2 = new Dog();
        dog1.sound();
        dog2.sound();
    }
}
```
<span class = "article-text">在上面的代码中，Animal dog1 = new Dog(); dog1的静态类型是（编译时类型）Animal，在编译的时候编译器会检查Animal中是否有sound方法，如果有则选择该方法，如果没有则报错。在运行的时候，JVM根据变量引用的动态类型（运行时类型）也就是实际类型来决定调用哪个方法，dog1的实际类型是Dog，所以调用的实际方法是Dog的sound方法。这个就是运行时多态，在运行的时候才确定方法的调用对象。</span>
<span class="article-text">在上述代码中的两个dog对象是不一样的，对于dog1来说，他可以访问的方法是Animal中的非私有方法或者是Dog中已经**重写**的方法，而对于dog2来说，他可以访问的方法是Animal中非私有可以继承过来的方法以及Dog中独有的方法。</span>


## Java的优势是什么？
1. 跨平台：由于JVM java 虚拟机的存在，可以实现一次编写多次运行。
2. 垃圾回收：Java的 GC 自动实现垃圾回收，不需要人工干预，简化开发过程。
3. 生态：Java的生态非常丰富，有大量的第三方库可以帮助开发者解决问题。
4. 面向对象：Java支持面向对象，可以将现实世界的物体抽象为对象，具有很高的灵活性以及可扩展性。

## 函数修饰符
<span>Java中函数的修饰符有四种：</span>

1. public：公有修饰符，可以被所有类访问
2. private：私有修饰符，只能被同一个类访问
3. protected：受保护修饰符，可以被同一个包内的类访问或者是其他包下的子类访问
4. static：静态修饰符，可以被静态方法、静态变量访问
5. final：最终修饰符，可以被子类继承，不能被修改
6. abstract：抽象修饰符，不能实例化，只能被子类继承
7. synchronized：同步修饰符，可以保证线程安全
8. native：本地修饰符，可以调用本地方法
   
## == 和 equals 的区别
<span class = "article-text">在基本数据类型中只能使用 == 来比较两个对象的内存地址是否一致，不能使用 equals 方法，会直接报错。</span>
<span class = "article-text">equals 在没有重写之前和 == 是相同的，在方法重写之后需要根据equals的具体方法来考虑，对于 == 而言的话，如果是基本数据类型，则比较的是值，如果是引用类型，则比较的是引用地址。</span>

## 序列化和反序列化
<span class = "article-text">序列化：将一个对象转换为字节流，字节流可以保存到文件，数据库缓存中，便于传递。</span>
1. 存储用户的设置
2. 存储未付款的订单

<span class = "article-text">反序列化：将字节流转换为一个对象。</span>
1. 从文件中读取用户的设置
2. 从数据库中读取未付款的订单

<span class = "article-text">使用场景：用户将本地设置上传到云端，可以分享给其他用户或者是等待以后再用当前app时可以快捷更改设置。将用户当前的设置存储为文件，然后数据库中保存这个文件

## 接口和抽象类有什么区别
### 接口
<span class = "article-text">接口中只是保存具体的方法名称以及方法参数，没有方法体，接口可以多继承比如接口A实现了方法A，B接口实现了方法B，C接口继承A和B，C接口中定了方法C，这个时候一个类如果要实现接口C的话需要实现A,B,C三个方法，代码如下：</span>

```java
public interface interfaceA{
    public void methodA();
}
public interface interfaceB{
    public void methodB();
}
public interface interfaceC extends interfaceA, interfaceB{
    public void methodC();
}
// 实现接口C
public class classC implements interfaceC{
    public void methodA(){
      sout("methodA");
      }
      public void methodB(){
        sout("methodB");
      }
      public void methodC(){
        sout("methodC");
      }
}
```

### 抽象类
<span class = "article-text">首先明确的一点内容是，抽象类也是一个类！只不过是加上了abstract关键字，抽象类无法被实例化，也就是说无法通过new的方式创建这个抽象类的对象，只能是继承抽象类。

```java
public abstract class Animal{
    // 抽象方法，子类必须要实现
    public abstract void eat();
    // 非抽象方法，子类可以选择是否实现
    public void sleep(){
        System.out.println("Animal sleep");
    }
}

public class Dog extends Animal{
    // 重写抽象父类的抽象方法
    public void eat(){
        System.out.println("Dog eat");
    }
}
```

<span class = article-text>抽象类之间的继承：抽象类可以继承另一个抽象类，但是无法实现多继承，抽象子类可以选择不实现抽象父类中的抽象方法。

```java
// 抽象父类
abstract class Animal {
    abstract void makeSound();  // 抽象方法
    public void eat() {
        System.out.println("正在吃饭...");
    }
}

// 抽象子类继承抽象父类
abstract class Dog extends Animal {
    abstract void guardHouse();  // 新增抽象方法
    // 可以不实现 makeSound()
}

// 普通类继承抽象子类
class Husky extends Dog {
    @Override
    public void makeSound() {
        System.out.println("哈士奇叫：嗷呜～");
    }
    // 这里只需要实现抽象子类的抽象方法 guardHouse()即可
    @Override
    public void guardHouse() {
        System.out.println("哈士奇守家...大概吧？");
    }
}
```
<span class = "article-text">通过上述内容基本就可以对抽象类以及接口有一个合理的了解，在实际开发中，我们应该尽量使用接口而不是抽象类，因为接口更加灵活，可以实现多继承，并且接口可以被多个类实现，而抽象类只能被继承，不能被实例化。


## 继承
<span class = "article-text">这里的问题出现在构造函数上，先说结论，如果父类**只有**一个全参构造函数，那么子类的构造函数必须用super把这个全参的部分调用过来,子类自己写的其余字段可以不加入进去，如下代码所示。

```java
public class Person implements Serializable{
    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}

public class Child extends Person{
    private String address;

    // 这里的地址可写可不写
    public Child(String name, int age, String address) {
        super(name,age);
    }
}
```
<span class = "article-text">如果父类有多个字段，并且存在1个字段，2个字段，以及全参的构造函数，子类可以选择调用父类的构造函数，比如构造函数super(name)

### Java为什么不支持多继承
<span class = "article-text">Java不支持多继承，原因是容易出现钻石问题
<span class = "article-text">比如B和C一起继承了A，D继承了B和C，那么D对于同一个方法，B和C有不同的实现，此时会出现歧义。

#### 追问：接口是否可以多继承
<span class = "article-text">接口可以多继承，因为接口中不包含方法体，只包含方法签名，所以接口可以实现多个接口，但是接口不能继承其他类。

## Java中的参数传递机制
<span class = "article-text">Java中无论是基本数据类型还是引用数据类型统一都是按照**值传递**的</span>
<span class = "article-text">值传递：传递给函数的都是当前变量所存储的值的副本，也就是这个变量实际代表了什么</span>

### 基本数据类型值传递
```java
public void change(int a) {
    a = 10;
}

int x = 5;
change(x);
System.out.println(x);  // 仍然是 5
```
<span class = "article-text">在上述代码中传递的是x，x变量代表的是5，所以在函数中实际是对5进行修改，但是在函数执行完毕后，x的值还是5，因为传递的是副本，并没有影响到原来的变量。</span>

### 引用数据类型值传递
第一种情况
```java
public void change(Person p) {
    p = new Person("Tom", 20);
}

Person p1 = new Person("Jerry", 18);
change(p1);
System.out.println(p1.getName());  // 仍然是 "Jerry"
```
<span class = "article-text">这里在调用change(p1)的时候会向函数内传递p1所代表的内存地址，这个地址会赋值给p，但是p = new Person("Tom", 20);这句话只是创建一个新的Person对象，更改p的指向，并不会改变p1的指向，所以在函数执行完毕后，p1的name仍然是"Jerry"。</span>
第二种情况

```java
public void changeName(Person p) {
    p.name = "Tom";
}

Person person1 = new Person("Jerry");
changeName(person1);
// 会输出Tom
System.out.println(person1.name);  
```
<span class = "article-text">这里传递过去之后，直接把person1内存地址下的name更改了，所以在下方输出的时候才会输出新的值Tom</span>

# 集合
## Java中集合的种类：

1. List：列表，元素有序、可重复
2. Set：集合，元素无序、不可重复
3. Map：映射，元素是键值对，键不可重复
4. Queue：队列，元素有序、先进先出
# 多线程
## 线程的创建方式
1. 继承Thread类
2. 实现Runnable接口
3. 实现CallAble接口
4. 通过线程池的方式创建线程
   
## volatile关键字
<span class = "article-text">volatile关键字是Java提供的一种轻量级的同步机制，用来确保变量的可见性，当一个变量被volatile修饰时，它会强制所有线程都从主内存中读取变量的值，而不会从线程缓存或寄存器中读取，从而可以确保所有线程都能看到该变量的最新值。</span>

## Synchronized关键字s
<span class = "article-text">synchronized 关键字包裹的代码块或方法，在同一时刻只能被一个线程执行，保证临界区代码的互斥访问，防止数据竞争。

```java
public class SafeCounter {
    private int count = 0;

    // 使用synchronized关键字修饰方法，保证同一时刻只有一个线程执行increment
    public synchronized void increment() {
        count++;
    }

    // 读取count时也加锁，确保读写一致性
    public synchronized int getCount() {
        return count;
    }

    public static void main(String[] args) throws InterruptedException {
        SafeCounter counter = new SafeCounter();

        // 创建多个线程同时调用increment
        Thread t1 = new Thread(() -> {
            for (int i = 0; i < 10000; i++) {
                counter.increment();
            }
        });

        Thread t2 = new Thread(() -> {
            for (int i = 0; i < 10000; i++) {
                counter.increment();
            }
        });

        t1.start();
        t2.start();
//        主线程调用join挂起自己，直到t1和t2执行完毕
        t1.join();
        t2.join();

        System.out.println("最终计数值：" + counter.getCount()); // 预期是20000
    }
}
```
## CAS 关键字
<span class = "article-text">CAS（Compare And Swap）是一种无锁算法，是一种原子操作，是一种用于多线程编程的技术。CAS算法是通过硬件保证的，通过CAS指令，可以保证一个变量的原子性操作，即对一个变量进行读-修改-写操作，是一个原子操作。
<span class = "article-text">如果当前的值等于旧值，那么就对当前值进行修改，否则什么都不做。这样就可以保障如果在变更值的过程中，其他线程修改了当前值，变更值操作就会失败</span>
**示例**
<span class = "article-text">银行转账余额有1000，想转出500，余下500，但是点击确定之前别的操作已经把余额该到了500，此时就会CAS失败，导致转账失败。

## ConcurrentHashMap为什么是线程安全的
<span class = "article-text">ConcurrentHashMap是线程安全的，原因是它内部使用了CAS和Synchronized锁机制来保证线程安全的。</span>

1. 添加数据的时候如果桶为空，仅仅使用CAS就可以实现线程安全，不会出现竞争条件。
   1. 可能出现两个线程同时往桶内写入数据，如果不使用CAS就会造成两个数据写入同一个位置，导致数据丢失。
2. 添加数据时如果桶不为空，需要使用Synchronized锁机制，保证线程安全。
   1. Synchornized锁会锁住对应的桶链表的第一个节点，保证线程安全。
3. 读操作是无锁的
   1. 节点数据是被Volatile关键字修饰的
4. 删除数据时如果桶不为空，需要使用Synchronized锁机制，保证线程安全。
   1. Synchornized锁会锁住对应的桶链表的第一个节点，保证线程安全。
5. 删除数据时如果桶为空，不需要操作

### ConcurrentHashMap的扩容机制
1. sizeCtl = 0.75 * capacity; // 当前桶数组容量 * 负载因子，当实际存储的节点数 size >= sizeCtl 时，就会触发扩容；扩容时，将数组扩大为原来的 2 倍。
2. 设置扩容状态sizeCtl = -1; // 负值表示正在扩容
3. 多个线程一起迁移数据
4. 将已经迁移完成的桶设置标记ForwardingNode，并将ForwardingNode的next指针指向新的数组，然后将ForwardingNode置为null，表示迁移完成。
5. 所有桶迁移完成之后table指向新的数组，sizeCtl = 0，表示扩容完成。

<span class = "article-text">ConcurrentHashMap内部是数组+链表/红黑树的结构（类似于HashMap），每次只对对应的桶加锁。</span>

## 线程的生命周期
1. 新建状态：线程刚被创建，但还没有开始运行。
2. 就绪状态：线程已经准备好运行，等待CPU分配时间片。
3. 运行状态：线程正在运行，占用CPU资源。
4. 阻塞状态：线程因为某种原因放弃CPU资源，暂时停止运行。
5. 死亡状态：线程已经执行完毕，或者被其他线程终止。


# SpringCloud
## Nacos
<span class = "article-text"> Nacos：配置中心+注册中心

1. 在Docker中下载运行Nacos的镜像文件
2. 配置Nacos
```Shell
docker run -d \
--name nacos \
--env-file ./nacos/custom.env \
-p 8848:8848 \
-p 9848:9848 \
-p 9849:9849 \
--network my-net \
nacos/nacos-server:v2.1.0-slim
```
1. 启动Nacos
2. 在项目对应的pom.xml文件中添加依赖
  
```xml
<dependency>  
    <groupId>com.alibaba.cloud</groupId>  
    <artifactId>spring-cloud-starter-alibaba-nacos-discovery</artifactId>  
    <version>2.2.6.RELEASE</version>  
</dependency>
```
5. 在配置文件中添加配置
```yaml
spring:
  application:
    name: cart-service   #这里是微服务的具体名称
  cloud:
    nacos:
      discovery:
        server-addr: 192.168.211.130:8848 #这里写Nacos运行的具体地址
```
6. 在启动类上添加注解  @EnableDiscoveryClient
```java
@EnableDiscoveryClient
@SpringBootApplication
public class NacosProviderApplication {
    public static void main(String[] args) {
        SpringApplication.run(NacosProviderApplication.class, args);
    }
}
```
## OpenFeign的使用方法
1. 在pom.xml文件中添加OpenFeign和负载均衡依赖
```xml
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-openfeign</artifactId>
</dependency>
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-loadbalancer</artifactId>
</dependency>
```
2. 在配置文件中添加配置
```yaml
feign:
  hystrix:
    enabled: true #开启熔断机制
  compression:
    request:
      enabled: true #开启请求压缩
      mime-types: text/xml,application/xml,application/json #压缩的类型
      min-request-size: 2048 #压缩的最小大小
  client:
    config:
      default:
        connectTimeout: 10000 #连接超时时间
        readTimeout: 5000 #读取超时时间
        loggerLevel: basic #日志级别
```
3. 在启动类上添加注解  @EnableFeignClients
```java
@EnableFeignClients
@SpringBootApplication
public class OpenFeignApplication {
    public static void main(String[] args) {
        SpringApplication.run(OpenFeignApplication.class, args);
    }
}
```
4. 编写OpenFeign接口
```java
@FeignClient("item-service")
public interface itemClient {
    @GetMapping("/items")
    List<ItemDto> queryItemsByIds(@RequestParam("ids") List<Long> ids)
}
```
    
5. 在调用接口的方法中注入ProviderService
```java
@RestController
public class ConsumerController {
    @Autowired
    private final Itemclient itemclient;

    @GetMapping("/consumer/hello")
    public String hello() {
        return itemClient.queryItemByIds(Arrays.asList(1L, 2L, 3L));
    }
} 
```
6. 当定义的Feign接口和调用的Feign接口不在同一个项目中时，需要在**启动类**上添加注解
```java
    @EnableFeignClients(basePackages = "com.hmall.api.clients")
```
## 网关
1. 创建一个网关模块，
2. 导入必要的依赖
```xml
<dependency>
  <!--网关-->
  <dependency>
    <groupId>org.springframework.cloud</groupId>
      <artifactId>spring-cloud-starter-gateway</artifactId>
  </dependency>
  <!-- 注册中心Nacos -->
  <dependency>
    <groupId>com.alibaba.cloud</groupId>
      <artifactId>spring-cloud-starter-alibaba-nacos-discovery</artifactId>
  </dependency>
  <!--负载均衡-->
  <dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-loadbalancer</artifactId>
  </dependency>
</dependency>
```
3. 配置文件中添加配置
```yaml
server:
  port: 8080
spring:
  application:
    name: gateway
  cloud:
    nacos:
      server-addr: 192.168.150.101:8848
    gateway:
      routes:
        - id: item # 自定义名称，给人类看的
          uri: lb://item-service # 路由的目标服务，需要和目标服务的application.name相同
          predicates: # 路由断言，匹配规则
            - Path=/items/**,/search/** 
        - id: cart
          uri: lb://cart-service
          predicates:
            - Path=/carts/**
        - id: user
          uri: lb://user-service
          predicates:
            - Path=/users/**,/addresses/**
```
## Nacos作为配置中心：配置共享
<span class = "article-text">在Nacos上新建一个配置项，然后在各个微服务的配置文件中添加配置项的地址，这样就可以实现配置共享。
<span class = "article-text">方案：这里出现的问题是yaml文件是SpringCloud上下文在初始化的时候读取的，如果yaml文件中不写入nacos的地址，那么启动会报错
<span class = "article-text">解决：新建一个BootStrap文件，在里边写入基本的配置内容
![配置读取顺序](../images/配置读取流程.png)
<span class = "article-text">将nacos地址配置到bootstrap.yaml中，那么在项目引导阶段就可以读取nacos中的配置了。

1. 在对应的微服务下添置配置依赖
```xml
<!--nacos配置管理-->
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-config</artifactId>
</dependency>
```

2.  在cart-service的Resource文件下添加bootstrap.yaml文件
```yaml
spring:
  application:
    name: cart-service
  cloud:
    nacos:
      discovery:
        server-addr: 192.168.211.130:8848
  profiles:
    active: dev
    config:
        file-extension: yaml # 文件后缀名
        shared-configs: # 共享配置
          - dataId: shared-jdbc.yaml # 共享mybatis配置
          - dataId: shared-log.yaml # 共享日志配置
          - dataId: shared-swagger.yaml # 共享日志配置
```
3. 修改原本的yaml文件
  
##  Nacos作为配置中心：配置热更新
1. 在Nacos中新建一个配置类，比如：cart-service.yaml
```yaml
hm:
  cart:
    maxAmount: 1 # 购物车商品数量上限
```
2. 在对应的微服务中新建一个属性读取类
```java
@Data
@Component
@ConfigurationProperties(prefix = "hm.cart")
public class CartProperties {
    private Integer maxAmount;  //这里的变量名要和yaml文件中的变量名一致
}
```
3. 在业务代码中注入这个类并且在业务代码加上@RefreshScope注解即可使用

## Sentienl入门
<span class = "article-text">Sentienl是一个开源的分布式微服务网关，它可以作为微服务架构中的网关层，为微服务架构提供统一的服务接入、安全、流量控制、熔断降级等功能。Sentienl以jar包的形式保存在了本地，运行的话只需要启动命令

```Shell
java -Dserver.port=8090 -Dcsp.sentinel.dashboard.server=localhost:8090 -Dproject.name=sentinel-dashboard -jar sentinel-dashboard.jar
```
<span class = "article-text">接下来在浏览器中输入8090端口即可进入到Sentienl的控制台。默认的账号密码都是Sentinel。

1. 在对应的微服务组件中引入依赖
```xml
<dependency>
    <groupId>com.alibaba.cloud</groupId>
    <artifactId>spring-cloud-starter-alibaba-sentinel</artifactId>
</dependency>
```
2. 在配置文件中添加Sentienl的配置
```yaml
spring:
  sentinel:
    transport:
      dashboard: localhost:8090 #Sentienl控制台地址
      port: 8090 #Sentienl的端口号
    http-method-specify: true # 开启请求方式前缀
```
3.  | QPS | TPS |
    | :--: | :--: |
    | 每秒请求数 | 每秒事务数 |
4. QPS：每秒请求数，即每秒钟系统能够处理的请求数量，QPS越高，系统的吞吐量越大。
5. TPS：每秒事务数，即每秒钟系统能够处理的事务数量，TPS越高，系统的吞吐量越大。

## 分布式事务：Seata
<span class = "article-text">Seat在事务管理中扮演3个角色：
-  TC (Transaction Coordinator) - 事务协调者：维护全局和分支事务的状态，协调全局事务提交或回滚。 
-  TM (Transaction Manager) - 事务管理器：定义全局事务的范围、开始全局事务、提交或回滚全局事务。 
-  RM (Resource Manager) - 资源管理器：管理分支事务，与TC交谈以注册分支事务和报告分支事务的状态，并驱动分支事务提交或回滚。
  
1. 导入资料文件中的seata-tc.sql文件到mysql数据库中，实现Seata的数据持久化
2. 将资料文件中的seata文件夹导入到虚拟机的/root目录下
3. docker部署seata-server
4. 给参与分布式事务的每一个微服务引入Seata的依赖
```xml
<!--统一配置管理-->
  <dependency>
      <groupId>com.alibaba.cloud</groupId>
      <artifactId>spring-cloud-starter-alibaba-nacos-config</artifactId>
  </dependency>
  <!--读取bootstrap文件(这个可以不写，具体要看版本)-->
  <dependency>
      <groupId>org.springframework.cloud</groupId>
      <artifactId>spring-cloud-starter-bootstrap</artifactId>
  </dependency>
  <!--seata-->
  <dependency>
      <groupId>com.alibaba.cloud</groupId>
      <artifactId>spring-cloud-starter-alibaba-seata</artifactId>
  </dependency>
```
5. 在Nacos配置中心中添加共享Seata的配置：shared-seata.yaml
```yaml
seata:
  registry: # TC服务注册中心的配置，微服务根据这些信息去注册中心获取tc服务地址
    type: nacos # 注册中心类型 nacos
    nacos:
      server-addr: 192.168.150.101:8848 # nacos地址
      namespace: "" # namespace，默认为空
      group: DEFAULT_GROUP # 分组，默认是DEFAULT_GROUP
      application: seata-server # seata服务名称
      username: nacos
      password: nacos
  tx-service-group: hmall # 事务组名称
  service:
    vgroup-mapping: # 事务组与tc集群的映射关系
      hmall: "default"
```
6. 在微服务中添加bootstrap.yaml文件，并添加seata的配置
```yaml
spring:
  application:
    name: trade-service # 服务名称
  profiles:
    active: dev
  cloud:
    nacos:
      server-addr: 192.168.211.139 # nacos地址
      config:
        file-extension: yaml # 文件后缀名
        shared-configs: # 共享配置
          - dataId: shared-jdbc.yaml # 共享mybatis配置
          - dataId: shared-log.yaml # 共享日志配置
          - dataId: shared-swagger.yaml # 共享日志配置
          - dataId: shared-seata.yaml # 共享seata配置
```
7. 改造原本的yaml配置文件
```yaml
server:
  port: 8085
feign:
  okhttp:
    enabled: true # 开启OKHttp连接池支持
  sentinel:
    enabled: true # 开启Feign对Sentinel的整合
hm:
  swagger:
    title: 交易服务接口文档
    package: com.hmall.trade.controller
  db:
    database: hm-trade
```
8. 将Seata-at.sql文件导入到对应事务涉及到的mysql数据库中，实现Seata的AT模式的分布式事务
9. 将原本事务处理的方法@Transactional注解改为@GlobalTransactional注解

## 消息队列MQ：RaabitMQ 
<span class = "article-text">1.RabbitMQ是用来实现异步调用的消息队列。
<span class = "article-text">2.比如原本的逻辑链条是A-B-C当我们请求发出之后，ABC被调用，全部是阻塞状态，这时候其他请求如果需要的微服务组件也是ABC的话就需要等待，但是如果引入MQ的话，我们请求只需要调用A即可，A会利用MQ通知BC，此时请求就可以结束，大大提高了工作效率。
<span class = "article-text">3.RabbitMQ的适用场景：无需立刻给用户返回结果或者是不需要返回结果，比如用户点击购买，如果库存有价格合适直接返回成功，至于库存-1，这个就可以交给MQ来做，提高了效率。

1. Docker中启动mq
2. 打开后台地址：http://192.168.211.130:15672/#/
3. 账号密码为：admin/1234
4. 在项目中导入MQ依赖
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-amqp</artifactId>
</dependency>
```
5. 在配置文件中添加MQ的配置
```yaml 
spring:
  rabbitmq:
    host: 192.168.211.130
    port: 5672
    username: admin
    password: 1234
    virtual-host: /
```
6. 在需要调用的微服务中注入RabbitTemplate
```java
@Autowired
private RabbitTemplate rabbitTemplate;
```
7. 简单调用MQ的方法
```java
public void testSimpleQueue() {
        // 队列名称
        String queueName = "simple.queue";
        // 消息
        String message = "hello, spring amqp!";
        // 发送消息，语法
        //rabbitTemplate.convertAndSend(".exchangename", "routing.key", "message");
        //表示使用默认交换机,队列是simple.queue,消息是hello, spring amqp!
        rabbitTemplate.convertAndSend(queueName," ", message);
        
    }

```
8. 启动消费者监听MQ
```java
@RabbitListener(queues = "queue.name")
    public void listenSimpleQueueMessage(String msg) throws InterruptedException {
        System.out.println("spring 消费者接收到消息：【" + msg + "】");
    }
```
9. 交换机的引入
交换机的类型有四种：
- Fanout：广播，将消息交给所有绑定到交换机的队列。
- Direct：订阅，基于RoutingKey（路由key）发送给订阅了消息的队列
- Topic：通配符订阅，与Direct类似，只不过RoutingKey可以使用通配符
- Headers：头匹配，基于MQ的消息头匹配，用的较少。
10. 在Fanout的情况下，消息会被交换机绑定的所有的队列消费；routing.key 被忽略，所有绑定的队列都收到消息
11. 在Direct的情况下，消息会被交换机绑定的队列消费，routing.key 必须与队列的binding key 一致才会被消费。模拟场景下两个队列emailQueue：接收 email 类型的消息，smsQueue：接收 sms 类型的消息交换机名称为：directExchange，使用 routingKey：email 和 sms
```java
//配置类
@Configuration
public class RabbitConfig {

    // 定义 Direct 类型的交换机
    @Bean
    public DirectExchange directExchange() {
        return new DirectExchange("directExchange");
    }

    // 定义 email 队列
    @Bean
    public Queue emailQueue() {
        return new Queue("emailQueue");
    }

    // 定义 sms 队列
    @Bean
    public Queue smsQueue() {
        return new Queue("smsQueue");
    }

    // 绑定 email 队列和交换机，routingKey 为 "email"
    @Bean
    public Binding bindingEmail(Queue emailQueue, DirectExchange directExchange) {
        return BindingBuilder.bind(emailQueue).to(directExchange).with("email");
    }

    // 绑定 sms 队列和交换机，routingKey 为 "sms"
    @Bean
    public Binding bindingSms(Queue smsQueue, DirectExchange directExchange) {
        return BindingBuilder.bind(smsQueue).to(directExchange).with("sms");
    }
}
//生产者
@Component
public class MessageProducer {

    @Autowired
    private RabbitTemplate rabbitTemplate;

    public void sendEmailMessage(String message) {
        rabbitTemplate.convertAndSend("directExchange", "email", message);
    }

    public void sendSmsMessage(String message) {
        rabbitTemplate.convertAndSend("directExchange", "sms", message);
    }
}
//消费者
@Component
public class MessageConsumer {

    @RabbitListener(queues = "emailQueue")
    public void receiveEmail(String message) {
        System.out.println("收到邮件消息：" + message);
    }

    @RabbitListener(queues = "smsQueue")
    public void receiveSms(String message) {
        System.out.println("收到短信消息：" + message);
    }
}
```

12. 在Direct的情况下routing.key 支持 模糊匹配（使用 * 和 # 通配符）；order.* 可以匹配 order.create、order.update这里采用注解的形式来举例
```java
@Component
public class TopicMessageConsumer {

    // 监听队列 email.topic.queue，自动声明并绑定到 topicExchange，routingKey 为 "notice.email"
    @RabbitListener(
        bindings = @QueueBinding(
            value = @Queue(value = "email.topic.queue", durable = "true"),
            exchange = @Exchange(value = "topicExchange", type = ExchangeTypes.TOPIC),
            key = "notice.email"
        )
    )
    public void handleEmailMessage(String message) {
        System.out.println("【邮件消费者】收到消息：" + message);
    }

    // 监听队列 sms.topic.queue，routingKey 为 notice.sms
    @RabbitListener(
        bindings = @QueueBinding(
            value = @Queue(value = "sms.topic.queue", durable = "true"),
            exchange = @Exchange(value = "topicExchange", type = ExchangeTypes.TOPIC),
            key = "notice.sms"
        )
    )
    public void handleSmsMessage(String message) {
        System.out.println("【短信消费者】收到消息：" + message);
    }
}
//生产者
@RestController
@RequestMapping("/send")
public class TopicMessageProducer {

    @Autowired
    private RabbitTemplate rabbitTemplate;

    @GetMapping("/email")
    public String sendEmailMsg() {
        String message = "通知：您有一封新邮件，请查收。";
        rabbitTemplate.convertAndSend("topicExchange", "notice.email", message);
        return "邮件消息发送成功！";
    }

    @GetMapping("/sms")
    public String sendSmsMsg() {
        String message = "通知：您收到一条短信，请查收。";
        rabbitTemplate.convertAndSend("topicExchange", "notice.sms", message);
        return "短信消息发送成功！";
    }

    //这个接收不到
    @GetMapping("/other")
    public String sendOtherMsg() {
        String message = "系统广播：所有人都能收到！";
        rabbitTemplate.convertAndSend("topicExchange", "notice.all", message);
        return "其他消息发送成功！";
    }
}
```
<span class = "article-text">在交换机设置中，如果routingKey设置为notice.*则表示可以匹配notice开头的内容，例如notice.email、notice.sms等，但是无法匹配notice.sms.info这种

## MQ高级
### 生产者重试机制
<span class = "article-text">修改配置文件，添加以下配置

```yaml
spring:
  rabbitmq: # RabbitMQ配置
    host: 192.168.211.130
    port: 5672
    username: admin
    password: 1234
    virtual-host: /
    retry:
      enabled: true # 开启重试机制
      max-attempts: 3 # 最大重试次数
      initial-interval: 1000 # 第一次重试的间隔时间
      multiplier: 1.5 # 间隔时间乘数
      max-interval: 30000 # 最大重试间隔时间
```
### 生产者确认机制
在publiser模块的yaml文件中添加配置
```yaml
spring:
  rabbitmq: # RabbitMQ配置    
    host: 192.168.211.130
    port: 5672
    username: admin
    password: 1234
    virtual-host: /
    publisher-confirms-type: true # 开启生产者确认机制
    publisher-returns: true # 开启发布返回
```
<span class = "article-text">这里publisher-confirms-type有三种模式可以选择：
- none：不开启生产者确认机制，默认模式
- simple：开启简单模式，只要消息被投递到队列，生产者会收到一个确认，如果消息没有被投递到队列，生产者会收到一个拒绝
- correlated：启用 confirm 并支持 CorrelationData，可以让生产者在发送消息时附带一个 CorrelationData，当消费者接收到消息并处理完后，可以调用 confirm(CorrelationData) 来确认消息已经被消费。

<span class = "article-text">新建一个配置包config，添加如下代码实现发送失败输出日志

```java
@Configuration
public class RabbitConfig {

    @Bean
    public RabbitTemplate rabbitTemplate(final ConnectionFactory connectionFactory) {
        final RabbitTemplate rabbitTemplate = new RabbitTemplate(connectionFactory);
        rabbitTemplate.setConfirmCallback(new RabbitTemplate.ConfirmCallback() {
            @Override    
            public void confirm(CorrelationData correlationData, boolean ack, String cause) {
                if (!ack) {
                    log.error("消息发送失败，原因：{}", cause);
                }
            }
        });
        rabbitTemplate.setReturnCallback(new RabbitTemplate.ReturnCallback() {
            @Override
            public void returnedMessage(Message message, int replyCode, String replyText, String exchange, String routingKey) {
                log.error("消息发送失败，交换机：{}, 路由键：{}, 回复码：{}, 回复信息：{}", exchange, routingKey, replyCode, replyText);
            }
        });
        return rabbitTemplate;
    }
}
```
<span class = "article-text">在 RabbitMQ 的生产者确认机制中：

1. ConfirmCallback（确认是否投递到 交换机）；如果交换机存在，那么就返回ack = true，否则返回false。
2. ReturnCallback（确认是否从交换机成功 路由到队列）；如果交换机名称正确，routingKey错了，那么消息是可以正常达到交换机的，但是无法路由到队列，此时setReturnCallback会输出日志。

### MQ的持久化