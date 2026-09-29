# DepthLightParams (System API)

```TypeScript
declare interface DepthLightParams
```

Provides lighting parameters.

**Since:** 26.0.0

<!--Device-unnamed-declare interface DepthLightParams--><!--Device-unnamed-declare interface DepthLightParams-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## color

```TypeScript
color: DepthColorRGB
```

Lighting color.

**Type:** [DepthColorRGB](arkts-arkui-common-comp-depthcolorrgb-i-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DepthLightParams-color: DepthColorRGB--><!--Device-DepthLightParams-color: DepthColorRGB-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## direction

```TypeScript
direction: DepthVector3
```

Lighting direction vector, without a unit. The value indicates the coordinates in 3D space.

**Type:** [DepthVector3](arkts-arkui-common-comp-depthvector3-i-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DepthLightParams-direction: DepthVector3--><!--Device-DepthLightParams-direction: DepthVector3-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## intensity

```TypeScript
intensity: number
```

Lighting intensity, without a unit. The value range is [0, +∞).

The recommended value range is [0, 1]. When set to 0, there is no light.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DepthLightParams-intensity: double--><!--Device-DepthLightParams-intensity: double-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
