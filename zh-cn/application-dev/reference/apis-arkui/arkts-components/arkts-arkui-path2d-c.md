# Path2D

路径对象，支持通过对象的接口进行路径的描述，并通过Canvas的stroke接口或者fill接口进行绘制。
> **说明：**  
>  
> Path2D对象不支持重置已设置的路径，如需新路径可重新创建一个空的Path2D对象。  
>  
> Path2D对象的方法无法对  
> [CanvasRenderingContext2D](../../../reference/apis-arkui/arkui-ts/ts-canvasrenderingcontext2d.md)  
> 和  
> [OffscreenCanvasRenderingContext2D](../../../reference/apis-arkui/arkui-ts/ts-offscreencanvasrenderingcontext2d.md)  
> 对象中设置的路径生效。

**继承/实现关系：** Path2D extends [CanvasPath](arkts-arkui-canvaspath-c.md)

**起始版本：** 8

<!--Device-unnamed-declare class Path2D extends CanvasPath--><!--Device-unnamed-declare class Path2D extends CanvasPath-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## addPath

```TypeScript
addPath(path: Path2D, transform?: Matrix2D): void
```

将另一个路径添加到当前的路径对象中，并使用Matrix2D对象对新添加的路径对象进行图形变换。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-Path2D-addPath(path: Path2D, transform?: Matrix2D): void--><!--Device-Path2D-addPath(path: Path2D, transform?: Matrix2D): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | [Path2D](arkts-arkui-path2d-c.md) | 是 | 需要添加到当前路径的路径对象，路径单位：px。<br>异常值undefined和null按无效值处理。 |
| transform | [Matrix2D](../arkts-apis/arkts-arkui-canvaspattern-matrix2d-c.md) | 否 | 新增路径的变换矩阵对象。<br>异常值undefined和null按无效值处理。<br>默认值：null。 |

## constructor

```TypeScript
constructor()
```

构造一个空的Path2D对象。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-Path2D-constructor()--><!--Device-Path2D-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(unit: LengthMetricsUnit)
```

构造一个空的Path2D对象，支持配置Path2D对象的单位模式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-Path2D-constructor(unit: LengthMetricsUnit)--><!--Device-Path2D-constructor(unit: LengthMetricsUnit)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| unit | [LengthMetricsUnit](../arkts-apis/arkts-arkui-graphics-lengthmetricsunit-e.md) | 是 | 用来配置Path2D对象的单位模式，配置后无法动态更改，配置方法同[CanvasRenderingContext2D](../../../reference/apis-arkui/arkui-ts/ts-canvasrenderingcontext2d.md)。<br>异常值NaN和Infinity按默认值处理。<br>默认值：DEFAULT。 |

## constructor

```TypeScript
constructor(path: Path2D)
```

使用路径对象构造Path2D对象。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-Path2D-constructor(path: Path2D)--><!--Device-Path2D-constructor(path: Path2D)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | [Path2D](arkts-arkui-path2d-c.md) | 是 | 路径对象。 |

## constructor

```TypeScript
constructor(path: Path2D, unit: LengthMetricsUnit)
```

使用路径对象构造Path2D对象，支持配置Path2D对象的单位模式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-Path2D-constructor(path: Path2D, unit: LengthMetricsUnit)--><!--Device-Path2D-constructor(path: Path2D, unit: LengthMetricsUnit)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | [Path2D](arkts-arkui-path2d-c.md) | 是 | 路径对象。 |
| unit | [LengthMetricsUnit](../arkts-apis/arkts-arkui-graphics-lengthmetricsunit-e.md) | 是 | 用来配置Path2D对象的单位模式，配置后无法动态更改，配置方法同[CanvasRenderingContext2D](../../../reference/apis-arkui/arkui-ts/ts-canvasrenderingcontext2d.md)。<br>异常值NaN和Infinity按默认值处理。<br>默认值：DEFAULT。 |

## constructor

```TypeScript
constructor(d: string)
```

使用符合SVG路径描述规范的路径字符串构造Path2D对象。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-Path2D-constructor(d: string)--><!--Device-Path2D-constructor(d: string)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| d | string | 是 | 符合SVG路径描述规范的路径字符串，格式参考[SVG路径描述规范](../../../reference/apis-arkui/arkui-ts/ts-drawing-components-path.md#svg路径描述规范)，异常值按无效值处理。 |

## constructor

```TypeScript
constructor(description: string, unit: LengthMetricsUnit)
```

使用符合SVG路径描述规范的路径字符串构造Path2D对象，支持配置Path2D对象的单位模式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-Path2D-constructor(description: string, unit: LengthMetricsUnit)--><!--Device-Path2D-constructor(description: string, unit: LengthMetricsUnit)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| description | string | 是 | 符合SVG路径描述规范的路径字符串，格式参考[SVG路径描述规范](../../../reference/apis-arkui/arkui-ts/ts-drawing-components-path.md#svg路径描述规范)，异常值按无效值处理。 |
| unit | [LengthMetricsUnit](../arkts-apis/arkts-arkui-graphics-lengthmetricsunit-e.md) | 是 | 用来配置Path2D对象的单位模式，配置后无法动态更改，配置方法同[CanvasRenderingContext2D](../../../reference/apis-arkui/arkui-ts/ts-canvasrenderingcontext2d.md)。<br>异常值NaN和Infinity按默认值处理。<br>默认值：DEFAULT。 |

