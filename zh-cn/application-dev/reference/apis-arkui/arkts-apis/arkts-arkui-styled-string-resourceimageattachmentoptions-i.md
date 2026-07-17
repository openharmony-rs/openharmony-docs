# ResourceImageAttachmentOptions

ResourceStr类型图片设置项。

**起始版本：** 15

<!--Device-unnamed-declare interface ResourceImageAttachmentOptions--><!--Device-unnamed-declare interface ResourceImageAttachmentOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## colorFilter

```TypeScript
colorFilter?: ColorFilterType
```

获取属性字符串的图片颜色滤镜效果。

**类型：** ColorFilterType

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-ResourceImageAttachmentOptions-colorFilter?: ColorFilterType--><!--Device-ResourceImageAttachmentOptions-colorFilter?: ColorFilterType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## layoutStyle

```TypeScript
layoutStyle?: ImageAttachmentLayoutStyle
```

设置图片布局。

**类型：** ImageAttachmentLayoutStyle

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-ResourceImageAttachmentOptions-layoutStyle?: ImageAttachmentLayoutStyle--><!--Device-ResourceImageAttachmentOptions-layoutStyle?: ImageAttachmentLayoutStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## objectFit

```TypeScript
objectFit?: ImageFit
```

设置图片的缩放类型，当前枚举类型不支持ImageFit.MATRIX。

默认值：ImageFit.Cover

**类型：** ImageFit

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-ResourceImageAttachmentOptions-objectFit?: ImageFit--><!--Device-ResourceImageAttachmentOptions-objectFit?: ImageFit-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## resourceValue

```TypeScript
resourceValue: Optional<ResourceStr>
```

设置图片数据源。

**类型：** Optional<ResourceStr>

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-ResourceImageAttachmentOptions-resourceValue: Optional<ResourceStr>--><!--Device-ResourceImageAttachmentOptions-resourceValue: Optional<ResourceStr>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: SizeOptions
```

设置图片大小。

**类型：** SizeOptions

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-ResourceImageAttachmentOptions-size?: SizeOptions--><!--Device-ResourceImageAttachmentOptions-size?: SizeOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## supportSvg2

```TypeScript
supportSvg2?: boolean
```

获取属性字符串是否开启[SVG标签解析能力增强功能](../../../../reference/apis-arkui/arkui-ts/ts-image-svg2-capabilities.md)。

true：支持SVG解析新能力；false：保持原有SVG解析能力。

默认值：false

**类型：** boolean

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ResourceImageAttachmentOptions-supportSvg2?: boolean--><!--Device-ResourceImageAttachmentOptions-supportSvg2?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## syncLoad

```TypeScript
syncLoad?: boolean
```

是否同步加载图片，默认是异步加载。同步加载时阻塞UI线程，不会显示占位图。

true：同步加载；false：异步加载。

默认值：false

**类型：** boolean

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-ResourceImageAttachmentOptions-syncLoad?: boolean--><!--Device-ResourceImageAttachmentOptions-syncLoad?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## verticalAlign

```TypeScript
verticalAlign?: ImageSpanAlignment
```

设置图片基于文本的对齐方式。

默认值：ImageSpanAlignment.BOTTOM

**类型：** ImageSpanAlignment

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-ResourceImageAttachmentOptions-verticalAlign?: ImageSpanAlignment--><!--Device-ResourceImageAttachmentOptions-verticalAlign?: ImageSpanAlignment-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

