# DepthComponentOptions (System API)

```TypeScript
declare interface DepthComponentOptions
```

Provides configuration options of **DepthComponent**.

**Since:** 26.0.0

<!--Device-unnamed-declare interface DepthComponentOptions--><!--Device-unnamed-declare interface DepthComponentOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## colorSpace

```TypeScript
colorSpace?: import('../api/@ohos.graphics.colorSpaceManager').default.ColorSpace
```

Color space of the rendering surface. When set, the color space information is applied to the underlying rendering surface. When not set, no color space information is applied, and the rendering surface retains the default color space. Default value: **colorSpaceManager.ColorSpace.SRGB**.

**Type:** import('../api/@ohos.graphics.colorSpaceManager').default.ColorSpace

**Default:** colorSpaceManager.ColorSpace.SRGB

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DepthComponentOptions-colorSpace?: import('../api/@ohos.graphics.colorSpaceManager').default.ColorSpace--><!--Device-DepthComponentOptions-colorSpace?: import('../api/@ohos.graphics.colorSpaceManager').default.ColorSpace-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## depthSpace

```TypeScript
depthSpace?: DepthSpaceType
```

Depth space type.

**Type:** [DepthSpaceType](arkts-arkui-depthcomponent-comp-depthspacetype-e-sys.md)

**Default:** DepthSpace.INSTANCE

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DepthComponentOptions-depthSpace?: DepthSpaceType--><!--Device-DepthComponentOptions-depthSpace?: DepthSpaceType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## render3DScale

```TypeScript
render3DScale?: number
```

Scale factor of the 3D rendering window, applied to both width and height. Value range: (0.0, 1.0]. Values outside this range are invalid (the previous value is inherited; if no value has been set, the default value is used). Default value: **1.0**.

**Type:** number

**Default:** 1.0

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DepthComponentOptions-render3DScale?: double--><!--Device-DepthComponentOptions-render3DScale?: double-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
