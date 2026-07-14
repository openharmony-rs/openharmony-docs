# @ohos.graphics.drawing

应用在开发中，经常需要针对不同的元素内容进行绘制，开发者通常可以选择直接使用ArkUI组件来绘制想要的元素或效果，但有些自定义图形或
效果无法满足，此时可以选择使用Drawing来实现灵活的自定义绘制效果。Drawing模块提供基本的绘
制能力，如绘制矩形、圆形、点、直线、自定义Path和字体等。

> **说明：**
>
> - 本模块使用屏幕物理像素单位px。
>
> - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 11

**系统能力：** SystemCapability.Graphics.Drawing

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [Brush](arkts-arkgraphics2d-brush-c.md) | 画刷对象，描述所绘制图形的填充信息。 |
| [Canvas](arkts-arkgraphics2d-canvas-c.md) | 承载绘制内容与绘制状态的载体。 |
| [ColorFilter](arkts-arkgraphics2d-colorfilter-c.md) | 颜色滤波器。 |
| [Font](arkts-arkgraphics2d-font-c.md) | 描述字型绘制时所使用的属性，如大小、字体等。 |
| [ImageFilter](arkts-arkgraphics2d-imagefilter-c.md) | 图像滤波器。 |
| [Lattice](arkts-arkgraphics2d-lattice-c.md) | 矩形网格对象。该对象用于将图片按照矩形网格进行划分。 |
| [MaskFilter](arkts-arkgraphics2d-maskfilter-c.md) | 蒙版滤镜对象。 |
| [Matrix](arkts-arkgraphics2d-matrix-c.md) | 矩阵对象。表示为3*3的矩阵，如下图所示：![matrix_3x3](../../../../reference/apis-arkgraphics2d/figures/matrix3X3.PNG)矩阵中的元素从左到右，从上到下分别表示水平缩放系数、水平倾斜系数、水平位移系数、垂直倾斜系数、垂直缩放系数、垂直位移系数、X轴透视系数、Y轴透视系数、透视缩放系数。设(x&lt;sub&gt;1&lt;/sub&gt;, y&lt;sub&gt;1&lt;/sub&gt;)为源坐标点，(x&lt;sub&gt;2&lt;/sub&gt;, y&lt;sub&gt;2&lt;/sub&gt;)为源坐标点通过矩阵变换后的坐标点，则两个坐标点的关系如下：![matrix_xy](../../../../reference/apis-arkgraphics2d/figures/matrix_xy.PNG) |
| [Path](arkts-arkgraphics2d-path-c.md) | 由直线、圆弧、二阶贝塞尔、三阶贝塞尔组成的复合几何路径。 |
| [PathEffect](arkts-arkgraphics2d-patheffect-c.md) | 路径效果对象。 |
| [PathIterator](arkts-arkgraphics2d-pathiterator-c.md) | 表示路径操作迭代器，可通过遍历迭代器读取path的操作指令。 |
| [Pen](arkts-arkgraphics2d-pen-c.md) | 画笔对象，描述所绘制图形形状的轮廓信息。 |
| [PointUtils](arkts-arkgraphics2d-pointutils-c.md) | This class offers a comprehensive set of operations for handling common2D Point objects. |
| [RectUtils](arkts-arkgraphics2d-rectutils-c.md) | 提供了处理矩形的工具。主要的使用场景：1. 矩形快速构建与获取基本属性，如构造新矩形、拷贝矩形、获取矩形的宽高以及中心点等。2. 边界计算与调整，如获取包含关系、计算与更新矩形之间交集和并集，更新边界值等。 |
| [Region](arkts-arkgraphics2d-region-c.md) | 区域对象，用于描述所绘制图形的区域信息。 |
| [RoundRect](arkts-arkgraphics2d-roundrect-c.md) | 圆角矩形对象。 |
| [SamplingOptions](arkts-arkgraphics2d-samplingoptions-c.md) | 采样选项对象。 |
| [ShaderEffect](arkts-arkgraphics2d-shadereffect-c.md) | 着色器。画刷和画笔设置着色器后，会使用着色器效果而不是颜色属性去绘制，但此时画笔和画刷的透明度属性仍然生效。 |
| [ShadowLayer](arkts-arkgraphics2d-shadowlayer-c.md) | 阴影层对象。 |
| [TextBlob](arkts-arkgraphics2d-textblob-c.md) | 由一个或多个具有相同字体的字符组成的字块。 |
| [Tool](arkts-arkgraphics2d-tool-c.md) | 本模块定义的工具类，仅提供静态的方法，主要完成其他模块和[common2D](arkts-graphics-common2d.md)中定义的数据结构的转换功能等操作。 |
| [Typeface](arkts-arkgraphics2d-typeface-c.md) | 字体，如宋体、楷体等。 |
| [TypefaceArguments](arkts-arkgraphics2d-typefacearguments-c.md) | 提供字体属性配置的结构体。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [FontFeature](arkts-arkgraphics2d-fontfeature-i.md) | 表示字体特征。字体特征是字体内置的排版规则，用于控制字形的显示效果，具体包括连字、替代字形、上下标等功能。 |
| [FontMetrics](arkts-arkgraphics2d-fontmetrics-i.md) | 描述字形大小和布局的属性信息，同一种字体中的字符属性大致相同。 |
| [TextBlobRunBuffer](arkts-arkgraphics2d-textblobrunbuffer-i.md) | 描述一行文字中具有相同属性的连续字形。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BlendMode](arkts-arkgraphics2d-blendmode-e.md) | 混合模式枚举。混合模式会将两种颜色（源色、目标色）以特定的方式混合生成一种新的颜色，通常用于叠加、滤镜和遮罩等图形操作场景。混合操作会分别作用于红、绿、蓝三个颜色通道，采用相同的混合逻辑，而透明度（Alpha通道）则根据各模式的定义另行处理。为简洁起见，我们使用以下缩写：s : source 源的缩写。d : destination 目标的缩写。sa : source alpha 源透明度的缩写。da : destination alpha 目标透明度的缩写。计算结果用如下缩写表示：r : 如果4个通道（透明度、红、绿、蓝）的计算方式相同，用r表示。ra : 如果只操作透明度通道，用ra表示。rc : 如果操作3个颜色通道，用rc表示。以黄色矩形为源图像，蓝色圆形为目标图像，各混合模式枚举生成的效果示意图请参考下表。 |
| [BlurType](arkts-arkgraphics2d-blurtype-e.md) | 定义蒙版滤镜模糊中操作类型的枚举。\| 名称 \| 值 \| 说明 \| 示意图 \|\| ------ \| - \| ------------------ \| -------- \|\| NORMAL \| 0 \| 全面模糊，外圈边缘和内部实体一起模糊。 \| ![image_BlueType_Normal.png](../../../../reference/apis-arkgraphics2d/figures/zh-ch_image_BlueType_Normal.png) \|\| SOLID \| 1 \| 内部实体不变，只模糊外圈边缘部分。 \| ![image_BlueType_Solid.png](../../../../reference/apis-arkgraphics2d/figures/zh-ch_image_BlueType_Solid.png) \|\| OUTER \| 2 \| 只有外圈边缘模糊，内部实体完全透明。 \| ![image_BlueType_Outer.png](../../../../reference/apis-arkgraphics2d/figures/zh-ch_image_BlueType_Outer.png) \|\| INNER \| 3 \| 只有内部实体模糊，外圈边缘清晰。 \| ![image_BlueType_Inner.png](../../../../reference/apis-arkgraphics2d/figures/zh-ch_image_BlueType_Inner.png) \| |
| [CapStyle](arkts-arkgraphics2d-capstyle-e.md) | 定义线帽样式的枚举，即画笔在绘制线段时，在线段头尾端点的样式。 |
| [ClipOp](arkts-arkgraphics2d-clipop-e.md) | 画布裁剪方式的枚举。 |
| [CornerPos](arkts-arkgraphics2d-cornerpos-e.md) | 圆角位置枚举。 |
| [FilterMode](arkts-arkgraphics2d-filtermode-e.md) | 过滤模式枚举。 |
| [FontEdging](arkts-arkgraphics2d-fontedging-e.md) | 字型边缘效果类型枚举。 |
| [FontHinting](arkts-arkgraphics2d-fonthinting-e.md) | 字型轮廓效果类型枚举。 |
| [FontMetricsFlags](arkts-arkgraphics2d-fontmetricsflags-e.md) | 字体度量标志枚举，指示字体度量中的各字段数据是否有效。 |
| [JoinStyle](arkts-arkgraphics2d-joinstyle-e.md) | 定义线条转角样式的枚举，即画笔在绘制折线段时，在折线转角处的样式。 |
| [PathDashStyle](arkts-arkgraphics2d-pathdashstyle-e.md) | 路径效果的绘制样式枚举。\| 名称 \| 值 \| 说明 \|\| ------ \| - \| ------------------ \|\| TRANSLATE \| 0 \| 不会随着路径旋转，只会平移。 \|\| ROTATE \| 1 \| 随着路径的旋转而旋转。 \|\| MORPH \| 2 \| 随着路径的旋转而旋转，并在转折处进行拉伸或压缩等操作以增加平滑度。 \| |
| [PathDirection](arkts-arkgraphics2d-pathdirection-e.md) | 添加闭合轮廓方向的枚举。 |
| [PathFillType](arkts-arkgraphics2d-pathfilltype-e.md) | 定义路径的填充类型枚举。 |
| [PathIteratorVerb](arkts-arkgraphics2d-pathiteratorverb-e.md) | 迭代器包含的路径操作类型枚举，可用于读取path的操作指令。 |
| [PathMeasureMatrixFlags](arkts-arkgraphics2d-pathmeasurematrixflags-e.md) | 路径测量中的矩阵信息维度枚举，常用于控制物体沿路径移动的动画场景。 |
| [PathOp](arkts-arkgraphics2d-pathop-e.md) | 路径操作类型枚举，可用于合并或裁剪路径等功能。 |
| [PointMode](arkts-arkgraphics2d-pointmode-e.md) | 绘制数组点的方式的枚举。 |
| [RectType](arkts-arkgraphics2d-recttype-e.md) | 定义填充网格的矩形类型的枚举。仅在[Lattice](arkts-graphics-drawing.md)中使用。 |
| [RegionOp](arkts-arkgraphics2d-regionop-e.md) | 两个区域合并时的操作的枚举。 |
| [ScaleToFit](arkts-arkgraphics2d-scaletofit-e.md) | 源矩形到目标矩形的缩放方式枚举。 |
| [ShadowFlag](arkts-arkgraphics2d-shadowflag-e.md) | 控制阴影绘制行为的枚举。 |
| [SrcRectConstraint](arkts-arkgraphics2d-srcrectconstraint-e.md) | 源矩形区域约束类型枚举，用于在画布绘制图像时指定是否将采样范围限制在源矩形区域内。 |
| [TextEncoding](arkts-arkgraphics2d-textencoding-e.md) | 文本的编码类型枚举。 |
| [TileMode](arkts-arkgraphics2d-tilemode-e.md) | 着色器效果平铺模式的枚举。 |
| [VertexMode](arkts-arkgraphics2d-vertexmode-e.md) | 顶点绘制的连接方式枚举。 |

