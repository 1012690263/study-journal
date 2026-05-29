# html:

## 认识标签

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
</html>
```

### DOCTYPE

声明不是html标签，是指示web浏览器关于也米娜使用哪个html版本进行编写的指令。

### head

其中的元素可以引用脚本、指示浏览器在哪里找到样式表、提供元信息等。

### title

当把文档加入用户的链接列表或者收藏夹或书签列表时，标题将成为该文档链接的默认名称。

### meta

元信息标签，可提供有关页面的元信息，比如针对搜索引擎和更新频度的描述和关键词

永远位于head内部

语法描述：

```
<meta name="descrption/keywords" content="页面的说明或者关键字">
```

## 标题文字

h1-h6

### 文字对齐

align="对齐方式"

left center right

### 文字字体

```
<font face="字体">引用了该字体的文字</font>
```

例如"黑体"，"楷体''

### 换行

<br>

### 字体颜色

```
<font color="颜色值"></font>
```

### 文字的上标和下标

```html
<sup></sup>
<sub></sub>
```

```html
X<sup>2</sup>+7X<sup>3</sup>-28=0
X<sub>2</sub>+7X<sub>3</sub>-28=0
```

![image-20260125115604910](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260125115604910.png)

### 文字删除线

```
<strike>文字</strike><br
<s>文字</s>
```

### 文字不换行

下方出现滑动块，拖动滑块才可以看到完整的文字

```
<nobr>不需要换行文字</nobr>
```

### 文字加粗

<b>

## 图片的格式

通常有三种

### gif

静态gif和动态gif，是一种压缩位图格式，支持透明背景图像，将多幅图像保存为一个图像文件，从而形成动画

### jpg

全名是jpeg，以24位颜色储存单个位图，是与平台无关的格式，支持最高级别的压缩

### png

设计目的是视图代替gif和TIFF文件格式，同时增加一些gif文件格式所不具备的特性。用来存储灰度图像时灰度图像的深度可多到16位，存储彩色图像时，彩色图像的深度可多到48位。使用从LZ77派生的**无损数据压缩**算法。所占的存储空间稍大。压缩比高，生成文件体积小。

### 添加图片

```
<img src="图片文件地址" width="图片的宽度" height="图片的高度" border="2">
```

### 水平间距和垂直间距

hspace=”水平间距"

vspace="垂直间距"

### 提示文字

鼠标放到图片上有提示

title="提示文字"

### 文字替换图片

图片路径或者下载出现问题，图片没法显示，这时候会在图片位置显示定义的替换文字

alt="提示文字"

## 表格

```html
<table>
    <caption>期末考试成绩单</caption>
    <tr>
        <th>语文</th>
        <th>数学</th>
        <th>英语</th>
    </tr>
    <tr>
        <td>100</td>
        <td>100</td>
        <td>100</td>
    </tr>
</table>
```

th是表格的表头

### 设置边框

```
<table border="参数值"></table>
```

### 设置边框颜色

bordercolor="颜色值"

### 单元格之间的间距

cellspacing="值"

### 单元格内内容和单元格边框间距

cellpadding="值"

### 行的背景颜色

```
<tr bgcolor="值"></tr>
```

### 行内文字的对齐方式

#### 行对齐

```
<tr align="值"></tr>
```

left right center

#### 列对齐

```
<tr vlign="值"></tr>
```

top bottom middle

### 表格背景插入图像

```
<table background="图片地址"></table>
```

### 单元格大小

```
<td width="",height=""></td>
```

### 单元格边框属性

```
<td bordercolor="值"></td>
```

### 合并单元格

colspan,rowspan

```
<td colspan=""></td>
<td rowspan=""></td>
```

### 完整代码

```html
<body>
    <table width="344" border="5" bordercolor="red" cellspacing="10" cellpadding="10">
        <tr>
            <th width="116">班级</th>
            <th width="116">平均分</th>
        </tr>
        <tr>
            <td>1班</td>
            <td rowspan="2">80分</td>
        </tr>
        <tr>
            <td>2班</td>
        </tr>
        <tr>
            <td>3班</td>
            <td>100分</td>
        </tr>
        <tr>
            <td colspan="2" align="center">3班第一</td>
        </tr>
    </table>
</body>
```

![image-20260125132452340](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260125132452340.png)

## 列表

### 无序列表

```html
<ul>
    <li>1</li>
    <li>2</li>
</ul>
```

#### 列表类型

disc:实心圆形

circle:空心圆形

square:实心正方型

### 有序列表

```html
<ol>
    <li>1</li>
    <li>2</li>
</ol>
```

#### 列表类型

type=序号类型

改成字母或者是其他排列方式

start=起始数值

```html
<ol type="A">
</ol>
    <li>沉鱼落雁</li>
	<li>闭月羞花</li>
</ol>
```

```html
<ol start="C">
    <li>及你太美</li>
</ol>
```

### 设置颜色

```
<li><font color="">...</font><li>
```

### 列表嵌套

多于一级层次的列表，一级下面可以存在二级项目、三级项目

```html
<dl>
    <dt>名词一</dt>
    <dd>解释一</dd>
    <dd>解释二</dd>
    <dt>名词二</dt>
    <dd>解释一</dd>
    <dd>解释二</dd>
</dl>
```

## 超链接

### 标签属性

href:指定链接地址

name:给链接命名

title:给链接设置提示文字

targer:指定链接的目标窗口

accesskey：指定链接热键

### 内部链接

#### target属性

_self:在当前页打开链接

_blank:在全新的空白窗口打开链接

_top:在顶层框架打开链接

_parent;在上一层窗口打开链接

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <p>
        <a href="hello.html" target="_self">这是一个链接</a>
    </p>
</body>
</html>
```

### 外部链接

```
<a href="https://www.baidu.com" target="_blank">这是一个链接</a>
```

## html5

### 省略

```html
<select name="" id="">
        <option value="">下面三个selected属性都是代表元素被默认选中</option>
        <option value="" selected="">items01</option>
        <option value="" selected>items02</option>
        <option value="" selected="selected">items03</option>
    </select>
```

```html
<form action="#" method="post">
    <input type="text">
    <input type='text'>
    <input type=text>
</form>
```

### 新的主体结构元素

#### article

```html
<body>
    <article align="center">
       <header>
            <hgroup>
                <h1>article元素</h1>
                <h2>html中的新增的结构元素</h2>
            </hgroup>
       </header>
       <p>
            article元素一般用于文章区块，定义外部内容。
       </p>
        <p>
            article元素表示文档、页面或应用程序中的独立内容，
            例如：博客文章、新闻文章、评论、用户提交的内容等。
        </p>
    </article>
</body>

```

![image-20260126124501342](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260126124501342.png)

#### section

主要用来定义文档中的节（section），比如章节、页眉、页脚或文档中的其他部分。

```html
<body>
    <article align="center">
       <header>
            <hgroup>
                <h1>article元素</h1>
                <h2>html中的新增的结构元素</h2>
            </hgroup>
       </header>
       <p>
            article元素一般用于文章区块，定义外部内容。
       </p>
        <p>
            article元素表示文档、页面或应用程序中的独立内容，
            例如：博客文章、新闻文章、评论、用户提交的内容等。
        </p>
    </article>
    <section align="center">
        <h1>article元素</h1>
        <p>article元素一般用于文章区块，定义外观的内容</p>
    </section>
    <section align="center">
        <h1>section元素</h1>
        <p>section元素一般用于定义文档中的节</p>
    </section>
</body>
```

![image-20260126125002391](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260126125002391.png)

#### nav

用来定义导航栏链接的部分，当链接到本页的某部分或者其他页面

```html
 <body>
    <h1>导航栏</h1>
    <nav>
        <ul>
            <li><a href="">首页</a></li>
            <li><a href="">关于我们</a></li>
            <li><a href="">联系我们</a></li>
        </ul>
    </nav>
    <header>
        <h2>nav元素</h2>
        <ul>
            <li><a href="">HTML</a></li>
            <li><a href="">CSS</a></li>
            <li><a href="">JavaScript</a></li>
        </ul>
    </header>
</body>
```

![image-20260126125512228](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260126125512228.png)

#### aside

定义article以外的、用于成节的内容，也可以用于表达注记、侧栏。

```html
    <article>
        <h1>html5aside元素</h1>
        <p>正文部分</p>
        <aside>
            正文部分的附属信息成分。其中的内容可以是与当前文章有关的相关资料，名词解释，等等。
        </aside>
    </article>
```

![image-20260126125827674](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260126125827674.png)

#### time

```html
<p>现在时间是<time>12:59</time>.</p>
<p>今天是<time datetime="2026-01-26">你的生日</time>，祝你生日快乐</p>
```

![image-20260126130146062](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260126130146062.png)

### 新的非主体元素结构

#### header

是一种具有引导和导航作用的辅助元素，通常代表一组简介或者导航性质的内容

```html
<header>
	<h1>
        这是页面的标题
    </h1>
</header>
<article>
	<h2>
        这是第一章
    </h2>
    <p>
        这是正文部分
    </p>
    <header>
    	<h2>
        	第二个header标签
        </h2>
        <p>
            因为html文档不会对header标签进行限制，所以我们可以创建多个header标签
        </p>
    </header>
</article>
```

![image-20260126130650708](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260126130650708.png)

#### hgroup

目的是将不同层级的标题封装成一组

一个标题可以省略hgroup，header子元素只有hgroup可以省略header

```html
<header>
    <hgroup>
        <h1>
            html5 group元素
        </h1>
        <h2>
            hgroup的使用方法
        </h2>
    </hgroup>
</header>
```

#### footer

之前是习惯于用<div id="footer">来定义页脚部分。

包含文档作者，版权信息，使用条款链接、联系信息等。

可以在文档中使用多个<footer>元素

```html
<footer>
    <ul>
        <li>关于我们</li>
        <li>联系我们</li>
        <li>隐私政策</li>
        <li>条款与条件</li>
        <li>版权所有</li>
        
    </ul>
</footer>
```

![image-20260126131218112](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260126131218112.png)

在section元素中加注脚

```html
<section>
    <h1>
        段落标题
    </h1>
    <p>
        正文部分
    </p>
    <footer>本段注脚</footer>
</section>
```

![image-20260126131347968](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260126131347968.png)

### 使用video元素添加视频

和audio使用方法一样

```html
<body>
    <video width="640" height="360" controls>
        <source src="及你太美.mp4" type="video/mp4">
        <source src="及你太美.ogg" type="video/ogg">你的浏览器不支持video标签
    </video>
</body>
```

## 表单

### action

真正处理表单的数据脚本或程序在action里，这个值可以是程序或者脚本的一个完整url

```
<!-- 一个没有控件的表单 -->
<form action="mail:1012690263@qq.com">
</form>
```

### name

不是必须属性，为了防止表单提交到后台处理程序时出现混乱

```
<form action="mail:1012690263@qq.com" name='register'>
</form>
```

### method

传送方法

#### get

使用这个设置时，表单数据会被视为CGI或者ASP的参数发送，也就是来访者输入的数据会附加url之后，由用户端直接发送至服务器，速度上比post更快，但是数据不能太长，没指定的情况下是默认get

#### post

表单数据和url是分开发送的，用户端的计算机会通知服务器来读取数据，所以通常没有数据长度上的限制，缺点是速度上会比get慢

### enctype

取值如下：

text/plain：以纯文本的方式传送

application/x-www-form-urlencoded:默认的编码形式

multipart/form-date:MIME, 上传文件的表单必须选择该项

### target

指定目标窗口的打开方式要用到target属性

```
_blank
_parent
_self
_top
```

## 表单的控件

### input

```
<input name="" type="">
```

type取值如下：

text:文字字段

password：密码域

radio：单选按钮

checkbox：复选框

button：普通按钮

submit：提交按钮

reset：重置按钮

image：图形域，也称图像提交按钮

hidden：隐藏域，不显示在页面上，只将内容传递到服务器中

file：文件域

#### text&password：

```
<form action="from_action.asp" method="get" name="form2">
        用户：
        <input type="text" name="name" size="10">
        <br><br>
        密码：
        <input type="password" name="pwd" size="10">
    </form>
```

#### radio:

```
 <input type="radio" name="anniu1" value="值1" >
 <input type="radio" name="anniu2" value="值2" checked="checked">
```

![image-20260126145919243](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260126145919243.png)

#### checkbox：

```
<input type="checkbox" name="fuxuankuang1" value="1" checked="checked">
<input type="checkbox" name="fuxuankuang2" value="2" >
<input type="checkbox" name="fuxuankuang3" value="3" >
```

![image-20260126150059741](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260126150059741.png)

## 表单按钮：

### button

```
<button name="" type="button" value="" onclick="处理程序">
```

```
<input type="checkbox" name="fuxuankuang1" value="1" checked="checked">
<input type="checkbox" name="fuxuankuang2" value="2" >
<input type="checkbox" name="fuxuankuang3" value="3" >
```

### 提交按钮submit

```
<input name="button2" type="submit" value="提交">
```

### 重置按钮reset

```
<input name="button3" type="reset" value="重置">
```

文件域名file

```
    <form action="" method="post" name="form2" enctype="multipart/form-data">
        <input name='button' type="button" value="点击试试" onclick="window.close()">
        <input name="button2" type="submit" value="提交">
        <input name="button3" type="reset" value="重置">

        用户名：
        <br>
        <input name="name" type="text" size="10">
        <br>
        密码：
        <br>
        <input name="pwd" type="password" size="10" maxlength="10">
        <br>
        上传照片：
        <br>
        <input name="file" type="file" size="25" maxlength="30">

    </form>
    
```

### 文本域标签textarea

```html
<textarea name="" cols="" rows="" wrap="换行方式">
    文本内容
</textarea>
```

```
 <textarea name="textarea2" rows="10" cols="40" wrap="virtual">
            及你太美须知：
            及你太美
            及你太美
            及你没
 </textarea>
```

![image-20260126161628963](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260126161628963.png)

## 表单定义标签：

### 使用label定义标签

用户选择label元素生成的标签时，浏览器会自动将焦点转移到和标签相关联的表单控件元素上。

绑定的是id，不是name

```
<h3>请点击文本标记之一，就可以出发相关控件：</h3>
    <form>
        <label for="male">姓名</label>
        <input type="text" name="sex" id="male">
        <br>
        <label for="famale">密码</label>
        <input type="password" name="sex" id="famale">
    </form>
```

![image-20260127164122519](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260127164122519.png)

### 使用button定义按钮

```html
<form action="" method="get" name="form2">
        用户名：
        <br>
        <label>
            <input name="name" type="text" size="10">
        </label>
        <br>
        密码：
        <br>
        <label>
            <input name="mima"  type="password" size="10" maxlength="10">
            <br>
            <button type="submit"><img src="meinv.jpg"></button>
        </label>
    </form>
```

按钮的内容是个图片当作按钮

### 列表、表单的设置

属性：

```
name:菜单和列表的名称
size:显示的选项数目
multiple:列表中的项目多项
value:选项值
selected：默认选项
```



```html
<select multiple size="">
    <option value="值" selected="selected"></option>
</select>
```

![image-20260127165226417](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260127165226417.png)

size越大显示越多，否则拉滑轮看见

## html5新

<input type="text" require>

<input type="number" min="1" max="10"/>

<input type="email"/>

### 输入型控件：

#### emial:

<input type="email" name="image_url">

#### url:

<inpupt type="url" name="user_url">

#### number:

<input type="number" name="points" max="10" min="1">

#### range:

<input type="range" name="range" value="20" min="2" max="100" step="5">滑动条

![image-20260127165932207](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260127165932207.png)

#### Date Pickers（日期选择器）:

data

month

week

time

datetime

datetime-local

#### search：

#### color:

让用户在浏览器中直接使用拾色器找到自己想要的颜色选择器

![image-20260127170243877](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260127170243877.png)

### 日期制作

```
<form action="" method="get">
        <label>到达日期：</label>
        <input type="date" id="arrial_dt" name="arrival_dt" required>
</form>
```

![image-20260127174804933](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260127174804933.png)

限制数字范围

```html
<form action="" method="get">
        <label for="nights">住宿天数：</label><br>
        <input type="number" id="nights" name="nights" value="1" min="1" max="30" required><br>
        <label>住宿人数：</label><br>
        <input type="number" id="guests" name="guests" value="1" min="1" max="4" required><br>
</form>
```



## 表单新元素

### datalist：

与input配合使用，用来定义input可能的值

```
	<input list="cars">
    <datalist id="cars">
        <option value="Audi">
        <option value="BMW">
        <option value="Mercedes">
        <option value="Volvo">
    </datalist>
```

![image-20260127181853764](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260127181853764.png)

### keygen：

规定表单的密钥对生成器字段，提交表单时，私钥存储在本地，公钥发送到服务器。

可以提高验证时的安全性

是跨越浏览器实现的，实现起来非常容易

同时如果是作为客户端证书来使用，可以提高对MIMT攻击的防御力度

```html
<form action="" method="get">
        username:<input type="text" name="username" id="username">
        encryption:<keygen name="security" />
        <input type="submit" value="提交">
</form>
```

### output：

定义不同类型的输，比如脚本的输出

换成id="x"也行，或者name="a"啥的都行

```html
<form  oninput="x.value=parseInt(a.value)+parseInt(b.value)">0
        <input type="range" id="a" value="50">100
        +<input type="number" id="b" value="50">
        =<output name="x" for="a b"></output>
</form>
```

![](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260127205308492.png)

![image-20260127205520608](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260127205520608.png)

## 表单新属性

### form属性

html4中的表单内的从属元素必须写在表单内部，但是在html5中，可以写在任何位置，然后给元素指定一个form属性，属性值为改表单单位的id

```html
<form action="" id="myform">
    <input type="text" name="">
</form>
<input type="submit" form="myform" value="提交">
```

### formaction属性

html4中，一个表单的所有元素只能通过表单的action属性统一提交到里一个页面，而在html5中可以给所有的按钮提交

```html
<form aciton="" id="myform">
    <input type="text" name="">
    <input type="submit" value="" formaction="a.php">
    <input type="image" src="img/logo.png" formaction="b.php">
    <button type="submit" formaction="c.php">
    </button>
</form>
```

### autofocus属性

用于指定input在网页加载后自动获得焦点

```
<form action="" id="myform">
        <input type="text" autofocus>
</form>
```



### novalidate属性：

新版本浏览器会对email、number等语义iinput做验证，有的会验证失败信息，有的则不提示失败信息只是不提交。增加novalidate，则提交表时的进行的有关检查会被取消，表单将无条件提交

```html
    <form action="" novalidate>
        <input type="text">
        <input type="email">
        <input type="number">
        <input type="submit" value="提交">
    </form>
```

### required属性：

可以对input元素与textarea元素指定required属性。该属性表示在用户提交时进行检查，检查该元素内一定要有输入内容。

```
<form action="" novalidate>
        <input type="text" name="username" required>
        <input type="password" name="password" required>
        <input type="submit" value="提交">
    </form>
```

### autofomplete属性：

用来保护敏感用户数据，避免浏览器对他们进行不安全的存储。可以设置input在输入时是否显示之前的输入项。

```html
<input type="text" name="username" autocomplete>
```

autocomplere属性值如下：

on,该字段不受保护，值可以被保存和回复

off,

不指定则使用浏览器默认值

### min和max：

是数值类型或日期类型input元素的专用属性

### step：

控制增减时的步幅

### pattern：

通过一个正则表达式来验证输入内容

```html
<input type="text" required pattern="[0-9][a-zA-Z]{5}"
```



## 输入占位符：

就是为了提示用户该单位框中应该输入的内容

```html
<form>
    <input type="text" name="username" placeholder="请输入用户名">
</form>
```

表示必须以一个数字开头，后面跟五个大小写不限的字母

### multiple：

允许输入域中选择多个值，常用于file类型

```
<input type="file" multiple>
```

本来file只能选择一个文件，加上之后可以选择多个

# CSS选择器：

控制页面样式与布局并允许央视信息与网页内容相分离

优点：简化代码。修改样式只需修改css代码

html:

<body bgcolor="black"></body>

css:

body{

background-color:#ccc;

}

## 基本语法：

选择器{属性名：属性值}，select{properties：values；}

## css引入方法：

### 1.内联引入：

```
<p style="color:red;"></p>
```

### 2.内部引入：

```
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        p{
            color:red;
            font-size: 20px;
        }
        div{
            color:blue;
            font-size: 40px;
        }
    </style>
</head>
<body>
    <p>日照香炉生紫烟，遥看瀑布挂前川。</p>
    <div>飞流直下三千尺，疑是银河落九天</div>
</body>
```

### 3.外部引入：

在文档外部创建.css样式表

在html文档的<head>部分以<link type="text/css" rel="stylesheet" href="url">

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="css引入.css">
</head>
<body>
    <p>测试</p>
</body>
</html>
```

## 三大选择器：

### 元素选择器

```html
<style>
    p{
        color:red;
        font-size:20px;
    }
    a{
        text-decoraction:none;
    }
</style>
```



### 类选择器

```html
<p class="mytxt">test1</p>
<style>
    .mytxt{
        text-align:center;
    }
</style>
```

```html
<body>
    <p class="mytxt">这是一个段落</p>
    <p class="mytxt"><a class="mytxt mya" href="#">文字</a></p>
<style>
    .mytxt{
        text-align:center;
        font-size: 50px;
    }
    .mya{
        text-decoration: none;
    }
</style>
```

![image-20260128170717838](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260128170717838.png)

把a自带的下滑线去掉

### id选择器



```
<p id="mytxt2">这是一个段落</p>
```

```html
<style>
	#mytxt2{
        font-size: 30px;
    }
</style>
```

### 集体选择器

所有元素使用同一个样式

```html
<style>
    li,.mytxt,span,a{
        font-size:20px;
        color:red;
    }
</style>
```

### 属性选择器：

可以根据元素的属性和属性值来选择元素

包含标题（title）的所有元素变为红色

```
*[title]{color:red;}
```

只对有href属性的a应用样式

```
a[href]{color:red;}
```

将同时具有title和href的超链接文本应用样式

```
a[href][title]{color:red}
```

```html
<style>
    img[alt]{
        border:3px solid red;
    }
    img[alt]{
        border:3px solid blue;
    }
</style>

<body>
    <img src="img.png" alt="" width="300">
    <img src="img.png" alt="image" width="300">
</body>
```

### 后代选择器

可以选择某元素作为后代元素

**根据上下文选择元素**：可以定义后代选择器创建一些规则，使这些规则在某些文档结构中起作用，而在另外一些结构中不起作用

举例来说，如果希望对h1元素中的em元素应用样式

```
h1 em{color:red;}
```

这个规则会把作为h1后代的em元素的文本变为红色，其他em文本则不会被这个规则选中

```html
<h1>
    this is a <em>important</em> heading
</h1>
<p>
    this is a <em>important</em> paragraph.
</p>
```

![image-20260128182013454](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260128182013454.png)

```css
div.sidebar {background:blue;}
div.maincontent {background:white;}
div.sidebar a:link {color:white;}
div.maincontent a:link{color:blue;}
```

### 子元素选择器：

之选下一代而不包括后续后代

```
   <style>
        h1 em{
            color:red;
        }
    </style>
</head>
<body>
    <h1>
    this is a <em>important</em> heading
    </h1>
    <p>
    this is a <em>important</em> paragraph.
    </p>
</body>
```



### 相邻兄弟选择器：

中间不能空格

```
<style>
        li+li {color:red;}
    </style>
</head>
<body>
    <ul>
        <li>111</li>
        <li>222</li>
        <li>333</li>
    </ul>
    <ol>
        <li>111</li>
        <li>222</li>
        <li>333</li>
    </ol>
```

![image-20260307155135407](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260307155135407.png)



### 选择器结合使用：

```
<style>
        html>body div+span,html>body hr+ul li{
            color:red;
            border:red solid 2px;
        }
    </style>
</head>
<body>
    <div>一个容器</div>
    <span>一个span容器</span>
    <hr>
    <ul>
        <li>111</li>
        <li>222</li>
        <li>333</li>
    </ul>
```

![image-20260307155622423](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260307155622423.png)

### 伪类：

selector:pseudo-class{property:value}

selector.class:psudo-class {property:value}

#### anchor伪类：

顺序不能改的

```
a:link{color:#FF0000;}未访问的链接
a:visited{color:#00FF00;}已访问的链接
a:hover{color:#FF00FF;}鼠标划过的链接
a:active{color:#0000FF;}已经点过的链接
```

#### 伪类和css类：

a.red:visited {color:#FF0000}

```
<a class="red" hred="#">CSS</a>
```

#### first-child伪类：

字面意思

 ul li:first-child{

​      color:red;

​    }

#### lang伪类：

![image-20260307161542690](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260307161542690.png)

### 伪元素：

selector.class:pseudo-element {property:value}

#### first-line

页面展示的第一行，放大页面会影响

<style>
        p:first-line{
            color:red;
        }
    </style>

#### first-letter:

首字母特殊格式

p:first-letter{

​      color:green;

​      font-size: 30px;

​    }

只能用于块级元素

下面属性可以用

font properties

color

background

margin

padding

border

text-decoraction

vertical-align

text-transform

line=height

float

clear

#### 伪元素和css类：

p.article:first-letter{color:#ff0000;}

```
<p class="article">111111111</p>
```

#### before伪元素：

在前面插入文字或者图片

<style>
        div:before{
            content:url("test.jpg");
        }
    </style>

<style>
        div:before{
            content:"这是一个段落:";
        }
    </style>

![image-20260307163047706](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260307163047706.png)

#### after伪元素：

与before相反

### css的继承和单位

比如

body{

}

会影响包含的元素

#### 设置字体边框

父级加了border属性，不会继承到子元素

div{

​	border:2px solid red;

}

```
<div>1111<em>222</em>11</div>
```

需要再去写子级的

当父级和子级产生矛盾时，子级遵循自己的

#### css绝对数值单位

像素：px

毫米：mm

厘米：cm

英尺：in（1 in=96px=2.54cm）

点：pt （point，1 point=1/72in）

#### css相对数值单位：

em：描述应用在当前元素的字体尺寸，一般浏览器字体大小默认16px，1 em=16px

ex：依赖于英文字母小x的高度

ch：数字0的宽度

rem：根元素html的font-size

vw：视窗宽度，1vm=视窗宽度的百分之一

vh:视窗高度

vmin：vh和vw中较小的那个

vmax：较大的那个



## css定位效果

div和h1或p元素常常被称为块级元素

意味着这些元素显示为一块内容，即块框

与之相反，span和strong等元素称为行内元素。

span和strong元素

### 制作图片浮动效果



```
<style>
        img{
            float:right;
        }
    </style>
</head>
<body>
    <p>
        <img src="test.jpg" alt="">
        这是一个段落,afsdfasdjfkladsfjlaksdfjlsdakfjlasdjflkdsfjlsadfjlaksjfasldkf
    </p>
```

### 定位属性：

position属性如下

absolute：生成绝对定位的元素，相对于static定位以外的第一个父元素进行定位，通过left top right bottom属性规定

fixed：left top fight bottom

relative：相对于其正常位置进行定位。left：20会向元素left位置添加20像素

static：默认值，出现在正常流中，忽略top，bottom等

#### 绝对定位：

```
<style>
        div{
            width:400px;
            height:200px;
        }
        .d1{
            background:pink;
        }
        .d2{
            background:lightblue;
        }
        .d3{
            background:lightgreen;
        }
    </style>
</head>
<body>
    <div class="d1"></div>
    <div class="d2"></div>
    <div class="d3"></div>
```

![image-20260308100004604](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260308100004604.png)

.d2{

​      background:lightblue;

​      position:absolute;

​    }

第三个被第二个挡住，对第二个使用绝对定位之后就会使第二个div完全脱离当前的文档流，在页面中形成一个虚拟的z轴，所占的物理空间也会空出来，被第三个补上。

![image-20260308100027955](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260308100027955.png)

 .d2{

​      background:lightblue;

​      position:absolute;

​      left: 100px;

​      top:300px;

​    }

![image-20260308100230099](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260308100230099.png)

#### 相对定位：

```
<style>
        div{
            width:200px;
            height:200px;
        }
        .d1{
            background:pink;
        }
        .d2{
            background:lightblue;
            position:relative;
            left:100px;
            top:100px;
        }
        .d3{
            background:lightgreen;
        }
    </style>
</head>
<body>
     <div class="d1"></div>
     <div class="d2"></div>
     <div class="d3"></div>
```

![image-20260308100806928](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260308100806928.png)

#### 固定定位：

类似于将position设置为absolute。但把元素固定在浏览器窗口的某一位置，而且不会随着文档的其他元素进行移动，例如购物网站侧栏。

```
<style>
        body{
            height:2000px;

        }
        .d1{
            width:200px;
            height:200px;
            background:pink;
            position:fixed;
            bottom:100px;
            right:100px;
        }
    </style>
</head>
<body>
    <div class="d1"></div>
```

![image-20260308101802436](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260308101802436.png)

### z轴索引优先级

无论是固定、相对、绝对定位都会对页面其他元素遮挡。

z-index属性设置元素的堆叠顺序。更高的堆叠顺序的元素总是处于堆叠顺序较低元素前面。可为负。

属性可有一下几种：

Auto：默认，堆叠顺序与父元素相等。

Number：设置元素的堆叠顺序

Inherit：规定应该从父元素继承z-index属性的值。

#### 设置z轴索引的优先级：

```
<style>
        body{
            height:2000px;
        }
        div{
            width:200px;
            height:200px;

        }
        .d1{
            background:pink;
        }
        .d2{
            background:lightblue;
            position:absolute;
            left: 100px;
            top: 100px;
        }
        .d3{
            background:lightgreen;
        }
    </style>
</head>
<body>
    <div class="d1"></div>
    <div class="d2"></div>
    <div class="d3"></div>
    
```

![image-20260308103010256](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260308103010256.png)

.d2{

​      background:lightblue;

​      position:absolute;

​      left: 100px;

​      top: 100px;

​      z-index: -1;

​    }

![image-20260308103120101](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260308103120101.png)

## 网页常用样式

### 字体样式：

#### 字体font-family：

通用字体，拥有相似外观的字体系统组合

如："Serif","Monospace"

特定字体，特定的~

如"Times","Courier"

多个系列字体用逗号隔开

p{font-family：”Times New Roman”,Times,serif}

如果汉字名称超过一个字就得用引号，比如“宋体”

#### 字号font-size：

属性值包括：

像素px

点数pt

英寸in，厘米cm，毫米mm

倍数em，当前文本的大小

百分比，当前文本的百分比定义大小

#### 字重font-weight：

用于字体加粗

两种写法

由100~900，只能写整百的数

可以是关键字，normal，bold，bolder，lighter，inherit

#### 文本转换text-transform

属性值如下：

none默认。定义带有大小写字母的标准文本

capitalize：每个单词以大写字母开头

uppercase：定义仅有大写

lowercase：仅小写

inherit：从父元素继承

#### 字体风格font-style：

值如下：

normal

italic：斜体

oblique：斜体显示

inherit

#### 字体颜色color：

值如下：

color_name:颜色名称

hex_number：十六进制值,如#ff0000

rgb_number：rgb代码，如(rgb(255,0,0))

inherit

#### 文本修饰text-decoration：

none

underline：下划线

overline：上划线

line-through：穿过文本

blink：闪烁文本

inherit：

#### 简写font：

font-style

font-variant

font-size/line-height

font-family

#### 简写font效果

![image-20260308110116068](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260308110116068.png)

## 段落样式：

### 字符间隔letter-spacing

normal

length字符间固定空间，允许使用负值，会让字母更加拥挤。

inherit

### 单词间隔word-spacing

nomal

length

inherit

### 段落缩进text-indent

length：固定缩进，默认为0

%定义基于父元素的百分比的缩进

inherit

### 横向对齐方式text-align

left

right

cent

justify实现两端对齐

inherit

### 纵向对齐方式vertical-align

baseline：元素放置在父元素的基线上

sub：垂直对其文本的下标

top：把元素的顶端与行中最高元素的顶端对齐

text-top：把元素的顶端与父元素字体的顶端对齐

middle：把此元素放置在父元素的中部

bottom：把元素的顶端与行中最低的元素的顶端对齐

text-bottom：把元素的底端与父元素字体的底端对齐

length：使用line-height属性的百分比值来排列此元素，允许使用负值

inherit规定应该从父元素vertical-align属性的值

```
 .top{
            vertical-align: top;
            
        }
        .bottom{
            vertical-align: bottom;
        }
        .middle{
            vertical-align: middle;
        }
    </style>
</head>
<body>
    <p>这是一幅位于<img src="test.jpg" alt="" class="top">文本中的图像</p>
    <hr>
    <p>这是一幅位于<img src="test.jpg" alt="" class="bottom">文本中的图像</p>
    <hr>
    <p>这是一幅位于<img src="test.jpg" alt="" class="middle">文本中的图像</p>
</body>
```

### 文本行间距line-height：

normal

number：会与当前字体的尺寸相乘来设置行距

length：固定行间距

%：基于当前字体尺寸的百分比设置行间距

inherit

## 边框样式

### 边框线型border-style

border-style：dotted solid double dashed

上边框点状 有边框实线，下边框是双线，左边框是虚线

border-style:dotted solid double;

上点，右左都是实线，下边框是双线

border-style：dotted solid

上下都是点，左右都是点

属性值：

none

hidden

dotted

dashed

solid

double

groove：3D凹槽边框

ridge：3D垄状边框，效果取决于border-color的值

inset：3Dinset边框

ouset

inherit

### 边框颜色border-color

border-color：red green blue pink；上右下左

color_name

hex_number

rgb_number

transparent:默认值，边框颜色为透明

inherit

### 边框宽度border-width

border-width:thin medium thick 10px;

thin

medium:默认

thick

length

inherit

### 制作边框效果

border-width

border-style

border-color

```
    <style>
        .border1{
            width:500px;
            height:200px;
            border-width:20px 10px 15px 5px;
            border-style:solid dashed dotted;
            border-color:red #00ff00 rgb(0,0,255);
        }
        .border2{
            width:500px;
            height:200px;
            border:solid green 10px;
        }
    </style>
</head>
<body>
    <div class="border1"></div>
    <div class="border2"></div>
</body>
```

## 外轮廓样式

位于边框边缘的外围，可起到突出元素的作用，不会占据空间，也不一定是矩形

### 轮廓线型outline-style

none：默认，定义无轮廓

dotted

dashed

solid

double

groove

ridge

inset

outset

inherit

### 轮廓颜色outline-color：

color_name

hex_number

rgb_number

invert：默认，执行颜色反转（逆向的颜色）可使轮廓在不同的背景颜色都可见

inherit

### 轮廓宽度outline-width

thin：细轮廓

medium：默认

thick：规定粗的轮廓

length：允许规定轮廓粗细的值

inherit：

### outline简写

可以按顺序设置如下属性

outline-width

outline-style

outline-color

### 边框与外轮廓的异点

ouline不占空间，border会增加盒子宽高

ouline不能上下左右单独设置，border可以

border几乎可用于所有有形html元素，outline针对链接、表单控件和imagemap等元素

outline的效果随着元素的focus而自动出现，相应的由blur而自动消失

outline和border同时存在，outline会围绕在border的外围

```
<style>
        .div{
            width:200px;
            height:200px;
            margin:20px auto;
            border-width:20px,10px,15px,5px;
            border-color:red green yellow blue;
            border-style:solid dashed dotted;
            outline-width:10px;
            outline-style: solid;
            outline-color: pink;
        }
    </style>
</head>
<body>
    <div class="div"></div>
```

![image-20260308193804529](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260308193804529.png)

## 列表相关属性

### 列表样式list-style-type

不管是有序列表或无序列表，都统一使用来定义元素样式

none无标记

disc默认。标记是实心圆

circle标记是空心圆

square实心方块

decimal数字

decimal-leading-zero0开头的数字标记

lower-roman

upper-roman大写罗马

lower-alpha小写英文字母

lower-greek小写希腊字母

lower-latin小写拉丁字母

hebrew

georgian

cjk-ideographic

hiragana

katakana

hiragana-iroha

### 使用css制作列表样式

```
 .u1{
            list-style-type: decimal-leading-zero;
        }
        .o1{
            list-style-type: lower-roman;
        }
        .u2{
            list-style-type: upper-alpha;
        }
        .o2{
            list-style-type: hebrew;
        }
```

### 列表标记的图像list-sytle-image

使用图像来替换列表项的标记

list-style-image:url();

### 列表标记的位置list-style-position

inside 列表项目标记放在文本以内，且环绕文本根据标记对齐

outside默认值，保持标记位于文本的左侧

inherit

### 列表属性简写格式list-style

list-style-type

list-style-position

list-style-image

initial默认值

inherit

## 盒子模型

属性：内容content 填充padding 边框border 边界margin

### 外边框设置

margin：10px,5px,15px,20px;

<style>
        div{
            width:200px;
            height:100px;
            border:2px green solid;
            background-color:#9C6;
        }
        .d2{
            margin-top:20px;
            margin-right:auto;
            margin-bottom:40px;
            margin-left:10px;
        }#简写为margin:top right bottom left;
    </style>

### 外边距合并

当两个垂直外边距相遇时，他们将形成一个外边距。合并后的外边距的高度等于两个发生合并的外边距的高度中的较大者

### 内边距设置

padding 接受长度和百分比值，不能为负

h1{

padding:10px;

}

h2{

padding:10px, 0.25em,2ex,20%;

}

p{

padding:10%;}

```
<div style="width:200px"><p>...</p></div>
```

内边距要跟节目div的width计算



## 弹性盒子

由弹性容器（flex container）和弹性盒子元素（flex item）组成

传统div+css布局方案依赖于盒子模型，基于display属性，如果还需要的话还会用上position属性和float属性。

新方案：flex

布局以后，子元素的float、clear和vertical-align属性失效

### 对父级容器的设置

#### flex-direction

row默认值。水平显示

row-reverse相反顺序

column垂直显示

column-reverse

initial设置该属性为它的默认值

inherit

```
.container{
            width:1200px;
            height:200px;
            border:5px solid green;
        }
        .content{
            width:100px;
            height:100px;
            background: lightpink;
            color: #fff;
            font-size: 50px;
            text-align: center;
            line-height: 100px;
        }
```

#### justify-content

flex-start默认值，项目位于容器开头

flex-end位于容器结尾

center位于容器中心

space-between位于各行之间留有空白的容器内

space-around：位于各行之前，之间，之后都留有空白的容器内

initial

inherit

#### align-items

设置或检索盒子在纵轴方向上的对齐方式

flex-start从纵轴起始位置紧靠纵轴起始边界

flex-end紧靠结束边界

center居中放置

baseline当行内轴与侧轴为同一条时，与start等效，其他情况下将参与基线对齐

stretch指定侧轴大小属性值为auto，则其值会使项目的边距盒尺寸尽可能接近所在行的尺寸

#### flex-wrap

规定容器时单行或者多行，同时横轴的方向决定了新行堆叠的方向

nowrap默认，弹性容器为单行，可能会溢出

wrap多行，溢出放到新行

wrap-reverse反转排列

#### align-content

stretch：默认，各行会伸展占用剩余空间

flex-start：各行像起始位置堆叠

flex-end

center像中间堆叠

### 对子级内容的设置

#### flex

用于设置或检索盒子的子元素如何分配空间

flex-grow相对于其他项目扩展的量

flex-shrink相对于其他灵活项目收缩的量

flex-basis项目的长度

auto

none

initial

inherit

```
.container{
            width: 500px;
            height:500px;
            border:5px green solid;
            display: flex;
            flex-wrap: wrap;
        }
        .content{
            height:100%;
            background:lightpink;
            color:#fff;
            font-size: 50px;
            text-align: center;
            line-height: 100px;
            flex:1;
        }
        .c2{
            background:lightblue;
        }
        .c3{
            background:lightgreen;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="content">1</div>
        <div class="content c2">2</div>
        <div class="content c3">3</div>
        <div class="content">4</div>
        <div class="content">5</div>
        <div class="content">6</div>
        <div class="content">7</div>
        <div class="content">8</div>
        <div class="content">9</div>
        <div class="content">10</div>
```



![image-20260308210010253](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260308210010253.png)

#### order

设置或检索弹性盒模型对象的子元素出现的顺序

number默认为0

initial

inherit

# javascript

特点：

脚本语言，解释型。在程序运行过程中逐行编译

基于对象，不仅可以创建对象，也能使用现有

简单

动态性，采用事件驱动

跨平台性，不依赖于操作系统，仅需要浏览器支持

不同于服务器端脚本语言，例如php和asp，js主要被作为客户端语言，不需要服务器支持

特殊功能AJAX必须依赖js在客户端支持。随着引擎（如v8）和框架（node.js)

的发展，以及事件驱动及异步IO等特性，js逐渐被用来写服务器端程序



## JavaScript用法：

### head中的js：

```
<script>
        function myfun(){
            document.getElementById("demo").innerHTML="我的第一个js函数";
        }
    </script>
</head>
<body>
    <h1>我的web页面</h1>
    <p id="demo">一个段落</p>
    <button type="button" onclick="myfun()">点击我</button>
</body>
```

![image-20260309095322006](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260309095322006.png)

![image-20260309095331546](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260309095331546.png)

### 外部的js

<script src="外部js.js"></script>

## js函数定义：

fuction name(){

}

function myfun(){

alert("hello");

}

<button onclik="myfun()"></button>

### 调用带参数的函数

myfuction(arg1,arg2){

}

### 带有返回值的函数

fuction myfun(){

var x=5;

return x;

}

var myvar=myfun();

fuction myfun(a,b){

if(a>b)

{

return a_b;

}

x=a+b;

}

### javascript函数参数：

#### 默认参数

function myfun(x,y){

if (y===undefined){

y-0;

}

return x*y;

}

document.getElementById("demo").innerHTML=myfun(4);

function myfun(x,y){

y=y||0;

}

#### arguments对象

通过值传递参数

var x=1;

function myfun(x){

x++;

console.log(x);

}

myfun(x);

console.log(x);//1

通过对象传递参数

因此在函数内部修改对象的属性就会修改其初始的值，修改对象属性可作用于函数外部（全局变量）。

var obj={x:1}

function myfun(obj){

obj.x++;

console.log(obj.x);

}

myfun(obj);

console.log(obj.x);//2

### js函数调用

#### 函数模式

function foo(){};

var func=function(){};

foo();

func();

(functon(){})();

#### 方法模式

function f(){

this.method=function(){};

}

var o={

method:function(){}

}

this的含义是这个依附的对象

#### 构造器模式

由于构造函数只是给this添加成员，没有做其他事情，而方法模式也能完成 这个操作，就this而言，两者没有本质区别

特征：

使用new关键字，来引导构造函数

构造函数中this与方法模式中一样，但是构造函数的对象是刚建立的

构造函数中不需要return，默认返回return this

手动添加return 基本类型，无效，保留返回原来的this

手动return null 和undefiend无效

手动添加return对象类型：原来的this就会丢掉

### 上下文模式

上下文就是环境，就是自定义设置this的含义

函数名.apply（对象，[参数]);

函数名.call(对象，参数)

函数名就是表示函数本身，使用函数进行调用的时候默认this是全局变量。

函数名也可以是方法提供的，使用方法调用的时候，this是指当前对象。

使用apply进行调用后，无论是函数还是方法都无效了。this由apply的第一个参数决定

## js基本用法

### 数据类型

简单数据类型：undefined，null，var，boolean,string,number

undefined，只有一个值，在使用var声明变量但未初始化时

Null，表示值是一个空对象指针，也正是typeof操作符检测null时会返回object的原因

```
var car=null;

alert(typeof car)；//object

如果定义的变量准备保存于对象，最好初始化为null而不是其他，检测null就可以知道相应的变量是否保存了一个对象的引用了

if(car!=null){

}

alert(undefined==null);//true
```

boolean

```
true和false，与数值不是一回事，不一定能相等
var message='hello world';
var messageAsboolean=Boolean(message);
```

number

```
用来表示整数和浮点数值，还有一种特殊的数值，即NaN，非数值

这样就不会报错，不会影响其他代码执行

任何涉及到nan的操作都会返回nan

aler（NaN==NaN);//false

alert(isNaN(NaN));true

alert(isNaN("10"))false

alert(isNaN("blue"))true

alert(isNaN(true))false
```

```
有三个函数可以把非数值转化为数值：Number()
parseInt()
parseFloat()
```



string类型

用于表示零个或多个16位unicode字符组成的字符序列，即字符串，可用单引号和双引号

```
alert(str1.length);

var age=1;

var ageAsString=age.toString();

var found=true;

var foundAsString=found.toString();
```

```
调用toString时可以传递一个参数，输出数值的基数
var num=10;
alert(num.toString());'10'
alert(num.toString(2));'1010'
alert(num.toString(8));'12'
alert(num.toString(10));'10'
alert(num.toString(16));'a'
```

object

一组数据和功能的集合，对象可以通过执行new操作符后跟要创建的对象类型的名称创建。创建示例并添加属性或方法，就可以创建自定义对象

var o=new Object();

### 常量和变量

const NUM=100;

var score=0.0

var x=10; var y=true;

### 运算符和表达式

一元二元三元运算符，需要几个运算数

？：

#### 赋值运算符=

a=b=c=0;

(a=b)==0先给a赋值b，再检测a是否为0

#### 加法赋值运算符+=

#### 加法+

#### 递增递减++ --

#### 乘除法赋值*= /=

#### 取余赋值运算符 %=

#### 取余运算符

#### 比较运算符

返回比较结果的boolean值

#### 关系运算符

< > <= >=

#### 相等运算符

== !=

#### 恒等运算符

===  

！==

#### 条件（三目）运算符

？:

#### delete运算符

从对象中删一个属性，或从数组删一个元素

#### in运算符

prop in objectName

测试对象是否存在该属性

#### new运算符

new constructor[(arguments)]；

new执行下面的任务：

一个没有成员的对象

对象调用构造函数，传递一个指针给新建的对象作为this指针

构造函数根据传递给他的参数初始化该对象

#### typeof运算符

返回数据类型

#### instanceof运算符

f安徽boolean值，指出对象是否时特定类的实例

#### void运算符

避免表达式返回值

### 基本语句

if语句

if else

for

## javascript事件

### 监听事件

#### HTML内联属性，避免使用

html元素里面直接填写事件有关属性，属性值为js代码

```
<button onclick="alert('点击了这个按钮')">点击这个按钮</button>
```

js代码和html代码耦合在了一起，不便于维护和开发

#### DOM属性绑定

设置dom属性来指定某个事件对应的处理函数

element.onoclick=function(event){

​	alert('你点击了这个按钮');

}

监听element节点的click事件

#### 使用事件监听函数

标准的事件监听函数如下

element.addEventListener(<event-name>,<callback>,<use-capure>);

表示在element这个对象上面添加一个事件监听器，当监听到有<event-name>事件发生时，调用<callback>这个回调函数。至于<use-capture>这个参数，表示该事件监听是在捕获阶段中监听（设置true）还是在冒泡阶段中监听（false）

```
var btn=document.getElementByTagName('button');
btn[0].addEventListener('click',function(){
	alert('你点击了按钮');
},false)
```

![image-20260309153346814](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260309153346814.png)

### 移除事件监听

当为某个元素绑定了一个事件，每次触发这个事件时，都会执行事件绑定的回调函数。如果想解除绑定，需要使用removeEventListener

element.removeEventListener(<event-name>,<callback>,<use-capture>);

#### 捕获阶段

在DOM树的某个节点发生了一些操作，就会有一个时间发射过去。事件从Window发出，不断经过下级节点直到目标节点。

#### 目标阶段

事件到达目标节点并触发。

事件触发的目标总是最底层的节点

#### 冒泡阶段

事件到了目标节点之后会沿着原路返回

#### 为什么不用第三个参数true

IE浏览器不支持在捕获阶段监听事件，是为了统一而设置

#### 使用事件代理(Event Delegate)提升性能

通过监听父级节点来实现监听子节点的功能

优势：

减少事件绑定，提升性能。

动态变化的DOM结构，仍然可以监听

#### 停止事件冒泡

element.addEventListener('click',function(event){

​	event.stopPropagation();

},false);

#### 事件的Event对象

事件被触发时会创建一个事件对象，包含一些有用的属性或方法。

```
<button>打印event object</button>
<script>
	var btn=document.getElementsByTagName('button');
	btn[0].addEventListener('click',function(event){
	console.log(event);
	},false);
</script>
```

#### 常用的属性和方法

type(string):事件的名称，比如click

target（node）事件要触发的目标节点。

bubbles（boolean）表明该事件是否在冒泡阶段触发的。

preventDefault（function）：可以禁止一切默认行为

stopPropagation(function):停止冒泡

stopImmediatePropagation(function)：阻止触发其他监听函数。

cancelable(boolean)：这个属性表明该事件是否可以通过调用event.preventDefault方法来禁用默认行为.

eventPhase(number)：这个属性的数字表示当前事件触发在什么阶段。none：0；捕获：1；目标：2；冒泡：3；

pageX和pageY（number）触发时，鼠标相对于页面的坐标。

isTrusted（boolean)表明该事件是浏览器触发（用户真实操作触发）还是js代码触发。

#### jQuery中的事件

jQuery来消除兼容问题

绑定事件和事件代理。这里统一用on绑定事件。

.on(events[,selector],[,data],handler)

处理过兼容性的事件对象（event object)

触发事件trigger方法。可模拟触发事件

```
（elementB).on('click',function()){
(elementA).trigger("click");
}
```



### 事件进阶话题

#### IE下绑事件

1

#### IE中Event需要注意的地方

1

### 事件回调函数作用域问题

1

### 用javascript模拟触发内置事件

function simulateClick(){

​	var event =new MouseEvent('click',{

​	'view':window

​	'bubbles':true,

​	'cancelable':true

});

var cb=document.getElementById('checkbox');

var canseled=!cb.dispatchEvent(event);

if (canceled){

alert("canceled");

}else{

alert("not canceled");

}

}

### 自定义事件

相关函数有Event customEvent dispatchEvent

var event =new event('build');

elem.addEventListener('build',function(e),{...},false);

elem.dispatchEvent(event);

var myEvent=new CustomEvent(eventname,options);

options可以是：

{

​	detail:{

...},

​	bubbles:true,

​	cancelable:false

}

内置事件就会由浏览器根据某些操作触发，自定义的事件需要人工触发。

dispatchEvent函数就是

element.dispatchEvent(customEvent);

11111



### 事件句柄

事件句柄被定义为这些对象的属性

```
<input type="checkbox" name="options"
value="giftwrap" onclick="giftwrap=this.checked;">
```

111

常用的事件句柄属性

onclick:

onmousedown,onmouseup

onmouseover,onmouseout

onchange

onload



### 事件处理

#### HTML事件处理程序

```
<input id='btn1' value="按钮" type="button" onclick="showmsg();">
<script>
	function showmsg(){
		alert('HTML添加事件处理')；
	}
</script>
```

html和js耦合性太强，如果想改showmsg，要在js和html都改

#### DOM0级事件

作用是为指定对象添加事件处理

```
<input id='btn2' value='anniu' type='button'>
<script>
	var btn2=document.getElementById("btn2");
	btn2.onclick=function(){
		alert("DOM0级添加事件处理")；
	}
	btn.onclick=null;
<script>
```

#### DOM2级事件处理程序

主要涉及两个方法，用于处理指定和删除事件处理程序的操作

addEventListener()和removeElementListener()

都接受三个参数：要处理的事件名、作为事件处理程序的函数和一个布尔值

```
<input id="btn3" value="按钮" type="button">
<script>
	var btn3=document.getElementById("btn3");
	btn3.addEventListener("click",showmsg,false);
	function showmsg(){
		alert("");
	}
	btn3.removeEventListener("click",showmsg,false);
</script>
```

# jacaScirpt事件解析

## 应用表单

### 按钮对象

```
<body>
    <form id="autoForm">
        用户名：<input type="text" name="userName">
        密码：<input type="password" name="userPwd">
        <input type="submit" value="提交">
    </form>
    <script>
        autoForm.elements[autoForm.elements.length - 1].onclick=function(e){
        //检测必须项
        if(autoForm.userName.value="" || autoForm.userPwd.value==""){
            alert("用户名或密码不能为空");
        }
        if(e){
            e.preventDefault();//标准方式
        }
        else{
            event.returnValue=false;//IE方式
        }
    }
    </script>
</body>
```

### 复选框对象

![image-20260309201322044](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260309201322044.png)

```
<body>
    <form id="autoForm">
        全选/不选<input type="checkbox" id="selector"><br>
        <hr>
        <label>江苏省<input type="checkbox"></label><br>
        <label>浙江省<input type="checkbox"></label><br>
        <label>安徽省<input type="checkbox"></label><br>
        <label>河南省<input type="checkbox"></label><br>
        <label>湖北省<input type="checkbox"></label><br>
        <label>湖南省<input type="checkbox"></label><br>
        <label>江西省<input type="checkbox"></label><br>
        <label>山东省<input type="checkbox"></label><br>
    </form>
    <script>
        var selector=document.getElementById("selector");
        selector.onclick=function(){
            for(var i=0;i<autoForm.elements.length;i++){
                autoForm.elements[i].checked=this.checked;
        }
    }
    </script>
</body>
```



## 事件分析

### 轮播图效果

????????

```
<body>
    <div class="container" sytle="left:-600px;">
        <img src="test1.jpg" alt="">
        <img src="test2.jpg" alt="">
        <img src="test3.jpg" alt="">
        <img src="test4.jpg" alt="">
        <img src="test5.jpg" alt="">
    </div>
    <div class="button">
        <span class="on">1</span>
        <span>2</span>
        <span>3</span>
        <span>4</span>
        <span>5</span>
    </div>
    <a href="javascript:;" rel="extenal nofollow" rel="extenal follow"  rel="extenal follow"
     rel="extenal follow" class="arrow arrow_left"><</a>
      <a href="javascript:;" rel="extenal nofollow" rel="extenal follow"  rel="extenal follow"
     rel="extenal follow" class="arrow arrow_right">></a>
```

#### <div>CSS部分

？

？

？





## 制作特效

#### 显示网页停留时间

用于显示浏览者在该页面停留了多长时间

三个变量second,minute,hour

不停加1，到六十进1

#### 制作定时关闭窗口

```
<script type="text/javascript">
        function webpageClose(){
            window.close();
        }
        setTimeout("webpageClose()",10000);//10秒后关闭窗口
    </script>
</head>
<body>
    <p>该窗口将在10秒后自动关闭</p>
    
```

## 网页常用效果

### 捕获错误信息

<script type="text/javascript">
        onerror=handleErr
        var txt=""
        function handleErr(msg,url,l){
            txt="本页存在错误.\n\n"
            txt+="错误信息："+msg+"\n"
            txt+="错误位置："+url+"\n"
            txt+="错误行号："+l+"\n"
            txt+="单击确定关闭本页\n"
            alert(txt)
            return true
        }
        function message(){
            adddlert("welcome") 
        }
    </script>
</head>
<body>
    <input type="button" value="查看消息" onclick="message()">
</body>

![image-20260309210420720](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260309210420720.png)
