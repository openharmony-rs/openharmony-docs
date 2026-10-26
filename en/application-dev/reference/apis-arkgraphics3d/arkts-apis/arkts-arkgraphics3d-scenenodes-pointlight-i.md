# PointLight

```TypeScript
export interface PointLight extends Light
```

Point light.

A point light emits light uniformly in all directions from a single point in space.

**Inheritance/Implementation:** PointLight extends [Light](arkts-arkgraphics3d-scenenodes-light-i.md)

**Since:** 26.1.0

<!--Device-unnamed-export interface PointLight extends Light--><!--Device-unnamed-export interface PointLight extends Light-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## range

```TypeScript
range?: number
```

Maximum distance that the point light affects. Beyond this range, the light intensity is zero. The unit is the scene unit (such as cm, m, and km) in the world coordinate system. The value must be greater than 0. If this parameter is not set, a safe range is calculated automatically based on the light intensity. The value must be greater than 0. Default value: Refer to the calculated value of intensity.

**Type:** number

**Default:** need to be decided

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PointLight-range?: double--><!--Device-PointLight-range?: double-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D
