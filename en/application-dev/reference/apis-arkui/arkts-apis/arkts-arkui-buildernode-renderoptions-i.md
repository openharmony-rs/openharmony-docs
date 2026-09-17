# RenderOptions

Provides optional parameters for creating a BuilderNode.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selfIdealSize

```TypeScript
selfIdealSize?: Size
```

Ideal size of the node.

Default value: **{ width: 0, height: 0 }**.

**Type:** Size

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## surfaceId

```TypeScript
surfaceId?: string
```

Surface ID of the texture receiver. Typically, the texture receiver is [OH_NativeImage](../../../reference/apis-arkgraphics2d/capi-oh-nativeimage-oh-nativeimage.md).

This parameter is effective only when **type** is set to **NodeRenderType.RENDER_TYPE_TEXTURE**.

Default value: **""**.

**Type:** string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type?: NodeRenderType
```

Rendering type of the node.

Default value: **NodeRenderType.RENDER_TYPE_DISPLAY**.

**Type:** [NodeRenderType](arkts-arkui-buildernode-noderendertype-e.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
