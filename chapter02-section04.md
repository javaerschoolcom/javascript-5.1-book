### 数据类型之null&undefined&布尔

### null&undefined

* `null`与`undefined`都可以表示“没有”，含义非常相似。

```javascript
undefined == null //true
```

* 区别：`null`是一个表示“空”的对象，转为数值时为`0`；`undefined`是一个表示"此处无定义"的原始值，转为数值时为`NaN`
* `null`表示空值，即该处的值现在为空。调用函数时，某个参数未设置任何值，这时就可以传入`null`，表示该参数为空
* `undefined`表示“未定义”，以下场景会出现``undefined``

```javascript
// 变量声明了，但没有赋值
var a;
console.log(a) // undefined

// 调用函数时，应该提供的参数没有提供，该参数等于 undefined
function f(x) {
  return x;
}
console.log(f()) // undefined

// 对象没有赋值的属性
var  o = new Object();
console.log(o.name) // undefined

// 函数没有返回值时，默认返回 undefined
function f() {}
console.log(f()) // undefined
```

##### 布尔

* 布尔值代表“真”和“假”两个状态。“真”用关键字`true`表示，“假”用关键字`false`表示。布尔值有且只有这两个
* 在===|==|！=|！==|>|>=|<|<=|！等运算符中，运算的结果都是布尔值
* 在需要布尔值的地方，其他类型的值都会转换为布尔值
* 有且仅有6种会转为布尔值``false``,其他任何值都转为``true``包括空对象和空数组

``` javascript
undefined
null
false
0
NaN
""或''（空字符串）
```

