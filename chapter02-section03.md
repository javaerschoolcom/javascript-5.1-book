### 数据类型之数值

##### 数值精度

* js中小数是不精确的（0.3-0.1）
* js中所有数值本质上都是小数

##### 数值范围

* 整数范围(Number.MAX_SAFE_INTEGER|Number.MIN_SAFE_INTEGER|2^53-1)
* 小数范围(Number.MAX_VALUE|Number.MIN_VALUE)


* 特殊数值
  * 表示超过了小数能够表示的最大范围(Math.pow(2,1024))就会显示Infinity
  * 表示的数超过了最小范围（Math.pow(2,-1075)）就会显示0

##### 特殊值0

* 在js中除数可以为0
* 1/0==infinity
* 1/-0==-infinity
* -0===0
* 0/0==NaN

##### 特殊NaN

* 10-"A"==NaN
* NaN永远不会等于自己，也不会大于自己，也不会小于自己
* NaN和任何数做数学运算，结果都为NaN
* isNaN()函数，``会把传入的数据首先转换为数值，再判断``如果结果是NaN,返回true|如果结果不是NaN返回false(特殊的空数组或者是数组只有一个元素而且元素的数字结果为fasle,其余不能转为数字的结果都是true,infinity返回false,undefined返回ture,null返回false)

##### 特殊值Infinity

* Infinity和常数（除了0）做四则运算的时候符合数学上的无穷运算
* 0*infinity==NaN
* isFinite()函数判断数值是不是有限数,**会把传入的数据首先转换为数值，再判断**，如果是则返回true,如果不是则返回false；除了Infinity|-infinity|NaN其余数值都返回true

##### 数值表示方法

* 字面量表示(不管是任何进制，结果都是以10进制展示)
  * 10进制表示：3.14
  * 16进制表示：0X11->17 |0x11->17
  * 8进制表示：0o11->9 |0O11->9|011->|091->910
  * 2进制表示：0B11->3 |0b11->3
* 科学计数法
  * 3.14e+2->314|3.14E2->314
  * 3.14e-2->0.0314|3.14E-2->0.0314
  * 小数点前面的位数超过21位会自动转换成科学计数法表示
  * 小数点后面的位数超过6位就会自动转换成科学计数法

##### parseInt()

* 基本用法

```javascript
parseInt('123') // 123
```

* 如果字符串头部有空格，空格会被自动去除

```javascript
parseInt('  81') // 81
```

* 如果parseInt的参数不是字符串，则会先转为字符串再转换

```javascript
parseInt(1.23) // 1
```

* 字符串转为整数的时候，是一个个字符依次转换，如果遇到不能转为数字的字符，就不再进行下去，返回已经转好的部分

```javascript
parseInt('8a') // 8
parseInt('15e2') // 15
parseInt('15px') // 15
```

* 如果字符串的第一个字符不能转化为数字（后面跟着数字的正负号除外），返回NaN

```javascript
parseInt('abc') // NaN
parseInt('.3') // NaN
parseInt('') // NaN
parseInt('+') // NaN
parseInt('+1') // 1
```

* 如果字符串以0x或0X开头，parseInt会将其按照十六进制数解析|ob开始按照2进制解析

```javascript
parseInt('0x10') // 16
```

* 如果字符串以0开头，将其按照10进制解析

```javascript
parseInt('011') // 11
```

* 科学计数法转换可能不符合预期


* parseInt()第二个参数(2-36之间)用于进制转换

```javascript
parseInt('1000', 2) // 8
parseInt('1000', 6) // 216
parseInt('1000', 8) // 512
```

* 如果第二个参数不是数值，会被自动转为一个整数。这个整数只有在2到36之间，才能得到有意义的结果，超出这个范围，则返回NaN

```javascript
parseInt('10', 37) // NaN
parseInt('10', 1) // NaN
```

* 如果第二个参数是0、undefined和null，则直接忽略

```javascript
parseInt('10', 0) // 10
parseInt('10', null) // 10
parseInt('10', undefined) // 10
```

##### parseFloat()

* 基本用法

```javascript
parseFloat('3.14') // 3.14
```

* 如果字符串符合科学计数法，则会进行相应的转换

```javascript
parseFloat('314e-2') // 3.14
parseFloat('0.0314E+2') // 3.14
```

* 如果字符串包含不能转为浮点数的字符，则不再进行往后转换，返回已经转好的部分

```javascript
parseFloat('3.14more non-digit characters') // 3.14
```

* parseFloat方法会自动过滤字符串前导的空格

```javascript
parseFloat('\t\r12.34\n ') // 12.34
```

* 如果参数不是字符串，或者字符串的第一个字符不能转化为浮点数，则返回NaN

```javascript
parseFloat([]) // NaN
parseFloat('FF2') // NaN
parseFloat('') // NaN
```

