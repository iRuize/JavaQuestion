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
# Java学习笔记
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
# SpringCloud
## Nacos
<span class = "article-text"> Nacos使用方法

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
3. 启动Nacos
4. 在项目对应的pom.xml文件中添加依赖
  
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