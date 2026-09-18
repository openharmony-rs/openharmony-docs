# AccelerationOptions

Particle acceleration.

> **NOTE:** 
> 
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18.
> While historical version information is preserved for anonymous objects, there may be cases where the
> outer element's

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## angle

```TypeScript
angle?: ParticlePropertyOptions<number, ACC_ANGLE_UPDATER>
```

Acceleration direction (in angles).

Default value: **{range:[0.0,0.0]}**

**Type:** [ParticlePropertyOptions](arkts-arkui-particlepropertyoptions-i.md)&lt;number, ACC_ANGLE_UPDATER&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## speed

```TypeScript
speed?: ParticlePropertyOptions<number, ACC_SPEED_UPDATER>
```

Acceleration speed.

Default value: **{range:[0.0,0.0]}**

**Type:** [ParticlePropertyOptions](arkts-arkui-particlepropertyoptions-i.md)&lt;number, ACC_SPEED_UPDATER&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
