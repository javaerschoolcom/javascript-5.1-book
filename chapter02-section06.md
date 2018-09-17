### 数据类型之函数

##### 函数是干嘛？

* 函数是一段可以反复重复使用的代码，它是为了完成某个功能而存在

##### 函数定义

* 语法1:function  函数名(参数1,参数2,...,参数N){  //N多语句 ;[return  表达式; ]   };

``` javascript
function  sum(x,y) {
        //函数体
        var z =x+y;
        return z;
    }
```

* 语法2:var 变量名 =function(参数1,参数2,...,参数N){ //N多语句 ;[return  表达式; ]};

```javascript
var result =function(x,y){retrun x+y;};
```

* 语法3:var 变量名=Function(参数1,参数2,...,参数N,函数体);

```javascript
var result =new Function("x","y","return x+y;");
```

##### 函数调用

* 语法：函数名(实参1,实参1,...实参N);

```javascript
sum(1,2);//3
```

##### 函数声明自动提升

* 函数式声明可以先调用，再定义

```javascript
sum(1,2);
function  sum(x,y) {
        //函数体
        var z =x+y;
        return z;
 }
```

* 变量式声明必须先声明，再调用

```javascript
var result =function(x,y) {
        //函数体
        var z =x+y;
        return z;
 }
result(1,2);
```

函数注意事项

* 定义了多个函数，函数同名？如果都为同类型声明不论参数个数，都会使用后声明的；如果一个是函数式声明，一个是变量式声明，变量式声明优先级更改

##### 函数作用域

* 全局作用域：作用范围是整个程序运行期间都可以在任意位置使用

```javascript
 var ceshi ="lero";

    function range(){

        console.log(ceshi);

    }
    range();
```

* 局部作用域：函数内部定义的var声明的变量，只能在函数内部使用，不能在外部使用

```javascript
function range(){
       var  ceshi ="lero";
    }
    range();
    console.log(ceshi); //Uncaught ReferenceError: ceshi is not defined
```

* 全局作用域和局部作用域变量同名，优先使用自己作用域的变量，自己作用域没有则会依次往上寻找离它最近的一个作用域，若果都没有，则找全局定义的变量，若还是没找到，则报错。

```javascript
 var ceshi ="lero";
    function panrent(){
        var  ceshi ="lucy";
        console.log("in:"+ceshi);//in:lucy
        function child(){
            var ceshi="lily"
            console.log("child:"+ceshi);//child:lily
        }
        child();
    }
    panrent();
    console.log("out:"+ceshi);//out:lero
```

* 函数执行中，如果内部在使用变量，这些变量的值使用定义环境中的，而非使用环境中的

```javascript
  var ceshi ="lero";
    //函数定义环境:亲妈
    function definedArea(){
        console.log("in:"+ceshi);
    }
    //函数使用环境:后妈
    function userArea(){
        var ceshi='lily';
        definedArea();
    }
    userArea();// lero
    console.log("out:"+ceshi);//out:lero
```

```javascript
 var ceshi ="lero";
    //函数定义环境
    function definedArea(){
        var ceshi="lily";
        var child =function(){
            console.log("in:"+ceshi);
        }
        return child;
    }
    var result =definedArea();
    result();//lily 因为child绑定是定义环境中的变量值
```

非要使用函数使用环境中变量,手动传递参数

``` javascript

    var ceshi ="lero";
    //函数定义环境
    function definedArea(ceshi){
        console.log("in:"+ceshi);
    }
    //函数使用环境
    function userArea(){
        var ceshi='lily';
        definedArea(ceshi);
    }
    userArea();// lily
    console.log("out:"+ceshi);//out:lero

```

##### 函数的参数

* 获取函数定义参数的个数；语法：函数名.length
* 获取函数名称； 语法：函数名.name
* 函数定义的参数，可以不使用
* 函数定义的参数个数可以和函数使用参数个数不一样
* 函数的参数可以是任意数据类型

> 被当做对象使用

```javascript
function userAsObject(x){
        x.speak(); //x被当做对象使用
    }
userAsObject({
        name:"zs",
        age:"17",
        speak:function(){
            alert("hello!"+"my name is:"+this.name+",i am"+this.age+" old");
        }
    });
```

> 被当做函数使用

```javascript
function userAsFunction(x){
        x();
    }
 userAsFunction(function(){alert(111);})
```

* 函数实际上传递的参数都封装到一个对象arguments中，这个对象类似数组，arguemnts.lengt获取的是函数实际参数的个数

求任意数的和

```javascript
 function sum(){
       //debugger;
       var count =0;
       for(var i=0;i<arguments.length;i++){
            count+=arguments[i];
       }
       console.log(count);
    }
    sum(3,2,5,2,3,4,6);
```

