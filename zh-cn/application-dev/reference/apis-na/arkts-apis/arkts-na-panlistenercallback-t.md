# PanListenerCallback

```TypeScript
type PanListenerCallback = (event: GestureEvent, current: GestureRecognizer, node?: FrameNode) => void
```

定义UIObserver监听拖拽事件时使用的回调类型。 event表示拖拽事件的信息。 node表示接收事件的frameNode。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-type PanListenerCallback = (event: GestureEvent, current: GestureRecognizer, node?: FrameNode) => void--><!--Device-unnamed-type PanListenerCallback = (event: GestureEvent, current: GestureRecognizer, node?: FrameNode) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [GestureEvent](../../apis-arkui/arkts-apis/arkts-arkui-gesture-gestureevent-i.md) | 是 | the information of pan event |
| current | [GestureRecognizer](../../apis-arkui/arkts-apis/arkts-arkui-gesture-gesturerecognizer-c.md) | 是 | the information of panRecognizer |
| node | FrameNode | 否 | the information of frameNode |

