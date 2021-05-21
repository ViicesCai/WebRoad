# CSS3 新布局

## 多列布局

排版长文字

``` css
<!-- 定义多列布局 -->
columns{"width", "count"};
```

![image-20200523155411363](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200523155411363.png)

### 设置列宽

`column-width: length|auto`

+ length：像素值

### 设置列数

`column-count: integer|auto`

+ int：整数，定义几列

### 设置列间距

`column-gap: normal|length`

+ normal：自动解析
+ length：像数值

### 设置边框样式

`column-rule: style|length|color|transparent`

+ style：边框样式
+ length：像数值
+ color：颜色
+ transparent：透明度

### 设置跨列显示

`column-span: none|all`

+ none：不跨列
+ all：横跨所有的列

### 设置列高度

`column-fill: auto|balance`

+ auto：自动
+ balance：自动调整

## 弹性盒布局

用于适配不同的设备尺寸和浏览器分辨率

### Flex 布局

+ 采用 Flex 布局的元素称为 Flex 容器（flex container）
+ 其所有的子元素自动成为容器成员，称为 Flex 项目（flex item）
+ 容器默认存在两根轴：水平的主轴（main axis）和垂直的交叉轴（cross axis）
+ 主轴的开始位置叫做main start，结束位置叫做main end；交叉轴的开始位置叫做cross start，结束位置叫做cross end
+ 项目默认沿主轴排列，单个项目占据的主轴空间叫做main size，占据的交叉轴空间叫做cross size

![image-20200523174455992](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200523174455992.png)

### 定义 Flexbox

html

``` html
<div class="box">
    <div class="box-item">1</div>
    <div class="box-item">2</div>
    <div class="box-item">3</div>
    <div class="box-item">4</div>
</div>
```

css

``` css
.box {
    background-color: brown;
    margin: 0 0 55px;
    display: flex;
}

.box-item {
    width: 200px;
    height: 200px;
    line-height: 200px;
    /* 垂直对齐 */
    vertical-align: middle;
    margin: 5px;
    background-color: skyblue;
    font-size: 100px;
    color: white;
    text-align: center;
}
```

![image-20200523175216006](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200523175216006.png)

### flex-direction

决定主轴的方向（即项目的排列方向）

`flex-direction: row|row-reverse|column|column-reverse`

+ row（默认）：主轴为水平方向，起点在左端
+ row-reverse：主轴为水平方向，起点在右端
+ column：主轴为垂直方向，起点在上沿
+ column-reverse：主轴为垂直方向，起点在下沿

![image-20200523175708451](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200523175708451.png)

### flex-warp

默认情况下，项目都排在一条线（又称"轴线"）上。flex-wrap属性定义，如果一条轴线排不下，如何换行。

`flex-wrap: nowrap | wrap | wrap-reverse`

#### nowrap

![image-20200523180754571](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200523180754571.png)

#### wrap

![image-20200523180813118](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200523180813118.png)

#### wrap-reverse

![image-20200523180825091](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200523180825091.png)

### flex-flow

flex-flow属性是flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap

`		    flex-flow: <flex-direction> || <flex-wrap>`

![image-20200523182814009](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200523182814009.png)

### justify-content

定义了项目在主轴上的对齐方式

`		    justify-content: flex-start | flex-end | center | space-between | space-around`

#### flex-start

![image-20200523182932145](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200523182932145.png)

#### flex-end

![image-20200523182942845](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200523182942845.png)

#### center

![image-20200523182953171](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200523182953171.png)



#### space-between

![image-20200523183017322](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200523183017322.png)

#### space-around

![image-20200523183029868](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200523183029868.png)

### align-items

定义项目在交叉轴上如何对齐

`		 	align-items: flex-start | flex-end | center | baseline | stretch`

#### flex-start

![image-20200523183107067](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200523183107067.png)

#### flex-end

![image-20200523183119585](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200523183119585.png)

#### center

![image-20200523183130005](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200523183130005.png)

#### baseline

![image-20200523183145420](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200523183145420.png)

#### stretch

![image-20200523183202046](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200523183202046.png)

### align-content

定义了多根轴线（多行）的对齐方式。如果项目只有一根轴线，该属性不起作用

`		  align-content: flex-start | flex-end | center | space-between | space-around | stretch`

#### flex-start

![image-20200523183241299](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200523183241299.png)

#### flex-end

![image-20200523183303920](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200523183303920.png)

#### center

![image-20200523183325913](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200523183325913.png)

#### space-between

![image-20200523183345549](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200523183345549.png)

#### space-around

![image-20200523183408938](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200523183408938.png)

#### stretch

![image-20200523183423663](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200523183423663.png)

### 项目的属性（item）

#### order

定义项目的排列顺序。数值越小，排列越靠前，默认为0

`		  order: <integer>`

![image-20200523184221425](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200523184221425.png)

#### flex-grow

定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大

如果所有项目的flex-grow属性都为1，则它们将等分剩余空间（如果有的话），如果一个项目的flex-grow属性为2，其他项目都为1，则前者占据的剩余空间将比其他项多一倍

`		  flex-grow: <number>`

![image-20200523184406242](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200523184406242.png)

#### flex-shrink

定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小

如果所有项目的flex-shrink属性都为1，当空间不足时，都将等比例缩小。如果一个项目的flex-shrink属性为0，其他项目都为1，则空间不足时，前者不缩小
负值对该属性无效

`		    flex-shrink: <number>`

![image-20200523184553118](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200523184553118.png)

#### flex-basis

定义了在分配多余空间之前，项目占据的主轴空间（main size）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小

`	flex-basis: <length>; | auto`

![image-20200523184753079](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200523184753079.png)

#### flex

是flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto，后两个属性可选。

该属性有两个快捷值：auto (1 1 auto) 和 none (0 0 auto)

`flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'>`

#### align-self

允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch

`align-self: auto | flex-start | flex-end | center | baseline | stretch`

![image-20200523184937255](https://typora-image-1301733210.cos.ap-guangzhou.myqcloud.com/img/image-20200523184937255.png)