# ImageAttachmentInterface

Defines the ImageAttachmentInterface.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface ImageAttachmentInterface--><!--Device-unnamed-export declare interface ImageAttachmentInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## colorFilter

```TypeScript
colorFilter?: ColorFilterType
```

设置属性字符串的图片颜色滤镜效果。

**类型：** [ColorFilterType](arkts-arkui-colorfiltertype-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageAttachmentInterface-colorFilter?: ColorFilterType--><!--Device-ImageAttachmentInterface-colorFilter?: ColorFilterType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## layoutStyle

```TypeScript
layoutStyle?: ImageAttachmentLayoutStyle
```

设置图片布局。

**类型：** [ImageAttachmentLayoutStyle](arkts-arkui-styledstring-imageattachmentlayoutstyle-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageAttachmentInterface-layoutStyle?: ImageAttachmentLayoutStyle--><!--Device-ImageAttachmentInterface-layoutStyle?: ImageAttachmentLayoutStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## objectFit

```TypeScript
objectFit?: ImageFit
```

设置图片的缩放类型，当前枚举类型不支持ImageFit.MATRIX。 默认值：ImageFit.Cover

**类型：** [ImageFit](arkts-arkui-imagefit-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageAttachmentInterface-objectFit?: ImageFit--><!--Device-ImageAttachmentInterface-objectFit?: ImageFit-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: SizeOptions
```

设置图片大小，不支持百分比。 size的默认值与objectFit的值有关，不同的objectFit的值对应size的默认值不同。比如当objectFit的值为Cover时，图片高度为组件高度减去组件上下的内边距，图片宽度为组件宽度减去组件左右的内边距。

**类型：** [SizeOptions](arkts-arkui-sizeoptions-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageAttachmentInterface-size?: SizeOptions--><!--Device-ImageAttachmentInterface-size?: SizeOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: PixelMap
```

设置图片数据源。

**类型：** [PixelMap](../arkts-components/arkts-arkui-pixelmap-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageAttachmentInterface-value: PixelMap--><!--Device-ImageAttachmentInterface-value: PixelMap-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## verticalAlign

```TypeScript
verticalAlign?: ImageSpanAlignment
```

设置图片基于文本的对齐方式。 默认值：ImageSpanAlignment.BOTTOM

**类型：** [ImageSpanAlignment](arkts-arkui-imagespanalignment-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageAttachmentInterface-verticalAlign?: ImageSpanAlignment--><!--Device-ImageAttachmentInterface-verticalAlign?: ImageSpanAlignment-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

