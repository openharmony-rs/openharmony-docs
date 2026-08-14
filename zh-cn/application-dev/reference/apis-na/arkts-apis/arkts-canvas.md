# canvas

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [CanvasGradient](arkts-na-canvas-canvasgradient-c.md) | 渐变对象。 |
| [CanvasPath](arkts-na-canvas-canvaspath-c.md) | Path object, which provides basic methods for drawing paths. |
| [CanvasRenderer](arkts-na-canvas-canvasrenderer-c.md) | Canvas渲染器，用于绘制形状、文本、图片等对象。 |
| [CanvasRenderingContext2D](arkts-na-canvas-canvasrenderingcontext2d-c.md) | CanvasRenderingContext2D对象与Canvas组件绑定后，可在Canvas组件上绘制， 绘制对象可以是形状、文本、图片等。 |
| [DrawingRenderingContext](arkts-na-canvas-drawingrenderingcontext-c.md) | DrawingRenderingContext对象与Canvas组件绑定后，可在Canvas组件上进行绘制， 绘制对象可以是形状、文本、图片等。 |
| [ImageBitmap](arkts-na-canvas-imagebitmap-c.md) | ImageBitmap对象可以存储canvas渲染的像素数据。 |
| [ImageData](arkts-na-canvas-imagedata-c.md) | ImageData对象可以存储canvas渲染的像素数据。 |
| [OffscreenCanvas](arkts-na-canvas-offscreencanvas-c.md) | OffscreenCanvas组件用于绘制自定义图形。 使用Canvas组件或CanvasRenderingContext2D对象时，渲染、动画和用户交互通常发生在应用程序的主线程上， 与画布动画和渲染相关的计算可能会影响应用程序性能。 OffscreenCanvas提供了一个可以在屏幕外渲染的画布，这样可以在单独的线程中运行一些任务， 从而避免影响应用程序主线程性能。 |
| [OffscreenCanvasRenderingContext2D](arkts-na-canvas-offscreencanvasrenderingcontext2d-c.md) | 使用OffscreenCanvasRenderingContext2D在Canvas上进行离屏绘制， 绘制对象可以是形状、文本、图片等。离屏绘制是指将需要绘制的内容先绘制在缓存区， 然后将其转换成图片，一次性绘制到Canvas上。离屏绘制使用CPU进行绘制， 绘制速度较慢，对绘制速度有要求的场景应避免使用离屏绘制。 |
| [Path2D](arkts-na-canvas-path2d-c.md) | 2D path object for path drawing |
| [RenderingContextSettings](arkts-na-canvas-renderingcontextsettings-c.md) | 用来配置CanvasRenderingContext2D对象的参数，包括是否开启抗锯齿。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CanvasParams](arkts-na-canvas-canvasparams-i.md) | 定义Canvas的具体配置参数。 |
| [CanvasPattern](arkts-na-canvas-canvaspattern-i.md) | 一个Object对象，使用createPattern方法创建，通过指定图像和重复方式创建图片填充的模板。 |
| [RenderingContextOptions](arkts-na-canvas-renderingcontextoptions-i.md) | 定义渲染上下文的具体配置参数。 |
| [TextMetrics](arkts-na-canvas-textmetrics-i.md) | 文本的尺寸信息。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [CanvasDirection](arkts-na-canvasdirection-t.md) | 定义当前文本方向的类型。 'inherit': 继承canvas组件通用属性已设定的文本方向，若canvas组件未设置direction属性，则跟随系统文字方向。 'ltr': 从左往右。 'rtl': 从右往左。 |
| [CanvasFillRule](arkts-na-canvasfillrule-t.md) | 定义用于确定点是在路径内还是路径外的填充样式算法的类型。 'evenodd': 奇偶规则。 此规则通过从画布上的某点向任意方向发射一条射线，并统计图形路径与射线的交点数量来判断该点是否在图形内部。 如果交点数量是奇数，则该点在图形内部，否则在图形外部。 'nonzero': 非零规则。 此规则通过从画布上的某点向任意方向发射一条射线，并检查图形路径与射线的交点来判断该点是否在图形内部。 初始计数为0，为路径的每一段线段指定一个方向值，每当路径从左向右穿过射线时加1，从右向左穿过时减1。 如果最终的结果是0，则该点在图形外部，否则在图形内部。 |
| [CanvasLineCap](arkts-na-canvaslinecap-t.md) | 定义绘制每条线段端点的类型。 'butt': 线条两端为平行线，不额外扩展。 'round': 在线条两端延伸半个圆，直径等于线宽。 'square': 在线条两端延伸一个矩形，宽度等于线宽的一半，高度等于线宽。 |
| [CanvasLineJoin](arkts-na-canvaslinejoin-t.md) | 定义长度不为0的两个连接部分（线段、圆弧和曲线）的类型。 'bevel': 在线段相连处使用三角形为底填充，每个部分矩形拐角独立。 'miter': 在相连部分的外边缘处进行延伸，使其相交于一点，形成一个菱形区域， 该属性可以通过设置miterLimit属性展现效果。 'round': 在线段相连处绘制一个扇形，扇形的圆角半径是线段的宽度。 |
| [CanvasTextAlign](arkts-na-canvastextalign-t.md) | 定义文本对齐方式的类型。ltr布局模式下'start'和'left'一致，rtl布局模式下'start'和'right'一致。 'center': 文本居中对齐。 'start': 文本对齐界线开始的地方。 'end': 文本对齐界线结束的地方。 'left': 文本左对齐。 'right': 文本右对齐。 |
| [CanvasTextBaseline](arkts-na-canvastextbaseline-t.md) | 定义文本基线类型。 'alphabetic': 文本基线是标准的字母基线。 'bottom': 文本基线在文本块的底部。与ideographic基线的区别在于ideographic基线不需要考虑下行字母。 'hanging': 文本基线是悬挂基线。 'ideographic': 文字基线是表意字基线；如果字符本身超出了alphabetic基线， 那么ideographic基线位置在字符本身的底部。 'middle': 文本基线在文本块的中间。 'top': 文本基线在文本块的顶部。 |
| [ImageSmoothingQuality](arkts-na-imagesmoothingquality-t.md) | 定义图片平滑度类型。 'high': 高画质。 'low': 低画质。 'medium': 中画质。 |

