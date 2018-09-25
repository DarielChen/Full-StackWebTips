# Full-StackWebTips⚡️
Web全栈开发的一些知识点

---

# 目录

[1.标签元素的划分和互相转化](#1)  
[2.CSS选择器以及优先级](#2)  
[3.CSS的浮动和定位](#3)  

---

<h2 id="1">1.标签元素的划分和互相转化</h2>  

#### 标签元素分为两大类: 块元素和行内元素.

块元素: 自己单独占一行，就像一个段落.**可以自由设置宽度和高度**.

> 常见的块标签有: **ul、li、form、h1~h6、hr、p、div**

行内元素: 不会自己独占一行,宽度和高度会根据自身内容撑开,在宽度允许的情况下,后来的宽度允许的话会自动排在右边.**除了不可以设置宽度和高度,也不可以设置内边距`padding`和外边距`margin`**
> 常见的行内标签有: **a、big、br、em、img、input、label、select、span、textarea**
#### 标签元素的转化
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

#### css常用的选择器:  
[CSS选择器以及优先级(打开页面后右击查看源码)](https://darielchen.github.io/Full-StackWebTips/source/2.CSS%E9%80%89%E6%8B%A9%E5%99%A8%E4%BB%A5%E5%8F%8A%E4%BC%98%E5%85%88%E7%BA%A7.html)

#### 选择器的优先级:
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
