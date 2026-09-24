# Path2D

```TypeScript
declare class Path2D extends CanvasPath
```

路径对象，支持通过对象的接口进行路径的描述和组合，并通过Canvas的stroke接口或者fill接口进行绘制。Path2D支持复用路径、组合多个路径、基于SVG路径字符串创建路径等功能，适用于需要多次绘制相同路径、动态组合复杂图形或基于SVG路径数据绘制图形的场景。

> **说明：** 
> 
> Path2D对象不支持重置已设置的路径，如需新路径可重新创建一个空的Path2D对象。
> 
> Path2D对象的方法无法对
> [CanvasRenderingContext2D](arkts-arkui-canvas-comp-canvasrenderingcontext2d-c.md)
> 和
> [OffscreenCanvasRenderingContext2D](arkts-arkui-canvas-comp-offscreencanvasrenderingcontext2d-c.md)
> 对象中设置的路径生效。

**继承/实现关系：** Path2D extends [CanvasPath](arkts-arkui-canvas-comp-canvaspath-c.md)

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## addPath

```TypeScript
addPath(path: Path2D, transform?: Matrix2D): void
```

将另一个路径添加到当前的路径对象中，并使用Matrix2D对象对新添加的路径对象进行图形变换。

**起始版本：** 8

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | [Path2D](arkts-arkui-canvas-comp-path2d-c.md) | 是 | 需要添加到当前路径的路径对象。<br>异常值undefined和null按无效值处理。 |
| transform | Matrix2D | 否 | 新增路径的变换矩阵对象，用于对添加的路径进行平移、旋转、缩放等变换。当需要对添加的路径进行图形变换时传入此参数，不需要变换时可不传。不传入时默认为null，表示不对路径进行变换。<br>异常值undefined和null按无效值处理。<br>默认值：null |

## constructor

```TypeScript
constructor()
```

构造一个空的Path2D对象。

**起始版本：** 8

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="constructor-1"></a>

## constructor

```TypeScript
constructor(unit: LengthMetricsUnit)
```

构造一个空的Path2D对象，支持配置Path2D对象的单位模式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| unit | LengthMetricsUnit | 是 | 用来配置Path2D对象的单位模式，配置后无法动态更改，配置方法同[CanvasRenderingContext2D](arkts-arkui-canvas-comp-canvasrenderingcontext2d-c.md)。<br>异常值NaN和Infinity按默认值处理。<br>默认值：DEFAULT |

<a id="constructor-2"></a>

## constructor

```TypeScript
constructor(path: Path2D)
```

使用路径对象构造Path2D对象。

**起始版本：** 8

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | [Path2D](arkts-arkui-canvas-comp-path2d-c.md) | 是 | 需要复制的路径对象，新创建的Path2D对象将包含与原路径相同的路径数据。异常值null和undefined时创建空路径对象。 |

<a id="constructor-3"></a>

## constructor

```TypeScript
constructor(path: Path2D, unit: LengthMetricsUnit)
```

使用路径对象构造Path2D对象，支持配置Path2D对象的单位模式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | [Path2D](arkts-arkui-canvas-comp-path2d-c.md) | 是 | 需要复制的Path2D路径对象，用于基于现有路径创建新的Path2D对象。传入的路径对象不会被修改，新创建的对象将包含该路径的完整副本。 |
| unit | LengthMetricsUnit | 是 | 用来配置Path2D对象的单位模式，配置后无法动态更改，配置方法同[CanvasRenderingContext2D](arkts-arkui-canvas-comp-canvasrenderingcontext2d-c.md)。<br>异常值NaN和Infinity按默认值处理。<br>默认值：DEFAULT |

<a id="constructor-4"></a>

## constructor

```TypeScript
constructor(d: string)
```

使用符合SVG路径描述规范的路径字符串构造Path2D对象。

**起始版本：** 8

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| d | string | 是 | 符合SVG路径描述规范的路径字符串，格式参考SVG路径描述规范，异常值按无效值处理。 |

<a id="constructor-5"></a>

## constructor

```TypeScript
constructor(description: string, unit: LengthMetricsUnit)
```

使用符合SVG路径描述规范的路径字符串构造Path2D对象，支持配置Path2D对象的单位模式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| description | string | 是 | 符合SVG路径描述规范的路径字符串，格式参考SVG路径描述规范，异常值按无效值处理。 |
| unit | LengthMetricsUnit | 是 | 用来配置Path2D对象的单位模式，配置后无法动态更改，配置方法同[CanvasRenderingContext2D](arkts-arkui-canvas-comp-canvasrenderingcontext2d-c.md)。<br>异常值NaN和Infinity按默认值处理。<br>默认值：DEFAULT |
