# RichEditorImageSpanStyle

图片样式。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## layoutStyle

```TypeScript
layoutStyle?: RichEditorLayoutStyle
```

图片布局样式。默认值：{"borderRadius":"","margin":""}

**类型：** [RichEditorLayoutStyle](arkts-arkui-richeditorlayoutstyle-i.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## objectFit

```TypeScript
objectFit?: ImageFit
```

图片缩放类型。默认值：ImageFit.Cover。

**类型：** [ImageFit](../arkts-apis/arkts-arkui-imagefit-e.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## resizable

```TypeScript
resizable?: ResizableOptions
```

图片拉伸选项。

**类型：** [ResizableOptions](arkts-arkui-resizableoptions-i.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: [Dimension, Dimension]
```

图片宽度和高度，默认单位为vp。默认值：与objectFit的值相关，不同的objectFit值有不同的默认尺寸。objectFit的值为Cover时，图片高度为组件高度减去组件上下内边距，宽度为组件宽度减去组件左右内边距。不支持 以Percentage形式设置。

**类型：** [Dimension, Dimension]

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## verticalAlign

```TypeScript
verticalAlign?: ImageSpanAlignment
```

图片垂直对齐方式。默认值：ImageSpanAlignment.BOTTOM

**类型：** [ImageSpanAlignment](../arkts-apis/arkts-arkui-imagespanalignment-e.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
