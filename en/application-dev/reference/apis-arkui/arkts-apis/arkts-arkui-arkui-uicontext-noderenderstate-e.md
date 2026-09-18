# NodeRenderState

An enumeration type that identifies the current node's rendering state. The UI components used in the application are automatically managed by the system and controlled for participation in graphical rendering by either mounting them onto the render tree or removing them from it. Only nodes that participate in graphical rendering have the potential to be displayed. However, participating in rendering does not equal to the node's visibility, as there may be many occlusion scenarios in the actual implementation of the application. Nevertheless, if a node does not participate in rendering, it will definitely not be visible.

**Since:** 20

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ABOUT_TO_RENDER_IN

```TypeScript
ABOUT_TO_RENDER_IN = 0
```

The node has been mount on to the render tree and will soon be rendered. Generally, after the next frame, the user will be able to see this node. However, this is not always the case, as in reality, the node may be occluded by other nodes, meaning it is rendered but not be visible. When registering a listener for the render state using the UIObserver interface, the system will immediately trigger the callback once, and the state notified at this time typically represents the current state.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ABOUT_TO_RENDER_OUT

```TypeScript
ABOUT_TO_RENDER_OUT = 1
```

The node has been removed from the render tree and will no longer be rendered shortly. Generally speaking, after the next frame, the user will no longer be able to see this node. When registering a listener for the render state using the UIObserver interface, the system will immediately trigger the callback once, and the state notified at this time typically represents the current state.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
