---
layout: post
title: "「CSS」CSS3 选择器介绍"
subtitle: " From Yuzj"
author: "Yuzj"
header-img: "img/post-bg-web.jpg"
header-mask: 0.3
catalog: true
tags:
- CSS3
- CSS
---

### Relationship Selectors （关系选择器）

```html
<!DOCTYPE html>
<htmL lang="en'">
  <head>
    <meta charset="UTF-8" />
    <title>Document</title>
    <style>
      /* E + F */
      /* 第一个满足条件的兄弟元素节点 */
      div + .demo {
        background-color: red;
      }

      /* E ~ F */
      /* 所有满足条件的兄弟元素节点 */
      div ~ p {
        background-color: green;
      }
    </style>
  </head>

  <body>
    <div>div</div>
    <span class="demo">234</span>
    <p class="demo">1</p>
    <p>2</p>
    <p>3</p>
    <ul>
      <li>
        <p>4</p>
      </li>
    </ul>
  </body>
</htmL>

```

### Attribute Selectors（属性选择器）

```html
<!DOCTYPE html>
<htmL lang="en'">
  <head>
    <meta charset="UTF-8" />
    <title>Document</title>
    <style>
      div[data~="a"] {
        background-color: red;
      }
    </style>
  </head>

  <body>
    <div class="demo" data="a">data</div>
    <div>data2</div>
  </body>
</htmL>

```

##### E[attr~=“a”]：

存在独立a（a b可以,aa不可以） 

##### E[attr|=“a”]：

a开头或者a-都可以

##### E[attr^=“a”]：

a开头

##### E[attr$=“a”]：

a结尾

##### E[attr\*=“a”]：

存在a就可以（a是 空格 - 都可以）

### Pseudo-Element Selectors（伪元素选择器）

旧版本伪元素选择器可以写一个或者两个冒号 但下面的两个选择器必须写两个

##### E::placeholder 

只能改变 input 字体颜色 （兼容性一般）

##### E::selection 

字体选中状态下可以改变颜色 （bgcolor color）

### Pseudo-Classes Selectors（伪类选择器）

```html
<!DOCTYPE html>
<htmL lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Document</title>
    <style>
      /* body中只能取到宽度 但是root可以取到视口高度 */
      :root,
      body {
        margin: 0;
        height: 100%;
      }

      #red,
      #green,
      #gray {
        height: 100%;
        width: 100%;
      }

      #red {
        background-color: #f20;
      }

      #green {
        background-color: green;
      }

      #gray {
        background-color: gray;
      }

      div[id]:not(:target) {
        display: none;
      }

      div.button-wrapper {
        position: absolute;
        width: 600px;
        top: 400px;
      }

      div.button-wrapper a {
        text-decoration: none;
        color: #fff;
        background-color: #fcc;
        font-size: 30px;
        border-radius: 3px;
        margin: 0 10px;
      }
    </style>
  </head>

  <body>
    <div class="button-wrapper">
      <a href="#red" class="bg red">red</a>
      <a href="#green" class="bg green">green</a>
      <a href="#gray" class="bg gray">gray</a>
    </div>
    <div id="red"></div>
    <div id="green"></div>
    <div id="gray"></div>
  </body>
</html>

```

##### E:not(s):

选择没有 s条件 的元素

##### E:root:

 在html环境（其他环境不确定）和html选择器相等 （根标签选择器）一般不写E

##### E:target:

通过锚点去改变其元素的状态//利用锚点进行页面转换

#### 不常用

##### E:first-child:

所有第一个子元素（子元素是谁 E就写谁 只要是其他元素的子元素 都符合改选择器 考虑其他元素对自己的影响

##### E:last-child:

所有最后一个子元素  只要是其他元素的子元素 都符合改选择器 考虑其他元素对自己的影响

##### E:only-child: 

所有子元素中只有该一个元素 考虑其他元素对自己的影响

#### 常用

##### E:nth-child(n):

所有第几个子级元素 只要是其他元素的子元素 都符合改选择器 css从1开始查数 n是从0开始递增 odd奇数 even偶数 考虑其他元素对自己的影响（假设第一个子元素不是E元素 第二个是则为E:nth-child(2) ）

##### E:nth-last-child(n):

上者取反 倒着查

##### E:first-of-type:

该E类型第一个元素

##### E:last-of-type:

该E类型第一个元素

##### E:only-of-type:

该E类型的仅有的元素 与only-child不同是 该选择器可以在有多种类型子元素下也可以进行选择

##### E:nth-of-type(n):

找同类型的元素 从第n个开始查起

##### E:nth-of-last-type(n):

上者取反

#### 不常用

##### E:empty:

该E什么都没有的元素（空格算内容，注释不算内容）

##### E:checked:

一般改变单选框后的属性

##### E:enabled:

一般在input默认是enabled 可以修改属性

##### E:disabled:

一般直接将disabled加在input 不可以可以修改属性

##### E:read-only:

一般直接将 readonly 加在input value=“文字” 该文字不可以修改

##### E:read-write:

上者可以修改





