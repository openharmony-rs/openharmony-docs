# SpatialEffectParams (System API)

```TypeScript
declare interface SpatialEffectParams
```

Spatial effect params.

**Since:** 26.0.0

<!--Device-unnamed-declare interface SpatialEffectParams--><!--Device-unnamed-declare interface SpatialEffectParams-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## occlusionWeight

```TypeScript
occlusionWeight?: number
```

Occlusion weight for spatial effect. <br>Value range:[0, 1].Default value:0

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SpatialEffectParams-occlusionWeight?: double--><!--Device-SpatialEffectParams-occlusionWeight?: double-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## position

```TypeScript
position: SpatialPosition | number
```

Spatial position defined by corner points or depth value.

**Type:** [SpatialPosition](arkts-arkui-common-comp-spatialposition-i-sys.md) &#124; number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SpatialEffectParams-position: SpatialPosition | double--><!--Device-SpatialEffectParams-position: SpatialPosition | double-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
