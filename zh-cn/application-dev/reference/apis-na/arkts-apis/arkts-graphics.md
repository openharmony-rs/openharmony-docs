# Graphics

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [borderRadiuses](arkts-na-graphics-borderradiuses-f.md) | 获取所有边都设置为相同半径的BorderRadiuses对象。 |
| [borderStyles](arkts-na-graphics-borderstyles-f.md) |  |
| [edgeColors](arkts-na-graphics-edgecolors-f.md) |  |
| [edgeWidths](arkts-na-graphics-edgewidths-f.md) |  |

### 类

| 名称 | 说明 |
| --- | --- |
| [ColorMetrics](arkts-na-graphics-colormetrics-c.md) | 用于混合颜色。 |
| [DrawContext](arkts-na-graphics-drawcontext-c.md) | 图形绘制上下文，提供绘制所需的画布宽度和高度。 |
| [LengthMetrics](arkts-na-graphics-lengthmetrics-c.md) | 用于设置长度属性，当长度单位为PERCENT时，值为1表示100%。 |
| [ShapeClip](arkts-na-graphics-shapeclip-c.md) | 用于设置图形裁剪。 |
| [ShapeMask](arkts-na-graphics-shapemask-c.md) | 用于设置图形遮罩。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ColorMetrics](arkts-na-graphics-colormetrics-c-sys.md) | 用于混合颜色。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [BackgroundBlur](arkts-na-graphics-backgroundblur-i.md) | 设置背景模糊效果。 .0.0 .0.0 |
| [Circle](arkts-na-graphics-circle-i.md) | 用于设置圆形的属性。 |
| [CommandPath](arkts-na-graphics-commandpath-i.md) | 用于设置路径绘制的指令。 |
| [ContentBlur](arkts-na-graphics-contentblur-i.md) | 设置内容模糊效果。 .0.0 .0.0 |
| [Corners](arkts-na-graphics-corners-i.md) | 用于设置四个角的圆角属性。 |
| [ForegroundBlur](arkts-na-graphics-foregroundblur-i.md) | 设置前景模糊效果。 .0.0 .0.0 |
| [Frame](arkts-na-graphics-frame-i.md) | 用于设置或返回组件的布局大小和位置。 |
| [NodeEdges](arkts-na-graphics-nodeedges-i.md) | 用于设置边框的属性，属性包括边框风格、边框颜色、边框宽度、边框长度等。 |
| [RoundRect](arkts-na-graphics-roundrect-i.md) | 用于设置带有圆角的矩形。 |
| [Size](arkts-na-graphics-size-i.md) | 用于返回组件布局大小的宽和高。默认单位为vp，不同的接口使用Size类型时会再定义单位，以接口定义的单位为准。 |
| [SizeT](arkts-na-graphics-sizet-i.md) | 用于设置宽高的属性。 |
| [Vector2](arkts-na-graphics-vector2-i.md) | 用于表示包含x和y两个值的向量。 |
| [Vector2T](arkts-na-graphics-vector2t-i.md) | 用于表示T类型的包含x和y两个值的向量。 |
| [Vector3](arkts-na-graphics-vector3-i.md) | 用于表示包含x、y、z三个值的向量。 |
| [Vector4](arkts-na-graphics-vector4-i.md) | 用于表示包含x、y、z、w四个值的向量。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [LengthMetricsUnit](arkts-na-graphics-lengthmetricsunit-e.md) | 长度属性单位枚举。 |
| [LengthUnit](arkts-na-graphics-lengthunit-e.md) | 长度属性单位枚举。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [CornerRadius](arkts-na-cornerradius-t.md) | 设置四个角的圆角x轴与y轴的半轴长。 |
| [Matrix4](arkts-na-matrix4-t.md) | 设置四阶矩阵。 用于设置组件的变换信息，该类型为一个 4x4 矩阵，使用一个长度为16的`number[]`进行表示，各number取值范围：(-∞, +∞)。例如： ``` const transform: Matrix4 = [ 1, 0, 45, 0, 0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1 ] ```。 |
| [NodeBorderRadiuses](arkts-na-nodeborderradiuses-t.md) | 设置四个角的圆角度数。 |
| [NodeOffset](arkts-na-nodeoffset-t.md) | 用于设置组件或效果的偏移。 |
| [NodePosition](arkts-na-nodeposition-t.md) | 用于设置或返回组件的位置。 |
| [Pivot](arkts-na-pivot-t.md) | 用于设置组件的轴心坐标，轴心会作为组件的旋转/缩放中心点，影响旋转和缩放效果。轴心的x和y轴坐标为浮点数，默认值为0.5， 取值范围为[0.0, 1.0]。 |
| [PositionT](arkts-na-positiont-t.md) | 用于设置或返回组件的位置。 |
| [Rect](arkts-na-rect-t.md) | 用于设置矩形的形状。 |
| [Rotation](arkts-na-rotation-t.md) | 用于设置组件的旋转角度。 |
| [Scale](arkts-na-scale-t.md) | 用于设置组件的缩放比例。 |
| [Translation](arkts-na-translation-t.md) | 用于设置组件的平移量。 |

