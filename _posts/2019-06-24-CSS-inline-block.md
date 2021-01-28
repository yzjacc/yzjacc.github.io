---
layout: post
title: "「CSS」inline-block元素vertical-align的问题分析"
subtitle: " From CSDN Blog"
author: "Yuzj"
header-img: "img/post-bg-web.jpg"
header-mask: 0.3
catalog: true
tags:
- CSS
---



**先来解释下这两个标签**

**inline-block:**

字面意思：行内块元素，相当于强制转换，把一个标签设置为行内的块元素，既有块元素的部分特性（支持width\height\maigin-top\margin-bottom），又有行内元素的部分特性(不换行)。

**vertical-align:**

vertical-align 属性设置元素的垂直对齐方式。

该属性定义行内元素的基线相对于该元素所在行的基线的垂直对齐方式。

在表单元格中，这个属性会设置单元格框中的单元格内容的对齐方式。

**可能的值**

| **值**      | **描述**                                                     |
| ----------- | ------------------------------------------------------------ |
| baseline    | 默认。元素放置在父元素的基线上。                             |
| sub         | 垂直对齐文本的下标。                                         |
| super       | 垂直对齐文本的上标                                           |
| top         | 把元素的顶端与行中最高元素的顶端对齐                         |
| text-top    | 把元素的顶端与父元素字体的顶端对齐                           |
| middle      | 把此元素放置在父元素的中部。                                 |
| bottom      | 把元素的顶端与行中最低的元素的顶端对齐。                     |
| text-bottom | 把元素的底端与父元素字体的底端对齐。                         |
| length      |                                                              |
| %           | 使用   "line-height" 属性的百分比值来排列此元素。允许使用负值。 |
| inherit     | 规定应该从父元素继承   vertical-align 属性的值。             |

**现在的问题是使用****inline-block****时遇到关于****vertical-align****的问题：**

HTML+CSS 代码：

<!DOCTYPE html>
```html
<html>

    <head>

        <meta charset="UTF-8">

        <title>浮动定义</title>
    
        <style type="text/css">
    
            div{
    
                border: 1px solid red;
    
            }
    
            .div1 , .div2{
    
                width: 100px;
    
                height: 100px;
    
                display: inline-block;
    
            }
    
        </style>
    
    </head>
    
    <body>
    
        <div class="demo">
    
            <div class="div2"></div>
    
            <div class="div1"></div>
    
        </div>
    
    </body>    

</html>
```

效果：

![img](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-6-24/clip_image003.png)

至于上下的边距，别急，还有更奇怪的，我们往这两个div任意一个里面加点文字

​```html
<!DOCTYPE html>
<html>

    <head>

        <meta charset="UTF-8">

        <title>浮动定义</title>

        <style type="text/css">

            div{

                border: 1px solid red;

            }

            .div1 , .div2{

                width: 100px;

                height: 100px;

                display: inline-block;

            }

        </style>

    </head>

    <body>

        <div class="demo">

            <div class="div2">Web前端</div>

            <div class="div1"></div>

        </div>

    </body>

</html>
```

效果：

![ads](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-6-24/clip_image004.png)

到这就完全摸不着头脑了。

**分析产生的原因：**

经过测试发现，这个下边距跟inline-block的垂直对齐方式有关，也就是vertical-align;

inline-block的默认对齐方式是vertical-block：baseline，由上面可知，就是inline-block元素要根据父元素的基线对齐，那么问题来了，基线又是什么鬼？

inline-block的基线是正常流中最后一个line box的基线，除非，这个line box里面既没有line boxes ，或者其本身overflow属性的计算值不是visible，则它的基线是margin底边缘。

上面这段不是人话，看不懂没关系，下面是人话：

如果一个inline-block元素里面是空的，或者它本身有overflow属性，这种情况下基线是它margin的底边缘。

如果一个inline-block元素里面不是空的（比如里面有文字或者图像），则它的基线由正常流中最后一个line box的基线决定。

如图：基线(Baseline)是大部分字母所“坐”在的，字体的下降部之上的直线。下图红色的直线就是基线。

![text-top  text-bottom  middle  baseline  top  bottom ](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-6-24/clip_image005.gif)

**正经原因：**

第一个盒子，里面是空的，所以它的基线是它的下边框。

第二个盒子，里面有文字，所以它的基线是正常流中最后一个行框的基线决定，也就是第二行的基线。

默认情况下基线对齐，所以它们就变成这样啦。

**解决办法：**

对于行内元素，vertical-align虽然不可见，但实际上【到处都是】！

也就是说，只要是行内元素，一定会受它影响。

在遇到由vertical-align:baseline造成的各种无法理解的怪异现象，可以直接放大招，废掉基线对齐（比如底线对齐、顶线对齐就很好啊），统一对齐方式。

```html
<!DOCTYPE html>

<html>

    <head>

        <meta charset="UTF-8">

        <title>浮动定义</title>

        <style type="text/css">
		   div{

               border: 1px solid red;

            }

			.div1 , .div2{
				
                width: 100px;

                height: 100px;

                display: inline-block;

                /*- 以下三种方式任意选一种都可以             */

                vertical-align: top;

                /*vertical-align: bottom;

                vertical-align: middle;*/

            }

        </style>

    </head>

    <body>

        <div class="demo">

            <div class="div2">Web前端</div>

            <div class="div1"></div>

        </div>

    </body>
    
</html>
```