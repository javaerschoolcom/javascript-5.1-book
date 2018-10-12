### 面向对象编程

* 面向对象简称OOP
* 面向过程：是解决问题逐步求精的过程
* 面向对象：把研究的问题转为一个个对象，对象与对象之间是通过通信进行联系的
* 对象：是一类实物的抽象概念，是有边界的。对象主要研究是属性和行为，以研究问题为中心，排除不重要的属性和行为，研究关心的属性和行为
* 对象实例：通过对象创建的个体，实例是个体，对象是抽象
* 如何设计对象：是通过构造函数去设计的
* 关键字new：创建对象的实例使用的
* 关键字this:指的是程序执行的上下文环境，随着运行环境改变，this指代的对象实例也在变化

```javascript
function sum(callback,time){
       callback(time);
}
function  callback(time) {
        console.log(this.name);
}
//传入匿名函数
sum(function(){
    this.name;
},1000)
//传入预定的函数
sum(callback);
//类别
setInterval(function(){},1000);
```



* 如果需要上下文环境固定(this指的对象固定)，可以借助call|applay|bind方法达到效果
* 语法：函数.call(this指代的对象,函数参数1,函数参数2)

  ```javascript
var name="lero";

    function f(a,b){
         console.log(a+b);
        console.log(this.name);
    }

    var o ={
        name:"lily"
    }

    f(); // 3 lero

    f.call(o,1,2); // 3 lily
    f.applay(o,[1,2])//3 lily
    var newf= f.bind(o,1,2)
    newf();//3 lily
  ```

* call与applay区别是：call参数用逗号隔开，applay参数是数组

```javascript
Math.max.apply(null,[1,2,3,4]); //null,undefind ==>指的是window
```

* bind方法一旦调用过后，返回是一个新的函数，使用的时候要重新调用。
* 原型|原型对象
  * 每一个函数都有一个prototype属性，该属性的值是一个对象，这个对象称作该函数的原型；
  * 由该函数创建的每个一个实例对象都有一个（__proto__）属性，该属性的值也是一个对象，这个对象称做该对象实例的原型对象
  * 这个两个属性的值是同一个对象
  * 解决了资源浪费，如果实例对象共享某个函数或者属性，建议采用原型定义

```javascript
 function Persion(name,age){
          this.name=name;
          this.age=age;
          this.speak=function(){
          console.log("我叫"+this.name+",我今年"+this.age+"岁了");
  };
  var  zhansan = new Persion("张三",10);
  var  lisi = new Persion("张四",20);
     Persion.prototype===zhansan.__proto__; //true
     Persion.prototype===lisi.__proto__;  //true
     zhansan.__proto__===lisi.__proto__; //true
```

```javascript
//普通构造函数定义浪费资源
 function Persion(name,age){
          this.name=name;
          this.age=age;
          this.speak=function(){
          console.log("我叫"+this.name+",我今年"+this.age+"岁了");
  };
  console.log(zhansan.speak===lisi.speak);//false  方法一样，每个实例复制了一份，造成资源浪费
```

```javascript
//采用原型定义
 function Persion(name,age){
          this.name=name;
          this.age=age;
  };
 Persion.prototype.speak=function(){
    console.log("我叫"+this.name+",我今年"+this.age+"岁了");
};
 console.log(zhansan.speak===lisi.speak);//true 公用一份资源
```

* 原型链

  一个对象在调用属性或者方法的时候，首先会从自己原型对象上去找，如果没找到，会从原型对象的原型对象上去继续找，如果一直未找到，最终会找到Object的原型,就停止了（Object.prototype是原型链的最顶端）

```javascript
 function Persion(name,age){
          this.name=name;
          this.age=age;
  };
 Persion.prototype=new Array();
 Persion.prototype.speak=function(){
    console.log("我叫"+this.name+",我今年"+this.age+"岁了");
};
 var  zhansan = new Persion("张三",10);
 zhangsan.push(1,2,3);//调用了原型对象[new Array()]的原型对象[Array.prototype]上的push方法
 zhangsan.toString();//调用了原型对象[new Array()]的原型对象[Array.prototype]的原型对象[Object.prototype]上的toString方法
```

