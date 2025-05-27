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
span {
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
<span>Java的基本数据类型有四种：整数类型、浮点类型、字符类型、布尔类型。</span>

1. 整数类型：byte（1字节）、short（2字节）、int（4字节）、long（8字节）
2. 浮点类型：float (4字节)、double (8字节)
3. 字符类型：char (2字节)
4. 布尔类型：boolean (1字节)


### 函数修饰符

<span>Java中函数的修饰符有四种：</span>

1. public：公有修饰符，可以被所有类访问
2. private：私有修饰符，只能被同一个类访问
3. protected：受保护修饰符，可以被同一个包内的类访问或者是其他包下的子类访问
4. static：静态修饰符，可以被静态方法、静态变量访问

### 集合

<span>Java中常用的集合有四种：</span>

1. List：列表，元素有序、可重复
2. Set：集合，元素无序、不可重复
3. Map：映射，元素是键值对，键不可重复
4. Queue：队列，元素有序、先进先出



