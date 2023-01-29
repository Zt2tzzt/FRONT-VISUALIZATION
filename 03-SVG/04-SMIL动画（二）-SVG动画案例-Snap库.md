# 一、SMIL 动画元素

## 1.animateTransform 元素

`<animateTransform>` 元素，控制元素的形变（平移、旋转、缩放、倾斜）动画。

在一个 svg 元素中，`<animateTransform>` 只能使用一次，如果使用多次，后面会覆盖前面的。

`<animateTransform>` 常用属性：

- `attributeName`：指示将在动画期间更改的目标元素的 CSS 属性或元素属性（attribute）的名称。
- `type` ：指定形变动画的类型，只支持 `translate` | `rotate`（若有参数，`cx`, `cy` 参照用户坐标系） | `scale` | `skewX` | `skewY` 。
- 动画值属性：`from`、`to`、`values`
- 动画时间属性：`begin`、`dur`、`fill`、`repeatCount`

### 1.平移（translate）动画

03-SVG\demo-project\13-SVG的SMIL动画\03-animateTransform-translate.html

```xml
<svg width="300" height="200" xmlns="http://www.w3.org/2000/svg" >
	<rect x="0" y="0" width="100" height="50" fill="red">
		<animateTransform
			attributeName="transform"
			type="translate"
			from="0, 0"
			to="200, 0"
			dur="2s"
			begin="1s"
			repeatCount="indefinite"
		>
		</animateTransform>
	</rect>
</svg>

<svg width="300" height="200" xmlns="http://www.w3.org/2000/svg" >
	<rect x="0" y="0" width="100" height="50" fill="red">
		<animateTransform
			attributeName="transform"
			type="translate"
			values="0 0; 200 0"
			dur="2s"
			begin="1s"
			repeatCount="indefinite"
		>
		</animateTransform>
	</rect>
</svg>
```

### 2.旋转（rotate）动画

可指定旋转的圆心点：`cx`, `cy`；

03-SVG\demo-project\13-SVG的SMIL动画\04-animateTransform-rotate.html

```xml
<svg width="300" height="300" xmlns="http://www.w3.org/2000/svg" >
	<rect x="0" y="0" width="50" height="50" fill="red">
		<animateTransform
			attributeName="transform"
			type="rotate"
			from="0 50 50"
			to="360 50 50"
			dur="5s"
			begin="1s"
			repeatCount="indefinite"
		>
		</animateTransform>
	</rect>
</svg>

<svg width="300" height="200" xmlns="http://www.w3.org/2000/svg" >
	<rect x="0" y="0" width="100" height="50" fill="red">
		<animateTransform
			attributeName="transform"
			type="rotate"
			values="0 50 25; -360 50 25"
			dur="2s"
			begin="1s"
			repeatCount="indefinite"
		>
		</animateTransform>
	</rect>
</svg>
```

### 3.缩放（sclae）动画

03-SVG\demo-project\13-SVG的SMIL动画\05-animateTransform-scale.html

```xml
<svg width="300" height="200" xmlns="http://www.w3.org/2000/svg" >
	<rect x="0" y="0" width="100" height="50" fill="red">
		<animateTransform
			attributeName="transform"
			type="scale"
			from="1 1"
			to="1 3"
			dur="2s"
			begin="1s"
			repeatCount="indefinite"
		>
		</animateTransform>
	</rect>
</svg>

<svg width="300" height="200" xmlns="http://www.w3.org/2000/svg" >
	<rect x="0" y="0" width="100" height="50" fill="red">
		<animateTransform
			attributeName="transform"
			type="scale"
			values="1; 0.5"
			dur="2s"
			begin="1s"
			repeatCount="indefinite"
		>
		</animateTransform>
	</rect>
</svg>
```

## 2.animateMotion 元素

`<animateMotion>` 定义了一个元素沿着路径进行移动。

- 进行动画的元素的坐标原点，会影响元素运动路径，建议将进行动画的元素放置在 `(0, 0)` 点开始。
- 要复用现有路径，可在 `<animateMotion>` 元素中使用 `<mpath>` 元素。

`<animateMotion>` 元素常用属性：

- `path`：定义运动的路径，值和 `<path>` 元素的 `d` 属性一样；
- `href`：引用一个进行动画的元素。
- `rotate`：动画元素自动跟随路径旋转，使元素动画方向和路径方向相同，值类型：`<number>` | `auto` | `auto-reverse`; 默认值：0
- 动画值属性：`from`、`to`、`values`
- 动画时间属性：`begin`、`dur`、`fill`、`repeatCount`

### 1.基本使用

```xml
<svg width="300" height="300" xmlns="http://www.w3.org/2000/svg" >
	<!-- 画一条路径 -->
	<path d="M 0 100, L 100 30, L 200 100, L 300 30" fill="transparent" stroke="red"></path>

  <!-- 汽车 -->
	<rect x="0" y="0" width="20" height="10" rx="4" ry="4" fill="red">
		<animateMotion
			path="M 0 100, L 100 30, L 200 100, L 300 30"
			dur="5s"
			rotate="auto"
		>
		</animateMotion>
	</rect>
</svg>
```

### 2.路径的复用

使用 `<mpath>`：

03-SVG\demo-project\13-SVG的SMIL动画\07-animateMotion动画-复用路径.html

```xml
<svg width="300" height="300" xmlns="http://www.w3.org/2000/svg" >
	<!-- 路径 -->
	<path id="linePath" d="M 0 100, L 100 30, L 200 100, L 300 30" fill="transparent" stroke="red"></path>

	<!-- 汽车 -->
	<rect x="0" y="0" width="20" height="10" rx="4" ry="4" fill="red">
		<!-- 动画 -->
		<animateMotion
			dur="5s"
			rotate="auto"
		>
			<mpath href="#linePath"></mpath>
		</animateMotion>
	</rect>
</svg>
```

### 3.动画的抽取

03-SVG\demo-project\13-SVG的SMIL动画\08-animateMotion动画-优化.html

```xml
<svg width="300" height="300" xmlns="http://www.w3.org/2000/svg" >

	<!-- 汽车 -->
	<rect id="rectangle" x="-10" y="-5" width="20" height="10" rx="4" ry="4" fill="red"></rect>

	<!-- 路径 -->
	<path id="linePath" d="M 0 100, L 100 30, L 200 100, L 300 30" fill="transparent" stroke="red"></path>

	<!-- 动画 -->
	<animateMotion
		href="#rectangle"
		dur="5s"
		rotate="auto"
		fill="freeze"
	>
		<mpath href="#linePath"></mpath>
	</animateMotion>
</svg>
```

# 二、SVG + SMIL 动画案例

飞机轨迹飞行

03-SVG\demo-project\14-SVG动画案例\01-飞机飞行轨迹-temp.html

动态图片案例

03-SVG\demo-project\14-SVG动画案例\02-进度加载动画-temp.html

# 三、SVG + CSS3 动画案例

城市定位动图

03-SVG\demo-project\14-SVG动画案例\03-定位动画+CSS3-temp.html

水球加载动图

03-SVG\demo-project\14-SVG动画案例\04-水球体+CSS3-temp.html

# 四、Snap 库

[Snap.svg 官网](http://snapsvg.io/)

## 1.Snap.svg 是什么？

Snap.svg 由 Dmitry Baranovskiy 从零开始编写，是一个专门用于处理 SVG 的 JavaScript 库 (类似 jQuery)。

Snap 为 Web 开发人员提供了干净、直观、功能强大的 API，专门用来操作 SVG。

Snap 可用于创建动画，操作现有的 SVG 内容，以及生成 SVG 内容。

## 2.Snap.svg 优势

Snap.svg 专为现代浏览器（IE9 及更高版本、Safari、Chrome、Firefox 和 Opera）而设计。并且支持遮罩、剪辑、图案、全渐变、组等功能。

SVG 内容不必使用 Snap 生成，也可使用 Snap 来处理它。

- 比如可以在 Illustrator 或 Sketch 等工具中创建 SVG 内容，然后使用 Snap 对其进行动画处理或其它操作。

Snap.svg 库处理 SVG 就像 jQuery 处理 DOM 一样简单，并且 Snap 是 100% 免费和 100% 开源的。

## 3.Snap.svg 的初体验

### 1.绘制一个圆

03-SVG\demo-project\15-第三方动画库-snap\01-Snap.svg的初体验.html

```html
<body>
  <script src="./libs/snap.svg-min.js"></script>
  <script>
    window.onload = function() {

      // 1.创建一个 svg 画布
      const svg = Snap(300, 300)
      console.log(svg === svg.paper) // true

      // 2.在 svg 画布中绘制一个圆
      const circle = svg.paper.circle(100, 100, 50)

      // 3.给圆添加一些属性
      circle.attr({
        fill: 'skyblue'
      })

      // 获取 svg 的元素的对象
      console.log(svg.node)

      // 4.将 svg 添加到 body 中
      document.body.appendChild(svg.node)
    }
  </script>
</body>
```

### 2.选中已有的 svg 元素

03-SVG\demo-project\15-第三方动画库-snap\02-Snap.svg操作SVG.html

```html
<body>
  <svg id="ztSvg" width="300" height="300" xmlns="http://www.w3.org/2000/svg" >
    <rect id="rectangle1" x="0" y="0" width="100" height="50"></rect>
  </svg>

  <script src="./libs/snap.svg-min.js"></script>
  <script>
    window.onload = function() {
      // 选中已有的 svg 画布
      const svg = Snap('#ztSvg')
      const paper = svg.paper

      // 1.绘制一个矩形
      const rectangle = paper.rect(0, 100, 100, 50)
      rectangle.attr({
        fill: 'red'
      })

      // 2.选择一个矩形
      const rectangle1 = paper.select('#rectangle1')
      rectangle1.attr({
        fill: 'green'
      })
    }
  </script>
</body>
```

### 3.常用的 API

`Snap`：工厂函数

- `Snap(w, h)` ：创建 svg 画布。
- `Snap(selector)` ：获取已存在的 svg 画布。

`paper`: 纸张 / SVG 画布

- `paper.circle`、`paper.rect`、`paper.line`、`paper.path`、`paper.text` …

Element：元素

- `animate`、`attr`、`select`、`before`、`after` …

`mina`：通常用到的一些动画时间函数。

- `mina.linear`、`mina.easeIn`、`mina.easeOut` …

### 4.动画实现

03-SVG\demo-project\15-第三方动画库-snap\03-Snap.svg-动画实现.html

```html
<body>
  <svg id="hySvg" width="300" height="300" xmlns="http://www.w3.org/2000/svg" >
    <rect id="rectangle1" x="0" y="0" width="100" height="50"></rect>
  </svg>

  <script src="./libs/snap.svg-min.js"></script>
  <script>
    window.onload = function() {
      const svg = Snap('#hySvg')
      const paper = svg.paper

      // 1.绘制一个矩形
      const rectangle = paper.rect(0, 100, 100, 50)
      rectangle.attr({
        fill: 'red'
      })

      // 2.选择一个矩形
      const rectangle1 = paper.select('#rectangle1')
      rectangle1.attr({
        fill: 'green'
      })

      // 3.动画的实现（底层用 requestAnimatationFrame 实现，1s 回调 61 次)
      Snap.animate(
        0, // from
        200, // to
        function(val) {
          console.log('val', val) // 函数会回调 61 次, 会将 0-200 拆分成 61 份
          rectangle.attr({
            x: val
          })
        },
        1000, // begin 毫秒 -> 1s
        mina.linear,
        function() {
          console.log('动画结束了')
        }
      )
    
      Snap.animate(
        [0, 0], // from x ,y 
        [200, 200], // to x, y
        function(val) {
          console.log('val', val)
          rectangle1.attr({
            x: val[0],
            y: val[1]
          })
        },
        3000,
        mina.easeout,
        function() {
          console.log('动画结束了')
        }
      )
    }
  </script>
</body>
```

## 2.Snap.svg 鳄鱼动画案例

03-SVG\demo-project\15-第三方动画库-snap\04-鳄鱼+Snap-temp.html

