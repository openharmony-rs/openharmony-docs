# RichEditorTextSpanResult

文本Span信息。

**起始版本：** 10

<!--Device-unnamed-declare interface RichEditorTextSpanResult--><!--Device-unnamed-declare interface RichEditorTextSpanResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offsetInSpan

```TypeScript
offsetInSpan: [number, number]
```

文本Span内容里有效内容的起始和结束位置。

**类型：** [number, number]

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextSpanResult-offsetInSpan: [number, number]--><!--Device-RichEditorTextSpanResult-offsetInSpan: [number, number]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## paragraphStyle

```TypeScript
paragraphStyle?: RichEditorParagraphStyle
```

段落样式。

省略时，使用系统默认段落样式。

**类型：** RichEditorParagraphStyle

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextSpanResult-paragraphStyle?: RichEditorParagraphStyle--><!--Device-RichEditorTextSpanResult-paragraphStyle?: RichEditorParagraphStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## previewText

```TypeScript
previewText?: string
```

文本Span预上屏内容。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextSpanResult-previewText?: string--><!--Device-RichEditorTextSpanResult-previewText?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## spanPosition

```TypeScript
spanPosition: RichEditorSpanPosition
```

Span位置。

**类型：** RichEditorSpanPosition

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextSpanResult-spanPosition: RichEditorSpanPosition--><!--Device-RichEditorTextSpanResult-spanPosition: RichEditorSpanPosition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolSpanStyle

```TypeScript
symbolSpanStyle?: RichEditorSymbolSpanStyle
```

组件SymbolSpan样式信息。

**类型：** RichEditorSymbolSpanStyle

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextSpanResult-symbolSpanStyle?: RichEditorSymbolSpanStyle--><!--Device-RichEditorTextSpanResult-symbolSpanStyle?: RichEditorSymbolSpanStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textStyle

```TypeScript
textStyle: RichEditorTextStyleResult
```

文本Span样式信息。

**类型：** RichEditorTextStyleResult

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextSpanResult-textStyle: RichEditorTextStyleResult--><!--Device-RichEditorTextSpanResult-textStyle: RichEditorTextStyleResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## urlStyle

```TypeScript
urlStyle?: RichEditorUrlStyle
```

url信息。

默认值：undefined。

当需要为文本设置超链接样式时传入此参数。

**类型：** RichEditorUrlStyle

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextSpanResult-urlStyle?: RichEditorUrlStyle--><!--Device-RichEditorTextSpanResult-urlStyle?: RichEditorUrlStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: string
```

文本Span内容或Symbol的id。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextSpanResult-value: string--><!--Device-RichEditorTextSpanResult-value: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## valueResource

```TypeScript
valueResource?: Resource
```

SymbolSpan资源内容。

默认值：undefined。

**类型：** Resource

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextSpanResult-valueResource?: Resource--><!--Device-RichEditorTextSpanResult-valueResource?: Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

