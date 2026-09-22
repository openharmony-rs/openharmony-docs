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

Defines the ParticleOptions Interface.

@interface ParticleOptions

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## acceleration

```TypeScript
acceleration?: AccelerationOptions<ACC_SPEED_UPDATER, ACC_ANGLE_UPDATER>
```

Particle acceleration.

**NOTE:** 

**speed** indicates the acceleration speed, and **angle** indicates the acceleration direction (in angles).

Default value: **{ speed:{range:[0.0,0.0]},angle:{range:[0.0,0.0]} }**

**Type:** [AccelerationOptions](arkts-arkui-particle-comp-accelerationoptions-i.md)&lt;ACC_SPEED_UPDATER, ACC_ANGLE_UPDATER&gt;

**Default:** {speed:{range:[0,0]};angle:{range:[0,0]}}

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ParticleColorPropertyOptions<COLOR_UPDATER>
```

Particle color.

**NOTE:** 

Default value: **{ range:[Color.White,Color.White] }.** Colors cannot be set for image particles.

**Type:** [ParticleColorPropertyOptions](arkts-arkui-particle-comp-particlecolorpropertyoptions-i.md)&lt;COLOR_UPDATER&gt;

**Default:** {range:['#FFFFFF','#FFFFFF']}

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## emitter

```TypeScript
emitter: EmitterOptions<PARTICLE>
```

Particle emitter.

**Type:** [EmitterOptions](arkts-arkui-particle-comp-emitteroptions-i.md)&lt;PARTICLE&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## opacity

```TypeScript
opacity?: ParticlePropertyOptions<number, OPACITY_UPDATER>
```

Particle opacity.

Default value: **{ range:[1.0,1.0] }**

**Type:** [ParticlePropertyOptions](arkts-arkui-particle-comp-particlepropertyoptions-i.md)&lt;number, OPACITY_UPDATER&gt;

**Default:** {range:[1.0,1.0]}

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scale

```TypeScript
scale?: ParticlePropertyOptions<number, SCALE_UPDATER>
```

Particle scale.

Default value: **{ range:[1.0,1.0] }**

**Type:** [ParticlePropertyOptions](arkts-arkui-particle-comp-particlepropertyoptions-i.md)&lt;number, SCALE_UPDATER&gt;

**Default:** {range:[1.0,1.0]}

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## spin

```TypeScript
spin?: ParticlePropertyOptions<number, SPIN_UPDATER>
```

Particle spin angle.

Default value: **{range:[0.0,0.0]}**

Direction: A positive number indicates clockwise spinning, and a negative number indicates anticlockwise spinning.

**Type:** [ParticlePropertyOptions](arkts-arkui-particle-comp-particlepropertyoptions-i.md)&lt;number, SPIN_UPDATER&gt;

**Default:** {range:[0,0]}

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## velocity

```TypeScript
velocity?: VelocityOptions
```

Particle velocity.

**NOTE:** 

**speed** indicates the time rate at which the particle moves. **angle** indicates the direction (in angles) in which the particle moves, with the geometric center of the element as the coordinate origin and the horizontal direction as the x-axis. A positive number indicates clockwise rotation.

Default value: **{speed: [0.0,0.0],angle: [0.0,0.0] }**

**Type:** [VelocityOptions](arkts-arkui-particle-comp-velocityoptions-i.md)

**Default:** {speed:[0,0];angle:[0,0]}

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
