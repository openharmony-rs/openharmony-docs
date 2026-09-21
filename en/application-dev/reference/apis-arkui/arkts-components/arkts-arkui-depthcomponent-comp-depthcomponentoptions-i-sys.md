# DepthComponentOptions (System API)

```TypeScript
declare interface DepthComponentOptions
```

Defines the options of DepthComponent.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## colorSpace

```TypeScript
colorSpace?: import('../api/@ohos.graphics.colorSpaceManager').default.ColorSpace
```

Color space of the background.

**Type:** import('../api/@ohos.graphics.colorSpaceManager').default.ColorSpace

**Default:** colorSpaceManager.ColorSpace.SRGB

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## render3DScale

```TypeScript
render3DScale?: number
```

Scale factor for 3D rendering window, applied to both width and height. The value range is (0.0, 1.0]. Values outside this range are invalid and the default value is used.

**Type:** number

**Default:** 1.0

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
