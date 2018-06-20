#面向初学者的jQuery之旅_初识jQuery
##一、实验介绍
###1.1实验内容
- jQuery是什么？是目前应用最广的JAVASCRIPT库，这里的库是广义的概念，是指别人已经封装好的方法和属性，可以直接拿来使用（可以补充jQuery官网上的概念截图，以及GITHUB上的STAR数量）
- 为什么要用到jQuery？在说到为什么要用它之前，先看一下反对的声音，事实上有很多的关于j的争论，甚至有一个youmightnotneedjquery.com的web，它陈列了若干不适用j的原因。在前段开发中我们所遇到的所有需求，都可以不通过j而完成（那当然了，它也仅仅是个库而已），这也许就是它最大的质疑，至于其他的观点和论据，你可以登录到you这个网站上自己看一下。
- 仍然使用j的原因：1、优化了DOM API，接口方法更易用；2、代码更短更简明；3、跨浏览器支持；4、AJAX；5、有很多人使用j，派生出了庞大的社区、教程、以及stackoverflow上面的问题。
- 为什么不用j：1、原生dom api已经优化的足够好了；2、所有j能够实现的，都可以不用它来实现（原生API,以及替代的工具等等），学习它反而是一个负担；3、很多人已经不再使用j。
作者的建议是在理解了DOM之后再使用j，它会让你更好的理解DOM API。


在认识jQuery之前，相信大家对web前端开发三板斧“HTML+CSS+JavaScript”已经有了接触和学习。jQuery是一个简便易用、功能强大、轻量级的JavaScript库，而且它完全开源，支持大多数主流的浏览器，因此对于前端开发者来说是一款JavaScript利器。希望通过这段jQuery之旅，我们能够熟练的掌握jQuery，并且把它运用到前端开发中。
###1.2实验知识点
- jQuery的历史版本
- jQuery的下载
- jQuery的导入
- jQuery的实例
###1.3实验环境
- Xfce终端
- Brackets
- Firefox 网络浏览器
###1.4适合人群
- web前端开发初学者；
- 对HTML/CSS/JAVASCRIPT有初步了解，想要进一步深入了解JavaScript的同学。
- 零基础同学需要在实验楼先修HTML基础教程、CSS速成教程、JavaScript基础这三门教程，以便加深理解。
##二、开发准备
有两种方式在项目中导入jQuery，下载到本地从本地导入以及CDN（网络镜像）导入；
- 在实际开发中，我们一般将jQuery库下载到本地使用，下载jQuery.js有两种方式：1、直接登录网站下载，[jQuery官网](http://jquery.com/download/),选择相应的版本保存；
![](https://i.imgur.com/DjfauPm.jpg)

![](https://i.imgur.com/xHzYj9z.jpg)
- 或者直接在Xfce终端中使用wget命令将jQueyr库下载到当前文件夹下。
```bach
wget https://code.jquery.com/jquery-3.3.1.js
```
- 在浏览器的console测试一下是否导入成功，输入jquery；
- jQuery的版本，目前最新的jQuery版本是3.3.1，历史版本还有1.x,2.x，本教程中使用最新的版本。三个版本内容上区别不大，1.x兼容了一些版本较老的浏览器，比如IE6，7，8等等，而2.x，3.x舍弃了对旧版本浏览器的支持。另外，我们会看到在下载链接中，同一个版本的jQuery会有压缩和未压缩版两个版本,在本教程以及实际开发中我们使用未压缩的版本（200多kb）,压缩版用于产品中（占用空间较小80多kb）。压缩版和未压缩版使用起来是一样的；
## 三、项目文件结构
- 实验用到的jQuery库和html文件一般放置在同一文件夹下；

![](https://i.imgur.com/QTvu998.jpg)

## 四、实验步骤
###4.1新建一个文件夹作为开发环境
打开Xfce终端，用mkdir命令创建一个名为jquery的文件夹，然后进入这个文件夹，用wget命令下载jquery库文件；
```bach 
mkdir jquery
cd jquery
wget https://code.jquery.com/jquery-3.3.1.js
```

打开Brackets，打开我们创建的jquery文件夹，我们会发现下载的jquery库文件已经在文件夹中；
![](https://i.imgur.com/d0zccj3.jpg)

![](https://i.imgur.com/A83xSFf.jpg)

然后新建一个test.html文件；

![](https://i.imgur.com/pelPaW4.jpg)

###4.2创建实验需要的页面
- 本实验中，我们创建3个div元素，设置属性和边框，并按顺序分配ID序号d1,d2,d3作为测试使用。语句如下：

```
<!DOCTYPE HTML>
<html>
<head>
<meta charset=utf-8>
	<style>
            div{
                display:block;
                border:1px solid black;
                width:30%;
                margin:10px;
                text-align:center;
            }
	</style>
</head>
    <body>
        <div id = "d1">
            <h2>ID1</h2>
            <p>Hello I am ID1 div element's text,welcome to the jquery tutorial.</p>  
        </div>
        <div id = "d2">
            <h2>ID2</h2>
            <p>Hello I am ID2 div element's text,welcome to the jquery tutorial.</p>  
        </div>
        <div id = "d3">
            <h2>ID3</h2>
            <p>Hello I am ID3 div element's text,welcome to the jquery tutorial.</p>  
        </div>
        
    </body>
</html>
```

- 用火狐浏览器打开test.html，效果应该是这样子：

![](https://i.imgur.com/FLzPeHI.jpg)

###4.3在HTML中导入jQuery库
- 在我们的页面文档中，导入jQuery库的语句一般在文档的头部head标签中，通过在script标签中注明jQury库的路径实现导入，语句如下：

```
<head>
<meta charset=utf-8>
<style>
div{
display:block;
border:1px solid black;
width:30%;
margin:10px;
text-align:center;}
</style>
/*在head标签中加入jquery库*/
<script src="jquery-3.3.1.js"></script>
</head>
```
###4.4编写你的第一行jQuery代码
在html中，为了保证jQuery函数的执行顺序，需要整个文档（DOM）加载完成以后再使用jQuery库对html的元素进行操作，因此所有的jQuery函数都要封装在文档的ready函数中，以确保执行顺序无误（当然也可以新建立一个后缀为.js的文件，将jQuery函数单独放到js文件中）。几个实例 $('#trigger').click/.css()/.fadeOut/.remove()

然后添加如下代码：

```
$document.ready(function(){
	$("div#d1").css("color","red");
}
```

###4.5在按钮上添加一个jQuery函数
当按钮被按下时，触发click事件中的函数function,在这里我们将id为d2的元素隐藏作为函数内容被触发。

```
<script>
$(document).ready(function(){
$("button#bt1").click(function(){
$("div#d2").css("color","blue");               
})
})
</script>
```
###4.6完整代码

## 六、练习
###6.1 熟悉jQuery的下载方式，将版本为3.3.1的jQuery.js文件下载到本地，并将jQuery库添加到test.html中。
###6.2 在实验步骤4.4基础上修改代码，用jQuery库将id为d3的元素的标题颜色显示修改为绿色。
###6.3 在实验步骤4.5基础上修改代码，用火狐浏览器打开test.html文档，当点击文本框下方的按钮时，弹出一个窗口，文本内容为“warning！”。

## 七、参考链接
[jQuery官方文档](http://api.jquery.com/)