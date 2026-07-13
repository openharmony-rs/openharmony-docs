# RichEditorImageSpanStyleResult

后端返回的图片样式信息。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## layoutStyle

```TypeScript
layoutStyle?: RichEditorLayoutStyle
```

图片布局风格。

**类型：** RichEditorLayoutStyle

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## objectFit

```TypeScript
objectFit: ImageFit
```

图片缩放类型。

**类型：** ImageFit

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size: [number, number]
```

图片的宽度和高度，单位为px。默认值：size的默认值与objectFit的值有关，不同的objectFit值对应的size默认值也不同。objectFit的值为Cover时，图片高度为组件高度减去组件上下内边距，图片宽度为组件宽
度减去组件左右内边距。

**类型：** [number, number]

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## verticalAlign

```TypeScript
verticalAlign: ImageSpanAlignment
```

图片垂直对齐方式。

**类型：** ImageSpanAlignment

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

