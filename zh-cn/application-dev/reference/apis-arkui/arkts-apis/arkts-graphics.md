# Graphics

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [borderRadiuses](arkts-arkui-graphics-borderradiuses-f.md#borderradiuses) | 用于生成边框圆角均设置为传入值的边框圆角对象。 |
| [borderStyles](arkts-arkui-graphics-borderstyles-f.md#borderstyles) | 用于生成边框样式均设置为传入值的边框样式对象。 |
| [edgeColors](arkts-arkui-graphics-edgecolors-f.md#edgecolors) | 用于生成边框颜色均设置为传入值的边框颜色对象。 |
| [edgeWidths](arkts-arkui-graphics-edgewidths-f.md#edgewidths) | 用于生成边框宽度均设置为传入值的边框宽度对象。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md) | 用于混合颜色。 |
| [DrawContext](arkts-arkui-graphics-drawcontext-c.md) | 图形绘制上下文，提供绘制所需的画布宽度和高度。 |
| [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | 用于设置长度属性，当长度单位为PERCENT时，值为1表示100%。 |
| [ShapeClip](arkts-arkui-graphics-shapeclip-c.md) | 用于设置图形裁剪。 |
| [ShapeMask](arkts-arkui-graphics-shapemask-c.md) | 用于设置图形遮罩。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ColorMetrics](arkts-arkui-graphics-colormetrics-c-sys.md) | 用于混合颜色。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [BackgroundBlur](arkts-arkui-graphics-backgroundblur-i.md) | 设置背景模糊效果。 |
| [Circle](arkts-arkui-graphics-circle-i.md) | 用于设置圆形的属性。 |
| [CommandPath](arkts-arkui-graphics-commandpath-i.md) | 用于设置路径绘制的指令。 |
| [ContentBlur](arkts-arkui-graphics-contentblur-i.md) | 设置内容模糊效果。 |
| [Corners](arkts-arkui-graphics-corners-i.md) | 用于设置四个角的圆角属性。 |
| [Edges](arkts-arkui-graphics-edges-i.md) | 用于设置边框的属性。 |
| [ForegroundBlur](arkts-arkui-graphics-foregroundblur-i.md) | 设置前景模糊效果。 |
| [Frame](arkts-arkui-graphics-frame-i.md) | 用于设置或返回组件的布局大小和位置。 |
| [RoundRect](arkts-arkui-graphics-roundrect-i.md) | 用于设置带有圆角的矩形。 |
| [Size](arkts-arkui-graphics-size-i.md) | 用于返回组件布局大小的宽和高。默认单位为vp，不同的接口使用Size类型时会再定义单位，以接口定义的单位为准。 |
| [SizeT](arkts-arkui-graphics-sizet-i.md) | 用于设置宽高的属性。 |
| [Vector2](arkts-arkui-graphics-vector2-i.md) | 用于表示包含x和y两个值的向量。 |
| [Vector2T](arkts-arkui-graphics-vector2t-i.md) | 用于表示T类型的包含x和y两个值的向量。 |
| [Vector3](arkts-arkui-graphics-vector3-i.md) | 用于表示包含x、y、z三个值的向量。 |
| [Vector4](arkts-arkui-graphics-vector4-i.md) | 用于表示包含x、y、z、w四个值的向量。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [LengthMetricsUnit](arkts-arkui-graphics-lengthmetricsunit-e.md) | 长度属性单位枚举。 |
| [LengthUnit](arkts-arkui-graphics-lengthunit-e.md) | 长度属性单位枚举。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [BorderRadiuses](arkts-arkui-borderradiuses-t.md) | 设置四个角的圆角半径。 |
| [CornerRadius](arkts-arkui-cornerradius-t.md) | 设置四个角的圆角x轴与y轴的半轴长。 |
| [Matrix4](arkts-arkui-matrix4-t.md) | 设置四阶矩阵。用于设置组件的变换信息，该类型为一个 4x4 矩阵，使用一个长度为16的`number[]`进行表示，各number取值范围：(-∞, +∞)。例如：``` const transform: Matrix4 = [ 1, 0, 45, 0, 0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1 ] ```。 |
| [Offset](arkts-arkui-offset-t.md) | 用于设置组件或效果的偏移。 |
| [Pivot](arkts-arkui-pivot-t.md) | 用于设置组件的轴心坐标，轴心会作为组件的旋转/缩放中心点，影响旋转和缩放效果。轴心的x和y轴坐标为浮点数，默认值为0.5， 取值范围为[0.0, 1.0]。 |
| [Position](arkts-arkui-position-t.md) | 用于设置或返回组件的位置。 |
| [PositionT](arkts-arkui-positiont-t.md) | 用于设置或返回组件的位置。 |
| [Rect](arkts-arkui-rect-t.md) | 用于设置矩形的形状。 |
| [Rotation](arkts-arkui-rotation-t.md) | 用于设置组件的旋转角度。 |
| [Scale](arkts-arkui-scale-t.md) | 用于设置组件的缩放比例。 |
| [Translation](arkts-arkui-translation-t.md) | 用于设置组件的平移量。 |

