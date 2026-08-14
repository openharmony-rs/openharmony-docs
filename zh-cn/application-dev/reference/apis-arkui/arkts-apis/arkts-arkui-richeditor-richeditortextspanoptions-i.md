# RichEditorTextSpanOptions

添加文本的偏移位置和文本样式信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface RichEditorTextSpanOptions--><!--Device-unnamed-export declare interface RichEditorTextSpanOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## gesture

```TypeScript
gesture?: RichEditorGesture
```

行为触发回调。省略时，仅使用系统默认行为。

**类型：** [RichEditorGesture](arkts-arkui-richeditor-richeditorgesture-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextSpanOptions-gesture?: RichEditorGesture--><!--Device-RichEditorTextSpanOptions-gesture?: RichEditorGesture-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: int
```

添加文本的位置。省略时，添加到所有内容的最后。 当值小于0时，放在所有内容最前面；当值大于所有内容长度时，放在所有内容最后面。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextSpanOptions-offset?: int--><!--Device-RichEditorTextSpanOptions-offset?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## paragraphStyle

```TypeScript
paragraphStyle?: RichEditorParagraphStyle
```

段落样式。

**类型：** [RichEditorParagraphStyle](arkts-arkui-richeditor-richeditorparagraphstyle-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextSpanOptions-paragraphStyle?: RichEditorParagraphStyle--><!--Device-RichEditorTextSpanOptions-paragraphStyle?: RichEditorParagraphStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: RichEditorTextStyle
```

文本Span样式信息。

**类型：** [RichEditorTextStyle](arkts-arkui-richeditor-richeditortextstyle-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextSpanOptions-style?: RichEditorTextStyle--><!--Device-RichEditorTextSpanOptions-style?: RichEditorTextStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## urlStyle

```TypeScript
urlStyle?: RichEditorUrlStyle
```

url信息。 默认值：undefined

**类型：** [RichEditorUrlStyle](arkts-arkui-richeditor-richeditorurlstyle-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextSpanOptions-urlStyle?: RichEditorUrlStyle--><!--Device-RichEditorTextSpanOptions-urlStyle?: RichEditorUrlStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

