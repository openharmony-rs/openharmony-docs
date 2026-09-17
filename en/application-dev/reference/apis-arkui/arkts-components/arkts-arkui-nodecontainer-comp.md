# NodeContainer

**NodeContainer** is a basic component for mounting custom nodes (such as FrameNode or BuilderNode) and dynamically managing node attachment and detachment through [NodeController](../arkts-apis/arkts-arkui-nodecontroller-c.md). This component does not support adding trailing child components and requires a [NodeController](../arkts-apis/arkts-arkui-nodecontroller-c.md) instance for operation. It must be used in combination with **NodeController**.

> **NOTE** > > Only custom FrameNodes or the root FrameNode obtained from a > BuilderNode can be attached to this component. > > [Proxy nodes](../arkts-apis/arkts-arkui-framenode-c.md#ismodifiable) of built-in system components obtained through > querying cannot be attached to this component. > > This component does not work with the attribute modifier. > > A [UIContext](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md) instance is used to construct the node tree for this component. During > instance switching, the input parameter of the > [makeNode](../arkts-apis/arkts-arkui-nodecontroller-c.md#makenode) callback method of the bound > [NodeController](../arkts-apis/arkts-arkui-nodecontroller-c.md) may be **undefined** due to instance mismatch. > Therefore, this component does not support cross-instance node reuse. > > When this component is not destroyed, the unmounting of its mounted child nodes will not be triggered.

## NodeContainer

```TypeScript
NodeContainer(controller: import('../api/@ohos.arkui.node').NodeController)
```

Creates a **NodeContainer** component.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| controller | import('../api/@ohos.arkui.node').NodeController | Yes | **NodeController** instance used to control the upper and lower tree nodes in the **NodeContainer**. It represents the lifecycle of the **NodeContainer**. |

## Summary

## Examples

```TypeScript
This example demonstrates how to mount a BuilderNode through NodeController.
```
