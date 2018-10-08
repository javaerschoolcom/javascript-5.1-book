JSON

它是(JavaScript Object Notation )的缩写,它是一种用于数据交换的文本格式，每个 JSON 对象，就是一个值

* 语法规则
  * 如果是复合类型只支持狭义对象和数组（函数，日期，正则都不支持）
  * 如果是原始类型只支持字符串,数值(必须以十进制表示),null,布尔值(NaN,undefined,infinity不支持)
  * 如果是对象,对象的key必须使用双引号括起来(不能使用单引号)
  * 如果值是字符串,字符串也必须使用双引号括起来(不能使用单引号)
  * 如果的对象，对象的最后一个键值对一定不能有逗号


```javascript
[32, 64, 128, 0xFFF] // 错误
{name: "张三", 'age': 32 }  // 错误
{"name": "张三", "age": undefined } //  错误

["one", "two", "three"]  //正确
{"one": 1, "two": 2, "three": 3 } //正确
{"names": ["张三", "李四"] } //正确
[{ "name": "张三"}, {"name": "李四"} ] //正确
//空数组和空对象都是合格的 JSON 值，null本身也是一个合格的 JSON 值
```

* 使用JSON构建省市区
* JSON和字符串互换
  * JSON.Stringify() 把JSON对象转字符串
  * JSON.parse()把字符串转对象对象


```javascript
// 把JSON对象转字符串
var obj ={name:"lero",age:18};
JSON.stringify(obj);
//把字符串转对象对象
var str ='{"name":"lero","age":18}';
JSON.parse(str);
JSON.parse("\"name\"") //字符串本身必须带有双引号
```

