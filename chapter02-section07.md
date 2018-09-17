### 数据类型之数组

##### 数组定义

* 语法1：var 数组名=[];
* 语法2：var 数组名= new Array();//不推荐
* 数组可以存放任意的数据类型 eg:var arr = [1,false,"lero",null,undefined,{},[],function(){}];

##### 数组使用

* 概念1:元素指的是数组每一个位置存放的内容
* 概念2:索引或者下标，每一个位置都有一个编号，编号从零开始，而且是有序的


* 取出数组中某个索引对应的元素语法：数组名[索引]
* 给数组某个索引位置赋值语法：数组名[索引]=值；

##### 数组属性

* length属性可以获取数组的元素个数，索引最大只能是length-1
* 可以通过length属性动态改变数组的长度

```javascript
 var arr = [1,2,3,4,5,6];
  arr.length =10; //增加数组长度
  console.log(arr[9]); //undefined

var arr1 = [1,2,3,4,5,6];
  arr1.length =3; //减小数组长度
  console.log(arr1[3]); //undefined

var arr2 =[1,2,3,4,5,6];
  arr2.length =0; //清空数组
```

* 不推荐使用for...in进行遍历，不仅仅把数组元素遍历出来了，而且把身上的属性也遍历出来了

```javascript
var arr = [1,2,3,4,5,6];
      arr.name='lero';
      //不推荐数组变量使用forin的原因
      for(var i in arr ){
          console.log(arr[i]); //1,2,3,4,5,6,lero
  }
```

* 数组可以添加非数字键，相当于对象添加属性

```javascript
var a = [];
a['name'] = 'lero';a.length // 0
```

##### 二维数组

* 数组中的每一个元素都是由数组构成，这样的数组称为二维数组

```javascript
var arr = [[1,2,3],[1,2,3]];//二维数组定义
   //获取二维数组元素
   arr[0][2];
   //修改二维数组元素
   arr[0][2]=false;
```

