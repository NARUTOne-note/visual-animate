# Canvas

> `HTML5`规范中支持的画布`位图技术`: `<canvas />`; Canvas是基于状态的绘制

canvas 有两个属性 width 和 Height，分别代表 Canvas 的宽和高；它有三个方法，分别是 getContext、toDataURL 和 toBlob。

```html
<!doctype html>
<html lang="zh">
<head>
<meta charset="UTF-8">
<title>基础的HTML5页面</title> 
</head>

<body>
  <canvas id="canvas" style="border: 1px solid #aaaaaa; display: block; margin: 50px auto;" width="800" height="600">
  你的浏览器居然不支持Canvas？！赶快换一个吧！！
  </canvas>
  <script>
    window.onload = function(){
      // 获得canvas对象
      var canvas = document.getElementById("canvas");
      // 获得画笔(2D环境)
      var context = canvas.getContext("2d");
    }
  </script> 
</body> 

</html>
```

**注意**：canvas中定义width、height跟在style中定义width和height是不同的，canvas标签的width和height是画布实际宽度和高度，绘制的图形都是在这个上面。
而style的width和height是canvas在浏览器中被渲染的高度和宽度。如果canvas的width和height没指定或值不正确，就被设置成默认值`(width:300px，height:150px)`。

canvas 画布的左上角为笛卡尔坐标系的原点，且y轴的正方向向下，x轴的正方向向右。

## CanvasRenderingContext2D 对象

**属性**：

-   `fillStyle` ：设置绘制的填充样式。可以是颜色值、渐变对象或图案对象。
-   `filter` ：设置绘制的滤镜效果。可以使用 CSS 滤镜函数来指定滤镜效果，如模糊、亮度调整等。
-   `font` ：设置绘制文本的字体样式。可以是字体大小和字体族名的组合，如 "16px Arial"。
-   `globalAlpha` ：设置绘制的全局透明度。取值范围为 0（完全透明）到 1（完全不透明）之间。
-   `globalCompositeOperation` ：设置绘制的全局合成操作。用于控制新绘制的图形如何与已有的图形混合。常见的操作包括源覆盖、目标覆盖、叠加等。
-   `lineCap` ：设置线条的端点样式。可以是 "butt"（平直端点，默认值）、"round"（圆形端点）或 "square"（方形端点）。
-   `lineDashOffset` ：设置虚线模式的起始偏移量。用于控制虚线的起始位置。
-   `lineJoin` ：设置线条的连接样式。可以是 "round"（圆角连接）、"bevel"（斜角连接）或 "miter"（尖角连接，默认值）。
-   `lineWidth` ：设置线条的宽度。可以是任意正数值，单位为像素。
-   `miterLimit` ：设置尖角连接的限制。当线条连接为尖角时，通过限制尖角的长度来控制连接的外观。
-   `shadowBlur` ：设置阴影的模糊程度。可以是任意正数值，值越大阴影越模糊。
-   `shadowColor` ：设置阴影的颜色。可以是颜色值，用于指定阴影的颜色。
-   `shadowOffsetX` ：设置阴影在水平方向的偏移量。可以是任意数值，单位为像素。
-   `shadowOffsetY` ：设置阴影在垂直方向的偏移量。可以是任意数值，单位为像素。
-   `strokeStyle` ：设置线条的样式。可以是颜色值、渐变对象或图案对象，用于指定线条的颜色或样式。
-   `textAlign` 的默认值为 `"start"` ，表示文本内容的起始位置与绘制位置对齐。
-   `textBaseline` 的默认值为 `"alphabetic"` ，表示文本内容的基线与绘制位置对齐。

**方法**：

-   `arc(x, y, radius, startAngle, endAngle, anticlockwise)` ：绘制一段圆弧或部分圆。参数 `x` 和 `y` 是圆心的坐标， `radius` 是半径，`startAngle` 和 `endAngle` 是起始角度和结束角度， `anticlockwise` 是一个布尔值，表示是否按逆时针方向绘制圆弧。
-   `arcTo(x1, y1, x2, y2, radius)` ：根据给定的控制点和半径绘制一段圆弧，使其与前一个点和给定的终点相切。 `x1` 和 `y1` 是第一个控制点的坐标， `x2` 和 `y2` 是第二个控制点的坐标， `radius` 是半径。
-   `beginPath()` ：创建一个新的路径，用于绘制图形。
-   `bezierCurveTo(cp1x, cp1y, cp2x, cp2y, x, y)` ：绘制贝塞尔曲线，通过控制点来确定曲线的形状。 `cp1x` 和 `cp1y` 是第一个控制点的坐标， `cp2x` 和 `cp2y` 是第二个控制点的坐标， `x` 和 `y` 是曲线的结束点坐标。
-   `clearRect(x, y, width, height)` ：清除指定矩形区域内的像素，使其变为透明。 `x` 和 `y` 是矩形区域的起始坐标， `width` 和 `height` 是矩形区域的宽度和高度。
-   `clip()` ：根据当前路径创建一个剪切区域，只有在剪切区域内的图形才会被绘制。
-   `closePath()` ：将当前路径的起点和终点连接，形成一个闭合路径。
-   `createImageData(width, height)` ：创建一个与给定尺寸相匹配的空白图像数据对象。 `width` 和 `height` 是图像数据的宽度和高度。
-   `createLinearGradient(x0, y0, x1, y1)` ：创建一个线性渐变对象，用于绘制线性渐变效果。 `x0` 和 `y0` 是起始点的坐标， `x1` 和 `y1` 是结束点的坐标。
-   `createPattern(image, repetition)` ：创建一个图案对象，用于绘制重复的图案。 `image` 是一个图像、画布或视频元素， `repetition` 是一个字符串，表示图案的重复方式。
-   `createRadialGradient(x0, y0, r0, x1, y1, r1)` ：创建一个径向渐变对象，用于绘制径向渐变效果。 `x0` 和 `y0` 是内圆的圆心坐标， `r0` 是内圆的半径， `x1` 和 `y1` 是外圆的圆心坐标， `r1` 是外圆的半径。
-   `drawFocusIfNeeded(element)` ：如果指定元素具有焦点，则绘制指定元素。
-   `drawImage(image, dx, dy)` ：将图像绘制到 Canvas 上。 `image` 是一个图像、画布或视频元素， `dx` 和 `dy` 是图像在 Canvas 上的绘制起始位置的坐标。
-   `ellipse(x, y, radiusX, radiusY, rotation, startAngle, endAngle, anticlockwise)` ：绘制一个椭圆或部分椭圆。 `x` 和 `y` 是椭圆中心的坐标， `radiusX` 和 `radiusY` 是椭圆的水平和垂直半径， `rotation` 是椭圆的旋转角度， `startAngle` 和 `endAngle` 是起始角度和结束角度， `anticlockwise` 是一个布尔值，表示是否按逆时针方向绘制椭圆。
-   `fill()` ：填充当前路径的内容。
-   `fillRect(x, y, width, height)` ：填充指定矩形区域内的像素。 `x` 和 `y` 是矩形区域的起始坐标， `width` 和 `height` 是矩形区域的宽度和高度。
-   `fillText(text, x, y [, maxWidth])` ：在指定位置绘制填充的文本。 `text` 是要绘制的文本， `x` 和 `y` 是文本的起始位置的坐标， `maxWidth` 是可选参数，表示文本的最大宽度。
-   `getImageData(x, y, width, height)` ：获取指定区域的像素数据。 `x` 和 `y` 是要获取像素数据的区域的起始坐标， `width` 和 `height` 是要获取像素数据的区域的宽度和高度。
-   `getLineDash()` ：获取当前虚线样式的线段和间隔序列。
-   `isPointInPath(x, y)` ：检查指定的点是否在当前路径中。 `x` 和 `y` 是要检查的点的坐标。
-   `isPointInStroke(x, y)` ：检查指定的点是否在当前路径的描边上。 `x` 和 `y` 是要检查的点的坐标。
-   `lineTo(x, y)` ：添加一条直线到当前路径的子路径中。 `x` 和 `y` 是直线的结束点坐标。
-   `measureText(text)` ：测量指定文本的宽度。 `text` 是要测量的文本。
-   `moveTo(x, y)` ：将路径的起始点移动到指定的坐标。 `x` 和 `y` 是起始点的坐标。
-   `putImageData(imageData, dx, dy)` ：将像素数据绘制到 Canvas 上。`imageData` 是要绘制的像素数据， `dx` 和 `dy` 是图像在 Canvas 上的绘制起始位置的坐标。
-   `quadraticCurveTo(cp1x, cp1y, x, y)` ：绘制二次贝塞尔曲线，通过控制点来确定曲线的形状。 `cp1x` 和 `cp1y` 是控制点的坐标， `x` 和 `y` 是曲线的结束点坐标。
-   `rect(x, y, width, height)` ：创建一个矩形路径。 `x` 和 `y` 是矩形的起始坐标， `width` 和 `height` 是矩形的宽度和高度。
-   `restore()` ：恢复之前保存的绘图状态和变换矩阵。
-   `rotate(angle)` ：旋转当前绘图。 `angle` 是旋转的角度，以弧度为单位。
-   `save()` ：保存当前的绘图状态和变换矩阵。
-   `scale(scaleX, scaleY)` ：缩放当前绘图。 `scaleX` 和 `scaleY` 是水平和垂直方向上的缩放因子。
-   `setLineDash(segments)` ：设置虚线样式的线段和间隔序列。 `segments` 是一个数组，表示线段和间隔的长度。
-   `setTransform(a, b, c, d, e, f)` ：设置绘图的变换矩阵。
-   `stroke()` ：绘制当前路径的描边。
-   `strokeRect(x, y, width, height)` ：绘制指定矩形区域的描边。 `x` 和 `y` 是矩形区域的起始坐标， `width` 和 `height` 是矩形区域的宽度和高度。
-   `strokeText(text, x, y [, maxWidth])` ：在指定位置绘制文本的描边。 `text` 是要绘制的文本， `x` 和 `y` 是文本的起始位置的坐标， `maxWidth` 是可选参数，表示文本的最大宽度。
-   `transform(a, b, c, d, e, f)` ：对当前绘图进行变换。
-   `translate(x, y)` ：平移当前绘图。

## 性能优化

Canvas 的性能优化可以通过以下几种方式来实现。

1.  **减少绘制区域**：只绘制需要更新的区域。
2.  **使用离屏渲染**：使用离屏 Canvas 进行复杂的图形处理，然后将处理结果绘制到主 Canvas 上。这样可以减少对主 Canvas 的直接绘制操作，提高性能。
3.  **批量绘制**：将多个绘制操作合并为一个，减少绘制次数。例如，可以将多个矩形的绘制合并为一个 `context.fillRect()` 调用。
4.  **使用图像缓存**：将经常使用的图像绘制到一个隐藏的 Canvas 上，并将其作为图像资源重复使用。这样可以减少重复绘制的开销，提高性能。
5.  **减少图像大小**：如果图像过大，可以将其缩放到合适的尺寸，以减少绘制的像素数量。可以使用 `context.drawImage()` 方法的缩放参数来实现。
6.  **避免频繁的状态更改**：在绘制过程中，避免频繁地修改 Canvas 的属性和状态。例如，可以将颜色、线宽等属性设置为常量，避免在每次绘制前都进行设置。
7.  **使用硬件加速**：在支持的浏览器中，可以使用 CSS 属性 `transform` 或 `opacity` 来触发硬件加速，提高绘制性能。
8.  **使用 requestAnimationFrame**：可以优化动画的绘制，确保在浏览器的刷新间隔内进行绘制，以获得更流畅的动画效果。
9.  **避免频繁的像素操作**：对于大量的像素级操作，如使用 `getImageData()` 和 `putImageData()` ，尽量减少其使用频率，因为这些操作会涉及大量的像素数据复制和粘贴。
10.  **Web Worker**：将复杂的 JavaScript 的计算放在工作线程中执行，这样可以避免在主线程上进行大量的计算，保持页面的流畅性。

Canvas 的离屏渲染是指在 Canvas 外部创建一个隐藏的 Canvas 元素，并将图形绘制到隐藏的 Canvas 上，然后通过drawImage再将隐藏 Canvas 上的内容绘制到可见的 Canvas 上。
Canvas 双缓冲技术是一种绘图技术，用于解决图像闪烁问题。在双缓冲技术中，使用两个缓冲区，一个用于绘制图像，另一个用于显示图像。绘制操作在后备缓冲区进行，绘制完成后将整个后备缓冲区的图像复制到前景缓冲区，然后显示在屏幕上。这样可以避免绘制过程中的闪烁问题，提供平滑的图像显示。

## 动画渲染

使用 requestAnimationFrame 是更好的选择。这是因为 requestAnimationFrame 会在浏览器的下一次重绘之前执行函数，这样可以保证动画的更新频率与浏览器的刷新率相匹配，避免了过度绘制和资源浪费。同时，使用 requestAnimationFrame 还可以获得更好的性能和更平滑的动画效果。

## 参考

[canvas 截图](https://juejin.im/post/593f7df4ac502e006b587b44)
