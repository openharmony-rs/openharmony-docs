# RichEditorImageSpanStyle

图片样式。

**起始版本：** 10

<!--Device-unnamed-declare interface RichEditorImageSpanStyle--><!--Device-unnamed-declare interface RichEditorImageSpanStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## layoutStyle

```TypeScript
layoutStyle?: RichEditorLayoutStyle
```

图片布局样式。默认值：{"borderRadius":"","margin":""}

**类型：** RichEditorLayoutStyle

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorImageSpanStyle-layoutStyle?: RichEditorLayoutStyle--><!--Device-RichEditorImageSpanStyle-layoutStyle?: RichEditorLayoutStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## objectFit

```TypeScript
objectFit?: ImageFit
```

图片缩放类型。

默认值：ImageFit.Cover。

**类型：** ImageFit

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorImageSpanStyle-objectFit?: ImageFit--><!--Device-RichEditorImageSpanStyle-objectFit?: ImageFit-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: [Dimension, Dimension]
```

图片宽度和高度，默认单位为vp。默认值：与objectFit的值相关，不同的objectFit值有不同的默认尺寸。objectFit的值为Cover时，图片高度为组件高度减去组件上下内边距，宽度为组件宽度减去组件左右内边距。不支持以Percentage形式设置。

**类型：** [Dimension, Dimension]

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorImageSpanStyle-size?: [Dimension, Dimension]--><!--Device-RichEditorImageSpanStyle-size?: [Dimension, Dimension]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## verticalAlign

```TypeScript
verticalAlign?: ImageSpanAlignment
```

图片垂直对齐方式。

默认值：ImageSpanAlignment.BOTTOM

**类型：** ImageSpanAlignment

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorImageSpanStyle-verticalAlign?: ImageSpanAlignment--><!--Device-RichEditorImageSpanStyle-verticalAlign?: ImageSpanAlignment-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

