---
layout: post
title: "「CSS」转 CSS3的column属性"
subtitle: " From 博客园"
author: "Yuzj"
header-img: "img/post-bg-web.jpg"
header-mask: 0.3
catalog: true
tags:
- CSS3
- CSS
---

CSS3 可以将文本内容设计成像报纸一样的多列布局。像下面这样：

![img](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-7-20/6482.png)

这样的布局称为“多列布局”。

对多列属性分别进行学习：

对于 column 的所有属性，ie10+ 支持，firefox 不支持 column-span。除 firefox 外，所有浏览器都不支持 column-fill 属性。

### 1. column-count: 需要分割的列数

```html
<div>
    记得早先少年时，大家诚诚恳恳，说一句是一句；清早上火车站，长街黑暗无行人，卖豆浆的小店冒着热气；从前的日色变得慢，车、马、邮件都慢，一生只够爱一个人；从前的锁也好看，钥匙精美有样子，你锁了人家就懂了。
</div>
div {
    -moz-column-count: 3;
         column-count: 3;
}
```

通过测试，firefox(version 49.0.1) 需要添加 -moz- 前缀，chrome，opera，safari，不需要添加 -webkit- 前缀也能正常显示，ie10+，edge 不需要添加前缀能正常显示。将页面缩小后(不缩小时由于文本字数不够，只显示两列)显示效果：

![img](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-7-20/1032021-20161012170355531-1117132674.png)

 

### 2. column-gap: 列与列间的间隙

ie下默认为 16px，其它浏览器未明确给出。

```html
<div>
    当我年轻的时候，我梦想改变这个世界；当我成熟以后，我发现我不能够改变这个世界，我将目光缩短了些，决定只改变我的国家；当我进入暮年以后，我发现我不能够改变我们的国家，我的最后愿望仅仅是改变一下我的家庭，但是，这也不可能。当我现在躺在床上，行将就木时，我突然意识到：如果一开始我仅仅去改变我自己，然后，我可能改变我的家庭；在家人的帮助和鼓励下，我可能为国家做一些事情；然后，谁知道呢?我甚至可能改变这个世界。
</div>
div {
    -moz-column-count: 4;
         column-count: 4;
    -moz-column-gap: 40px;
         column-gap: 40px;         
}
```

![img](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-7-20/1032021-20161012171341437-1007051741.png)

 

### 3. column-rule-width: 列与列间的边框宽度

### 4. column-rule-style: 列与列间的边框样式

### 5. column-rule-color: 列与列间的边框颜色

以上三个属性可以简写为 column-rule。同 border 一样，这三个属性里 width 和 color 可以省略其中之一或都省略，浏览器会使用默认的 width 和 color，但是 style 不能省略。**在谷歌浏览器中做测试：**

(1). 省略 width(chrome 默认为 3px, 其它浏览器未明确给出)

```html
<div>
    这么多年咨询信看下来，让我逐渐明白了一件事。很多时候，咨询者心里已经有了答案，来咨询只是想确认自己的确定是对的。所以有些人读过回信后，会再次来信，大概就是因为回答的内容和他们的想法不一样吧。
</div>
div {
    -moz-column-count: 4;
         column-count: 4;
    -moz-column-gap: 40px;
         column-gap: 40px;
    -moz-column-rule-style: solid;
         column-rule-style: solid;
    -moz-column-rule-color: #f00;
         column-rule-color: #f00;
}
```

![img](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-7-20/1032021-20161012173247875-731014877.png)

(2). 省略 color(默认为 rbg(0,0,0))

```html
div {
    -moz-column-count: 4;
         column-count: 4;
    -moz-column-gap: 40px;
         column-gap: 40px;
    -moz-column-rule-width: 2px;
         column-rule-width: 2px;
    -moz-column-rule-style: solid;
         column-rule-style: solid;
}
```

![img](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-7-20/1032021-20161012173604078-36544294.png)

(3). width 和 color 两者都省略

```css
div {
    -moz-column-count: 4;
         column-count: 4;
    -moz-column-gap: 40px;
         column-gap: 40px;
    -moz-column-rule-style: dotted;
         column-rule-style: dotted;
}
```

![img](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-7-20/1032021-20161012173821312-1531762192.png)

 

### 6. column-span: 元素跨越列数(firefox 不支持)

可用值为 1 和 all，默认值为 1。火狐浏览器不支持此属性，但是当使用此属性值时，变现效果和 column-span: 1; 一样，因此可以放心的使用 column-span: 1; 不建议使用 column-span: all;

```css
<div>
    <h2>
		在情感的问题上，很多人都是傻瓜
		</h2>
他在感情上的愚钝就像是门窗紧闭的屋子，虽然爱情的脚步正在缓缓向他走来，可他还是在屋子里走过去又走过来，他也听到了，可是他觉得那是幻想，是有人走错了方向，她终究会明白过来，然后找对自己的方向继续过自己该有的生活。然而联系着美好爱情的生活不单单这么简单，否则恋爱就没有那么美好，那么令人向往了。他喜欢的是另外一个女孩，可是他仅仅向前迈了一小步，最终在院子里徘徊，他觉得女孩走的是另外一条路，她迈着不一样的步伐，很清晰自己的目标和价值所在，走得很快。当然他不止一次的做梦醒来希望女孩旁边给他留了一条路，这样他们就能携手并进，在让大家都变得更好的路上越走越远，这是他最美好的期待。他依然在这件事情纠结着，直到女孩说：“倾尽所有，你会得到你想要的！”
</div>
div {
    -moz-column-count: 4;
         column-count: 4;
}
h2 {
    -moz-column-span: 1;
         column-span: 1;
}
```



![img](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-7-20/1032021-20161012203430687-1204780521.png)

与其他属性不同，column-span 是用在子元素上，表示跨越多少列，好像表格中 col-span 属性一样。因为用的值是 1，而不是 all，所以 firefox 浏览器中的显示效果和其它浏览器一样。

 

### 7.column-width: 列的宽度

```css
<div>
我以前常常想：“朋友有很多，能成为朋友，必定是在生活习惯、爱好、脾气、秉性、追求、对事物的看法、处事风格等一件事或多方面有共同点或相似之处，何其难得。可碰到自己每当安静下来就想起的人，每当自己有空闲时就迫不及待想要去了解的人可遇而不可求。能在人海中相识并愿意花时间想去走进一个人内心这样的人，更应该努力去争取。朋友失去了一个，你还有很多，可是你失去喜欢的人，就是你的大过！”
</div>
div {
    -moz-column-count: 4;
         column-count: 4;
    -moz-column-width: 200px;
         column-width: 200px;    
}
```

![img](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-7-20/1032021-20161012204358609-773879917.png)

这个属性要求比较多：列数与宽度的乘积(column-count * column-width)应该要小于页面的宽度，才能展示想要的四列效果。当文本字数比较少，页面又比较宽时，就显示不了四列，可能只有三列或更少。

 

### 8.column-fill: 如何填充列

这个属性目前只有 firefox 支持，fill 翻译为填充，所以 column-fill 是指定填充列的方式。有两个值可用，balance，列长短平衡，浏览器应尽量减少改变列的长度。auto，列顺序填充，他们将有不同的长度。

 

### 9.columns: 指定列的宽度和数量

这是一个合写属性，是 column-width 和 column-count 的合写。

```html
<div>
后来他在“我”的生活里悄然离去之后，“我”常常会心酸地想起这个夏天早晨站台上的情景，“我”在他二十一岁的时候突然闯进他的生活，而且完全挤满他的生活，他本来应有的幸福一点也挤不进来了。当他含辛茹苦把“我”养育成人，“我”却不知不觉把他抛弃在站台上。人世间的亲情像一杯咖啡，通过收养来建立的亲情是一杯苦咖啡，打算喝咖啡的人走了，他知道有更好的咖啡等着他，后来这杯咖啡越来越苦。但我相信喝咖啡的人终究会回来的。
</div>
div {
    -moz-columns: 150px 4;
         columns: 150px 4;    
}
```

这个合写的属性不是都满足 width 和 count。针对本例我们撇开每一列之间的间距不谈，假设每一列之间的间距为 0。那么当文本的宽度不小于 600px 时，文本将始终显示 4 列(至少确实想显示 4 列，如果文本字数足够的话就一定显示 4 列)，就不能同时满足于宽度也为 150px；当文本的宽度小于 600px 时，文本就显示为 3 列，当文本宽度小于 300px 时，文本就显示为 2 列。

本例中，对于元素可用宽度不同显示的列数也不同。

显示为 4 列：

![img](/https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-7-20/1032021-20161012212835171-1265803493.png)

显示为 3 列：

![img](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-7-20/1032021-20161012212905687-1069952213.png)

显示为 2 列：

![img](/https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-7-20/1032021-20161012212937203-1170865178.png)

显示为 1 列：

![img](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-7-20/1032021-20161012212959812-2078319533.png)

总结：那么这个合写属性就可以理解为(还是假设每列之间的间距为 0)：当元素可用宽度很小时，它只显示 1 列；当元素的可用宽度不小于 count * 2 它就显示 2 列；当元素的可用宽度不小于 count * 3 时，它就显示 3 列；依此规则类推，至到元素的可用宽度不小于 count * width 时，就显示为 width 列。

------

 

### 一些猜想：

在元素可用宽度确定的情况下，既设置 column-width， 又设置了 column-count 和 coiumn-gap 时，页面该怎么布局呢？

经过测试，基本可以得出以下结论：

##### 1. 第九点中的总结在这里依然有效；

##### 2. 当元素的宽度能够排下两列及以上时(一列时，没有间距)，column-gap 间距能始终被满足。

这里的 columns 属性时 column-count 和 column-width 属性的简写形式。

如果只设置 column-count 属性，浏览器会严格生成指定数量的栏，不管宽度如何。

如果同时设置了 column-count 和 column-width，前者会作为最大栏数，后者会作为最小栏宽。

```html
columns: 20em;  /* 在保证最小宽度 20em 的前提下，自动设置栏数 */
column-width: 20em;   /* 同上 */
columns: 3;   /* 3 栏，自动设置宽度 */
column-count: 3;   /* 同上 */
columns: 3 20em;   /* 至多 3 栏，每栏宽度至少 20em */
```

### 实现左右翻页效果

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Document</title>
  </head>
  <style>
    .wrapper {
      position: relative;
      display: block;
      column-width: 200px;
      border: 1px solid #ccc;
      width: 200px;
      height: 500px;
      overflow: hidden;
    }
    .content {
      position: relative;
      transition: all 0.4s;
    }
  </style>
  <body>
    <div class="wrapper">
      <div class="content">
        福建省宁德市霞浦县人大常委会称，当天上午召开的常委会上，县人大常委会听取和审议并表决通过了关于许可县公安局对第十七届人大代表苏某辉采取强制措施，并暂时停止其执行代表职务的决定。此前，苏某辉因违停、醉驾，拒不配合交警执法，并叫嚣“我是人大代表，你们无权处置我”受到社会关注。
        Play Video
        视频：县人大代表醉驾违停称你们无权处置我此前澎湃新闻曾报道，7月17日20时37分，苏某辉饮酒后在霞浦县松港街道金山路发现自己的闽JD***8号小车因违规停车被交警贴告知单，遂心怀不满，故意将车行驶至霞浦县太康路正中，以南北朝向将车辆停在太康路中心达23分钟之久，其时正值该路段通行高峰期，苏某辉的行为导致太康路通行不畅直至堵塞。
        巡特警大队出警后，苏某辉自称为县人大代表，拒不将车移开。后霞浦县公安局指挥中心指派霞浦交警协助，苏某辉仍不配合。交警大队民警将苏某辉带回队部进行调查。
        7月19日，福建正扬司法鉴定所出具意见书，苏某辉的血样中检出乙醇含量为203.5mg
        /100ml,霞浦县交警大队对苏某辉以涉嫌危险驾驶罪立案调查。随后，霞浦县公安局向霞浦县人大提请许可对苏某辉依法采取刑事强制措施和行政拘留。
        div class="wrapper">
        福建省宁德市霞浦县人大常委会称，当天上午召开的常委会上，县人大常委会听取和审议并表决通过了关于许可县公安局对第十七届人大代表苏某辉采取强制措施，并暂时停止其执行代表职务的决定。此前，苏某辉因违停、醉驾，拒不配合交警执法，并叫嚣“我是人大代表，你们无权处置我”受到社会关注。
        Play Video
        视频：县人大代表醉驾违停称你们无权处置我此前澎湃新闻曾报道，7月17日20时37分，苏某辉饮酒后在霞浦县松港街道金山路发现自己的闽JD***8号小车因违规停车被交警贴告知单，遂心怀不满，故意将车行驶至霞浦县太康路正中，以南北朝向将车辆停在太康路中心达23分钟之久，其时正值该路段通行高峰期，苏某辉的行为导致太康路通行不畅直至堵塞。
        巡特警大队出警后，苏某辉自称为县人大代表，拒不将车移开。后霞浦县公安局指挥中心指派霞浦交警协助，苏某辉仍不配合。交警大队民警将苏某辉带回队部进行调查。
        7月19日，福建正扬司法鉴定所出具意见书，苏某辉的血样中检出乙醇含量为203.5mg
        /100ml,霞浦县交警大队对苏某辉以涉嫌危险驾驶罪立案调查。随后，霞浦县公安局向霞浦县人大提请许可对苏某辉依法采取刑事强制措施和行政拘留。
        div class="wrapper">
        福建省宁德市霞浦县人大常委会称，当天上午召开的常委会上，县人大常委会听取和审议并表决通过了关于许可县公安局对第十七届人大代表苏某辉采取强制措施，并暂时停止其执行代表职务的决定。此前，苏某辉因违停、醉驾，拒不配合交警执法，并叫嚣“我是人大代表，你们无权处置我”受到社会关注。
        Play Video
        视频：县人大代表醉驾违停称你们无权处置我此前澎湃新闻曾报道，7月17日20时37分，苏某辉饮酒后在霞浦县松港街道金山路发现自己的闽JD***8号小车因违规停车被交警贴告知单，遂心怀不满，故意将车行驶至霞浦县太康路正中，以南北朝向将车辆停在太康路中心达23分钟之久，其时正值该路段通行高峰期，苏某辉的行为导致太康路通行不畅直至堵塞。
        巡特警大队出警后，苏某辉自称为县人大代表，拒不将车移开。后霞浦县公安局指挥中心指派霞浦交警协助，苏某辉仍不配合。交警大队民警将苏某辉带回队部进行调查。
        7月19日，福建正扬司法鉴定所出具意见书，苏某辉的血样中检出乙醇含量为203.5mg
        /100ml,霞浦县交警大队对苏某辉以涉嫌危险驾驶罪立案调查。随后，霞浦县公安局向霞浦县人大提请许可对苏某辉依法采取刑事强制措施和行政拘留。
      </div>
    </div>
    <script src="./jquery.js"></script>
    <script>
      function bindEvent() {
        var temp = 0;
        var conWidth = $(".wrapper").width();
        var conHeight = $(".wrapper").height();

        $(".content").on("click", function(e) {
          console.log(temp);
          if (e.clientX >= conWidth / 2) {
            if (temp > -$(".content").width() + 215) temp = temp - 216;
            $(".content").css({ left: temp + "px" });
            console.log(e);
          } else {
            if (temp != 0) temp = temp + 216;
            $(".content").css({ left: temp + "px" });
            console.log(temp);
          }
        });
      }
      bindEvent();
    </script>
  </body>
</html>

```

