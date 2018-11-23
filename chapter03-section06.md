### Date

创建当前时间

```javascript
var now = new Date(); //本地时间  默认是调用toString()
var time =  now.valueOf(); //返回的是1970年起点时间到当前之差的毫秒数 1538012821057
```

创建非当前时间

* 年份4位数如2018| 年份为2位数的时候要加上1900年
* 月份0-11，月份是从0开始计算
* 每月中天数1-31，从1开始计算
* 小时0-23
* 分钟0-59
* 秒0-59
* 毫秒0-999
* 如果传入的参数不在正常范围之内，会自动转换到正确的时间

```javascript
var now =new Date(2018,8,27,10,10,10,998); //一般使用
var now =new Date(2018,8); //至少要传入年份和月份   Sat Sep 01 2018 00:00:00 GMT+0800
var now =new Date(2018);  //只传入一个参数，会当成毫秒计算  Thu Jan 01 1970 08:00:02 GMT+0800
var now =new Date("2018-09-27"); //
var now =new Date("2018/09/27"); //
var now =new Date("2018:09:27"); //
```

日期中常用方法

* toXXX

```javascript
var now = new Date();
now.toLocaleString() //2018/9/27 上午10:55:26
now.toLocaleDateString()//2018/9/27
now.toLocaleTimeString()//上午10:55:26
```

* getXXX

```javascript
var now = new Date();
var time =now.getTime();// 返回当前时间毫秒数
var year = now.getFullYear() //返回4位数年份
var month = now.getMonth()+1; //返回月份
var date = now.getDate();    //返回每月多少号
var week = now.getDay();     //返回星期几  没有set方法，通过计算出来的
var hours = now.getHours();  //返回小时数
var minutes =now.getMinutes();//返回分钟数
var seconds =  now.getSeconds();//返回秒数
var milliseconds = now.getMilliseconds();//返回毫秒数
```

* 计算今年还剩下多少天
* setXXX

```javascript
var now = new Date();
var year = now.setFullYear(2018) //设置4位数年份
var month = now.setMonth(8); //设置月份
var date = now.setDate(1);    //设置每月多少号
var hours = now.setHours(11);  //设置小时数
var minutes =now.setMinutes(22);//设置分钟数
var seconds =  now.setSeconds(11);//设置秒数
var milliseconds = now.setMilliseconds(888);//设置毫秒数
```

* 设置时间为明天的这个这个时候

```javascript
var now = new Date();
now.setHours(now.getHours()+24);
console.log(now);
```

* 上述的所有函数都有对应的UTC时间

Date中的静态方法

```javascript
var now = new Date();
now.valueOf();
now.getTime();
Date.now();   //等价于now.valueOf()
Date.parse("2018,8")//用于把字符串解析成日期
```

