# NodeRenderState

An enumeration type that identifies the current node's rendering state. The UI components used in the application are automatically managed by the system and controlled for participation in graphical rendering by either mounting them onto the render tree or removing them from it. Only nodes that participate in graphical rendering have the potential to be displayed. However, participating in rendering does not equal to the node's visibility, as there may be many occlusion scenarios in the actual implementation of the application. Nevertheless, if a node does not participate in rendering, it will definitely not be visible.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export const enum NodeRenderState--><!--Device-unnamed-export const enum NodeRenderState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ABOUT_TO_RENDER_IN

```TypeScript
ABOUT_TO_RENDER_IN = 0
```

节点已挂载到渲染树上，即将被渲染。通常在下一帧后， the user will be able to see this node. However, this is not always the case, as in reality, the node may be occluded by other nodes, meaning it is rendered but not be visible. When registering a listener for the render state using the UIObserver interface, the system will immediately trigger the callback once, and the state notified at this time typically represents the current state.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NodeRenderState-ABOUT_TO_RENDER_IN = 0--><!--Device-NodeRenderState-ABOUT_TO_RENDER_IN = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ABOUT_TO_RENDER_OUT

```TypeScript
ABOUT_TO_RENDER_OUT = 1
```

节点已从渲染树移除，即将停止渲染。通常在下一帧后， after the next frame, the user will no longer be able to see this node. When registering a listener for the render state using the UIObserver interface, the system will immediately trigger the callback once, and the state notified at this time typically represents the current state.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NodeRenderState-ABOUT_TO_RENDER_OUT = 1--><!--Device-NodeRenderState-ABOUT_TO_RENDER_OUT = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

