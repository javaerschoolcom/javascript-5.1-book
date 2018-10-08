### RegExp

##### 什么是正则

* 匹配的一种模式，从海量的字符串中找到你所想要的字符串片段。它相当于一种模板。

##### 正则定义方式

* 通过new创建正则；

```javascript
var  str="abacafejfejfehfjie";
var  reg =   new RegExp("e",'g');
var  reslut = reg.test(str); //true
```

* 直接创建正则

```javascript
var reg =/e/     //创建正则的简写
var reg =/e/g    //g全局搜索
var reg=/e/i     //i不区分大小写
var reg=/e/gi    //既要全局匹配又不忽略大小写
```

##### 正则常用方法

* test方法匹配到返回true,没匹配到返回false

```javascript
var  str="abc";
var  reg=/a/g;
reg.test(str); //true
```

* exec方法匹配到返回的结果组成数组（包括全局匹配），没匹配到返回null

```javascript
var  str="abcabcabc";
var  reg=/ab/g;
reg.exec(str); //["ab", index: 0, input: "abcabcabc", groups: undefined]

reg=/(.)b/g;   //带有括号的匹配会返回多个，每个括号会返回一个结果
reg.exec(str); //["ab", "a", index: 0, input: "abcabcabc", groups: undefined]
```

##### 字符串中可以使用正则的方法

* match方法全局匹配，会返回找到所有匹配结果组成的数组，没找到返回null

```javascript
var  str="abcabcabc";
var  reg=/ab/g;
str.match(reg); // ["ab", "ab", "ab"]

reg=/ef/g;
str.match(reg); //null
```

* search方法全局匹配，会返回第一个匹配结果开始的索引，没找到返回-1

```javascript
var  str="abcabcabc";
var  reg=/ab/g;
str.search(reg); // 0

reg=/ef/g;
str.search(reg); //0
```

* replace方法全局匹配，会替换掉所有匹配到的结果

```javascript
var  str="abcabcabc";
var  reg=/a/g;
str.replace("a","A"); // Abcabcabc
str.replace(reg,"A"); // AbcAbcAbc

```

* split方法

```javascript
var  str="abcabcabc";
var  reg=/a/g;
str.split(reg); // ["", "bc", "bc", "bc"]
```

正则常用属性

* lastIndex:当前开始匹配位置的索引，在全局匹配的时候，正则方法调用可读写

```javascript
//全局匹配，读lastIndex
var str="abcabc";
var reg=/a/g;
console.log(reg.lastIndex); //0 从0号位置开始匹配
console.log(reg.exec(str)); //["a", index: 0, input: "abcabc", groups: undefined]
console.log(reg.lastIndex); //1
console.log(reg.exec(str)); //["a", index: 3, input: "abcabc", groups: undefined]
console.log(reg.lastIndex); //4
console.log(reg.exec(str)); //null
console.log(reg.lastIndex); //0 匹配完成后，又返回开始位置进行匹配
console.log(reg.exec(str)); //["a", index: 0, input: "abcabc", groups: undefined]
```

```javascript
//全局匹配，写lastIndex
var str="abcabc";
var reg=/a/g;
reg.lastIndex=3; //设置从索引为3的位置开始检索
console.log(reg.exec(str)); //["a", index: 3, input: "abcabc", groups: undefined]
```

```javascript
//非正则方法，修改lastIndex无效
var str="abcabc";
var reg=/a/g;
reg.lastIndex=3; //设置从索引为3的位置开始检索
console.log(str.match(reg)); //["a", "a"]  还是匹配到了索引为0处的字符
```

匹配模式

字面量字符

* /a/匹配a 在正则表达式中，就是字面的含义

元字符

* 字符有特殊含义，不代表字面的意思


* 符号(.):匹配空格以外的任何``一个``字符

```javascript
var str="cat,c2t,c*t,clerot";
var reg=/c.t/g;
str.match(reg); // ["cat", "c2t", "c*t"]
```

* 位置字符:^匹配开始位置,$匹配结束位置

```javascript
/^lero/.test('lero123') // true lero必须出现在开始位置
/lero$/.test('123lero') // true lero必须出现在结束位置
/^lero$/.test('lero123lero') // true lero必须出现在开始和结束位置
```

* 选择符(|):该符号左边或者右边满足，都会匹配到

```javascript
"catanddog".match(/cat|dog/g); //[cat,dog]
```

* 转义符：元字符要当成普通字符的时候需要加反斜杠

```javascript
"a|b|c".match(/\|/g); // ["|", "|"]
```

* 特殊字符：\n \t \r等
* 字符类
  * []表示方括号内只需要匹配一个就行
  * [^]除了方括号内的所有字符，其他字符都可以匹配
  * [-]连续的字符可以通过该字符简写

```javascript
/[abc]/.test('apple') // true
/[^abc]/.test('dbc') // false
/[a-z]/.test('c') // true
```

* 预定义模式:常用的一些匹配已经简写成固定写法

```javascript
\d 匹配0-9之间的任一数字，相当于[0-9]。
\D 匹配所有0-9以外的字符，相当于[^0-9]。
\w 匹配任意的字母、数字和下划线，相当于[A-Za-z0-9_]。
\W 除所有字母、数字和下划线以外的字符，相当于[^A-Za-z0-9_]。
\s 匹配空格（包括换行符、制表符、空格符等），相等于[ \t\r\n\v\f]。
\S 匹配非空格的字符，相当于[^ \t\r\n\v\f]。
\b 匹配词的边界。
\B 匹配非词边界，即在词的内部。
```

* 重复类
  * {n}恰好重复n次
  * {n,}至少重复n次,
  * {n,m}表示重复不少于n次，不多于m次

```javascript
/le{2}ro/.test('leero') // true
/le{2}r{1}o/.test('leero') // true
/le{1,}r{1}o/.test('leero') // true
/le{1,}r{1,3}o/.test('leero') // false
```

* 量词符
  * ? 问号表示某个模式出现0次或1次，等同于{0,1}
  * *星号表示某个模式出现0次或多次，等同于{0,}
  * +加号表示某个模式出现1次或多次，等同于{1,}

```javascript
/le*ro/.test('leero') // true
```

* 修饰符:i忽略大小写，g全局匹配
* 组匹配:小括号中的内容看成一个整体

```javascript
/lero+/.test('leroooooooo') // true
/(lero)+/.test('lerolero') // true

var m = 'abcabc'.match(/(.)b(.)/);  // ['abc', 'a', 'c']
var m1 = 'ab'.match(/(.)b(.)/);  // null
```

