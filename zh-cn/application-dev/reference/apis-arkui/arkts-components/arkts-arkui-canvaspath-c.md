# CanvasPath

路径对象，提供基本的路径绘制方法。路径相关API的详细说明请参见CanvasRenderingContext2D中的描述。

**起始版本：** 8

<!--Device-unnamed-declare class CanvasPath--><!--Device-unnamed-declare class CanvasPath-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="arc"></a>
## arc

```TypeScript
arc(x: number, y: number, radius: number, startAngle: number, endAngle: number, counterclockwise?: boolean): void
```

绘制弧线路径。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CanvasPath-arc(x: number, y: number, radius: number, startAngle: number, endAngle: number, counterclockwise?: boolean): void--><!--Device-CanvasPath-arc(x: number, y: number, radius: number, startAngle: number, endAngle: number, counterclockwise?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 弧线圆心的x坐标值。<br>API version 18之前，设置NaN或Infinity时，整条路径不显示；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的路径方法正常绘制。默认单位：vp |
| y | number | 是 | 弧线圆心的y坐标值。<br>API version 18之前，设置NaN或Infinity时，整条路径不显示；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的路径方法正常绘制。默认单位：vp |
| radius | number | 是 | 弧线的圆半径。<br>API version 18之前，设置NaN或Infinity时，整条路径不显示；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的路径方法正常绘制。默认单位：vp |
| startAngle | number | 是 | 弧线的起始弧度。单位：弧度。 |
| endAngle | number | 是 | 弧线的终止弧度。单位：弧度。 |
| counterclockwise | boolean | 否 | 是否逆时针绘制圆弧。<br>**true**：逆时针方向绘制圆弧。<br>**false**：顺时针方向绘制圆弧。<br>默认值：**false**，设置**null**或**undefined**按默认值处理。 |

<a id="arcto"></a>
## arcTo

```TypeScript
arcTo(x1: number, y1: number, x2: number, y2: number, radius: number): void
```

依据圆弧经过的点和圆弧半径创建圆弧路径。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CanvasPath-arcTo(x1: number, y1: number, x2: number, y2: number, radius: number): void--><!--Device-CanvasPath-arcTo(x1: number, y1: number, x2: number, y2: number, radius: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x1 | number | 是 | 圆弧经过的第一个点的x坐标值。<br>API version 18之前，设置NaN或Infinity时，整条路径不显示；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的路径方法正常绘制。默认单位：vp |
| y1 | number | 是 | 圆弧经过的第一个点的y坐标值。<br>API version 18之前，设置NaN或Infinity时，整条路径不显示；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的路径方法正常绘制。默认单位：vp |
| x2 | number | 是 | 圆弧经过的第二个点的x坐标值。<br>API version 18之前，设置NaN或Infinity时，整条路径不显示；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的路径方法正常绘制。默认单位：vp |
| y2 | number | 是 | 圆弧经过的第二个点的y坐标值。<br>API version 18之前，设置NaN或Infinity时，整条路径不显示；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的路径方法正常绘制。默认单位：vp |
| radius | number | 是 | 圆弧的圆半径值。<br>API version 18之前，设置NaN或Infinity时，整条路径不显示；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的路径方法正常绘制。默认单位：vp |

<a id="beziercurveto"></a>
## bezierCurveTo

```TypeScript
bezierCurveTo(cp1x: number, cp1y: number, cp2x: number, cp2y: number, x: number, y: number): void
```

创建三次贝塞尔曲线的路径。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CanvasPath-bezierCurveTo(cp1x: number, cp1y: number, cp2x: number, cp2y: number, x: number, y: number): void--><!--Device-CanvasPath-bezierCurveTo(cp1x: number, cp1y: number, cp2x: number, cp2y: number, x: number, y: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cp1x | number | 是 | 第一个贝塞尔参数的x坐标值。<br>API version 18之前，设置NaN或Infinity时，整条路径不显示；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的路径方法正常绘制。默认单位：vp |
| cp1y | number | 是 | 第一个贝塞尔参数的y坐标值。<br>API version 18之前，设置NaN或Infinity时，整条路径不显示；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的路径方法正常绘制。默认单位：vp |
| cp2x | number | 是 | 第二个贝塞尔参数的x坐标值。<br>API version 18之前，设置NaN或Infinity时，整条路径不显示；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的路径方法正常绘制。默认单位：vp |
| cp2y | number | 是 | 第二个贝塞尔参数的y坐标值。<br>API version 18之前，设置NaN或Infinity时，整条路径不显示；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的路径方法正常绘制。默认单位：vp |
| x | number | 是 | 路径结束时的x坐标值。<br>API version 18之前，设置NaN或Infinity时，整条路径不显示；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的路径方法正常绘制。默认单位：vp |
| y | number | 是 | 路径结束时的y坐标值。<br>API version 18之前，设置NaN或Infinity时，整条路径不显示；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的路径方法正常绘制。默认单位：vp |

<a id="closepath"></a>
## closePath

```TypeScript
closePath(): void
```

将路径的当前点移回到路径的起点，当前点到起点间画一条直线。如果形状已经闭合或只有一个点，则此功能不执行任何操作。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CanvasPath-closePath(): void--><!--Device-CanvasPath-closePath(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="ellipse"></a>
## ellipse

```TypeScript
ellipse(
    x: number,
    y: number,
    radiusX: number,
    radiusY: number,
    rotation: number,
    startAngle: number,
    endAngle: number,
    counterclockwise?: boolean,
  ): void
```

在规定的矩形区域绘制一个椭圆。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CanvasPath-ellipse(
    x: number,
    y: number,
    radiusX: number,
    radiusY: number,
    rotation: number,
    startAngle: number,
    endAngle: number,
    counterclockwise?: boolean,
  ): void--><!--Device-CanvasPath-ellipse(
    x: number,
    y: number,
    radiusX: number,
    radiusY: number,
    rotation: number,
    startAngle: number,
    endAngle: number,
    counterclockwise?: boolean,
  ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 椭圆圆心的x轴坐标。<br>API version 18之前，设置NaN或Infinity时，整条路径不显示；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的路径方法正常绘制。默认单位：vp |
| y | number | 是 | 椭圆圆心的y轴坐标。<br>API version 18之前，设置NaN或Infinity时，整条路径不显示；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的路径方法正常绘制。默认单位：vp |
| radiusX | number | 是 | 椭圆x轴的半径长度。<br>API version 18之前，设置NaN或Infinity时，整条路径不显示；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的路径方法正常绘制。默认单位：vp |
| radiusY | number | 是 | 椭圆y轴的半径长度。<br>API version 18之前，设置NaN或Infinity时，整条路径不显示；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的路径方法正常绘制。默认单位：vp |
| rotation | number | 是 | 椭圆的旋转角度。单位：弧度。 |
| startAngle | number | 是 | 椭圆绘制的起始点角度。单位：弧度。 |
| endAngle | number | 是 | 椭圆绘制的结束点角度。单位：弧度。 |
| counterclockwise | boolean | 否 | 是否以逆时针方向绘制椭圆。<br>**true**：逆时针方向绘制椭圆。<br>**false**：顺时针方向绘制椭圆。<br>默认值：**false**，设置**null**或**undefined**按默认值处理。 |

<a id="lineto"></a>
## lineTo

```TypeScript
lineTo(x: number, y: number): void
```

从当前点绘制一条直线到目标点。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CanvasPath-lineTo(x: number, y: number): void--><!--Device-CanvasPath-lineTo(x: number, y: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 目标点X轴坐标。<br>API version 18之前，设置NaN或Infinity时，整条路径不显示；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的路径方法正常绘制。默认单位：vp |
| y | number | 是 | 目标点Y轴坐标。<br>API version 18之前，设置NaN或Infinity时，整条路径不显示；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的路径方法正常绘制。默认单位：vp |

<a id="moveto"></a>
## moveTo

```TypeScript
moveTo(x: number, y: number): void
```

将路径的当前坐标点移动到目标点，移动过程中不绘制线条。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CanvasPath-moveTo(x: number, y: number): void--><!--Device-CanvasPath-moveTo(x: number, y: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 目标点X轴坐标。<br>API version 18之前，设置NaN或Infinity时，整条路径不显示；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的路径方法正常绘制。默认单位：vp |
| y | number | 是 | 目标点Y轴坐标。<br>API version 18之前，设置NaN或Infinity时，整条路径不显示；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的路径方法正常绘制。默认单位：vp * > **说明：**   >   > API version 18之前，如果没有调用**moveTo**接口或传入无效参数，路径从(0,0)开始。   >   > API version 18及以后，如果没有调用**moveTo**接口或传入无效参数，路径将从第一个有效调用的   > **lineTo**、**arcTo**、**bezierCurveTo**或**quadraticCurveTo**的起始点开始。* |

<a id="quadraticcurveto"></a>
## quadraticCurveTo

```TypeScript
quadraticCurveTo(cpx: number, cpy: number, x: number, y: number): void
```

创建二次贝塞尔曲线路径。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CanvasPath-quadraticCurveTo(cpx: number, cpy: number, x: number, y: number): void--><!--Device-CanvasPath-quadraticCurveTo(cpx: number, cpy: number, x: number, y: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cpx | number | 是 | 贝塞尔参数的x坐标值。<br>API version 18之前，设置NaN或Infinity时，整条路径不显示；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的路径方法正常绘制。默认单位：vp |
| cpy | number | 是 | 贝塞尔参数的y坐标值。<br>API version 18之前，设置NaN或Infinity时，整条路径不显示；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的路径方法正常绘制。默认单位：vp |
| x | number | 是 | 路径结束时的x坐标值。<br>API version 18之前，设置NaN或Infinity时，整条路径不显示；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的路径方法正常绘制。默认单位：vp |
| y | number | 是 | 路径结束时的y坐标值。<br>API version 18之前，设置NaN或Infinity时，整条路径不显示；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的路径方法正常绘制。默认单位：vp |

<a id="rect"></a>
## rect

```TypeScript
rect(x: number, y: number, w: number, h: number): void
```

创建矩形路径。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CanvasPath-rect(x: number, y: number, w: number, h: number): void--><!--Device-CanvasPath-rect(x: number, y: number, w: number, h: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 指定矩形的左上角x坐标值。<br>API version 18之前，设置NaN或Infinity时，整条路径不显示；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的路径方法正常绘制。默认单位：vp |
| y | number | 是 | 指定矩形的左上角y坐标值。<br>API version 18之前，设置NaN或Infinity时，整条路径不显示；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的路径方法正常绘制。默认单位：vp |
| w | number | 是 | 指定矩形的宽度。<br>API version 18之前，设置NaN或Infinity时，整条路径不显示；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的路径方法正常绘制。默认单位：vp |
| h | number | 是 | 指定矩形的高度。<br>API version 18之前，设置NaN或Infinity时，整条路径不显示；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的路径方法正常绘制。默认单位：vp |

<a id="roundrect"></a>
## roundRect

```TypeScript
roundRect(x: number, y: number, w: number, h: number, radii?: number | Array<number>): void
```

创建圆角矩形路径，此方法不会直接渲染内容，如需将圆角矩形绘制到画布上，可以使用fill或stroke方法。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

<!--Device-CanvasPath-roundRect(x: number, y: number, w: number, h: number, radii?: number | Array<number>): void--><!--Device-CanvasPath-roundRect(x: number, y: number, w: number, h: number, radii?: number | Array<number>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 矩形左上角x坐标值。<br>设置**null**时，按照**0**处理；设置**undefined**时，按无效值处理，不进行绘制。<br>绘制完整矩形时，取值范围为[0, 画布宽度)。<br>默认单位：vp |
| y | number | 是 | 矩形左上角y坐标值。<br>设置**null**时，按照**0**处理；设置**undefined**时，按无效值处理，不进行绘制。<br>绘制完整矩形时，取值范围为[0, 画布高度)。<br>默认单位：vp |
| w | number | 是 | 矩形的宽度。负值表示从右向左绘制矩形。<br>设置**null**时，按照**0**处理；设置**undefined**时，按无效值处理，不进行绘制。<br>绘制完整矩形时，取值范围为[-x, 画布宽度 - x]。<br>默认单位：vp |
| h | number | 是 | 矩形的高度。负值表示向上绘制。<br>设置**null**时，按照**0**处理；设置**undefined**时，按无效值处理，不进行绘制。<br>绘制完整矩形时，取值范围为[-y, 画布高度 - y]。<br>默认单位：vp |
| radii | number \| Array&lt;number&gt; | 否 | 矩形圆角的圆弧半径值或半径值列表。<br>参数类型为number时，表示矩形四个角的圆弧半径。<br>参数类型为Array<number>时，数组包含1到4个数字，含义如下：<br>[矩形四个角的圆弧半径]<br>[矩形左上角和右下角的圆弧半径，矩形右上角和左下角的圆弧半径]<br>[矩形左上角的圆弧半径，矩形右上角和左下角的圆弧半径，矩形右下角的圆弧半径]<br>[矩形左上角的圆弧半径，矩形右上角的圆弧半径，矩形右下角的圆弧半径，矩形左下角的圆弧半径]<br>如果**radii**中包含负数或数组元素个数不在[1,4]范围内，则上报错误码103701。<br>默认值：**0**。设置**null**或**undefined**时按默认值处理。<br>如果圆弧半径超过矩形的宽度和高度，将按比例缩小以匹配对应尺寸。<br>默认单位：vp |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [103701](../errorcode-canvas.md#103701-参数错误) | 参数错误。可能的原因：<br> 1. 参数radii数组的元素个数为0或超过4个。<br> 2. 参数radii中包含负数。 |

