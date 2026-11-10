# NodeSensitiveInputCallback

```TypeScript
export declare type NodeSensitiveInputCallback = (info: NodeSensitiveInputInfo, node?: FrameNode) => void
```

Defines the callback type for listening for input events of a specific node.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-unnamed-export declare type NodeSensitiveInputCallback = (info: NodeSensitiveInputInfo, node?: FrameNode) => void--><!--Device-unnamed-export declare type NodeSensitiveInputCallback = (info: NodeSensitiveInputInfo, node?: FrameNode) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [NodeSensitiveInputInfo](arkts-arkui-arkui-uicontext-nodesensitiveinputinfo-i.md) | Yes | Information about the input event delivered to the node. |
| node | [FrameNode](arkts-arkui-framenode-c.md) | No | Component that receives the input event; returns **null** if the component has been released. |
