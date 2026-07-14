# BackgroundImageOptions

定义背景图选项。

> **说明：**
>
> 背景图片的同步加载可能会带来潜在性能问题，详情可见[Image](../../../../reference/apis-arkui/arkui-ts/ts-basic-components-image.md#image-1)中说明。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## repeat

```TypeScript
repeat?: ImageRepeat
```

设置背景图片的重复样式。默认值为ImageRepeat.NoRepeat。

**类型：** ImageRepeat

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## syncLoad

```TypeScript
syncLoad?: boolean
```

是否同步加载图片，默认是异步加载。同步加载时阻塞UI线程，不会显示占位图。

默认值：false

false：异步加载图片。

true：同步加载图片。

**类型：** boolean

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

