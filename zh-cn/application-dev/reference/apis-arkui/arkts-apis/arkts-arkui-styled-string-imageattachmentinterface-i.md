# ImageAttachmentInterface

定义图片设置项接口。

**起始版本：** 12

<!--Device-unnamed-declare interface ImageAttachmentInterface--><!--Device-unnamed-declare interface ImageAttachmentInterface-End-->

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

<!--Device-ImageAttachmentInterface-colorFilter?: ColorFilterType--><!--Device-ImageAttachmentInterface-colorFilter?: ColorFilterType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## layoutStyle

```TypeScript
layoutStyle?: ImageAttachmentLayoutStyle
```

设置图片布局。

**类型：** ImageAttachmentLayoutStyle

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAttachmentInterface-layoutStyle?: ImageAttachmentLayoutStyle--><!--Device-ImageAttachmentInterface-layoutStyle?: ImageAttachmentLayoutStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## objectFit

```TypeScript
objectFit?: ImageFit
```

设置图片的缩放类型，当前枚举类型不支持ImageFit.MATRIX。

默认值：ImageFit.Cover

**类型：** ImageFit

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAttachmentInterface-objectFit?: ImageFit--><!--Device-ImageAttachmentInterface-objectFit?: ImageFit-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: SizeOptions
```

设置图片大小，不支持百分比。

size的默认值与objectFit的值有关，不同的objectFit的值对应size的默认值不同。比如当objectFit的值为Cover时，图片高度为组件高度减去组件上下的内边距，图片宽度为组件宽度减去组件左右的内边距。

**类型：** SizeOptions

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAttachmentInterface-size?: SizeOptions--><!--Device-ImageAttachmentInterface-size?: SizeOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: PixelMap
```

设置图片数据源。

**类型：** PixelMap

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAttachmentInterface-value: PixelMap--><!--Device-ImageAttachmentInterface-value: PixelMap-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## verticalAlign

```TypeScript
verticalAlign?: ImageSpanAlignment
```

设置图片基于文本的对齐方式。

默认值：ImageSpanAlignment.BOTTOM

**类型：** ImageSpanAlignment

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAttachmentInterface-verticalAlign?: ImageSpanAlignment--><!--Device-ImageAttachmentInterface-verticalAlign?: ImageSpanAlignment-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

