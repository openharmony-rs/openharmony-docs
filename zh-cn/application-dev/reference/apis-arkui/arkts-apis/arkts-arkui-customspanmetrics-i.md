# CustomSpanMetrics

```TypeScript
declare interface CustomSpanMetrics
```

定义自定义绘制Span的尺寸信息接口。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: number
```

自定义绘制Span的高。

默认值：不传入时默认取Text组件的fontSize值作为CustomSpan的高度。

单位：[vp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位)

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width: number
```

自定义绘制Span的宽。

单位：[vp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位)

**类型：** number

**默认值：** 0

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
