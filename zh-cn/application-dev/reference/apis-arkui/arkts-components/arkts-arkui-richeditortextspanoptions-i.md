# RichEditorTextSpanOptions

添加文本的偏移位置和文本样式信息。

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

## offset

```TypeScript
offset?: number
```

添加文本的位置。省略时，添加到所有内容的最后。

当值小于0时，放在所有内容最前面；当值大于所有内容长度时，放在所有内容最后面。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## paragraphStyle

```TypeScript
paragraphStyle?: RichEditorParagraphStyle
```

段落样式。

**类型：** RichEditorParagraphStyle

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: RichEditorTextStyle
```

文本Span样式信息。

**类型：** RichEditorTextStyle

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## urlStyle

```TypeScript
urlStyle?: RichEditorUrlStyle
```

url信息。

默认值：undefined

**类型：** RichEditorUrlStyle

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

