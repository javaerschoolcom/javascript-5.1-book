### 数据类型之对象

##### 对象定义

* 由花括号包裹的内容，里面的内容按照键值对的方式进行组织，每个键值对之间用逗号隔开，最后一个键值对的末尾不加逗号，其中键本质上是字符串，值可以是任何的数据类型，组成了一个无序的集合。

``` javascript
var persion ={
        name:"lero",
        age:18,
        gender:undefined,
        hasParent:true,
        parent:{
            name:"father"
        },
        hasSon:null,
        fav:["足球","篮球"],
        speak:function(){
            alert("i am chinese!"); //调试经常使用
        }
    };
```

* 注意事项:key本质上字符串，命名的时候尤其注意不能出现以下方式

``` javascript
 1p:"这是错误的key命名，不满足标识符命名规则"
 p.1:"这也是错误的命名方法",
 p x:"key中不能包含特殊的符号，比如空格，点"
```

##### 对象的使用

* 取出对象中的某个key对象的值
  * 语法1(标准key)：对象.属性名称 eg:persion.name -->lero
  * 语法2(非标准key):对象["属性名称"]eg:persion["3.14"]
  * 调用对象函数：对象.函数名(实参):
  * 如果存在多个层次，一层一层按照语法进行，直到目标位置
* 给对象赋值
  * 语法：对象.属性名=属性值；

##### 对象引用

* 两个或者对个变量引用同一个对象的时候，一个变量修改对象的属性,另一个变量也同时改变

``` javascript
var one={name:"lero"};
var two=one;
one.name="lily";
console.log(two.name);//lily
```

##### 对象的动态性

* 定义对象的时候，可以是空对象，可以动态的往对象上添加属性和值。

```javascript
 var a ={};
    a.p=1;
    a.name="xx";
    a.speak= function(){};
    a.toString="oo";
```

##### 查看对象的属性

* Object.keys()可以查看对象的属性名称

```javascript
var a ={};
    a.p=1;
    a.name="xx";
    a.speak= function(){};
    a.toString="oo"; //覆盖继承的toString方式
console.log(Object.keys(a)); //["p","name","speak","toString"]
```

##### 删除对象的属性

* delete 对象.属性名，如果删除成功返回true|删除失败返回false

```javascript
var a ={};
    a.p=1;
    a.name="xx";
    a.speak= function(){};
console.log(delete a.p); //true 删除掉返回true
console.log(a.p);//undefined  代表删除成功
consele.log(delete a.toString); //返回true，但是没有删掉，因为它设计为不可删除属性
```

##### 查看对象是否包含某个属性

* 属性名 in  对象名 判断某个对象是否拥有某个属性，也能够查看继承的属性

```javascript
 var demo ={
        name:"lero"
    };
    console.log("name" in demo);//true 自己身上的属性
    console.log("toString" in demo);//true 继承的属性
```

* 判断一个属性是否是自己拥有的而不是继承?

``` javascript
 var demo ={
        name:"lero"
    };
    console.log(demo.hasOwnProperty("name"));//true  自己身上的属性
    console.log( demo.hasOwnProperty("toString"));//false 继承的属性
```

##### 遍历对象的属性

* for...in,遍历的时候会把继承过来的并且是可遍历的属性都遍历出来（在数组的遍历的时候不推荐使用）

```javascript
 var a ={};
    a.p=1;
    a.name="xx";
    a.speak= function(){};
    a.toString="oo";

     for(var i in a){
         //避免遍历继承属性
         if(a.hasOwnProperty(i)){
             console.log(i+":="+a[i]);
         }
     }
```

##### 总结

* 本小节主要内容
  * 对象定义
  * 对象的使用
  * 对象的属性增删改查遍历以及判断某个属性是否在对象上