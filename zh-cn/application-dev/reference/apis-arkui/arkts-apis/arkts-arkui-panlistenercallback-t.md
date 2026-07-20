# PanListenerCallback

```TypeScript
declare type PanListenerCallback = (event: GestureEvent, current: GestureRecognizer, node?: FrameNode) => void
```

Pan手势事件监听函数类型。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type PanListenerCallback = (event: GestureEvent, current: GestureRecognizer, node?: FrameNode) => void--><!--Device-unnamed-declare type PanListenerCallback = (event: GestureEvent, current: GestureRecognizer, node?: FrameNode) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [GestureEvent](arkts-arkui-gestureevent-i.md) | 是 | 触发事件监听的手势事件的相关信息。  |
| current | [GestureRecognizer](arkts-arkui-gesturerecognizer-c.md) | 是 | 触发事件监听的手势识别器的相关信息。  |
| node | [FrameNode](../arkts-components/arkts-arkui-framenode-t.md) | 否 | 触发事件监听的手势事件所绑定的组件。  |

