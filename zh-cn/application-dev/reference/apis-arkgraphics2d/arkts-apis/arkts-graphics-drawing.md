# @ohos.graphics.drawing

开发者在绘制界面元素时，若ArkUI组件无法满足自定义图形需求，可使用Drawing模块实现灵活的自定义绘制效果。 Drawing模块提供基础的图形绘制能力，包括绘制矩形、圆形、点、直线、自定义Path和字体等。 > **说明：** > > - 本模块使用屏幕物理像素单位px。 > > - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 23

<!--Device-unnamed-declare namespace drawing--><!--Device-unnamed-declare namespace drawing-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [Brush](arkts-arkgraphics2d-drawing-brush-c.md) | 画刷对象，用于设置图形的填充样式，包括颜色、抗锯齿、混合模式、颜色滤波器、蒙版滤波器、着色器效果、阴影层效果及图像滤波器等，并支持获取颜色、透明度、抗锯齿等属性及重置画刷为初始状态。 画刷需通过Canvas的[attachBrush](arkts-arkgraphics2d-drawing-canvas-c.md#attachbrush)方法绑定到画布后生效，绘制完成后通过 [detachBrush](arkts-arkgraphics2d-drawing-canvas-c.md#detachbrush)方法解绑；画刷用于图形填充，画笔（Pen）用于图形描边，详见[Pen](arkts-arkgraphics2d-drawing-pen-c.md)。 |
| [Canvas](arkts-arkgraphics2d-drawing-canvas-c.md) | 承载绘制内容与绘制状态的载体。Canvas提供矩形、圆形、椭圆、弧线、路径、文字、图片等多种图形的绘制能力，支持通过画笔和画刷设置绘制样式，支持画布裁剪、矩阵变换、画布状态保存与恢复等功能。 |
| [ColorFilter](arkts-arkgraphics2d-drawing-colorfilter-c.md) | 颜色滤波器，用于对图像或图形的颜色进行变换和处理，支持创建混合模式颜色滤波器、组合颜色滤波器、矩阵颜色滤波器、伽马颜色空间转换滤波器、亮度颜色滤波器和光照颜色滤波器等多种类型。 |
| [Font](arkts-arkgraphics2d-drawing-font-c.md) | Font类用于描述字型绘制时所使用的属性（如大小、字体、粗细、倾斜、缩放等），并支持文本测量、字形转换、路径轮廓获取、主题字体跟随等能力。 |
| [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) | 图像滤波器，用于对图像应用各种滤波效果，支持创建模糊、颜色混合、级联组合、偏移、基于着色器等多种图像滤波器。 |
| [Lattice](arkts-arkgraphics2d-drawing-lattice-c.md) | 矩形网格对象。该对象用于将图像按照矩形网格进行划分，支持固定指定网格区域、缩放其余网格实现局部拉伸、自定义网格绘制类型、网格颜色填充以及指定绘制边界矩形等能力。创建Lattice对象后，需配合 [Canvas.drawImageLattice](arkts-arkgraphics2d-drawing-canvas-c.md#drawimagelattice)方法使用以实现图像的局部拉伸绘制。 |
| [MaskFilter](arkts-arkgraphics2d-drawing-maskfilter-c.md) | 蒙版滤镜对象，用于对绘制内容施加模糊效果。 |
| [Matrix](arkts-arkgraphics2d-drawing-matrix-c.md) | 矩阵对象，用于图形的坐标变换，支持平移、旋转、缩放和倾斜等变换操作。通过矩阵变换可实现不同坐标系之间的映射。 表示为3×3的矩阵，如下图所示：  矩阵中的元素从左到右，从上到下分别表示水平缩放因子、水平倾斜系数、水平位移系数、垂直倾斜系数、垂直缩放因子、垂直位移系数、x轴透视系数、y轴透视系数、透视缩放因子。 设(x&lt;sub&gt;1&lt;/sub&gt;, y&lt;sub&gt;1&lt;/sub&gt;)为源坐标点，(x&lt;sub&gt;2&lt;/sub&gt;, y&lt;sub&gt;2&lt;/sub&gt;)为源坐标点通过矩阵变换后的坐标点，则两个坐标点的关系如下：  |
| [Path](arkts-arkgraphics2d-drawing-path-c.md) | Path是Drawing模块提供的复合几何路径类，由直线、圆弧、圆锥曲线、二阶贝塞尔、三阶贝塞尔等基本图元组成， 支持路径的构造、变换、布尔运算、SVG路径解析与转换、测量与片段截取等能力。 未设置填充类型时，默认填充类型为WINDING，可通过[setFillType](arkts-arkgraphics2d-drawing-path-c.md#setfilltype)修改。 |
| [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | 路径效果对象，用于创建多种路径效果，包括虚线、圆角、离散、叠加和组合路径效果等。可通过[Pen.setPathEffect](arkts-arkgraphics2d-drawing-pen-c.md#setpatheffect)将其应用到画笔上，从而在绘制路径时改变路 径的渲染样式。 |
| [PathIterator](arkts-arkgraphics2d-drawing-pathiterator-c.md) | 表示路径操作迭代器，可通过遍历迭代器逐段读取路径的操作指令。 迭代器按顺序遍历路径中的操作指令，便于实现对路径的细粒度分析与自定义处理。 |
| [Pen](arkts-arkgraphics2d-drawing-pen-c.md) | 画笔对象，用于描述所绘制图形形状的轮廓信息，支持设置颜色、线宽、抗锯齿、透明度、混合模式、转角样式、线帽样式，以及颜色滤波器、蒙版滤波器、路径效果、着色器、阴影层等绘制效果。 |
| [PointUtils](arkts-arkgraphics2d-drawing-pointutils-c.md) | 本Class是提供处理坐标点的工具类，支持对坐标点进行取反、偏移等操作，适用于需要对坐标点进行变换处理的图形绘制场景。 |
| [RectUtils](arkts-arkgraphics2d-drawing-rectutils-c.md) | 提供处理矩形的工具，支持矩形的快速构建与基本属性获取、边界计算与调整、平移与状态判断、边界规范化等功能。 主要的使用场景： 1. 矩形快速构建与获取基本属性，如构造新矩形、拷贝矩形、获取矩形的宽高以及中心点等。 2. 边界计算与调整，如判断包含关系、计算与更新矩形之间交集和并集，更新边界值等。 3. 矩形平移与状态判断，如对矩形进行平移、将矩形平移到指定位置、判断矩形是否为空以及判断两个矩形是否相等。 4. 矩形边界规范化，如对存在反转情况的矩形边界值进行交换排序等。 |
| [Region](arkts-arkgraphics2d-drawing-region-c.md) | 区域对象，用于描述所绘制图形的区域信息。Region支持设置矩形区域和路径区域，提供区域间的合并运算、相交判断、平移、边界获取等操作。 |
| [RoundRect](arkts-arkgraphics2d-drawing-roundrect-c.md) | 圆角矩形对象。支持设置和获取指定圆角位置的圆角半径，以及对圆角矩形进行平移操作。 |
| [SamplingOptions](arkts-arkgraphics2d-drawing-samplingoptions-c.md) | 采样选项对象，用于配置图像采样时的过滤模式，控制图像缩放或变换过程中的像素采样方式。典型使用场景为在Canvas上绘制图像（如drawImage）时，以不同过滤模式决定图像的采样质量与渲染效果。 |
| [ShaderEffect](arkts-arkgraphics2d-drawing-shadereffect-c.md) | 着色器，用于在绘图中填充颜色和渐变效果。画刷和画笔设置着色器后，会使用着色器效果而不是颜色属性去绘制，但此时画刷和画笔的透明度属性仍然生效。 着色器支持创建单色着色器、线性渐变、径向渐变、扇形渐变、锥形渐变、图片着色器及混合着色器等多种类型。 |
| [ShadowLayer](arkts-arkgraphics2d-drawing-shadowlayer-c.md) | 阴影层对象，通过设置模糊半径、偏移量和颜色，可为图形、文本等绘制内容添加阴影渲染效果。 |
| [TextBlob](arkts-arkgraphics2d-drawing-textblob-c.md) | TextBlob是由一个或多个具有相同字型的字符组成的字块。支持通过文本、字符串、RunBuffer等多种方式创建字形集合，适用于需要批量渲染文本或获取文字边界框的场景。 |
| [Tool](arkts-arkgraphics2d-drawing-tool-c.md) | 本模块定义的工具类，仅提供静态的方法，主要完成其他模块和[common2D](arkts-graphics-common2d.md)中定义的数据结构的转换功能。 |
| [Typeface](arkts-arkgraphics2d-drawing-typeface-c.md) | Typeface类用于表示和管理字体对象。支持的字体操作包括：获取字体族名、从字体文件或rawfile资源构造字体、结合字体属性构造新字体，以及检查字体的加粗、斜体状态等。 |
| [TypefaceArguments](arkts-arkgraphics2d-drawing-typefacearguments-c.md) | 提供字体属性配置的类，用于配置可变字体的属性参数（如字重维度等轴标签及对应属性值）。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [FontFeature](arkts-arkgraphics2d-drawing-fontfeature-i.md) | 表示字体特征。字体特征是字体内置的排版规则，用于控制字形的显示效果，具体包括连字、替代字形、上下标等功能。 |
| [FontMetrics](arkts-arkgraphics2d-drawing-fontmetrics-i.md) | 描述字形大小和布局的属性信息，同一种字体中的字符属性大致相同。 |
| [TextBlobRunBuffer](arkts-arkgraphics2d-drawing-textblobrunbuffer-i.md) | 描述一行文字中具有相同属性的连续字形。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BlendMode](arkts-arkgraphics2d-drawing-blendmode-e.md) | 混合模式枚举。混合模式会将两种颜色（源色、目标色）以特定的方式混合生成一种新的颜色，通常用于叠加、滤镜和遮罩等图形操作场景。 混合操作会分别作用于红、绿、蓝三个颜色通道，采用相同的混合逻辑，而透明度（Alpha通道）则根据各模式的定义另行处理。 为简洁起见，我们使用以下缩写： s : source 源的缩写； d : destination 目标的缩写； sa : source alpha 源透明度的缩写； da : destination alpha 目标透明度的缩写。 计算结果用如下缩写表示： r : 如果4个通道（透明度、红、绿、蓝）的计算方式相同，用r表示。 ra : 如果只操作透明度通道，用ra表示。 rc : 如果操作3个颜色通道，用rc表示。 以黄色矩形为源图像，蓝色圆形为目标图像，各混合模式枚举生成的效果示意图请参考下表。 |
| [BlurType](arkts-arkgraphics2d-drawing-blurtype-e.md) | 定义蒙版滤镜模糊中操作类型的枚举。蒙版用于定义图像的可绘制区域，滤镜用于应用模糊等视觉效果。该枚举控制模糊效果如何应用到蒙版定义的区域内。 \| 名称 \| 值 \| 说明 \| 示意图 \| \| ------ \| - \| ------------------ \| -------- \| \| NORMAL \| 0 \| 全面模糊，外圈和内部实体一起模糊。 \|  \| \| SOLID \| 1 \| 内部实体不变，只模糊外圈边缘部分。 \|  \| \| OUTER \| 2 \| 只有外圈边缘模糊，内部实体完全透明。 \|  \| \| INNER \| 3 \| 只有内部实体模糊，外圈边缘清晰。 \|  \| |
| [CapStyle](arkts-arkgraphics2d-drawing-capstyle-e.md) | 定义线帽样式的枚举，即画笔在绘制线段时，在线段头尾端点的样式。 |
| [ClipOp](arkts-arkgraphics2d-drawing-clipop-e.md) | 画布裁剪方式的枚举。 |
| [CornerPos](arkts-arkgraphics2d-drawing-cornerpos-e.md) | 圆角位置枚举。 |
| [FilterMode](arkts-arkgraphics2d-drawing-filtermode-e.md) | 过滤模式枚举。 |
| [FontEdging](arkts-arkgraphics2d-drawing-fontedging-e.md) | 字型边缘效果类型枚举。 |
| [FontHinting](arkts-arkgraphics2d-drawing-fonthinting-e.md) | 字型轮廓效果类型枚举。 |
| [FontMetricsFlags](arkts-arkgraphics2d-drawing-fontmetricsflags-e.md) | 字体度量标志枚举，指示字体度量中的各字段数据是否有效。常用于精确文本布局、自定义文本渲染等需要获取字体详细度量信息的场景。 |
| [JoinStyle](arkts-arkgraphics2d-drawing-joinstyle-e.md) | 定义线条转角样式的枚举，即画笔在绘制折线段时，在折线转角处的样式。 |
| [PathDashStyle](arkts-arkgraphics2d-drawing-pathdashstyle-e.md) | 路径效果的绘制样式枚举。 \| 名称 \| 值 \| 说明 \| \| ------ \| - \| ------------------ \| \| TRANSLATE \| 0 \| 不会随着路径旋转，只会平移。 \| \| ROTATE \| 1 \| 随着路径的旋转而旋转。 \| \| MORPH \| 2 \| 随着路径的旋转而旋转，并在转折处进行拉伸或压缩等操作以增加平滑度。 \| |
| [PathDirection](arkts-arkgraphics2d-drawing-pathdirection-e.md) | 添加闭合轮廓方向的枚举。 |
| [PathFillType](arkts-arkgraphics2d-drawing-pathfilltype-e.md) | 定义路径的填充类型枚举。 |
| [PathIteratorVerb](arkts-arkgraphics2d-drawing-pathiteratorverb-e.md) | 迭代器包含的路径操作类型枚举，可用于读取path的操作指令。常用于路径分析、路径转换、路径动画等需要解析路径构成的场景。 |
| [PathMeasureMatrixFlags](arkts-arkgraphics2d-drawing-pathmeasurematrixflags-e.md) | 路径测量中的矩阵信息维度枚举，常用于控制物体沿路径移动的动画场景。位置矩阵包含路径上某点的坐标平移信息； 切线矩阵包含路径上某点切线方向的旋转变换信息；位置和切线矩阵同时包含位置和切线信息，提供完整的路径几何信息。 |
| [PathOp](arkts-arkgraphics2d-drawing-pathop-e.md) | 路径操作类型枚举，可用于合并或裁剪路径等功能。 |
| [PointMode](arkts-arkgraphics2d-drawing-pointmode-e.md) | 绘制点数组的方式的枚举。 |
| [RectType](arkts-arkgraphics2d-drawing-recttype-e.md) | 定义填充网格的矩形类型的枚举，用于在图像分割绘制时指定各个矩形区域的填充方式。仅在[Lattice](arkts-arkgraphics2d-drawing-lattice-c.md)中使用。 |
| [RegionOp](arkts-arkgraphics2d-drawing-regionop-e.md) | 两个区域合并时的操作的枚举。常用于图形编辑、裁剪区域计算等需要组合多个区域的场景。 |
| [ScaleToFit](arkts-arkgraphics2d-drawing-scaletofit-e.md) | 源矩形到目标矩形的缩放方式枚举。 |
| [ShadowFlag](arkts-arkgraphics2d-drawing-shadowflag-e.md) | 控制阴影绘制行为的枚举。 |
| [SrcRectConstraint](arkts-arkgraphics2d-drawing-srcrectconstraint-e.md) | 源矩形区域约束类型枚举，用于在画布绘制图像时指定是否将采样范围（图像像素读取范围）限制在源矩形区域内。 |
| [TextEncoding](arkts-arkgraphics2d-drawing-textencoding-e.md) | 文本的编码类型枚举。 |
| [TileMode](arkts-arkgraphics2d-drawing-tilemode-e.md) | 着色器效果平铺模式的枚举。 |
| [VertexMode](arkts-arkgraphics2d-drawing-vertexmode-e.md) | 顶点绘制的连接方式枚举。 |

