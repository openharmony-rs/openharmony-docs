# ClickEventListenerCallback

```TypeScript
declare type ClickEventListenerCallback = (event: ClickEvent, node?: FrameNode) => void
```

定义了用于在UIObserver中监听点击事件的回调类型。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type ClickEventListenerCallback = (event: ClickEvent, node?: FrameNode) => void--><!--Device-unnamed-declare type ClickEventListenerCallback = (event: ClickEvent, node?: FrameNode) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [ClickEvent](../arkts-components/arkts-arkui-clickevent-i.md) | 是 | 触发事件监听的点击事件的相关信息。  |
| node | [FrameNode](../arkts-components/arkts-arkui-framenode-t.md) | 否 | 触发事件监听的点击事件所绑定的组件。  |

