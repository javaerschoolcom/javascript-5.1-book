### Element节点

Element节点属性:

* 如果元素身上有标准属性，都可以通过element.标准属性


* element.id:读写元素id属性的值
* element.title:读写title属性的值
* element.name:读写name属性的值
* element.className:读写class属性的值，返回的是字符串
* element.classList:会返回一个类似数组的集合，可以方便操作样式
  * classList.add("className");//增加一个样式
  * classList.remove("className");//删除一个样式
  * classList.toggle("className",boolean);//切换样式
  * classList.contains("className");//查看该element是否包含指定样式,包含返回true
* element.style:获取样式对象，对象上支持css属性
  * cssText:可以通过字符串方式操作,赋值标准css属性组成的字符串
  * 直接使用css的属性，不过要把标准属性改成驼峰法表示（关键字，保留字前面加css前缀 cssFloat）
  * 支持方法操作,其中的key都是css中标准属性
  * style.setProperty(key,value,"important");
  * style.getProperty(key);
  * style.removeProperty(key);
  * style.getPropertyPriority(key);获取属性优先级 “important” |""
* element.attributes:获取元素上所有属性（包括自定义），组成一个集合
* element.dataset:获取自定义标准属性（data-xxx）
* element.innerHTML:读写该元素的子节点和node.textContent有差别

* 只获取元素节点的属性

  * element.firstElementChild:获取第一个子元素节点（不会获取文本节点或者注释节点）
  * element.lastElementChild::获取最后一个子元素节点
  * element.previousElementChild:获取上一个兄弟元素节点
  * element.nextElementChild:获取下一个兄弟元素节点
  * element.children:获取元素的所有的子元素节点|childNodes获取所有的子节点

* Element尺寸相关的属性

  * clientWidth:获取元素的宽度（包括style.width+padding）
  * clientHeight:获取元素的高度（包括style.height+padding）
  * clientLeft:获取元素的左边border的宽度
  * clientTop:获取元素的上边border的宽度
  * offsetWidth:获取元素的宽度（包括style.width+padding+border）
  * offsetHeight:获取元素的高度（包括style.height+padding+border）
  * offsetParent:获取该元素最近的有定位的父元素
  * offsetLeft:获取元素左边界离定位父元素左边界的距离
  * offsetTop:获取元素上边界离定位父元素上边界的距离


Element节点方法：

* 获取指定的元素方法同Document，为了缩小查找的范围，除了getElementById()方法没有

  * element.getElementByName();
  * element.getElementByTagName();
  * element.getElementByClassName();
  * element.querySelector();
  * element.querySelectorAll();

* 操作元素节点CRUD方法

  * parentElement.append(node,text);给当前元素节点添加子节点,作为最后一儿子（可以是元素也可以是文本）；
  * parentElement.prepend(node.text);给当前元素节点添加子节点,作为第一个儿子（可以是元素也可以是文本）；
  * siblingElement.after(node);在某个元素节点后面添加兄弟节点
  * siblingElement.brefore(node);在某个元素节点前面添加兄弟节点
  * element.replaceWith(node);
  * element.remove();//删除元素自己


* 提供了一组操作属性的方法(CRUD)

  * element.setAttributeNode(attrNode);//给元素添加属性节点
  * element.removeAttributeNode(attrNode);//删除元素某个属性节点
  * element.setAttribute("key","value");//给元素节点添加属性
  * element.setAttribute("key","value1");//给元素节点修改属性
  * element.removeAttribute("key");//删除元素某个属性
  * element.getAttribute("key");//获取元素某个属性
  * element.hasAttribute("key");//判断元素是否有某个属性，若果有返回true
  * element.hasAttributes();//判断该元素上是否具有具有属性，至少有一个属性就返回true


```javascript
var div = document.getElementById("c");
var attr= document.createAttribute("id");
attr.value="lero";
div.setAttributeNode(attr);
//等同于
div.setAttribute("id","lero");

```

Element操作表格

* table.insertRow(索引)；//创建一行
* tr.insertCell(索引)；//创建某一行的单元格
* table.deleteRow(索引)；//删除行
* tr.deleteCell(索引)；//删除某一行单元格

```javascript
var table= document.getElementById("table");
var tr= table.insertRow(0);
tr.insertCell(0).innerHTML="姓名";
tr.insertCell(1).innerHTML="年龄";
tr.insertCell(2).innerHTML="分数";

```


* 常用属性：
* table.tBodies;//获取到tbody的集合
* tbody.rows;//获取到tbody中的行的集合
* tr.cells;//获取tr中的列的集合

```javascript
table.tBodies[0].rows[0].cells[0]
```

Element表单操作

```javascript
<form name="myform">
<input type="text" name="username"> <!--type=password|hidden -->
<input type="radio" value="1" name="gender">男
<input type="radio" value="2" name="gender">女
<select name="city">
<option value="1">北京</option>
<option value="2">上海</option>
<option value="3">广州</option>
</select>
<input type="button" value="提交" name="submit">
</form>
<img src="1.png" />
<a href="http://www.baidu.com">百度</a>

//快速获取表单
document.forms.myform
//快读获取name=username的input框
document.forms.myform.username
//控制单选或者多选被选中
document.forms.myform.gender[1].checked=true;
//控制下拉框某一个option被选中
document.forms.myform.city.options[1].selected=true;
//控制按钮禁用
document.forms.myform.submit.disabled=true
//点击切换图片
document.images[0].src="2.png";
//点击切换链接
document.linkes[0].href="http://www.taobao.com";


```
