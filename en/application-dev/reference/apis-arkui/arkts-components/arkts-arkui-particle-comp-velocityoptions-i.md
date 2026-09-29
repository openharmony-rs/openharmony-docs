# VelocityOptions

```TypeScript
declare interface VelocityOptions
```

Particle velocity.

> **NOTE:** 
> 
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18.
> While historical version information is preserved for anonymous objects, there may be cases where the outer element
> 's

**Since:** 18

<!--Device-unnamed-declare interface VelocityOptions--><!--Device-unnamed-declare interface VelocityOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## angle

```TypeScript
angle: ParticleTuple<number, number>
```

Direction of velocity, in degrees (°). With the geometric center of the element as the coordinate origin and the horizontal direction as the X-axis, a positive value indicates a clockwise rotation angle.

Default value: **{range:[0.0,0.0]}**

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** [ParticleTuple](arkts-arkui-particle-comp-particletuple-t.md)&lt;number, number&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-VelocityOptions-angle: ParticleTuple<number, number>--><!--Device-VelocityOptions-angle: ParticleTuple<number, number>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## speed

```TypeScript
speed: ParticleTuple<number, number>
```

Velocity magnitude.

Default value: **{range:[0.0,0.0]}**

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** [ParticleTuple](arkts-arkui-particle-comp-particletuple-t.md)&lt;number, number&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-VelocityOptions-speed: ParticleTuple<number, number>--><!--Device-VelocityOptions-speed: ParticleTuple<number, number>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
