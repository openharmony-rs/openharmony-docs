# SetPreviewTextWithStyleCallback

```TypeScript
export type SetPreviewTextWithStyleCallback = (text: string, range: Range, style: PreviewTextStyle) => void
```

当输入法框架需要显示带样式的预览文本时触发的回调。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-inputMethod-export type SetPreviewTextWithStyleCallback = (text: string, range: Range, style: PreviewTextStyle) => void--><!--Device-inputMethod-export type SetPreviewTextWithStyleCallback = (text: string, range: Range, style: PreviewTextStyle) => void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 预览文本内容。 |
| range | [Range](arkts-ime-inputmethod-range-i.md) | 是 | 文本的选中范围。 |
| style | [PreviewTextStyle](arkts-ime-inputmethod-previewtextstyle-i.md) | 是 | 预上屏文本的样式。 |
