### String

length属性

* 获取字符串长度

charAt

* 给定一个索引，返回该索引上的字符

```javascript
var s ='abc';
s.charAt(1); //b
```

charCodeAt

* 给定一个索引，返回该索引上的字符对应的Unicode码值

```javascript
var s='abc';
s.charCodeAt(0);//97
```

concat

* 用于合并多个字符串,原字符不变

```javascript
var s='abc';
var s1='def';
var result =s.concat(s1).concat(s1).concat(s1);//链式调用
console.log(result,s);
```

indexOf

* 从字符开始位置查找某个子字符串在原字符串中第一次出现的索引，找到返回该索引，找不到返回-1

```javascript
var s='aba';
var result=s.indexOf("a"); //0
result= s.indexOf('a',1) ;//2  从索引1开始查找
```

lastIndexOf

* 从字符结束位置查找某个子字符串在原字符串中第一次出现的索引，找到返回该索引，找不到返回-1

slice

* 截取部分字符串，组成新字符串，原字符串不变
* 使用方式同数组

substring

* 和slice作用一样，用于截取部分字符串 ,不推荐使用

```javascript
var s='cabc';
var result =s.substring(3,1); //第二个参数比第一个参数小，会自动交换顺序
console.log(result,s); //ab  cabc

result =s.substring(-1); //如果参数为负数，结果会把负数变成0
console.log(result,s); //cabc  cabc

```

substr

* 用于截取字符串，组成新字符串，和数组中splice有点相似,原字符串不变
* 第一个参数，代表截取开始索引
* 第二个参数，代表截取的个数

```javascript
var s="abcd";
s.substr(1,3)//bcd
```

toUpperCase

* 把英文字符全变成大写

tolowerCase

* 把英文字符变变成小写

trim

* 去掉字符串前后的空格，包括转移符回车，制表符等

```javascript
 var s='\t\n  a b c   ';
 result = s.trim();
 console.log(result);// a b c  中间空格不能被去掉
```

以下函数除了能正常使用，还支持正则匹配

split

* 把字符串分割成数组

```javascript
 var s='dabc';
 var result = s.split("");
 console.log(result,s);  //[d,a,b,c]  dabc
 result = s.split();
 console.log(result,s);  //['dabc']  dabc
 var s1='hello=xx&everyone=dd';
 result = s.split("&");
 console.log(result,s);  //['hello=xx','everone=dd']
```

replace

* 一般情况下只会替换第一次出现的单个子字符串

```javascript
 var s='hello=xx&everyone=dd';
 result = s.replace("o","A");
 console.log(result,s); //hellA=xx&everyone=dd hello=xx&everyone=dd
 result =s.replace("hello","Hi");
 console.log(result) //Hi=x&everyone=dd
```

match

* 匹配字符串中是否包含指定的子字符串，匹配到则返回第一个匹配到的子字符串组成的数组

```javascript
 var s='hello=xx&everyone=dd';
 result = s.match("o");
 console.log(result); //["o", index: 4, input: "hello=xx&everyone=dd", groups: undefined]
```

search

* 匹配字符串中是否包含指定的子字符串，匹配到则返回匹配到的子字符串开始的索引

```javascript
 var s='hello=xx&everyone=dd';
 result = s.search("o");
 console.log(result,s); //4 hello=xx&everyone=dd
```

练习作业

* 给定任意一段英文，把该英文中每个单词首字母变成大写，再输出该段英文

```javascript
function changeWord(words){
        var words_arr = words.split(" ");
        var result = words_arr.map(function(item,index,arr){
            var number =item.indexOf(","); //逗号所在索引
            if(number!=-1){
                var big=  item.charAt(number+1).toUpperCase(); //大写字母
                var item_arr = item.split(""); //返回数组
                item_arr[number+1]=big;
                return  item_arr.join("");
            }else{
                return  item.charAt(0).toUpperCase()+item.slice(1);
            }
        })
        console.log(result);
    }
 changeWord("In a report on Monday,reuters said a 21-year-old University of Minnesota student sent a WeChat message to a friend in the middle of the night.")
```

* 随便给一段字符串，判断该字符串知否只是有a-z或者A-Z字母组成

```javascript
function isExist(str){
         var arr = str.split("");
         var result =arr.every(function (value) {
             var number =value.charCodeAt(0);
              if((number>=65 && number<=90)||(number>=97 && number<=122)){
                  return true;
              }else{
                  return false;
              }
         });
         if(!result){
             alert("该字符串含有非字母的字符！");
         }
    }
 isExist("owifhewo**");
```

* 给定一段字符串，把该字符串反转

```javascript
 function myreverse(str){
         var arr = str.split("");
         arr.reverse();
         console.log(arr.join(""));
     }
myreverse("abc123");
```

* 给一段只有字母的字符串，统计该段中每个字符出现的频率

```javascript
function getCount(str){
        var obj={};
        var arr =str.split("");
        for(var i=0;i<arr.length;i++){
              if(obj.hasOwnProperty(arr[i])){
                  obj[arr[i]]+=1;
              }else{
                  obj[arr[i]]=1;
              }
        }
        console.log(obj);
        for(var j in obj){
            if(obj.hasOwnProperty(j)){
                console.log(j+"出现了"+obj[j]+"次！");
            }
        }
    }
 getCount("aafhoiehxsffoqhiowqheofwofbwvfwohouwhewwihee");
```

* 给定一个字符串http://www.zhanyisc.com?username=lero&age=18要求把参数截取并组装成对象表示 obj={username:"lero",age:18}

```javascript
 function parseUrl(url){
             var  o={};
             var  param =   url.split("?")[1];
             var arr = param.split("&");
             arr.forEach(function (value) {
                   var temp_arr= value.split("=");
                   o[temp_arr[0]]=temp_arr[1];
             });
             console.log(o);
     }
parseUrl("http://www.zhanyisc.com?username=lero&age=18");
```

* 给定一个字符串，判断该字符串是否只有字母组成
* 给定一段字符串，把该字符串反转
* 给定一个字符串，找出某个字符在该字符串中出现的次数
* 传入任意字符串，统计字符串中的大写字母个数、小写字母个数、数字个数、其他字符个数
* 给定一段英文，把每个单词的首字母变成大小再输出
* 给定一个字符串http://www.zhanyisc.com?username=lero&age=18要求把参数截取并组装成对象表示 obj={username:"lero",age:18}
* 给一段只有字母的字符串，统计该段中每个字符出现的频率




