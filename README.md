# 题目

#### Doctype作用？标准模式与兼容模式各有什么区别?

1. 
   `<!DOCTYPE>`声明位于HTML文档中的第一行，处于 `<html>` 标签之前。告知浏览器的解析器用什么文档标准解析这个文档。DOCTYPE不存在或格式不正确会导致文档以兼容模式呈现。

2. 标准模式的排版 和JS运作模式都是以该浏览器支持的最高标准运行。在兼容模式中，页面以宽松的向后兼容的方式显示,模拟老式浏览器的行为以防止站点无法工作。



#### HTML5 为什么只需要写 `<!DOCTYPE HTML>`？

1.    HTML5 不基于 SGML，因此不需要对DTD进行引用，但是需要doctype来规范浏览器的行为（让浏览器按照它们应该的方式来运行）；
2. 而HTML4.01基于SGML,所以需要对DTD进行引用，才能告知浏览器文档所使用的文档类型。

#### 行内元素有哪些？块级元素有哪些？ 空(void)元素有那些？

1. 行内元素有：`a b span img input select strong`（强调的语气）
2. 块级元素有：`div ul ol li dl dt dd h1 h2 h3 h4…p`
3. 常见的空元素：`<br><hr> <img> <input> <link> <meta>`
	鲜为人知的是：
	`<area> <base> <col> <command> <embed> <keygen> <param> <source> <track> <wbr>`

#### 页面导入样式时，使用link和@import有什么区别？

1. link属于XHTML标签，除了加载CSS外，还能用于定义RSS, 定义rel连接属性等作用；而@import是CSS提供的，只能用于加载CSS;
2. 页面被加载的时，link会同时被加载，而@import引用的CSS会等到页面被加载完再加载;
3. import是CSS2.1 提出的，只在IE5以上才能被识别，而link是XHTML标签，无兼容问题;
4. link支持使用js控制DOM去改变样式，而@import不支持;

#### 介绍一下你对浏览器内核的理解？

主要分成两部分：渲染引擎(layout engineer或Rendering Engine)和JS引擎。

1. 渲染引擎：负责取得网页的内容（HTML、XML、图像等等）、整理讯息（例如加入CSS等），以及计算网页的显示方式，然后会输出至显示器或打印机。浏览器的内核的不同对于网页的语法解释会有不1. 所以渲染的效果也不相同。所有网页浏览器、电子邮件客户端以及其它需要编辑、显示网络内容的应用程序都需要内核。
2. JS引擎则：解析和执行javascript来实现网页的动态效果。
最开始渲染引擎和JS引擎并没有区分的很明确，后来JS引擎越来越独立，内核就倾向于只指渲染引擎。


#### 常见的浏览器内核有哪些？

1. ​    Trident内核：IE,MaxThon,TT,The World,360,搜狗浏览器等。[又称MSHTML]
2. ​    Gecko内核：Netscape6及以上版本，FF,MozillaSuite/SeaMonkey等
3. ​    Presto内核：Opera7及以上。      [Opera内核原为：Presto，现为：Blink;]
4. ​    Webkit内核：Safari,Chrome等。   [ Chrome的：Blink（WebKit的分支）]

#### html5有哪些新特性、移除了那些元素？如何处理HTML5新标签的浏览器兼容问题？如何区分 HTML 和 HTML5？

HTML5 现在已经不是 SGML 的子集，主要是关于图像，位置，存储，多任务等功能的增加。
+ 绘画 canvas;
+ 用于媒介回放的 video 和 audio 元素;
+ 本地离线存储 localStorage 长期存储数据，浏览器关闭后数据不丢失;
+ sessionStorage 的数据在浏览器关闭后自动删除;
+ 语意化更好的内容元素，比如 article、footer、header、nav、section;
+ 表单控件，calendar、date、time、email、url、search;
+ 新的技术webworker, websocket, Geolocation;
  ​+ 移除的元素：
+ 纯表现的元素：basefont，big，center，font, s，strike，tt，u;
+ 对可用性产生负面影响的元素：frame，frameset，noframes；
+ 支持HTML5新标签：
    IE8/IE7/IE6支持通过document.createElement方法产生的标签，可以利用这一特性让这些浏览器支持HTML5新标签，浏览器支持新标签后，还需要添加标签默认的样式。当然也可以直接使用成熟的框架、比如html5shim;
    ```
    	 <!--[if lt IE 9]>
    		<script> src="http://html5shim.googlecode.com/svn/trunk/html5.js"</script>
    	 <![endif]-->
    ```


#### 简述一下你对HTML语义化的理解？

- 用正确的标签做正确的事情。
- ​html语义化让页面的内容结构化，结构更清晰，便于对浏览器、搜索引擎解析;
- ​即使在没有样式CSS情况下也以一种文档格式显示，并且是容易阅读的;
- ​搜索引擎的爬虫也依赖于HTML标记来确定上下文和各个关键字的权重，利于SEO;
- ​使阅读源代码的人对网站更容易将网站分块，便于阅读维护理解。

#### HTML5的离线储存怎么使用，工作原理能不能解释一下？

​在用户没有与因特网连接时，可以正常访问站点或应用，在用户与因特网连接时，更新用户机器上的缓存文件。

原理：HTML5的离线存储是基于一个新建的.appcache文件的缓存机制(不是存储技术)，通过这个文件上的解析清单离线存储资源，这些资源就会像cookie一样被存储了下来。之后当网络在处于离线状态下时，浏览器会通过被离线存储的数据进行页面展示。
​如何使用：
1. 页面头部像下面一样加入一个manifest的属性；
​2. 在cache.manifest文件的编写离线存储的资源；
​    CACHE MANIFEST
​    CACHE:
    js/app.js
    css/style.css
    NETWORK:
    resourse/logo.png
    FALLBACK:
    offline.html
3. 在离线状态时，操作window.applicationCache进行需求实现。

#### 浏览器是怎么对HTML5的离线储存资源进行管理和加载的呢？

1. 在线的情况下，浏览器发现html头部有manifest属性，它会请求manifest文件，如果是第一次访问app，那么浏览器就会根据manifest文件的内容下载相应的资源并且进行离线存储。如果已经访问过app并且资源已经离线存储了，那么浏览器就会使用离线的资源加载页面，然后浏览器会对比新的manifest文件与旧的manifest文件，如果文件没有发生改变，就不做任何操作，如果文件改变了，那么就会重新下载文件中的资源并进行离线存储。

2. 离线的情况下，浏览器就直接使用离线存储的资源。


  详细请参考：[有趣的HTML5：离线存储](http://segmentfault.com/a/1190000000732617)

#### 请描述一下 cookies，sessionStorage 和 localStorage 的区别？

- cookie是网站为了标示用户身份而储存在用户本地终端（Client Side）上的数据（通常经过加密）。

- cookie数据始终在同源的http请求中携带（即使不需要），记会在浏览器和服务器间来回传递。
- sessionStorage和localStorage不会自动把数据发给服务器，仅在本地保存。

​存储大小：

- cookie数据大小不能超过4k。

- sessionStorage和localStorage 虽然也有存储大小的限制，但比cookie大得多，可以达到5M或更大。

​有期时间：

- localStorage    存储持久数据，浏览器关闭后数据不丢失除非主动删除数据；

- sessionStorage  数据在当前浏览器窗口关闭后自动删除。
- cookie          设置的cookie过期时间之前一直有效，即使窗口或浏览器关闭

#### iframe有那些缺点？

* iframe会阻塞主页面的Onload事件；
* 搜索引擎的检索程序无法解读这种页面，不利于SEO; 
* iframe和主页面共享连接池，而浏览器对相同域的连接有限制，所以会影响页面的并行加载。
  
使用iframe之前需要考虑这两个缺点。如果需要使用iframe，最好是通过javascript
动态给iframe添加src属性值，这样可以绕开以上两个问题。


#### Label的作用是什么？是怎么用的？


+ label标签来定义表单控制间的关系,当用户选择该标签时，浏览器会自动将焦点转到和标签相关的表单控件上。
+ `<label for="Name">Number:</label>`
+ `<input type=“text“name="Name" id="Name"/>`
+ `<label>Date:<input type="text" name="B"/></label>`


#### HTML5的form如何关闭自动完成功能？

给不想要提示的 form 或某个 input 设置为 autocomplete=off。

#### 如何实现浏览器内多个标签页之间的通信? (阿里)

+ WebSocket、SharedWorker；
+ 也可以调用localstorge、cookies等本地存储方式；
+ localstorge另一个浏览上下文里被添加、修改或删除时，它都会触发一个事件，
我们通过监听事件，控制它的值来进行页面信息通信；
注意quirks：Safari 在无痕模式下设置localstorge值时会抛出 QuotaExceededError 的异常；

#### webSocket如何兼容低浏览器？(阿里)

+ Adobe Flash Socket 、
+ ActiveX HTMLFile (IE) 、
+ 基于 multipart 编码发送 XHR 、
+ 基于长轮询的 XHR

#### 页面可见性（Page Visibility API） 可以有哪些用途？

+ 通过 visibilityState 的值检测页面当前是否可见，以及打开网页的时间等;
+ 在页面被切换到其他后台进程的时候，自动暂停音乐或视频的播放；

#### 如何在页面上实现一个圆形的可点击区域？

+ 1、map+area或者svg
+ 2、border-radius
+ 3、纯js实现 需要求一个点在不在圆上简单算法、获取鼠标坐标等等

#### 实现不使用 border 画出1px高的线，在不同浏览器的标准模式与怪异模式下都能保持一致的效果。

`<div style="height:1px;overflow:hidden;background:red"></div>`

#### 网页验证码是干嘛的，是为了解决什么安全问题。

+ 区分用户是计算机还是人的公共全自动程序。可以防止恶意破解密码、刷票、论坛灌水；
+ 有效防止黑客对某一个特定注册用户用特定程序暴力破解方式进行不断的登陆尝试。

#### title与h1的区别、b与strong的区别、i与em的区别？

+ title属性没有明确意义只表示是个标题，H1则表示层次明确的标题，对页面信息的抓取也有很大的影响；
+ strong是标明重点内容，有语气加强的含义，使用阅读设备阅读网络时：`<strong>`会重读，而`<B>`是展示强调内容。
+ i内容展示为斜体，em表示强调的文本；
+ Physical Style Elements -- 自然样式标签
+ b, i, u, s, pre
+ Semantic Style Elements -- 语义样式标签
+ strong, em, ins, del, code
+ 应该准确使用语义样式标签, 但不能滥用, 如果不能确定时首选使用自然样式标签。

#### 介绍一下标准的CSS的盒子模型？低版本IE的盒子模型有什么不同的？

+ 有两种， IE 盒子模型、W3C 盒子模型；
+ 盒模型： 内容(content)、填充(padding)、边界(margin)、 边框(border)；
+ 区  别： IE的content部分把 border 和 padding计算了进去;

#### CSS选择符有哪些？哪些属性可以继承？

1. id选择器（ # myid）
2. 类选择器（.myclassname）
3. 标签选择器（div, h1, p）
4. 相邻选择器（h1 + p）
5. 子选择器（ul > li）
6. 后代选择器（li a）
7. 通配符选择器（ * ）
8. 属性选择器（a[rel = "external"]）
9. 伪类选择器（a:hover, li:nth-child）
+ 可继 承的样式： font-size font-family color, UL LI DL DD DT;
+ 不可 继承的样式：border padding margin width height ;

#### CSS优先级算法如何计算？

- 优先级就近原则，同权重情况下样式定义最近者为准;

- 载入样式以最后载入的定位为准;

- 优先级为:
同权重: 内联样式表（标签内部）> 嵌入样式表（当前文件中）> 外部样式表（外部文件中）。
!important >  id > class > tag
important 比 内联优先级高


#### CSS3新增伪类有那些？

+ p:first-of-type	选择属于其父元素的首个 `<p>` 元素的每个 `<p>` 元素。
	 p:last-of-type	选择属于其父元素的最后 `<p>` 元素的每个 `<p>` 元素。
	 p:only-of-type	选择属于其父元素唯一的 `<p>` 元素的每个 `<p>` 元素。
	 p:only-child		选择属于其父元素的唯一子元素的每个 `<p>` 元素。
	 p:nth-child(2)	选择属于其父元素的第二个子元素的每个 `<p>` 元素。
	 ::after			在元素之前添加内容,也可以用来做清除浮动。
	 ::before			在元素之后添加内容
	 :enabled  		
	 :disabled 		控制表单控件的禁用状态。
+ :checked        单选框或复选框被选中。

#### 如何居中div？
  水平居中 1

```
  div {
 	width:200px;
 	margin:0 auto;
    }    
```

  水平居中2

```
   div {
 	position: absolute;
 	width: 300px;
 	height: 300px;
 	margin: auto;
 	top: 0;
 	left: 0;
 	bottom: 0;
 	right: 0;
 	background-color: pink;	/* 方便看效果 */
 }
```

 水平垂直居中1

```
  div {
 	position: relative;		/* 相对定位或绝对定位均可 */
 	width:500px;
 	height:300px;
 	top: 50%;
 	left: 50%;
 	margin: -150px 0 0 -250px;     	/* 外边距为自身宽高的一半 */
 	background-color: pink;	 	/* 方便看效果 */

  }
```

  水平垂直居中2

```
   div {
 	position: absolute;		/* 相对定位或绝对定位均可 */
 	width:500px;
 	height:300px;
 	top: 50%;
 	left: 50%;
 	transform: translate(-50%, -50%);
 	background-color: pink;	 	/* 方便看效果 */

 }
```

 水平垂直居中三

```
  .container {
 	display: flex;
 	align-items: center; 		/* 垂直居中 */
 	justify-content: center;	/* 水平居中 */

 }
 .container div {
 	width: 100px;
 	height: 100px;
 	background-color: pink;		/* 方便看效果 */
 }
```
#### display有哪些值？说明他们的作用。

+ block       	块类型。默认宽度为父元素宽度，可设置宽高，换行显示。
	 none        	元素不显示，并从文档流中移除。
	 inline      	行内元素类型。默认宽度为内容宽度，不可设置宽高，同行显示。
+ inline-block  默认宽度为内容宽度，可以设置宽高，同行显示。
	 list-item   	象块类型元素一样显示，并添加样式列表标记。
	 table       	此元素会作为块级表格来显示。
	 inherit     	规定应该从父元素继承 display 属性的值。

#### position的值relative和absolute定位原点是？

+ absolute
生成绝对定位的元素，相对于值不为 static的第一个父元素进行定位。
+ fixed （老IE不支持）
生成绝对定位的元素，相对于浏览器窗口进行定位。
+ relative
生成相对定位的元素，相对于其正常位置进行定位。
+ static
默认值。没有定位，元素出现在正常的流中（忽略 top, bottom, left, right z-index 声明）。
+ inherit
规定从父元素继承 position 属性的值。


#### CSS3有哪些新特性？

+ 新增各种CSS选择器	（: not(.input)：所有 class 不是“input”的节点）
	 圆角		    （border-radius:8px）
	 多列布局	    （multi-column layout）
	 阴影和反射	（Shadow\Reflect）
	 文字特效		（text-shadow、）
	 文字渲染		（Text-decoration）
	 线性渐变		（gradient）
	 旋转		 	（transform）
+ 缩放,定位,倾斜,动画,多背景


#### 请解释一下CSS3的Flexbox（弹性盒布局模型）,以及适用场景

一个用于页面布局的全新CSS3功能，Flexbox可以把列表放在同一个方向（从上到下排列，从左到右），并让列表能延伸到占用可用的空间。

#### 用纯CSS创建一个三角形的原理是什么？

  把上、左、右三条边隐藏掉（颜色设为 transparent）
```
  #demo {
    width: 0;
    height: 0;
    border-width: 20px;
    border-style: solid;
    border-color: transparent transparent red transparent;
  }
```

#### 一个满屏 品 字布局 如何设计?

简单的方式：
  上面的div宽100%，
  下面的两个div分别宽50%，
  然后用float或者inline使其不换行即可

#### css多列等高如何实现？


+ 利用padding-bottom|margin-bottom正负值相抵；
+ 设置父容器设置超出隐藏（overflow:hidden），这样子父容器的高度就还是它里面的列没有设定padding-bottom时的高度，
+ 当它里面的任 一列高度增加了，则父容器的高度被撑到里面最高那列的高度，
+ 其他比这列矮的列会用它们的padding-bottom补偿这部分高度差。


#### 对BFC规范(块级格式化上下文：block formatting context)的理解

+ W3C CSS 2.1 规范中的一个概念,它是一个独立容器，决定了元素如何对其内容进行定位,以及与其他元素的关系和相互作用。
+ 一个页面是由很多个 Box 组成的,元素的类型和 display 属性,决定了这个 Box 的类型。
+ 不同类型的 Box,会参与不同的 Formatting Context（决定如何渲染文档的容器）,因此Box内的元素会以不同的方式渲染,也就是说BFC内部的元素和外部的元素不会互相影响。

#### css定义的权重

  以下是权重的规则：标签的权重为1，class的权重为10，id的权重为100，以下例子是演示各种定义的权重值：
  如果权重相同，则最后定义的样式会起作用，但是应该避免这种情况出现
```
  /*权重为1*/
  div{
  }
  /*权重为10*/
  .class1{
  }
  /*权重为100*/
  #id1{
  }
  /*权重为100+1=101*/
  #id1 div{
  }
  /*权重为10+1=11*/
  .class1 div{
  }
  /*权重为10+10+1=21*/
  .class1 .class2 div{
  }
```

#### 请解释一下为什么需要清除浮动？清除浮动的方式

清除浮动是为了清除使用浮动元素产生的影响。浮动的元素，高度会塌陷，而高度的塌陷使我们页面后面的布局不能正常显示

#### 什么是外边距合并？

外边距合并指的是，当两个垂直外边距相遇时，它们将形成一个外边距。
合并后的外边距的高度等于两个发生合并的外边距的高度中的较大者。

#### zoom:1的清除浮动原理

+ 清除浮动，触发hasLayout；
+ Zoom属性是IE浏览器的专有属性，它可以设置或检索对象的缩放比例。解决ie下比较奇葩的bug。
+ 譬如外边距（margin）的重叠，浮动清除，触发ie的haslayout属性等。
+ 当设置了zoom的值之后，所设置的元素就会就会扩大或者缩小，高度宽度就会重新计算了，这里一旦改变zoom值时其实也会发生重新渲染，运用这个原理，也就解决了ie下子元素浮动时候父元素不随着自动扩大的问题。
+ Zoom属是IE浏览器的专有属性，火狐和老版本的webkit核心的浏览器都不支持这个属性。然而，zoom现在已经被逐步标准化，出现在 CSS 3.0 规范草案中。
+ 目前非ie由于不支持这个属性，它们又是通过什么属性来实现元素的缩放呢？
+ 可以通过css3里面的动画属性scale进行缩放。

#### ::before 和 :after中双冒号和单冒号 有什么区别？解释一下这2个伪元素的作用

+ 单冒号(:)用于CSS3伪类，双冒号(::)用于CSS3伪元素。（伪元素由双冒号和伪元素名称组成）
+ 双冒号是在当前规范中引入的，用于区分伪类和伪元素。不过浏览器需要同时支持旧的已经存在的伪元素写法， 比如:first-line、:first-letter、:before、:after等，
+ 而新的在CSS3中引入的伪元素则不允许再支持旧的单冒号的写法。
+ 想让插入的内容出现在其它内容前，使用::before，否者，使用::after；
+ 在代码顺序上，::after生成的内容也比::before生成的内容靠后。
+ 如果按堆栈视角，::after生成的内容会在::before生成的内容之上

#### 如何修改chrome记住密码后自动填充表单的黄色背景 ？

```
  input:-webkit-autofill, textarea:-webkit-autofill, select:-webkit-autofill {
    background-color: rgb(250, 255, 189); /* #FAFFBD; */
    background-image: none;
    color: rgb(0, 0, 0);
  }
```

#### 让页面里的字体变清晰，变细用CSS怎么做？

```
-webkit-font-smoothing: antialiased;
```

#### 介绍js的基本数据类型

```
 Undefined、Null、Boolean、Number、String、Object ECMAScript 2015 新增:Symbol
```



#### JavaScript原型，原型链 ? 有什么特点？
 + 每个对象都会在其内部初始化一个属性，就是prototype(原型)，当我们访问一个对象的属性时，如果这个对象内部不存在这个属性，那么他就会去prototype里找这个属性，这个prototype又会有自己的prototype.于是就这样一直找下去，也就是我们平时所说的原型链的概念。
 + 关系：`instance.constructor.prototype = instance.__proto__`
+ 特点：
JavaScript对象是通过引用来传递的，我们创建的每个新对象实体中并没有一份属于自己的原型副本。当我们修改原型时，与之相关的对象也会继承这一改变

#### 如何实现数组的随机排序？

```
  方法一：
  	var arr = [1,2,3,4,5,6,7,8,9,10];
  	function randSort1(arr){
  		for(var i = 0,len = arr.length;i < len; i++ ){
  			var rand = parseInt(Math.random()*len);
  			var temp = arr[rand];
  			arr[rand] = arr[i];
  			arr[i] = temp;
  		}
  		return arr;
  	}
  	console.log(randSort1(arr));
  	
  方法二：
  	var arr = [1,2,3,4,5,6,7,8,9,10];
  	function randSort2(arr){
  		var mixedArray = [];
  		while(arr.length > 0){
  			var randomIndex = parseInt(Math.random()*arr.length);
  			mixedArray.push(arr[randomIndex]);
  			arr.splice(randomIndex, 1);
  		}
  		return mixedArray;
  	}
  	console.log(randSort2(arr));

  方法三：
  	var arr = [1,2,3,4,5,6,7,8,9,10];
  	arr.sort(function(){
  		return Math.random() - 0.5;
  	})
  	console.log(arr);
```

#### Javascript如何实现继承？

1、构造继承
2、原型继承
3、实例继承
4、拷贝继承

#### javascript创建对象的几种方式？

javascript创建对象简单的说,无非就是使用内置对象或各种自定义对象，当然还可以用JSON；但写法有很多种，也能混合使用。

 1、对象字面量的方式

 `person={firstname:"Mark",lastname:"Yun",age:25,eyecolor:"black"}`

 2、用`function`来模拟无参的构造函数
```
 	function Person(){}
 	var person=new Person();//定义一个function，如果使用new"实例化",该function可以看作是一个Class
 	person.name="Mark";
 	person.age="25";
 	person.work=function(){
 	alert(person.name+" hello...");
 	}
 	person.work();
```
 3、用`function`来模拟参构造函数来实现（用this关键字定义构造的上下文属性）
```
 	function Pet(name,age,hobby){
 	   this.name=name;//this作用域：当前对象
 	   this.age=age;
 	   this.hobby=hobby;
 	   this.eat=function(){
 	      alert("我叫"+this.name+",我喜欢"+this.hobby+",是个程序员");
 	   }
 	}
 	var maidou =new Pet("麦兜",25,"coding");//实例化、创建对象
 	maidou.eat();//调用eat方法
```

 4、用工厂方式来创建（内置对象）

```
 	 var wcDog =new Object();
 	 wcDog.name="旺财";
 	 wcDog.age=3;
 	 wcDog.work=function(){
 	   alert("我是"+wcDog.name+",汪汪汪......");
 	 }
 	 wcDog.work();
```


 5、用原型方式来创建

```
 	function Dog(){

 	 }
 	 Dog.prototype.name="旺财";
 	 Dog.prototype.eat=function(){
 	 alert(this.name+"是个吃货");
 	 }
 	 var wangcai =new Dog();
 	 wangcai.eat();
```


 6、用混合方式来创建

```
 	function Car(name,price){
 	  this.name=name;
 	  this.price=price;
 	}
 	 Car.prototype.sell=function(){
 	   alert("我是"+this.name+"，我现在卖"+this.price+"万元");
 	  }
 	var camry =new Car("凯美瑞",27);
 	camry.sell();
```

#### 谈谈This对象的理解。

this总是指向函数的直接调用者（而非间接调用者）；
如果有new关键字，this指向new出来的那个对象；
在事件中，this指向触发这个事件的对象，特殊的是，IE中的attachEvent中的this总是指向全局对象Window；

eval是做什么的？

-  它的功能是把对应的字符串解析成JS代码并运行；
-  应该避免使用eval，不安全，非常耗性能（2次，一次解析成js语句，一次执行）。
-  由JSON字符串转换为JSON对象的时候可以用eval，var obj =eval('('+ str +')');



#### null，undefined 的区别？

```
 null 		表示一个对象是“没有值”的值，也就是值为“空”；
 undefined 	表示一个变量声明了没有初始化(赋值)；

 undefined不是一个有效的JSON，而null是；
 undefined的类型(typeof)是undefined；
 null的类型(typeof)是object；


 Javascript将未赋值的变量默认值设为undefined；
 Javascript从来不会将变量设为null。它是用来让程序员表明某个用var声明的变量时没有值的。

 typeof undefined
 	//"undefined"
 	undefined :是一个表示"无"的原始值或者说表示"缺少值"，就是此处应该有一个值，但是还没有定义。当尝试读取时会返回 undefined；
 	例如变量被声明了，但没有赋值时，就等于undefined

 typeof null
 	//"object"
 	null : 是一个对象(空对象, 没有任何属性和方法)；
 	例如作为函数的参数，表示该函数的参数不是对象；

 注意：
 	在验证null时，一定要使用　=== ，因为 == 无法分别 null 和　undefined
 	null == undefined // true
 	null === undefined // false

 再来一个例子：

 	null
 	Q：有张三这个人么？
 	A：有！
 	Q：张三有房子么？
 	A：没有！

 	undefined
 	Q：有张三这个人么？
 	A：有！
 	Q: 张三有多少岁？
 	A: 不知道（没有被告诉）
```

#### 什么是闭包（closure），为什么要用它？

 闭包是指有权访问另一个函数作用域中变量的函数，创建闭包的最常见的方式就是在一个函数内创建另一个函数，通过另一个函数访问这个函数的局部变量,利用闭包可以突破作用链域，将函数内部的变量和方法传递到外部。

 闭包的特性：

 1.函数内再嵌套函数
 2.内部函数可以引用外层的参数和变量
 3.参数和变量不会被垃圾回收机制回收

#### javascript 代码中的"use strict";是什么意思 ? 使用它区别是什么？

-  use strict是一种ECMAscript 5 添加的（严格）运行模式,这种模式使得 Javascript 在更严格的条件下运行,
-  使JS编码更加规范化的模式,消除Javascript语法的一些不合理、不严谨之处，减少一些怪异行为。默认支持的糟糕特性都会被禁用，比如不能用with，也不能在意外的情况下给全局变量赋值;全局变量的显示声明,函数必须声明在顶层，不允许在非函数代码块内声明函数,arguments.callee也不允许使用；
-  消除代码运行的一些不安全之处，保证代码运行的安全,限制函数中的arguments修改，严格模式下的eval函数的行为和非严格模式的也不相同;
-  提高编译器效率，增加运行速度；
   为未来新版本的Javascript标准化做铺垫。

#### Ajax 是什么? 如何创建一个Ajax？

ajax的全称：Asynchronous Javascript And XML。异步传输+js+xml。
所谓异步，在这里简单地解释就是：向服务器发送请求的时候，我们不必等待结果，而是可以同时做其他的事情，等到有了结果它自己会根据设定进行后续操作，与此同时，页面是不会发生整页刷新的，提高了用户体验。

+ 创建XMLHttpRequest对象,也就是创建一个异步调用对象
+ 创建一个新的HTTP请求,并指定该HTTP请求的方法、URL及验证信息
+ 设置响应HTTP请求状态变化的函数
+ 发送HTTP请求
+ 获取异步调用返回的数据
+ 使用JavaScript和DOM实现局部刷新

#### Ajax 解决浏览器缓存问题？

+ 在ajax发送请求前加上 anyAjaxObj.setRequestHeader("If-Modified-Since","0")。
+ 在ajax发送请求前加上 anyAjaxObj.setRequestHeader("Cache-Control","no-cache")。
+ 在URL后面加上一个随机数： "fresh=" + Math.random();
+ 在URL后面加上时间戳："nowtime=" + new Date().getTime();。
+ 如果是使用jQuery，直接这样就可以了 $.ajaxSetup({cache:false})。

#### 同步和异步的区别?

+ 同步的概念应该是来自于OS中关于同步的概念:不同进程为协同完成某项工作而在先后次序上调整(通过阻塞,唤醒等方式).同步强调的是顺序性.谁先谁后.异步则不存在这种顺序性.
+ 同步：浏览器访问服务器请求，用户看得到页面刷新，重新发请求,等请求完，页面刷新，新内容出现，用户看到新内容,进行下一步操作。
+ 异步：浏览器访问服务器请求，用户正常操作，浏览器后端进行请求。等请求完，页面不刷新，新内容也会出现，用户看到新内容。

#### 如何解决跨域问题?

jsonp、 iframe、window.name、window.postMessage、服务器上设置代理页面

#### DOM操作——怎样添加、移除、移动、复制、创建和查找节点?

+ 创建新节点
createDocumentFragment()    //创建一个DOM片段
createElement()   //创建一个具体的元素
createTextNode()   //创建一个文本节点
+ 添加、移除、替换、插入
appendChild()
removeChild()
replaceChild()
insertBefore() //在已有的子节点前插入一个新的子节点
+ 查找
getElementsByTagName()    //通过标签名称
getElementsByName()    //通过元素的Name属性的值(IE容错能力较强，会得到一个数组，其中包括id等于name值的)
getElementById()    //通过元素Id，唯一性

#### jquery.extend 与 jquery.fn.extend的区别？

+ jquery.extend 为jquery类添加类方法，可以理解为添加静态方法
+ jquery.fn.extend:
  - 源码中j`query.fn = jquery.prototype`，所以对`jquery.fn`的扩展，就是为`jquery`类添加成员函数
  - jquery.extend扩展，需要通过jquery类来调用，而jquery.fn.extend扩展，所有jquery实例都可以直接调用。

#### 如何判断当前脚本运行在浏览器还是node环境中？（阿里）

通过判断Global对象是否为window，如果不为window，当前脚本没有运行在浏览器中
  `this === window ? 'browser' : 'node';`

#### What is a Polyfill?

+ polyfill 是“在旧版浏览器上复制标准 API 的 JavaScript 补充”,可以动态地加载 JavaScript 代码或库，在不支持这些标准 API 的浏览器中模拟它们。
+ 例如，geolocation（地理位置）polyfill 可以在 navigator 对象上添加全局的 geolocation 对象，还能添加 getCurrentPosition 函数以及“坐标”回调对象，
+ 所有这些都是 W3C 地理位置 API 定义的对象和函数。因为 polyfill 模拟标准 API，所以能够以一种面向所有浏览器未来的方式针对这些 API 进行开发，
+ 一旦对这些 API 的支持变成绝对大多数，则可以方便地去掉 polyfill，无需做任何额外工作。

#### React 使用场景？

逻辑复杂单页应用，偏中后台管理系统，纯展示性的UI页面不合适、

#### 描述一下React 生命周期
+ 渲染过程调用到的生命周期函数，主要几个要知道；
  - constructor
  - getInitialState
  - getDefaultProps
  - componentWillMount
  - render
  - componentDidMount
+ 更新过程
  - componentWillReceiveProps 
  - shouldComponentUpdate 
  - componentWillUpdate 
  - render 
  - componentDidUpdate 

+ 卸载过程
  - componentWillUnmount

#### 实现组件有哪些方式？

+ React.createClass 使用API来定义组件
+ React ES6 class component 用 ES6 的class 来定义组件
+ Functional stateless component 通过函数定义无状态组件

#### 应该在React生命周期的什么阶段发出ajax请求，为什么？

AJAX请求应在 componentDidMount函数 进行请求。

#### shouldComponentUpdate函数有什么作用？

+ `shouldComponentUpdate` 是一个允许我们自行决定某些组件（以及他们的子组件）是否进行更新的生命周期函数，reconciliation的最终目的是尽可能以最有效的方式去根据新的state更新UI，
+ 如果你已经知道UI的哪些状态无需进行改变，就没必要去让React去判断它是否该改变。 让shouldComponentUpdate返回falss, React就会让当前的组件和其子组件保持不变。

#### 当组件的setState函数被调用之后，发生了什么？

+ React会做的第一件事就是把你传递给setState的参数对象合并到组件原先的state。这个事件会导致一个“reconciliation”（调和）的过程。reconciliation的最终目标就是，尽可能以最高效的方法，去基于新的state来更新UI。为了达到这个目的，React会构建一个React元素树（你可以把这个想象成一个表示UI的一个对象）。一旦这个树构建完毕，React为了根据新的state去决定UI要怎么进行改变，它会找出这棵新树和旧树的不同之处。React能够相对精确地找出哪些位置发生了改变以及如何发生了什么变化，并且知道如何只通过必要的更新来最小化重渲染。

#### 为什么循环产生的组件中要利用上key这个特殊的prop？

Keys负责帮助React跟踪列表中哪些元素被改变/添加/移除。React利用子元素的key在比较两棵树的时候，快速得知一个元素是新的还是刚刚被移除。没有keys，React也就不知道当前哪一个的item被移除了。

#### 页面重构怎么操作？
+ 网站重构：在不改变外部行为的前提下，简化结构、添加可读性，而在网站前端保持一致的行为。也就是说是在不改变UI的情况下，对网站进行优化，在扩展的同时保持一致的UI。
+ 对于传统的网站来说重构通常是：
  - 表格(table)布局改为DIV+CSS
  - 使网站前端兼容于现代浏览器(针对于不合规范的CSS、如对IE6有效的)
  - 对于移动平台的优化
  - 针对于SEO进行优化
  - 深层次的网站重构应该考虑的方面
  - 减少代码间的耦合
  - 让代码保持弹性
  - 严格按规范编写代码
  - 设计可扩展的API
  - 代替旧有的框架、语言(如VB)
  - 增强用户体验
  - 通常来说对于速度的优化也包含在重构中
  - 压缩JS、CSS、image等前端资源(通常是由服务器来解决)
  - 程序的性能优化(如数据读写)
  - 采用CDN来加速资源加载
  - 对于JS DOM的优化
  - HTTP服务器的文件缓存

#### 什么叫优雅降级和渐进增强？

+ 优雅降级：Web站点在所有新式浏览器中都能正常工作，如果用户使用的是老式浏览器，则代码会针对旧版本的IE进行降级处理了,使之在旧式浏览器上以某种形式降级体验却不至于完全不能用。如：border-shadow
+ 渐进增强：从被所有浏览器支持的基本功能开始，逐步地添加那些只有新版本浏览器才支持的功能,向页面增加不影响基础浏览器的额外样式和功能的。当浏览器支持时，它们会自动地呈现出来并发挥作用如：默认使用flash上传，但如果浏览器支持 HTML5 的文件上传功能，则使用HTML5实现更好的体验；

#### 是否了解公钥加密和私钥加密。

+ 一般情况下是指私钥用于对数据进行签名，公钥用于对签名进行验证;
+ HTTP网站在浏览器端用公钥加密敏感数据，然后在服务器端再用私钥解密。

#### WEB应用从服务器主动推送Data到客户端有那些方式？

+ html5提供的Websocket
+ 不可见的iframe
+ WebSocket通过Flash
+ XHR长时间连接
+ XHR Multipart Streaming
+ `script`标签的长时间连接(可跨域)

#### 你有用过哪些前端性能优化的方法？

+ 减少http请求次数：CSS Sprites, JS、CSS源码压缩、图片大小控制合适；网页Gzip，CDN托管，data缓存 ，图片服务器。
+ 前端模板 JS+数据，减少由于HTML标签导致的带宽浪费，前端用变量保存AJAX请求结果，每次操作本地变量，不用请求，减少请求次数
+ 用innerHTML代替DOM操作，减少DOM操作次数，优化javascript性能。
+ 当需要设置的样式很多时设置className而不是直接操作style。
+ 少用全局变量、缓存DOM节点查找的结果。减少IO读取操作。
+ 避免使用CSS Expression（css表达式)又称Dynamic properties(动态属性)。
+ 图片预加载，将样式表放在顶部，将脚本放在底部  加上时间戳。
+ 避免在页面的主体布局中使用table，table要等其中的内容完全下载之后才会显示出来，显示比div+css布局慢。
对普通的网站有一个统一的思路，就是尽量向前端优化、减少数据库操作、减少磁盘IO。向前端优化指的是，在不影响功能和体验的情况下，能在浏览器执行的不要在服务端执行，能在缓存服务器上直接返回的不要到应用服务器，程序能直接取得的结果不要到外部取得，本机内能取得的数据不要到远程取，内存能取到的不要到磁盘取，缓存中有的不要去数据库查询。减少数据库操作指减少更新次数、缓存结果减少查询次数、将数据库执行的操作尽可能的让你的程序完成（例如join查询），减少磁盘IO指尽量不使用文件系统作为缓存、减少读写文件次数等。程序优化永远要优化慢的部分，换语言是无法“优化”的。

#### http状态码有那些？分别代表是什么意思？

简单版
+ 100  Continue	继续，一般在发送post请求时，已发送了http header之后服务端将返回此信息，表示确认，之后发送具体参数信息
	 200  OK 		正常返回信息
	 201  Created  	请求成功并且服务器创建了新的资源
	 202  Accepted 	服务器已接受请求，但尚未处理
+ 301  Moved Permanently  请求的网页已永久移动到新位置。
	 302 Found  		临时性重定向。
	 303 See Other  	临时性重定向，且总是使用 GET 请求新的 URI。
+ 304  Not Modified 自从上次请求后，请求的网页未修改过。
+ 400 Bad Request  服务器无法理解请求的格式，客户端不应当尝试再次使用相同的内容发起请求。
+ 401 Unauthorized 请求未授权。
	 403 Forbidden  	禁止访问。
	 404 Not Found  	找不到如何与 URI 相匹配的资源。
+ 500 Internal Server Error  最常见的服务器端错误。
+ 503 Service Unavailable 服务器端暂时无法处理请求（可能是过载或维护）。

完整版
+ 1**(信息类)：表示接收到请求并且继续处理
+ 100——客户必须继续发出请求
+ 101——客户要求服务器根据请求转换HTTP协议版本
+ 2**(响应成功)：表示动作被成功接收、理解和接受
+ 200——表明该请求被成功地完成，所请求的资源发送回客户端
+ 201——提示知道新文件的URL
+ 202——接受和处理、但处理未完成
+ 203——返回信息不确定或不完整
+ 204——请求收到，但返回信息为空
+ 205——服务器完成了请求，用户代理必须复位当前已经浏览过的文件
+ 206——服务器已经完成了部分用户的GET请求
+ 3**(重定向类)：为了完成指定的动作，必须接受进一步处理
+ 300——请求的资源可在多处得到
+ 301——本网页被永久性转移到另一个URL
+ 302——请求的网页被转移到一个新的地址，但客户访问仍继续通过原始URL地址，重定向，新的URL会在response中的Location中返回，浏览器将会使用新的URL发出新的Request。
+ 303——建议客户访问其他URL或访问方式
+ 304——自从上次请求后，请求的网页未修改过，服务器返回此响应时，不会返回网页内容，代表上次的文档已经被缓存了，还可以继续使用
+ 305——请求的资源必须从服务器指定的地址得到
+ 306——前一版本HTTP中使用的代码，现行版本中不再使用
+ 307——申明请求的资源临时性删除
+ 4**(客户端错误类)：请求包含错误语法或不能正确执行
+ 400——客户端请求有语法错误，不能被服务器所理解
+ 401——请求未经授权，这个状态代码必须和WWW-Authenticate报头域一起使用
+ HTTP 401.1 - 未授权：登录失败
  - HTTP 401.2 - 未授权：服务器配置问题导致登录失败
  - HTTP 401.3 - ACL 禁止访问资源
  - HTTP 401.4 - 未授权：授权被筛选器拒绝
HTTP 401.5 - 未授权：ISAPI 或 CGI 授权失败
+ 402——保留有效ChargeTo头响应
+ 403——禁止访问，服务器收到请求，但是拒绝提供服务
+ HTTP 403.1 禁止访问：禁止可执行访问
  - HTTP 403.2 - 禁止访问：禁止读访问
  - HTTP 403.3 - 禁止访问：禁止写访问
  - HTTP 403.4 - 禁止访问：要求 SSL
  - HTTP 403.5 - 禁止访问：要求 SSL 128
  - HTTP 403.6 - 禁止访问：IP 地址被拒绝
  - HTTP 403.7 - 禁止访问：要求客户证书
  - HTTP 403.8 - 禁止访问：禁止站点访问
  - HTTP 403.9 - 禁止访问：连接的用户过多
  - HTTP 403.10 - 禁止访问：配置无效
  - HTTP 403.11 - 禁止访问：密码更改
  - HTTP 403.12 - 禁止访问：映射器拒绝访问
  - HTTP 403.13 - 禁止访问：客户证书已被吊销
  - HTTP 403.15 - 禁止访问：客户访问许可过多
  - HTTP 403.16 - 禁止访问：客户证书不可信或者无效
+ HTTP 403.17 - 禁止访问：客户证书已经到期或者尚未生效
+ 404——一个404错误表明可连接服务器，但服务器无法取得所请求的网页，请求资源不存在。eg：输入了错误的URL
+ 405——用户在Request-Line字段定义的方法不允许
+ 407——类似401，用户必须首先在代理服务器上得到授权
+ 406——根据用户发送的Accept拖，请求资源不可访问
+ 408——客户端没有在用户指定的饿时间内完成请求
+ 409——对当前资源状态，请求不能完成
+ 410——服务器上不再有此资源且无进一步的参考地址
+ 411——服务器拒绝用户定义的Content-Length属性请求
+ 412——一个或多个请求头字段在当前请求中错误
+ 413——请求的资源大于服务器允许的大小
+ 414——请求的资源URL长于服务器允许的长度
+ 415——请求资源不支持请求项目格式
+ 416——请求中包含Range请求头字段，在当前请求资源范围内没有range指示值，请求也不包含If-Range请求头字段
+ 417——服务器不满足请求Expect头字段指定的期望值，如果是代理服务器，可能是下一级服务器不能满足请求长。
+ 5**(服务端错误类)：服务器不能正确执行一个正确的请求
+ HTTP 500 - 服务器遇到错误，无法完成请求
  - HTTP 500.100 - 内部服务器错误 - ASP 错误
  - HTTP 500-11 服务器关闭
  - HTTP 500-12 应用程序重新启动
  - HTTP 500-13 - 服务器太忙
  - HTTP 500-14 - 应用程序无效
  - HTTP 500-15 - 不允许请求 global.asa
  - Error 501 - 未实现
+ HTTP 502 - 网关错误
+ HTTP 503：由于超载或停机维护，服务器目前无法使用，一段时间后可能恢复正常

#### 一个页面从输入 URL 到页面加载显示完成，这个过程中都发生了什么？（流程说的越详细越好）

+ 详细版：
  1. 浏览器会开启一个线程来处理这个请求，对 URL 分析判断如果是 http 协议就按照 Web 方式来处理;
  2. 调用浏览器内核中的对应方法，比如 WebView 中的 loadUrl 方法;
  3. 通过DNS解析获取网址的IP地址，设置 UA 等信息发出第二个GET请求;
  4. 进行HTTP协议会话，客户端发送报头(请求报头);
  5. 进入到web服务器上的 Web Server，如 Apache、Tomcat、Node.JS 等服务器;
  6. 进入部署好的后端应用，如 PHP、Java、JavaScript、Python 等，找到对应的请求处理;
  7. 处理结束回馈报头，此处如果浏览器访问过，缓存上有对应资源，会与服务器最后修改时间对比，一致则返回304;
  8. 浏览器开始下载html文档(响应报头，状态码200)，同时使用缓存;
  9. 文档树建立，根据标记请求所需指定MIME类型的文件（比如css、js）,同时设置了cookie;
  10、页面开始渲染DOM，JS根据DOM API操作DOM,执行事件绑定等，页面显示完成。
+ 简洁版：
  1. 浏览器根据请求的URL交给DNS域名解析，找到真实IP，向服务器发起请求；
  2. 服务器交给后台处理完成后返回数据，浏览器接收文件（HTML、JS、CSS、图象等）；
  3. 浏览器对加载到的资源（HTML、JS、CSS等）进行语法解析，建立相应的内部数据结构（如HTML的DOM）；
  4. 载入解析到的资源文件，渲染页面，完成。

#### 移动端（Android IOS）怎么做好用户体验?

+ 清晰的视觉纵线、
+ 信息的分组、极致的减法、
+ 利用选择代替输入、
+ 标签及文字的排布方式、
+ 依靠明文确认密码、
+ 合理的键盘利用、

 

#### 你做的页面在哪些流览器测试过?这些浏览器的内核分别是什么?

一般都会在主流浏览器中进行测试,包括 IE,Chrome,Safari,Firefox 和 Opera.

内核:

- IE: trident 内核(1997 年的 IE4 中首次被采用,沿用至今.腾讯,猎豹,360 等浏览器都是用了 IE 的内核)

- Firefox:gecko 内核 (开源内核,因为火狐用户最多,被称为火狐内核,是一个跨平台内核,windows,linux 和mac os 中可以使用)

- Chrome:Blink(基于 webkit,Google 与 Opera Software 共同开发) (2013 年之前是用 webkit)

- Safari:webkit 内核 (苹果公司的内核,开源代码,不受 IE,火狐限制. 遨游浏览器,塞班手机浏览器,安卓默认浏览器都是用

- webkit 作为内核.另外 google chrome ,360 极速浏览器和搜狗高速浏览器高速模式也使用 webkit 作为内核.)

- Opera:以前是 presto 内核(渲染速度达到极致,ie 内核速度的 3 倍,但是兼容性很差),Opera 现已改用Google Chrome 的 Blink内核


#### 谈谈以前端角度出发做好 SEO 需要考虑什么?

- Meta 标签优化

- 主要包括主题(Title),网站描述(Description),和关键词(Keywords).其他还有 Author(作者),Category(目录),Language(编码语种)等.

- 放置关键词

- 关键词分析和选择是 SEO 最重要的工作之一.首先要给网站确定主关键词(一般在 5 个上下),然后针对这些关键词进行优化,包括关键词密度(Density),相关度(Relavancy),突出性(Prominency)等等.

- 合理的标签使用.


#### 对 WEB 标准以及 W3C 的理解与认识.

web 标准简单来说可以分为结构、表现和行为.

web 标准三层分离,使其更具有模块化.但一般产生行为时,就会有结构或者表现的变化,也使这三者的界限并不那么清晰.

W3C 对 web 标准提出了规范化的要求,也就是在实际编程中的一些代码规范:包含如下几点:

1.对于结构要求:(标签规范可以提高搜索引擎对页面的抓取效率,对 SEO 很有帮助)

1)标签字母要小写

2)标签要闭合

3)标签不允许随意嵌套

2.对于 css 和 js 来说

1)尽量使用外链 css 样式表和 js 脚本.是结构、表现和行为分为三块,符合规范.同时提高页面渲染速度

2)样式尽量少用行间样式表,使结构与表现分离,标签的 id 和  class  等属性命名要做到见文知义,标签越少,加载越快,用户体验提高,代码维护简单,便于改版

3)不需要变动页面内容,便可提供打印版本而不需要复制内容,提高网站易用性.

#### 从用户刷新网页开始, 一次 js 请求一般情况下有哪些地方会有缓存处理?

- DNS 缓存(成功访问后网站的域名、IP 地址信息缓存到本地

- CDN 缓存(内容分发网络,选择一个离用户最近的 CDN 边缘节点来响应用户的请求)

- 浏览器缓存(存储最近访问的过的页面,再次请求时,从本地磁盘显示文档来加速页面的阅览,节约网络的资源加速浏览)       服务器缓存(将需要频繁访问的网络内容存放在离用户较近、访问速度更快的系统中,来提高访问速度).


#### 大量图片加载很慢,有哪些方法优化 这些图片的加载,给用户更好的体验.

1.图片懒加载,在页面上的未可视区域可以添加一个滚动条事件,判断图片位置与浏览器顶端的距离与页面的距离,如果前者        小于后者,优先加载. (大型电商网站常见)

2.图片预加载:如果为幻灯片、相册等,可以使用图片预加载技术,将当前展示图片的前一张和后一张优先下载.

3.如果图片为 css 图片,可以使用 CSSsprite 精灵图、SVGsprite 矢量图、Iconfont 字体图标、Base64 等技术.

4.缩略图:如果图片过大,可以使用特殊编码的图片,加载时会先加载一张压缩的特别厉害的缩略图,以提高用户体验.

#### 知道的网页制作会用到的图片格式有哪些?

1. PSD 格式,是 Photoshop 专用文件.非压缩的原始文件保存格式.常用于保留原始信息,文件较大,不便于传输,一般用于备份.

2. GIF 图片格式, 256 种的颜色,无损压缩,支持透明度,

3. PNG 图片格式,有 PNG-8、PNG-24 两种,比 gif 更好,但旧的浏览器和程序可能不支持 PNG 文件.

4. JPEG 图片格式,目前最流行的图像格式,可以把文件压缩到最小的格式,下载速度快.存在一定损耗

5. BMP 图片格式,Windows 系统标准图像,缺点--占用磁盘空间过大.在单机上比较流行

6. webp  是由谷歌推出的新一代图片格式,在压缩方面比当前   JPEG   格式更优越,同时提供了有损压缩与无损压缩的图片文件格式,派生自图像编码格式 VP8

优点:在质量相同的情况下,WebP 格式图像的体积要比 JPEG 格式图像小 40%.

缺点:编解码速度偏慢.但是由于减少了文件体积,缩短了加载的时间,实际上文件的渲染速度反而变快了.      浏览器支持不全.因此,目前可行的解决方法只能是同时提供两套图片.

#### 简介盒子模型.

CSS 的盒子模型有两种:IE 盒子模型、标准的 W3C 盒子模型模型.

内容(content)、填充(padding)、边框(border)、边界(margin)都是盒模型的基本属性.

区别:

标准的 W3C 盒子模型模型: 设置的 border 值只包括 content 和 padding.

IE 盒子模型:设置的 border 值包括 content,padding 和 border 值.

#### CSS 中可以通过哪些属性定义,使得一个 DOM 元素不显示在浏览器可视范围内?

基本的: 设置 `display :none`;(不占位置),或者设置 `visibility :hidden`(占位置)

使用 display:none 属性后,HTML 元素(对象)的宽度、高度等各种属性值都将"丢失";而使用 visibility:hidden 属性后,HTML 元素(对象)仅仅是在视觉上看不见(完全透明),而它所占据的空间位置仍然存在.

技巧性: 设置宽高为 0,设置透明度为 0,设置 z-index 位置在-1000

#### img 的 alt 与 title 有何异同? strong 与 em 的异同?

`alt` 属性是在你的图片因为某种原因不能加载时在页面显示的提示信息,它会直接输出在原本加载图片的地方

`title` 属性是在你鼠标悬停在该图片上时显示一个小提示,鼠标离开就没有了,有点类似jQuery  的hover.HTML  的绝大多数标签都支持 title 属性,title 属性就是专门做提示信息的.

默认显示样式上:`<em>`默认样式是斜体,`<strong>`默认样式是粗体.

语义上:`<em>` 用来局部强调,`<strong>` 则是全局强调. 从视觉上考虑,`<em>` 的强调是有顺序的, 阅读到某处时, 才会注意到.`<strong>`的强调则是一种随意无顺序的,看见某文时,立刻就凸显出来的关键词句          【注】:在实际开发中,我们看到一般大网站都只是使用`<strong>`标签就够了,比较少使用`<em>`标签.此外,使用`<em>`和`<strong>`这两个标签可以为 SEO 关键词排名加分.

#### 简述一下 src 与 href 的区别.

src 用于替换当前元素(引入),href 用于在当前文档和引用资源之间确立联系(关联).

src 是source  的缩写,指向外部资源的位置,指向的内容将会嵌入到文档中当前标签所在位置;在请求src  资源时会将其指向的资源下载并应用到文档内,例如 js 脚本,img 图片和 frame 等元素.

当浏览器解析到该元素时,会暂停其他资源的下载和处理,直到将该资源加载、编译、执行完毕,图片和框架等元素也如此, 类似于将所指向资源嵌入当前标签内.这也是为什么将 js 脚本放在底部而不是头部.

href 是  Hypertext Reference  的缩写,指向网络资源所在位置,建立和当前元素(锚点)或当前文档(链接)之间的链接,如果我们在文档中添加` <link href="common.css" rel="stylesheet"/>`那么浏览器会识别该文档为 css 文件,就会并行下载资源并且不会停止对当前文档的处理.这也是为什么建议使用 link 方式来加载 css,而不是使用@import 方式

补充:link 和@import 的区别,两者都是外部引用 CSS 的方式,但是存在一定的区别:

1. link 是 HTML 标签,除了加载 CSS 外,还可以定义 RSS 等其他事务;@import 属于 CSS 范畴,只能加载 CSS.

2. link 引用 CSS 时,在页面载入时同时加载;@import 需要页面网页完全载入以后加载.

3. link 是 XHTML 标签,无兼容问题;@import 是在 CSS2.1 提出的,低版本的浏览器不支持.

4. link 支持使用 Javascript 控制 DOM 去改变样式;而@import 不支持.

#### px 和 em 的区别.

px 和 em 都是长度单位.区别是,px 的值是固定的,指定是多少就是多少,计算比较容易.em 得值不是固定的,并且 em 会继承父级元素的字体大小(先计算结果后继承,和数值+%一样).

浏览器的默认字体高都是 16px.所以未经调整的浏览器都符合: 1em=16px.那么 12px=0.75em,	10px=0.625em

#### 行内元素和块级元素的具体区别是什么?行内元素的 padding 和 margin 可设置吗?

一、块级元素:block element

块级元素默认占一整行,可嵌套块级元素或行内元素;一般作为容器出现,用来组织结构,特例:`<form>`只能包含块级元素

DIV 是最常用的块级元素,元素样式的 display:block 都是块级元素二、行内元素:inline element

也叫内联元素、内嵌元素等;行内元素一般都是基于语义级(semantic)的基本元素,只能容纳文本或其他内联元素    元素样式的 display : inline 的都是行内元素

三、block(块)元素的特点

①、总是在新行上开始;

②、高度,行高以及外边距和内边距都可控制;

③、宽度缺省是它的容器的 100%,除非设定一个宽度.

④、它可以容纳内联元素和其他块元素四、inline 元素的特点

①、和其他元素都在一行上;

②、高,行高及外边距和内边距不可改变;

③、宽度就是它的文字或图片的宽度,不可改变

④、内联元素只能容纳文本或者其他内联元素 对行内元素,需要注意如下

设置宽度 width 无效.

设置高度 height 无效,可以通过 line-height 来设置. 设置 margin 只有左右 margin 有效,上下无效.

设置 padding 只有左右 padding 有效,上下则无效.注意元素范围是增大了,但是对元素周围的内容是没影响的. 五、常见的块状元素

Address、blockquote、center、dir、div、dl、fieldset、form  、h1 到 h6、hr、input、prompt、	menu、noframes、noscript、

ol、p、pre、table、ul

六、常见的内联元素

a、abbr、acronym、b、bdo、big、br、cite、code、dfn、em、 font、i、img、input、 kbd、label、q、s、samp、select、

small、span、strike、strong、sub、sup、textarea、u

七、空元素

没有内容的 HTML 内容被称为空元素.空元素是在开始标签中关闭的.`<br/><hr> <input> <img>`

#### rgba()和 opacity 的透明效果有什么不同?

rgba()和 opacity 都能实现透明效果.

opacity 作用于元素,以及元素内的所有内容的透明度

rgba()只作用于元素的颜色或其背景色.(设置 rgba 透明的元素的子元素不会继承透明效果！)

#### BFC 是什么?

BFC(块级格式化上下文),一个独立的渲染区域,只有块级元素参与,规定了内部块级元素的布局方式,且该区域与外部无关.

BFC  元素特性表现原则:内部子元素再怎么变动都不会影响外部元素布局规则:

1.内部 BOX 会在垂直方向上一个接一个放置,所以是从上向下排列

2.元素的 margin 左边和父级的左边紧挨,浮动元素也是这样,所以是从左向右排列

3. BOX 垂直方向上距离由 margin 决定,但同一个 BFC 内的两个相邻元素的 margin 会出现外边距合并(overflow 可以解决外边距合并)

4. BFC 是页面上一个隔离的独立容器,内容子元素不影响外部元素

5.计算 BFC 高度时,浮动元素也参与计算(overflow 清除浮动以后可以撑开盒子高度)

BFC 的生成:

根元素 body、浮动 float 不为 none、定位 position:absolute/fixed、overflow、display:inline-block/flex/table-cell

#### 如何垂直居中一个浮动元素?

1.已知浮动元素的宽高

设定父元素为相对定位,浮动元素为绝对定位 top 和 left 为 50%,再设置浮动元素的 margin-left/top 值为浮动元素宽高一半的负值.

2.不知道浮动元素的宽高

设定父元素为相对定位,浮动元素为绝对定位.且 left/right/top/bottom 设置为 0,再给浮动元素设置 margin auto.

另:如何居中 div? 答:默认 div 有宽度,设置 margin:0 auto;

#### 列出 display 的值及作用.position 的值, relative 和 absolute 定位原点是?

display:

block---块级元素默认显示方式.单独占一行,能设置宽高 margin 和 padding 值;

inline-block---能像块级元素一样设置宽高,但也能像行内元素一样,和其他 div 平列一行. inline---行内元素的默认显示方式.

none---缺省值(不存在页面中) position :

relative ----相对定位,相对于其正常位置进行定位.

absolute ----绝对定位,相对于非 static 定位第一个直接父元素进行定位.

fixed ---- (老 IE 不支持)-----生成绝对定位的元素,相对于浏览器窗口进行定位.

static ---- 默认值.没有定位,元素出现在正常的流中(忽略 top, bottom, left, right z-index 声明).

#### absolute 的 containing block 计算方式跟正常流有什么不同?(即 absolute 的元素,浏览器是怎么找到最终的位置的)

css 核心:包含块(Containing Block)是视觉格式化模型的一个重要概念,它与框模型类似,也可以理解为一个矩形,而这个矩形

的作用是为它里面包含的元素提供一个参考,元素的尺寸和位置的计算往往是由该元素所在的包含块决定的.

包含块简单说就是定位参考框,或者定位坐标参考系,元素一旦定义了定位显示(相对、绝对、固定)都具有包含块性质,它所包含的定位元素都将以该包含块为坐标系进行定位和调整.

确定一个元素的 containing block,由 position 属性确定:

1. static(默认的)/relative:简单说就是它的父元素的内容框(即去掉 padding 的部分)

2. absolute: 向上找最近的定位为 absolute/relative 的元素

3. fixed: 它的 containing block 一律为根元素(html/body),根元素也是initial containing block

#### 描述一个"reset"的 CSS 文件并如何使用它.知道 normalize.css 吗?说明不同之处?

引入:不同的浏览器对一些元素有不同的默认样式,不处理时在不同的浏览器下会存在风险,显示差异,甚至布局被打乱,(初始        化 CSS 会对搜索引擎优化造成小影响)

可以用  Normalize.css   来代替重置样式文件.但它没有重置所有的样式风格,仅提供了一套合理的默认样式值.既能让众多浏览器达到一致和合理,但又不扰乱其他的东西(如粗体的标题). 在这一方面,无法做每一个复位重置.它也确实有些超过一个重置,它处理了我们永远都不用考虑的怪癖,像 HTML 的 audio 元素不一致或 line-height 不一致.

#### html 常见兼容性问题?

1. IE 的双边距 BUG

问题:块级元素 float 后设置横向margin,ie6 显示的 margin 比设置的较大. 解决:给块级元素设置_display:inline;(_ 只有 ie6 能识别)

2. 超链接访问过后 hover 样式就不出现的问题是什么?如何解决? 问题:被点击访问过的超链接样式不在具有 hover 和 active 了

解决:改变 CSS 属性的排列顺序: L-V-H-A(link,visited,hover,active)

3. 个像素问题

问题:在IE7 中两个div 是紧挨着的,但是在IE6 中会出现两个div 之间出现3px 左右的间隙,这就是传说中的"IE 3px bug".

解决:这是由于使用 float 引起的使用 dislpay:inline -3px 可以解决.

4. IE z-index 问 题

问题:父元素有定位,子元素即便设置 z-index 为多少,都会显示在最上面.

解决:那是因为 z-index 是有继承的.父元素有定位,默认 z-index 为 1.那么子元素也就 z-index 为 1. 要想改变,就得给父元素设置 position:relative,后再设置 z-index.

5. IE5-8 不支持 opacity

解决: 使用滤镜 filter

filter: alpha(opacity=60); /* for IE5-7 */

-ms-filter: "progid:DXImageTransform.Microsoft.Alpha(Opacity=60)"; /* for IE 8*/

6. IE6 不支持 PNG 透明背景

解决: IE6 下使用 gif 图片

7. Png 透 明

问题:用透明 PNG 图片作为链接的背景,图像的透明部分变得不能点击.

解决:在兼容 ie 的代码中,给 a 标签设置背景,而 background 的 url()设置为当前页面上.

8. Min-height 最小高度

问题:没办法设置最小高度

解决:用!Important 解决.代码:	height:auto !important ; height:最小 px;

9. select 在 ie6 下遮盖 使用 iframe 嵌套

解决:用 iframe 当做 div 的底. div 可以遮盖 iframe,iframe 可以遮盖 select.

10. 没法定义 1px 左右的宽度容器问题:IE6 默认的行高造成的

解决:使用 over:hidden,zoom:0.08, line-height:1px 可以解决.

11. 浏览器默认的 margin 和 padding 不同.

解决: 加一个全局的 *{ margin:0; padding:0;} 或者 css 初始化

12. a(有 href 属性)标签嵌套下的 img 标签,在IE 下会有边框. 解决: a img{border:none;}

13. input 中 button 会有默认的边框,阴影

解决:用 border:none; 解决.在 IE6 以下,还需要加上 border-color:transparet;

#### 书写代码,实现 table 表格的隔行变色

方案 1:js 里的隔行变色,js 代码核心为i%2 时的取值,进行操作 style

方案 2:使用 c3 选择器 E:nth-of-type(2n)、E:nth-of-type(2n+1)

#### CSS3 有哪些新特性?

简化:选择器、RGBA、阴影、盒模型、边框圆角、边框图片、渐变、背景、变换、过渡、动画、列布局、伸缩布局、媒体查询

1. css3 选择器:
2. 颜色:
3. 文本阴影:
4. 盒模型:
5. 盒子阴影:
6. 边框圆角:
7. 边框图片:
8. 渐变:
9. 背景:
10. 过渡:
11. 变换:
12. 动画
13. 列布局:
14. 伸缩布局:
15. 媒体查询

#### html5 有哪些新特性、移除了那些元素?如何处理 HTML5 新标签的浏览器兼容问题?如何区 分 HTML 和 HTML5?

1、新特性:

语义特性,本地存储特性,设备兼容特性,连接特性,网页[多媒体](http://baike.baidu.com/view/3323.htm)特性,三维、图形及特效特性,性能与集成特性

a.语义化更好的内容标签(header,nav,footer,aside,article,section)

b.表单控件,calendar、date、time、email、url、search

c.音频、视频 API(audio,video)	自定义播放器案例

d.地理定位(Geolocation) API	掌握获取、使用第三方 API 方法

e.拖拽释放(Drag and drop) API	给元素设置[draggable ](http://www.runoob.com/tags/att-global-draggable.html)= "true" 属性使其可拖动,链接和图片默认可拖动

f. WEB 存储 API	只能存储字符串

localStorage 长期存储,浏览器关闭后数据不丢失;sessionStorage 临时存储,不共享,关闭页面数据丢失

g.画布(Canvas) API

h.新的技术 webworker, websocket, Geolocation(作为了解)

webworker:可以在浏览器后台运行 [JavaScript](http://lib.csdn.net/base/javascript), 而不占用浏览器自身线程.Web Worker 可以提高应用的总体性能,并且提升用户体验.受限于不能访问 DOM 节点、全局变量和函数、window 和 document,但可以使用定时器和 XMLHttpRequest 实现 Ajax 通信. 可分为两种类型:专用线程 dedicated web worker(单页面),以及共享线程 shared web worker(多页面).

websocket:html5 中的新通讯协议,实现了浏览器与服务器全双工通信(full-duplex).一开始的握手需要借助 HTTP 请求完成.前期的网站实时通讯是通过轮询技术实现,定期发送请求,比较占带宽.IE10+实现了该协议.

Geolocation:地理定位,html5 提供了 api

2、移除的元素:

纯表现的元素:basefont,big,center,font,dir,strike,

对可用性产生负面影响的元素:frame,frameset,noframes;

3、HTML5 新标签兼容性处理:

a.IE8/IE7/IE6 支持通过 document.createElement 方法产生的标签,但会把新标签解析成行内元素,还需要添加标签默认的样式 display:block

b.引入兼容性处理文件 html5shiv.min.js(bootstrap 框架中有使用)

4、区分 html 和 html5:

查看 DOCTYPE 声明:`<!DOCTYPE html>`为 html5 标准

#### HTML5 和 CSS3 的新标签

HTML5:canvas , audio , video , datalist , keygen ,meter, header, footer, nav, section, article, aside,

CSS3:RGBA, text-shadow, box-shadow, border-radius, border-image,border-color, transform, transition, animation, linear-gradient, radial-gradient, flex

#### 如何在  HTML5	页面中嵌入音频、视频?

HTML 5 包含嵌入音频文件的标准方式,支持的格式包括 MP3、Wav 和 Ogg:

方 法 1:`<audio src="../mp3/See.mp3" controls autoplay></audio>`

方法 2:`<audio controls><source src="jamshed.mp3" type="audio/mpeg"></audio>`

####  HTML5 Canvas 元素有什么用?

Canvas  元素用于在网页上绘制图形,属于  html5,ie9-不支持,自身只是一个标签,没有任何绘制方法,绘图是通过  js  实现,该对象提供了各种绘图 api.常用 2d 库 konvajs.

#### 语义化的理解?

1、利于   SEO,搜索引擎的爬虫依赖于标记来确定上下文和各个关键字的权重,      页面是否对爬虫容易理解非常重要,因为爬虫很大程度上会忽略用于表现的标记,而只注重语义标记

2、让页面的内容结构化,便于各种终端根据其自身的条件来合适地显示页面,虽然部分 HTML 标签存在默认样式,甚至浏览器都各有默认样式,这种表现虽然不是语义化 HTML 结构的有点,但同样是为了更好的表达 HTML 语义

3、便于维护,方便阅读源码, 去掉或样式丢失的时候能让页面呈现清晰的结构

4、便于团队开发和维护,W3C        给我们定了一个很好的标准,在团队中大家都遵循这个标准,可以减少很多差异化的东西,方便开发和维护,提高开发效率,甚至[实现模块化开发](http://www.cssforest.org/blog/index.php?id=134)

总之一句话,用正确的标签做正确的事情！

#### 什么是响应式设计?

网页制作的过程中让不同的设备有不同的尺寸和不同的功能.包括弹性网格和布局、图片、CSS media query 媒体查询的使用等.响应式网页设计就是一个网站能够兼容多个终端,而不必多次开发.

#### 例举 3 种强制类型转换和 2 种隐式类型转换? ?

强制:parseInt,parseFloat,Number()

隐式:+string 可以转成数字, a+""可以转成字符串,!var 可以转成布尔值

#### 传统事件绑定和符合 W3C 标准的事件绑定有什么区别?

DOM0 传统事件绑定,如 onclick

会出现同一元素同名事件的覆盖,不支持 DOM 事件流事件捕获阶段

DOM1 没有事件绑定规范

IE 绑定:attachEvent("onclick",function(){}),不支持捕获

DOM2 事件绑定:addEventListener("click",function(){},true);参数 3 为 true 支持捕获,参数 3 为 false 支持冒泡不会出现同名事件覆盖,支持完整事件流

事件流:捕获->目标->冒泡

事件绑定是指把事件注册到具体的元素之上,普通事件指的是可以用来注册的事件

#### 事件冒泡和事件委托

事件冒泡:当一个元素上的事件被触发的时候,比如说鼠标点击了一个按钮,同样的事件将会在那个元素的所有祖先元素中被触发. 这一过程被称为事件冒泡;这个事件从原始元素开始一直冒泡到 DOM 树的最上层.

阻止事件冒泡和捕获: 标准浏览器 e. stopPropagation();	IE9 之前 event.canceBubble=true;

阻止默认事件:为了不让 a 点击之后跳转,我们就要给他的点击事件进行阻止

return false;	e.preventDefault();

事件委托:让利用事件冒泡的原理,让自己的所触发的事件,让他的父元素代替执行！

#### IE 和标准下有哪些兼容性的写法

var event = event || window.event document.documentElement.clientWidth || document.body.clientWidth var target = event.srcElement||event.target

#### call 和 apply 的区别

call 和 apply 都是为了改变某个函数运行时的 context 即上下文而存在的,换句话说,就是为了改变函数体内部 this 的指向.因为 JavaScript 的函数存在「定义时上下文」和「运行时上下文」以及「上下文是可以改变的」这样的概念.

二者的作用完全一样,只是接受参数的方式不太一样,参数 1 是 this ,all 需要把参数按顺序传递进去,而 apply 则是把参数放在数组里,若第一个参数为 null 那么函数中的 this 指向 window

Bind 也可以改变当前this 指向;返回的是个函数.

#### b 继承 a 的方法

继承:原型继承,借用构造函数继承,组合继承,拷贝继承.

一般最简单面试会用的继承方式:原型继承:b.prototype=new a();

#### 添加删除替换插入到某个节点的方法

obj.appendChild()	//追加子节点

obj.insertBefore()	//插入子节点,参数 2 为 null 时等同于 appendChild obj.replaceChild()	//替换子节点,参数:新节点、旧节点(应该是没用过)

obj.removeChild()	//删除子节点

此外,jQuery 还提供了 append、perpend、after、before,appendTo、prependTo、insertAfter、insertBefore

#### javascript 的本地对象、内置对象和宿主对象

本地对象为 array、obj、regexp 等可以 new 实例化

内置对象为 Global、Math 等不可以实例化的(也是本地对象,Global 不存在,但是类似于 isNaN()、parseInt()和 parseFloat()方法都是他的方法)

宿主对象为浏览器提供的对象,所有的 BOM 和 DOM,如 document,window

#### JavaScript 是一门什么样的语言,它有哪些特点?

弱类型:声明变量都使用 var(ES6 中有 let 和 const)

动态类型:声明时类型不定,运行时才明确变量类型;对象可以随意添加属性、方法    解析型:遇到一行解析一行(区别是编译型全解析后再执行)

脚本语言:不需要编译,直接执行

#### 看下列代码输出为何?解释原因(变量提升和简单数据类型)

#### undefined 会在以下三种情况下产生

1、一个变量定义了却没有被赋值

2、想要获取一个对象上不存在的属性或者方法:

3、一个数组中没有被赋值的元素

注意区分 undefined 跟 not defnied(语法错误)是不一样的



#### foo = foo||bar ,这行代码是什么意思?为什么要这样写?

短路表达式,等同于 if(!foo) foo = bar;如果 foo 存在,值不变,否则把 bar 的值赋给 foo.

作为"&&"和"||"操作符的操作数表达式,这些表达式在进行求值时,只要最终的结果已经可以确定是真或假,求值过程便告终止,这称之为短路求值.

#### 列举浏览器对象模型 BOM 里常用对象,并列举 window 对象的常用方法

对象:window、document、location、screen、history、navigator  方法:alert()、confirm()、prompt()、open()、close()

补充:

window 对象是BOM 中所有对象的核心;

history 对象是用来把窗口的浏览历史用文档和文档状态列表的形式表示

back()与 forward()与浏览器的"后退","前进"功能一样.history.go(-2);后退两个历史记录;

location 对象是解析 URL,

location.reload()	重新加载页面

location.replace()   本窗口载入新文档

location.assign()	本窗口载入新文档

navigator 浏览器

navigator.appName Web 浏览器全称

navigator.appVersion Web 浏览器厂商和版本的详细字符串

navigator.userAgent 客户端绝大部分信息

navagator.platform 浏览器运行所在的操作系统

screen 窗 口

screen.availWidth   可用的屏幕宽度

screen.availHeigh   可用的屏幕高度

#### 简述列举文档对象模型 DOM 里 document 的常用的查找访问节点的方法并做简单说明

Document.getElementById	根据元素 id 查找元素

Document.getElementByClassName	根据元素类查找元素(存在兼容问题),得到的是对象数组

Document.getElementTagName	根据指定的元素名查找元素,得到的是对象数组

Document.querySelectorAll	通过 CSS 选择器获取元素,以类数组形式存在

#### 简述创建函数的几种方式

第一种(函数声明):	function sum1(num1,num2){ return num1+num2; }

第二种(函数表达式) :	var sum2 = function(num1,num2){ return num1+num2; }

第三种(函数对象方式) : var sum3 = new Function("num1","num2","return num1+num2");

匿名函数:	function(){}:只能自己执行自己

#### Script 标签在页面最底部 body 封闭之前和封闭之后有什么区别?浏览器会如何解析它们?

如果放在 body 封闭之前,将会阻塞其他资源的加载

如果放在 body 封闭之后,不会影响 body 内元素的加载



#### javascript 中的垃圾回收机制

在 Javascript 中,如果一个对象不再被引用,那么这个对象就会被  GC  回收.如果两个对象互相引用,而不再被第  3  者所引用,那么这两个互相引用的对象也会被回收.因为函数 a 被 b 引用,b 又被 a 外的 c 引用,函数 a 执行后不会被回收



#### 你如何优化自己的代码?

代码重用

避免全局变量(命名空间,封闭空间,模块化 mvc..)

拆分函数避免函数过于臃肿:单一职责原则

适当的注释,尤其是一些复杂的业务逻辑或者是计算逻辑,都应该写出这个业务逻辑的具体过程     内存管理,尤其是闭包中的变量释放

#### 简述 readyonly 与 disabled 的区别

readonly 只针对 input(text/password)和 textarea 有效

disabled 对于所有的表单元素都有效

当表单以 POST 或 GET 的方式提交的话, disabled 元素的值不会被传递出去,而 readonly 会将该值传递出去

#### 为什么扩展 javascript 内置对象不是好的做法?

因为扩展内置对象会影响整个程序中所使用到的该内置对象的原型属性

#### HTTP 协议中,GET 和 POST 有什么区别?分别使用什么场景?

get 传送的数据长度有限制,post 没有

get 通过 url 传递,在浏览器地址栏可见,post 是在报文中传递

post 一般用于表单提交.

get 一般用于简单的数据查询,严格要求不是那么高的场景

#### HTTP 协议中,header 信息里面,怎么控制页面失效时间(last-modified, cache-control,

Expires 分别代表什么)

HTTP(HyperTextTransferProtocol)即超文本传输协议,目前网页传输的的通用协议.HTTP 协议采用了请求/响应模型,浏览器或其他客户端发出请求, 服务器给与响应. 就整个网络资源传输而言, 包括 message-header 和 message-body 两部分. 首先传递message-header,即 httpheader 消息.http header  消息通常被分为 4 个部分:general header, request header, response header, entity

header.但是这种分法就理解而言,感觉界限不太明确.根据维基百科对 http header 内容的组织形式,大体分为 Request 和 Response

两部分.

last-modified 处在 Response 中,代表请求资源的最后修改时间.客户可以通过 If-Modified-Since 请求头提供一个日期,该请求将被视为一个条件 GET,只有改动时间迟于指定时间的文档才会返回,否则返回一个 304(Not Modified)状态.Last-Modified 也可用

setDateHeader 方法来设置.

Expires 处在 Response 中,代表响应过期的日期和时间.

cache-control 指定请求和响应遵循的缓存机制请求时的缓存指令包括 no-cache、no-store、max-age、 max-stale、min-fresh、only-if-cached,响应消息中的指令包括 public、private、no-cache、no- store、no-transform、must-revalidate、proxy-revalidate、max-age. 各个消息中的指令含义如下:
+ Public 指示响应可被任何缓存区缓存.
+ Private 指示对于单个用户的整个或部分响应消息,不能被共享缓存处理.这允许服务器仅仅描述+ 当用户的部分响应消息,此响应消息对于其他用户的请求无效.
+ no-cache 指示请求或响应消息不能缓存.
+ no-store 用于防止重要的信息被无意的发布.在请求消息中发送将使得请求和响应消息都不使用+ 缓存.
+ max-age 指示客户机可 以接收生存期不大于指定时间(以秒为单位)的响应.
+ min-fresh 指示客户机可以接收响应时间小于当前时间加上指定时间的响应
+ max-stale 指示客户机可以接收超出超时期间的响应消息.如果指定   
+ max-stale 消息的值,那么客户机可以接收超出超时期指定值之内的响应消息.

#### HTTP 协议目前常用的有哪几个?KEEPALIVE 从哪个版本开始出现的?

超文本传输协议已经演化出了很多版本,它们中的大部分都是向下兼容的.在RFC 2145  中描述了HTTP  版本号的用法.客户端在请求的开始告诉服务器它采用的协议版本号,而后者则在响应中采用相同或者更早的协议版本.

0.9 已过时.只接受 GET 一种请求方法,没有在通讯中指定版本号,且不支持请求头.由于该版本不支持 POST 方法,所以客户端无法向服务器传递太多信息.

HTTP/1.0 这是第一个在通讯中指定版本号的 HTTP 协议版本,至今仍被广泛采用,特别是在[代理服务器](http://baike.baidu.com/view/751.htm)中.

HTTP/1.1        当前版本.持久连接被默认采用,并能很好地配合代理服务器工作.还支持以管道方式同时发送多个请求,以便降低线路负载,提高传输速度.

HTTP/1.1 相较于 HTTP/1.0 协议的区别主要体现在:1 缓存处理,2 带宽优化及网络连接的使用,3 错误通知的管理,4 消息在网络中的发送,5 互联网地址的维护,6 安全性及完整性

keep-Alive  功能使客户端到服务器端的连接持续有效,当出现对服务器的后继请求时,Keep-Alive  功能避免了建立或者重新建立连接.市场上的大部分 Web 服务器,包括 iPlanet、IIS 和 Apache,都支持 HTTP Keep-Alive.对于提供静态内容的网站来说,这个功能通常很有用.但是,对于负担较重的网站来说,这里存在另外一个问题:虽然为客户保留打开的连接有一定的好处,但它同样影响了性能,因为在处理暂停期间,本来可以释放的资源仍旧被占用.当  Web  服务器和应用服务器在同一台机器上运行时,Keep-  Alive   功能对资源利用的影响尤其突出.此功能为 HTTP 1.1 预设的功能,HTTP 1.0 加上 Keep-Alive header 也可以提供 HTTP 的持续作用功能.

#### 业界常用的优化 WEB  页面加载速度的方式(可以分别从页面元素展现,请求连接,css,js, 服务器等方面介绍)

(1) 优化图像:这个绝对是显而易见的,可以看到图片占据的页面内容分量最重.在现代网页设计中,图片绝对占据了大部分        的内容.你需要针对你的页面重新定义图片大小.这能够有效地帮助你减少页面大小.

(2) 减少DNS 查询(DNS lookups):减少DNS 查询是一个WEB 开发人员可以用了页面加载时间快速有效的方法.DNS 查询需要话费很长的时间来返回一个主机名的 IP 地址.而浏览器在查询结束前不会进行任何操作.对于不同的元素可以使用不同的主机名, 如 URL、图像、脚本文件、样式文件、FLASH 元素等.具有多种网络元素的页面经常需要进行多个  DNS  查询,因而花费的时间更长. 减少不同域名的数量将减少并行下载的数量,加速你的网站

(3) 减少 HTTP 请求:还有一种简单的优化网页速度的方法是,减少 HTTP 请求.当一个网站一下子收到太多的 HTTP 请求,它的访客就会有响应时间延迟的体验,这不仅增加了 CPU 使用率也增加了页面的加载时间.那么,又该如何减少 HTTP 请求?减少网站上的对象数量;最小化网站上的重定向数量;使用 CSS Sprites 技术(只要你需要的那部分图片内容).

(4) 使用内容分发网络(Content Delivery Network  CDN):服务器处理大流量是很困难的,这最终会导致页面加载速度变慢.而使用CDN    就可以解决这一问题,提升页面加载速度.CDN    是位于全球不同地方的高性能网络服务,复制你网络的静态资源,并以最有效的方式来为访客服务.

(5) 把CSS 文件放在页面顶部,而JS 文件放在底部:把CSS  文件在页面底部引入可以禁止逐步渲染,节省浏览器加载和重绘页面元素的资源.JavaScript  是用于功能和验证.把JS  文件放在页面底部可以避免代码执行前的等待时间,从而提升页面加载速度.这些都是一些减少页面加载时间和提高转换率的方法.在某些情况下,需要 JavaScript 在页面的顶部加载(如某些第三方跟踪脚本).

(6) 压缩 CSS 和  JavaScript:压缩是通过移除不必要的字符(如  TAB、空格、回车、代码注释等),以帮助减少其大小和网页的后续加载时间的过程.这是非常重要的,但是,你还需要保存 JS 和 CSS 的原文件,以便更新和修改代码.

(7) 利用浏览器缓存:[浏览器缓存](https://developers.google.com/speed/docs/best-practices/caching?csw=1)是允许访客的浏览器缓存你网站页面副本的一个功能.这有助于访客再次访问时,直接从缓存中读取内容而不必重新加载.这节省了向服务器发送    HTTP    请求的时间.此外,通过优化您的网站的缓存系统往往也会降低您的网站的带宽和托管费用.

(8) 启用 GZIP 压缩:在服务器上压缩网站的页面是提升网站访问速度非常有效的一种方法.你可以用  gzip  压缩做到这一点.Gzip 是一个减小发送给访客的 HTML 文件、JS 和 CSS 体积的工具.压缩的文件减少了 HTTP 响应时间.据 Yahoo 报道,这大概可以减少 70%的下载时间.而目前 90%的通过浏览器的流量都支持 Gzip 压缩,因此,这是一个提示网站性能有效的选项.

#### 解释什么是 sql 注入,xss 漏洞

结构化查询语言(Structured Query Language)简称 SQL,是一种特殊目的的编程语言,是一种数据库查询和[程序设计语言](http://baike.baidu.com/view/128511.htm),用于存取数据以及查询、更新和管理[关系数据库系统](http://baike.baidu.com/view/549699.htm);同时也是[数据库脚本文件](http://baike.baidu.com/view/3542225.htm)的扩展名.

所谓SQL 注入,就是通过把SQL  命令插入到Web  [表单](http://baike.baidu.com/view/296684.htm)提交或输入域名或页面请求的查询字符串,最终达到欺骗服务器执行恶意的 SQL 命令.具体来说,它是利用现有应用程序,将(恶意)的 SQL 命令注入到后台数据库引擎执行的能力,它可以通过在 Web 表单中输入(恶意)SQL 语句得到一个存在安全漏洞的网站上的数据库,而不是按照设计者意图去执行 SQL 语句.

XSS 攻击:[跨站脚本攻击](http://baike.baidu.com/view/2633667.htm)(Cross Site Scripting),为不和层叠样式表(Cascading Style Sheets, CSS)的缩写混淆,故将跨站脚本攻击缩写为XSS.XSS 是一种经常出现在web  应用中的计算机安全漏洞,它允许恶意web  用户将代码植入到提供给其它用户使用的页面中. 比如这些代码包括 HTML 代码和客户端脚本.攻击者利用 XSS 漏洞旁路掉访问控制——例如[同源策略](http://baike.baidu.com/view/3747010.htm)(same origin policy).这种类型的漏洞由于被黑客用来编写危害性更大的[网络钓鱼](http://baike.baidu.com/view/77554.htm)(Phishing)攻击而变得广为人知.对于[跨站脚本攻击](http://baike.baidu.com/view/2633667.htm),黑客界共识是:跨站脚本攻        击是新型的"[缓冲区溢出攻击](http://baike.baidu.com/view/700134.htm)",而 JavaScript 是新型的"ShellCode".

#### 如何判断一个 js 变量是数组类型

ES5:Array.isArray(); [] instanceof Array;

调 用 数 组 的 slice 方 法 ; Object.prototype.toString.call([]); // "[object Array]"

#### 请列举 js 数组类型中常用的方法

| 方法     | 描述                             | FF   | IE   |
| -------- | -------------------------------- | ---- | ---- |
| concat() | 连接两个或更多的数组,并返回结果. | 1    | 4    |
| join()           | 把数组的所有元素放入一个字符串.元素通过指定的分隔符进行分隔. | 1    | 4    |
| pop()            | 删除并返回数组的最后一个元素                                 | 1    | 5.5  |
| push()           | 向数组的末尾添加一个或更多元素,并返回新的长度.               | 1    | 5.5  |
| reverse()        | 颠倒数组中元素的顺序.                                        | 1    | 4    |
| shift()          | 删除并返回数组的第一个元素                                   | 1    | 5.5  |
| slice()          | 从某个已有的数组返回选定的元素                               | 1    | 4    |
| sort()           | 对数组的元素进行排序                                         | 1    | 4    |
| splice()         | 删除元素,并向数组添加新元素.                                 | 1    | 5.5  |
| toSource()       | 返回该对象的源代码.                                          | 1    | -    |
| toString()       | 把数组转换为字符串,并返回结果.                               | 1    | 4    |
| toLocaleString() | 把数组转换为本地数组,并返回结果.                             | 1    | 4    |
| unshift()        | 向数组的开头添加一个或更多元素,并返回新的长度.               | 1    | 6    |
| valueOf()        | 返回数组对象的原始值                                         | 1    | 4    |

#### js 可否实现面向对象编程,如果可以如何实现 js 对象的继承

创建对象的方式:

(1)new Object()	varobj = new Object();

(2)自定义构造函数	function Person () {};

(3)对象字面量 varobj = {};

实现继承:

(1)原型继承 student.prototype = new Person();

(2)借用构造函数 function Student () {Person.call(this, name,age)};

(3)组合继承 Person.call(this.name); Student.prototype = new Person();

(4)克隆继承 object.extend = function(obj1, obj2) {

for (var key in obj1) {

obj2[key] = obj1[key];

};

};

(5)object.create()	var obj3 = object.create(obj4);



#### 列出 3 条以上 ff 和 IE 的脚步兼容问题

(1) window.event:

表示当前的事件对象,IE 有这个对象,FF 没有,FF 通过给事件处理函数传递事件对象

(2) 获取事件源

IE 用 srcElement 获取事件源,而 FF 用 target 获取事件源

(3) 添加,移除事件添加事件

IE:element.attachEvent("onclick", function) FF:element.addEventListener("click", function, true) 移除事件element.removeEventListener("click",function, true)

(4) 获取标签的自定义属性

IE:div1.value 或 div1["value"]

FF:可用 div1.getAttribute("value")

(5) document.getElementByName()和 document.all[name]

IE;document.getElementByName()和 document.all[name]均不能获取 div 元素

FF:可以

(6) input.type 的属性

IE:input.type 只读

FF:input.type 可读写

(7) innerTexttextContentouterHTML

IE:支持 innerText, outerHTML

FF:支持 textContent

(8) 是否可用 id 代替 HTML 元素

IE:可以用 id 来代替 HTML 元素

FF:不可以



#### 简述一下什么叫事件委托以及其原理

使用事件委托技术能让你避免对特定的每个节点添加事件监听器;相反,事件监听器是被添加到它们的父元素上.事件监听器会分析从子元素冒泡上来的事件,找到是哪个子元素的事件.

假设,当每个子元素被点击时,将会有各自不同的事件发生.你可以给每个独立的li    元素添加事件监听器,但有时这些li   元素可能会被删除,可能会有新增,监听它们的新增或删除事件将会是一场噩梦,尤其是当你的监听事件的代码放在应用的另一个地方时. 此时采用事件委托的方式的话,当子元素的事件冒泡到父 ul 元素时,你可以检查事件对象的 target 属性,捕获真正被点击的节点元素的引用.

#### 如何测试前端代码?知道 BDD, TDD, Unit Test 么?知道怎么测试你的前端工程么 (mocha, sinon, jasmin, qUnit..)?开发模式都是什么意思:
+ TDD:测试驱动开发(Test-Driven Development)
测试驱动开发是敏捷开发中的一项核心实践和技术,也是一种设计方法论.TDD        的原理是在开发功能代码之前,先编写单元测试用例代码,测试代码确定需要编写什么产品代码.TDD 的基本思路就是通过测试来推动整个开发的进行,但测试驱动开发并不只是单纯的测试工作,而是把需求分析,设计,质量控制量化的过程.TDD        首先考虑使用需求(对象、功能、过程、接口等),主要是编写测试用例框架对功能的过程和接口进行设计,而测试框架可以持续进行验证.
+ BDD:行为驱动开发(Behavior Driven Development)
行为驱动开发是一种敏捷软件开发的技术,它鼓励软件项目中的开发者、QA 和非技术人员或商业参与者之间的协作.主要是从用户的需求出发,强调系统行为.BDD 最初是由 Dan North  在  2003  年命名,它包括验收测试和客户测试驱动等的极限编程的实践, 作为对测试驱动开发的回应.使用 BDD 可以解决需求和开发脱节的问题,首先他们都是从用户的需求出发,保证程序实现效果与用户需求一致.

以上两种是开发模式,个人认为在代码编写过程常有按照 TDD 模式对代码进行小单元测试,以保证逻辑正确,而在整体上看按照 BDD 模式测试,保证开发和需求不发生脱节,但其实两种模式的框架都有. Unit Test 单元测试, 测试必须随生产代码的演进而修改,测试越脏就越难修改,所以为了保证其质量和可维护性,测试代码也常使用框架,常见的测试框架如下:

[Jasmine](http://pivotal.github.io/jasmine/):BDD 框架,

不依赖于任何框架,所以适用于所有的 Javascript 代码.使用一个全局函数 describe 来描述每个测试,并且可以嵌套.describe 函数有  2  个参数,一个是字符串用于描述,一个是函数用于测试.在该函数中可以使用全局函数it   来定义Specs,也就是单元测试的主要内容,   使用 expect 函数来测试.另外如果想去掉某个 describe,无须注释掉整段代码,只需要在 describe 前面加上 x 即可忽略该

describe.toBe 方法是一个基本的  matcher( 匹配器) 用来定义判断规则; 时间控制上,   提供了  Clock 方法来模拟时间, 以获取

setTimeout 的不同状态;由于异步需要等待回调, 提供了runs 和waitsFor 两个方法来完成这个异步的等待

[Qunit](http://qunitjs.com/)

jQuery 团队开发的一款测试套件.Qunit 采用断言(Assert)来进行测试,相比于 Jasmine 的 matcher 更加多的类型,Qunit 更集中在测试的度上.deepEqual 用于比较一些纵向数据,比如 Object 或者 Function 等.而最常用的 ok 则直接判断是否为 true.异步方面

Qunit 也很有趣,通过 stop 来停止测试等待异步返回,然后使用 start 继续测试,这要比 Jasmine 的过程化的等待更自由一些,不过有时也许会更难写一些.Qunit 还拥有 3 组 AOP 的方法( done 和 'begin' )来对应于整个测试,测试和模块.

[Sinon](http://sinonjs.org/)

Sinon 并不是一个典型的单元测试框架,更像一个库,最主要的是对 Function 的测试,包括Spy 和Stub 两个部分,Spy 用于侦测

Function,而 Stub 更像是一个 Spy 的插件或者助手,在 Function 调用前后做一些特殊的处理,比如修改配置或者回调.它正好极大的弥补了 Qunit 的不足,所以通常会使用 Qunit+Sinon 来进行单元测试.

值得一提的是,Sinon 的作者[Christian Johansen ](http://tddjs.com/)就是 *Test-Driven JavaScript Development* 一书的作者,这本书针对Javascript 很详细的描述了单元测试的每个环节.

[Mocha](http://visionmedia.github.io/mocha)

Mocha 将更多的方法集中在了 describe 和 it 中,比如异步的测试就非常棒,在 it 的回调函数中会获取一个参数done ,类型是

function,用于异步回调,当执行这个函数时就会继续测试.还可以使用  only 和 skip  去选择测试时需要的部分.Mocha  的接口也一样自由,除了 BDD 风格和 Jasmine 类似的接口,还有 TDD 风格的 (suite test setup teardown suiteSetup suiteTeardown),还有 AMD 风格的exports,Qunit   风格等.同时测试报告也可以任意组织,无论是列表、进度条、还是飞机跑道这样奇特的样式都可以在  bash  中显示.

#### 直接在对象的原型上添加方法是否安全?尤其是在 Object 对象

不安全,存在以下情况

容易造成全局污染,有可能和其他库冲突(考虑现在)

有可能出现代码向上不兼容的情况,有可能和新语法冲突(考虑未来)

不利于项目协作开发,易冲突,出了 Bug 不太好定位问题(考虑开发过程)

#### 函数声明与函数表达式的区别?

在 js 中,解析器在向执行环境中加载数据时,会先读取函数声明(预解析的函数提升),并使其在执行任何代码之前可用(可以访问),至于函数表达式,则必须等到解析器执行到它所在的代码行,才会真正被解析执行

函数声明:function func(){}	函数表达式:var foo = function(){};

而且要求,凡是函数的声明,不允许出现在代码的逻辑结构中或表达式中,函数声明必须独立存在(特例:在 if 语句中执行的

function xxx(){}会被当做表达式)

#### 在 Javascript 中什么是伪数组?如何将伪数组转化为标准数组?

伪数组(类数组):无法直接调用数组方法或期望 length 属性有什么特殊的行为,但仍可以对真正数组遍历方法来遍历它们.典型的是函数的 argument 参数,还有像调用 getElementsByTagName,document.childNodes 之类的,它们都返回 NodeList 对象都属于伪数组. 可以使用 Array.prototype.slice.call(likeArray)将数组转化为真正的 Array 对象.


#### 谈谈 this 对象的理解.

普通函数中:this ==》window

定时器中:this==》window

构造函数中:this==》当前实例对象

对象的方法中:this==》当前实例对象

原型对象的方法中:this==》当前实例对象事件处理函数中:this==》事件触发对象

#### 关于事件 IE 与火狐的事件机制有什么区别?如何阻止冒泡?

在 IE 中,事件对象是作为一个全局变量来保存和维护的.所有的浏览器事件,不管是用户触发的,还是其他事件,都会更新

window.event 对象.所以在代码中,只要调用 window.event 就可以获取事件对象, 再  event.srcElement  就可以取得触发事件的元素进行进一步处理.

在 FireFox 中, 事件对象却不是全局对象, 一般情况下是现场发生,现场使用, FireFox 把事件对象自动传给事件处理程序. 存在不同,就要进行兼容性处理,通常在事件执行函数中兼容性获取,e = window.event || e; //后面 e 是执行函数参数

阻止冒泡:window.event? window.event.cancelBubble = true : e.stopPropagation();

阻止默认:window.event? window.event.returnValue = false : e.preventDefault();

原生 javascript 的 return false 只会阻止默认行为,而是用 [jQuery ](http://caibaojian.com/jquery/)的话则既阻止默认行为又防止对象冒泡


#### 谈一谈你对 ECMAScript6 的了解?

1、let、const 和 块级作用域

let 允许创建块级作用域,ES6 中推荐使用 let 定义变量

同样在块级作用域有效的另一个变量声明方式是const,它可以声明一个常量.ES6  中,const   声明的常量类似于指针,它指向某个引用,也就是说这个「常量」并非一成不变的

注意点:

let 关键词声明的变量不具备变量提升(hoisting)特性

let 和 const 声明只在最靠近的一个块中(花括号内)有效

当使用常量 const 声明时,请使用大写变量,如:CAPITAL_CASING

const 在声明时必须被赋值

2、箭头函数

ES6 中,箭头函数就是函数的一种简写形式,使用括号包裹参数,跟随一个 =>,紧接着是函数体: var sum = function() {

return 1 + 1;

};

转换后:

let sum = () => 1 + 1;

3、函数参数默认值

let  sum  =  (a,  b=1)  =>  a  +  b;

4、Symbol

Symbol 是一种新的数据类型,它的值是唯一的,不可变的.ES6 中提出  symbol  的目的是为了生成一个唯一的标识符,不过你访问不到这个标识符

#### ECMAScript6 怎么写 class 么,为什么会出现 class 这种东西?

1、类

在 ECMAScript5 中,用通过原型的方式来进行模拟类和继承,但在 ECMAScript6 当中,出现了类(class)和继承(extend).ES6 中有

class 语法.值得注意是,这里的 class 不是新的对象继承模型,它只是原型链的语法糖表现形式

注意点:

类的声明不会提升(hoisting),如果你要使用某个 Class,那你必须在使用之前定义它,否则会抛出一个ReferenceError 的错误在类中定义函数不需要使用function 关键词

2、为什么要有 class 这种东西

a.引入了 Class(类)这个概念,作为对象的模板.通过class 关键字,可以定义类.基本上,ES6 的 class 可以看作只是一个语法糖,它的绝大部分功能,ES5 都可以做到

b.新的 class 写法只是让对象原型的写法更加清晰、更像面向对象编程的语法而已

#### document.write 和 innerHTML 的区别?

document.write  是重写整个  document,  写入内容是字符串的  html

innerHTML  是  HTMLElement  的属性,是一个元素的内部  html  内容

#### DOM 操作——怎样添加、移除、移动、复制、创建和查找节点?

1.添加节点

createElement()、createTextNode()、craeteDocumentFragment()

2.添加、移除、替换、插入

appendChild()、removeChild()、replaceChild()、insertBefore()

3.查找节点

getElementById() getElementsByTagName() getElementsByClassName() -->IE9+ querySelect() -->IE8+ querySelectAll() -->IE8+

#### 数组和对象有哪些原生方法,列举一下??

1. Array.concat()	//数组拼接 2.Array.push()	//向数组尾部添加元素 3.Array.pop()	//从数组尾部删除元素 4.Array.shift()	//从数组头部删除元素 5.Array.unshift()	//向数组头部删除元素 6.Array.slice()	//返回数组的一部分 7.Array.splice()	//插入,删除或替换元素 8.Array.reverse()	//颠倒数组中元素的顺序

	.Array.sort()	//对数组进行排序 10.Array.toString()	//将数组转换成一个字符串 11.Array.valueOf()	//

	2.Array.join()	//将数组元素连接起来以构建一个字符串 13.Array.length()	//数组的长度 14.Array.toLocalString()  //把数组转换成局部字符串

#### JavaScript 中的作用域与变量声明提升?

作用域:

1.全局作用域:使用范围在整个的页面(在 script 标签中)

2.函数作用域:使用方位在该函数内部----(闭包)

3.js 中没有块级作用域预解析:

1. 把变量的声明和函数的声明提升了,函数内部的变量只能提升到函数内部的顶部

2. 作用域链: 把全局的变量和函数f1 都看成是 0 级的链,f1 内部的函数和变量堪称是 1 级的,如果函数内部访问变量的时候,先在自己的函数中搜索,如果有则直接使用,如果没有则去上一级查找,找到则使用,找不到则继续向上一级找,一直找到全    局作用域,如果还没有则报错

#### 如何编写高性能的 JavaScript?

1.使用  DocumentFragment  优化多次  append

2.通过模板元素  clone  ,替代  createElement

3.使用一次  innerHTML  赋值代替构建  dom  元素

4.使用  firstChild  和  nextSibling  代替  childNodes  遍历  dom  元素

5.使用  Array  做为  StringBuffer  ,代替字符串拼接的操作

6.将循环控制量保存到局部变量

7.顺序无关的遍历时,用  while  替代  for

8.将条件分支,按可能性顺序从高到低排列

9.在同一条件子的多(  >2  )条件分支时,使用  switch  优于  if

10.使用三目运算符替代条件分支

11.需要不断执行的时候,优先考虑使用  setInterval

#### 那些操作会造成内存泄漏?

所谓的内存泄露,就是在您不再拥有或需要它的时候仍然存在

垃圾回收机制会定期扫描对象,并计算引用了每个对象的其他对象的数量.如果一个对象的没有被其他对象引用过,或对该对象的唯一引用是循环的,那么该对象内存即可回收

1.setTimeout 的第一个参数使用字符串而非函数的话,会引发内存泄露

2.闭包

3.控制台日志

4.循环(在两个对象彼此引用且彼此保留时,就会产生一个循环)


#### JavaScript 原型,原型链? 有什么特点?

1. 原型对象也是普通的对象,是对象一个自带隐式的 proto 属性,原型也有可能有自己的原型,如果一个原型对象的原型不为  null  的话,我们就称之为原型链

2. 原型链是由一些用来继承和共享属性的对象组成的(有限的)对象链(基本思想是利用原型让一个引用类型继承另一个引用类型的属性和方法)

理解:每个构造函数都有一个原型对象,原型对象都包含一个指向构造函数的指针,而实例都包含一个指向原型对象  的内部指针.那么,假如我们让原型对象等于另一个类型的实例,结果会怎么样呢?显然,此时的原型对象将包含一个指向另   一个原型的指针,相应地,另一个原型中也包含着一个指向另一个构造函数的指针.假如另一个原型又是另一个类型的实例, 那么上述关系依然成立,如此层层递进,就构成了实 例与原型的链条.这就是所谓原型链的基本概念

3. 当我们需要一个属性的时,JavaScript   引擎会先看当前对象中是否有这个属性, 如果没有的话,就会查找他的 Prototype 对象是否有这个属性


#### 前端开发的优化问题(看雅虎 14 条性能优化原则)

1.减少  http  请求次数:CSS  Sprites,  JS、CSS  源码压缩、图片大小控制合适;网页 Gzip,CDN  托管,data  缓存  ,图片服

务器.

2. 前端模板 JS+数据,减少由于 HTML 标签导致的带宽浪费,前端用变量保存  AJAX 请求结果,每次操作本地变量,不用请求,减少请求次数

3. 用  innerHTML  代替  DOM  操作,减少  DOM  操作次数,优化  javascript  性能.

4. 当需要设置的样式很多时设置  className  而不是直接操作  style.

5. 少用全局变量、缓存  DOM  节点查找的结果.减少  IO  读取操作.

6. 避免使用  CSS  Expression(css  表达式)又称  Dynamic  properties(动态属性).

7. 图片预加载,将样式表放在顶部,将脚本放在底部 加上时间戳.

8. 避免在页面的主体布局中使用  table,table  要等其中的内容完全下载之后才会显示出来,显示比  div+css  布局慢.


#### Ajax 是什么?它最大的特点是?优缺点?

Ajax (asynchronous javascript and xml),即异步 JavaScript 和 xml,主要用来实现客户端与服务器端的异步数据交互,实现页面的局部刷新.早期浏览器并不能原生支持 ajax,可以使用隐藏帧(iframe)方式变相实现异步效果,后来的浏览器提供了对 ajax 的原生 支 持                                                                                                                                                                                                                                . ajax 的最大的特点+优点:

Ajax 可以实现异步通信效果,实现页面局部刷新,避免用户不断刷新或者跳转页面,带来更好的用户体验;按需获取数据,节约带宽资源;

ajax 的缺点

1、 ajax  不 支 持 浏 览 器back按 钮 . 
2、安全问题, AJAX 暴露了与服务器交互的细节,诸如跨站点脚步攻击、SQL 注入攻击.

3、对搜索引擎的支持比较弱.


#### 请解释一下 JavaScript 的同源策略.

同源策略是客户端脚本(尤其是 Javascript)的重要的安全度量标准.它最早出自 Netscape Navigator2.0,其目的是防止某个文档或脚本从多个不同源装载.所谓同源指的是:协议,域名,端口相同,同源策略是一种安全协议,指一段脚本只能读取来自同一来源的窗口和文档的属性.

#### 如何解决跨域问题?

理解跨域的概念:协议、域名、端口都相同才同域,否则都是跨域 .

出于安全考虑,服务器不允许 ajax 跨域获取数据,但是可以跨域获取文件内容.基于这一点,可以动态创建 script 标签,使用标签的 src 属性访问 js 文件的形式,获取 js 脚本,并且这个 js 脚本中的内容是函数调用,该函数调用的参数是服务器返回的数据.为了获取这里的参数数据,需要事先在页面中定义回调函数,在回调函数中处理服务器返回的数据,这就是解决跨域问题的主流解决方案 .

#### 解释 jsonp 的原理,以及为什么不是真正的 ajax

Jsonp 并不是一种数据格式,而 json 是一种数据格式,jsonp 是用来解决跨域获取数据的一种解决方案,具体是通过动态创建

script 标签,然后通过标签的 src 属性获取 js 文件中的 js 脚本,该脚本的内容是一个函数调用,参数就是服务器返回的数据,为了处理这些返回的数据,需要事先在页面定义好回调函数,本质上使用的并不是 ajax 技术

#### 页面编码和被请求的资源编码如果不一致如何处理?

对于 ajax 请求传递的参数,如果是 get 请求方式,如果传递中文参数,由于不同的浏览器对参数编码的处理方式不同,在有些浏览器会乱码,所以对于  get  请求的参数需要使用 encodeURIComponent  函数对参数进行编码处理,后台开发语言都有相应的解码 api.对于 post 请求不需要进行编码 .



# 参考

> 广州数羊小队

[https://github.com/markyun/My-blog/blob/master/Front-end-Developer-Questions/Questions-and-Answers/README.md](https://github.com/markyun/My-blog/blob/master/Front-end-Developer-Questions/Questions-and-Answers/README.md)

[https://juejin.im/entry/5b4953a4e51d4519575a07f1](https://juejin.im/entry/5b4953a4e51d4519575a07f1)