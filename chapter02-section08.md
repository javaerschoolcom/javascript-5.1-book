### 字符串

##### 字符串定义

* 由双引号或者单引号包裹起来内容，推荐使用单引号

```javascript
//基本用法
'hello'
//单引号字符串的内部，可以使用双引号。双引号字符串的内部，可以使用单引号
"hello 'word'"
//单引号字符串的内部，使用单引号，就必须在内部的单引号前面加上反斜杠，用来转义。双引号字符串内部使用双引号，也是如此
'you  say \'hello\'?'
```

##### 特殊字符转义

* 必须使用反斜杠进行转义
* 常用转义

```javascript
\n ：换行符
\r ：回车键
\t ：制表符
\' ：单引号
\" ：双引号
\\ ：反斜杠
```

##### 字符串特性

* 属性length计算字符串长度

```javascript
"aaaaaa".length //6
```

* 取出字符串任意位置的字符

```javascript
"abcde"[0] //a
```



