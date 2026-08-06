# OnTextSelectionChangeCallback

```TypeScript
export type OnTextSelectionChangeCallback = (selectionStart: int, selectionEnd: int) => void
```

文本选择变化回调或光标位置变化回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnTextSelectionChangeCallback = (selectionStart: int, selectionEnd: int) => void--><!--Device-unnamed-export type OnTextSelectionChangeCallback = (selectionStart: int, selectionEnd: int) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectionStart | int | 是 | 所选文本的起始位置，文字的起始位置为0。  |
| selectionEnd | int | 是 | 所选文本的结束位置。  |

