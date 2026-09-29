# RichEditorParagraphResult

```TypeScript
declare interface RichEditorParagraphResult
```

后端返回的段落信息。

**起始版本：** 11

<!--Device-unnamed-declare interface RichEditorParagraphResult--><!--Device-unnamed-declare interface RichEditorParagraphResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## range

```TypeScript
range: [number, number]
```

段落起始和结束位置，取值范围为[起始位置, 结束位置)，结束位置对应的内容不包含在内。

**类型：** [number, number]

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-RichEditorParagraphResult-range: [number, number]--><!--Device-RichEditorParagraphResult-range: [number, number]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style: RichEditorParagraphStyle
```

段落样式。

**类型：** [RichEditorParagraphStyle](arkts-arkui-richeditor-comp-richeditorparagraphstyle-i.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-RichEditorParagraphResult-style: RichEditorParagraphStyle--><!--Device-RichEditorParagraphResult-style: RichEditorParagraphStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
