### 数据类型概述

##### 定义

* JavaScript 中每一个值，都用某一种与之对应的类型进行描述，称之为数据类型。ES5中数据类型共有六种

##### 六种数据类型

* 原始类型：是最基本的数据类型，不能再细分了
  * ``string``字符串：用单引号或者是双引号包裹的内容
  * ``number``数值:整数|小数
  * ``boolean``布尔:true(真)|false(假)
* 复合类型：往往是多个原始类型的值的合成，可以看作是一个存放各种值的容器
  * ``object``对象:包含狭义的对象``object``+数组``array``+函数``function``
* 特殊值：设计者对特殊情况采用的设计
  * ``undefined``:变量定义没有初始化，表示未知
  * ``null``:表示没有，表示空的空间

##### 三种方法鉴别数据类型

* `typeof`运算符,对原始类型和特殊值鉴别没什问题，但对于对象的鉴别不够细粒度

```javascript
typeof 111  // "number"
typeof 'abc' // "string"
typeof true // "boolean"
function f() {}
typeof f   // "function"
typeof undefined  // "undefined"
typeof {} // "object"
typeof [] // "object"
typeof null // "object"
```

* `instanceof`运算符,是对typeof的补充，能够进一步细粒度鉴别对象

```javascript
var obj = {};
var arr = [];

obj instanceof Array // false
arr instanceof Array // true
```

* `Object.prototype.toString`函数

