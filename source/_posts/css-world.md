---
title: css-world
date: 2018-01-20 22:13:53
tags: css
categories: 前端__CSS
top: 100
---

# 前言
　　与其说是总结，倒不如说是我对这本书的一些笔记，希望借此来巩固并复习这些知识。
买来这本书已经有一段时间了，由于期末的原因最近才开始学习。《css世界》是张鑫旭大神的新作，我买这本书的原因之一是支持一下张大大，我开始关注到[张鑫旭大神](http://www.zhangxinxu.com/)是从他一篇博客开始的，我感觉他博客里面的东西如果没有点基础是看不懂的，因此我也意识到了自己在css学习上还有很长的路要走，所以希望这本书能够让我对css有一个更深的感悟。另外的原因就是这本书的内容十分新颖，并不是那种传统的工具书，现在读起来确实有别于其它技术性书籍。
- - -
# 第一章 概述
　　正如书中前沿写的那样，张大大以一种第一人称的角度，带有情感的来写这本书的内容，用了很多形象的比喻，还配有代码案例，让读者读起来不仅不枯燥，反而更加有趣，这就是有别于其它技术性书籍的原因。对于接下来的笔记我会更多的使用列表来记录。　　

+ 首先书中将css整块内容比作了世界，将不同的操作系统视为各个平行的css世界，不同的浏览器视为各个王国，那么html标签是魔法石，选择器为选择法器，css属性就是魔法师，魔法师通过使用法器来变化魔法石。
+ css能够在历史中完胜SVG靠的就是“*层叠*”这个特性。  
+ 流的概念只要学过css的都会知道，全名称“标准文档流”。是一种基本的定位和布局机制，就像现实生活中的水流一样，块级元素会像水流一样铺满容器盒子，而内联元素则是像木块一样按排列顺序浮在水面上。
+ 所谓的流体布局就是曾经的 css+div 布局   
这就是这一章的内容，并没有特别的东西，接下来开始下一章。　　　

# 第二章 专业术语
　　因为我也不是css初学者了，对这些专业术语比较熟悉，所以就不一一记录了，不过我对这章另一个内容还是很陌生的。搞前端的程序员必须考虑的一件事就是浏览器的兼容性，很多人包括我自己都认为相同的代码在不同的浏览器中出现了不同的表现，这就是bug。但张大大指出，> 这种现象在计算机领域中的专业术语描述应该是"未定义行为",web标准不可能面面俱到，各大浏览器肯定会出现差异。

# 第三章 流、元素与基本尺寸
　　到了这一章好多硬货开始蹭蹭的摆了出来，而且都是我没有接触过的，我是一边流着鼻血一边学习完这些东西，哈哈，都是含金量很高的内容，我得坚持住全部吸收。　　　
## 块级元素
　　以前肤浅的认为块级元素和display:block可以等价，盒子模型也就是那些margin、padding、border、content，然而非也，看来我还真是个前端小白，还得虚心学习啊。
+ 块级元素可以配合clear属性来清除浮动，但不仅是将display设置成block,同样可以是table、list-item,但一般不用list-item，除了兼容性外（ie），还有list-item的特殊性....
+ 盒子分为块级盒子与内联盒子，块级负责结构，内联负责内容。但元素的盒子没这么简单。每个元素其实都有两个盒子，分为外在盒子和内在盒子，内在盒子也叫容器盒子。比如：display:block可以脑补成display：block-block，display:table脑补成block-table。inline-block就很好理解了，外在盒子为内联，可以使元素和图文一行显示，而容器盒子为块级，负责设置宽高。
+ 刚才提到了list-item的特殊性，就因为设置为list-item后会出现像列表一样的符号，原因是它还有一个附加盒子，专门来放这些圆点，数字项目符号，当然了这个附加盒子是张大神为了理解自己给取得名字。　　

## width与height
　　翻到这块内容时，想着不就是设置宽高嘛，还能有啥讲的，看完后才真心觉得这本书买对了。
### width
+ width/height作用在容器盒子
+ width的默认值是auto，包含了四种不同宽度表现：充分利用可用空间、收缩与包裹（如浮动、绝对定位、inline-block、table）、收缩到最小、超出容器限制
+ 在css世界中，盒子分为内在盒子和外在盒子，显示也分为内部显示与外部显示，尺寸也分为内部尺寸与外部尺寸。而外部尺寸为流的精髓。
+ 外部尺寸的块级元素一旦设置了宽度，流动性就丢失了。所谓流动性，并不是看上去的宽度100%，而是一种margin、border、padding、content内容区域自动分配水平空间的机制。所以要记住“无宽度”这条准则，避免“砌砖头，搭积木”这种思维的页面制作。
+ 内部尺寸与流体特性表现为：
1.包裹性：就是内联元素的宽度随着内容的宽度变化自适应，如button和input
2.首选最小宽度：外部容器的宽度为240px,假设宽度为0，里面的Inline-block元素宽度不为0，为首选最小宽度，由内容决定。
3.最大宽度
+ width默认作用在content box上，所以会出现设置宽度为100px后，再设置padding:20px,实际宽度为140px，这种不一致。这种设置宽度，会使流动性丢失。解决方法有：“宽度分离原则”、设置box-sizing，但后者并不能完全解决，因为浏览器都不支持box-sizing:margin-box。  

### height 
+ 如果父类没有明确的高度，只是默认的auto,则后代设置100%无效。解决方法：html,body{height:100%}
+ 设置max-wdith/height的元素权重将超越！important
+ 同一元素设置{min-width:1400px;max-width:1200px},表现为min-width，max-width被忽略了。　　

## 内联元素
+ 内联元素中的内联指“外在盒子”

# 第四章 盒尺寸四大家族
　　更加深入的解读了这四种属性
## 深入理解content
### content与替换元素
1.替换元素是指可以通过修改某个属性值呈现的内容就可以被替换的元素，如&lt;img>&lt;object>&lt;video>&lt;iframe>或者表单元素
  替换元素特性
	* 内容的外观不受页面上的css的影响
	* 有自己的尺寸，很多替换元素在没有明确尺寸时，默认300px*150px,部分元素为0px，如<img>
	* 在很多css属性上有自己的一套表现规则
2.所有的替换元素都是内联水平元素
![p1](http://p3cvr28fw.bkt.clouddn.com/IMG_20180202_185129.jpg "书中截图")
3.替换元素的尺寸计算规则
  + 替换元素的尺寸分为：固有尺寸、HTML尺寸、CSS尺寸
  + 按照渲染的优先级为：CSS尺寸>HTML尺寸>固有尺寸
  + 替换元素的固有尺寸有一个特性：无法改变元素的固有尺寸。
  + 我们平时也会设置&lt;img>的宽高，但这并不是改变了图片的固有尺寸,而是改变了图片的content宽高，content替换内容默认的适配方式是填充(fill)，因此感觉是图片尺寸改变了。在CSS3中可以通过object-fit属性来改变适配方式

4.替换与非替换的距离
  + 将&lt;img>元素的src属性去掉后，就等同于span的内联元素。
  + chrome中所有元素都支持content属性，其它浏览器中只在after,before伪类元素中支持。当使用content属性时，可以让普通标签元素变成替换元素。
  ~~~
  h1{
   content: url(logo.png);
}
~~~
  + 使用content生成的文本无法被选中，无法复制，生成的图片无法设置宽高，无法被下载

### content计数器
+ counter-reset 计数器-重置 作用是给计数器起个名，还有从几开始计数
+ counter-increment 计数器递增 每普照一次，普照源增加一次计数值
+ counter()/counters() 是方法，输出计数值
~~~
   .counter{
   counter-reset:wangxiaoer 2 wangxiaosan 3;
   counter-increment:wangxiaoer wangxiaosan;
}
  .counter:before{
    content:counter(wangxiaoer);
}
.counter:after{
	content:counter(wangxiaosan);
}
~~~
## padding属性
### padding与元素尺寸
+ css中默认的box-sizing是content-box,所以使用padding会增加元素的尺寸
+ 在块级元素中设置足够大的padding，并且为border-box，则width也会无效，内容表现为首选最小长度
~~~
.box{
	box-sizing:border-box;
	width:80px;
	padding:20px 60px;
}
实际宽度为120px;
~~~
+ 内联元素中设置padding不只会影响水平方向，也会影响垂直方向，只是对垂直布局没影响，会和上下元素发生层叠
+ **这种不影响元素布局只出现层叠效果的现象包括**：relative元素定位、box-shadow、outline、内联元素padding。**这些层叠现象分两类**：1是纯视觉层叠，不影响外部尺寸（box-shaow、outline）、2是会影响外部尺寸（inline的padding）。**区分方式**：设置父容器overflow:auto，层叠区域超过父容器时，没有滚动条，则是纯视觉的；如果出现滚动条，则会影响尺寸和布局。点击查看[案例](http://demo.cssworld.cn/4/2-1.php)
+ 应用方面可以使用padding增加点击区域，内联元素padding实现高度可控的分隔线

### padding的百分比值
+ padding不支持负值
+ padding百分比值无论是水平方向还是垂直方向均是相对于宽度计算的
+ 应用方面块状元素可以使用padding进行头图的等比例控制,点击查看[案例](http://demo.cssworld.cn/4/2-3.php)
~~~
.box{
	padding:10% 50%;
	position:relative;
}
.box>img{
	position：absolute;
	left:0;top:0;
	width:100%;
	height:100%;
}
为宽高比5:1的比例固定的头图效果
~~~
+ 内联元素则会断行  

## margin属性
### margin与元素尺寸和相关布局
1.margin与元素的内部尺寸
  + 只有元素是“充分利用可用空间”时，margin才可以改变元素的可视尺寸
~~~
<div class="father">
	<div class="son"></div>
</div>
.father{
	width:300px;
}
.son{
	margin:0 -20px;
}
.son元素宽度为340px;
~~~
  + margin可以方便的实现多流体布局效果，如一侧定宽一侧自适应
~~~
.left{
	width:200px;
	float:left;
}
.right{
	margin-left:220px;
}
~~~
  + 使用margin实现等高,点击查看[案例](http://demo.cssworld.cn/4/3-2.php)
~~~
.column-box{
	overflow:hidden;
}
.column-left,.column-right{
	margin-bottom:-9999px;
	padding-bottom:9999px;
}
原理上是用增加了9999px的背景色，但被padding抵消，然后父元素overflow：hidden,将其隐藏
~~~

### margin的合并
1.块级元素的margin-top与margin-bottom有时会合并成单个外边距，这种现象只发生在块级元素（不包括浮动和绝对定位）还有垂直方向
2.合并的3种场景
 + 相邻兄弟的margin合并
 + 父级和第一个/最后一个子元素
 + 空块级元素的margin合并
 ~~~
 .father{ overflow:hidden;}
 .son{margin:1em 0;}
 <div class="father">
 	<div class="son"></div>
 </div>
 此时margin-top和margin-bottom合并，总共为1em;
 ~~~
3.合并规则
 + 正正取最大值
 + 正负值相加
 + 负负最负值  

### margin:auto
　　以前用auto是在将布局居中方面，也仅仅是会用而已，现在有了更深理解。
+ auto填充规则：1.如果一侧定值，一侧auto，则auto为剩余空间大小。2.如果两侧是auto，则平分剩余空间
+ 如果想让块级元素右对齐，除了浮动，可以设置margin-left:auto,更好的选择;左对齐相反
+ 触发margin:auto计算有一个前提条件：width或height为auto时，元素是具有对应方向的自动填充特性
~~~
一种方法
.father{
		width:200px;
		height: 100px;
		position: relative;
		background: red;
	}
	.son{
		position: absolute;
		top:0;left:0;bottom: 0;right:0; /*格式化宽度和高度*/
		background: black;
		width:180px;
		height: 80px;
		margin:auto;  /*宽高都居中*/
	}
~~~

### margin无效情形
1.display计算值inline的非替换元素的垂直margin是无效的
2.表格中的&lt;tr>和&lt;td>元素或则设置display计算值是table-cell或table-row的元素margin都无效
3.margin合并的时候，更改margin值可能是没有效果的，取决与合并计算规则
4.绝对定位元素非定位方向的margin值，能渲染，但看不到变化，也叫“无效”
5.定高容器的子元素的margin-bottom或则宽度定死的子元素的margin-right定位“失效”，和上一条原因类似
~~~
 .box{height:100px;}
 .son{height:80px;margin-bottom:100px;}
 margin-bottom不会形成100px的外边距
 - - -
 .box{width:100px;}
 .son{width:80px;margin-left:100px;}
 *经自己测试后，这种情况虽然对该设置的元素的定位
 没影响，但是仍会影响后面的元素布局。
 ~~~
 6.鞭长莫及导致的margin无效。
 7.内联特性导致的margin无效

 ## border属性
 　　这块内容不是很多，都是先前遇到的。
 1.首先是border-width不支持百分比值。
 2.border-style默认值none。
 3.border-width默认值media（3px），原因是width为media时style为double才能有表现
 ![规则](http://p3cvr28fw.bkt.clouddn.com/p2.jpg "书中图片")
 4.当没有指定border-color颜色值的时候，会使用当前元素的color计算值作为边框色
 5.border也可以像padding那样增加点击区域，只是设置颜色为透明
 6.图像绘制这些之前接触过，就不赘述了