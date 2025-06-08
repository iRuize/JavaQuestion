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
## Java通识
### Java的基本数据类型
<span  class="article-text">Java的基本数据类型有四种：整数类型、浮点类型、字符类型、布尔类型。</span>

1. 整数类型：byte（1字节）、short（2字节）、int（4字节）、long（8字节）
2. 浮点类型：float (4字节)、double (8字节)
3. 字符类型：char (2字节)
4. 布尔类型：boolean (1字节)

### JDK和JRE的区别
<span class="article-text">JDK全称是Java Development Kit，是Java开发工具包，包含了JRE和编译器javac，调试器jdb，和打包工具jar。</span>

<span class="article-text">JRE全称是Java Runtime Environment，是Java运行环境，包含了JVM和Java核心类库。</span>

### 面向对象
<span class="article-text">面向对象是一种编程范式，将现实世界的物体抽象为对象，对象具有自己的属性以及行为（方法），通过对象之间的交互来实现系统的功能，具有很高的灵活性以及可扩展性</span>

### Java三大特性：封装，继承，多态
<span class="article-text">封装：是指将数据和操作数据的代码封装在一起，对外提供接口，隐藏内部的实现细节，使得外部代码只能通过接口来访问数据，从而实现信息的隐藏和保护。</span>

<span class="article-text">继承：是指一个类可以从另一个类继承其属性和方法，从而扩展自己的功能。</span>

<span class="article-text">多态：同一个接口表现出的不同行为。多态又划分为编译时多态以及运行时多态。</span>

#### 编译时多态
<span class="article-text">编译时多态是指在编译阶段就确定了方法的调用对象，根据调用对象不同，选择不同的方法执行。在Java中编译时多态主要是方法重载，在源代码编译成字节码文件的时候，编译器会根据方法签名来选择调用哪个方法。</span>

#### 运行时多态
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
<span class = "article-text">在上面的代码中，Animal dog1 = new Dog(); dog1的静态类型是Animal，在编译的时候编译器会检查Animal中是否有sound方法，如果有则选择该方法，如果没有则报错。在运行的时候，JVM根据变量引用的动态类型也就是实际类型来决定调用哪个方法，dog1的实际类型是Dog，所以调用的实际方法是Dog的sound方法。这个就是运行时多态，在运行的时候才确定方法的调用对象。</span>
<span class="article-text">在上述代码中的两个dog对象是不一样的，对于dog1来说，他可以访问的方法是Animal中的非私有方法或者是Dog中已经**重写**的方法，而对于dog2来说，他可以访问的方法是Animal中非私有可以继承过来的方法以及Dog中独有的方法。</span>


### Java的优势是什么？
1. 跨平台：由于JVM java 虚拟机的存在，可以实现一次编写多次运行。
2. 垃圾回收：Java的 GC 自动实现垃圾回收，不需要人工干预，简化开发过程。
3. 生态：Java的生态非常丰富，有大量的第三方库可以帮助开发者解决问题。
4. 面向对象：Java支持面向对象，可以将现实世界的物体抽象为对象，具有很高的灵活性以及可扩展性。
### 函数修饰符

<span>Java中函数的修饰符有四种：</span>

1. public：公有修饰符，可以被所有类访问
2. private：私有修饰符，只能被同一个类访问
3. protected：受保护修饰符，可以被同一个包内的类访问或者是其他包下的子类访问
4. static：静态修饰符，可以被静态方法、静态变量访问
5. final：最终修饰符，可以被子类继承，不能被修改
6. abstract：抽象修饰符，不能实例化，只能被子类继承
7. synchronized：同步修饰符，可以保证线程安全
8. native：本地修饰符，可以调用本地方法
### == 和 equals 的区别
<span>在基本数据类型中只能使用 == 来比较两个对象的内存地址是否一致，不能使用 equals 方法，会直接报错。</span>
<span>equals 在没有重写之前和 == 是相同的，在方法重写之后需要根据equals的具体方法来考虑，对于 == 而言的话，如果是基本数据类型，则比较的是值，如果是引用类型，则比较的是引用地址。</span>


### 集合

<span>Java中常用的集合有四种：</span>

1. List：列表，元素有序、可重复
2. Set：集合，元素无序、不可重复
3. Map：映射，元素是键值对，键不可重复
4. Queue：队列，元素有序、先进先出



