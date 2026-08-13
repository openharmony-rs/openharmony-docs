# OnWillStopDraggingCallback

```TypeScript
export type OnWillStopDraggingCallback = (velocity: double) => void
```

On scroll callback using in scrollable onWillStopDragging.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnWillStopDraggingCallback = (velocity: double) => void--><!--Device-unnamed-export type OnWillStopDraggingCallback = (velocity: double) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| velocity | double | 是 | The veolicity of the scroll view at the moment the touch was released. <br>Unit: vp/s. |

