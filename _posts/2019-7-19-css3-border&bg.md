---
layout: post
title: "「CSS」CSS3的border&background属性"
subtitle: " From Yuzj"
author: "Yuzj"
header-img: "img/post-bg-web.jpg"
header-mask: 0.3
catalog: true
tags:
- CSS3
- CSS
---

### border-radius

![屏幕快照 2019-07-19 下午9.24.24](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-7-19/屏幕快照 2019-07-19 下午9.24.24.png)

书写方式如下

```css
  div {
    width: 200px;
    height: 100px;
    border: 1px solid #000;
    position: absolute;
    left: calc(50% - 50px); /*减号两边必须加空格*/
    top: calc(50% - 50px);
    /* border-radius:50%;
    border-radius:10px;
    border-radius :10px 20px 30px 40px;*/
    /*border-top-left-radius: 10px;
    border-top-right-radius :20px;
    border-bottom-right-radius :30px;
    border-bottom-left-radius :40px;*/
    /* 下面两个像素是代表切割圆的水平垂直半径长度*/
    /*border-top-left-radius : 100px 100px;
    border-top-right-radius: 100px 100px;
    border-bottom-right-radius: 100px 100px;
    border-bottom-left-radius:40px 40px;*/
    /*border-radius:10px 20px 30px 40px/10px 					20px 30px 40px;第一个10px加第二个10px代表左上 				 以此类推	*/
    /*前一半是横坐标后一半是纵坐标*/
  }
```

### box-shadow

![屏幕快照 2019-07-19 下午9.35.51](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-7-19/屏幕快照 2019-07-19 下午9.35.51.png)

box-shadow: 0px 0px 0px 0px #0ff  //外阴影 水平偏移量 垂直偏移量 以边框为标准向两侧同时模糊值 上下左右扩大像素 颜色

box-shadow:insert  0px 0px 0px 0px #0ff  //内阴影 水平偏移量 垂直偏移量 以边框为标准向两侧同时展开模糊值 上下左右扩大像素 颜色

背景颜色在阴影的下面 文字在阴影的上面

```html
<DOCYPE html>
  <html lang="en">
    <head>
      <meta charset="utf-8" />
      <title>title</title>
      <style>
        * {
          margin: 0;
          padding: 0;
        }
        body {
          background-color: #000;
        }
        div {
          position: absolute;
          left: calc(50% - 150px);
          top: calc(50% - 150px);
          width: 300px;
          height: 300px;
          border-radius: 50%;
          box-shadow: inset 0px 0px 50px #fff, inset 10px 0px 80px #f0f,
            inset -10px 0px 80px #0ff, inset 10px 0px 300px #f0f,
            inset -10px 0px 300px #0ff, 0px 0px 50px #fff, -10px 0px 80px #f0f,
            10px 0px 80px #0ff;
        }
      </style>
    </head>

    <body>
      <div></div>
    </body></html
></DOCYPE>

```

效果如下

![屏幕快照 2019-07-19 下午9.48.54](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-7-19/屏幕快照 2019-07-19 下午9.48.54.png)

```html
<DOCYPE html>
  <html lang="en">
    <head>
      <meta charset="utf-8" />
      <title>title</title>
      <style>
        * {
          margin: 0;
          padding: 0;
        }

        body {
          background-color: #000;
        }

        div {
          position: absolute;
          left: calc(50% - 25px);
          top: calc(50% - 25px);
          width: 50px;
          height: 50px;
          background-color: #fff;
          border-radius: 50%;

          box-shadow: 0px 0px 100px 80px #fff, 0px 0px 250px 180px #ff0;
        }
      </style>
    </head>

    <body>
      <div></div>
    </body></html
></DOCYPE>

```

效果如下

![屏幕快照 2019-07-19 下午9.53.54](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-7-19/屏幕快照 2019-07-19 下午9.53.54.png)

### 3.boder-image

该属性直接会覆盖boder-color

#### border-image-source ：

##### 可以引入图片url（）或者渐变色（linear-gradient(red,yellow)）

#### border-image-slice ： 只能写数字 （不写默认值100%）

![屏幕快照 2019-07-19 下午10.00.57](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-7-19/屏幕快照 2019-07-19 下午10.00.57.png)

按照图片分割像素

border-image-slice: 100 100 100 100;(上 右 下 左) fill可以填充内容区 不填写px

如果默认值100% 也就是说整个图会覆盖该四个角

![屏幕快照 2019-11-08 下午7.12.47](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-7-19/屏幕快照 2019-11-08 下午7.12.47.png)

#### border-image-width ：默认值1（倍数） 设置图片背景宽度 如果写auto 会自动取slice的值

#### border-image-outset ：背景边框图片向外延伸

#### border-image-repeat：可以两个参数 一个水平一个垂直

##### stretch默认

![屏幕快照 2019-07-19 下午10.17.30](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-7-19/屏幕快照 2019-07-19 下午10.17.30.png)

##### round

![屏幕快照 2019-07-19 下午10.11.58](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-7-19/屏幕快照 2019-07-19 下午10.11.58.png)

##### repeat

![屏幕快照 2019-07-19 下午10.11.25](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-7-19/屏幕快照 2019-07-19 下午10.11.25.png)

speace

![屏幕快照 2019-07-19 下午10.13.00](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-7-19/屏幕快照 2019-07-19 下午10.13.00.png)

#### border-image：source slice repeat；

### background

##### background-image  

(可以填渐变色与图片路径）可以进行多个填写 第一个没有加载出来 会加载第二个

background-image:url(./#.jpg),url(./#1.jpg);

##### background-position

（多个背景用逗号隔开）处理背景的位置

##### background-origin

![屏幕快照 2019-11-08 下午7.52.11](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-7-19/屏幕快照 2019-11-08 下午7.52.11.png)

（图片从哪个位置开始加载）border-box padding-box（默认值） content-box

##### background-clip

![屏幕快照 2019-11-08 下午7.55.17](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-7-19/屏幕快照 2019-11-08 下午7.55.17.png)

（图片从哪个位置截断）border-box（默认值）padding-box content-box 

text（文字里为背景图片）：特殊写法

```html
-webkit-background-clip:text;<!-- 划重点 一旦设置该属性 文字会变为背景的一部分 效果如下图 -->
background-clip:text;
-webkit-text-fill-color:transparent;
text-fill-color:transparent;
```

![屏幕快照 2019-11-10 下午2.37.33](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-7-21/屏幕快照 2019-11-10 下午2.37.33.png)

##### background-repeat 

round 平铺（拉伸图片） no-repeat  speace（不会改变图片，不够宽度就是空格） 可以为两个值表示xy

写repeat-x 默认no-repeat-y

##### background-attachment

相对于容器进行添加background-position 默认值默认scroll 相当于平时fix相对容器 不相对视口；

local可以跟容器滚轮滚动 ；fix相对于视口不动 但是图片超过容器外 不能显示

##### background-size

cover 不改变图片比例 填充背景 可能超出

contain 不改变图片比例 填充背景 可能repeat

### linear-gradient / radial-gradient 渐变色

linear-gradient (to right,#0f0 20px,#ff0);

linear-gradient (180deg,#0f0 20%,#ff0);

第一个为圆心 ellipse或者circle 

##### 放射半径到哪里：

closest-corner

close-side

farthest-corner

farthest-side

例子 circle-close-side

radial-gradient (circle-close-side at right bottom,#0f0 20%,green 40px,#ff0 40%);

### hsla处理颜色

hsla（360，50%，50%，5）；

### 当不设置border-color时 默认等于currentcolor currentcolor会去取color的值



