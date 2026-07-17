# DrawContext

图形绘制上下文，提供绘制所需的画布宽度和高度。

**起始版本：** 11

<!--Device-unnamed-export class DrawContext--><!--Device-unnamed-export class DrawContext-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## canvas

```TypeScript
get canvas(): drawing.Canvas
```

获取用于绘制的画布。

**类型：** drawing.Canvas

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DrawContext-get canvas(): drawing.Canvas--><!--Device-DrawContext-get canvas(): drawing.Canvas-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
get size(): Size
```

获取画布的宽度和高度。

**类型：** Size

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DrawContext-get size(): Size--><!--Device-DrawContext-get size(): Size-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## sizeInPixel

```TypeScript
get sizeInPixel(): Size
```

获取以px为单位的画布的宽度和高度。

**类型：** Size

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DrawContext-get sizeInPixel(): Size--><!--Device-DrawContext-get sizeInPixel(): Size-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

