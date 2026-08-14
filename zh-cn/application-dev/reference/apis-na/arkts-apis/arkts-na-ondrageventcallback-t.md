# OnDragEventCallback

```TypeScript
export type OnDragEventCallback = (event: DragEvent, extraParams?: string) => void
```

The event callback function for drag and drop common interfaces.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnDragEventCallback = (event: DragEvent, extraParams?: string) => void--><!--Device-unnamed-export type OnDragEventCallback = (event: DragEvent, extraParams?: string) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [DragEvent](arkts-na-common-dragevent-i.md) | 是 | the event object indicating current drag status. |
| extraParams | string | 否 | extra information set by user or system. |

