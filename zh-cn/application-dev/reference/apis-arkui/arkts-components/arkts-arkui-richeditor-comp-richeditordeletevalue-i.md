# RichEditorDeleteValue

```TypeScript
declare interface RichEditorDeleteValue
```

删除操作和被删除内容的信息。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction: RichEditorDeleteDirection
```

删除操作的方向。

**类型：** [RichEditorDeleteDirection](arkts-arkui-richeditor-comp-richeditordeletedirection-e.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## length

```TypeScript
length: number
```

删除内容长度，删除范围为[offset, offset + length)，结束位置对应的内容不包含在内。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset: number
```

删除内容的偏移位置。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## richEditorDeleteSpans

```TypeScript
richEditorDeleteSpans: Array<RichEditorTextSpanResult | RichEditorImageSpanResult>
```

删除的文本或图片Span的信息。

**类型：** Array&lt;[RichEditorTextSpanResult](arkts-arkui-richeditor-comp-richeditortextspanresult-i.md) &#124; [RichEditorImageSpanResult](arkts-arkui-richeditor-comp-richeditorimagespanresult-i.md)&gt;

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
