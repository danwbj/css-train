# css-train

### 盒子模型
margin-外边距
padding-内填充
border-边框
元素的实际宽度或者高度=左边距+左边框+左填充+右填充+右边框+右边距
块状元素独占一行

### 布局模型
#### 流动模型：
块级元素独占一行，默认宽度100%，自上而下排列
内联元素自左向右依次排列

#### 浮动模型：
float:left;

#### 层模型：
绝对定位
将元素从文档流中拖出来,然后使用left、right、top、bottom属性相对于其最接近的一个具有定位属性的父包含块进行绝对定位,如果不存在这样的包含块，则相对于body元素，即相对于浏览器窗口
position:absolute;

相对定位
在正常文档流中的偏位置
 position:relative;
固定定位
position:fixed;
相对移动的坐标是视图（屏幕内的网页窗口）本身

绝对定位如何相对于一个前辈元素进行移动?
box1为前辈元素（参照元素），box2需要相对于参照元素进行定位
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<title>相对参照元素进行定位</title>
<style type="text/css">
div{border:2px red solid;}
#box3{
    width:200px;
    height:200px;
    position:relative;
           
}
#box4{
    width:99%;
    position:absolute;
    bottom:0px;
    
}
</style>
</head>

<body>
<div id="box1">
	<div id="box2">相对参照元素进行定位</div>
</div>

<h1>将文字当成图片的解说放在图片的下边</h1>
<div id="box3">
    <img src="http://img.mukewang.com/541a7d8a00018cf102000200.jpg">
    <div id="box4">当我还是三年级的学生时是一个害羞的小女生。</div>
</div>
</body>
</html>


### 水平居中的几种情况
1、行内元素文字居中  
text-align:center;
2、定宽、块状
“左右margin”值为“auto”来实现居中的
margin-left:auto;
margin-right:auto;
text-align:center；
或者
margin:40px auto;  //元素居中
text-align:center; //元素中的文字居中
3、不定宽、块状
三种方法实现：
  ● 包在table元素中，再设置table元素左右 margin 居中
table{
    margin:0 auto;
}
  ● 设置为行内元素display:inline;，再使用text-align:center
  ● 通过给父元素设置 float，然后给父元素设置 position:relative 和 left:50%，子元素设置 position:relative 和 left: -50% 来实现水平居中
.wrap{
    float:left;
	position:relative;
	left:50%
}
.wrap-center{
    background:#ccc;
    position:relative;
	left:-50%;
}
<div class="wrap">
    <div class="wrap-center">我们来学习一下这种方法。</div>
</div>

### 重置居中的几种情况
1、父元素高度确定的单行文本
 height:100px;
    line-height:100px;
2、父元素高度确定的多行文本
使用插入 table  (包括tbody、tr、td)标签，同时设置 vertical-align：middle
html代码：
<body>
<table><tbody><tr><td class="wrap">
<div>
    <p>看我是否可以居中。</p>
</div>
</td></tr></tbody></table>
</body>
css代码：
table td{height:500px;background:#ccc}

 td 标签默认情况下就默认设置了 vertical-align 为 middle，所以我们不需要显式地设置了。


浮动会让元素塌陷。即被浮动元素的父元素不具有高度。例如一个父元素包含了浮动元素，它将塌陷具有零高度。此时可以使用clear
