### 运算符之逻辑运算符

##### 逻辑运算符有4种，运算的结果不一定是布尔值，运算的结果一定是一个表达式

```javascript
!  //取反运算 not
&& //与运算符 and
|| //或运算符 or
?: //三元运算符
```

##### 运算符``!``

* 它的运算结果一定是布尔值，是对算子采用``Boolean()``函数进行隐式转换,只有6个值求反是true,其余全是false

```javascript
!"" //true
!0 //true
!undefined //true
!null //true
!false //true
!NaN  //true
```

* 快速对一个值转布尔值的方式，是对原值连续两次求反

```javascript
!!4 //true --->Boolean(4)
```

##### 运算符``&&``

* 结果是表达式的值，不一定是布尔值
* 首先会依次对算子求布尔值，如果最后一个&&前的算子的布尔值都是是true,直接返回最后一个算子的表达式的值,而不是布尔值
* 首先会依次对算子求布尔值，如果遇到算子是false的,直接该算子的表达式的值，而不是布尔值

```javascript
3&&4 //4
0&&4 //0
1&&(10-3)&&8 //8
1&&false&&true //false
```

* 高级运用

```javascript
 function sum(x,y){
      return x+y;
  }
//正常版
var i=1;
if(i){
      sum(1,2);
}
//高级版
i && sum(1,2);
```

##### 运算符``||``

* 结果是表达式的值，不一定是布尔值
* 首先会依次对算子求布尔值，如果遇到算子的布尔值是true就停止继续往下执行，直接返回该算子表达式的值
* 首先会依次对算子求布尔值，如果最后一个||之前的算子的布尔值都是false,直接返回最后一个算子的表达式的值，不是布尔值

```javascript
var x=1;
console.log(3||(++x)); //3
console.log(x); //1
```

* 常见运用

```javascript
//给变量赋初始，防止没有传递初始值
function sum(x,y){
      x = x ||1;
      y = y ||2;
      return x+y;
  }
```

##### 运算符``?:``

* 三元运算符语法： 表达式1?表达式2:表达式3
* 首先对表达式1进行Boolean()函数隐式转换，如果转换的结果是true,就会返回表达式2的值，否则返回表达式3的值

```javascript
var result1=(3+4)?1:2; //result1 =1
var result2=(3>4)?1:2  //result2 =2

 var x =1;
 var result= (--x)?x--:(x++&&++x);
 console.log(result);//0
```

