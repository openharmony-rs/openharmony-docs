# OnTextSelectionChangeCallback

```TypeScript
declare type OnTextSelectionChangeCallback = (selectionStart: number, selectionEnd: number) => void
```

文本选择变化回调或光标位置变化回调。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type OnTextSelectionChangeCallback = (selectionStart: number, selectionEnd: number) => void--><!--Device-unnamed-declare type OnTextSelectionChangeCallback = (selectionStart: number, selectionEnd: number) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectionStart | number | 是 | 所选文本的起始位置，文字的起始位置为0。 |
| selectionEnd | number | 是 | 所选文本的结束位置。 |

