# 一、SVG 邂逅

SVG 全称为（Scalable Vector Graphics），即可缩放矢量图形。

> 矢量定义：既有大小又有方向的量。
>
> - 在物理学中称作矢量，如一个带箭头线段：长度表示大小，箭头表示方向；
> - 在数学中称作向量。
> - 在计算机中，矢量图可无限放大而不变形。

SVG 规范是万维网联盟（W3C）自 1998 年以来开发的标准。

SVG 是一种基于 XML 格式的矢量图，主要用于定义二维图形，支持交互和动画。

SVG 图像可在不损失质量的情况下按比例缩放，并支持压缩。

基于 XML 的 SVG 可轻松的用文本编辑器或矢量图形编辑器创建和编辑，并可以直接在浏览器显示。

<img src="NodeAssets/svg的logo.jpg" style="zoom:50%;" />

SVG 的兼容性：

<img src="NodeAssets/SVG的兼容性.jpg" style="zoom:150%;" />

# 二、SVG 发展历史

## 1.SVG 1.x 版本

1. SVG 是 W3C SVG 工作组于 1998 年开始开发，
2. SVG 1.0 于 2001 年 9 月 4 日 成为 W3C 推荐的标准。
3. SVG 1.1 于 2003 年 1 月 14 日成为 W3C 推荐的标准。

   - 该版本增加了模块化规范的内容。除此之外，1.1 和 1.0 几乎没有区别。

4. SVG Tiny 1.2 于 2008 年 12 月 22 日成为 W3C 推荐标准，

   - 主要是为性能低的小设备生成图形，但是后来被 SVG 2.0 所弃用了。

5. SVG 1.1 第二版于 2011 年 8 月 16 日发布，
   - 这次只是更新了勘误表和说明，并没有增加新功能 。

## 2.SVG 2.0 版本（推荐）

1. SVG 2.0 于 2016 年 9 月 15 日成为 W3C 候选推荐标准，
2. 最新草案于 2020 年 5 月 26 日发布。

[SVG 2.x Change From SVG 1.x](https://www.w3.org/TR/SVG/changes.html)，比如：

- Removed the `baseProfile` and `version` attributes from the `<svg>` element.
- Added the ability to use `auto` for the `width` and `height` attributes on `<image>`.
- Added `lang` attribute on `<desc>` and `<title>` elements.
- Removed the `xlink:type`, `xlink:role`, `xlink:arcrole`, `xlink:show` and `xlink:actuate` attributes（“xlink”为命名空间的前缀）.
- Deprecated the `xlink:href` attribute in favor of using `href` without a namespace.

# 三、SVG 优缺点

## 1.SVG 优点：

【扩展好】：矢量图像在浏览器中放大缩小不会失真，可在许多设备和浏览器中使用。而光栅图像（PNG、JPG）放大缩小会失真。

> 矢量图像，是基于矢量的点、线、形状和数学公式来构建的图形，该图形是没有像素的，放大缩小是不会失真的。
>
> 光栅图像，是由像素点（微小的彩色方块）构建的图像，大量像素点可以形成高清图像，比如照片。图像像素越多，质量越高。

【灵活】：SVG 是 W3C 开发的标准，可集成到 DOM 中，结合 CSS、JavaScript、HTML 和 SMIL。使用时非常方便和灵活。

- SVG 图像可以使用 JS、CSS 和 SMIL 进行动画处理。对于 Web 开发人员来说非常的友好。

【轻量级】：与其它格式相比，SVG 图像的尺寸非常小。

【可打印】：SVG 图像可用任何分辨率打印，不会损失质量。

【利于SEO】：SVG 图像集成在 DOM 中，能被搜索引擎索引。非常适合 SEO（搜索引擎优化）优化。

【可压缩】：与其它图像格式一样，SVG 文件支持压缩。

【易于编辑】：只需一个文本编辑器就可以创建 SVG 图像。

- 设计师通常会使用 Adobe Illustrator（AI）等矢量图形工具创建和编辑。
- 在 Vue 或 React 中可以方便地将 SVG 图片，转成 SVG 组件。

## 2.SVG 的缺点：

不适合高清图片制作：

- SVG 格式非常适合用于徽标和图标（ICON）等 2D 图形，但不适用于高清图片，不适合进行像素级操作。
- SVG 的图像无法显示与标准图像格式一样多的细节，因为它们是使用点和路径而不是像素来渲染的。

SVG 图像变得复杂时，加载会比较慢；

不完全扩平台：

- 它不适用于 IE8 及更低版本的旧版浏览器。根据 caniuse 的数据，大约还有 5% 的用户在使用不支持 SVG 的浏览器。

# 四、SVG 应用场景

下面是一些保证 SVG 优于其他图像格式的应用场景：

- 显示矢量徽标（Logo）、图标（ICON）和其他几何设计。
- 应用在需适配多种尺寸的屏幕上展示，因为 SVG 的扩展性更好。
- 创建一些简单动画的场景：
  - 可以方便的适用 JS、CSS、SMIL 实现动画效果。
- 制作各种图表（条形图、折线图、饼图、散点图等等），以及大屏可视化页面开发。

<img src="NodeAssets/SVG的应用场景.jpg" style="zoom:150%;" />

# 五、SVG 和 Canvas 的区别

可扩展性：

- SVG 基于矢量的点、线、形状和数学公式来构建图形，没有像素，放大缩小不会失真。可在任何分辨率下高质量的打印
- Canvas 由一个个像素点构成的图形，放大会使图形变得颗粒状和像素化（模糊），不适合在任意分辨率下打印。

渲染能力：

- SVG 很复杂时，渲染会很慢，在很大程度上使用了 DOM。图像中具有大量元素。
- Canvas 提供了高性能的渲染和更快的图形处理能力，
  - 适合制作 H5 小游戏；当图像中有很多内容时，文件大小不会增加太多；相对的，内存会有较大消耗，

灵活度：

- SVG 可以通过 JavaScript、CSS、SMIL 进行修改，用 SVG 来创建动画和制作特效非常方便。
- Canvas 只能通过 JavaScript 进行修改，创建动画得一帧帧重绘。

使用场景：

- SVG 非常适合显示矢量徽标（Logo）、图标（ICON）和其他几何设计。
- Canvas 主要用于游戏开发、绘制复杂图形、复杂照片的合成，以及对图片进行像素级别的操作，如：取色器、复古照片。

# 六、SVG 创建方式

四种方式：

- 方式一：在一个单独的 svg 文件中绘制，该文件可直接在浏览器预览或嵌入到 HTML 中使用（推荐）；
- 方式二：直接在 HTML 文件中使用 svg 元素来绘制（推荐）；
- 方式三：直接使用 JavaScript 代码来生成 svg 矢量图；
- 方式四：使用 AI（Adobe IIIustractor）矢量绘图工具来绘制矢量图，并导出为 svg 文件（推荐）。

## 1.svg 文件

4 个步骤：

1. 新建一个 .svg 文件，在文件第一行编写 XML 文件声明；
2. 编写一个 `<svg>` 元素，并给该元素添加下属性：

   - `version`：指定使用 svg 的版本（值为 `1.0` 和 `1.1`，并没有 `2.0`）。
   - `baseProfile`：渲染时的语言描述。

   > 【注意】：SVG2.0 之前，`version` 和 `baseProfile` 属性用来验证和识别 SVG 版本。而 **SVG2.0 后不推荐使用这两个属性了**。

   - `width / height`：指定 svg 画布（视口）的宽和高，默认值分别为 `300` 和 `150`，默认使用 px 单位。
   - `xmlns`：给 svg 元素绑定一个命名空间（http://www.w3.org/2000/svg） 意味着这个 `<svg>` 标签和它的子元素都属于该命名空间下。

3. 在 `<svg>` 元素中，添加图形，如：`<rect>`元素
4. 在浏览器直接预览或嵌入到 HTML 中预览。[嵌入 HTML 的 6 种方式](#七、svg 在 HTML 中引用的方式)。

### 1.XML 声明：

由于 SVG 文件是一个 XML 文件格式，在编写 XML 文档时，通常是推荐编写 XML 声明的。

- 在 XML1.0 中，XML 声明是可选的，推荐写但不强制。
- 在 XML1.1 中，声明是强制性的，如果没有声明，则自动暗示该文档是 XML1.0 文档。

所以建议在编写 .svg 文件时也编写一个 XML 声明。

SVG 的 XML 声明格式：

```html
<?xml version="1.1" encoding="UTF-8" standalone="no" ?>
```

- `version` 指定版本（必填）；
- `encoding` 指定 XML 文档的编码（可选，默认是 UTF-8）；
- `standalone`：指定当前 XML 文档是否依赖于外部标记声明（可选，和 DTD 声明一起用才有意义）。
  - `no`：默认值，代表依赖外部标记声明；
  - `yes`：代表依赖内部默认的标记声明。

### 2.DTD 声明：

SVG 的文档类型声明 DTD（Document Type Declare）；

用于解析器验证 XML 文件是否符合该规范，与 HTML5 文件的 DTD 声明类似。

XML 中内部 DTD 声明（可选）；

<img src="NodeAssets/xml内部DTD声明.jpg" style="zoom:50%;" />

XML 中外部 DTD 声明（可选）

```html
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" "http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">
```

### 4.创建 svg 矢量图

```html
<?xml version="1.1" encoding="UTF-8" standalone="no" ?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" "http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">
<!--
  version="1.1"
  baseProfile="full" 正确渲染 svg 内容时所需要最小 SVG 语言概述(版本);
    * full: 正常的 SVG 语言概述；
    * basic: 基本 SVG 语言概述；
    * tiny: 轻量级 SVG 语言概述。
  xmlns: 指定 svg 元素和 svg 内的子元素都是属于 http://www.w3.org/2000/svg 这个命名空间下
-->
<svg version="1.1" baseProfile="full" width="100" height="100" xmlns="http://www.w3.org/2000/svg">
  <rect x="0" y="0" width="100" height="100"></rect>
  <title>我是 svg title</title>
</svg>
```

### 3.SVG 文档解构

[SVG 1.1 文档结构](https://www.w3.org/TR/SVG11/struct.html)

第一行：XML 声明。

第二行：DTD 声明.

[SVG 2.0 文档结构](https://www.w3.org/TR/SVG2/struct.html#Namespace)

第一行：XML 声明。

不推荐写 DTD 声明。

`<svg>` 标签上 `version` 和 `baseProfile` 属性已删除；

`<desc>` 元素是用来描述该文件的。

<img src="NodeAssets/SVG文档解构对比.jpg" style="zoom:150%;" />

使用 SVG 2.0 文档结构重构上面代码：

```html
<?xml version="1.1" standalone="no" ?>
<svg width="100" height="100" xmlns="http://www.w3.org/2000/svg">
  <rect x="0" y="0" width="100" height="100"></rect>
</svg>
```

## 2.svg 元素

在 HTML 文件中，使用 `<svg>` 元素绘制。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <!-- 1.创建svg 1.0 -->
    <svg
      version="1.0"
      baseProfile="full"
      width="100"
      height="100"
      xmlns="http://www.w3.org/2000/svg"
    >
      <rect x="0" y="0" width="100" height="100"></rect>
    </svg>

    <!-- 2.创建svg 2.0 -->
    <svg width="100" height="100" xmlns="http://www.w3.org/2000/svg">
      <rect x="0" y="0" width="100" height="100"></rect>
    </svg>

    <!--
      3.创建 svg 2.0 简写
        * 默认：w：300px；h：150px
        * xmlns="http://www.w3.org/2000/svg" 这个命名空间浏览器的解析器会自动添加
    -->
    <svg>
      <rect x="0" y="0" width="100" height="100"></rect>
    </svg>
  </body>
</html>
```

## 3.JS 创建 svg

使用 JS 脚本来创建 SVG 时，创建的元素都是需要添加命名空间的。

- 比如：创建 `<svg>` 或者 `<rect>` 元素时，都需要添加命名空间 “`http://www.w3.org/2000/svg`”
- 对于元素上不带前缀的属性，命名空间就为 `null`。

因为在 XML1.1 命名空间规范中建议，不带前缀的属性（带前缀如 `xlink:href`）命名空间的名称是没有值的，

这时命名空间的值必须使用 `null` 值。

创建 SVG 常用的 DOM API：

- `createElementNS(ns, elname)`：创建 SVG 元素；
- `setAttributeNS(ns, attrname, value)`：给 SVG 元素添加属性；
- `getAttributeNS(ns, attrname)`：获取 SVG 元素上的属性；
- `hasAttributeNS(ns, attrname)`： 判断 SVG 元素上是否存在某个属性；
- `removeAttributeNS(ns, attname)`：删除 SVG 元素上的某个属性；
- [更多的 API](https://developer.mozilla.org/zh-CN/docs/Web/SVG/Namespaces_Crash_Course)

03-SVG\demo-project\01-创建 SVG 的方式\05-方式三-通过 JS 来创建 SVG.html

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <script>
      /**
       * 使用 js 操作；
       * svg 的框架 Snap.svg，类似于 jQuery。
       */
      window.onload = function () {
        // 1.创建 svg 和 rect 元素
        const xmlns = 'http://www.w3.org/2000/svg'
        const svgEl = document.createElementNS(xmlns, 'svg')
        const rectEl = document.createElementNS(xmlns, 'rect')

        // 2.给 svg 和 rect 元素对象添加属性
        svgEl.setAttributeNS(null, 'version', '1.0')
        svgEl.setAttributeNS(null, 'width', 100)
        svgEl.setAttributeNS(null, 'height', 100)

        rectEl.setAttributeNS(null, 'width', 50)
        rectEl.setAttributeNS(null, 'height', 50)

        // 3.将 svg 添加到 body 上
        svgEl.appendChild(rectEl)
        document.body.appendChild(svgEl)
      }
    </script>
  </body>
</html>
```

# 七、SVG 在 HTML 中引用的方式

## 1.img 元素

作为一张图片使用，不支持交互，只兼容 ie9 以上。

```html
<img src="./rect.svg" alt="" />
```

## 2.CSS 背景

作为一张背景图片使用，不支持交互。

```css
.box {
  width: 200px;
  height: 200px;
  background-image: url(./rect.svg);
  background-repeat: no-repeat;
}
```

## 3.svg 元素

作为 HTML 的 DOM 元素，支持交互，只兼容 ie9 以上。见上方 [svg 元素](##2.svg 元素)。

## 4.object 元素（了解）

支持交互式 svg，能拿到 object 的引用，为 SVG 设置动画、更改其样式表等。

```html
<object data="./svg/rect.svg" type="image/svg+xml"></object>
```

## 5.iframe 元素（了解）

支持交互式 svg，能拿到 iframe 的引用，为 SVG 设置动画、更改其样式表等

```html
<iframe src="./svg/rect.svg"></iframe>
```

## 6.embed 元素（了解）

- 支持交互式 svg，能拿到 embed 的引用，为 SVG 设置动画、更改其样式表等，对旧版浏览器有更好的支持。

```html
<embed src="./svg/rect.svg" type="image/svg+xml" />
```

# 八、SVG 坐标系（Grid）

SVG 使用的坐标系统（网格系统）和 Canvas 的差不多；

坐标系以左上角 (0,0) 为坐标原点，被称为初始**视口坐标系**；

坐标以像素为单位，x 轴正方向向右，y 轴正方向向下。

- `<svg>` 元素默认宽为 `300px`, 高为 `150px`。默认被网格所覆盖。
- 通常来说，网格中的一个单元相当于 `<svg>` 元素中的一像素。
- `<svg>` 元素的 `transform` 属性可以用来移动、旋转、缩放 SVG 中的某个元素，
  - 如 `<svg>` 中某个元素用了变形，**该元素内部会建立一个新的坐标系统，该元后续所有形变都是基于新创建的坐标系统**。

03-SVG\demo-project\03-SVG 坐标系\01-坐标系统.html

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      body {
        margin: 0;
        padding: 0;
        background-image: url(../images/grid.png);
      }
      svg {
        background-color: rgba(255, 0, 0, 0.1);
      }
    </style>
  </head>
  <body>
    <svg width="300" height="300" xmlns="http://www.w3.org/2000/svg">
      <rect x="10" y="10" width="100" height="100"></rect>
    </svg>
  </body>
</html>
```

# 九、SVG 坐标系单位

SVG 坐标系统，在没有明确指定单位时，默认以像素为单位。

```html
<!-- 定义一个矩形，即从左上角开始，向右延展 100px，向下延展 100px，形成一个 100*100 大的矩形 -->
<rect x="0" y="0" width="100" height="100" />
```

也可以手动指明坐标系的单位，比如：

```html
<svg width="15cm" height="300" xmlns="http://www.w3.org/2000/svg">
  <rect x="10" y="10" width="100px" height="5cm"></rect>
</svg>
```

<img src="NodeAssets/可用于SVG元素的单位列表.jpg" style="zoom:80%;" />

# 十、SVG 视口（viewport）

视口是 SVG 可见的区域（也可以说是 SVG 画布大小）。

使用 `<svg>` 元素的 `width` 和 `height` 属性指定视口的大小。

一旦设置了 svg 元素的宽度和高度，浏览器就会建立“初始**视口坐标系**”和“初始**用户坐标系**”。

## 1.视口坐标系

视口坐标系是在视口上建立的坐标系，原点在视口左上角的点 (0, 0)，x 轴正向向右，y 轴正向向下。

初始视口坐标系中的一个单位等于视口中的一个像素，该坐标系类似于 HTML 元素的坐标系。

## 2.用户坐标系

**用户坐标系**是建立在 SVG 视口上的坐标系。该坐标系最初与视口坐标系相同，它的原点位于视口的左上角。

使用 `viewBox` 属性，可以修改初始用户坐标系，使其不再与视口坐标系相同。

用户坐标系，也称为**当前坐标系**或**正在使用的用户空间**，后面绘图都是参照该坐标系。

> 为什么要有两个坐标系？
>
> - 因为 SVG 是矢量图，支持任意缩放。在用户坐标系绘制的图形，最终会参照视口坐标系来进行等比例缩放。

03-SVG\demo-project\04-viewport 和 viewBox\02-viewport 和 viewBox 有相同的宽高比.html

```html
<svg width="400" height="400" viewBox="0 0 100 100">
  <circle cx="50" cy="50" r="50"></circle>
</svg>
```

### 1.svg 上的 viewBox 属性

`viewBox` 称为视图框：

- viewport 是 SVG 画布的大小，
- 而`viewBox` 是用来定义用户坐标系中的位置和尺寸的（该区域通常会被缩放来填充视口）。

SVG 的图形都是绘制在用户坐标系中。用户坐标系可以比视口坐标系更小或更大，也可以在视口内完全或部分可见。

一旦创建了视口坐标系（即 `<svg>` 使用 `width` 和 `height`），浏览器就会创建一个与其相同的用户坐标系。

`viewBox` 属性指定用户坐标系的大小。

- 如果用户坐标系与视口坐标系具有**相同的宽高比**，它将 `viewBox` 区域拉伸以填充视口区域。
- 如果用户坐标系和视口坐标系**没有相同的宽高比**，可用 `preserveAspectRatio` 属性来指定整个用户坐标系，是否在视口内可见。

`viewBox` 的语法：

- viewBox = “`<min-x> <min-y> <width> <height>`”，比如：`viewBox = “0 0 100 100”`
- `<min-x>`、`<min-y>` 确定视图框的左上角坐标
  - 即视图框的可见区域，**不是修改用户坐标系的原点**，绘图还是从原来的 (0, 0) 开始.
- `viewBox = "50 50 100 100"` 的效果如下图所示：

<img src="NodeAssets/确定视图框的左上角坐标.jpg" style="zoom:50%;" />

- `<width>`、`<height>` 确定该视图框的宽度和高度。
  - 宽度和高度为 0 是禁用元素的显示；
  - 宽度和高度负值无效。

用户坐标系与视口坐标系相同宽高比的情况：

等比例缩放：

```html
<svg width="400" height="400" viewBox="0 0 100 100">
  <circle cx="50" cy="50" r="50"></circle>
</svg>
```

<img src="NodeAssets/用户坐标系与视口坐标系相同宽高比情况.jpg" style="zoom:110%;" />

用户坐标系与视口坐标系不同宽高比的情况

保留视图框 `viewBox` 的宽高比，但视图框 `viewBox` 不会拉伸以覆盖整个视口区域。而是在视口内垂直和水平居中。

03-SVG\demo-project\04-viewport 和 viewBox\04-viewport 和 viewBox 不同的宽高比.html

```html
<svg width="400" height="400" viewBox="0 0 200 100">
  <circle cx="50" cy="50" r="50"></circle>
</svg>
```

<img src="NodeAssets/用户坐标系与视口坐标系不同宽高比情况一.jpg" style="zoom:80%;" />

改变视口内的视框位置，给 `<svg>` 添加 `preserveAspectRatio` 属性，该属性允许强制统一缩放视图框 viewBox

- `preserveAspectRatio= "none"`, 强制拉伸图形以填充整个视口。
- `preserveAspectRatio= “xMinYMin”`, 图形在视口的最小 x 和 y 轴上显示。

```html
<svg width="400" height="400" viewBox="0 0 200 100" preserveAspectRatio="xMinYMin">
  <circle cx="50" cy="50" r="50"></circle>
</svg>
```

<img src="NodeAssets/用户坐标系与视口坐标系不同宽高比情况二.jpg" style="zoom:80%;" />

# 十一、使用 SVG 绘制矩形

使用 `<rect>` 元素绘制矩形，其中有 6 个基本属性：

- `x`： 矩形左上角的 x 轴位置；
- `y`： 矩形左上角的 y 轴位置；
- `width`： 矩形的宽度；
- `height`： 矩形的高度；
- `rx`： 圆角的 x 轴方位的半径；
- `ry`： 圆角的 y 轴方位的半径。

03-SVG\demo-project\05-SVG 基本图形\01-绘制-矩形.html

```html
<svg width="300" height="300" xmlns="http://www.w3.org/2000/svg">
  <rect x="0" y="0" width="100" height="50"></rect>
  <rect x="100" y="100" width="100" height="50" rx="20" ry="20"></rect>
</svg>
```

