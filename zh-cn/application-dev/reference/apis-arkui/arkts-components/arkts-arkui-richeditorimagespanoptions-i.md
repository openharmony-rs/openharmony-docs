# RichEditorImageSpanOptions

设置图片的偏移位置和图片样式信息。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## gesture

```TypeScript
gesture?: RichEditorGesture
```

行为触发回调。省略时，仅使用系统默认行为。

**类型：** RichEditorGesture

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageStyle

```TypeScript
imageStyle?: RichEditorImageSpanStyle
```

图片样式。

**类型：** RichEditorImageSpanStyle

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: number
```

添加图片的位置。省略时，添加到所有内容的末尾。

当值小于0时，设置在所有内容最前面；当值大于所有内容长度时，设置在所有内容最后面。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onHover

```TypeScript
onHover?: OnHoverCallback
```

鼠标悬停触发回调。省略时，不执行相关行为。

**类型：** OnHoverCallback

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

