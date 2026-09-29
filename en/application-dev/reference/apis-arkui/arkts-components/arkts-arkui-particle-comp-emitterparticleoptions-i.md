# EmitterParticleOptions

```TypeScript
interface EmitterParticleOptions<PARTICLE extends ParticleType>
```

Particle configuration.

> **NOTE:** 
> 
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18.
> While historical version information is preserved for anonymous objects, there may be cases where the outer element
> 's

**Since:** 18

<!--Device-unnamed-interface EmitterParticleOptions<PARTICLE extends ParticleType>--><!--Device-unnamed-interface EmitterParticleOptions<PARTICLE extends ParticleType>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## config

```TypeScript
config: ParticleConfigs[PARTICLE]
```

Configuration of the corresponding type.

The **config** type is related to the **type** value:

1. If **type** is **ParticleType.POINT**, the **config** type is [PointParticleParameters](arkts-arkui-particle-comp-pointparticleparameters-i.md).
2. If **type** is **ParticleType.IMAGE**, the **config** type is [ImageParticleParameters](arkts-arkui-particle-comp-imageparticleparameters-i.md).

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** ParticleConfigs[PARTICLE]

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-EmitterParticleOptions-config: ParticleConfigs[PARTICLE]--><!--Device-EmitterParticleOptions-config: ParticleConfigs[PARTICLE]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## count

```TypeScript
count: number
```

Total number of emitted particles. The value of **count** must be greater than or equal to -1. When **count** is - 1, the total number of particles is infinite.

**Note:** 

When **count** is -1, the emitter continuously emits particles. If you do not need to continuously generate a large number of particles, it is recommended not to set **count** to -1, as this may cause significant performance impact. It is recommended to set reasonable **emitRate** and **lifetime** values to avoid performance issues.

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-EmitterParticleOptions-count: number--><!--Device-EmitterParticleOptions-count: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lifetime

```TypeScript
lifetime?: number
```

Lifecycle of a single particle. The default value is **1000** (that is, 1000 ms, or 1 s), and **lifetime** must be greater than or equal to -1. When **lifetime** is -1, the particle lifecycle is infinite. When **lifetime** is less than -1, the default value is used.

**Note:** If you do not need the animation to play continuously, it is recommended not to set the **lifecycle** to -1, as this may cause significant performance impact.

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** number

**Default:** 1000

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-EmitterParticleOptions-lifetime?: number--><!--Device-EmitterParticleOptions-lifetime?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lifetimeRange

```TypeScript
lifetimeRange?: number
```

Value range of the particle lifecycle, in milliseconds (ms). After **lifetimeRange** is set, the particle lifecycle is a random integer between [lifetime - lifetimeRange, lifetime + lifetimeRange]. The default value of **lifetimeRange** is **0**, and the value range is from 0 to positive infinity. When it is set to a negative value, the default value is used.

**Atomic service API:** Since API version 12, this API is supported in atomic services.

**Type:** number

**Default:** 0

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-EmitterParticleOptions-lifetimeRange?: number--><!--Device-EmitterParticleOptions-lifetimeRange?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: PARTICLE
```

Particle type, which can be an image or a point.

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** PARTICLE

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-EmitterParticleOptions-type: PARTICLE--><!--Device-EmitterParticleOptions-type: PARTICLE-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
