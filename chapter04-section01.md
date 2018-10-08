### DOM概述

##### 什么是DOM

* 一份HTML网页就是DOM,DOM是网页的抽象设计，JS通过操作DOM接口属性或者是方法，就能操作html页面中的内容。DOM叫做文档对象模型.
* DOM的最小组成单元叫节点(Node),节点是一个抽象的概念,浏览器提过了Node顶级接口
* DOM组成分成7大类
  * Document:9:一份HTML构成的网页称作DOM
  * DocumentType:指的是HTML页面的文档声明
  * Element：1:指的是HTML页面中的元素如<head>,<body>
  * Attribute：2:指的是HTML页面中的属性
  * Text:3:指的是HTML页面的中文本
  * Commit:指的是HTML页面中注释
  * DocumentFragment:指的是HTML文档片段
* DOM树指的是把HTML文档抽象成节点后，组成的结构想一颗倒立的树
* DOM树的节点除了跟节点以外，都和其他有一种关系
  * 每个节点都有一个父节点(parentNode)
  * 每个节点可能有子节点（childNodes）
  * 每个节点可能有同级节点（silbing|nextSibling|previousSibling|firstChid|lastChid）

##### Node节点属性

* nodeName：获取该节点的名称
* nodeType:判断每个节点的类型
* nodeValue:获取该节点的值(对Text,Commit有效)，其他节点都返回null
* firstChild:获取当前节点的第一个子节点（可以获取文本或者注释节点），没有的话返回null
* lastChild:获取当前节点的第一个子节点（可以获取文本或者注释节点），没有的话返回null
* nextSibling:获取当前节点的下一个兄弟节点（可以获取文本或者注释节点）,没有的话返回null
* previousSibling:获取当前节点的下一个兄弟节点（可以获取文本或者注释节点）,没有的话返回null
* parentNode:获取一个节点的父节点（可能是Element，Document,DocumentFragement)
* parentElement:只获取该节点Elment类型的父节点
* childNodes:获取所有的子节点组成的NodeList对象（类似于数组）
* textContent:可以获取或者是设置后代的文本，会把文本转义成普通的字符串

  Node节点方法（CRUD）

* appendChild(node):给一个节点添加一个子节点，子节点添加在最后一个位置

```javascript
 <div id="d"><p>默认的儿子</p></div>
 <button id="btn">插入</button>

var node =  document.getElementById("d");
     //事件 onclick 点击事件
     var  btn = document.getElementById("btn");
     btn.onclick=function(){
         var eleNode= document.createElement("p");
         eleNode.textContent="动态添加节点";
         node.appendChild(eleNode);//添加节点
}
```

```javascript
 <div id="d"><p>默认的儿子</p></div>
 <div id="d2">同级关系</div>

 var node =  document.getElementById("d");
     //事件 onclick 点击事件
     var  btn = document.getElementById("btn");
     btn.onclick=function(){
         var eleNode2 =document.getElementById("d2");
         node.appendChild(eleNode2);//添加节点
     }
//说明：如果被添加的节点在html当中，对它进行移动操作，原来在html中的结构就不存在了
```

* removeChild(node):只能通过父节点删除自己，不能自己删自己

```javascript
 <div id="d"><p>默认的儿子</p></div>
var node =  document.getElementById("d");
node.parentNode.removeChild(node);
```

* replaceChild(newNode,oldNode):用新节点替换新节点，父节点调用该方法

```javascript
<div id="d"><p>默认的儿子</p></div>
 <div id="d2">同级关系</div>

 var node =  document.getElementById("d");
     var node2 =  document.getElementById("d2");
     node.parentNode.replaceChild(node2,node);
```

* hasChildNodes():判断一个节点是否有子节点（文本节点也包含在内），如果有返回true，没有返回false

```javascript
<ul id="d">
     <li>1</li>
     <li>2</li>
     <li>3</li>
 </ul>
 <button id="btn">删除</button>
 <script>
     //删除ul中所有的子节点
     //事件 onclick 点击事件
     var  btn = document.getElementById("btn");
     btn.onclick=function(){
         var node =  document.getElementById("d");
         while (node.hasChildNodes()){
             node.removeChild(node.firstChild);
         }
     }
 </script>
```

* insertBefore(insertNode,refrenceNode):把第一参数节点插入到第二个参数点，父节点调用该方法

```javascript
var text1 = document.createTextNode('1'); //创建文本节点
var li = document.createElement('li');
li.appendChild(text1);
var ul = document.getElementById('ul');
ul.insertBefore(li, ul.firstChild);
```

