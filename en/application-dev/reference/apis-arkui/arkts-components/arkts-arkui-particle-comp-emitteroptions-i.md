# EmitterOptions

```TypeScript
interface EmitterOptions<PARTICLE extends ParticleType>
```

Particle emitter configuration.

@interface EmitterOptions

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## annulusRegion

```TypeScript
annulusRegion?: ParticleAnnulusRegion
```

Annulus emitter parameters. This parameter takes effect only when the emitter shape is annulus (that is, the shape parameter is ParticleEmitterShape.ANNULUS). For an annulus emitter, the shape information must be specified by the annulusRegion parameter, and the position and size parameters do not take effect.

**Type:** [ParticleAnnulusRegion](arkts-arkui-particle-comp-particleannulusregion-i.md)

**Default:** {innerRadius:LengthMetrics.vp(0),outerRadius:LengthMetrics.vp(0)}

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## emitRate

```TypeScript
emitRate?: number
```

Emit rate (that is, the number of particles emitted per second).

Default value: **5**. If the value specified is less than 0, the default value is used.

The **emitRate** value can significantly impact performance when it exceeds 5000; you are advised to set it to be less than 5000.

**Type:** number

**Default:** 5

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## particle

```TypeScript
particle: EmitterParticleOptions<PARTICLE>
```

Particle configuration.

- **type**: particle type, which can be **IMAGE** or **POINT**.  
- **config**: configuration of the particle type.  
- The value type of **config** is subject to the value of **type**.

1. If the type is ParticleType.POINT, the config type is [PointParticleParameters](arkts-arkui-particle-comp-pointparticleparameters-i.md).
2. If the type is ParticleType.IMAGE, the config type is [ImageParticleParameters](arkts-arkui-particle-comp-imageparticleparameters-i.md).

- **count**: number of particles. The value is greater than or equal to -1. The value **-1** indicates that the  
number of particles is infinite.  
- **lifetime**: lifetime of a single particle. The default value is **1000** (that is, 1000 ms, 1s). The value is  
greater than or equal to -1. The value **-1** indicates that the lifetime of the particle is infinite. If the value specified is less than **-1**, the default value is used.

Note: If you do not want the animation to keep playing, you are advised not to set the lifetime to –1, which may greatly affect the performance.

The **lifeTimeRange** parameter indicates the range of the particle lifetime. After this parameter is set, the lifetime of a particle is a random integer within the range of [lifetime – lifeTimeRange, lifetime + lifeTimeRange]. The default value of lifeTimeRange is 0. The value ranges from 0 to positive infinity. If it is set to a negative value, the default value is used.

**Type:** [EmitterParticleOptions](arkts-arkui-particle-comp-emitterparticleoptions-i.md)&lt;PARTICLE&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## position

```TypeScript
position?: ParticleTuple<Dimension, Dimension>
```

Emitter position (distance from the upper left corner of the component). The first parameter indicates the relative offset along the x-axis, and the second parameter indicates the relative offset along the y-axis.

Default value: **[0.0, 0.0]**

**Type:** [ParticleTuple](arkts-arkui-particle-comp-particletuple-t.md)&lt;[Dimension](../arkts-apis/arkts-arkui-dimension-t.md), [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)&gt;

**Default:** [0,0]

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shape

```TypeScript
shape?: ParticleEmitterShape
```

Shape of emitter.

Default value: ParticleEmitterShape.RECTANGLE

**Type:** [ParticleEmitterShape](arkts-arkui-particle-comp-particleemittershape-e.md)

**Default:** ParticleEmitterShape.RECTANGLE

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: ParticleTuple<Dimension, Dimension>
```

Size of the emit window. The first parameter indicates the emitter width, and the second parameter indicates the emitter height.

Default value: **['100%','100%']** (that is, the emission window occupies the entire Particle component.)

**Type:** [ParticleTuple](arkts-arkui-particle-comp-particletuple-t.md)&lt;[Dimension](../arkts-apis/arkts-arkui-dimension-t.md), [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)&gt;

**Default:** ['100%','100%']

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
