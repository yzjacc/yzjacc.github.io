---
layout: post
title: "「HTML」HTML5新增标签 Canvas "
subtitle: " From Yuzj"
author: "Yuzj"
header-img: "img/post-bg-web.jpg"
header-mask: 0.3
catalog: true
tags:
- HTML
- HTML5
---

### 1.利用canvas画线

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
			ctx.lineWidth = 10;//设置线宽
			ctx.moveTo(100, 100);
			ctx.lineto(200,100)
			ctx.stroke();
			ctx.beginPath();//重新开始构建一条新的线
			ctx.lineWidth=5;
			ctx.moveto (200, 100);
			ctx.1ineTo (200,200);
			ctx lineTo (150, 200);
			ctx closePath();//将图形闭合
			ctx.stroke();//开始渲染
    	ctx.fill();//填满闭合区域颜色
  </script>
</body>
```

### 2.利用canvas画矩形

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
  		ctx.rect(100,100,200,100);
    	ctx.fill();
    	ctx.stroke();
    
    	ctx.strokeRect(100,100,200,100);//前两个为起始位置 后两个为长和宽
    
    	ctx.fillRect(100,100,200,100);
  </script>
</body>
```

### 3.利用canvas方块下落

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
  		var height = 100;
    	var timer = setInterval(function (){
        	ctx.clearRect(0, 0, 500, 300);
        	ctx.strokeRect(100, height, 50, 50);
        	height += 2;
        
      },100/60);
  </script>
</body>
```

### 4.利用canvas画圆形

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
  <!--圆心(x,y),半径(r),弧度（起始弧度，结束弧度），方向（顺时针，逆时针）-->
  <script>
  		var canvas = document.getElementById("can");
			var ctx = canvas.getContext("2d");
  		ctx.arc(100,100,50,0,Math.PI*2,0);
    	ctx.stroke();
  </script>
</body>
```

### 5.利用canvas画圆角矩形

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
    	//  B（x，y），C（x，y），圆角大小
  		var canvas = document.getElementById("can");
			var ctx = canvas.getContext("2d");
    	ctx.moveTo(100, 100);
    	ctx.arcTo(100,200,200,200,10);
      ctx.arcTo(200,200,200,100,10);
      ctx.arcTo(200,100,100,100,10);
      ctx.arcTo(100,100,100,200,10);
      ctx.stroke();
			
  </script>
</body>
```

![屏幕快照 2019-07-18 下午3.25.50](https://github.com/yzjacc/yzjacc.github.io/raw/master/img/in-post/2019-7-18/屏幕快照 2019-07-18 下午3.25.50.png)

### 6.利用canvas坐标平移旋转与缩放

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
			ctx.beginPath();
   		ctx.rotate(Math.PI/6);//默认以画布原点（左上角）旋转
    	ctx.translate(100,100);//改变坐标系（原点）位置
	    ctx.moveTo(0, 0);
	    ctx.lineTo(100,0)
      ctx.stroke();
			
    	ctx.beginPath();
     	ctx.strokeRect(100,100,100,100);
    	ctx.scale(2,1);//x坐标变为原来的2倍 y不变
     //translate与scale都是全局影响的
  </script>
</body>
```

### 7.利用canvas坐标save与restore

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
  	  ctx.save();//保存之前的坐标状态（平移 缩放 旋转）
			ctx.beginPath();
      ctx.strokeRect(0,0,100,50);
    	ctx.translate(100,0);//改变坐标系（原点）位置
	    ctx.moveTo(0, 0);
	    ctx.lineTo(100,0)
      ctx.stroke();
    	ctx.beginPath();
    	ctx.restore();//恢复之前的坐标状态
     	ctx.strokeRect(200,0,100,50);
  </script>
</body>
```

### 8.利用canvas进行背景填充

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
			var img = new Image();
    	img.src = "./!!!";
    	img.onload = function (){
        	    ctx.beginPath();
        			var bg = ctx.createPattern(img,"repeat");//	图片是根据坐标系原点进行填充
       			  ctx.fillStyle = bg;
       			  ctx.fillRect(100, 100, 200, 100);
      }

  </script>
</body>
```

### 9.利用canvas线性渐变

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
      ctx.beginPath();
      var bg = ctx.createLinearGradient(0,0,200,0);//	线性渐变是根据坐标系原点进行填充
    	bg.addColorStop(0,"while");
    	bg.addColorStop(0.5,"blue");
    	bg.addColorStop(1,"black");
   		ctx.fillStyle = bg;
      ctx.fillRect(0, 0, 200, 100);
  </script>
</body>
```

### 10.利用canvas辐射渐变

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
      ctx.beginPath();//起始圆圆心半径 结束圆～～
      var bg = ctx.createRadialGradient(100,,100,100,100,100);//	辐射渐变是根据坐标系原点进行填充
    	bg.addColorStop(0,"while");
    	bg.addColorStop(0.5,"blue");
    	bg.addColorStop(1,"black");
   		ctx.fillStyle = bg;
      ctx.fillRect(0, 0, 200, 100);
  </script>
</body>
```

### 11.利用canvas阴影

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
      ctx.beginPath();
    	ctx.shadowColor = "red";
    	ctx.shadowBlur = 30;
    	ctx.shadowOffsetX = 15;
    	ctx.shadowOffsetY = 15;
      ctx.fillRect(0, 0, 200, 200);
  </script>
</body>
```

### 12.利用canvas渲染文字

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
      ctx.beginPath();
			ctx.strokeRect(0, 0, 200, 200);
    	ctx.font = "30px Georgia";
    	ctx.strokeText("panda",200,100);//文字描边
    	ctx.fillStyle = "red";
    	ctx.fillText("monkey",200,250);//文字填充
  </script>
</body>
```

### 13.利用canvas线端样式

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
            //线端样式

            ctx.beginPath();
            ctx.lineWidth = 15;
            ctx.moveTo(100, 100);
            ctx.lineto(200, 100);
            ctx.lineto(100, 130);

            // ctx.linecap =butt, square, round

            ctx.lineJoin = "miter"; //round, bevel, miter (miterlimit)
            ctx.miterLimit = 5;
            ctx.stroke();
        </script>
    </body>
```

### 9.globalCompositeOperation 属性![图片1](https://github.com/yzjacc/yzjacc.github.io/raw/master/img/in-post/2019-7-22/图片1.png)

