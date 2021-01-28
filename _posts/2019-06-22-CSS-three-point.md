---
layout: post
title: "「CSS」三大特性**继承、 优先级和层叠。**"
subtitle: " From CSDN Blog"
author: "Yuzj"
header-img: "img/post-bg-web.jpg"
header-mask: 0.3
catalog: true
tags:
- CSS
---

**继承：**即子类元素继承父类的样式;

**优先级：**是指不同类别样式的权重比较;

**层叠：**是说当数量相同时，通过层叠(后者覆盖前者)的样式。

**css****选择符分类**

首先来看一下css选择符(css选择器)有哪些?

1.标签选择器(如：body,div,p,ul,li)

2.类选择器(如：class="head",class="head_logo")

3.ID选择器(如：id="name",id="name_txt")

4.全局选择器(如：*号)

5.组合选择器(如：.head .head_logo,注意两选择器用空格键分开)

6.后代选择器 (如：#head .nav ul li 从父集到子孙集的选择器)

7.群组选择器 div,span,img {color:Red} 即具有相同样式的标签分组显示

8.继承选择器(如：div p,注意两选择器用空格键分开)

9.伪类选择器(如：就是链接样式,a元素的伪类，4种不同的状态：link、visited、active、hover。)

10.字符串匹配的属性选择符(^ $ *三种，分别对应开始、结尾、包含)

11.子选择器 (如：div>p ,带大于号>)

12.CSS 相邻兄弟选择器器 (如：h1+p,带加号+)

**css****优先级**

当两个规则都作用到了同一个html元素上时，如果定义的属性有冲突，那么应该用谁的值的，CSS有一套优先级的定义。

#### **不同级别**

1. 在属性后面使用 !important 会覆盖页面内任何位置定义的元素样式。

2. 作为style属性写在元素内的样式

3. id选择器

4. 类选择器

5. 标签选择器

6. 通配符选择器

7. 浏览器自定义或继承

    **总结排序：****!important >** **行内样式****>ID选择器** **>** **类选择器** **>** **标签** **>** **通配符** **>** **继承** **>** **浏览器默认属性**

#### **同一级别**

同一级别中后写的会覆盖先写的样式

上面的级别还是很容易看懂的，但是有时候有些规则是多个级别的组合，像这样

```html
<!doctype html>
 <html lang="en">
 <head>
     <meta charset="UTF-8">
     <title>Document</title>
     <style type="text/css">
         div.test{
             background-COLOR:#a00;
             width:100px;
             height: 100px;
         }

.test.test2{
    	 background-COLOR:#0e0;
      	 width:100px;
 		 height: 100px;
   }

</style>

</head>

<body>

    <div class="test test2"></div>
    
</body>

</html>
```

到底div是应用那条规则呢，有个简单的计算方法（经园友提示，权值实际并不是按十进制，用数字表示只是说明思想，一万个class也不如一个id权值高）

- 内联样式表的权值为 1000
- ID 选择器的权值为 100
- Class 类选择器的权值为 10
- HTML 标签选择器的权值为 1

 我们可以把选择器中规则对应做加法，比较权值，如果权值相同那就后面的覆盖前面的了，div.class的权值是1+10=11，而.test1 .test2的权值是10+10=20，所以div会应用.test1 .test2变成绿色

![clip_image002](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/clip_image002.png)![clip_image002](https://pg12138.oss-cn-beijing.aliyuncs.com/1_120816005841_3.jpg?Expires=1573368340&OSSAccessKeyId=TMP.hfxbAPugHbYrw7V8RTSk9SxSVJxmfKUYD7mdetre5kHN1e2EZfgGsrNCCS2ByXT7Xu5Gopb3GxmCscsqnqrSJymw47EaBffFPShwpK7HJkuwCpgeM1dAgbajixNmAs.tmp&Signature=pJxYzo1Tpus1crJiOZw%2BDvE127g%3D)

#### **另外一种理解方式：**

CSS优先级：是由四个级别和各级别的出现次数决定的。

四个级别分别为：行内选择符、ID选择符、类别选择符、元素选择符。

优先级的算法：

每个规则对应一个初始"四位数"：0、0、0、0

若是 行内选择符，则加1、0、0、0

若是 ID选择符，则加0、1、0、0

若是 类选择符/属性选择符/伪类选择符，则分别加0、0、1、0

若是 元素选择符/伪元素选择符，则分别加0、0、0、1

算法：将每条规则中，选择符对应的数相加后得到的”四位数“，从左到右进行比较，大的优先级越高。

#### **需注意的：**

①、!important的优先级是最高的，但出现冲突时则需比较”四位数“;

②、优先级相同时，则采用就近原则，选择最后出现的样式;

③、继承得来的属性，其优先级最低;

!important > 行内样式>ID选择器 > 类选择器 > 标签 > 通配符 > 继承 > 浏览器默认属性

*css选择器使用强烈建议采用低权重原则，利于充分发挥css的继承性，复用性，模块化、组件化。

**CSS****选择器的解析原则**

​         以前一直认为选择器的定位DOM元素是从左向右的方向，查看了网上的相关资料之后才发现原来自己一直都是错的。郑重的声明选择器定位DOM元素是从右往左的方向，这样的好处是尽早的过滤掉一些无关的样式规则和元素 。[为什么CSS选择器是从右往左解析 ？？？](http://blog.csdn.net/jinboker/article/details/52126021)

#### **简洁、高效的****css**

​        所谓高效就是让浏览器查找更少的元素标签来确定匹配的style元素。

​      1.不要再ID选择器前使用标签名

​        解释：ID选择是唯一的，加上标签名相当于画蛇添足了，没必要。

​      2.不要在类选择器前使用标签名

​      解释：如果没有相同的名字出现就是没必要，但是如果存在多个相同名字的类选择器则有必要添加标签名防止混淆如（p.colclass{color：red;} 和 span.colclass{color:red;}

​      3.尽量少使用层级关系；

​         \#divclass p.colclass{color:red;}改为  .colclass{color:red;}

​      4.使用类选择器代替层级关系（如上） 