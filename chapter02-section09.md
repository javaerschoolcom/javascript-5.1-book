### 数据类型转换

##### 强制转换

* 把其他数据类型转换为``String``
* 把其他数据类型转换为``Number``
* 把其他数据类型转换为``Boolean``

##### String()函数

* 原始类型转为字符串规则:把原始类型用双引号包裹起来

```javascript
String("lero"); // "lero"
String(""); //""
String(0); // "0"
String(NaN); //"NaN"
String(infinity) //infinity
String(3.14E2); //"314"
String(3.14E30);//"3.14+E30"
String(true); //"true"
String(false); //"false"
String(null);  //"null"
String(undefined); //"undefined"
```

* 对象转为字符串分三步
  * 第一步先使用对象的``toString``函数进行转换，如果能够被转为原始的数据类型，对转换后的数据类型再使用String()进行转换
  * 如果``toString``转换结果是对象，再接着使用``valueOf``函数进行转换，如果能够被转为原始的数据类型，就使用String()进行转换
  * 如果``valueOf``函数转换的结果是对象，就报错
* 一般的对象默认转换都是``"[Object object]"``

```javascript
String({}) //"[Object object]"
String({"name":'lero'}) //"[Object object]"
```

* 数组由于覆写了``toString``函数，转换规则比较特殊

```javascript
String([]) // ""
String([1]) // "1"
String([1,2])//"1,2"
```

* 覆盖对象``toString``函数或者``valueOf``函数，用于自定义转换结果

```javascript
//只覆盖toString函数
 var o={
         "toString":function(){
             //测试是否调用该函数
             console.log("into this palce");
             return 1;
         }
     };
console.log(String(o));// "1"

//只覆盖valeOf函数
var o={
         "valueOf":function(){
             //测试是否调用该函数
             console.log("into this palce");
             return 1;
         }
     };
console.log(String(o));// "[Object object]"
//覆盖toString函数并返回对象，且覆盖valueOf函数返回原始类型
var o={
         "toString":function(){
             return {};
         },
         "valueOf":function () {
             return true;
         }
     };
 console.log(String(o));// "true"
//覆盖toString函数并返回对象，且覆盖valueOf函数返回对象
 var o={
         "toString":function(){
             return {};
         },
         "valueOf":function () {
             return {};
         }
     };
 console.log(String(o));//Uncaught TypeError: Cannot convert object to primitive value

```

**注意事项**：``覆写toString和valueOf函数的时候，key一定要加双引号，value一定是一个函数``

##### Number()函数

* 原始类型规则:能转换成功就是数值，转换不成功就是NaN或者报错

```javascript
Number(""); //0
Number("1");//12
Number("3.14e2");//314
Number("3.14e30");//3.14e+30
Number("3.14abc"); //NaN,比parseInt严格
Number("\n\r123 "); //123
Number("NaN"); //NaN
Number("infinity") //infinity
Number("0"); //0
Number("true"); //1
Number("false"); //0
Number(null); //0
Number(undefined); //NaN,undefined与null在转换成数值的差异性
```

* 对象转换规则分三步：
  * 第一步先使用对象的``valueOf``函数进行转换，如果能够被转为原始的数据类型，再使用``Number()``进行转换
  * 如果``valueOf``转换结果是对象，再接着使用``toString``函数进行转换，如果能够被转为原始的数据类型，就使用``Number()``进行转换
  * 如果``toString``函数转换的结果是对象，就报错
* 一般的对象默认转换结果都是``NaN``

```javascript
Number({}) //NaN
Number({"name":"lero"}) //NaN
```

* 数组由于覆写了``toString``函数，转换规则比较特殊

```javascript
Number([]) // 0
Number([1]) // 1
Number([1,2])// NaN
```

* 覆盖对象``toString``函数或者``valueOf``函数，用于自定义转换结果

```javascript
//只覆盖toString函数
 var o={
         "toString":function(){
             //测试是否调用该函数
             console.log("into this palce");
             return 1;
         }
     };
console.log(Number(o));// "1"

//只覆盖valeOf函数
var o={
         "valueOf":function(){
             //测试是否调用该函数
             console.log("into this palce");
             return false;
         }
     };
console.log(Number(o));// 0
//覆盖toString函数并返回对象，且覆盖valueOf函数返回原始类型
var o={
         "toString":function(){
             return {};
         },
         "valueOf":function () {
             return true;
         }
     };
 console.log(Number(o));// 1
//覆盖toString函数并返回对象，且覆盖valueOf函数返回对象
 var o={
         "toString":function(){
             return {};
         },
         "valueOf":function () {
             return {};
         }
     };
 console.log(Number(o));//Uncaught TypeError: Cannot convert object to primitive value
```



##### Boolean()函数

* 只有6种会转换成false,其余都转换为true

```javascript
Boolean("") //false
Boolean(NaN)//false
Boolean(0)//false
Boolean(false)//false
Boolean(undefined)//false
Boolean(null)//false
```

* 特殊的转为true

```javascript
Boolean(infinity)//true
Boolean(new Boolean(false))//true
Boolean([]])//true
Boolean([0])//true
Boolean({})//true
```

##### 隐式转换

* 不用显示的调用``String()``|``Number()``|``Boolean()``而是JS自己在需要对应的数据类型的时候，会自动调用上面三个函数进行转换
* 在进行运算的时候，不仅仅是算术运算符，还可能是其他运算符
* 在进行流程控制时候，需要把其他类型转换为布尔值,会隐式的调用``Boolean()``进行转换，典型代表``if（boolean表达式）``
* 在进行一元运算的时候，需要把其他类型转换为数值,会隐式的调用``Number()``进行转换,比如一元``+``,一元``-``