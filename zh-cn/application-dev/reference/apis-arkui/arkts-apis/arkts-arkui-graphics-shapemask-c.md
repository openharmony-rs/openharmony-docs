# ShapeMask

用于设置图形遮罩。

**起始版本：** 12

<!--Device-unnamed-export declare class ShapeMask--><!--Device-unnamed-export declare class ShapeMask-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

ShapeMask的构造函数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ShapeMask-constructor()--><!--Device-ShapeMask-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setCircleShape

```TypeScript
setCircleShape(circle: Circle): void
```

用于设置圆形遮罩。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ShapeMask-setCircleShape(circle: Circle): void--><!--Device-ShapeMask-setCircleShape(circle: Circle): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| circle | [Circle](arkts-arkui-graphics-circle-i.md) | 是 | 圆形的形状。 |

## setCommandPath

```TypeScript
setCommandPath(path: CommandPath): void
```

用于设置路径绘制指令。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ShapeMask-setCommandPath(path: CommandPath): void--><!--Device-ShapeMask-setCommandPath(path: CommandPath): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | [CommandPath](arkts-arkui-graphics-commandpath-i.md) | 是 | 路径绘制指令。 |

## setOvalShape

```TypeScript
setOvalShape(oval: Rect): void
```

用于设置椭圆形遮罩。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ShapeMask-setOvalShape(oval: Rect): void--><!--Device-ShapeMask-setOvalShape(oval: Rect): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| oval | [Rect](../../apis-test-kit/arkts-apis/arkts-test-uitest-rect-i.md) | 是 | 椭圆形的形状。 |

## setRectShape

```TypeScript
setRectShape(rect: Rect): void
```

用于设置矩形遮罩。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ShapeMask-setRectShape(rect: Rect): void--><!--Device-ShapeMask-setRectShape(rect: Rect): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | [Rect](../../apis-test-kit/arkts-apis/arkts-test-uitest-rect-i.md) | 是 | 矩形的形状。 |

## setRoundRectShape

```TypeScript
setRoundRectShape(roundRect: RoundRect): void
```

用于设置圆角矩形遮罩。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ShapeMask-setRoundRectShape(roundRect: RoundRect): void--><!--Device-ShapeMask-setRoundRectShape(roundRect: RoundRect): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| roundRect | [RoundRect](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-drawing-roundrect-c.md) | 是 | 圆角矩形的形状。 |

## fillColor

```TypeScript
fillColor: number
```

遮罩的填充颜色，使用ARGB格式。默认值为`0XFF000000`。

通过fillColor的透明度和亮度生成一个仅含透明度的颜色。亮度越高，颜色越透明。然后，使用[BlendMode.SRC_IN](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-drawing-blendmode-e.md)方式与RenderNode本身的颜色混合，生成最终颜色。

**类型：** number

**默认值：** 0XFF000000

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ShapeMask-fillColor: number--><!--Device-ShapeMask-fillColor: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeColor

```TypeScript
strokeColor: number
```

遮罩的边框颜色，使用ARGB格式。默认值为`0XFF000000`。

通过strokeColor的透明度和亮度生成一个仅含透明度的颜色。亮度越高，颜色越透明。然后，使用[BlendMode.SRC_IN](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-drawing-blendmode-e.md)方式与RenderNode本身的颜色混合，生成最终颜色。

**类型：** number

**默认值：** 0XFF000000

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ShapeMask-strokeColor: number--><!--Device-ShapeMask-strokeColor: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth: number
```

遮罩的边框宽度，单位为px。默认值为0。

**类型：** number

**默认值：** 0

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ShapeMask-strokeWidth: number--><!--Device-ShapeMask-strokeWidth: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

