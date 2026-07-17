# RichEditorTextSpanOptions

添加文本的偏移位置和文本样式信息。

**起始版本：** 10

<!--Device-unnamed-declare interface RichEditorTextSpanOptions--><!--Device-unnamed-declare interface RichEditorTextSpanOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## gesture

```TypeScript
gesture?: RichEditorGesture
```

行为触发回调。当需要自定义文本Span的点击或长按交互行为时传入此参数；省略时，仅使用系统默认行为。

**类型：** RichEditorGesture

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextSpanOptions-gesture?: RichEditorGesture--><!--Device-RichEditorTextSpanOptions-gesture?: RichEditorGesture-End-->

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

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextSpanOptions-offset?: number--><!--Device-RichEditorTextSpanOptions-offset?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## paragraphStyle

```TypeScript
paragraphStyle?: RichEditorParagraphStyle
```

段落样式。当需要设置文本的对齐方式、缩进、断行规则等段落级排版属性时传入此参数。不传入时，使用系统默认段落样式（左对齐、无缩进、按单词断行）。

**类型：** RichEditorParagraphStyle

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextSpanOptions-paragraphStyle?: RichEditorParagraphStyle--><!--Device-RichEditorTextSpanOptions-paragraphStyle?: RichEditorParagraphStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: RichEditorTextStyle
```

文本样式信息。当需要设置文本的颜色、字体大小、粗细等自定义样式时传入此参数。省略时，使用系统默认文本信息。

**类型：** RichEditorTextStyle

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextSpanOptions-style?: RichEditorTextStyle--><!--Device-RichEditorTextSpanOptions-style?: RichEditorTextStyle-End-->

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

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextSpanOptions-urlStyle?: RichEditorUrlStyle--><!--Device-RichEditorTextSpanOptions-urlStyle?: RichEditorUrlStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

