# OnVisibleIndexesChangeCallback

```TypeScript
export type OnVisibleIndexesChangeCallback = (start: int, end: int) => void
```

Defines the callback type used in OnVisibleIndexesChange.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnVisibleIndexesChangeCallback = (start: int, end: int) => void--><!--Device-unnamed-export type OnVisibleIndexesChangeCallback = (start: int, end: int) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | int | 是 | the first index in visible content.  |
| end | int | 是 | the last index in visible content.  |

