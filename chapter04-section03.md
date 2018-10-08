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

Element节点方法：

* 获取指定的元素方法同Document，除了getElementById()方法没有

  * element.getElementByName();
  * element.getElementByTagName();
  * element.getElementByClassName();
  * element.querySelector();
  * element.querySelectorAll();
* 提供了一组操作属性的方法(CRUD)

  * element.setAttributeNode(attrNode);//给元素添加属性节点
  * element.removeAttributeNode(attrNode);//删除元素某个属性节点
  * element.setAttribute("key","value");//给元素节点添加属性
  * element.setAttribute("key","value1");//给元素节点修改属性
  * element.removeAttribute("key");//删除元素某个属性
  * element.getAttribute("key");//获取元素某个属性
  * element.hasAttribute("key");//判断元素是否有某个属性，若果有返回true
  * element.hasAttributes();//判断该元素上是否具有具有属性，至少有一个属性就返回true

Element操作表格

* table.insertRow(索引)；//创建一行
* tr.insertCell(索引)；//创建某一行的单元格
* table.deleteRow(索引)；//删除行
* tr.deleteCell(索引)；//删除某一行单元格
* 常用属性：
* table.tBodies;//获取到tbody的集合
* tbody.rows;//获取到tbody中的行的集合
* tr.cells;//虎丘tr中的列的集合

