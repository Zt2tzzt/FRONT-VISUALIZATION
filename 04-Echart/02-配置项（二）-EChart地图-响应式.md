# 一、series 配置项（二）

## 1.legend 图例配置

[legend：图例](https://echarts.apache.org/zh/option.html#legend)，展现了不同系列的标记、颜色和名字（从 `data` 中获取）。object 类型。

- `show`、`icon`、`formatter`、`textStyle`、`itemWidth`、`itemGap` ...

04-Echart\demo-project\02-ECharts的组件和配置\09-ECharts-legend-图例组件.html

```js
window.onload = function() {
	const myChart = echarts.init(document.getElementById('main'));
	const option = {
		backgroundColor: 'rgba(255, 0, 0, 0.1)',
		grid: {
			show: true,
			backgroundColor: 'rgba(0, 255, 0, 0.1)',
		},
		legend: {
			show: true,
			// width: 100,
			// itemWidth: 20,
			icon: 'circle',  // round ...
			formatter: 'zhu-{name}', // 字符春写法
			formatter: function(name) { // 函数的写法
				console.log(name)
				return name + '{percentageStyle|\n40%}' // 富文本的语法: {styleName|content}，\n 表示换行
			},
			textStyle: {
				rich: { // 给富文本添加样式
					percentageStyle: {
						// css 样式
						color: 'red',
						fontSize: 12
					}
				}
			}

		},
		xAxis: {
			show: false,
			data: ['衬衫', '羊毛衫', '雪纺衫', '裤子', '高跟鞋', '袜子']
		},
		yAxis: {},
		series: [
			{
				type: 'pie',
				label: {
					show: true
				},
				data: [
					{
						value: 5,
						name: "衬衫", // 数据项名称, 比如pie系列 tooltip 需要用到
					},
					{
						value: 20,
						name: "羊毛衫",
					},
					{
						value: 36,
						name: "雪纺衫",
					},
					{
						value: 10,
						name: "裤子",
					},
					{
						value: 10,
						name: "高跟鞋",
					},
					{
						value: 20,
						name: "袜子",
					},
				],
			}
		]
	};
	myChart.setOption(option);
}
```

## 2.tooltip 提示框配置

[tooltip：提示框组件](https://echarts.apache.org/zh/option.html#legend.tooltip)，object 类型。

- `show`、`trigger`、`axisPointer` ……

04-Echart\demo-project\02-ECharts的组件和配置\10-ECharts-tooltip-提示框组件.html

```js
window.onload = function() {
	const myChart = echarts.init(document.getElementById('main'));
	const option = {
		backgroundColor: 'rgba(255, 0, 0, 0.1)',
		grid: {
			show: true,
			backgroundColor: 'rgba(0, 255, 0, 0.1)',
		},
		tooltip: {
			show: true,
			// 使用了 trigger，一般也结合 axisPointer
			trigger: "axis",  // 默认是 item
			axisPointer: {
				type: "shadow", //  line，默认是竖线；cross，横线 + 竖线；shadow，横线 + 竖线；
			},
			// formatter: '<div style="color:red">haha</div>'
		},
		xAxis: {
			data: ['衬衫', '羊毛衫', '雪纺衫', '裤子', '高跟鞋', '袜子']
		},
		yAxis: {},
		series: [
			{
				type: 'bar',
				data: [5, 20, 36, 10, 10, 20]
			}
		]
	};
	myChart.setOption(option);
}
```

# 二、ECharts 中配置 color 渐变色

ECharts 中 Color 支持的格式：RGB、RGBA、关键字、十六进制格式：

ECharts 中的渐变色：

- 线性渐变，前四个参数分别是 `(x, y)`, `(x2, y2)` 范围从 `0 – 1`。
- 径向渐变，前三个参数分别是圆心坐标 `x`, `y` 和半径 `r`，取值同线性渐变。

04-Echart\demo-project\02-ECharts的组件和配置\11-ECharts-图形-渐变色.html

```js
window.onload = function() {
	const myChart = echarts.init(document.getElementById('main'));
	const option = {
		backgroundColor: 'rgba(255, 0, 0, 0.1)',
		grid: {
			show: true,
			backgroundColor: 'rgba(0, 255, 0, 0.1)',
		},
		tooltip: {
			show: true,
			trigger: "axis",
			axisPointer: {
				type: "shadow",
			},
		},
		xAxis: {
			data: ['衬衫', '羊毛衫', '雪纺衫', '裤子', '高跟鞋', '袜子']
		},
		yAxis: {},
		series: [
			{
				type: 'bar',
				// 图形的颜色
				itemStyle: {
					color: {
						// 渐变
						type: "linear",
						x: 0,
						y: 0,
						x2: 0,
						y2: 1,
						colorStops: [
							{
								offset: 0,
								color: "red",
							},
							{
								offset: 1,
								color: "blue",
							},
						],
					}
				},
        data: [
					{
						value: 5,
						name: "衬衫", // 数据项名称, 比如pie系列 tooltip 需要用到
						// 图形的颜色
						itemStyle: {
							color: new echarts.graphic.LinearGradient(
								0,
								0,
								0,
								1,
								[
									{
										offset: 0,
										color: "#20FF89",
									},
									{
										offset: 1,
										color: "rgba(255, 255, 255, 0)",
									},
								],
								false
							),
						},
					},
					{
						value: 20,
						name: "羊毛衫",
					},
					{
						value: 36,
						name: "雪纺衫",
					},
					{
						value: 10,
						name: "裤子",
					},
					{
						value: 10,
						name: "高跟鞋",
					},
					{
						value: 20,
						name: "袜子",
					},
				],

			}
		]
	};
	myChart.setOption(option);
}
```
# 三、读懂案例中的配置

## 1.读懂柱形图案例的配置项

04-Echart\demo-project\03-ECharts图表实战\01-柱形图.html

## 2.读懂折线图案例的配置项

04-Echart\demo-project\03-ECharts图表实战\02-折线图-.html

## 3.读懂饼图案例的配置项

04-Echart\demo-project\03-ECharts图表实战\03-饼图-.html

# 四、ECharts 地图绘制

ECharts 需要使用 GeoJSON 格式的数据作为地图的轮廓，获取第三方的 GeoJSON 数据注册到 ECharts 中：[获取方式一](https://github.com/echarts-maps/echarts-china-cities-js/tree/master/js/shape-with-internal-borders)；[获取方式二](https://datav.aliyun.com/portal/school/atlas/area_selector)

## 1.ECharts 地图引入并展示

### 1.引入地图配置方式：

#### 1.引入 json 文件

引入 json 格式的地图数据，并手动注册。

```js
echarts.registerMap('china', { geoJSON: china_geojson })
```

#### 2.引入 js 文件

引入 js 文件，该文件中已经将 json 数据注册好。

### 2.展示地图的两种方式：

#### 1.配置 geo 选项。

04-Echart\demo-project\04-Echarts地图\01-方式一-初体验中国地图-json.html

```js
window.onload = function() {
	// 2.注册一下中国地图的 geo json ( 需要在 setOption 之前调用 )
	echarts.registerMap('china', { geoJSON: china_geojson })
	const myChart = echarts.init(document.getElementById('main'));
	const option = {
		// 3.在 echarts 中展示中国地图
		geo: {
			map: 'china'
		},
	};
	myChart.setOption(option);
}
```

#### 2.配置 series 选项

配置 `series` 选项，`series: {type: "map", map: "china"}`。

04-Echart\demo-project\04-Echarts地图\02-方式二-初体验中国地图-json.html

```js
window.onload = function() {
  // 2.注册一下中国地图的 geojson ( 需要在 setOption 之前调用 )
  echarts.registerMap('china', { geoJSON: china_geojson })

  const myChart = echarts.init(document.getElementById('main'));
  const option = {
    // 3.在 echarts 中展示中国地图
    series: [
      {
        type: 'map', // 系列图是 地图
        map: 'china' // 展示中国地图（因为只注册一个中国地图）
      }
    ]
  };
  myChart.setOption(option);
}
```

#### 1.两种方式有何区别？

方式一：`geo` 组件配置：

- 会生成一个 geo 地理坐标系组件，用于地图的绘制；
- 该组件上支持绘制散点图，线集；
- 该组件可以共其它系列复用；

> 注意：其他系列在复用该地理坐标系时，`series` 的 `itemStyle` 等样式将不起作用。

方式二：`series` 系列图组件 `map` 配置：

- 默认情况下，会自己生成内部专用的 geo 地理坐标系组件；用于地图的绘制；
- 主要用于地理区域数据的可视化，配合 `data`, `visualMap` 使用

04-Echart\demo-project\04-Echarts地图\03-geo地图和series地图区别.html

```js
window.onload = function() {
	// 2.注册一下中国地图的 geo json ( 需要在setOption之前调用 )
	echarts.registerMap('中国', { geoJSON: china_geojson })

	const myChart = echarts.init(document.getElementById('main'));
	const option = {
		geo: [
			{
				map: '中国', // 全局的地图( 创建一个地理坐标系统, 供其它系列复用该坐标系 )
				roam: true, // 可拖动地图
			}
		],
		series: [
			{
				type: 'map', // 系列图是 地图( 创建一个地理坐标系统, 用来展示数据 )
				map: '中国',
				roam: true,

			}
		]
	};
	myChart.setOption(option);
}
```

## 2.ECharts 地图着色

地图着色，通过 `itemStyle` 属性中的 `areaColor` 和 `borderColor` 属性。

- `areaColor`：地图区域的颜色；
- `borderColor`：图形（边界）的描边颜色。

04-Echart\demo-project\04-Echarts地图\04-中国地图着色.html

```js
window.onload = function() {
	echarts.registerMap('china', { geoJSON: china_geojson })
	const myChart = echarts.init(document.getElementById('main'));
	const option = {
		tooltip: {},
		// 方式一
		geo: {
			map: 'china',
			itemStyle: {
				areaColor: "#023677", // 地图区域的颜色。
				borderColor: "#1180c7", // 图形的描边颜色。
			},

			emphasis: {
				itemStyle: {
					areaColor: "#4499d0",
				},
				label: {
					color: "white",
				},
			},
		},
		// 方式二
		series: [
			{
				type: 'map', // 系列图是 地图(创建一个地理坐标系统, 用来展示数据)
				map: 'china', //
				roam: true,
				itemStyle: {
					areaColor: "#023677", // 地图区域的颜色。
					borderColor: "#1180c7", // 图形的描边颜色。
				},

				emphasis: {
					itemStyle: {
						areaColor: "#4499d0",
					},
					label: {
						color: "white",
					},
				},
			}
		]
	};
	myChart.setOption(option);
}
```

## 3.ECharts 地图数据可视化

主要步骤：

1. 数据填充；
2. 添加视觉映射。

04-Echart\demo-project\04-Echarts地图\05-中国地图-填充数据.html

```js
const option = {
	tooltip: {},
	grid: {},

	// 1.视觉数据映射
	visualMap: [
		{
			type: "continuous", // 连续型视觉映射组件 (默认)
			// type: "piecewise", // 分段型视觉映射组件
			left: "20%",
			seriesIndex: [0], // 指定取哪个系列的数据
			// 定义 在选中范围中的视觉元素, 对象类型。
			inRange: {
				color: ["#04387b", "#467bc0"], // 映射组件和地图的颜色(一般和地图色相近)
			},
		},
	],

	series: [
		{
			name: "中国地图",
			type: "map",
			map: "中国",
			data,
			/* data: [
				{ name: "北京", value: 199 },
				{ name: "天津", value: 42 },
				// ……
			], */
			itemStyle: {
				areaColor: "#023677",
				borderColor: "#1180c7",
			},
			emphasis: {
				itemStyle: { areaColor: "#4499d0" },
				label: { color: "white" },
			},
			select: {
				label: { color: "white" },
				itemStyle: { areaColor: "#4499d0" },
			},
		},
	],
};
```

## 4.ECharts 地图散点图设置

基本步骤：

1. 添加一个 effectScatter series；
   - `series: {type: 'effectScatter'}`
2. 指定使用的地理坐标系；
   - `series: {geoIndex: 0, coordinateSystem: "geo"}` 复用 geo 组件。
3. 添加地图所需的数据；
   - `series: {data: ...}`
4. 修改标记的大小和样式；
5. 修改默认的 `tooltip` 提示。

04-Echart\demo-project\04-Echarts地图\06-中国地图+散点图.html

```js
const option = {
	// 3.在 echarts 中展示中国地图
  geo: [
    {
      map: '中国'
    }
  ],
  series: [
    {
      name: "散点图",
      type: "effectScatter",
      geoIndex: 0, // geo 支持数组，默认是 0
      coordinateSystem: "geo", // 使用地理坐标系，通过 geoIndex 指定相应的地理坐标系组件。
      data: [
        {
          name: "广东",
          value: [113.280637, 23.125178, 93],
        },
        {
          name: "北京",
          value: [116.405285, 39.904989, 199],
        },
      ],

      // ====== 散点大小和着色========
      symbolSize: function(val) {
        console.log(val)
        return val[2] / 10;  // 控制散点图的大小
      },
      itemStyle: {
        color: "green",
        shadowBlur: 10,
        shadowColor: "yellow",
      },
      // ====== 散点大小和着色========
    }
  ]
}
```

## 5.ECharts 地图综合案例

04-Echart\demo-project\04-Echarts地图\07-中国地图+散点图-最终案例.html

# 五、ECharts 常见 API 总结

[全局 echarts 对象](https://echarts.apache.org/zh/api.html#echarts)，在 script 标签引入 echarts.js 文件后获得。

- `init(dom，theme，opts)`：创建 echartsInstance 实例。
- `registerMap(mapName，opts)`：注册地图。
- `getMap(mapName)`：获取已注册地图。

通过 `echarts.init`，创建的 [echartsInstance 实例](https://echarts.apache.org/zh/api.html#echartsInstance)

- `setOption(opts)`：设置图表实例的配置项以及数据，万能接口。
- `getWidth()`、`getHeight()`：获取 ECharts 实例容器的宽高度。
- `resize(opts)`：改变图表尺寸，在容器大小发生改变时需要手动调用。
- `showLoading()`、`hideLoading()`：显示和隐藏加载动画效果。
- `dispatchAction( )`：触发图表行为，例如：图例开关、显示提示框等。
- `dispose()`：销毁实例，销毁后实例无法再被使用。
- `on()`：添加事件处理函数，该文档描述了所有 ECharts 的事件列表。

# 六、ECharts 响应式图表实现

## 1.根据窗口大小，改变图表宽度

基本步骤：

1. 图表设置高度，宽度设置为 `100%` 或不设置。
2. 监听窗口的 `resize` 事件（如果要考虑性能优化，需节流）。
3. 当窗口大小改变时，调用 `echartsInstance.resize()` 改变图表的大小。

04-Echart\demo-project\05-ECharts的补充API\01-响应式图表-.html

```js
window.onload = function() {
	const myChart = echarts.init(document.getElementById('main'));
  
	const option = {
		backgroundColor: 'rgba(255, 0, 0, 0.1)',
		grid: {
			show: true,
			backgroundColor: 'rgba(0, 255, 0, 0.1)',
		},
		xAxis: {
			data: ['衬衫', '羊毛衫', '雪纺衫', '裤子', '高跟鞋', '袜子']
		},
		yAxis: {},
		series: [
			{
				type: 'bar',
				data: [5, 20, 36, 10, 10, 20]
			}
		]
	};
  
	myChart.setOption(option);

	// 1.响应式图表
	window.addEventListener('resize', function() {
		myChart.resize()
	})
}
```

## 2.轮播显示 tooltip

04-Echart\demo-project\05-ECharts的补充API\02-自动触发Action实现提示框轮播.html

```js
window.onload = function() {
	const myChart = echarts.init(document.getElementById('main'));
  
	const option = {
		backgroundColor: 'rgba(255, 0, 0, 0.1)',
		grid: {
			show: true,
			backgroundColor: 'rgba(0, 255, 0, 0.1)',
		},
		tooltip: {
			position: 'top', // top
		},
		xAxis: {
			data: ['衬衫', '羊毛衫', '雪纺衫', '裤子', '高跟鞋', '袜子']
		},
		yAxis: {},
		series: [
			{
				type: 'bar',
				data: [5, 20, 36, 10, 10, 20]
			}
		]
	};
  
	myChart.setOption(option);

	// 1.实现提示框轮播的功能
	setInterval(function () {
		autoToolTip();
	}, 1000);

	let index = 0; // 0-5

	function autoToolTip() {
		if (++index > 5) index = 0;
		// 1.显示提示框
		myChart.dispatchAction({
			type: "showTip", // 触发的 action type
			seriesIndex: 0, // 系列的 索引
			dataIndex: index,// 数据项的 索引
			position: "top", // top
		});
	}
}
```

## 3.动态注册地图，点击展示

04-Echart\demo-project\05-ECharts的补充API\03-地图-下钻.html

```html
<button onclick="back()"> 返回 > 中国地图</button>
<div id="main" style="height: 400px"></div>
```

```js
let myChart = null
let option = {}
window.onload = function() {
	// 2.注册一下中国地图的 geo json ( 需要在setOption之前调用 )
	echarts.registerMap('中国', { geoJSON: china_geojson })

	myChart = echarts.init(document.getElementById('main'));
	option = {
		series: [
			{
				type: 'map', // 系列图是 地图
				map: '中国', // 展示中国地图( 因为只注册一个中国地图 )
				roam: true
			}
		]
	};
	myChart.setOption(option);

	// 1.地图下钻的功能
	myChart.on('click', function(event) {
		console.log(event)
		if(event.name === '广东'){
			// 如果还未注册地图
			if(!echarts.getMap(event.name)){
				// 注册地图
				echarts.registerMap(event.name, { geoJSON: guangdong_geojson })
			}
			option.series[0].map = event.name // 将中国地图切换为广东地图
			myChart.setOption(option)
		}
	})
}
function back() {
	option.series[0].map ='中国'
	myChart.setOption(option)
}
```
