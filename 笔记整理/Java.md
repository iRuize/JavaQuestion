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

</style>
# Java学习笔记
## 目录划分
开始之前应该先梳理一下思路，目前
## Java基础
### 什么是Java？
### 你好

