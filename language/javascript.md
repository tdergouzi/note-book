# JavaScript



## 什么是 JavaScript 语言？



### JavaScript 定义

JavaScript 是轻量脚本语言（script language）

JavaScript 也是一种嵌入式（embeded）语言

宿主环境（host）主要为浏览器和 Node

JavaScript 语言版本，比如 ECMAScritp 5.1 和 ES6

JavaScript 程序可采用事件驱动（event-driven）和非阻塞式设计（non-blocking），用于服务器端高并发环境



### JavaScritp 的出现

1995年，Netscape 公司雇用了程序员 Brendan Eich 开发网页脚本语言。



### JavaScript & Java

Java 与 JavaScript 关系，后者的基本语法和对象体系，模仿前者设计。两者之间具有相似性，所以在命名方面，经过 Java 公司 Sun 的同意，由最开始的 LiveScript 改名为 JavaScript。



### JavaScript & ECMAScript

ECMAScript 与 JavaScript 的关系，前后是后者的规格，后者是前者的实现。



### JavaScript 版号

2011年6月，ECMAScript 5.1 版发布，并且成为国际标准（ISO/IEC 16262:2011）

2015年6月，ECMAScript 6 正式发布，并且更名为 ECMAScript 2015。因为 TC93 委员会计划每年发布一个新的版本，后续版本名称以此类推。



### JavaScript 基本语法

#### 变量

变量名区分大小写，`A`和`a`是两个不同的变量。



#### 变量提升

JavaScript 引擎的工作方式是，先解析代码，获取所有被声明的变量，然后再一行一行运行。实际运行代码过程中，所有的变量的声明语句，都会被提升到代码的头部，称为变量提升（hoisting）。

```javascript
console.log(a);
var a = 1;

// 实际运行代码

var a;
console.log(a);
a = 1；

// 输出结果
undefined
```



