### BOM

* 浏览器对象模型
* window对象是顶层对象
* window对象提供几种子对象
  * document
  * history
  * location
  * console
  * navigator
  * screen
* window对象自身属性
  * innerWidth/innerHeight:浏览器可用宽度/高度
  * name:获取浏览器窗口名称
  * screenX/screenY:浏览器窗口到屏幕的X距离/Y距离
* window对象自身方法
  * window.alert();
  * setInterval()/setTimeout()
  * window.confirm();//返回boolean
  * window.prompt();//返回的是输入的结果
  * window.open(url,name,option);//打开一个窗口
  * window.close();//关闭打开的窗口
  * setInterval(fn,毫秒数)；//每间隔多少毫秒，就会执行一次函数，返回的是一个定时器编号
  * setInterval(fn(x,y),毫秒数,x,y);//第三个参数开始，支持传递函数参数
  * clearnInterval(定时器编号)；//不用该定时器的时候一定要清除定时器
  * setTimeout(fn,毫秒数)；//延迟多少毫秒，只执行一次函数
  * clearnInterval（定时器编号）；//可以不用清除
* 全局的变量，函数都是属性window对象身上的

```javascript
var a=1;
window.a===a //true

function f();
window.f===f;//true

```

* screen对象:判断设备尺寸
  * screen.width//获取设备的分辨率宽度
  * screen.heigth//获取设备的分辨率高度
  * screen.availwidth//获取设备可用的宽度
  * screen.availheigth//获取设备可用的高度，会减去任务栏
* history对象：浏览器历史对象
  * foward();//前进上一个页面
  * back();//回退上一个页面
  * go(-1);//返回上一个页面
* location对象：获取操作浏览器地址栏信息
  * location.href:获取浏览器地址
  * location.search:获取浏览器地址的参数
  * location.hash:获取浏览器地址的锚点值
* navigator对象:获取浏览器自身信息
  * navigator.user

Cookie

* 是客户端存储信息一种方法4KB，一个站点20个，一个浏览器300个左右，不同浏览器不能交叉使用
* 用途1：记住登录|加入购物车
* 用途2：聊天主题设置|皮肤设置|本地历史排行榜数据
* 用途3：个性推荐
* 缺点：不安全，用来存储不重要数据|启用需要浏览器启用
* document.cookie:获取cookie,返回一个字符串

```javascript
//取cookie：
document.cookie
```

* 添加cookie:默认的生命周期是浏览器从打开到关闭整个期间

```javascript
document.cookie="name1=lero";
document.cookie="name2=lily";
document.cookie="name3=lucy";

//等价于
document.cookie="name1=lero; name2=lily; name3=lucy";

```

* 设置cookie存在时间Max-age,单位是秒

```javascript
document.cookie="name1=lero; Max-age=10";//设置一个cookie 存在时间为10秒
```

* 删除cookie

```javascript
document.cookie="name1=lero; Max-age=0";//删除cookie
```

* cookie存中文记得编码

```javascript
var res =  encodeURI("你好"); //编码
console.log(res);

res  = decodeURI(res); //解码
console.log(res);

```
