# CSS复合选择器

复合选择器是由两个或多个基础选择器，通过不同的方式组合而成的,目的是为了可以选择更准确更精细的目标元素标签。

## 一、交集选择器

交集选择器由两个选择器构成，其中第一个为标签选择器，第二个为class选择器，两个选择器之间不能有空格，如`h3.special`。

![](../images/css/pic8_1.png)

**记忆技巧：**交集选择器是并且的意思，即...又...的意思。比如：`p.one`选择的是类名为`.one`的段落标签。  

用的相对来说比较少，不太建议使用。

## 二、并集选择器

并集选择器（CSS选择器分组）是各个选择器通过<strong style="color:#f00">逗号</strong>连接而成的，任何形式的选择器（包括标签选择器、class类选择器id选择器等），都可以作为并集选择器的一部分。如果某些选择器定义的样式完全相同，或部分相同，就可以利用并集选择器为它们定义相同的CSS样式。

![](../images/css/pic8_2.png)

**记忆技巧：**并集选择器是和的意思，就是说，只要逗号隔开的，所有选择器都会执行后面样式，通常用于集体声明。比如`.one, p , #test {color: #F00;}`表示` .one`和`p`和`#test`这三个选择器都会执行颜色为红色。  

## 三、后代选择器

后代选择器又称为包含选择器，用来选择元素或元素组的后代，其写法就是把外层标签写在前面，内层标签写在后面，中间用空格分隔。当标签发生嵌套时，内层标签就成为外层标签的后代。

![](../images/css/pic8_3.png)

子孙后代都可以这么选择。 或者说，它能选择任何包含在内的标签。 

## 四、子元素选择器

子元素选择器只能选择作为某元素子元素的元素。其写法就是把父级标签写在前面，子级标签写在后面，中间跟一个 &gt; 进行连接，注意，符号左右两侧各保留一个空格。

![](../images/css/pic8_4.png)

**注意：**这里的儿子指的是亲儿子，不包含孙子、重孙子之类。

比如：`.demo > h3 {color: red;}`说明  h3 一定是demo 亲儿子，demo 元素包含着h3。

## 五、测试题

```html
<div class="nav">    <!-- 主导航栏 -->
  <ul>
    <li><a href="#">公司首页</a></li>
	<li><a href="#">公司简介</a></li>
	<li><a href="#">公司产品</a></li>
	<li>
         <a href="#">联系我们</a>
		 <ul>
		    		<li><a href="#">公司邮箱</a></li>
		    		<li><a href="#">公司电话</a></li>
		 </ul>
	</li>
  </ul>
</div>
<div class="sitenav">    <!-- 侧导航栏 -->
  <div class="site-l">左侧侧导航栏</div>
  <div class="site-r"><a href="#">登录</a></div>
</div>
```

在不修改以上代码的前提下，完成以下任务：

1. 链接 登录 的颜色为红色,同时主导航栏里面的所有的链接改为蓝色     (简单)

2. 主导航栏和侧导航栏里面文字都是14像素并且是微软雅黑。（中等)

3. 主导航栏里面的一级菜单链接文字颜色为绿色。（难)


## 六、属性选择器

选取标签带有某些特殊属性的选择器 我们成为属性选择器

~~~css
/* 获取到 拥有 该属性的元素 */
div[class^=font] { /*  class^=font 表示 font 开始位置就行了 */
    color: pink;
}
div[class$=footer] { /*  class$=footer 表示 footer 结束位置就行了 */
    color: skyblue;
}
div[class*=tao] { /* class*=tao  *=  表示tao 在任意位置都可以 */
    color: green;
}
~~~

~~~html
<div class="font12">属性选择器</div>
    <div class="font12">属性选择器</div>
    <div class="font24">属性选择器</div>
    <div class="font24">属性选择器</div>
    <div class="font24">属性选择器</div>
    <div class="24font">属性选择器123</div>
    <div class="sub-footer">属性选择器footer</div>
    <div class="jd-footer">属性选择器footer</div>
    <div class="news-tao-nav">属性选择器</div>
    <div class="news-tao-header">属性选择器</div>
    <div class="tao-header">属性选择器</div>
~~~

## 七、伪元素选择器（CSS3)

1. E::first-letter文本的第一个单词或字（如中文、日文、韩文等）
2. E::first-line 文本第一行；
3. E::selection 可改变选中文本的样式；

~~~css
p::first-letter {
  font-size: 20px;
  color: hotpink;
}

/* 首行特殊样式 */
p::first-line {
  color: skyblue;
}

p::selection {
  /* font-size: 50px; */
  color: orange;
}
~~~

4、E::before和E::after

在E元素内部的开始位置和结束位创建一个元素，该元素为行内元素，且必须要结合content属性使用。

~~~css
div::befor {
  content:"开始";
}
div::after {
  content:"结束";
}
~~~

E:after、E:before 在旧版本里是伪元素，CSS3的规范里“:”用来表示伪类，“::”用来表示伪元素，但是在高版本浏览器下E:after、E:before会被自动识别为E::after、E::before，这样做的目的是用来做兼容处理。

E:after、E:before后面的练习中会反复用到，目前只需要有个大致了解

":" 与 "::" 区别在于区分伪类和伪元素

