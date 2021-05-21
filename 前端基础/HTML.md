# HTML

## 简述

### Hypertext markup language : 超文本标记语言

HTML 通过 浏览器渲染 就是我们所见到的网页

### HTML5:超文本协议的第五代版本

+ 优势
  + 解决了跨浏览器的问题
  + 新增了多个新特性
  + 用户优先原则
  + 化繁为简的优势

### 开发工具

+ Dreamweaver
+ Sublime Text
+ WebStorm
+ VScode(推荐：可拓展性强)
+ HBuilder

## HTML5语法

标签不区分大小写

允许属性值不使用引号

允许部分属性值的属性省略

## 标签

此元素可告知浏览器其自身是一个 HTML 文档

``` html
<html> </html> // 这个就一个HTML 标签，也成为HTML 元素
```

### 分类

通常将 HTML 标签分为两大类

+ 单标签

  也成为空标签，是使用一个标签符号即可完整的描述某个功能的标签

  ``` html
  例如：<img /> 
  ```

+ 双标签

  也成为体标签，是指由开始和结束两个标签符组成的标签

  ``` html
  例如：<title></title> <body> </body>
  ```

### 关系

HTML 标签有两种关系

+ 包含关系

  ``` html
  <html>
      <head>
          <title>网页标题</title>
      </head>
  </html>
  ```

+ 并列关系

  ``` html
  <html>
      <head> </head>
      <body> </body>
  </html>
  ```

### 注释

需要对某处进行结束说明，就可以添加注释，内容应言简意赅

``` html
<!-- 注释语句 -->
```

###  属性

标签的属性

``` html
例如：<p aligin=left> 文本左对齐 </p>

```

### 基本结构标签

``` html
<!DOCTYPE html> 
<html>
    <!-- 首部 -->
    <head>
        <meta charset="utf-8"/>
        <title>网页的标题</title>
    </head>
    
    <!-- 主体部分 -->
    <body>
        网页的内容
    </body>
</html>
```

### 文档类型声明的标签

``` html
<!DOCTYPE html> 表示这是HTML5文档
```

### HTML标签

``` html
<html> 页面中最大的标签，称为根标签
```

### head:文档头部

相关标签

#### < title >

``` html
<title>:文档的标题，使页面有标题，只能有一个 
```

#### < link >

``` html
<link>:引用外部文件，可以有任意多个
基本语法：<link href="", rel="", type="">
herf = URL：指定引用外部文件的地址
rel = stylesheet：表示定义一个外部样式表
type = text/css：引用外部文档的类型为CSS样式表
type = text/javascript：引用外部文档的类型为javascript
```

#### < style >

``` html
基本语法：<style></style>
在 HTML 中使用 style 标记时，常常定义其属性为 type , 相应的属性值为 text/css , 表示使用内嵌式的CSS 样式
```

#### < meta >

``` html
<meta>:定义页面的元信息，charset="utf-8"仅仅是其中一个属性，用于设置网页的字符编码，该标签可以有任意多个
作用：
1.搜索引擎（SEO）优化
2.定义页面使用语言
3.自动刷新页面
4.控制页面缓存
5.网页定级评价
```

+ meta总共有 3 个属性不同的属性和值组成了网页不同的功能

+ name 属性

  name 属性主要是用于描述网页的，对应 content 属性中的内容是便于搜索引擎查找和分类信息

  ``` html
  基本语法：<meta name="" content="" />
  <meta name="keywords" content="HTML,CSS" /> name="keywords"：设置搜索引擎获取网页的关键字
  <meta name="description" content="个人博客" /> name="description"：设置搜索引擎获取网页的描述内容
  <meta name="robots" content="" /> name="robots"：设置搜索引擎是否能检索
  content有如下参数：
  all：文件将被检索，且页面上的链接可以被查询
  none：文件将不被检索，且页面上的链接不可以被查询
  index：文件将被检索
  noindex：文件将不被检索，但页面上的链接可以被查询
  follow：页面上的链接可以被查询
  nofollow：文件将被检索，但页面上的链接不可以被查询
  
  <meta name="author" content="jay" /> name="author"：设置页面的作者
  <meta name="generator" content="hobbit" /> name="generator"：设置生成网页文档的软件包
  <meta name="COPYRIGHT" content="CAI" /> name="generator"：设置网页的版权信息
  <meta name="revisit-after" content="30day" /> name="revisit-after"：设置搜索引擎重访的天数：30天
  <meta name="viewport" content="width=device-width, initial-scale=1.0"> name="viewport"：一般用来设计手机端网页的缩放，这里不详细解释
  ```

+ http-equiv 属性：设置 http 的文件头

  ``` html
  <meta http-equiv="Content-Language" content="zh-cn" /> http-equiv="Content-Language":设置页面的语言
  <meta http-equiv="Refresh" content="5;URL=http://m.baichanghui.com" /> http-equiv="Refresh"：设置自动刷新并跳转新页面，content = 5：表示五秒之后
  <meta http-equiv="content-Type" content="text/html;charset=utf-8" /> 设置页面使用的字符集
  ```

### body:文档的主体

剩下的标签都是主体的标签，只能在主题内使用

#### 标题标签

``` html
基本语法：
<hn></hn> n:1~6，共有六级标题
基本属性：
<hn align="对齐方式"> 标题文本 </hn>
align = left：左对齐（默认），center：居中，right：右对齐
```

![image-20200405105938338](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405105938338.png)

#### 段落标签

```html
基本语法：
<p align = "对齐方式"> 段落文本 </p>
```

![image-20200405110000733](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405110000733.png)

#### 水平线

``` html
基本语法：
<hr 属性="属性值"/> 用于段落与段落之间的分隔
align：设置水平线的对齐方式 = （left，right，center）
size：设置水平线的粗细（以像素为单位，默认为2px）
color：设置水平线的颜色（可用颜色名，#RGB，rgb(r,g,b)
width：设置水平线的宽度（可以是像素值，也可以是屏幕的比（默认100%））
```

![image-20200405110035054](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405110035054.png)

#### 换行标签

``` html
<br> 用于实现段落的换行，使用 回车行换在HTML中没有效果
```

#### 文本格式化标签

``` html
<b></b> = <strong></strong> 文本以粗体方式显示
<i></i> = <em></em> 文本以斜体方式显示
<s></s> = <del></del> 文本以加删除线的方式显示
<u></u> = <ins></ins> 文本以加下划线的方式显示
```

#### 文字标签

``` html
基本语法：
<font> 文字 </font>
常用属性：
size：设置文字的大小，默认为3
color：设置文字的颜色
face：设置文字的字体
```

![image-20200405110828416](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405110828416.png)

#### 特殊字符标签

``` h
空格 = &nbsp;
< = &lt;
> = &gt;
& = &amp;
￥ = &yen;
© = &copy;
® = &reg;
° = &deg;
± = &plusmn;
× = &times;
÷ = &divide;
² = &sup2;
³ = &sup3;
```

## 表格与列表

多用于数据展示

### 表格

``` html
基本语法:
<table>
    <!-- tr(table row)：行 -->
    <tr>
        <!-- th(table head)：表格的表头-->
        <th>内容</th>
        <!-- td(table data)：行中的数据-->
        <td>文字</td>
        <td>文字</td>
    </tr>
</table>

基本属性：
如果想要对表格进行修改 建议使用CSS
align = 对齐方式
bgcolor = 背景颜色
border = 边框宽度
cellpadding = 内间距（表格边与内容的距离）
cellspacing = 空间（单元格之间的空白）
frame = 规定外侧边框哪部分是可见的
rules = 规定内侧边框哪部分是可见的
summary = 表格的摘要
width = 表格宽度
```

![image-20200405112732754](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405112732754.png)

#### 表格的结构标签

无实际意义，但是使的表格的结构更为清晰明了，推荐使用

![image-20200405112923728](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405112923728.png)

#### 合并单元格

``` html
rowspan = "合并个数" ：跨行合并
colspan = "合并个数" ：跨列合并
```

![image-20200405113113727](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405113113727.png)

### 列表

简单的布局（整齐，整洁）

#### 无序列表

``` html
基本语法
注意：每对 ul 中至少包含一对 li
<!-- 用于定义无序列表 -->
<ul>
    <!-- 描述具体的列表项 -->
    <li>列表项</li>
    <li>列表项</li>
    <li>列表项</li>
</ul>
```

![image-20200405113526426](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405113526426.png)

### 有序列表

``` html
基本语法：
注意：每对 ol 中至少包含一对 li
<!-- 用于定义有序列表 -->
<ol>
    <!-- 描述具体的列表项 -->
    <li>列表项</li>
    <li>列表项</li>
    <li>列表项</li>
</ol>

tips:
<ol start="2"></ol> 修改起始编号
<ol start="2" reversed></ol> 反序

基本属性：
type = 显示的序号类型（1：默认；a或A：以该字母起始；i或I：以罗马符号起始）
start = 起始值
value = 项目符号的数字
```

![image-20200405114223898](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405114223898.png)

### 定义列表

常用于图文混排

``` html
基本语法：
<!-- 指定定义列表 -->
<dl>
    <!-- 标记用于指定术语的名词 -->
    <dt> 名词 </dt>
    <!-- 对名词进行解释或描述 -->
    <dd> 名词解释</dd>
</dl>
```

![image-20200405114549537](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405114549537.png)

## 表单的应用

表单是HTML网页中的重要元素，利用表单可以使网页实现交互行为，如：网上注册，网上登录，网上交易

### 构成

+ 提示信息

  提示用户进行填写和操作

+ 表单控件

  具体的表单功能项，如：输入框、复选框、提交按钮

+ 表单域

  相当于一个容器，用来容纳表单控件和提示信息

### 创建

``` html
基本语法：
<form action="url地址" method="提交方式" name="表单名称">
    各种控件
</form>

基本属性：
action：指定接受并处理表单数据的服务器程序的 url 地址（通常和PHP结合使用）
method：设置表单的提交方式
get = 用户名和密码将明文出现在URL上，因为登录页面有可能被浏览器缓存,GET请求请提交的数据放置在HTTP请求协议头(不安全，且长度有限制=提交的数据有限)
post = POST提交的数据则放在实体数据，POST请求数据不能被缓存下来，不会被保存在浏览器历史或 web 服务器日志中，没有长度限制

name：指定表单的名称，以区分同一页面的多个表单
autocomplete：指定表单是否有自动完成功能
novalidate：提交表单时取消对表单进行的有效检查

```

### input 元素

按照不同的类型定义不同的控件

#### 文本输入框

``` html
用户名：<input type="text" value="张三" maxlength="6">
常用属性：
name：控件名
value：控件的值
maxlength：允许输入的最大长度
```

![image-20200405122026952](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405122026952.png)

#### 密码输入框

```html
密码：<input type="password" size="40">
size：控件的宽度
```

![image-20200405122320579](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405122320579.png)

### 单选按钮

``` html
<input type="radio" name="sex" checked="男" value="男"> 男
checked：单选框选择的值
value：获得选中的单选框的值
```

![image-20200405122904758](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405122904758.png)

### 复选框

``` html
兴趣：<input type="checkbox" name="bobby" value="唱歌">唱歌
```

![image-20200405123315136](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405123315136.png)

### 普通按钮

通常配合JavaScript使用

``` html
<input type="button" value="普通按钮">
```

![image-20200405123718422](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405123718422.png)

### 提交按钮

提交按钮是表单中的核心控件，单击提交按钮即可发送表单

```html
<input type="submit">
```



![image-20200405123907520](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405123907520.png)

### 重置按钮

取消所有已输入的表单信息

``` html
<input type="reset">
```

![image-20200405124048460](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405124048460.png)

### 图片形式的提交按钮

以图片的形式替代了按钮的显示样式

``` html
<input type="image" src="">
```

![image-20200405124450512](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405124450512.png)

### 隐藏域

对用户是不可见的，通常应用于后台程序

``` html
<input type="hidden">
```

### 提交文件

用户可以通过填写文件路径或直接选择文件的方式，将文件提交给后台服务器

``` html
<input type="file">
```

![image-20200405124815803](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405124815803.png)

### email输入框

用来验证输入的数据是否符合 Email 格式，如果不符合会提示相应的错误信息

``` html
email:<input type="email">
```

![image-20200405124959641](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405124959641.png)

### URL输入框

用来验证输入的数据是否符合 URL 格式，如果不符合会提示相应的错误信息

``` html
网站地址:<input type="url">
```

### Tel输入框

用于提供输入电话号码的文本框，通常需要配合正则表达式来使用

``` html
Tel:<input type="tel">
pattern = 可自定义正则的格式
```

### 搜索框

用于输入搜索关键词的文本，它能自动记录一些字符。在用户输入内容后，右侧会自带一个删除图标，用于快速清除内容

``` html
搜索框：<input type="search">
```

### Color

用于实现一个RGB颜色的输入

``` html
请选择一种颜色：<input type="color">
```

![image-20200405132528796](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405132528796.png)

### Number

用于提供输入数值的文本框，在提交时会自动检查输入的内容是否为数字，且数字是否在限定范围内

``` html
请输入数值：<input type="number" name="number" value="name" min="1" max="20" step="4">
min：最小范围
max：最大范围
step：数字间隔
```

![image-20200405133212557](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405133212557.png)

### Range

用于提供一定内数值的输入范围

``` html
<input type="range">
```

![image-20200405133457031](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405133457031.png)

### Date

提供可供选择的日期和时间，用于验证输入的日期

``` html
请输入日期：<input type="date">
```

![image-20200405133555881](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405133555881.png)

![image-20200405133638295](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405133638295.png)

### 常用的其他属性

#### autofocus

自动获取焦点

#### form

可以将表单内的任意子元素写在页面中，只需要将 form 的属性值设置为该表单的 id 即可

#### list

list属性用于指定输入框所绑定的 datalist 元素，其值是某个 datalist 的id

``` html
<input id="myCar" list="cars" />
<datalist id="cars">
  <option value="BMW">
  <option value="Ford">
  <option value="Volvo">
</datalist>
```

![image-20200405134824342](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405134824342.png)

#### multiple

multiple 属性规定输入字段可选择多个值，适用于上传文件的场景

``` html
 <input type="file" name="img" multiple="multiple" />
```

![image-20200405135633315](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405135633315.png)

#### pattern

验证用户的输入值是否和定义的正则表达式相匹配

![image-20200405140104424](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405140104424.png)

![image-20200405140130152](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405140130152.png)

#### placeholder

为 input 输入框提供相关的提示信息

``` html
<input type="text" placeholder="请输入姓名：">
```

![image-20200405140405063](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405140405063.png)

#### required

规定输入框的内容不能为空，否者不允许提交

``` html
Name:<input type="text" required="required">
```



![image-20200405140545415](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405140545415.png)

### 其他表单元素

#### textarea

创建一个文本域

``` html
基本语法
<textarea cols="每行中的字符数" rows="显示的行数">
    文本内容
</textarea>
```

![image-20200405140913728](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405140913728.png)

可选属性

![image-20200405141001700](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405141001700.png)

#### select

下拉菜单

``` html
基本语法
<select>
    <option>选项1</option>
    <option>选项2</option>
    <option>选项3</option>
</select>
```

常见属性

![image-20200405141328808](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405141328808.png)

例

``` html
<select>
<optgroup label="福建省"></optgroup>
	<option>福州</option>
	<option>泉州</option>
	<option>莆田</option>
</select>
```

![image-20200405141915325](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405141915325.png)

#### keygen

keygen用于表单的密钥生成器，能够使用于验证更为安全、可靠。当提交表单时会生成两个键：

私钥：储存在客户端

公钥：被发送到服务器，验证用户的客户端证书

![image-20200405142608972](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405142608972.png)

![image-20200405142801887](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405142801887.png)