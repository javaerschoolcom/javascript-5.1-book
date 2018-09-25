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

##### 分支结构

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
* 输入一个整数，判断是正数还是负数

```javascript
 var numer= prompt("请输入一个数值：");

    numer =parseInt(numer);

    if(numer>0){
      alert(numer+"是正数");
    }else if(numer<0){
      alert(numer+"是负数");
    }else{
      alert(numer+"是特殊的自然数")
    }
```

* 输入两个整数，打印两数之差的绝对值

```java
//方法一
var first= prompt("请输入第一个整数：");
    var second= prompt("请输入第二个整数：");
    first =parseInt(first);
    second =parseInt(second);
    var abs =0;

    if(first>second){
        abs =first-second;
    }else{
        abs=second-first;
    }
    alert(first+"和"+second+"差值的绝对值是"+abs);
```

```javascript
//方法二
 var first= prompt("请输入第一个整数：");
    var second= prompt("请输入第二个整数：");
    first =parseInt(first);
    second =parseInt(second);
    var abs = first>second? (first-second):(second-first);
    alert(first+"和"+second+"差值的绝对值是"+abs);
```

* 输入一个4位数的年份，判断这个年份是否为闰年

```javascript
var year= prompt("请输入一个四位数年份：");
    year = parseInt(year);
    if((year%4==0&&year%100!=0)||year%400==0){
        alert(year+"年是润年");
    }else{
        alert(year+"年是平年");
    }
```

* 分别输入身高和体重，根据公式（身高-108）*2=体重，超过10斤输出体重太重需要减肥，少于10斤输出体重太轻

```javascript
 var hight= prompt("请输入你的身高(单位斤)：");
    var weight= prompt("请输入你的体重(单位斤)：");
    hight =parseInt(hight);
    weight =parseInt(weight);

    var standard = (hight-108)*2-weight;

    if(standard>=-10 && standard<=10){
        alert("你的身高是："+hight+",体重是："+weight+"和标准体重差值为"+Math.abs(standard)+"斤,简直是完美身材");
    }else if(standard<-10){
        alert("你的身高是："+hight+",体重是："+weight+"和标准体重差值为"+Math.abs(standard)+"斤,需要减肥哟亲");
    }else if(standard>10){
        alert("你的身高是："+hight+",体重是："+weight+"和标准体重差值为"+Math.abs(standard)+"斤,亲，赶快来两斤煎饼果子吧");
    }else{
        alert("你是外星人吧！");
    }
```

* 分别输入三角形三条边长判断是否是一个三角形

```javascript
    var x= prompt("请输入第一条边：");
    var y= prompt("请输入第一条边：");
    var z= prompt("请输入第三条边：");
    x =parseInt(x);
    y =parseInt(y);
    z =parseInt(z);

    if((x + y) > z && (x + z) > y && (y + z) > x){
        alert("三条边"+x+","+y+","+z+"能够组成一个三角形");
    }else{
        alert("三条边"+x+","+y+","+z+"不能组成一个三角形");
    }

```

* 从键盘分别输入3个整数，求出最大值并输出在控制台

```javascript
//方法一
 var first= prompt("请输入第一个整数：");
    var second =prompt("请输入第二个整数：");
    var third= prompt("请输入第三个整数：");

    first = parseInt(first);
    second=parseInt(second);
    third=parseInt(third);

    var max ;

    if(first<second){
        if(second<third){
            max =third;
        }else{
            max= second;
        }
    }else{
        if(first<third){
            max =third;
        }else{
            max =first;
        }
    }
    alert("三个数"+first+","+second+","+third+"中最大的数是"+max);
```

```javascript
//方法二：三目运算
    var first= prompt("请输入第一个整数：");
    var second =prompt("请输入第二个整数：");
    var third= prompt("请输入第三个整数：");

    first = parseInt(first);
    second=parseInt(second);
    third=parseInt(third);

    var max =(first>second?(first>third?first:third):(second>third?second:third));

    alert("三个数"+first+","+second+","+third+"中最大的数是"+max);
```

* 从键盘分别输入3个整数分别依次代表小时(0-23)分钟(0-59)秒(0-59),然后由程序输出下一秒时间15:09:09

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

* 写个彩票游戏：分别随机生成2个一位数，提示用户猜测如果完全匹配奖励1000，只匹配数字没顺序奖励300，只匹配1个数字奖50，没匹配则没中奖

```javascript
 var first= prompt("请输入第一个[0-9]之间中奖号码：");
    var second =prompt("请输入第二个[0-9]之间中奖号码：");

    first = parseInt(first);
    second=parseInt(second);

    //随机生成开奖号码
    var one = Math.floor(Math.random()*10);
    var two = Math.floor(Math.random()*10);

    if(first==one && second==two){
        alert("开奖号码是【"+one+","+two+"】;你买的号码是["+first+","+second+"]恭喜你中奖1000元");
    }else if(first==two && second==one){
        alert("开奖号码是【"+one+","+two+"】;你买的号码是["+first+","+second+"]恭喜你中奖300元");
    }else if(first==one ||first==two ||second==one ||second ==two){
        alert("开奖号码是【"+one+","+two+"】;你买的号码是["+first+","+second+"]恭喜你中奖50元");
    }else{
        alert("开奖号码是【"+one+","+two+"】;你买的号码是["+first+","+second+"]骚年不服气？再来一次吧");
    }
```

* switch分支结构
  * 如果条件是有穷可列举推荐使用switch,若果条件是在一个范围内，推荐使用if
  * 表达式值是恒等的关系，类型要一致
  * 表达式常用的数据类型是字符串，数值

```javascript
switch(表达式){
       case 值1: //语句集合
                break;
       case 值2: //语句集合
                break;
       case 值N: //语句集合
                break;
       default: //语句集合
}
```

```javascript
   var  s = prompt("请输入一个字符");
    switch (s){
        case  "a" : alert("输入了a"); break;
        case  "b" : alert("输入了b"); break;
        case  "c" : alert("输入了c"); break;
        default :alert("其他值");
    }
    console.log("break过后，跳出switch分支");
```

* 需求:输入1-12之间的数值，输入1的时候，提示这是一月份，依次类推

```javascript
  var  s = prompt("请输入一个字符");
    s = parseInt(s);
    switch (s){
        case  1 : alert("这是1月份"); break;
        case  2 : alert("这是1月份"); break;
        case  3 : alert("这是3月份"); break;
        case  4 : alert("这是4月份"); break;
        case  5 : alert("这是5月份"); break;
        case  6 : alert("这是6月份"); break;
        case  7 : alert("这是7月份"); break;
        case  8 : alert("这是8月份"); break;
        case  9 : alert("这是9月份"); break;
        case  10 : alert("这是10月份"); break;
        case  11 : alert("这是11月份"); break;
        case  12 : alert("这是12月份"); break;
    }
    console.log("break过后，跳出switch分支");
```

* 需求：输入1-12之间的数值，输入1,2,3的时候，提示这个一季度，依次类型

```javascript
//利用case穿透性：一旦匹配到某个case，该case没有break,执行完该case,后面的case都会执行，直到遇到break,或者是分支结束
var  s = prompt("请输入一个字符");
    s = parseInt(s);
    switch (s){
        case  1 :
        case  2 :
        case  3 : alert("这是1季度"); break;
        case  4 :
        case  5 :
        case  6 : alert("这是2季度"); break;
        case  7 :
        case  8 :
        case  9 : alert("这是3季度"); break;
        case  10 :
        case  11 :
        case  12 : alert("这是4季度"); break;
    }
    console.log("break过后，跳出switch分支");
```

* 需求：输入年月日，求出本年度过了多少天

```javascript
    var  year = prompt("请输四位数的年：");
    var  month = prompt("请输月：");
    var  day = prompt("请输日：");
    year = parseInt(year);
    month = parseInt(month);
    day = parseInt(day);
    var total =0; //存储过了多少天
    switch (month){
        case 12:
            total+=30;
        case 11:
            total+=31;
        case 10:
            total+=30;
        case 9:
            total+=31;
        case 8:
            total+=31;
        case 7:
            total+=30;
        case 6:
            total+=31;
        case 5:
            total+=30;
        case 4:
            total+=31;
        case 3:
            if((year%4==0&&year%100!=0)||year%400==0){
                total+=29;
            }else{
                total+=28;
            }
        case 2:
            total+=31;
        case 1: total+=day;
    }
    alert(year+"年已经过去了"+total+"天");
```

* 输入星期的首字母，判断是星期几，如果首字母不能判断，则根据第二个字母判断

```javascript
 var first =prompt("请输入第一个字母");

    switch (first){
        case "M":
            alert("星期一");break;
        case "T":
            var second=prompt("第一个字母无法判断星期几,请输入第二个字母");
            if(second==="U"){
                alert("星期二");
            }else{
                alert("星期四");
            }
            break;
        case "W":
            alert("星期三");break;
        case "F"  :
            alert("星期三");break;
        case "S":
            second=prompt("第一个字母无法判断星期几,请输入第二个字母");
            if(second==="A"){
                alert("星期六");
            }else{
                alert("星期天");
            }
            break;
    }
```

循环控制

* 当一个功能需要重复执行N多次的时候，就会使用循环流程去控制
* 当一个功能有些量可以通过循环去控制的时候，也可以采用循环

```java
//for循环
for(Ⅰ初始表达式;Ⅱboolean表达式;Ⅲ表达式){
    // Ⅳ循环体，代码集合
}
//执行顺序  Ⅰ(有且只会执行一次)->Ⅱ(true)->Ⅳ->Ⅲ->Ⅱ(true)->>Ⅳ->Ⅲ...->Ⅱ(false)->结束循环(IV不会被执行)
```

* 变种for循环

```javascript
  var i =1;
     for(;;){
         console.log("数星星"+i);
         i++;
         if(i>10){
             break;
         }
     }
```

* 标准的for循环

```javascript
 for(var i =1;i<11;i++){
         console.log("数星星"+i);
     }
```

* 对于for循环，if分支的大括号内定义的变量是全局变量，注意对后面代码的影响

```javascript
for(var i =1;i<11;i++){
         console.log("数星星"+i);
     }
 console.log(i);//11

for(var i =1;i<11;i++){
         console.log("数星星"+i);
     }
 console.log(i);//11
```

* 需求：求1+2+3+...+100的和

```javascript
var result=0;

     for(var i=1;i<101;i++){
         result+=i;
     }

     alert(result);//5050
```

* 关键字continue：跳出本轮循环，继续下一次循环

```javascript
//求1+3+5+...+99的和
 var result=0;

     for(var i=1;i<101;i++){

         if(i%2==0){
             continue; //跳出本轮循环，继续下一次循环
         }
         result+=i;
     }
     alert(result);//5050
```

* 关键字break：用于结束循环体或者结果switch结果；return是结束函数体

```javascript
     var result=0;
     function a(){
         for(var i=1;i<101;i++){
             if(i==50){
                return ; //结束函数体
             }
             result+=i;
         }
     }
     a();
     alert(result);//1225
```

```javascript
   for(var i=1;i<101;i++){
             if(i==50){
               break ; //结束循环体
             }
             result+=i;
    }
   alert(result);//1225
```

* 练习作业
* 求1+3+5+7+..99的和

```javascript
 var sum =0;
    for(var i =1;i<=99;i+=2){
        sum +=i;
    }
    alert("1+3+5+7+..99的和为"+sum);
```

* 求1-2+3-4+5-6...-100的和

```javascript
var sum =0;
    for(var i =1;i<=100;i++){
        if(i%2==0){
            sum += -i;
        }else{
            sum +=i;
        }
    }
    alert("1-2+3-4+5-6...-100的和为"+sum);
```

* 求100以内能被3整除的数的和

```javascript
//方法一
var sum =0;
    for(var i =1;i<=100;i++){
        if(i%3==0){
            sum += i;
        }
    }
    alert("100以内能被3整除的数的和为"+sum);
```

```javascript
//方法二
 var sum =0;
    for(var i =3;i<=100;i+=3){
      sum += i;
    }
    alert("100以内能被3整除的数的和为"+sum);

```

* 输出1-100之间的整数，如果这个数是3的倍数或者是5的倍数,就不输出

```javascript
var arr =[];
    for(var i =1;i<=100;i++){
      if(i%3==0 || i%5==0){
          continue;
      }else{
         arr.push(i);
      }
    }
    alert("1-100之间的整数，不能被3整除或者不能被5的整除的数有"+arr);
```

* 分别输入2个正整数，求两个数的最小公倍数

```javascript
 var x= prompt("请输入第一个正整数：");
    var y= prompt("请输入第二个正整数：");

    x =parseInt(x);
    y =parseInt(y);

    var min = (x-y)>0?x:y; //求输入两个数最小的数
    var flag=false;  //假设不存在最小公倍数
    var numer=0;  //存储最小公倍数

    for(var i=2;i<=min;i++){
      if(x%i==0 && y%i==0){
          numer=i;
          flag=!flag;  //存在最小公倍数
          break;

      }
    }
    if(flag){
        alert(x+","+y+"存在最小共倍数是:"+numer);
    }else{
        alert(x+","+y+"不存在最小共倍数");
    }
```

* 天朝有一个乞丐姓洪，去天桥要钱，第一天要了1块钱，第二天要了2块钱，第三天要了4块钱，第四天要了8块钱，以此类推，问题： 洪乞丐干10天，收入是多少？

```java
 var money=0; //乞丐要的钱
    for(var i=1;i<=10;i++){
      money += (i**2);
    }
    alert("洪乞丐干10天，收入是"+money+"元");
```

* 一张纸的厚度大约是0.08mm，对折多少次之后能达到珠穆朗玛峰的高度（8848.13米）

```javascript
 var number =0 //需要折叠的次数
    var paper = 0.00008 ;//一张纸厚度
    for(;paper<8848.13;){
        paper =paper*2;
        number++;
    }
    alert("对折"+number+"次之后能达到珠穆朗玛峰的高度");

```

* 输出9*9乘法表

```javascript
  for(var i=1;i<10;i++){
       for(var j=1;j<=i;j++){
           document.write(""+j+"*"+i+"="+(i*j)+"&nbsp;&nbsp;&nbsp;&nbsp;");
       }
       document.write("<br/>")
  }
```

* 求1!+2!+3!+…..+10!

```javascript
 var sum =0; //存放最终总和
   var every =1; //存放每个数的阶乘
   for(var i=1;i<=10;i++){
       for(var j=i;j>=1;j--){
           every*=j
       }
       sum+=every;
       every=1; //每个数阶乘算完，恢复初始值
   }
   alert("1!+2!+3!+…..+10!的和为"+sum);
```

* 用循环结构输出如下的数值列表

```javascript
/* 1		 10			 100		 1000
   2		 20			 200		 2000
   3		 30			 300		 3000
   4		 40			 400		 4000
   5		 50			 500		 5000*/

 for(var i=1;i<=5;i++){
      for(var j=1;j<=4;j++){
          document.write(i*(10**(j-1))+"&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;");
      }
      document.write("<br/>");
  }
```

* 现在市场上公鸡5元每只，母鸡3元每只，小鸡3只1元，现在有100元需要买一百只鸡,而且三种鸡都必须买，请问有多少种买法刚好把钱花完，并输出每种鸡各买多少只？

```javascript
//方法一 三层循环
var cock = parseInt(100/5);//全买公鸡，最多买20只
    var hen  = parseInt(100/3); //全买母鸡，最多买33只
    var chick= 100;//题目要求最多买100只鸡，全买小鸡也只能有100只小鸡
    var money =100; //100块钱买鸡
    var count =0; //买鸡的可能数
    for(var i=1;i<cock;i++){
        for(var j =1;j<hen;j++){
            for(var k =3;k<chick;k+=3){
                if(i*5+j*3+k/3==money&&(i+j+k==100)){
                    count++;
                    console.log("公鸡买"+i+"只"+",母鸡买"+j+"只"+",小鸡买"+k+"只");
                }
            }
        }
    }
    console.log("有"+count+"种买法刚好把钱花完");

```

```javascript
//方法二 两层循环
var cock = parseInt(100/5);//全买公鸡，最多买20只
    var hen  = parseInt(100/3); //全买母鸡，最多买33只
    var money =100; //100块钱买鸡
    var count =0; //买鸡的可能数
    for(var i=1;i<cock;i++){
        for(var j =1;j<hen;j++){
            if(i*5+j*3+(100-i-j)/3==money){
                count++;
                console.log("公鸡买"+i+"只"+",母鸡买"+j+"只"+",小鸡买"+(100-i-j)+"只");
            }
        }
    }
    console.log("有"+count+"种买法刚好把钱花完");
```

* 假设你月收入是3000，除开平时花销，每个月留下1000块钱进行投资。然后你选了一个稳定回报的基金投资后，达到了每年20%的投资回报率。 那么问题来了，以每个月投资1000块钱的节奏，持续投资多少年，总收入达到100万 （复利计算按照每年12000投入计算，不按照每月计息）复利公式：F = p* ( (1+r)^n );
  F 最终收入
  p 本金
  r 年利率
  n 存了多少年

```javascript
var year =1;
   var money=12000;//本金初始值12000元

    for(year;;year++){
        money = money*((1+0.2)**year);
        if(money>=1000000){
            break;
        }
    }
    alert("屌丝持续投资"+year+"年，总收入可达到100万,走上人生巅峰，迎娶白富美");

```

* 输出所有的水仙花(水仙花数定义：1. 一定是3位数;2. 每一位的立方加起来恰好是这个数本身，比如153=111+5*5*5+3*3*3)

```javascript
//题目的关键是把一个三位数的每个位拆开来
for(var i=100;i<=999;i++){
     var x= parseInt(i/100) //百位
     var y= parseInt(i/10)%10 //百位
     var z= i%10  //个位

     if(i==(x*x*x)+(y*y*y)+(z*z*z)){
        console.log(i+"是水仙花");
     }
  }
```

* while循环
  * while循环可以和for循环进行转换
  * 当不知道循环的次数，推荐使用while循环，循环一定要有出口
* 需求：可以不断输入数据，直到遇到-1就停止，并求输入的数据最大的数

```javascript
//语法
while(布尔表达式){
    //循环体
}
```

```javascript
 var max =0;
   while(true){
       var number= prompt("请输入一个数:");
       number =parseInt(number);
       if(number==-1)break;
       if(number>max) max =number;

   }
   alert("最大值为："+max);
```

* do...while循环
  * 首先执行一次代码，再循环

```javascript
//语法
do{
    //代码集合
}while(布尔表达式);
```

* lable标签
  * 控制跳出其他层循环

```javascript
//语法
out: for(){

    for(){
        if(){
           break out;
           }
    }
}
```

* 作业：求任意两个区间内的质数

```javascript
 function find(start,end){
     //交换变量,如果start传入小于end
     if(start<end){
         start^=end;
         end^=start;
         start^=end;
     }
    for(var i=start;i<=end;i++){
        var flag= false;
        for(var j =2;j<i;j++){
            if(i%j==0){ //如果整除，肯定不是质数
                flag=true;
                break;
            }
        }
        if(!flag){
            console.log(i+"是质数！");
        }
    }
}
find(300,50);
```

* 求n2大于12000的最小数n

```javascript
 var n=1;
    while(n**2<12000){
        n++;
    }
    alert("n2大于12000的最小数n是："+n);
```

* 输入一个正整数,把一个正整数逆序输出(比较难)(例如：输入1342 ，输出2341)

```javascript
 var input= prompt("请输一个正整数：");
   input=parseInt(input);
   var origin=input;
   var output=0;
   var current =0; //余数
   var reverse =0; //初始反转
   while(input>=10){
       current=input%10; //每次余数
       input =parseInt(input/10); //每次的商
       reverse =(current+reverse)*10;
   }
   output =reverse+input;
   alert(origin+"倒叙的结果是："+output);
```



* 输入一个正整数，对它分解质因数(比较难)。(例如：输入20 ，输出20=2*2*5)

```javascript
var input= prompt("请输一个正整数：");
   input=parseInt(input);
   var origin =input;
   var arr =[];
   var plus="";
   var i=2;
   while(i<=(origin/2)){
       if(input%i==0){
           arr.push(i);
           input/=i;
           i=1;
       }
       i++;
   }

   for(var j=0;j<arr.length;j++){
       if(j==(arr.length-1)){
           plus+=arr[j];
       }else{
           plus+=arr[j]+"*";
       }
   }
   alert(origin+"分解质因数为:"+origin+"="+plus);
```



* 输入一个1-9的数字，再输入5-9的数字表示位数，求形如x+xx+xxx+xxxx的和（难，例如第一个数字是5，第二个输入数字是3，式子则为5+55+555）
* 输入整数，直到遇到-1结束，对输入的数进行从小到大排序

