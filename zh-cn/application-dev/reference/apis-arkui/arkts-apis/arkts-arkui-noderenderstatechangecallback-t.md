# NodeRenderStateChangeCallback

```TypeScript
export declare type NodeRenderStateChangeCallback = (state: NodeRenderState, node?: FrameNode) => void
```

定义了用于在UIObserver中监控某个特定节点渲染状态的回调类型。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export declare type NodeRenderStateChangeCallback = (state: NodeRenderState, node?: FrameNode) => void--><!--Device-unnamed-export declare type NodeRenderStateChangeCallback = (state: NodeRenderState, node?: FrameNode) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | [NodeRenderState](arkts-arkui-arkui-uicontext-noderenderstate-e.md) | 是 | 触发事件监听的手势事件的相关信息。  |
| node | [FrameNode](../arkts-components/arkts-arkui-framenode-t.md) | 否 | 触发事件监听的手势事件所绑定的组件，如果组件被释放将返回null。  |

