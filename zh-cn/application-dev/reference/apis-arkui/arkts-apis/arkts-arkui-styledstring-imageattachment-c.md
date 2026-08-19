# ImageAttachment

图片对象说明。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class ImageAttachment--><!--Device-unnamed-export declare class ImageAttachment-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(value: AttachmentType | undefined)
```

图片对象的构造函数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageAttachment-constructor(value: AttachmentType | undefined)--><!--Device-ImageAttachment-constructor(value: AttachmentType | undefined)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [AttachmentType](arkts-arkui-attachmenttype-t.md) \| undefined | 是 | PixelMap类型或 [ResourceStr](../../../reference/apis-arkui/arkui-ts/ts-types.md#resourcestr)类型图片设置项。 |

## colorFilter

```TypeScript
readonly colorFilter?: ColorFilterType
```

获取属性字符串的图片颜色滤镜效果。

**类型：** [ColorFilterType](arkts-arkui-colorfiltertype-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageAttachment-readonly colorFilter?: ColorFilterType--><!--Device-ImageAttachment-readonly colorFilter?: ColorFilterType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## layoutStyle

```TypeScript
readonly layoutStyle?: ImageAttachmentLayoutStyle
```

获取属性字符串的图片布局。

**类型：** [ImageAttachmentLayoutStyle](arkts-arkui-styledstring-imageattachmentlayoutstyle-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageAttachment-readonly layoutStyle?: ImageAttachmentLayoutStyle--><!--Device-ImageAttachment-readonly layoutStyle?: ImageAttachmentLayoutStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## objectFit

```TypeScript
readonly objectFit?: ImageFit
```

获取属性字符串的图片缩放类型。

**类型：** [ImageFit](arkts-arkui-imagefit-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageAttachment-readonly objectFit?: ImageFit--><!--Device-ImageAttachment-readonly objectFit?: ImageFit-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## resourceValue

```TypeScript
readonly resourceValue?: string
```

获取属性字符串的图片资源路径。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageAttachment-readonly resourceValue?: string--><!--Device-ImageAttachment-readonly resourceValue?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
readonly size?: SizeOptions
```

获取属性字符串的图片尺寸。 返回number类型值的单位为`px`。

**类型：** [SizeOptions](arkts-arkui-sizeoptions-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageAttachment-readonly size?: SizeOptions--><!--Device-ImageAttachment-readonly size?: SizeOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## sizeInVp

```TypeScript
readonly sizeInVp?: SizeOptions
```

获取属性字符串的图片尺寸。 返回number类型值的单位为`vp`。 当ImageAttachment尺寸设置为负数值或undefined时，返回为undefined。

**类型：** [SizeOptions](arkts-arkui-sizeoptions-i.md)

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageAttachment-readonly sizeInVp?: SizeOptions--><!--Device-ImageAttachment-readonly sizeInVp?: SizeOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## supportSvg2

```TypeScript
readonly supportSvg2?: boolean
```

获取属性字符串是否开启[SVG标签解析能力增强功能](../../../reference/apis-arkui/arkui-ts/ts-image-svg2-capabilities.md)。 true：支持SVG解析新能力；false：保持原有SVG解析能力。 默认值：false

**类型：** boolean

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageAttachment-readonly supportSvg2?: boolean--><!--Device-ImageAttachment-readonly supportSvg2?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
readonly value: PixelMap
```

获取属性字符串的图片数据源。

**类型：** [PixelMap](../arkts-components/arkts-arkui-pixelmap-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageAttachment-readonly value: PixelMap--><!--Device-ImageAttachment-readonly value: PixelMap-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## verticalAlign

```TypeScript
readonly verticalAlign?: ImageSpanAlignment
```

获取属性字符串的图片对齐方式。

**类型：** [ImageSpanAlignment](arkts-arkui-imagespanalignment-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageAttachment-readonly verticalAlign?: ImageSpanAlignment--><!--Device-ImageAttachment-readonly verticalAlign?: ImageSpanAlignment-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

