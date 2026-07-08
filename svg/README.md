# svg

> 可缩放矢量图形，即SVG，是W3C XML的分支语言之一，用于标记可缩放的矢量图形；

加载慢是SVG的一个缺点。但是SVG也有自身的优点，比如它实现了DOM接口（比Canvas方便）。

```js
<svg version="1.1"
     baseProfile="full"
     width="300" height="200"
     xmlns="http://www.w3.org/2000/svg">

  <rect width="100%" height="100%" fill="red" />

  <circle cx="150" cy="100" r="80" fill="green" />

  <text x="150" y="125" font-size="60" text-anchor="middle" fill="white">SVG</text>

</svg>
```

## 特性

SVG 最大的特征就是**矢量化**。

- **无损放缩**：矢量图形可以无限放大或缩小而不失真，因为它们是基于数学公式计算的。
- **小文件大小**：相对于像素图形，矢量图形通常具有较小的文件大小，因为它们只需存储图形的数学描述。
- **可编辑性**：由于矢量图形是由数学公式定义的，因此可以轻松地编辑和修改其形状、颜色和属性。
- **清晰度**：矢量图形具有高分辨率和平滑的边缘，无论其显示尺寸如何，都能保持清晰度

- 元素的渲染顺序，越后面的元素越可见
- svg文件使用
  - 如果HTML是HTML5并且浏览器支持HTML5，同样可以直接嵌入SVG
  - 可以通过 object 元素引用SVG文件 `<object data="image.svg" type="image/svg+xml" />`
  - 使用 iframe 元素引用SVG文件 `<iframe src="image.svg"></iframe>`
  - 最后SVG可以通过JavaScript动态创建并注入到HTML DOM中。 这样具有一个优点，可以对浏览器使用替代技术，在不能解析SVG的情况下，可以替换创建的内容

svg 只能用于简单的图片，复杂的图片最佳使用位图，位图是一种图像表示方法，也被称为栅格图像或点阵图像。

## 坐标定位

x 和 y 代表坐标位置，width 和 height 代表宽高，r 代表半径，cx 和 cy 代表圆心

```html
<svg width="256" height="256" viewBox="0 0 256 256" xmlns="http://www.w3.org/2000/svg">       
    <rect x="10" y="10" width="300" height="300" />
    <circle cx="175" cy="100" r="75" fill="red" />
</svg>
```

### 视图框 ViewBox

使用 `viewBox` 属性可以控制 SVG 元素的视图范围，使其适应不同的显示设备和尺寸。通过调整 `viewBox` 的值，可以缩放、平移和裁剪 SVG 内容，以适应不同的需求和场景。

`viewBox` 中包含四个值的字符串，分别表示：`x` 、 `y` 、 `width` 和 `height` 。

-   `x` 是可视区域左上角的横坐标。
-   `y` 是可视区域左上角的纵坐标。
-   `width` 是可视区域的宽度。
-   `height` 是可视区域的高度。

`preserveAspectRatio` 宽高比，是 SVG（可缩放矢量图形）中的属性，用于控制元素在视口中的缩放和对齐方式，以保持其纵横比。
`preserveAspectRatio` 属性的值由两部分组成，用空格分隔。

1.  **对齐方式（Alignment）**：指定元素在视口中的对齐方式，可以是以下值之一。
    
    -   `none` ：不保持纵横比，直接拉伸元素以填充整个视口。
    -   `xMinYMin` ：保持纵横比，将元素缩放到视口内并保持在左上角。
    -   `xMidYMid` ：保持纵横比，将元素缩放到视口内并居中显示。
    -   `xMaxYMax` ：保持纵横比，将元素缩放到视口内并保持在右下角。
    -   `xMinYMid` ：保持纵横比，将元素缩放到视口内并保持在左边垂直居中。
2.  **缩放方式（Meet or Slice）**：指定元素在视口中的缩放方式，可以是以下值之一。
    
    -   `meet` ：缩放元素以适应视口，并保持元素完全可见，可能会留有空白区域。
    -   `slice` ：缩放元素以填充视口，可能会裁剪掉部分元素。例如， `preserveAspectRatio="xMidYMid meet"` 表示元素将保持纵横比，缩放到视口内并在视口中居中显示，同时保持元素完全可见。 `preserveAspectRatio` 属性通常应用于 `<svg>` 元素或 `<image>` 元素，以控制其在视口中的显示方式。它允许响应式地调整 SVG 元素，以适应不同的屏幕尺寸和显示环境。

## xmlns、xmlnk

xmlns 和 xmlns:xlink 是 XML 命名空间的属性，而 xlink:href 是 XLink 规范中的属性
xmlns 属性用于定义默认命名空间，xmlns:xlink 属性用于定义 XLink 命名空间，而 xlink:href 属性用于指定 XLink 链接的目标资源。

## 优化svg

为了优化 SVG，我们可以使用 SVGO。

SVG Optimizer 是一个基于 Node.js 的工具，用于优化 SVG 矢量图形文件，可以针对元数据、注释、隐藏元素、默认值或非最佳值以及其他可以安全删除或转换的内容，而不会影响 SVG 渲染结果。

## 引入svg

- img src
- background-image
- html内联svg
- `<object>` 标签
- iframe
- `<embed>` 标签

## svg 动画

实现方式

- SMIL
- JS
- CSS
- `<animate>、<animateTransform>、<animateMotion>`
  -  `<animate>`：用于在 SVG 中创建`基本的属性动画`。它可以用于对元素的位置、大小、颜色等属性进行动画处理。通过指定起始值和结束值，以及动画的持续时间和重复次数，可以实现属性的渐变过渡效果。
  -  `<animateTransform>`：用于对 SVG 元素的`变换属性`进行动画处理，例如平移、旋转、缩放等。它可以通过指定起始值和结束值，以及动画的持续时间和重复次数，实现变换属性的平滑过渡动画。
  -  `<animateMotion>`：用于在 SVG 中`创建沿路径移动的动画效果`。它可以使元素沿着指定的路径进行运动，并可以控制运动的速度、方向和重复次数。通过指定路径和动画的持续时间，可以实现元素沿路径移动的动画效果。

## 参考

- [SVG元素参考](https://developer.mozilla.org/zh-CN/docs/Web/SVG/Element)
- [SVG 属性参考](https://developer.mozilla.org/zh-CN/docs/Web/SVG/Attribute)
