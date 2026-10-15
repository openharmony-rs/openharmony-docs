# SurfaceConfig

```TypeScript
declare interface SurfaceConfig
```

Describes whether the surface held by the XComponent component is opaque during rendering.

**Since:** 22

<!--Device-unnamed-declare interface SurfaceConfig--><!--Device-unnamed-declare interface SurfaceConfig-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isOpaque

```TypeScript
isOpaque?: boolean
```

Whether the Surface held by the XComponent needs to be treated as opaque during rendering. If this parameter is not set, the default value is false, which means that the transparency of the pixels of the content drawn on the Surface is applied during rendering.<br>The value true means that the Surface needs to be treated as opaque, and false means the opposite.<br>Default value: false

**Type:** boolean

**Default:** false

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-SurfaceConfig-isOpaque?: boolean--><!--Device-SurfaceConfig-isOpaque?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
