### Math

提供数学计算相关值

```javascript
Math.E：常数e。
Math.LN2：2的自然对数。
Math.LN10：10的自然对数。
Math.LOG2E：以2为底的e的对数。
Math.LOG10E：以10为底的e的对数。
Math.PI：常数Pi。
Math.SQRT1_2：0.5的平方根。
Math.SQRT2：2的平方根
```

静态函数

* 直接通过Math本身去调用的函数

Math.random()

* 随机生成一个0~1之间的随机数，但是1取不到

```javascript
Math.random() //0~1
Math.random()*10 //0~10
//生成任意区间内的随机数
```

Math.max()

* 求最大值

```javascript
Math.max() //-Infinity
Math.max(10,20,32,11,222)//222
```

Math.min()

* 求最小值

```javascript
Math.min() //Infinity
Math.min(10,20,32,11,222)//10
```

Math.abs()

* 求绝对值

```javascript
Math.abs(-1) //1
```

Math.round()

* 四舍五入

```javascript
Math.round(-3.5); //-3
Math.round(-3.6); //-4
Math.round(-3.4); //-3
```

Math.floor()

* 舍去小数部分

```javascript
Math.floor(3.99) //3
Math.floor(3.1) //3
Math.floor(-3.99) //-4
```

Math.ceil()

* 收起小数部分

```javascript
Math.ceil(3.14) //4
Math.ceil(-3.14) //-3
```

Math.pow()

* 求平方

```javascript
Math.pow(2,3) //8 求2的3次方
```

Math.sqrt

* 开平方

```javascript
Math.sqrt(4) //2
Math.sqrt(-4)//NaN
```

数学上常用的函数

* 它们的参数都是``弧度值``（360°==2π）,方向为逆时针

```javascript
Math.sin()：返回参数的正弦   （弧度值）
Math.cos()：返回参数的余弦   （弧度值）
Math.tan()：返回参数的正切   （弧度值）
Math.asin()：返回参数的反正弦（弧度值）
Math.acos()：返回参数的反余弦（弧度值）
Math.atan()：返回参数的反正切（弧度值）
```

```javascript
Math.sin(Math.PI/4) // 等于sin45°
```

* 弧度转度

```javascript
function radian_to_degree(radian) {
    return (radian / Math.PI) * 180;
}
```

* 度转弧度

```javascript
function degree_to_radian(degree) {
    return (degree / 180) * Math.PI;
}
```

练习作业

* 任意给两个点(x1,y1),(x2,y2),求这两个点之间的距离
* 假设秒针的初始值（起点）为12点钟方向，圆心的坐标为(0,0)，秒针长度为1，求1秒后，秒针针尖的坐标？

