### 关系运算符

关系运算符8种,运算的结果一定是布尔值

```javascript
>
>=
<
<=
==
!=
=== //恒等于
!== //不恒等于
```

运算符``<>``

* 运算符左右两边算子都是字符串的时候，会从左到右每一个字符进行比较，一旦比较有结果，就停止。比较的是它们的Unicode码值大小(字典顺序)

``` javascript
"a">"b" // false a=97,b=98
"A">"a" // false A=65,a=97
"aa">"ab" //false
"aa">"a" // true
```

* 运算符左右两个算子都是原始类型但是不全是字符串类型，比较的时候会进行隐士转换成数值

```javascript
"4">3 //true "4"字符串转为数值4
undefined>3 //false undefined转换成数值是NaN, NaN和任何类型比较都是false
null<3 //true  null转为数值是0  0<3->true
true>1 //    false  true会转换成1
false<1 //  true    false会转为0
```

* 运算符左右两边有算子是对象，比较的时候会把对象转为原始的类型调用Number进行隐士转换

```javascript
 var o ={"toString":function(){
                    console.log("toString");
                        return 1
                       },
           "valueOf":function(){
                     console.log("valueOf");
                     return 4
                     }
    }

   console.log(3>o); //false     3>4
```

运算符``===,!==``

* 首先判断比较两个因子数据类型是否一致，不一致就直接是false;如果类型一致，还要比其他的
  * 类型一致，如果算子都是原始类型，比的是数值
  * 类型一致，如果算子都是对象，比的是对象的地址
  * 特殊的NaN和任何类型的值比较都是false，包括它自己

```javascript
1==="1" //false  类型不一致
1===0x1 //true   类型一致，数值也相等
{}==={} //false  类型一致，但是地址不一致
var a={}; var b =a;
a===b //true     类型一致，地址也一致
NaN===NaN //false
var c,d;
c===d //true   c,d因为没赋初值，都是undefined
```

运算符``==,!=``

* 比较的时候不考虑数据类型，只有字符串，数值，布尔，对象进行比较的时候会隐士转换成数值(Number)进行比较
* 特殊值undefined,null和任何值比较都是false,而undefined和null比较的时候是true

```javascript
1 =="1" //true
false==0 //true
null == 0 //false

var a,b;
a==b //


 var o ={"toString":function(){
              console.log("toString");
                 return false;
              },
           "valueOf":function(){
                     console.log("valueOf");
                     return true;
          }
    }

   console.log(1==o); //true 对象首先调用valueOf进行转为数值
```

