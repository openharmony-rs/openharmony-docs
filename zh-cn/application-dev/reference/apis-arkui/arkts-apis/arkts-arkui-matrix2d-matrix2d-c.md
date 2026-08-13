# Matrix2D

用于画布绘制[CanvasRenderingContext2D](../../../reference/apis-arkui/arkui-ts/ts-canvasrenderingcontext2d.md)、 [OffscreenCanvasRenderingContext2D](../../../reference/apis-arkui/arkui-ts/ts-offscreencanvasrenderingcontext2d.md)、 [CanvasPattern](../../../reference/apis-arkui/arkui-ts/ts-components-canvas-canvaspattern.md)和 [Path2D](../../../reference/apis-arkui/arkui-ts/ts-components-canvas-path2d.md)的矩阵对象， 可以对矩阵进行缩放、旋转和平移等变换。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class Matrix2D--><!--Device-unnamed-export declare class Matrix2D-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(unit?: LengthMetricsUnit)
```

构造二维变换矩阵对象，默认值是属性全为0的矩阵。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Matrix2D-constructor(unit?: LengthMetricsUnit)--><!--Device-Matrix2D-constructor(unit?: LengthMetricsUnit)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| unit | [LengthMetricsUnit](../../apis-na/arkts-apis/arkts-na-graphics-lengthmetricsunit-e.md) | 否 | 用来配置Matrix2D对象的单位模式，配置后无法动态更改。&lt;br&gt; 异常值NaN和Infinity按默认值处理。&lt;br&gt; 默认值：DEFAULT。 |

## identity

```TypeScript
identity(): Matrix2D
```

创建单位矩阵。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Matrix2D-identity(): Matrix2D--><!--Device-Matrix2D-identity(): Matrix2D-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Matrix2D](arkts-arkui-matrix2d-matrix2d-c.md) | 单位矩阵。 |

## invert

```TypeScript
invert(): Matrix2D
```

获取当前矩阵的逆矩阵。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Matrix2D-invert(): Matrix2D--><!--Device-Matrix2D-invert(): Matrix2D-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Matrix2D](arkts-arkui-matrix2d-matrix2d-c.md) | 逆矩阵结果。 |

## rotate

```TypeScript
rotate(degree: double, rx?: double, ry?: double): Matrix2D
```

以旋转点为中心，对当前矩阵进行右乘旋转运算。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Matrix2D-rotate(degree: double, rx?: double, ry?: double): Matrix2D--><!--Device-Matrix2D-rotate(degree: double, rx?: double, ry?: double): Matrix2D-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| degree | double | 是 | 旋转弧度，取值范围无限制。顺时针方向为正弧度， 可以通过`角度 Math.PI / 180`将角度转换为弧度值传入该接口。&lt;br&gt; 异常值undefined和null按无效值处理，NaN和Infinity会导致Matrix2D异常。&lt;br&gt; 默认单位：弧度。 |
| rx | double | 否 | 旋转点的水平方向坐标，取值范围无限制。&lt;br&gt; 默认单位：vp。&lt;br&gt; 异常值undefined和null按无效值处理，NaN和Infinity会导致Matrix2D异常。&lt;br&gt; 默认值：0。 |
| ry | double | 否 | 旋转点的垂直方向坐标，取值范围无限制。&lt;br&gt; 默认单位：vp。&lt;br&gt; 异常值undefined和null按无效值处理，NaN和Infinity会导致Matrix2D异常。&lt;br&gt; 默认值：0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Matrix2D](arkts-arkui-matrix2d-matrix2d-c.md) | 旋转后结果矩阵对象。 |

## scale

```TypeScript
scale(sx?: double, sy?: double): Matrix2D
```

对当前矩阵进行右乘缩放运算。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Matrix2D-scale(sx?: double, sy?: double): Matrix2D--><!--Device-Matrix2D-scale(sx?: double, sy?: double): Matrix2D-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sx | double | 否 | 水平缩放比例系数，取值范围无限制。&lt;br&gt; 异常值undefined和null按无效值处理，NaN和Infinity会导致Matrix2D异常。&lt;br&gt; 默认值：1.0。 |
| sy | double | 否 | 垂直缩放比例系数，取值范围无限制。&lt;br&gt; 异常值undefined和null按无效值处理，NaN和Infinity会导致Matrix2D异常。&lt;br&gt; 默认值：1.0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Matrix2D](arkts-arkui-matrix2d-matrix2d-c.md) | 缩放结果矩阵对象。 |

## translate

```TypeScript
translate(tx?: double, ty?: double): Matrix2D
```

对当前矩阵进行左乘平移运算。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Matrix2D-translate(tx?: double, ty?: double): Matrix2D--><!--Device-Matrix2D-translate(tx?: double, ty?: double): Matrix2D-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tx | double | 否 | 水平方向平移距离，取值范围无限制。&lt;br&gt; 异常值undefined和null按无效值处理，NaN和Infinity会导致Matrix2D异常。&lt;br&gt; 默认单位：vp。&lt;br&gt; 默认值：0。 |
| ty | double | 否 | 垂直方向平移距离，取值范围无限制。&lt;br&gt; 异常值undefined和null按无效值处理，NaN和Infinity会导致Matrix2D异常。&lt;br&gt; 默认单位：vp。&lt;br&gt; 默认值：0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Matrix2D](arkts-arkui-matrix2d-matrix2d-c.md) | 平移后结果矩阵对象。 |

