# OnMoveHandler

```TypeScript
export type OnMoveHandler = (from: int, to: int) => void
```

Defines the onMove callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnMoveHandler = (from: int, to: int) => void--><!--Device-unnamed-export type OnMoveHandler = (from: int, to: int) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| from | int | 是 | Index number for moving elements. |
| to | int | 是 | Target index number for moving elements. |

