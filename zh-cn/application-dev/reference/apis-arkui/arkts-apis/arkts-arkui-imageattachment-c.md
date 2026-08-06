# ImageAttachment

图片对象说明。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-unnamed-declare class ImageAttachment--><!--Device-unnamed-declare class ImageAttachment-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(value: ImageAttachmentInterface)
```

图片对象的构造函数。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAttachment-constructor(value: ImageAttachmentInterface)--><!--Device-ImageAttachment-constructor(value: ImageAttachmentInterface)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 图片设置项。 |

## constructor

```TypeScript
constructor(attachment: Optional<AttachmentType>)
```

图片对象的构造函数。与value类型入参构造函数相比，attachment参数增加了对undefined类型和[ResourceStr]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_类型图片的支持。

**起始版本：** 15

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为15。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAttachment-constructor(attachment: Optional<AttachmentType>)--><!--Device-ImageAttachment-constructor(attachment: Optional<AttachmentType>)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| attachment | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;AttachmentType&gt; | 是 | PixelMap类型或[ResourceStr]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_类型图片设置项。 |

## colorFilter

```TypeScript
readonly colorFilter?: ColorFilterType
```

获取属性字符串的图片颜色滤镜效果。

**类型：** ColorFilterType

**起始版本：** 15

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为15。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAttachment-readonly colorFilter?: ColorFilterType--><!--Device-ImageAttachment-readonly colorFilter?: ColorFilterType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## layoutStyle

```TypeScript
readonly layoutStyle?: ImageAttachmentLayoutStyle
```

获取属性字符串的图片布局。

**类型：** ImageAttachmentLayoutStyle

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAttachment-readonly layoutStyle?: ImageAttachmentLayoutStyle--><!--Device-ImageAttachment-readonly layoutStyle?: ImageAttachmentLayoutStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## objectFit

```TypeScript
readonly objectFit?: ImageFit
```

获取属性字符串的图片缩放类型。

**类型：** ImageFit

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAttachment-readonly objectFit?: ImageFit--><!--Device-ImageAttachment-readonly objectFit?: ImageFit-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
readonly size?: SizeOptions
```

获取属性字符串的图片尺寸。 返回number类型值的单位为\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** SizeOptions

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAttachment-readonly size?: SizeOptions--><!--Device-ImageAttachment-readonly size?: SizeOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## sizeInVp

```TypeScript
readonly sizeInVp?: SizeOptions
```

获取属性字符串的图片尺寸。 返回number类型值的单位为\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。 当ImageAttachment尺寸设置为负数值或undefined时，返回为undefined。

**类型：** SizeOptions

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为21。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAttachment-readonly sizeInVp?: SizeOptions--><!--Device-ImageAttachment-readonly sizeInVp?: SizeOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## supportSvg2

```TypeScript
readonly supportSvg2?: boolean
```

获取属性字符串是否开启\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。 true：支持SVG解析新能力；false：保持原有SVG解析能力。 默认值：false

**类型：** boolean

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAttachment-readonly supportSvg2?: boolean--><!--Device-ImageAttachment-readonly supportSvg2?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
readonly value: PixelMap
```

获取属性字符串的图片数据源。

**类型：** PixelMap

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAttachment-readonly value: PixelMap--><!--Device-ImageAttachment-readonly value: PixelMap-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## verticalAlign

```TypeScript
readonly verticalAlign?: ImageSpanAlignment
```

获取属性字符串的图片对齐方式。

**类型：** ImageSpanAlignment

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAttachment-readonly verticalAlign?: ImageSpanAlignment--><!--Device-ImageAttachment-readonly verticalAlign?: ImageSpanAlignment-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

