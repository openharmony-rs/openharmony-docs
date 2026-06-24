# Graphics

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [borderRadiuses](arkts-arkui-graphics-borderradiuses-f.md#borderRadiuses-1) | 用于生成边框圆角均设置为传入值的边框圆角对象。<br/> |
| [borderStyles](arkts-arkui-graphics-borderstyles-f.md#borderStyles-1) | 用于生成边框样式均设置为传入值的边框样式对象。<br/> |
| [edgeColors](arkts-arkui-graphics-edgecolors-f.md#edgeColors-1) | 用于生成边框颜色均设置为传入值的边框颜色对象。<br/> |
| [edgeWidths](arkts-arkui-graphics-edgewidths-f.md#edgeWidths-1) | 用于生成边框宽度均设置为传入值的边框宽度对象。<br/> |

### 类

| 名称 | 说明 |
| --- | --- |
| [ColorMetrics](arkts-arkui-colormetrics-c.md) | 用于混合颜色。<br/> |
| <!--DelRow-->[ColorMetrics](arkts-arkui-colormetrics-c-sys.md) | 用于混合颜色。<br/> |
| [DrawContext](arkts-arkui-drawcontext-c.md) | 图形绘制上下文，提供绘制所需的画布宽度和高度。<br/> |
| [LengthMetrics](arkts-arkui-lengthmetrics-c.md) | 用于设置长度属性，当长度单位为PERCENT时，值为1表示100%。<br/> |
| [ShapeClip](arkts-arkui-shapeclip-c.md) | 用于设置图形裁剪。<br/> |
| [ShapeMask](arkts-arkui-shapemask-c.md) | 用于设置图形遮罩。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [BackgroundBlur](arkts-arkui-backgroundblur-i.md) | 设置背景模糊效果。<br/> |
| [Circle](arkts-arkui-circle-i.md) | 用于设置圆形的属性。<br/> |
| [CommandPath](arkts-arkui-commandpath-i.md) | 用于设置路径绘制的指令。<br/> |
| [ContentBlur](arkts-arkui-contentblur-i.md) | 设置内容模糊效果。<br/> |
| [Corners](arkts-arkui-corners-i.md) | 用于设置四个角的圆角属性。<br/> |
| [Edges](arkts-arkui-edges-i.md) | 用于设置边框的属性。<br/> |
| [ForegroundBlur](arkts-arkui-foregroundblur-i.md) | 设置前景模糊效果。<br/> |
| [Frame](arkts-arkui-frame-i.md) | 用于设置或返回组件的布局大小和位置。<br/> |
| [RoundRect](arkts-arkui-roundrect-i.md) | 用于设置带有圆角的矩形。<br/> |
| [Size](arkts-arkui-size-i.md) | 用于返回组件布局大小的宽和高。默认单位为vp，不同的接口使用Size类型时会再定义单位，以接口定义的单位为准。<br/> |
| [SizeT](arkts-arkui-sizet-i.md) | 用于设置宽高的属性。<br/> |
| [Vector2](arkts-arkui-vector2-i.md) | 用于表示包含x和y两个值的向量。<br/> |
| [Vector2T](arkts-arkui-vector2t-i.md) | 用于表示T类型的包含x和y两个值的向量。<br/> |
| [Vector3](arkts-arkui-vector3-i.md) | 用于表示包含x、y、z三个值的向量。<br/> |
| [Vector4](arkts-arkui-vector4-i.md) | 用于表示包含x、y、z、w四个值的向量。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [LengthMetricsUnit](arkts-arkui-lengthmetricsunit-e.md) | 长度属性单位枚举。<br/> |
| [LengthUnit](arkts-arkui-lengthunit-e.md) | 长度属性单位枚举。<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |
| [BorderRadiuses](arkts-arkui-borderradiuses-t.md) | 设置四个角的圆角半径。<br/> |
| [CornerRadius](arkts-arkui-cornerradius-t.md) | 设置四个角的圆角x轴与y轴的半轴长。<br/> |
| [Matrix4](arkts-arkui-matrix4-t.md) | 设置四阶矩阵。<br/>用于设置组件的变换信息，该类型为一个 4x4 矩阵，使用一个长度为16的`number[]`进行表示，例如：<br/>```<br/>const transform: Matrix4 = [<br/>1, 0, 45, 0,<br/>0, 1,  0, 0,<br/>0, 0,  1, 0,<br/>0, 0,  0, 1<br/>]<br/>```。<br/> |
| [Offset](arkts-arkui-offset-t.md) | 用于设置组件或效果的偏移。<br/> |
| [Pivot](arkts-arkui-pivot-t.md) | 用于设置组件的轴心坐标，轴心会作为组件的旋转/缩放中心点，影响旋转和缩放效果。<br/> |
| [Position](arkts-arkui-position-t.md) | 用于设置或返回组件的位置。<br/> |
| [PositionT](arkts-arkui-positiont-t.md) | 用于设置或返回组件的位置。<br/> |
| [Rect](arkts-arkui-rect-t.md) | 用于设置矩形的形状。<br/> |
| [Rotation](arkts-arkui-rotation-t.md) | 用于设置组件的旋转角度。<br/> |
| [Scale](arkts-arkui-scale-t.md) | 用于设置组件的缩放比例。<br/> |
| [Translation](arkts-arkui-translation-t.md) | 用于设置组件的平移量。<br/> |

