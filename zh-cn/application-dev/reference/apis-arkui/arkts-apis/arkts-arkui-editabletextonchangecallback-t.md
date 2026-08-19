# EditableTextOnChangeCallback

```TypeScript
declare type EditableTextOnChangeCallback = (value: string, previewText?: PreviewText, options?: TextChangeOptions) => void
```

输入内容发生变化时，触发该回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type EditableTextOnChangeCallback = (value: string, previewText?: PreviewText, options?: TextChangeOptions) => void--><!--Device-unnamed-declare type EditableTextOnChangeCallback = (value: string, previewText?: PreviewText, options?: TextChangeOptions) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | Text displayed in the text box. |
| previewText | [PreviewText](arkts-arkui-previewtext-i.md) | 否 | Information about the preview text, including its start position and text content. |
| options | [TextChangeOptions](arkts-arkui-textchangeoptions-i.md) | 否 | Information about the text change, including the selection range, text displayed in the text box, and preview text. |

