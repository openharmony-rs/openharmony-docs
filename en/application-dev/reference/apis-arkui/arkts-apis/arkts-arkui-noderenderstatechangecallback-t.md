# NodeRenderStateChangeCallback

```TypeScript
export declare type NodeRenderStateChangeCallback = (state: NodeRenderState, node?: FrameNode) => void
```

Defines the callback type for listening for the rendering state of a specific node in **UIObserver**.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-unnamed-export declare type NodeRenderStateChangeCallback = (state: NodeRenderState, node?: FrameNode) => void--><!--Device-unnamed-export declare type NodeRenderStateChangeCallback = (state: NodeRenderState, node?: FrameNode) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| state | [NodeRenderState](arkts-arkui-arkui-uicontext-noderenderstate-e.md) | Yes | Current render state of the node, which indicates whether the monitored node is in a renderable state. |
| node | [FrameNode](arkts-arkui-framenode-c.md) | No | Component that triggers the render state change listener. When you need to obtain the node information of the component whose render state has changed, you can obtain it through this parameter. If the component is released, **null** is returned. If this parameter is not passed, the default value is **undefined**. |
