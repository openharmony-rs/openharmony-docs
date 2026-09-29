# ParticleOptions

```TypeScript
interface ParticleOptions<
  PARTICLE extends ParticleType,
  COLOR_UPDATER extends ParticleUpdater,
  OPACITY_UPDATER extends ParticleUpdater,
  SCALE_UPDATER extends ParticleUpdater,
  ACC_SPEED_UPDATER extends ParticleUpdater,
  ACC_ANGLE_UPDATER extends ParticleUpdater,
  SPIN_UPDATER extends ParticleUpdater
>
```

Sets particle parameters.

**Since:** 10

<!--Device-unnamed-interface ParticleOptions<  PARTICLE extends ParticleType,  COLOR_UPDATER extends ParticleUpdater,  OPACITY_UPDATER extends ParticleUpdater,  SCALE_UPDATER extends ParticleUpdater,  ACC_SPEED_UPDATER extends ParticleUpdater,  ACC_ANGLE_UPDATER extends ParticleUpdater,  SPIN_UPDATER extends ParticleUpdater>--><!--Device-unnamed-interface ParticleOptions<  PARTICLE extends ParticleType,  COLOR_UPDATER extends ParticleUpdater,  OPACITY_UPDATER extends ParticleUpdater,  SCALE_UPDATER extends ParticleUpdater,  ACC_SPEED_UPDATER extends ParticleUpdater,  ACC_ANGLE_UPDATER extends ParticleUpdater,  SPIN_UPDATER extends ParticleUpdater>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## acceleration

```TypeScript
acceleration?: AccelerationOptions<ACC_SPEED_UPDATER, ACC_ANGLE_UPDATER>
```

Particle acceleration configuration.

**Note:** 

**speed** indicates the acceleration magnitude, and angle indicates the acceleration direction (unit: degree).

Default value: **{ speed:{range:[0.0,0.0]},angle:{range:[0.0,0.0]}** }

**Type:** [AccelerationOptions](arkts-arkui-particle-comp-accelerationoptions-i.md)&lt;ACC_SPEED_UPDATER, ACC_ANGLE_UPDATER&gt;

**Default:** {speed:{range:[0,0]};angle:{range:[0,0]}}

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ParticleOptions-acceleration?: AccelerationOptions<ACC_SPEED_UPDATER, ACC_ANGLE_UPDATER>--><!--Device-ParticleOptions-acceleration?: AccelerationOptions<ACC_SPEED_UPDATER, ACC_ANGLE_UPDATER>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ParticleColorPropertyOptions<COLOR_UPDATER>
```

Particle color configuration.

**Note:** 

Default value: **{ range:[Color.White,Color.White] }**. Image particles do not support setting the color.

**Type:** [ParticleColorPropertyOptions](arkts-arkui-particle-comp-particlecolorpropertyoptions-i.md)&lt;COLOR_UPDATER&gt;

**Default:** {range:['#FFFFFF','#FFFFFF']}

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ParticleOptions-color?: ParticleColorPropertyOptions<COLOR_UPDATER>--><!--Device-ParticleOptions-color?: ParticleColorPropertyOptions<COLOR_UPDATER>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## emitter

```TypeScript
emitter: EmitterOptions<PARTICLE>
```

Particle emitter configuration.

**Type:** [EmitterOptions](arkts-arkui-particle-comp-emitteroptions-i.md)&lt;PARTICLE&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ParticleOptions-emitter: EmitterOptions<PARTICLE>--><!--Device-ParticleOptions-emitter: EmitterOptions<PARTICLE>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## opacity

```TypeScript
opacity?: ParticlePropertyOptions<number, OPACITY_UPDATER>
```

Particle opacity configuration.

Default value: **{ range:[1.0,1.0] }**

**Type:** [ParticlePropertyOptions](arkts-arkui-particle-comp-particlepropertyoptions-i.md)&lt;number, OPACITY_UPDATER&gt;

**Default:** {range:[1.0,1.0]}

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ParticleOptions-opacity?: ParticlePropertyOptions<number, OPACITY_UPDATER>--><!--Device-ParticleOptions-opacity?: ParticlePropertyOptions<number, OPACITY_UPDATER>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scale

```TypeScript
scale?: ParticlePropertyOptions<number, SCALE_UPDATER>
```

Particle size configuration.

Default value: **{ range:[1.0,1.0] }**

**Type:** [ParticlePropertyOptions](arkts-arkui-particle-comp-particlepropertyoptions-i.md)&lt;number, SCALE_UPDATER&gt;

**Default:** {range:[1.0,1.0]}

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ParticleOptions-scale?: ParticlePropertyOptions<number, SCALE_UPDATER>--><!--Device-ParticleOptions-scale?: ParticlePropertyOptions<number, SCALE_UPDATER>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## spin

```TypeScript
spin?: ParticlePropertyOptions<number, SPIN_UPDATER>
```

Particle spin angle configuration, unit is degree (°).

Default value: **{range:[0.0,0.0]}**

Direction: a positive value indicates clockwise rotation, and a negative value indicates counterclockwise rotation.

**Type:** [ParticlePropertyOptions](arkts-arkui-particle-comp-particlepropertyoptions-i.md)&lt;number, SPIN_UPDATER&gt;

**Default:** {range:[0,0]}

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ParticleOptions-spin?: ParticlePropertyOptions<number, SPIN_UPDATER>--><!--Device-ParticleOptions-spin?: ParticlePropertyOptions<number, SPIN_UPDATER>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## velocity

```TypeScript
velocity?: VelocityOptions
```

Particle velocity configuration.

**Note:** 

**speed** indicates the velocity magnitude. **angle** indicates the direction of the velocity (unit: degree), with the geometric center of the element as the coordinate origin and the horizontal direction as the X-axis. A positive value indicates clockwise rotation angle.

Default value: **{ speed:[0.0,0.0],angle:[0.0,0.0] }**

**Type:** [VelocityOptions](arkts-arkui-particle-comp-velocityoptions-i.md)

**Default:** {speed:[0,0];angle:[0,0]}

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ParticleOptions-velocity?: VelocityOptions--><!--Device-ParticleOptions-velocity?: VelocityOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
