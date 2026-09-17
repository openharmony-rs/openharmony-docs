# SpotLight

Spotlight, which inherits from Light.

A spotlight emits a conical beam of light in a specific direction, with the intensity of the light decaying according to the angles defined by the innerAngle and outerAngle parameters. Like a point light, a spotlight's intensity also diminishes with distance from the source.

> **NOTE:** 
> 
> Ensure that the innerAngle and outerAngle values are proper.
> If the value set for outerAngle is greater than PI/2, it is forcibly set to PI/2 internally.
> If the value set for outerAngle is less than innerAngle, it is forcibly set to innerAngle internally.

@extends Light @interface SpotLight

**Inheritance/Implementation:** SpotLight extends [Light](arkts-arkgraphics3d-scenenodes-light-i.md)

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## innerAngle

```TypeScript
innerAngle?: number
```

Angle from the center of the spotlight to the start of the decay, corresponding to the semi-apex angle of the cone, within which the light intensity does not decay with angle. The unit is radian (rad), and the default value is 0. The value must be greater than or equal to 0 and less than or equal to outerAngle.

**Type:** number

**Default:** 0

**Since:** 23

**System capability:** SystemCapability.ArkUi.Graphics3D

## outerAngle

```TypeScript
outerAngle?: number
```

Angle from the center of the spotlight to the end of the decay, corresponding to the semi-apex angle of the cone, beyond which there is no light intensity. The unit is radian (rad), and the default value is PI/4. The value must be greater than or equal to innerAngle and less than or equal to PI/2.

**Type:** number

**Default:** PI / 4.0

**Since:** 23

**System capability:** SystemCapability.ArkUi.Graphics3D
