# ImageAttachment

图片对象说明。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor(value: ImageAttachmentInterface)
```

图片对象的构造函数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ImageAttachmentInterface](arkts-arkui-imageattachmentinterface-i.md) | 是 | 图片设置项。 |

## constructor

```TypeScript
constructor(attachment: Optional<AttachmentType>)
```

图片对象的构造函数。与value类型入参构造函数相比，attachment参数增加了对undefined类型和[ResourceStr](arkts-arkui-resourcestr-t.md)类型图片的支持。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| attachment | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;[AttachmentType](arkts-arkui-attachmenttype-t.md)&gt; | 是 | PixelMap类型或[ResourceStr](arkts-arkui-resourcestr-t.md)类型图片设置项。 |

## colorFilter

```TypeScript
readonly colorFilter?: ColorFilterType
```

获取属性字符串的图片颜色滤镜效果。

**类型：** [ColorFilterType](arkts-arkui-colorfiltertype-t.md)

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## layoutStyle

```TypeScript
readonly layoutStyle?: ImageAttachmentLayoutStyle
```

获取属性字符串的图片布局。

**类型：** [ImageAttachmentLayoutStyle](arkts-arkui-imageattachmentlayoutstyle-i.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## objectFit

```TypeScript
readonly objectFit?: ImageFit
```

获取属性字符串的图片缩放类型。

**类型：** [ImageFit](arkts-arkui-imagefit-e.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## resizable

```TypeScript
readonly resizable?: ResizableOptions
```

获取属性字符串的图片拉伸选项。

**类型：** [ResizableOptions](../arkts-components/arkts-arkui-resizableoptions-i.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
readonly size?: SizeOptions
```

获取属性字符串的图片尺寸。返回number类型值的单位为`px`。

**类型：** [SizeOptions](arkts-arkui-sizeoptions-i.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## sizeInVp

```TypeScript
readonly sizeInVp?: SizeOptions
```

获取属性字符串的图片尺寸。返回number类型值的单位为`vp`。当ImageAttachment尺寸设置为负数值或undefined时，返回为undefined。

**类型：** [SizeOptions](arkts-arkui-sizeoptions-i.md)

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## supportSvg2

```TypeScript
readonly supportSvg2?: boolean
```

获取属性字符串是否开启SVG标签解析能力增强功能。true：支持SVG解析新能力；false：保持原有SVG解析能力。默认值：false

**类型：** boolean

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
readonly value: PixelMap
```

获取属性字符串的图片数据源。

**类型：** PixelMap

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## verticalAlign

```TypeScript
readonly verticalAlign?: ImageSpanAlignment
```

获取属性字符串的图片对齐方式。

**类型：** [ImageSpanAlignment](arkts-arkui-imagespanalignment-e.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
