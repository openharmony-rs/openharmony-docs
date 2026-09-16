# RichEditorSelection

选中内容信息。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selection

```TypeScript
selection: [number, number]
```

选中范围，取值范围为[起始位置, 结束位置)，结束位置对应的内容不包含在内。

**类型：** [number, number]

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## spans

```TypeScript
spans: Array<RichEditorTextSpanResult | RichEditorImageSpanResult>
```

span信息。

**类型：** Array&lt;[RichEditorTextSpanResult](arkts-arkui-richeditortextspanresult-i.md) &#124; [RichEditorImageSpanResult](arkts-arkui-richeditorimagespanresult-i.md)&gt;

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
