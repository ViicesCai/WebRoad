# CSS3

Cascading Style Sheet：层叠样式表

## 简述

如果希望网页美观、大方，并且轻松升级、维护方便，就需要使用CSS，实现结构与表现的分离

CSS 非常灵活，既可以嵌入在 HTML 文档中，也可以是单独的外部文件，如果是独立文件，则必须以 .css 为后缀名

### 浏览器支持情况

![image-20200405184021715](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405184021715.png)

由于各浏览器厂商对CSS3各属性的支持程度不一样，因此在标准尚未明确的情况下，会用厂商的前缀加以区分，通常把这些加上私有前缀的属性称为"私有属性"

内核类型：

+ Trident（IE8/IE9/IE10）私有前缀：-ms
+ Webkit（谷歌Chrome/Safari）私有前缀：-webkit
+ Gecko（火狐Firefox）私有前缀：-moz
+ Blink（Opera）私有前缀：-o

注意：

+ 使用时要遵照一定的书写顺序，即先写私有的CSS3属性，再写标准的CSS3属性

+ 当一个 CSS3 属性成为标准属性，并且被主流浏览器的最新版普遍兼容时，就可以省略私有的CSS3 属性

``` css
例如：一个CSS3圆角的代码
-webkit-border-radius:50%;
-o-border-radius:50%;
-moz-border-radius:50%;
-ms-border-radius:50%;
```

## 注释

``` css
基本语法
/* 注释内容 */
```

## CSS核心基础

### 样式规则

``` css
选择器 {
    属性1:属性值1;
    属性2:属性值2;
    属性3:属性值3;
}

选择器用于指定 CSS 样式作用的 HTML 对象,花括号内是该对象设置的具体样式。
属性和属性值以"键值对"的形式出现,用英文":"连接,多个"键值对"之间用英文";"进行区分
```

注意：

+ CSS 选择器严格区分大小写，属性和值不区分大小写，按照书写习惯一般将"选择器、属性和值"都采用小写的方式
+ 多个属性间用 , 隔开，最后一个属性的分号可以省略，但为了便于增加新样式，最好保留
+ 如果属性的值由多个单词组成且中间包含空格，则必须为这个属性加上英文状态下的引号
+ 在编写CSS代码时，为了提高代码的可读性，通常会加上CSS的注释
+ CSS代码中的空格不会被解析，花括号以及分号前后的空格可有可无

### 引入CSS样式表

#### 行内式

也成为内联式，是通过标记 style 属性来设置元素的样式

``` html
语法格式
<标记名 style="属性1:属性1值;属性2:属性2值">内容</标记名>
```

![image-20200405191421200](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405191421200.png)

#### 内嵌式

内嵌式是将CSS代码集中写在HTML文档的 < head >头部标签中，并且用 < style >定义

``` html
语法格式
<head>
    <style type="text/css">
        选择器{属性1:属性值1;属性2:属性值2}
    </style>
</head>
```

![image-20200405191707916](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405191707916.png)

#### 链接式

链接式是将所有的样式放在一个或多个以 .css 为扩展名的外部样式表文件中，通过< link > 标记将外部样式表链接到 HTML 文档中

``` html
<head>
    <link href="CSS文件的路径" type="text/css" rel="stylesheet">
</head>
```

#### 注意

除了链接式以外，还有一种导入样式的方式

``` html
<style type="text/css">
    @import xxxx.css;
    @import 'xxxx.css';
    @import "xxxx.css";
    @import url(xxxx.css);
    @import url('xxxx.css');
    @import url("xxxx.css");
</style>
```

## 选择器

### CSS基础选择器

要想将 CSS 样式应用于特定的 HTML 元素，首先需要找到该目标元素。在 CSS 中，执行这一任务的样式规则部分被称为选择器

#### 标签选择器

``` css
标签名{属性1:属性值1;属性2:属性值2}
body{font-size:12px;color:#cccccc}
```

#### 类选择器

标记中的 class 属性规定元素的类名(classname)

``` css
基本语法
.类名{属性1:属性值1;属性2:属性值2}
```

![image-20200405192851389](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405192851389.png)

#### id 选择器

标签的 id 属性规定元素的 id 名，id 是唯一的

``` css
基本语法
#id名{属性1:属性值1;属性2:属性值2}
```

![image-20200405193220893](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200405193220893.png)

#### 通配符选择器

通配符选择器用 * 表示，它是所有选择器中作用范围最广的，能匹配页面中的所有元素

``` css
基本语法
*{属性1:属性值1;属性2:属性值2}

/* 清除所有标签的默认边距 */
*{
    margin:0;
    padding:0;
}
```

### 组合选择器

#### 包含选择器

主要用来选择某个元素的包含的某个元素：即 div -> p

``` html
基本语法
#ip 标签名
```

![image-20200418124924187](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200418124924187.png)

#### 子代选择器

用来选择某个元素的第一级子元素

``` css
基本语法
标签名 > 子级标签名
```

![image-20200418125322247](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200418125322247.png)

#### 相邻选择器

用来选择与前后相邻的元素

``` css
基本语法
标签名+相邻的标签名
```

![image-20200418125524990](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200418125524990.png)

#### 兄弟选择器

使用 "~"来链接前后两个选择器，选择器中的两个元素必须有同一个父亲，但第二个元素不必紧跟第一个元素

``` css
基本语法
标签名~同级的标签名
```

![image-20200418130121990](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200418130121990.png)

### 属性选择器

``` css
E[att^=value]
```

选择名字为 E 的标记，且该标记定义了 att 属性，att 属性包含前缀为 value 的子字符串

+ E 可以省略，如果省略则表示可以匹配满足条件的任意元素

![image-20200418130450705](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200418130450705.png)

``` css
E[att$=value]
```

att 属性包含后缀为 value 的子字符串，同上

![image-20200418132400944](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200418132400944.png)

``` css
E[att*=value]
```

att 属性包含 value 的子字符串

![image-20200418132553493](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200418132553493.png)

### 伪类选择器

许多标签都有伪类：这里列举超链接的伪类，如：input、img 也存在伪类

#### 动态伪类

![image-20200418133135940](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200418133135940.png)

#### 结构化伪类

``` css
:root 选择器
用于匹配文档根元素，即HTML
在这个选择器中定义的样式，在所有的页面都生效

:first-child 和 :last-child 选择器
分别用于父元素中的第一个或最后一个元素设置样式

:nth-child(n) 和 :nth-last-child(n) 选择器
上一个选择器的拓展，选择第n个或倒数第n个

:nth-of-type(n) 和 :nth-lash-of-type(n) 选择器
用于匹配属于父元素的特定类型的第n子元素和倒数第n个子元素

:only-child 选择器
用于匹配某个父元素的唯一子元素的元素

:empty 选择器
选择没有子元素或文本内容为空的所有元素

:not 选择器
如果对某个结构元素使用样式，但是想排除这个结构元素下面的子结构元素，让它不使用这个样式，可以使用 :not

:target 选择器
为页面中的某个 target 元素指定样式。只有用户单击了页面中的超链接，并跳转到 target 元素后，该选择器的样式才会起作用
```

## 字体与字体的 CSS

### 文本标签：可使用字体 CSS 的标签

``` html
标题文本：h1 h2 h3...
段落文本：p
引用文本：q blockquote
强调文本：em
格式文本：b(加粗) i(斜体) big(大字体) small(小字体) sup(上标) sub(下标)
输出文本：code(源代码) pre(预定义格式的源代码) tt(打印机字体) kbd(键盘字体)
文本方向：bdo
```

### 字体样式

``` css
font-family : 用于设置字体
如：p {font-family:"微软雅黑";}
```

``` css
font-size : 用于设置字号
如：p {font-size:"10px";}
```

![image-20200418141052479](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200418141052479.png)

``` css
font-weight : 用于定义字体的粗细
如：p {font-weight:"normal";}
```

![image-20200418141221221](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200418141221221.png)

``` css
font-style : 用于定义字体风格
```

![image-20200418141323871](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200418141323871.png)

``` css
也可以对字体样式进行综合设置
进行综合设置必须按照一下格式
选择器 {font:font-style font-variant font-weigth font-size/line-height(行高) font-family;}
```

### 文本样式

+ 字体样式

``` css
设定服务器字体：即将本地的字体添加到网页中
@font-face {
    font-family:字体名称;
    src:字体路径;
}
```

``` css
word-wrap : 用于长单词和 URL 地址的自动换行
选择器 {word-wrap:属性值;}
```

![image-20200418142011439](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200418142011439.png)

+ 外观样式

``` css
color : 定义文本的颜色
取值方式：
1.预定义的颜色值：如：red green blue
2.十六进制：如：#FF0000 #FF6600(最常用)
3.RGB代码：如：rgb(255,0,0) 或 rgb(100%,0%,0%)
```

``` css
letter-spacing : 定义字间距
可参照长度单位，允许使用负值，默认为：normal
```

``` css
word-spacing : 定义英文单词之间的间距，对中文字符无效
同上
```

``` css
line-height : 设置行间距，即行高
参照上面的长度单位
```

``` css
text-transform : 控制英文字符的大小写
```

![image-20200418142827534](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200418142827534.png)

``` css
text-decoration : 设置文本的下划线、上划线、删除线等装饰效果
```

![image-20200418142917404](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200418142917404.png)

``` css
text-align : 设置文本内容水平对齐
```

![image-20200418143333669](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200418143333669.png)

``` css
text-indent : 设置首行文本的缩进
参考长度单位，允许使用负值，通常使用：em 为单位
```

``` css
white-space : 设置空白符的处理方式
```

![image-20200418143526505](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200418143526505.png)

### CSS3 新特性

``` css
text-shadow : 为页面中的文本添加阴影效果
例：text-shadow:10px 10px 10px red;  /*设置文字阴影的距离、模糊半径、和颜色*/
```

![image-20200418143851062](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200418143851062.png)

``` css
text-overflow : 用于标示对象内溢出的文本
例：
p {
    /* 设置省略标记的步骤如下 */
	width:200px;               /*定义对象的宽度*/
	height:100px; 
	border:1px solid #000;
	white-space:nowrap;       /*强制文本不能换行*/
	overflow:hidden;           /*修剪溢出文本*/
	text-overflow:ellipsis;  /*用省略标记标示被修剪的文本*/
}
```

![image-20200418144119108](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200418144119108.png)

![image-20200418144153466](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200418144153466.png)

### 拓展

+ 可以使用 text-shadow 给文字添加多个阴影，从而产生阴影叠加的效果，方法为设置多组阴影参数，中间用逗号隔开

![image-20200418144817500](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200418144817500.png)

![image-20200418145206932](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200418145206932.png)

## CSS 模型（布局基础）

### 概述

#### 概念

+ 在 HTML 中即盛放元素内容的容器
+ 每个盒子模型都由元素的内容、内边距（padding）、边框（border）和外边距（margin）组成

![image-20200514081845681](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200514081845681.png)

#### 高度和宽度

+ 盒子的宽度和高度决定了盒子的大小
  + 总宽度：width + 左右内边距之和 + 左右边框宽度之和 + 左右外边距之和
  + 总高度：height + 上下内边距之和 + 上下边框宽度之和 + 上下外边距之和

#### box-sizing

![image-20200514082146472](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200514082146472.png)

#### <div> 标记

+ 块容器标记
+ 可以将网页分割为独立的部分，以实现网页的规划和布局
+ 大多数 HTML 标记都可以嵌套在 div 标记中，div 中还可以嵌套多次 div
+ 可以替代大多数的块级文本标记

### 相关属性

#### 边框属性

![image-20200514082625915](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200514082625915.png)

+ border-style

  ``` css
  border-style: solid; /* 四边都是实线 */
  border-style: solid dotted; /* 上下实线、左右点线 */
  border-style: solid dotted dashed; /* 上实线、左右点线、下虚线 */
  ```

+ border-width

  + 设置边框宽度的前提是设置了边框样式，单位为 px

+ border-color

  边框颜色属性

  + border-top-colors
  + border-right-colors
  + border-bottom-colors
  + border-left-colors

+ 注意：宽度、样式、颜色顺序任意，不分先后

  ![image-20200514091511240](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200514091511240.png)

  

+ border-image

  ![image-20200514091759985](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200514091759985.png)

+ margin允许使用负值，padding不允许

  ``` css
  margin:0 auto; /* 利用margin 实现快元素居中 */
  ```

+ 为了更方便的控制页面中的元素，制作网页时，通常先清除元素的默认内外边距

  ``` css
  * {
      padding:0; /* 清除内边距 */
      margin:0; /* 清除外边距 */
  }
  ```

#### box-shadow

![image-20200514092417805](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200514092417805.png)

## 浮动与定位

### 浮动

+ 浮动：设置了浮动属性的元素会脱离标准文档流的控制，移动到其父元素中指定位置的过程

``` css
选择器{float: 属性值;}
```

![image-20200517091555088](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200517091555088.png)

#### 特性

+ 设置了浮动属性的元素会脱离标准文档流的控制

+ 如果多个盒子设置了浮动，则他们会按照属性值一行内显示并且顶端对齐排列

  + 注意：浮动的元素是互相贴靠在一起的（不会有缝隙），如果父级宽度装不下这些浮动的盒子，多出的盒子会另起一行对齐

+ 浮动元素会具有行内块元素特性

  任何元素都可以浮动，不管原先是什么模式的元素，添加浮动之后具有行内块元素相似的特性

  + 块级盒子没有设置宽度，默认宽度和父级一样，但是添加浮动后，它的大小根据内容来决定
  + 未设置外边距时，浮动的盒子之间是没有缝隙的，紧紧贴着
  + 行内元素同理

#### 使用样例

+ 浮动的元素经常和标准流父级搭配使用
  + 在布局中，为了约束浮动元素的位置，一般会搭配标准流
  + 先用标准流的父元素排列上下位置，之后内部子元素采取浮动排列左右位置

![image-20200517092845842](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200517092845842.png)

![image-20200517092913262](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200517092913262.png)

![image-20200517092929572](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200517092929572.png)

### 清除浮动

由于浮动元素不再占用原文档流中的位置，所以会对页面中的其他元素的排版产生影响，如果要避免这种影响，就需要对元素清除浮动

#### clear 属性

``` css
选择器{clear: 属性值;}
```

![image-20200517093255805](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200517093255805.png)

+ 在浮动元素之后添加空标记，并对该标记应用"clear: both"样式，可以清除浮动，这个空标记可以为 <div> <p> <hr> 等任何标记

#### overflow 属性

可以解决溢出问题

``` css
选择器{overflow: 属性值;}
```

![image-20200517093712962](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200517093712962.png)

+ "overflow: hidden" 样式，也可以清除浮动对该元素的影响，该方法弥补了空标记清除浮动的不足

#### after 伪对象

使用 after 伪对象也可以清除浮动，但是该方法只适用于 IE8 及以上版本浏览器和其他非 IE 浏览器

### 定位

在 css 中通过 position 可以实现网页元素的精确定位，元素的定位属性主要包括定位模式和边偏移两部分

#### 定位模式

``` css
选择器{position: 属性值;}
```

![image-20200517094534850](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200517094534850.png)

#### 边偏移

通过边偏移属性 top、bottom、left、right，来精确定义定位元素的位置，其取值为不同单位的数值或百分比

![image-20200517094724646](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200517094724646.png)

#### 静态定位：static

+ 元素的默认定位方式，当 position 属性的取值为 static 时，可以将元素定位在 HTML 文档流的默认位置，在静态定位状态下，无法通过边偏移属性（top、bottom、left、right）来改变元素的位置

#### 相对定位：relative

+ 相对定位是将元素相对于他在标准文档流中的位置进行定位

![image-20200517095130451](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200517095130451.png)

![image-20200517095153725](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200517095153725.png)

#### 绝对定位：absolute

+ 将元素依据最近的已经定位（绝对、固定或相对定位）的父元素进行定位，若所有的父元素都没有定位，则依据 body 根元素（浏览器窗口）进行定位

![image-20200517095455360](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200517095455360.png)

![image-20200517095511090](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200517095511090.png)

#### 固定定位：fixed

+ 是绝对定位的一种特殊形式，它以浏览器窗口作为参照物来定义网页元素，当 position 属性的取值为 fixed 时，即可将元素的定位模式设置为固定模式

  ``` css
  选择器{position: fixed;}
  ```

  + 当多个元素同时设置定位时，定位元素之间可能会发生重叠
  + z-index：可以调整重叠定位元素的堆叠顺序，其取值可以为正整数、负整数和0，z-index的默认值为0

![image-20200517100731347](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200517100731347.png)