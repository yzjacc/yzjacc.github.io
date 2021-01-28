---
layout: post
title: "「HTML」HTML5 标签篇 Canvas "
subtitle: " From Yuzj"
author: "Yuzj"
header-img: "img/post-bg-web.jpg"
header-mask: 0.3
catalog: true
tags:
- HTML
- HTML5
---

### 利用canvas画线

```html
<DOCYPE html>
  <html lang="en">
    <head>
      <meta charset="utf-8" />
      <title>title</title>
      <style>
        canvas {
          width: 500px;
          height: 300px;
          border: 1px solid;
        }
      </style>
    </head>
    <body>
      <canvas id="can" width="500px" height="300px"></canvas>
      <!--该画板只能在行间样式定义宽高-->
      <script>
        var canvas = document.getElementById("can");
        var ctx = canvas.getContext("2d");
        ctx.lineWidth = 10;//设置线宽
        ctx.moveTo(100,100);
        ctx.lineTo(200,100)
        ctx.stroke();
        ctx.beginPath();//重新开始构建一条新的线
        ctx.lineWidth = 5;
        ctx.moveTo (200, 100);
        ctx.lineTo (200,200);
        ctx.lineTo (150, 200);
        ctx.closePath();//将图形闭合
        ctx.stroke();//开始渲染
        ctx.fill();//填满闭合区域颜色
      </script>
    </body>
  </html>
</DOCYPE>
```

### 利用canvas画矩形

```html
<DOCYPE html>
  <html lang="en">
    <head>
      <meta charset="utf-8" />
      <title>title</title>
      <style>
        canvas {
          width: 500px;
          height: 300px;
          border: 1px solid;
        }
      </style>
    </head>

    <body>
      <canvas id="can" width="500px" height="300px"></canvas>
      <!--该画板只能在行间样式定义宽高-->
      <script>
        var canvas = document.getElementById("can");
        var ctx = canvas.getContext("2d");
        //0 一根一根画
        //1
        ctx.rect(100, 100, 200, 100); //前两个为起始位置 后两个为长和宽
        ctx.fill();
        ctx.stroke();
        //2
        ctx.strokeRect(100, 100, 200, 100); //前两个为起始位置 后两个为长和宽
        //3
        ctx.fillRect(100, 100, 200, 100); //比上者多填充功能
      </script>
    </body>
  </html>
</DOCYPE>
```

### 利用canvas方块下落

```html
<DOCYPE html>
  <html lang="en">
    <head>
      <meta charset="utf-8" />
      <title>title</title>
      <style>
        canvas {
          width: 500px;
          height: 300px;
          border: 1px solid;
        }
      </style>
    </head>

    <body>
      <canvas id="can" width="500px" height="300px"></canvas>
      <!--该画板只能在行间样式定义宽高-->
      <script>
        var canvas = document.getElementById("can");
        var ctx = canvas.getContext("2d");
        var height = 100;
        var timer = setInterval(function() {
          ctx.clearRect(0, 0, 500, 300);
          ctx.strokeRect(100, height, 50, 50);
          height += 2;
        }, 100 / 60);
      </script>
    </body>
  </html>
</DOCYPE>
```

### 利用canvas画 弧形 圆形

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>title</title>
    <style>
      canvas {
        width: 500px;
        height: 300px;
        border: 1px solid;
      }
    </style>
  </head>
  <body>
    <canvas id="can" width="500px" height="300px"></canvas>
    <!--该画板只能在行间样式定义宽高-->
    <!-- 圆心(x,y),半径(r),弧度（起始弧度，结束弧度),方向（顺时针 0,逆时针 1）-->
    <script>
      var canvas = document.getElementById("can");
      var ctx = canvas.getContext("2d");
      ctx.arc(100, 100, 50, 0, Math.PI * 2, 0);
      ctx.stroke();
    </script>
  </body>
</html>

```

### 利用canvas画圆角矩形

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Document</title>
    <style>
      canvas {
        width: 500px;
        height: 300px;
        border: 1px solid;
      }
    </style>
  </head>
  <body>
    <canvas id="can" width="500px" height="300px"></canvas>
    <!--该画板只能在行间样式定义宽高-->
    <script>
      //  B（x，y），C（x，y），圆角大小
      var canvas = document.getElementById("can");
      var ctx = canvas.getContext("2d");
      ctx.moveTo(100, 100);//A点
      ctx.arcTo(100, 200, 200, 200, 10);
      ctx.arcTo(200, 200, 200, 100, 10);
      ctx.arcTo(200, 100, 100, 100, 10);
      ctx.arcTo(100, 100, 100, 200, 10);
      ctx.stroke();
    </script>
  </body>
</html>

```

![屏幕快照 2019-07-18 下午3.25.50](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-7-18/屏幕快照 2019-07-18 下午3.25.50.png)

### 利用canvas画贝塞尔曲线

```html
<DOCYPE html>
  <html lang="en">
    <head>
      <meta charset="utf-8" />
      <title>title</title>
      <style>
        canvas {
          width: 500px;
          height: 300px;
          border: 1px solid;
        }
      </style>
    </head>

    <body>
      <canvas id="can" width="500px" height="300px"></canvas
      >
      <script>
        var canvas = document.getElementById("can");
        var ctx = canvas.getContext("2d");
        ctx.beginPath();
        ctx.moveTo(100,100);
        ctx.quadraticCurveTo(200,200,300,100);//二次贝塞尔曲线
        ctx.bezierCurveTo(200,200,300,100,400,200);//三次贝塞尔曲线
        ctx.stroke();
      </script>
    </body>
  </html>
</DOCYPE>

```

贝塞尔曲线

几个点的匀速运动 画出的曲线

![屏幕快照 2019-11-07 下午5.23.27](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-7-18/屏幕快照 2019-11-07 下午5.23.27.png)

![屏幕快照 2019-11-07 下午5.25.02](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-7-18/屏幕快照 2019-11-07 下午5.25.02.png)

![屏幕快照 2019-11-07 下午5.25.14](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-7-18/屏幕快照 2019-11-07 下午5.25.14.png)

### 利用canvas坐标平移旋转与缩放

```html
<DOCYPE html>
  <html lang="en">
    <head>
      <meta charset="utf-8" />
      <title>title</title>
      <style>
        canvas {
          width: 500px;
          height: 300px;
          border: 1px solid;
        }
      </style>
    </head>

    <body>
      <canvas id="can" width="500px" height="300px"></canvas
      ><!--该画板只能在行间样式定义宽高-->
      <script>
        var canvas = document.getElementById("can");
        var ctx = canvas.getContext("2d");
        ctx.beginPath();
        ctx.rotate(Math.PI / 6); // 默认以画布原点（左上角）旋转
        ctx.translate(100, 100); // 改变坐标系（原点）位置
        ctx.moveTo(0, 0);
        ctx.lineTo(100, 0);
        ctx.stroke();

        ctx.beginPath();
        ctx.strokeRect(100, 100, 100, 100);
        ctx.scale(2, 1); //横向缩放与纵向缩放 x坐标变为原来的2倍 y不变
        //translate与scale都是全局影响的
      </script>
    </body>
  </html>
</DOCYPE>

```

### 利用canvas坐标save与restore

```html
<DOCYPE html>
  <html lang="en">
  <head>
  
          <meta charset="utf-8">
          <title>title</title>
          <style>
                canvas {
                    width: 500px;
                    height: 300px;
                    border: 1px solid;				
                }
          </style>
  </head>
  
  <body>
    <canvas id="can" width="500px" height="300px"></canvas><!--该画板只能在行间样式定义宽高-->
    <script>
        var canvas = document.getElementById("can");
        var ctx = canvas.getContext("2d");
        //为了预防平移与旋转 对全局的坐标状态
        ctx.save();// 保存之前的坐标状态（平移 缩放 旋转）
        ctx.beginPath();
        ctx.strokeRect(0,0,100,50);
        ctx.translate(100,0);//改变坐标系（原点）位置
        ctx.moveTo(0, 0);
        ctx.lineTo(100,0)
        ctx.stroke();
        ctx.beginPath();
        ctx.restore();// 恢复之前的坐标状态
        ctx.strokeRect(200,0,100,50);
    </script>
  </body>
  </html>
</DOCYPE>
```

### 利用canvas进行背景填充

```html
<DOCYPE html>

  <html lang="en">
  
  <head>
  
          <meta charset="utf-8">
          <title>title</title>
          <style>
                canvas {
                    width: 500px;
                    height: 300px;
                    border: 1px solid;				
                }
          </style>
  </head>
  
  <body>
    <canvas id="can" width="500px" height="300px"></canvas>
    <!--该画板只能在行间样式定义宽高-->
    <script>
        var canvas = document.getElementById("can");
        var ctx = canvas.getContext("2d");
        var img = new Image();
        img.src = "./!!!";
        img.onload = function (){
                ctx.beginPath();
                var bg = ctx.createPattern(img,"repeat");
          			//	图片是根据坐标系原点进行填充
                ctx.fillStyle = bg;
                ctx.fillRect(100, 100, 200, 100);
        }
    </script>
  </body>
  </html>
</DOCYPE>

```

### 利用canvas线性渐变

```html
<DOCYPE html>
  <html lang="en">
    <head>
      <meta charset="utf-8" />
      <title>title</title>
      <style>
        canvas {
          width: 500px;
          height: 300px;
          border: 1px solid;
        }
      </style>
    </head>

    <body>
      <canvas id="can" width="500px" height="300px"></canvas
      ><!--该画板只能在行间样式定义宽高-->
      <script>
        var canvas = document.getElementById("can");
        var ctx = canvas.getContext("2d"); 
        ctx.beginPath();
        var bg = ctx.createLinearGradient(0, 0, 200, 0); 
        //	线性渐变是根据坐标系原点进行填充
        bg.addColorStop(0, "white");
        bg.addColorStop(0.5, "blue");
        bg.addColorStop(1, "black");
        ctx.fillStyle = bg;
        ctx.fillRect(0, 0, 200, 100);
      </script>
    </body>
  </html>
</DOCYPE>

```

### 利用canvas辐射渐变

```html
<DOCYPE html>
  <html lang="en">
    <head>
      <meta charset="utf-8" />
      <title>title</title>
      <style>
        canvas {
          width: 500px;
          height: 300px;
          border: 1px solid;
        }
      </style>
    </head>

    <body>
      <canvas id="can" width="500px" height="300px"></canvas
      ><!--该画板只能在行间样式定义宽高-->
      <script>
        var canvas = document.getElementById("can");
        var ctx = canvas.getContext("2d");
        ctx.beginPath();//起始圆 圆心 半径 结束圆～～
        var bg = ctx.createRadialGradient(100,100,100,100,100,100);
        //	辐射渐变是根据坐标系原点进行填充
        bg.addColorStop(0,"while");
        bg.addColorStop(0.5,"blue");
        bg.addColorStop(1,"black");
         ctx.fillStyle = bg;
        ctx.fillRect(0, 0, 200, 100);
      </script>
    </body>
  </html>
</DOCYPE>

```

![屏幕快照 2019-11-07 下午5.48.59](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-7-18/屏幕快照 2019-11-07 下午5.48.59.png)

### 利用canvas阴影

```html
<DOCYPE html>
  <html lang="en">
    <head>
      <meta charset="utf-8" />
      <title>title</title>
      <style>
        canvas {
          width: 500px;
          height: 300px;
          border: 1px solid;
        }
      </style>
    </head>

    <body>
      <canvas id="can" width="500px" height="300px"></canvas
      ><!--该画板只能在行间样式定义宽高-->
      <script>
        var canvas = document.getElementById("can");
        var ctx = canvas.getContext("2d");
        ctx.beginPath();
        ctx.shadowColor = "red"; //颜色
        ctx.shadowBlur = 30;     // 阴影大小
        ctx.shadowOffsetX = 15;  // x y移动阴影
        ctx.shadowOffsetY = 15;
        ctx.fillRect(0, 0, 200, 200);
      </script>
    </body>
  </html>
</DOCYPE>

```

### 利用canvas渲染文字

```html
<DOCYPE html>
  <html lang="en">
    <head>
      <meta charset="utf-8" />
      <title>title</title>
      <style>
        canvas {
          width: 500px;
          height: 300px;
          border: 1px solid;
        }
      </style>
    </head>

    <body>
      <canvas id="can" width="500px" height="300px"></canvas
      ><!--该画板只能在行间样式定义宽高-->
      <script>
        var canvas = document.getElementById("can");
        var ctx = canvas.getContext("2d");
        ctx.beginPath();
        ctx.strokeRect(0, 0, 200, 200);
        ctx.font = "30px Georgia";
        ctx.strokeText("yuzijun", 200, 100); //文字描边
        ctx.fillStyle = "red";
        ctx.fillText("monkey", 200, 250); //文字填充
      </script>
    </body>
  </html>
</DOCYPE>

```

### 利用canvas线端样式

```html
<DOCYPE html>
  <html lang="en">
    <head>
      <meta charset="utf-8" />
      <title>title</title>
      <style>
        canvas {
          width: 500px;
          height: 300px;
          border: 1px solid;
        }
      </style>
    </head>

    <body>
      <canvas id="can" width="500px" height="300px"></canvas>
      <!--该画板只能在行间样式定义宽高-->
      <script>
        var canvas = document.getElementById("can");
        var ctx = canvas.getContext("2d");
        //线端样式

        ctx.beginPath();
        ctx.lineWidth = 15;
        ctx.moveTo(100, 100);
        ctx.lineTo(200, 100);
        ctx.lineTo(100, 130);
        // 在原来长度基础上两边加上一部分 
        // ctx.linecap = butt, square, round
        // 两根线拐点时设置的属性 round（圆角）, bevel（默认）, miter（砍角） 							//(miterlimit)
        ctx.lineJoin = "miter";
        ctx.miterLimit = 5;//砍角的大小
        ctx.stroke();
      </script>
    </body>
  </html>
</DOCYPE>

```

### globalCompositeOperation 属性

```html
<DOCYPE html>
  <html lang="en">
    <head>
      <meta charset="utf-8" />
      <title>title</title>
      <style>
        canvas {
          width: 500px;
          height: 300px;
          border: 1px solid;
        }
      </style>
    </head>

    <body>
      <canvas id="can" width="500px" height="300px"></canvas>
      <!--该画板只能在行间样式定义宽高-->
      <script>
          var c=document.getElementById("myCanvas");
          var ctx=c.getContext("2d");

          ctx.fillStyle="red";
          ctx.fillRect(20,20,75,50);
          ctx.globalCompositeOperation="source-over";
          ctx.fillStyle="blue";
          ctx.fillRect(50,50,75,50);

          ctx.fillStyle="red";
          ctx.fillRect(150,20,75,50);
          ctx.globalCompositeOperation="destination-over";
          ctx.fillStyle="blue";
          ctx.fillRect(180,50,75,50);
      </script>
    </body>
  </html>
</DOCYPE>

```

### 

### ![图片1](https://pg12138.oss-cn-beijing.aliyuncs.com/img/in-post/2019-7-22/图片1.png)

