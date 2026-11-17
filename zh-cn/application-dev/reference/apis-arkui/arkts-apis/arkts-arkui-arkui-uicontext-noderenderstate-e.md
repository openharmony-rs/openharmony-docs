# NodeRenderState

```TypeScript
export const enum NodeRenderState
```

节点的渲染状态。

**起始版本：** 20

<!--Device-unnamed-export const enum NodeRenderState--><!--Device-unnamed-export const enum NodeRenderState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ABOUT_TO_RENDER_IN

```TypeScript
ABOUT_TO_RENDER_IN = 0
```

该节点已挂载到渲染树上，通常会在下一帧渲染并对用户可见，但节点被渲染不代表一定可见。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

<!--Device-NodeRenderState-ABOUT_TO_RENDER_IN = 0--><!--Device-NodeRenderState-ABOUT_TO_RENDER_IN = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ABOUT_TO_RENDER_OUT

```TypeScript
ABOUT_TO_RENDER_OUT = 1
```

该节点已从渲染树中删除，一般下一帧不会被渲染，用户将不会看到此节点。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

<!--Device-NodeRenderState-ABOUT_TO_RENDER_OUT = 1--><!--Device-NodeRenderState-ABOUT_TO_RENDER_OUT = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
