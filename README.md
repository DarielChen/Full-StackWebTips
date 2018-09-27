# Full-StackWebTips⚡️
Web全栈开发的一些知识点

---

# 目录

[1.标签元素的划分和互相转化](#1)  
[2.CSS选择器以及优先级](#2)  
[3.CSS的浮动和定位](#3)  
[4.CSS的高度塌陷问题](#4)
[5.Flexbox布局](#5)  

---

<h2 id="1">1.标签元素的划分和互相转化</h2>  

#### 1.标签元素分为两大类: 块元素和行内元素.

块元素: 自己单独占一行，就像一个段落.**可以自由设置宽度和高度**.

> 常见的块标签有: **ul、li、form、h1~h6、hr、p、div**

行内元素: 不会自己独占一行,宽度和高度会根据自身内容撑开,在宽度允许的情况下,后来的宽度允许的话会自动排在右边.**除了不可以设置宽度和高度,也不可以设置内边距`padding`和外边距`margin`**
> 常见的行内标签有: **a、big、br、em、img、input、label、select、span、textarea**
#### 2.标签元素的转化
块元素 -> 行内元素: 
```html
display:inline;
```
行内元素 -> 块元素:
```html
display:block;
```
**一般情况下这样的转化并不能满足要求,我们需要元素既能够修改宽度高度,内边距外边距又可以显示在一行之内:**
```html
dipslay:inline-block;
```
<h2 id="2">2.CSS选择器以及优先级</h2>  

#### 1.css常用的选择器:  
1. 通用选择器: 同时选中页面中的所有元素.
2. 标签选择器: 选中页面中对应的所有标签.
3. 类选择器: 选择同一类名所对应的标签.
4. id选择器: 选中特定id的标签, id具有唯一性.
5. 兄弟选择器: 根据从属关系,选择同一层级的元素, ~查找后边所有的兄弟元素. +查找后边一个兄弟元素.
6. 直接后代选择器: 有直接层级关系的元素.
7. 属性选择器: 获取包含某一属性名的元素.
8. 伪类: 对于特殊的场景使用的标签,例如段落首行或鼠标进入,选择第一个子标签,选择指定位置的子元素等.
9. 后代选择器: 根据父类标签和子类标签选择元素.
10. 群组选择器: 满足其中的一个标签元素.
11. 复合选择器: 同时满足多个条件的元素.
12. 否定伪类选择器: 选择非指定类型的元素.
13. 序号选择器: 获取子元素中指定位置的元素.

[查看具体内容](https://darielchen.github.io/Full-StackWebTips/source/2.CSS%E9%80%89%E6%8B%A9%E5%99%A8%E4%BB%A5%E5%8F%8A%E4%BC%98%E5%85%88%E7%BA%A7.html)

#### 2.选择器的优先级:
1. 权值加到一起，大的优先,如果权值相同，后定义的优先.

类型 | 权值
---|---
通用选择器 | 0
标签选择器 | 1
类选择器 | 10
属性选择器 | 10
伪类选择器 | 10
id选择器 | 100
!important修饰符 | 1000

2. 优先级排序: !important修饰符>内联的样式>id选择器>类选择器>标签选择器! = 伪类选择器 = 属性选择器>*选择器>继承过来的样式


<h2 id="3">3.CSS的浮动和定位</h2> 

#### 1.`float`浮动:
为了让多个块元素显示在一行之内,常用的属性有两个: `left`和`right`.  
[查看具体效果](https://darielchen.github.io/Full-StackWebTips/source/3.CSS%E7%9A%84%E6%B5%AE%E5%8A%A8%E5%92%8C%E5%AE%9A%E4%BD%8D.html)  

#### 2.`position`定位:
通过定位设置页面中元素的位置.

可选值 | 作用
---|---
static | 默认值，元素没有开启定位
relative | 开启元素的相对定位
absolute | 开启元素的绝对定位
fixed | 开启元素的固定定位 

**偏移量**可以有四个属性: `left`、`right`、`top`、`bottom`.分别表示距离左右上下的距离,通常设置两个值就可以确定需要定位的位置了.

**层级**:
1. 定位元素 > 浮动元素 > 文档流中的元素.
2. 当元素开启了定位以后，可以通过z-index来设置元素的层级.
3. z-index值越高元素越优先显示.
4. 如果z-index值一样，或者都没有z-index则优先显示下边的元素.
5. 父元素永远不会盖住子元素.


**定位类型**

##### 1. 相对定位`relative`:
1. 设置后如果不设置偏移量,元素位置不会发生改变.  
2. 相对定位元素相对于其自身在文档流中的位置来定位.
3. 相对定位依然还是属于当前文档流.
4. 相对定位不会改变元素的性质，块元素还是块元素，内联元素还是内联元素.
5. 相对定位的元素会提升一个层级.

##### 2. 绝对定位`absolute`:
1. 元素设置绝对定位以后，如果不设置偏移量，元素的位置不会发生变化.
2. 绝对定位的元素是相对于距离他最近的开启了定位的祖先元素进行定位，如果所有的祖先元素都没开启定位，则相对于浏览器窗口进行定位.
3. 绝对定位的元素会完全脱离文档流.
4. 绝对定位会改变元素的性质.内联变块，块的高度和宽度都被内容撑开，并且不独占一行.
5. 绝对定位会使元素提升一个层级

##### 3. 固定定位`fixed`:
1. 固定定位是一种特殊的绝对定位，它的特点大部分都和绝对定位一样.
2. 不同的是，固定定位的元素永远都是相对于浏览器窗口进行定位的.并且他不会随滚动条滚动.

[查看具体效果](https://darielchen.github.io/Full-StackWebTips/source/3.CSS%E7%9A%84%E6%B5%AE%E5%8A%A8%E5%92%8C%E5%AE%9A%E4%BD%8D.html)  


<h2 id="4">4.CSS的高度塌陷问题</h2>  

##### 1.高度塌陷的原因及后果:  
父元素在文档流中高度默认是被子元素撑开的，当子元素脱离文档流以后，将无法撑起父元素的高度，也就会导致父元素的高度塌陷.  
父元素的高度一旦塌陷,所有标准流中元素的位置将会上移，导致整个页面的布局混乱.
##### 2.高度塌陷的解决方法:
1. 开启父元素的BFC`Block Formatting Context`块级格式化环境.  
BFC是元素的隐含属性，默认是在关闭状态的,可以通过一些特殊的样式，来开启BFC.

开启BFC以后元素将会具有如下特性:
- 父元素的垂直外边距不会与子元素重叠
- 开启BFC的元素不会被浮动元素所覆盖
- 开启BFC的元素可以包含浮动子元素  

开启BFC的方式:
- 设置元素浮动
- 设置元素绝对定位
- 设置元素的类型为`inline-block`
- 设置overflow为一个非默认值,一般为:`overflow:hidden`

[查看具体内容](https://darielchen.github.io/Full-StackWebTips/source/4.CSS%E7%9A%84%E9%AB%98%E5%BA%A6%E5%A1%8C%E9%99%B7%E9%97%AE%E9%A2%98%E8%A7%A3%E5%86%B3%E6%96%B9%E6%A1%881.html)


2. 在塌陷的父元素的最后添加一个空白的div，然后对该div进行清除浮动
```html
<div id="box1">
    <div id="box2"></div>
    <!--clear可以用来清除其他浮动元素对当前元素的影响 none，默认值，不清除浮动 left，清除左侧浮动元素对当前元素的影响 right，清除右侧浮动元素对当前元素的影响 both，清除两侧浮动元素对当前元素的影响
    -->
    <div style="clear:both"></div>
</div>
```
但这样做会在页面中添加多余的结构.  
[查看具体内容](https://darielchen.github.io/Full-StackWebTips/source/4.CSS%E7%9A%84%E9%AB%98%E5%BA%A6%E5%A1%8C%E9%99%B7%E9%97%AE%E9%A2%98%E8%A7%A3%E5%86%B3%E6%96%B9%E6%A1%882.html)

3. 使用after伪类，向父元素后添加一个块元素，并对其清除浮动,该种方式的原理和方法二原理一样，但是不用向页面中添加对于的结构.
```html
.clearfix:after{
    content:"";
    display:block;
    clear:both;
}
```  
[查看具体内容](https://darielchen.github.io/Full-StackWebTips/source/4.CSS%E7%9A%84%E9%AB%98%E5%BA%A6%E5%A1%8C%E9%99%B7%E9%97%AE%E9%A2%98%E8%A7%A3%E5%86%B3%E6%96%B9%E6%A1%883.html)

4. 当子元素和父元素相邻的垂直外边距会发生重叠，子元素的外边距会传递给父元素.

```html
<style>
    #box4{
        width: 200px;
        height: 200px;
        background-color: palevioletred;
    }
    #box5{
        width: 100px;
        height: 100px;
        background-color: cornflowerblue;
        /*子元素和父元素相邻的垂直外边距会发生重叠，子元素的外边距会传递给父元素*/
        margin-top: 100px;
    }
</style>

<div id="box4" class="clear-fix">
    <!--<table></table>-->
    <div id="box5"></div>
</div>
```  
也就是父元素的位置会随着子元素设置了margin-top而向下移动了100px,这时需要在box5前添加`<table></table>`
结合上面3.中的伪类样式:
```html
.clear-fix:before,
.clear-fix:after{
    content: '';
    display: table;
    clear: both;
}
```
这样以后碰到类似问题就可以直接用了.

[查看具体内容](https://darielchen.github.io/Full-StackWebTips/source/4.CSS%E7%9A%84%E9%AB%98%E5%BA%A6%E5%A1%8C%E9%99%B7%E9%97%AE%E9%A2%98%E8%A7%A3%E5%86%B3%E6%96%B9%E6%A1%884.html)


<h2 id="5">5.Flexbox布局</h2>  
#### 1.Flexbox布局的两种方式:  
`display: inline-flex;`:将对象作为弹性伸缩盒展示,用于行内元素.  
`display: flex;` :将对象作为弹性伸缩盒展示,用于块级元素.  
#### 2.常用属性
##### 1.flex-direction
用于指定Flex**主轴**的方向,继而决定 Flex子项在Flex容器中的位置. 
###### 取值：row | row-reverse | column | column-reverse
- row：默认值,表示水平方向从左到右排列,此时水平方向轴线为主轴.
- row-reverse：与row相反.
- column：表示垂直方向从上到下排列,此时垂直方向轴线为主轴.
- column-reverse：与column相反.  

<!--[查看具体效果]()-->
##### 2.justify-content
用于指定主轴(水平方向)上Flex子项的对齐方式.
###### 取值：flex-start | flex-end | center | space-between | space-around  
- flex-start：默认值,表示与行的起始位置对齐.
- flex-end：表示与行的结束位置对齐.
- center：表示与行中间对齐.
- space-between：表示两端对齐,中间间距相等.要注意特殊情况,当剩余空间为负数或者只有一个项时,效果等同于flex-start.
- space-around：表示间距相等,中间间距是两端间距的2倍.要注意特殊情况，当剩余空间为负数或者只有一个项时,效果等同于center.  

<!--[查看具体效果]()-->
##### 3.align-items
用于指定**侧轴**(垂直方向)上Flex子项的对齐方式.
###### 取值：stretch | flex-start | flex-end | center | baseline
- stretch：默认值,当Flex子项未设置高度或者高度值为auto时,stretch起作用,将Flex子项高度设置为行高度.这里需要注意,在只有一行的情况下,行的高度为容器的高度,即Flex子项高度为容器的高度.
- flex-start：表示与侧轴开始位置对齐.
- flex-end：表示与侧轴的结束位置对齐.
- center：表示与侧轴中间对齐.
- baseline：表示基线对齐,当行内轴与侧轴在同一线上,即所有Flex子项的基线在同一线上时,效果等同于flex-start.  

[查看具体效果]()
##### 4.flex-wrap
用于指定Flex子项是否换行.
###### 取值：nowrap | wrap | wrap-reverse
- nowrap：默认值,表示不换行,Flex子项可能会溢出.
- wrap：表示换行,溢出的Flex子项会被放到下一行.
- wrap-reverse：表示反方向换行.  

<!--[查看具体效果]()-->
##### 5.align-content
该属性只作用于多行的情况下,用于多行的对齐方式.
###### 取值：stretch | flex-start | flex-end | center | space-between | space-around
- stretch：默认值,当Flex子项未设置高度或者高度值为auto时,stretch起作用,将Flex子项高度设置为行高度.
- flex-start：表示各行与侧轴开始位置对齐,第一行紧靠侧轴开始边界,之后的每一行都紧靠前面一行.
- flex-end：表示各行与侧轴的结束位置对齐,最后一行紧靠侧轴结束边界,之后的每一行都紧靠前面一行.
- center：表示各行与侧轴中间对齐.
- space-between：表示两端对齐,中间间距相等.要注意特殊情况,当剩余空间为负数时,效果等同于flex-start.
- space-around：表示各行之间间距相等,中间间距是两端间距的2倍.要注意特殊情况,当剩余空间为负数时,效果等同于center.  

<!--[查看具体效果]()-->
##### 6.align-self
该属性用来**单独指定**某Flex子项的对齐方式.
###### 取值：auto | flex-start | flex-end | center | baseline | stretch
- auto: 默认值.元素继承了它的父容器的 align-items 属性.如果没有父容器则为stretch.
- flex-start: 元素位于容器的开头.弹性盒子元素的侧轴(纵轴)起始位置的边界紧靠住该行的侧轴起始边界.
- flex-end: 元素位于容器的结尾.弹性盒子元素的侧轴(纵轴)起始位置的边界紧靠住该行的侧轴结束边界.
- center: 元素位于容器的中心.弹性盒子元素在该行的侧轴（纵轴）上居中放置.（如果该行的尺寸小于弹性盒子元素的尺寸,则会向两个方向溢出相同的长度）.
- baseline: 元素位于容器的基线上.如弹性盒子元素的行内轴与侧轴为同一条,则该值与'flex-start'等效.其它情况下,该值将参与基线对齐.
- stretch: 元素被拉伸以适应容器.

<!--[查看具体效果]()-->
#### 3.复合属性flex
##### 复合属性flex,是flex-grow 、flex-shrink和flex-basis 的简写属性,用来指定Flex子项如何分配空间.
- flex-grow：默认值为0,若省略则被默认为1.
- flex-shrink：默认值为1,省略时默认为1.
- flex-basis：默认值为auto,省略时默认为0%.

<!--[查看具体效果]()-->
