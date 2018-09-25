### Array函数

##### 基本用法

##### push

* 往数组末尾添加元素，返回值是添加元素后数组的长度

```javascript
var arr=[];
arr.push("a");       // 1     添加一个元素
arr.push("b","c");   // 3     添加N多个元素
```

##### pop

* 从数组末尾删除一个元素，返回值是删除掉的那个元素

```javascript
var arr=["a","b","c"];
arr.pop(); //c
arr; // ["a","b"]
```

##### unshift

* 往数组开始位置添加元素，返回值是添加元素后数组的长度

```javascript
var arr=["a","b","c"];
arr.unshift("d"); //4
arr.unshift("e","f"); //6
arr; // ["e","f","d","a","b","c"]
```

##### shift

* 从数组开始位置删除一个元素，返回值是删除掉的那个元素

```javascript
var arr=["a","b","c"];
arr.shift(); //a
arr //["b","c"]
```

##### slice

* 截取原数组某个区间元素，然后把截取掉的元素组成一个新数组，```原数组不变```
* 第一个参数，截取起始位置索引，左闭
* 第二个参数，截取结束位置索引，右开
* 如果参数都是负数，可以转化为正数，转化规则：参数+length
* 如果第一个参数小于第二个参数，结果为空数组
* 如果不传递参数，相当于拷贝数组
* 如果只传递一个参数，第二个参数默认为length

```javascript
var arr=["a","b","c","d","e"];
arr.slice(0,2); // ["a","b"]
arr.slice(2); //["c","d","e"]        如果只传递一个参数，第二个参数默认为length
arr.slice(-2,-1) // ["e"]  ===> arr.slice(-2+5,-1+5);
arr.slice(-1,2); //[]                 如果第一个参数小于第二个参数，结果为空数组
arr.slice(); //["a","b","c","d","e"]  如果不传递参数，相当于拷贝数组
```

##### splice(start,n,newarr1,newarr2...)

* 对数组进行新增元素，删除元素，修改元素综合操作，返回值为截取元素组成的数组，``原数组改变``
* 第一个参数：截取起始位置索引，包含该索引
* 第二个参数：从第一个参数开始起，截取元素的个数
* 第三个及后面的参数，添加元素到第一个参数的位置，包含该索引

```javascript
//基本操作
arr=["a","b","c","d","e"];
arr.splice(1,2,"hello","world") //["b","c"];
arr //['a',"hello","world"]

//有点类似于slice操作
var arr=["a","b","c","d","e"];
arr.splice(1,2) //["b","c"];
arr //["a","d","e"]

//类似于push操作
var arr=["a","b","c","d","e"];
arr.splice(5,0,"hello") //[];
arr //["a","b","c","d","e","hello"]

//类似于pop操作
var arr=["a","b","c","d","e"];
arr.splice(4,1) //["e"];
arr //["a","b","c","d"]

//类似于shift/unshift略

```

##### join

* 每个元素之间分割方式返回分割后的字符串,``原数组不变``

```javascript
var arr=["a","b","c","d","e"];
arr.join() //a,b,c,d,e
arr.join("*") //a*b*c*d*e
```

##### concat

* 合并数组返回一个新数组，``原数组不变``

```javascript
var arr=["a","b"];
var arr1=["c","d","e"];
arr.concat(arr1) // ["a","b","c","d","e"]; 参数为数组
arr //["a","b"]
arr.concar("1","2") //["a","b",'1','2']; 参数为非数组
```

##### indexof

* 从开始位置查找指定元素是否在数组中，找到就返回该元素所在的索引，找不到则返回-1

```javascript
var arr=["a","b","a"];
arr.indexof("a"); //0   找到
arr.indexof("1")  //-1  没找到
```

##### lastIndexOf

* 从结束位置查找指定元素是否在数组中，找到就返回该元素所在的索引，找不到则返回-1

```javascript
var arr=["a","b","a"];
arr.lastIndexof("a"); //2
arr.lastIndexof("1"); //-1
```

##### reverse

* 反转数组，返回反转后的数组，``原数组改变``

```javascript
var arr=["a","b","c"];
var result= arr.reverse(); //["c","b","a"]
console.log(result,arr);  // ["c","b","a"]
```

##### 数组排序

* 冒泡法

```javascript
//下沉冒泡，每一轮比较后，求出当轮最大的值，跑到数组右边
var arr=[2,1,33,13,43,23,99,12];
var temp =0;
     for(var i=0;i<arr.length;i++){ //比较的轮数
         for(var j=0;j<arr.length-i-1;j++){
             if(arr[j]>arr[j+1]){
                 temp=arr[j];
                 arr[j]=arr[j+1];
                 arr[j+1]=temp;
             }
         }
     }
     alert(arr);
//上浮冒泡，每一轮比较后，求出当轮最小的值，跑到数组左边
var arr=[2,1,33,13,43,23,99,12];
var temp =0;
for(var i=0;i<arr.length;i++){ //比较的轮数
         for(var j=i+1;j<arr.length;j++){
             if(arr[i]>arr[j]){
                 temp=arr[i];
                 arr[i]=arr[j];
                 arr[j]=temp;
             }
         }
     }
  alert(arr);
```

* 快速排序法
  * （1）在数据集之中，选择一个元素作为"基准"（pivot）
  * （2）所有小于"基准"的元素，都移到"基准"的左边；所有大于"基准"的元素，都移到"基准"的右边
  * （3）对"基准"左边和右边的两个子集，不断重复第一步和第二步，直到所有子集只剩下一个元素为止

```javascript
   var quickSort = function(arr) {
　　if (arr.length <= 1) { return arr; }
　　var pivotIndex = Math.floor(arr.length / 2);
　　var pivot = arr.splice(pivotIndex, 1)[0];
　　var left = [];
　　var right = [];
　　for (var i = 0; i < arr.length; i++){
　　　　if (arr[i] < pivot) {
　　　　　　left.push(arr[i]);
　　　　} else {
　　　　　　right.push(arr[i]);
　　　　}
　　}
　　return quickSort(left).concat([pivot], quickSort(right));
};
var arr=[2,1,33,13,43,23,99,12];
alert(quickSort(arr));
```

* 输入N多个整数，输入-1结束，并对它们从小到大排序输出

高级用法

##### sort

* 默认的排序规则是字典顺序，返回排好序的数组，``原数组改变``

```javascript
var arr=[1,2,11,22]
arr.sort(); //[1,11,2,22]
```

* 需要自定义排序，需要重写排序规则
  * 第一个参数减去第二个参数，结果大于0，升序排，小于0，降序排

```javascript
var arr=[1,2,11,22]
arr.sort(function(x,y){return x>y;});
```

```javascript
//先比较年龄，按从小到大排序，如果年龄相等，再比较分数，分数从小到大排序
var student1={
        "name":"Lero",
        "age":18,
        "score":100
    }
    var student2={
        "name":"Lero",
        "age":20,
        "score":99
    }
    var student3={
        "name":"Lero",
        "age":19,
        "score":98
    }
    var student4={
        "name":"Lero",
        "age":19,
        "score":99
    }

    arr =[student1,student2,student3,student4];

   var xx= function(x,y){
        return x.age==y.age?x.score>x.score:x.age>y.age;
   }

   var result=arr.sort(xx);
   console.log(arr);
```

##### map

* 依次对数组中每一个元素做相同的操作，返回操作过后的新数组，``原数组没改变``

```javascript
   var arr2=[1,2,3,4];
   var result =arr2.map(function (value, index, array) {
        console.log("value->"+value);
        console.log("index->"+index);
        console.log("array->"+array);
        //value =array[index];
        if(index%2==0){
            return value**2;
        }else{
            return value;
       }
   })

   console.log(result); //arr3[1,2,9,4]
```

##### filter

* 对原数组每个元素进行过滤操作，返回过滤后的新数组，``原数组不变``

```javascript
var arr2=[1,2,3,4,5,6,7];

   var result =arr2.filter(function (value, index, array) {
        console.log("value->"+value);
        console.log("index->"+index);
        console.log("array->"+array);
        if(value>3){
            return value;
        }
   })

   console.log(result); //[4,5,6,7]
```

##### some

* 对原数组每个元素进行判断，如果有一项返回true,函数结果就为true,``原数组不变``

```javascript
var arr2=[1,2,3,4,5,6,7];
var result =arr2.every(function (value, index, array) {
        if(value>3){
            return true;
        }
   })
 console.log(result);//true
```

##### every

* 对原数组每个元素进行判断，如果有一项返回false,函数结果就为false,``原数组不变``

```javascript
var arr2=[1,2,3,4,5,6,7];
var result =arr2.every(function (value, index, array) {
        if(value>3){
            return true;
        }
   })
 console.log(result);//fasle
```

##### forEach

* 遍历数组，没有返回值，如果需要对数组修改后返回，请使用map|filter

##### reduce

* 第一个参数：默认第一次执行为数组第一个元素，第二次为上一次返回的结果
* 第一个参数：默认第一次执行为数组的第二个元素，第二次开始分别依次为数组的其他元素

```javascript
   //求数组各元素的累加结果
   var arr2=[1,2,3,4,5,6,7,8,9,10];
   var result = arr2.reduceRight(function(x,y){
       console.log("x->"+x);
       console.log("y->"+y);
       return x+y;//10
   })
    console.log(result);//55
```

##### reduceRight

* 第一个参数：默认第一次执行为数组最后一个元素，第二次为上一次返回的结果
* 第二个参数：默认第一次执行为数组倒数第二个元素，第二次开始分别依次为数组的其他元素

```javascript
   //求数组各元素的累加结果
   var arr2=[1,2,3,4,5,6,7,8,9,10];
   var result = arr2.reduceRight(function(x,y){
       console.log("x->"+x);
       console.log("y->"+y);
       return x+y;//10
   })
    console.log(result);//55
```

