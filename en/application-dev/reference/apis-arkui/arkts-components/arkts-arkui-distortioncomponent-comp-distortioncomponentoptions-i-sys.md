# DistortionComponentOptions (System API)

```TypeScript
declare interface DistortionComponentOptions
```

Defines the spatial distortion options.

**Since:** 26.0.0

<!--Device-unnamed-declare interface DistortionComponentOptions--><!--Device-unnamed-declare interface DistortionComponentOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## distortion

```TypeScript
distortion?: DistortionParam
```

Spatial distortion parameter that produces a distortion effect by specifying the positional relationship of the four corner points and the barrel distortion degree of the four edges. Pass this parameter when spatial distortion needs to be applied; if it is not passed, the component is rendered normally without any distortion effect.

Default value: **{ topLeft: { x:0, y:0 }, topRight: { x:1, y:0 }, bottomLeft: { x:0, y:1 }, bottomRight: { x:1, y:1 }, barrelDistortion: { x:0, y:0, z:0, w:0 } }**

**Type:** [DistortionParam](arkts-arkui-distortioncomponent-comp-distortionparam-i-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DistortionComponentOptions-distortion?: DistortionParam--><!--Device-DistortionComponentOptions-distortion?: DistortionParam-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
