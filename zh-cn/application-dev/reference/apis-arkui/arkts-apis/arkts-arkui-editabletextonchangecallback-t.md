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
| value | string | 是 | 文本框内正式上屏的文本内容。  |
| previewText | [PreviewText](arkts-arkui-previewtext-i.md) | 否 | 预上屏文本信息，包含预上屏起始位置和文本内容。  |
| options | [TextChangeOptions](arkts-arkui-textchangeoptions-i.md) | 否 | 文本内容变化信息，包含文本的选中区范围、文本框内正式上屏的文本内容、预上屏文本内容。 |

