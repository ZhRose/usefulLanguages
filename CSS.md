# CSS



###  1.position定位

##### 常用的有五种形式分别是 static, relative,absolute,fixed,sticky,当设置定位后，可以使用z-index来调节元素的层级关系，当然z-index也可以设置为负值，这时候页面中的文档流将会遮盖定位的元素

```
1.static: 未设置定位或者定位的初始值
2.relative: 相对定位，定义后不会使元素脱离文档流，设置偏移量（offset）后，当前位置仍然为该元素所占用的位置，设置后优先级也会上升
3.absolute：绝对定位，定义后会使元素脱离文档流，如果祖先元素中未设置相对定位，则会默认的和html外层的初始内容块对齐位置，如果祖先设置定位则会优先和祖先中最近定位的元素对齐位置，设置后优先级会上升
4.fixed：固定定位，设置后图片在文章中的位置不会发生改变，和absolute一样也会脱离文档流，层级也会提升
5.sticky :粘滞定位，和relative类似，参照物为祖先元素中最近的有滚动条的元素,该元素不会在指定位置外的地方发生移动
```



### 2.弹性盒

##### 通过display来设置，有三个属性分别为none,flex,inline-flex，还可以通过flex-direction来指定主轴和横轴方向，水平则为row,竖直为column,还可以通过添加-reverse来设置是否需要倒叙排列，flex-warp是用来指定排列是否需要换行，默认值是nowrap，连写形式flex-flow设定轴向和是否换行

```
none:未设置或默认初始值
flex：设置为块级弹性盒子，后白你的容器会自动按照块级元素性质排列
inline-flex :设置为行内块弹性容器，后面的容器还会默认按照同行排列

flex-basis  :容器基础值大小默认值auto,也可以根据basis值给主轴方向元素设置大小
flex-shrink 指的是收缩系数，默认值是1，计算的是相对比例
flex-grow是生长系数，默认值是1，计算的是相对比
flex:可以同时设置shrink,grow,basis值,设置为auto自动分配空间

justify-content  指的是主轴上的对齐方式
align-items align-content设  指的是侧轴上的对齐方式
上述两种对齐方式都有下述选项
			start 沿着开始位置排列
			end  主轴顺序排列，最后元素靠边框
			center	水平（竖直）居中排列
             space-around  将空白分给元素周围，外边可能空间不一致
             space-between	将空表分给元素中间
             space-evently	将空白元素分给平均分给元素的周围



```



### 3.外边距折叠问题

##### 当使用盒子模型时，如果兄弟元素之间的外边距不一样时会默认选取距离较小的值作为二者的外边距的大小，防止元素之间的距离过大导致的折叠问题。

##### 当父子元素之间的外边据重合时，给子元素设置外边距会默认的传递给父元素，导致父元素也发生移动，解决方法通过在父元素或子元素之间添加内容或内边距来隔开外边距或者通过定位或者弹性盒来实现一个垂直居中的效果。



### 4.居中方式总结

##### 1.盒子模型：盒子模型可以通过  水平外边距+元素宽度=外部容器宽度公式，来实现水平居中，缺点是垂直方向会发生外边距折叠问题导致垂直居中无法实现

```html
 .box1{
            height: 100px;
            width: 100px;
            background: #bfa;
            margin: 0,auto;
        }
```



##### 2.定位实现居中：通过给子元素设置绝对定位，给父元素设置相对定位，然后再给子元素的偏移量全部设置为‘ 0 ’以后，再通过给margin设置auto属性即可,缺点是需要找到父元素并设置相对定位且代码比较冗长

```html
 .box1{
           position: absolute;
           top: 0;
           bottom: 0;
           left: 0;
           right: 0;
           margin: auto；
        }
```



##### 3.通过将外部容器通过display=tabel-cell变成表格，然后通过vertical-align 和margin=0，auto来达到水平竖直居中或者通过将子元素设置为inlin-block然后再设置text-align也能达到一种居中的效果,缺点是外部容器不太灵活无法使用margin来达到居中

```html
 .box4{
            display: table-cell; 
            vertical-align: middle;
            margin: 0,auto;//二者选其一
        }
        .box5{
            display: inline-block;
            text-align: center;
        }
```



##### 4.弹性盒实现居中的方式非常简单，分别通过主轴和侧轴实现居中的方式即可

```html
.box6{
            display: flex;
            justify-content: center;
            align-items: center;
        }
```



##### 5.定位结合平移translateX和translateY来实现页面居中的效果,translate不会使元素脱离文档流，可以设置px或者百分数的单位，百分数相对的是自身大小

```html
.box7{
		width:300px;
		height:300px;
		position:absolute;
		top:50%
		left:50%
		transform:translateX(-50%);
		transform:translateY(-50%0);
}
```





> 引入方式
>          内嵌式：css直接写在style标签中
>          外联式：写在单独的css文件中，通过link标签引入
>          行内式：直接写在HTML标签中，需要加style引入



### 选择器

- 标签选择器：标签名+｛css内容｝，同名标签也会显示该内容

- 类选择器：.类名{}，在对应的标签中加class属性，通过类名找到该标签，类名只能由数字字母下滑线中划线组成，不能以数字中划线开头，一个标签可以使用多个类名，需要空格隔开即可

- id选择器：#id名{}，所有标签都有id属性，id一个界面只能有一个。

- 通配符选择器：*{}，将所有标签设置样式，一般用于除去外间距margin和内间距padding
	文字字体和文本样式

- 后代选择器：标签名加空格加子代标签名，样式默认会给后代都添上

- ​    子代选择器：标签名>标签名{}，子代只包括儿子

- ​    并集选择器：选择器1，选择器2{}，同时控制多个标签设置样式

- ​    复合选择器：选择器1选择器2{}，紧挨着

- ​    兄弟选择器：兄+弟｛｝紧随其后的变颜色，兄～弟｛｝选中的是中间所有的

- >   ` hover `伪类选择器：选择器:hover{}，选中鼠标悬停在元素上的状态，设置样式 ， :visited只能用于访问过的链接，涉及隐私，慎用，:link用来表示未访问的链接，：active点击超链接会显示的状态
	>    :first-of-child第一个子元素，:first-of-type同类型中的第一个子元素，:nth-child(任意数)第n个子元素，:ntg-last-child()倒数第n个子元素，:only-child唯一的子元素
	>     选择器：not(选择器)，否定伪类，除了某些元素，伪元素语法::before标签起始位置，::after标签结束位置，conten可以在该位置添加内容，不算网页中的正式内容，::selection表示选中的文字内容
	>   伪类是具有顺序的，同一个类设置同一个可以同时存在的样式，会后面覆盖前面

	

> emmet语法
>   标签名div
>   类选择器.类名
>   id选择器#id
>   交集选择器p.red#one
>   子代选择器ul>li{}*个数

##### 属性  

   font-size:文字大小，默认16px,1em就是一个font-size，rem参照于根元素 

​     font-weight:字体粗细，正常为400,加粗700

​     font-style:字体样式（是否倾斜），italic

​     font-family:字体系列，微软雅黑，苹体

​     sans-serif:无衬线字体笔画粗细均匀，网页使用

​     serif:衬线字体，首尾有笔锋装饰 ，报纸书籍应用

​     monospace:等宽字体，程序员编写，利于代码阅读 Consolas，fire code

 @font-face可以远程提供字体供用户使用，内有src和font-family属性（自定义名称），涉及版权问题

>  复合属性：就是多个属性连写的形式，属性之间需要加空格，font有顺序

 text-indent:字体缩进效果，一般设置为2em，1em代表一个字节长度

 text-align:文本水平对齐方式，left为左对齐，center为居中对齐，right为右对齐，如果要让水平元素居中，只需给父级元素加text-align即可

 text-decoration:给文本加装饰线，underline 加下划线，line-through加删除线，overline上划线，none无装饰线。

line-height:控制一行的上下行间距，取值第一种数字加px，第二种倍数（font-size的倍数）


  background-image(url)：设置背景图片

 background-repeat(bgr)：repeat水平和垂直方向都平铺，no-repeat不平铺，repeat-x沿着水平方向平铺，  repeat-y沿着垂直方向平铺

  background-position：背景图位置，center，top，bottom可以连写，没有顺序

##### 元素显示模式
块级元素：可以设置宽高，独占一行，代表标签 

  div,，p，h，ul，li，dl…默认宽度和他爹一样

  行内元素：一行显示多个，不能设置宽高，代表标签，span，，a，strong…

  行内块元素：一行可以设置多个，可以设置宽高，代表元素input，textarea，button，select

  三种模式转化，通过加display属性，block，inline-block，inline

  包含块：包含块就是离当前元素最近的祖先块元素
###### 继承
> 子标签默认会继承父标签中的文本样式，如果子标签自带有样式，则不会被继承



##### 盒子模型
   border为属性，可以连写为像素（粗细）+solid（线条种类）+颜色，datted为点线，dashed虚线，solid为实线，加-方向，表示单个方向添加。

outline是轮廓线，box-shadow是阴影，作为装饰，不会影响布局
图标字体 iconfont （小图标随意改大小）

第三方图标字体库!
浮动 float使元素脱离文档流，none，left左移，right右移，同行排列，浮动元素不会盖住文字，可以设置环绕效果，脱离文档流，块元素不再单独占一行，行内元素变成块元素

 浮动会导致高度塌陷问题：通过开启BFC后 ，子元素的垂直外边距不会传递给父元素，元素不会被浮动元素所覆盖，元素可以包含浮动的子元素。

浮动会开启BFC，overflow也会开启BFC，display：flow-root，还有很多方式
clear ：left，right清除浮动元素产生的影响
