# ColorModeOptions

定义截图时所使用的色彩空间。

**起始版本：** 23

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## colorSpace

```TypeScript
colorSpace?: colorSpaceManager.ColorSpace
```

指定截图使用的色彩空间。

如果知道被截图组件使用的色彩空间，可以通过`colorSpace`字段指定，并将`isAuto`设置为false，以达到预期的截图效果。

取值范围：[colorSpaceManager.ColorSpace](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-colorspace-e.md)中
DISPLAY_P3、SRGB、DISPLAY_BT2020_SRGB。

默认值：SRGB

如果值为undefined、null或未设置，则使用默认值截图；其他异常值会导致截图失败，返回错误码160003。

**类型：** colorSpaceManager.ColorSpace

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isAuto

```TypeScript
isAuto?: boolean
```

是否由系统自动决定所使用的色彩空间。

支持取值为：true表示系统自动决定所使用的色彩空间；false表示使用通过`colorSpace`字段设置的色彩空间类型进行截图。取非法值时，按默认值false处理。

默认值：false

离屏截图仅支持设置为false，否则会返回错误码160004。

当`isAuto`设置为true时，建议将[SnapshotOptions](arkts-arkui-snapshotoptions-i.md)中的`waitUntilRenderFinished`字段也设置为
true，以便确保系统可以正常检测到所用的模式。

在不确定组件使用的色彩空间时，建议将`isAuto`设置为true，让系统根据实际情况自动决定使用的色彩空间。

当`isAuto`为true时，`colorSpace`字段设置的值会被忽略。此时，如果被截图组件同时包含不同色彩空间的子组件时，截图的色彩空间为优先级最高的色彩空间类型，优先级排序为DISPLAY_BT2020_SRGB >
DISPLAY_P3 > SRGB。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

