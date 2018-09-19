### 流程控制

##### 表达式

* 由基本数据类型的值，变量，运算符，小括号经常排列组合，并且能够求得唯一的值

```javascript
var a=1,b=2;
a+b;
f();
```

##### 顺序结构

* 代码从上到下一行一行的执行

```javascript
congsole.log(1);
congsole.log(2);
congsole.log(3);
// 1,2,3 永远不会出现以下结果 3,2,1| 1,3,2

function sout(){ //声明不会被执行
    congsole.log(4);
	congsole.log(5);
    sout1();
	congsole.log(6);
}
function sout1(){ //声明不会被执行
    congsole.log(7);
	congsole.log(8);
	congsole.log(9);
}
sout();
congsole.log(0);
```

分支结构

* 需求:给一个数，如果该数大于5，就把这个数加1输出，否则直接输出该值
* if关键字可以实现分支结构

```javascript
//语法
if(boolean表达式)  //此处会使用Boolean()函数进行隐式转换，为true的时候，会执行{}内的全部代码
{
    //语句集合
}
//继续按照顺序结构执行
```

```javascript
 var input = prompt("请输入一个数值");
    input =parseInt(input);
    if(input>5){
       input++;
    }
    console.log("值是："+input);
```

* 需求:给一个整数，判断该数是否是奇数

```javascript
//当条件是对立面的时候，就可以使用if..else
if（boolena表达式）{
    //boolean表达式值为true的时候，会执行该大括号中的代码
}else{
    //boolean表达式值为false的时候，会执行该大括号中的代码
}
```

```javascript
    var input = prompt("请输入一个数值");
    input =parseInt(input);

    if(input%2==0){
       alert("这是一个偶数");
    }else{
       alert("这是一个奇数");
    }
```

* 需求：输入0-100以内的数，小于60输出不及格，60~80输出良好，80~99输出优秀，100输出完美

```javascript
//当条件有2个以上的时候，就可以使用if..elseif..elseif..elseif..[else]
if（boolena表达式1）{
    //boolean表达式1值为true的时候，会执行该大括号中的代码
}else if(boolena表达式2){
    //boolean表达式值2为true的时候，会执行该大括号中的代码
}else if(boolena表达式N){
     //boolean表达式值N为true的时候，会执行该大括号中的代码
}else{
    //前面的分支都不满足，就会进入该分支
}

```

```javascript
var input = prompt("请输入一个数值");
    input =parseInt(input);
    if(input<60){
       alert("不及格");
    }else if(input>=60 && input<80){
       alert("良好");
    }else if(input>=80 && input<=99){
        alert("优秀");
    }else{
        alert("完美")
    }
```

* 练习作业
  * 从键盘分别输入3个整数，求出最大值并输出在控制台
  * 从键盘分别输入3个整数分别依次代表小时(0-23)分钟(0-59)秒(0-59),然后由程序输出下一秒时间15:09:09
  * 写个彩票游戏：分别随机生成2个一位数，提示用户猜测如果完全匹配奖励1000，只匹配数字没顺序奖励300，只匹配1个数字奖50，没匹配则没中奖

```javascript
// 从键盘分别输入3个整数分别依次代表小时(0-23)分钟(0-59)秒(0-59),然后由程序输出下一秒时间
    var hour = prompt("请输入小时：范围为[0-23]");
    hour =parseInt(hour);
    var minute = prompt("请输入分钟：范围为[0-59]");
    minute =parseInt(minute);
    var second = prompt("请输入秒数：范围为[0-59]");
    second =parseInt(second);

    function caleTime(time){
        time++;
        if(time<10){
            time="0"+time;
        }
        return time;
    }
    if(second<59){
        second =caleTime(second);
    }else{
        second ='00';
        if(minute<59){
            minute= caleTime(minute);
        }else{
            minute='00';
            if(hour<23){
              hour= caleTime(hour);
            }else{
                hour='00';
            }
        }
    }
    alert("输入时间的下一秒是【"+hour+":"+minute+":"+second+"】");
```

