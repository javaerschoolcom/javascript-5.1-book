### Document节点

Document属性

* document.doctype:获取文档声明
* document.documentElement:获取文档的根元素->html元素

```javascript
document.documentElement.nodeName;//HTML
document.firstElementChild.nodeName;//HTML
```

* document.body:获取到body元素，返回元素节点

```javascript
document.body.nodeName;//BODY
```

* document.head:获取到head元素，返回元素节点

```javascript
document.head.nodeName;//HEAD
```

* document.title:获取title元素中的文本

```javascript
<title>我是文本</title>
document.title; //我是文本
```

* document.forms:获取页面中所有的表单的集合->返回HTMLCollection集合

```javascript
document.forms[0]; //获取表单集合中第一个表单
document.forms[0].submit();//提交第一个表单
```

* document.links:获取页面中所有的``a``和``area``返回HTMLCollection集合
* document.images:获取页面中所有的``img``返回HTMLCollection集合
* document.scripts:获取页面中所有的``script``返回HTMLCollection集合

HTMLCollection集合特点：

* 具有动态性

```javascript
<form id="f1"></form>
<form id="f2"></form>

document.forms.length;//2
document.forms[0].remove();//
document.forms.length;//1
```

* 只能装element节点
* 可以使用length获取长度，可以使用[]操作

NodeList集合特点：

* node.childNodes:返回的是NodeList集合，可以装任何类型的节点
* document.querySelectorAll("css选择器")：不具有动态性，其余都具有动态性
* 可以使用length获取长度，可以使用[]操作

Document方法

* document.write()；

* 获取页面中指定的元素节点或者是元素节点的集合

  * document.getElementById("id") //传id属性对应的值->只会获取到一个


  * document.getElementByTagName("div"); //传的是html标签->获取到集合
  * document.getElementByName("name"); //传入的是属性name对应的值，获取到NodeList集合
  * document.getElementByClassName("classNmae"); //传入的是属性class对应的值,获取到集合
  * document.querySelector("css选择器"); //返回的第一次匹配到的结果，只有一个
  * document.querySelectorAll("css选择器");//返回的NodeList集合

* 创建方法

  * document.createElement("li");//创建一个element节点，返回该节点
  * document.createTextNode("text")//创建一个文本节点，返回文本节点
  * document.createAttribute("属性名");//创建一个属性节点，返回属性节点