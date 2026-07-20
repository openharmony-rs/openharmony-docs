# Path

由直线、圆弧、二阶贝塞尔、三阶贝塞尔组成的复合几何路径。

> **说明：**  
>  
> - 本模块使用屏幕物理像素单位px。  
>  
> - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 11

<!--Device-drawing-class Path--><!--Device-drawing-class Path-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

<a id="addarc"></a>
## addArc

```TypeScript
addArc(rect: common2D.Rect, startAngle: number, sweepAngle: number): void
```

向路径添加一段圆弧。当startAngle和sweepAngle同时满足以下两种情况时，添加整个椭圆而不是圆弧：1.startAngle对90取余接近于0；2.sweepAngle不在(-360, 360)区间内。其余情况sweepAngle会对360取余后添加圆弧。

**起始版本：** 12

<!--Device-Path-addArc(rect: common2D.Rect, startAngle: double, sweepAngle: double): void--><!--Device-Path-addArc(rect: common2D.Rect, startAngle: double, sweepAngle: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | common2D.Rect | 是 | 包含弧的椭圆的矩形边界。 |
| startAngle | number | 是 | 弧的起始角度，单位为度，0度为x轴正方向，该参数为浮点数。 |
| sweepAngle | number | 是 | 扫描角度，单位为度。正数表示顺时针方向，负数表示逆时针方向，该参数为浮点数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

<a id="addcircle"></a>
## addCircle

```TypeScript
addCircle(x: number, y: number, radius: number, pathDirection?: PathDirection): void
```

按指定方向，向路径添加圆形，圆的起点位于(x + radius, y)。

**起始版本：** 12

<!--Device-Path-addCircle(x: double, y: double, radius: double, pathDirection?: PathDirection): void--><!--Device-Path-addCircle(x: double, y: double, radius: double, pathDirection?: PathDirection): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 表示圆心的x轴坐标，该参数为浮点数。 |
| y | number | 是 | 表示圆心的y轴坐标，该参数为浮点数。 |
| radius | number | 是 | 表示圆形的半径，该参数为浮点数，小于等于0时不会有任何效果。 |
| pathDirection | [PathDirection](arkts-arkgraphics2d-drawing-pathdirection-e.md) | 否 | 表示路径方向，默认为顺时针方向。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

<a id="addoval"></a>
## addOval

```TypeScript
addOval(rect: common2D.Rect, start: number, pathDirection?: PathDirection): void
```

按指定方向，将矩形的内切椭圆添加到路径中。

**起始版本：** 12

<!--Device-Path-addOval(rect: common2D.Rect, start: int, pathDirection?: PathDirection): void--><!--Device-Path-addOval(rect: common2D.Rect, start: int, pathDirection?: PathDirection): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | common2D.Rect | 是 | 椭圆的矩形边界。 |
| start | number | 是 | 表示椭圆初始点的索引，0，1，2，3分别对应椭圆的上端点，右端点，下端点，左端点，该参数为不小于0的整数，大于等于4时会对4取余。 |
| pathDirection | [PathDirection](arkts-arkgraphics2d-drawing-pathdirection-e.md) | 否 | 表示路径方向，默认为顺时针方向。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

<a id="addpath"></a>
## addPath

```TypeScript
addPath(path: Path, matrix?: Matrix | null): void
```

对源路径进行矩阵变换后，将其添加到当前路径中。

**起始版本：** 12

<!--Device-Path-addPath(path: Path, matrix?: Matrix | null): void--><!--Device-Path-addPath(path: Path, matrix?: Matrix | null): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | [Path](arkts-arkgraphics2d-drawing-path-c.md) | 是 | 表示源路径对象。 |
| matrix | [Matrix](arkts-arkgraphics2d-drawing-matrix-c.md) \| null | 否 | 表示矩阵对象，默认为单位矩阵。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

<a id="addpolygon"></a>
## addPolygon

```TypeScript
addPolygon(points: Array<common2D.Point>, close: boolean): void
```

通过坐标点列表添加多条连续的线段。

**起始版本：** 12

<!--Device-Path-addPolygon(points: Array<common2D.Point>, close: boolean): void--><!--Device-Path-addPolygon(points: Array<common2D.Point>, close: boolean): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| points | Array&lt;common2D.Point&gt; | 是 | 坐标点数组。 |
| close | boolean | 是 | 表示是否将路径闭合，即是否添加路径起始点到终点的连线。true表示将路径闭合，false表示不将路径闭合。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

<a id="addrect"></a>
## addRect

```TypeScript
addRect(rect: common2D.Rect, pathDirection?: PathDirection): void
```

按指定方向，将矩形添加到路径中，添加的路径的起始点为矩形左上角。

**起始版本：** 12

<!--Device-Path-addRect(rect: common2D.Rect, pathDirection?: PathDirection): void--><!--Device-Path-addRect(rect: common2D.Rect, pathDirection?: PathDirection): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | common2D.Rect | 是 | 向路径中添加的矩形轮廓。 |
| pathDirection | [PathDirection](arkts-arkgraphics2d-drawing-pathdirection-e.md) | 否 | 表示路径方向，默认为顺时针方向。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

<a id="addroundrect"></a>
## addRoundRect

```TypeScript
addRoundRect(roundRect: RoundRect, pathDirection?: PathDirection): void
```

按指定方向，向路径添加圆角矩形轮廓。路径添加方向为顺时针时，起始点位于圆角矩形左下方圆角与左边界的交点；路径添加方向为逆时针时，起始点位于圆角矩形左上方圆角与左边界的交点。

**起始版本：** 12

<!--Device-Path-addRoundRect(roundRect: RoundRect, pathDirection?: PathDirection): void--><!--Device-Path-addRoundRect(roundRect: RoundRect, pathDirection?: PathDirection): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| roundRect | [RoundRect](arkts-arkgraphics2d-drawing-roundrect-c.md) | 是 | 圆角矩形对象。 |
| pathDirection | [PathDirection](arkts-arkgraphics2d-drawing-pathdirection-e.md) | 否 | 表示路径方向，默认为顺时针方向。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

<a id="approximate"></a>
## approximate

```TypeScript
approximate(acceptableError: number): Array<number>
```

将当前路径转化为由连续直线段构成的近似路径。

> **说明：**  
>  
> - 当acceptableError为0时，曲线路径被极度细分，会严重影响性能和内存消耗，不建议设置误差值为0。  
>  
> - 当acceptableError特别大时，路径会极度简化，保留少量关键点，可能会丢失原有形状。  
>  
> - 对于椭圆等曲线，当acceptableError过大时，拟合结果通常只包含椭圆的分段贝塞尔曲线的起止点，椭圆形会被极度简化为多边形。

**起始版本：** 20

<!--Device-Path-approximate(acceptableError: number): Array<number>--><!--Device-Path-approximate(acceptableError: number): Array<number>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| acceptableError | number | 是 | 表示路径上每条线段的可接受误差。该参数为浮点数，不应小于0，当参数小于0时报错。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;number&gt; | 返回包含近似路径的点的数组，至少包含两个点。每个点由三个值组成：<br>1. 该点所在的位置距离路径起点的长度比例值，范围为[0.0, 1.0]。<br>2. 点的x坐标。<br>3. 点的y坐标。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-参数值异常) | Parameter error. Possible causes: Incorrect parameter range. |

<a id="arcto"></a>
## arcTo

```TypeScript
arcTo(x1: number, y1: number, x2: number, y2: number, startDeg: number, sweepDeg: number): void
```

给路径添加一段弧线，绘制弧线的方式为角度弧，该方式首先会指定一个矩形边框，取其内切椭圆，然后会指定一个起始角度和扫描度数，从起始角度扫描截取的椭圆周长一部分即为绘制的弧线。另外会默认添加一条从路径的最后点位置到弧线起始点位置的线段。

**起始版本：** 11

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Path-arcTo(x1: double, y1: double, x2: double, y2: double, startDeg: double, sweepDeg: double): void--><!--Device-Path-arcTo(x1: double, y1: double, x2: double, y2: double, startDeg: double, sweepDeg: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x1 | number | 是 | 矩形左上角的x坐标，该参数为浮点数。 |
| y1 | number | 是 | 矩形左上角的y坐标，该参数为浮点数。 |
| x2 | number | 是 | 矩形右下角的x坐标，该参数为浮点数。 |
| y2 | number | 是 | 矩形右下角的y坐标，该参数为浮点数。 |
| startDeg | number | 是 | 起始的角度。角度的起始方向（0°）为x轴正方向。 |
| sweepDeg | number | 是 | 扫描的度数，为正数时顺时针扫描，为负数时逆时针扫描。实际扫描的度数为该入参对360取模的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

<a id="buildfromsvgstring"></a>
## buildFromSvgString

```TypeScript
buildFromSvgString(str: string): boolean
```

解析SVG字符串表示的路径。

**起始版本：** 12

<!--Device-Path-buildFromSvgString(str: string): boolean--><!--Device-Path-buildFromSvgString(str: string): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| str | string | 是 | SVG格式的字符串，用于描述绘制路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回是否成功解析SVG字符串的结果。true表示解析成功，false表示解析失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

<a id="close"></a>
## close

```TypeScript
close(): void
```

闭合路径，会添加一条从路径起点位置到最后点位置的线段。

**起始版本：** 11

<!--Device-Path-close(): void--><!--Device-Path-close(): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

<a id="conicto"></a>
## conicTo

```TypeScript
conicTo(ctrlX: number, ctrlY: number, endX: number, endY: number, weight: number): void
```

在当前路径上添加一条路径最后点位置（若路径没有内容则默认为 (0, 0)）到目标点位置的圆锥曲线，其控制点为 (ctrlX, ctrlY)，结束点为 (endX, endY)。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Path-conicTo(ctrlX: double, ctrlY: double, endX: double, endY: double, weight: double): void--><!--Device-Path-conicTo(ctrlX: double, ctrlY: double, endX: double, endY: double, weight: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ctrlX | number | 是 | 控制点的x坐标，该参数为浮点数。 |
| ctrlY | number | 是 | 控制点的y坐标，该参数为浮点数。 |
| endX | number | 是 | 目标点的x坐标，该参数为浮点数。 |
| endY | number | 是 | 目标点的y坐标，该参数为浮点数。 |
| weight | number | 是 | 表示曲线权重，决定了曲线的形状。值越大，曲线越接近控制点。小于等于0时，效果与[lineTo](arkts-arkgraphics2d-drawing-path-c.md#lineto-1)相同；值为1时，效果与[quadTo](arkts-arkgraphics2d-drawing-path-c.md#quadto-1)相同。该参数为浮点数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

构造一个路径。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Path-constructor()--><!--Device-Path-constructor()-End-->

**系统能力：** SystemCapability.Graphics.Drawing

<a id="constructor-1"></a>
## constructor

```TypeScript
constructor(path: Path)
```

构造一个已有路径的副本。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Path-constructor(path: Path)--><!--Device-Path-constructor(path: Path)-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | [Path](arkts-arkgraphics2d-drawing-path-c.md) | 是 | 待复制的路径对象。 |

<a id="contains"></a>
## contains

```TypeScript
contains(x: number, y: number): boolean
```

判断指定坐标点是否被路径包含，判定是否被路径包含的规则参考[PathFillType](arkts-arkgraphics2d-drawing-pathfilltype-e.md)。

**起始版本：** 12

<!--Device-Path-contains(x: double, y: double): boolean--><!--Device-Path-contains(x: double, y: double): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | x轴上坐标点，该参数必须为浮点数。 |
| y | number | 是 | y轴上坐标点，该参数必须为浮点数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回指定坐标点是否在路径内。true表示点在路径内，false表示点不在路径内。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

<a id="converttosvgstring"></a>
## convertToSvgString

```TypeScript
convertToSvgString(): string
```

将路径转换为SVG字符串。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Path-convertToSvgString(): string--><!--Device-Path-convertToSvgString(): string-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 转换后的SVG字符串结果。 |

<a id="cubicto"></a>
## cubicTo

```TypeScript
cubicTo(ctrlX1: number, ctrlY1: number, ctrlX2: number, ctrlY2: number, endX: number, endY: number): void
```

添加一条从路径最后点位置（若路径没有内容则默认为 (0, 0)）到目标点位置的三阶贝塞尔圆滑曲线。

**起始版本：** 11

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Path-cubicTo(ctrlX1: double, ctrlY1: double, ctrlX2: double, ctrlY2: double, endX: double, endY: double): void--><!--Device-Path-cubicTo(ctrlX1: double, ctrlY1: double, ctrlX2: double, ctrlY2: double, endX: double, endY: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ctrlX1 | number | 是 | 第一个控制点的x坐标，该参数为浮点数。 |
| ctrlY1 | number | 是 | 第一个控制点的y坐标，该参数为浮点数。 |
| ctrlX2 | number | 是 | 第二个控制点的x坐标，该参数为浮点数。 |
| ctrlY2 | number | 是 | 第二个控制点的y坐标，该参数为浮点数。 |
| endX | number | 是 | 目标点的x坐标，该参数为浮点数。 |
| endY | number | 是 | 目标点的y坐标，该参数为浮点数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

<a id="getbounds"></a>
## getBounds

```TypeScript
getBounds(): common2D.Rect
```

获取包含路径的最小矩形边界。

**起始版本：** 12

<!--Device-Path-getBounds(): common2D.Rect--><!--Device-Path-getBounds(): common2D.Rect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| common2D.Rect | Minimum bounding rectangle. |

<a id="getconicweightdata"></a>
## getConicWeightData

```TypeScript
getConicWeightData(): Array<number>
```

获取路径的圆锥曲线权重数据。在路径（path）图元中，圆锥曲线数据采用有理贝塞尔曲线（Rational Bézier Curve）形式表示，其中每个控制点附带一个权重值（weight）。权重属于曲线定义的几何参数。主要作用如下：形状调控：权重值越大，曲线越靠近对应控制点；权重为1时退化为标准贝塞尔曲线；权重为0时该控制点不起作用。精确表示圆锥曲线：通过组合权重与二次贝塞尔曲线，可以精确表示圆弧、椭圆弧、抛物线等圆锥曲线段，无需使用分段逼近或专用椭圆弧指令。数据组织：权重通常以数组形式与点数据并列，按顺序对应每个控制点，与相应的指令verb（如[conicTo](arkts-arkgraphics2d-drawing-path-c.md#conicto-1)）配合使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Path-getConicWeightData(): Array<double>--><!--Device-Path-getConicWeightData(): Array<double>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;number&gt; | 类型为浮点数（取值范围为非负数）。取值为0.0时，该控制点完全无效，曲线不经过此点，曲线实际由其余控制点定义。取值为1.0时，该控制点对应的曲线变为标准贝塞尔曲线，此时权重不产生额外形变效果。取值大于1时，权重值越大，曲线越靠近该控制点；小于1.0但大于0.0时，曲线则相对远离该控制点。 |

<a id="getfilltype"></a>
## getFillType

```TypeScript
getFillType(): PathFillType
```

获取路径的填充类型。

**起始版本：** 20

<!--Device-Path-getFillType(): PathFillType--><!--Device-Path-getFillType(): PathFillType-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PathFillType](arkts-arkgraphics2d-drawing-pathfilltype-e.md) | 路径填充类型。 |

<a id="getlastpoint"></a>
## getLastPoint

```TypeScript
getLastPoint(): common2D.Point
```

获取路径的最后一个点坐标。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Path-getLastPoint(): common2D.Point--><!--Device-Path-getLastPoint(): common2D.Point-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| common2D.Point | Returns the last point of the path. |

<a id="getlength"></a>
## getLength

```TypeScript
getLength(forceClosed: boolean): number
```

获取路径长度。

**起始版本：** 12

<!--Device-Path-getLength(forceClosed: boolean): double--><!--Device-Path-getLength(forceClosed: boolean): double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| forceClosed | boolean | 是 | 表示是否按照闭合路径测量，true表示测量时路径会被强制视为已闭合，false表示会根据路径的实际闭合状态测量。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 路径长度。 |

<a id="getmatrix"></a>
## getMatrix

```TypeScript
getMatrix(forceClosed: boolean, distance: number, matrix: Matrix, flags: PathMeasureMatrixFlags): boolean
```

在路径上的某个位置，获取一个变换矩阵，用于表示该点的坐标和朝向。

**起始版本：** 12

<!--Device-Path-getMatrix(forceClosed: boolean, distance: double, matrix: Matrix, flags: PathMeasureMatrixFlags): boolean--><!--Device-Path-getMatrix(forceClosed: boolean, distance: double, matrix: Matrix, flags: PathMeasureMatrixFlags): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| forceClosed | boolean | 是 | 表示是否按照闭合路径测量，true表示测量时路径会被强制视为已闭合，false表示会根据路径的实际闭合状态测量。 |
| distance | number | 是 | 表示与路径起始点的距离，小于0时会被视作0，大于路径长度时会被视作路径长度。该参数为浮点数。 |
| matrix | [Matrix](arkts-arkgraphics2d-drawing-matrix-c.md) | 是 | 矩阵对象，用于存储得到的矩阵。 |
| flags | [PathMeasureMatrixFlags](arkts-arkgraphics2d-drawing-pathmeasurematrixflags-e.md) | 是 | 矩阵信息维度枚举。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回是否成功获取变换矩阵的结果。true表示成功，false表示失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

<a id="getpathiterator"></a>
## getPathIterator

```TypeScript
getPathIterator(): PathIterator
```

返回该路径的操作迭代器。

**起始版本：** 18

<!--Device-Path-getPathIterator(): PathIterator--><!--Device-Path-getPathIterator(): PathIterator-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PathIterator](arkts-arkgraphics2d-drawing-pathiterator-c.md) | 该路径的迭代器对象。 |

<a id="getpointdata"></a>
## getPointData

```TypeScript
getPointData(): Array<common2D.Point>
```

获取路径的点数据。在路径（path）图元中，点数据以数值序列的形式存在，与动词verb指令一一对应，用来精确指定绘图操作的几何坐标位置。点数据的主要类型包括：终点坐标：与[moveTo](arkts-arkgraphics2d-drawing-path-c.md#moveto-1)、[lineTo](arkts-arkgraphics2d-drawing-path-c.md#lineto-1)等指令配合，定义线段或移动的目标位置。控制点坐标：与曲线指令配合，用于定义贝塞尔曲线的形状（如三次曲线需要两个控制点和一个终点）。闭合点：通常不单独提供坐标，由[close](arkts-arkgraphics2d-drawing-path-c.md#close-1)指令隐式使用路径起点。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Path-getPointData(): Array<common2D.Point>--><!--Device-Path-getPointData(): Array<common2D.Point>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;common2D.Point&gt; | path points array. |

<a id="getpositionandtangent"></a>
## getPositionAndTangent

```TypeScript
getPositionAndTangent(forceClosed: boolean, distance: number, position: common2D.Point, tangent: common2D.Point): boolean
```

获取路径起始点指定距离处的坐标点和切线值。

**起始版本：** 12

<!--Device-Path-getPositionAndTangent(forceClosed: boolean, distance: double, position: common2D.Point, tangent: common2D.Point): boolean--><!--Device-Path-getPositionAndTangent(forceClosed: boolean, distance: double, position: common2D.Point, tangent: common2D.Point): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| forceClosed | boolean | 是 | 表示是否按照闭合路径测量，true表示测量时路径会被强制视为已闭合，false表示会根据路径的实际闭合状态测量。 |
| distance | number | 是 | 表示与路径起始点的距离，小于0时会被视作0，大于路径长度时会被视作路径长度。该参数为浮点数。 |
| position | common2D.Point | 是 | 存储获取到的距离路径起始点distance处的点的坐标。 |
| tangent | common2D.Point | 是 | 存储获取到的距离路径起始点distance处的点的切线值，tangent.x表示该点切线的余弦值，tangent.y表示该点切线的正弦值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示是否成功获取距离路径起始点distance处的点的坐标和正切值的结果。true表示获取成功，false表示获取失败，position和tangent不会被改变。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

<a id="getsegment"></a>
## getSegment

```TypeScript
getSegment(forceClosed: boolean, start: number, stop: number, startWithMoveTo: boolean, dst: Path): boolean
```

截取路径的片段并追加到目标路径上。

**起始版本：** 18

<!--Device-Path-getSegment(forceClosed: boolean, start: double, stop: double, startWithMoveTo: boolean, dst: Path): boolean--><!--Device-Path-getSegment(forceClosed: boolean, start: double, stop: double, startWithMoveTo: boolean, dst: Path): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| forceClosed | boolean | 是 | 表示是否按照闭合路径测量，true表示测量时路径会被强制视为已闭合，false表示会根据路径的实际闭合状态测量。 |
| start | number | 是 | 表示与路径起始点的距离，距离路径起始点start距离的位置即为截取路径片段的起始点，小于0时会被视作0，大于等于stop时会截取失败。该参数为浮点数。 |
| stop | number | 是 | 表示与路径起始点的距离，距离路径起始点stop距离的位置即为截取路径片段的终点，小于等于start时会截取失败，大于路径长度时会被视作路径长度。该参数为浮点数。 |
| startWithMoveTo | boolean | 是 | 表示是否在目标路径执行[moveTo](arkts-arkgraphics2d-drawing-path-c.md#moveto-1)移动到截取路径片段的起始点位置。true表示执行，false表示不执行。 |
| dst | [Path](arkts-arkgraphics2d-drawing-path-c.md) | 是 | 目标路径，截取成功时会将得到的路径片段追加到目标路径上，截取失败时不做改变。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示是否成功截取路径片段。true表示截取成功，false表示截取失败。 |

<a id="getverbdata"></a>
## getVerbData

```TypeScript
getVerbData(): Array<PathIteratorVerb>
```

获取路径的指令数据。在路径（path）图元中，指令数据verb用于描述路径构造过程中的基本绘图动作。指令数据以枚举的形式存在，每个取值对应一种几何操作类型，例如：[moveTo](arkts-arkgraphics2d-drawing-path-c.md#moveto-1)：将当前绘图点移至指定坐标，不产生线段。[lineTo](arkts-arkgraphics2d-drawing-path-c.md#lineto-1)：从当前点向指定点绘制直线段。[close](arkts-arkgraphics2d-drawing-path-c.md#close-1)：将当前点与路径起点相连，形成封闭区域。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Path-getVerbData(): Array<PathIteratorVerb>--><!--Device-Path-getVerbData(): Array<PathIteratorVerb>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;PathIteratorVerb&gt; | 类型为浮点数。理论上取值范围为全体实数，但实际受限于渲染坐标系的有效范围（如-2^31到2^31-1或屏幕可见区域）；超出范围可能导致图形不可见或裁剪。 |

<a id="interpolate"></a>
## interpolate

```TypeScript
interpolate(other: Path, weight: number, interpolatedPath: Path): boolean
```

根据给定的权重，在当前路径和另一条路径之间进行插值，并将结果存储在目标路径对象中。两条路径点数相同即可插值成功，目标路径按照当前路径的结构进行创建。

**起始版本：** 20

<!--Device-Path-interpolate(other: Path, weight: double, interpolatedPath: Path): boolean--><!--Device-Path-interpolate(other: Path, weight: double, interpolatedPath: Path): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| other | [Path](arkts-arkgraphics2d-drawing-path-c.md) | 是 | 表示另一条路径对象。 |
| weight | number | 是 | 表示插值权重，必须在[0.0, 1.0]范围内。该参数为浮点数。 |
| interpolatedPath | [Path](arkts-arkgraphics2d-drawing-path-c.md) | 是 | 表示用于存储插值结果的目标路径对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回插值操作是否成功的结果。true表示插值成功，false表示插值失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-参数值异常) | Parameter error. Possible causes: Incorrect parameter range. |

<a id="isclosed"></a>
## isClosed

```TypeScript
isClosed(): boolean
```

获取路径是否闭合。

**起始版本：** 12

<!--Device-Path-isClosed(): boolean--><!--Device-Path-isClosed(): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示当前路径是否闭合，true表示闭合，false表示不闭合。 |

<a id="isempty"></a>
## isEmpty

```TypeScript
isEmpty(): boolean
```

判断路径是否为空。

**起始版本：** 20

<!--Device-Path-isEmpty(): boolean--><!--Device-Path-isEmpty(): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 路径是否为空。true表示当前路径为空，false表示路径不为空。 |

<a id="isequal"></a>
## isEqual

```TypeScript
isEqual(path: Path): boolean
```

Checks if two paths are equal.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Path-isEqual(path: Path): boolean--><!--Device-Path-isEqual(path: Path): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | [Path](arkts-arkgraphics2d-drawing-path-c.md) | 是 | Another Path object to compare. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the two paths are equal, otherwise returns false. |

<a id="isinterpolate"></a>
## isInterpolate

```TypeScript
isInterpolate(other: Path): boolean
```

判断当前路径与另一条路径在结构和操作顺序上是否完全一致，以确定两条路径是否兼容插值。若路径中包含圆锥曲线（Conic）操作，则对应操作的权重值也必须一致，才能视为兼容插值。

**起始版本：** 20

<!--Device-Path-isInterpolate(other: Path): boolean--><!--Device-Path-isInterpolate(other: Path): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| other | [Path](arkts-arkgraphics2d-drawing-path-c.md) | 是 | 表示另一条路径对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回当前路径与另一条路径是否兼容插值的结果。true表示兼容插值，false表示不兼容插值。 |

<a id="isinversefilltype"></a>
## isInverseFillType

```TypeScript
isInverseFillType(): boolean
```

检查当前路径填充类型是否是反向填充类型。例如填充类型Winding、EvenOdd不是反向类型，InverseWinding、InverseEvenOdd是反向类型。

**起始版本：** 23

<!--Device-Path-isInverseFillType(): boolean--><!--Device-Path-isInverseFillType(): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查当前路径填充类型是否是反向填充类型。true表示是反向填充类型，false表示不是反向填充类型。 |

<a id="isrect"></a>
## isRect

```TypeScript
isRect(rect: common2D.Rect | null): boolean
```

判断路径是否构成矩形。

**起始版本：** 20

<!--Device-Path-isRect(rect: common2D.Rect | null): boolean--><!--Device-Path-isRect(rect: common2D.Rect | null): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | common2D.Rect \| null | 是 | 矩形对象，作为出参使用，路径构成矩形时，会被改写为路径表示的矩形，否则不会改变。可以为null，表示无需获取路径表示的矩形。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回路径是否构成矩形。true表示路径构成矩形，false表示路径不构成矩形。 |

<a id="lineto"></a>
## lineTo

```TypeScript
lineTo(x: number, y: number): void
```

添加一条从路径的最后点位置（若路径没有内容则默认为 (0, 0)）到目标点位置的线段。

**起始版本：** 11

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Path-lineTo(x: double, y: double): void--><!--Device-Path-lineTo(x: double, y: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 目标点的x轴坐标，该参数为浮点数。 |
| y | number | 是 | 目标点的y轴坐标，该参数为浮点数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

<a id="moveto"></a>
## moveTo

```TypeScript
moveTo(x: number, y: number): void
```

设置自定义路径的起始点位置。

**起始版本：** 11

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Path-moveTo(x: double, y: double): void--><!--Device-Path-moveTo(x: double, y: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 起始点的x轴坐标，该参数为浮点数。 |
| y | number | 是 | 起始点的y轴坐标，该参数为浮点数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

<a id="offset"></a>
## offset

```TypeScript
offset(dx: number, dy: number): Path
```

将路径沿着x轴和y轴方向偏移一定距离并保存在返回的路径对象中。

**起始版本：** 12

<!--Device-Path-offset(dx: number, dy: number): Path--><!--Device-Path-offset(dx: number, dy: number): Path-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dx | number | 是 | x轴方向偏移量，正数往x轴正方向偏移，负数往x轴负方向偏移，该参数为浮点数。 |
| dy | number | 是 | y轴方向偏移量，正数往y轴正方向偏移，负数往y轴负方向偏移，该参数为浮点数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Path](arkts-arkgraphics2d-drawing-path-c.md) | 返回当前路径偏移(dx,dy)后生成的新路径对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

<a id="op"></a>
## op

```TypeScript
op(path: Path, pathOp: PathOp): boolean
```

将当前路径置为和path按照指定的路径操作类型合并后的结果。

**起始版本：** 12

<!--Device-Path-op(path: Path, pathOp: PathOp): boolean--><!--Device-Path-op(path: Path, pathOp: PathOp): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | [Path](arkts-arkgraphics2d-drawing-path-c.md) | 是 | 路径对象，用于与当前路径合并。 |
| pathOp | [PathOp](arkts-arkgraphics2d-drawing-pathop-e.md) | 是 | 路径操作类型枚举。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回路径合并是否成功的结果。true表示合并成功，false表示合并失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

<a id="quadto"></a>
## quadTo

```TypeScript
quadTo(ctrlX: number, ctrlY: number, endX: number, endY: number): void
```

添加从路径最后点位置（若路径没有内容则为 (0, 0)）到目标点位置的二阶贝塞尔曲线。

**起始版本：** 11

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Path-quadTo(ctrlX: double, ctrlY: double, endX: double, endY: double): void--><!--Device-Path-quadTo(ctrlX: double, ctrlY: double, endX: double, endY: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ctrlX | number | 是 | 控制点的x坐标，该参数为浮点数。 |
| ctrlY | number | 是 | 控制点的y坐标，该参数为浮点数。 |
| endX | number | 是 | 目标点的x坐标，该参数为浮点数。 |
| endY | number | 是 | 目标点的y坐标，该参数为浮点数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

<a id="rconicto"></a>
## rConicTo

```TypeScript
rConicTo(ctrlX: number, ctrlY: number, endX: number, endY: number, weight: number): void
```

使用相对位置在当前路径上添加一条路径终点（若路径没有内容则默认为 (0, 0)）到目标点位置的圆锥曲线。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Path-rConicTo(ctrlX: double, ctrlY: double, endX: double, endY: double, weight: double): void--><!--Device-Path-rConicTo(ctrlX: double, ctrlY: double, endX: double, endY: double, weight: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ctrlX | number | 是 | 控制点相对于路径终点的x轴偏移量，正数往x轴正方向偏移，负数往x轴负方向偏移，该参数为浮点数。 |
| ctrlY | number | 是 | 控制点相对于路径终点的y轴偏移量，正数往y轴正方向偏移，负数往y轴负方向偏移，该参数为浮点数。 |
| endX | number | 是 | 目标点相对于路径终点的x轴偏移量，正数往x轴正方向偏移，负数往x轴负方向偏移，该参数为浮点数。 |
| endY | number | 是 | 目标点相对于路径终点的y轴偏移量，正数往y轴正方向偏移，负数往y轴负方向偏移，该参数为浮点数。 |
| weight | number | 是 | 表示曲线的权重，决定了曲线的形状，越大越接近控制点。若小于等于0则等同于使用[rLineTo](arkts-arkgraphics2d-drawing-path-c.md#rlineto-1)添加一条到结束点的线段，若为1则等同于[rQuadTo](arkts-arkgraphics2d-drawing-path-c.md#rquadto-1)，该参数为浮点数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

<a id="rcubicto"></a>
## rCubicTo

```TypeScript
rCubicTo(ctrlX1: number, ctrlY1: number, ctrlX2: number, ctrlY2: number, endX: number, endY: number): void
```

使用相对位置在当前路径上添加一条当前路径终点（若路径没有内容则默认为 (0, 0)）到目标点位置的三阶贝塞尔曲线。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Path-rCubicTo(ctrlX1: double, ctrlY1: double, ctrlX2: double, ctrlY2: double, endX: double, endY: double): void--><!--Device-Path-rCubicTo(ctrlX1: double, ctrlY1: double, ctrlX2: double, ctrlY2: double, endX: double, endY: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ctrlX1 | number | 是 | 第一个控制点相对于路径终点的x轴偏移量，正数往x轴正方向偏移，负数往x轴负方向偏移，该参数为浮点数。 |
| ctrlY1 | number | 是 | 第一个控制点相对于路径终点的y轴偏移量，正数往y轴正方向偏移，负数往y轴负方向偏移，该参数为浮点数。 |
| ctrlX2 | number | 是 | 第二个控制点相对于路径终点的x轴偏移量，正数往x轴正方向偏移，负数往x轴负方向偏移，该参数为浮点数。 |
| ctrlY2 | number | 是 | 第二个控制点相对于路径终点的y轴偏移量，正数往y轴正方向偏移，负数往y轴负方向偏移，该参数为浮点数。 |
| endX | number | 是 | 目标点相对于路径终点的x轴偏移量，正数往x轴正方向偏移，负数往x轴负方向偏移，该参数为浮点数。 |
| endY | number | 是 | 目标点相对于路径终点的y轴偏移量，正数往y轴正方向偏移，负数往y轴负方向偏移，该参数为浮点数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

<a id="rlineto"></a>
## rLineTo

```TypeScript
rLineTo(dx: number, dy: number): void
```

使用相对位置在当前路径上添加一条当前路径终点（若路径没有内容则默认为 (0, 0)）到目标点位置的线段。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Path-rLineTo(dx: double, dy: double): void--><!--Device-Path-rLineTo(dx: double, dy: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dx | number | 是 | 目标点相对于当前路径终点的x轴偏移量，正数往x轴正方向偏移，负数往x轴负方向偏移，该参数为浮点数。 |
| dy | number | 是 | 目标点相对于当前路径终点的y轴偏移量，正数往y轴正方向偏移，负数往y轴负方向偏移，该参数为浮点数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

<a id="rmoveto"></a>
## rMoveTo

```TypeScript
rMoveTo(dx: number, dy: number): void
```

设置一个相对于当前路径终点（若路径没有内容则默认为 (0, 0)）的路径起始点位置。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Path-rMoveTo(dx: double, dy: double): void--><!--Device-Path-rMoveTo(dx: double, dy: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dx | number | 是 | 路径新起始点相对于当前路径终点的x轴偏移量，正数往x轴正方向偏移，负数往x轴负方向偏移，该参数为浮点数。 |
| dy | number | 是 | 路径新起始点相对于当前路径终点的y轴偏移量，正数往y轴正方向偏移，负数往y轴负方向偏移，该参数为浮点数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

<a id="rquadto"></a>
## rQuadTo

```TypeScript
rQuadTo(dx1: number, dy1: number, dx2: number, dy2: number): void
```

使用相对位置在当前路径上添加一条当前路径终点（若路径没有内容则默认为 (0, 0)）到目标点位置的二阶贝塞尔曲线。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Path-rQuadTo(dx1: double, dy1: double, dx2: double, dy2: double): void--><!--Device-Path-rQuadTo(dx1: double, dy1: double, dx2: double, dy2: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dx1 | number | 是 | 控制点相对于路径终点的x轴偏移量，正数往x轴正方向偏移，负数往x轴负方向偏移，该参数为浮点数。 |
| dy1 | number | 是 | 控制点相对于路径终点的y轴偏移量，正数往y轴正方向偏移，负数往y轴负方向偏移，该参数为浮点数。 |
| dx2 | number | 是 | 目标点相对于路径终点的x轴偏移量，正数往x轴正方向偏移，负数往x轴负方向偏移，该参数为浮点数。 |
| dy2 | number | 是 | 目标点相对于路径终点的y轴偏移量，正数往y轴正方向偏移，负数往y轴负方向偏移，该参数为浮点数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

<a id="reset"></a>
## reset

```TypeScript
reset(): void
```

重置自定义路径数据。

**起始版本：** 11

<!--Device-Path-reset(): void--><!--Device-Path-reset(): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

<a id="rewind"></a>
## rewind

```TypeScript
rewind(): void
```

将路径内添加的各类点/线清空，但是保留内存空间。

**起始版本：** 20

<!--Device-Path-rewind(): void--><!--Device-Path-rewind(): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

<a id="set"></a>
## set

```TypeScript
set(src: Path): void
```

使用另一个路径对当前路径进行更新。

**起始版本：** 20

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Path-set(src: Path): void--><!--Device-Path-set(src: Path): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [Path](arkts-arkgraphics2d-drawing-path-c.md) | 是 | 用于更新的路径。 |

<a id="setfilltype"></a>
## setFillType

```TypeScript
setFillType(pathFillType: PathFillType): void
```

设置路径的填充类型，决定路径内部区域的定义方式。例如，使用Winding填充类型时，路径内部区域由路径环绕的次数决定，而使用EvenOdd填充类型时，路径内部区域由路径环绕的次数是否为奇数决定。

**起始版本：** 12

<!--Device-Path-setFillType(pathFillType: PathFillType): void--><!--Device-Path-setFillType(pathFillType: PathFillType): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pathFillType | [PathFillType](arkts-arkgraphics2d-drawing-pathfilltype-e.md) | 是 | 表示路径填充规则。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

<a id="setlastpoint"></a>
## setLastPoint

```TypeScript
setLastPoint(x: number, y: number): void
```

修改路径的最后一个点。

**起始版本：** 20

<!--Device-Path-setLastPoint(x: double, y: double): void--><!--Device-Path-setLastPoint(x: double, y: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 指定点的x轴坐标，该参数为浮点数。0表示坐标原点，负数表示位于坐标原点左侧，正数表示位于坐标原点右侧。 |
| y | number | 是 | 指定点的y轴坐标，该参数为浮点数。0表示坐标原点，负数表示位于坐标原点上侧，正数表示位于坐标原点下侧。 |

<a id="toggleinversefilltype"></a>
## toggleInverseFillType

```TypeScript
toggleInverseFillType(): void
```

切换路径的填充类型为反向类型。例如，使用Winding填充类型时，经过取反后填充类型为InverseWinding，而使用EvenOdd填充类型时，经过取反后填充类型为InverseEvenOdd，反之亦然。

**起始版本：** 23

<!--Device-Path-toggleInverseFillType(): void--><!--Device-Path-toggleInverseFillType(): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

<a id="transform"></a>
## transform

```TypeScript
transform(matrix: Matrix): void
```

对路径进行矩阵变换。

**起始版本：** 12

<!--Device-Path-transform(matrix: Matrix): void--><!--Device-Path-transform(matrix: Matrix): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| matrix | [Matrix](arkts-arkgraphics2d-drawing-matrix-c.md) | 是 | 表示矩阵对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

