### 基础语法

#####  语句

* 以分号(半角英文)结束，称为一条语句，多条语句可以放在一行。
* 语句是程序最小的执行单元

```javascript
var a =1;
;;;  //空语句
'lero';//没有意义的语句
```

##### 变量

* 概念：变量是对值的引用，变量其实是人为开辟内存中一块存储区域用来存储值，然后给这个区域取名字
* 变量声明：1）var 变量名 = 表达式；2）var 变量名；3）var 变量名1,变量名2，...变量名N；

```javascript
var name="lero";
var age;
var me,you,he;
var me="I",you="You",he="He";
```

* 变量必须先声明再使用；

```javascript
var name='lero';
console.log(name); //lero
```

* 变量声明自动提升（对没有使用var声明的变量无效）

```javascript
console.log(name);  //undefind
var name='lero';
//上面两句等效于下面三句
var name；
console.log(name);  //undefind
name='lero';
```

* 变量可以重复使用

```javascript
var name='lero';
name='lily';
name=true;
```

##### 标识符

* 取名字(变量|函数|在程序中只要不是关键字保留字,都叫标识符)
* 标识符命名规则：
  * 1）第一个字符可以是英文字母大小写或者是_,$开始
  * 2)从第二个字符开始还可以是0-9罗马数字
  * eg: 错误写法：*a; @b；1；
  * 3）标识符大小写敏感
  * 4）自己取标识符的时候切记不要使用关键字|保留字|其他API名字

##### 关键字&保留字

* 在JS中有特殊的用途或者是特殊的含义的单词称之为关键字
* 在JS中虽然暂时没有特殊的用途，不排除未来可能会使用的单词
* eg：var ,true,false(undefined)

##### 注释

* 浏览器不会解释执行，供开发人员使用，作用是标志，备注。
* 单行注释：// todo
* 多行注释：/* todo */ (不能嵌套)
* 支持html注释: <!--todo -->

##### 区块

* 用括号包裹的区域，称为区块，把一个功能的语句包裹起来

##### 数据类型

ECMAScript5.1中有6种数据类型

* (string)字符串：用单引号或者是双引号包裹的内容
* (number)数值:整数|小数
* (boolean)布尔:true(真)|false(假)
* undefined:变量定义没有初始化，表示未知
* null:表示没有，表示空的空间
* (object)对象:狭义的对象(object)+数组+函数

如何去鉴别数据的类型？

* typeof
  * 可以鉴别简单数据类型(string,number,boolean,undefined)
  * 对于对象来说，鉴别不是很细致
* instanceof
* Object.prototype.toString

