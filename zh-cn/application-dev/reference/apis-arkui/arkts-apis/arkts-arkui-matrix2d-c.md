# Matrix2D

用于画布绘制[CanvasRenderingContext2D](../../../reference/apis-arkui/arkui-ts/ts-canvasrenderingcontext2d.md)、[OffscreenCanvasRenderingContext2D](../../../reference/apis-arkui/arkui-ts/ts-offscreencanvasrenderingcontext2d.md)、[CanvasPattern](../../../reference/apis-arkui/arkui-ts/ts-components-canvas-canvaspattern.md)和[Path2D](../../../reference/apis-arkui/arkui-ts/ts-components-canvas-path2d.md)的矩阵对象，可以对矩阵进行缩放、旋转和平移等变换。

**起始版本：** 8

<!--Device-unnamed-declare class Matrix2D--><!--Device-unnamed-declare class Matrix2D-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

构造二维变换矩阵对象，默认值是属性全为0的矩阵。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-Matrix2D-constructor()--><!--Device-Matrix2D-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(unit: LengthMetricsUnit)
```

构造二维变换矩阵对象，默认值是属性全为0的矩阵，支持配置Matrix2D对象的单位模式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-Matrix2D-constructor(unit: LengthMetricsUnit)--><!--Device-Matrix2D-constructor(unit: LengthMetricsUnit)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| unit | [LengthMetricsUnit](arkts-arkui-graphics-lengthmetricsunit-e.md) | 是 | 用来配置Matrix2D对象的单位模式，配置后无法动态更改，配置方法同[CanvasRenderingContext2D](../../../reference/apis-arkui/arkui-ts/ts-canvasrenderingcontext2d.md)。<br>异常值NaN和Infinity按默认值处理。<br>默认值：DEFAULT |

## identity

```TypeScript
identity(): Matrix2D
```

创建单位矩阵。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-Matrix2D-identity(): Matrix2D--><!--Device-Matrix2D-identity(): Matrix2D-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Matrix2D](arkts-arkui-canvaspattern-matrix2d-c.md) | - 单位矩阵。 |

## invert

```TypeScript
invert(): Matrix2D
```

获取当前矩阵的逆矩阵。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-Matrix2D-invert(): Matrix2D--><!--Device-Matrix2D-invert(): Matrix2D-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Matrix2D](arkts-arkui-canvaspattern-matrix2d-c.md) | - 逆矩阵结果。 |

## multiply

```TypeScript
multiply(other?: Matrix2D): Matrix2D
```

当前矩阵与目标矩阵相乘。

**起始版本：** 8

**废弃版本：** 10

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-Matrix2D-multiply(other?: Matrix2D): Matrix2D--><!--Device-Matrix2D-multiply(other?: Matrix2D): Matrix2D-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| other | [Matrix2D](arkts-arkui-canvaspattern-matrix2d-c.md) | 否 | 目标矩阵。<br>异常值undefined和null按无效值处理。<br>默认值：null |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Matrix2D](arkts-arkui-canvaspattern-matrix2d-c.md) | - 相乘结果矩阵。 |

## rotate

```TypeScript
rotate(rx?: number, ry?: number): Matrix2D
```

对当前矩阵进行旋转运算。

**起始版本：** 8

**废弃版本：** 10

**替代接口：** [rotate](arkts-arkui-matrix2d-c.md#rotate)

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-Matrix2D-rotate(rx?: number, ry?: number): Matrix2D--><!--Device-Matrix2D-rotate(rx?: number, ry?: number): Matrix2D-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rx | number | 否 | 旋转点的水平方向坐标，取值范围无限制。<br>异常值undefined和null按无效值处理，NaN和Infinity会导致Matrix2D异常。<br>默认单位：vp |
| ry | number | 否 | 旋转点的垂直方向坐标，取值范围无限制。<br>异常值undefined和null按无效值处理，NaN和Infinity会导致Matrix2D异常。<br>默认单位：vp |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Matrix2D](arkts-arkui-canvaspattern-matrix2d-c.md) | @syscap SystemCapability.ArkUI.ArkUI.Full@FaAndStageModel@form |

## rotate

```TypeScript
rotate(degree: number, rx?: number, ry?: number): Matrix2D
```

以旋转点为中心，对当前矩阵进行右乘旋转运算。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-Matrix2D-rotate(degree: number, rx?: number, ry?: number): Matrix2D--><!--Device-Matrix2D-rotate(degree: number, rx?: number, ry?: number): Matrix2D-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| degree | number | 是 | 旋转角度，取值范围无限制。顺时针方向为正角度，可以通过 degree * Math.PI / 180 将角度转换为弧度值。<br>异常值undefined和null按无效值处理，NaN和Infinity会导致Matrix2D异常。<br>默认单位：弧度 |
| rx | number | 否 | 旋转点的水平方向坐标，取值范围无限制。<br>默认单位：vp<br>异常值undefined和null按无效值处理，NaN和Infinity会导致Matrix2D异常。<br>默认值：0 |
| ry | number | 否 | 旋转点的垂直方向坐标，取值范围无限制。<br>默认单位：vp<br>异常值undefined和null按无效值处理，NaN和Infinity会导致Matrix2D异常。<br>默认值：0 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Matrix2D](arkts-arkui-canvaspattern-matrix2d-c.md) | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@form@atomicservice |

## scale

```TypeScript
scale(sx?: number, sy?: number): Matrix2D
```

对当前矩阵进行右乘缩放运算。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-Matrix2D-scale(sx?: number, sy?: number): Matrix2D--><!--Device-Matrix2D-scale(sx?: number, sy?: number): Matrix2D-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sx | number | 否 | 水平缩放比例系数，取值范围无限制。<br>异常值undefined和null按无效值处理，NaN和Infinity会导致Matrix2D异常。<br>默认值：1.0 |
| sy | number | 否 | 垂直缩放比例系数，取值范围无限制。<br>异常值undefined和null按无效值处理，NaN和Infinity会导致Matrix2D异常。<br>默认值：1.0 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Matrix2D](arkts-arkui-canvaspattern-matrix2d-c.md) | @syscap SystemCapability.ArkUI.ArkUI.Full@FaAndStageModel@crossplatform |

## translate

```TypeScript
translate(tx?: number, ty?: number): Matrix2D
```

对当前矩阵进行左乘平移运算。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-Matrix2D-translate(tx?: number, ty?: number): Matrix2D--><!--Device-Matrix2D-translate(tx?: number, ty?: number): Matrix2D-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tx | number | 否 | 水平方向平移距离，取值范围无限制。<br>异常值undefined和null按无效值处理，NaN和Infinity会导致Matrix2D异常。<br>默认单位：vp<br>默认值：0 |
| ty | number | 否 | 垂直方向平移距离，取值范围无限制。<br>异常值undefined和null按无效值处理，NaN和Infinity会导致Matrix2D异常。<br>默认单位：vp<br>默认值：0 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Matrix2D](arkts-arkui-canvaspattern-matrix2d-c.md) | - 平移后结果矩阵对象。 |

## rotateX

```TypeScript
rotateX?: number
```

水平倾斜系数，取值范围无限制。<br>异常值undefined按无效值处理，NaN和Infinity会导致Matrix2D异常，设置后绘制内容不显示。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-Matrix2D-rotateX?: number--><!--Device-Matrix2D-rotateX?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## rotateY

```TypeScript
rotateY?: number
```

垂直倾斜系数，取值范围无限制。<br>异常值undefined按无效值处理，NaN和Infinity会导致Matrix2D异常，设置后绘制内容不显示。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-Matrix2D-rotateY?: number--><!--Device-Matrix2D-rotateY?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scaleX

```TypeScript
scaleX?: number
```

水平缩放系数，取值范围无限制。<br>异常值undefined按无效值处理，NaN和Infinity会导致Matrix2D异常，设置后绘制内容不显示。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-Matrix2D-scaleX?: number--><!--Device-Matrix2D-scaleX?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scaleY

```TypeScript
scaleY?: number
```

垂直缩放系数，取值范围无限制。<br>异常值undefined按无效值处理，NaN和Infinity会导致Matrix2D异常，设置后绘制内容不显示。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-Matrix2D-scaleY?: number--><!--Device-Matrix2D-scaleY?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## translateX

```TypeScript
translateX?: number
```

水平平移距离，取值范围无限制。<br>异常值undefined按无效值处理，NaN和Infinity会导致Matrix2D异常，设置后绘制内容不显示。<br>默认单位：vp

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-Matrix2D-translateX?: number--><!--Device-Matrix2D-translateX?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## translateY

```TypeScript
translateY?: number
```

垂直平移距离，取值范围无限制。<br>异常值undefined按无效值处理，NaN和Infinity会导致Matrix2D异常，设置后绘制内容不显示。<br>默认单位：vp

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-Matrix2D-translateY?: number--><!--Device-Matrix2D-translateY?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

