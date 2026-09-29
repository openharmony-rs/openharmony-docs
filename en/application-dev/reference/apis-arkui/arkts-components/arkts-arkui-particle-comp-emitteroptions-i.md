# EmitterOptions

```TypeScript
interface EmitterOptions<PARTICLE extends ParticleType>
```

Defines the configuration options of the particle emitter.

**Since:** 10

<!--Device-unnamed-interface EmitterOptions<PARTICLE extends ParticleType>--><!--Device-unnamed-interface EmitterOptions<PARTICLE extends ParticleType>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## annulusRegion

```TypeScript
annulusRegion?: ParticleAnnulusRegion
```

Ring emitter parameter. It takes effect only when the emitter shape is annulus (that is, the **shape** parameter is **ParticleEmitterShape.ANNULUS**). For a annulus emitter, the shape information must be specified through the **annulusRegion** parameter, and **position** and **size** do not take effect. When it is not set, the emitter does not use the annulus region parameter.

**Atomic service API:** Since API version 20, this API is supported in atomic services.

**Type:** [ParticleAnnulusRegion](arkts-arkui-particle-comp-particleannulusregion-i.md)

**Default:** {innerRadius:LengthMetrics.vp(0),outerRadius:LengthMetrics.vp(0)}

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-EmitterOptions-annulusRegion?: ParticleAnnulusRegion--><!--Device-EmitterOptions-annulusRegion?: ParticleAnnulusRegion-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## emitRate

```TypeScript
emitRate?: number
```

Emission rate of the emitter (that is, the number of particles emitted per second). Default value: **5**. When the value is less than 0, the default value **5** is used. When **emitRate** exceeds 5000, performance is severely affected and the frame rate may drop significantly. It is recommended to set this parameter to a value less than 5000.

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** number

**Default:** 5

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-EmitterOptions-emitRate?: number--><!--Device-EmitterOptions-emitRate?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## particle

```TypeScript
particle: EmitterParticleOptions<PARTICLE>
```

Particle configuration.

-**type** indicates the particle type, which can be an image or a point.

-**config** indicates the configuration of the corresponding type.

-The **config** type is related to the **type** value:

1. If **type** is **ParticleType.POINT**, the **config** type is [PointParticleParameters](arkts-arkui-particle-comp-pointparticleparameters-i.md).
2. If **type** is **ParticleType.IMAGE**, the **config** type is [ImageParticleParameters](arkts-arkui-particle-comp-imageparticleparameters-i.md).

-**count** indicates the total number of emitted particles. The value of **count** must be greater than or equal to -1. When **count** is -1, the total number of particles is infinite.

-**lifetime** indicates the lifecycle of a single particle. The default value is **1000** (that is, 1000 ms, 1 s). The value of lifetime must be greater than or equal to -1. When **lifetime** is -1, the particle lifecycle is infinite. When **lifetime** is less than -1, the default value is used.

**Note:** If the animation does not need to play continuously, it is recommended not to set the lifecycle to -1, as this may cause significant performance impact.

**lifetimeRange** indicates the value range of the particle lifecycle. After **lifetimeRange** is set, the particle lifecycle is a random integer in [lifetime - lifetimeRange, lifetime + lifetimeRange]. The default value of **lifetimeRange** is **0**, and the value range is [0, +∞). When it is set to a negative value, the default value is used.

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** [EmitterParticleOptions](arkts-arkui-particle-comp-emitterparticleoptions-i.md)&lt;PARTICLE&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-EmitterOptions-particle: EmitterParticleOptions<PARTICLE>--><!--Device-EmitterOptions-particle: EmitterParticleOptions<PARTICLE>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## position

```TypeScript
position?: ParticleTuple<Dimension, Dimension>
```

Emitter position (the position relative to the upper left corner of the component. The first parameter is the relative offset in the x direction, and the second parameter is the relative offset in the y direction.). When the emitter shape is annular (that is, **shape** is **ParticleEmitterShape.ANNULUS**), this property does not take effect, and the shape information must be specified through the **annulusRegion** parameter.

Default value: `[0.0, 0.0]`

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** [ParticleTuple](arkts-arkui-particle-comp-particletuple-t.md)&lt;[Dimension](../arkts-apis/arkts-arkui-dimension-t.md), [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)&gt;

**Default:** [0,0]

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-EmitterOptions-position?: ParticleTuple<Dimension, Dimension>--><!--Device-EmitterOptions-position?: ParticleTuple<Dimension, Dimension>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shape

```TypeScript
shape?: ParticleEmitterShape
```

Shape of the emitter.

Default value: **ParticleEmitterShape.RECTANGLE**

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** [ParticleEmitterShape](arkts-arkui-particle-comp-particleemittershape-e.md)

**Default:** ParticleEmitterShape.RECTANGLE

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-EmitterOptions-shape?: ParticleEmitterShape--><!--Device-EmitterOptions-shape?: ParticleEmitterShape-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: ParticleTuple<Dimension, Dimension>
```

Size of the emitter. The first parameter is the emitter width, and the second parameter is the emitter height. When the emitter shape is annulus (that is, **shape** is **ParticleEmitterShape.ANNULUS**), this property does not take effect, and the shape information must be specified through the **annulusRegion** parameter.

Default value: `['100%','100%']` (that is, the emission window occupies the entire **Particle** component)

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** [ParticleTuple](arkts-arkui-particle-comp-particletuple-t.md)&lt;[Dimension](../arkts-apis/arkts-arkui-dimension-t.md), [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)&gt;

**Default:** ['100%','100%']

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-EmitterOptions-size?: ParticleTuple<Dimension, Dimension>--><!--Device-EmitterOptions-size?: ParticleTuple<Dimension, Dimension>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
