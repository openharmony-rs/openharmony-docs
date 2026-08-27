# ImageAttachmentInterface

定义图片设置项接口。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## colorFilter

```TypeScript
colorFilter?: ColorFilterType
```

获取属性字符串的图片颜色滤镜效果。

**类型：** [ColorFilterType](arkts-arkui-colorfiltertype-t.md)

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## layoutStyle

```TypeScript
layoutStyle?: ImageAttachmentLayoutStyle
```

设置图片布局。不传入时使用默认布局（外边距、内边距和圆角均为0）。

**类型：** [ImageAttachmentLayoutStyle](arkts-arkui-imageattachmentlayoutstyle-i.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## objectFit

```TypeScript
objectFit?: ImageFit
```

设置图片的缩放类型，当前枚举类型不支持ImageFit.MATRIX。具体枚举及说明请参考ImageFit。默认值：ImageFit.Cover

**类型：** [ImageFit](arkts-arkui-imagefit-e.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## resizable

```TypeScript
resizable?: ResizableOptions
```

获取属性字符串的图片拉伸选项。

**类型：** [ResizableOptions](../arkts-components/arkts-arkui-resizableoptions-i.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: SizeOptions
```

设置图片大小，不支持百分比。size的默认值与objectFit的值有关，不同的objectFit的值对应size的默认值不同。比如当objectFit的值为Cover时，图片高度为组件高度减去组件上下的内边距，图片宽度为组件宽度减去组件左右的内边距。

**类型：** [SizeOptions](arkts-arkui-sizeoptions-i.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

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

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## verticalAlign

```TypeScript
verticalAlign?: ImageSpanAlignment
```

设置图片基于文本的对齐方式。默认值：ImageSpanAlignment.BOTTOM

**类型：** [ImageSpanAlignment](arkts-arkui-imagespanalignment-e.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
