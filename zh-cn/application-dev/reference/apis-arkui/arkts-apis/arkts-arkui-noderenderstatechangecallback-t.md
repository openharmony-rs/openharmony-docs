# NodeRenderStateChangeCallback

```TypeScript
export declare type NodeRenderStateChangeCallback = (state: NodeRenderState, node?: FrameNode) => void
```

定义UIObserver监听指定节点渲染状态时使用的回调类型。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare type NodeRenderStateChangeCallback = (state: NodeRenderState, node?: FrameNode) => void--><!--Device-unnamed-export declare type NodeRenderStateChangeCallback = (state: NodeRenderState, node?: FrameNode) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | the node's render state  |
| node | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | the information of frameNode  |

