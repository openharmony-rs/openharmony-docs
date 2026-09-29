# GravityCenterOptions (System API)

```TypeScript
declare interface GravityCenterOptions
```

Defines the parameters of the center of gravity.

**Since:** 26.0.0

<!--Device-unnamed-declare interface GravityCenterOptions--><!--Device-unnamed-declare interface GravityCenterOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## gravityCenter

```TypeScript
gravityCenter?: boolean
```

Specifies whether the current component is the center of gravity. <br>Default value:false.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-GravityCenterOptions-gravityCenter?: boolean--><!--Device-GravityCenterOptions-gravityCenter?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## gravityIntensity

```TypeScript
gravityIntensity?: number
```

Defines the gravitational strength of the attraction/repulsion force at the gravitational center. <br>Default value:0. <br>Negative numbers are repulsion, positive numbers are attractionn.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-GravityCenterOptions-gravityIntensity?: double--><!--Device-GravityCenterOptions-gravityIntensity?: double-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
