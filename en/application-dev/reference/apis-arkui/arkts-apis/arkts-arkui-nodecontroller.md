# NodeController

## Summary

### Classes

| Name | Description |
| --- | --- |
| [NodeController](arkts-arkui-nodecontroller-c.md) | The **NodeController** module provides APIs for managing custom nodes, such as creating, showing, and updating custom nodes, and APIs for mounting custom nodes to a NodeContainer component. |

## Examples

```TypeScript
### Example 1: Adding Lifecycle Callbacks for Node Layout, Touch, Attachment, and Detachment Events

This example demonstrates how to implement lifecycle callbacks of the NodeContainer component using aboutToResize and onTouchEvent for node layout and touch event receiving.

It implements lifecycle callbacks for the NodeContainer node attachment to the main node tree and detachment from the main node tree through aboutToAppear and aboutToDisappear.

It also shows how to mount a BuilderNode using NodeController.


```

```TypeScript
### Example 2: Implementing Lifecycle Callbacks for Node Binding/Unbinding and Tree Attachment/Detachment

This example demonstrates how to implement lifecycle of callbacks of the NodeContainer component using onAttach and onDetach when it is attached to or detached from the main node tree.

It implements lifecycle callbacks using onWillBind, onWillUnbind, onBind, and onUnbind when it is bound or unbound.
```
