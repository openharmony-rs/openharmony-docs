# EmitterParticleOptions

Defines parameters of particles used by emitters.

> **NOTE:** 
> 
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18.
> While historical version information is preserved for anonymous objects, there may be cases where the outer element
> 's

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## config

```TypeScript
config: ParticleConfigs[PARTICLE]
```

Configuration of the particle type.

The value type of **config** is subject to the value of **type**.

1. If the type is ParticleType.POINT, the config type is [PointParticleParameters](arkts-arkui-pointparticleparameters-i.md).
2. If the type is ParticleType.IMAGE, the config type is [ImageParticleParameters](arkts-arkui-imageparticleparameters-i.md).

**Type:** ParticleConfigs[PARTICLE]

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## count

```TypeScript
count: number
```

Number of particles. The value is greater than or equal to -1. The value **-1** indicates that the number of particles is infinite.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lifetime

```TypeScript
lifetime?: number
```

Lifetime of a single particle. The default value is **1000** (that is, 1000 ms, 1s). The value is greater than or equal to -1. The value **-1** indicates that the lifetime of the particle is infinite. If the value specified is less than **-1**, the default value is used.

Note: If you do not want the animation to keep playing, you are advised not to set the lifetime to –1, which may greatly affect the performance.

**Type:** number

**Default:** 1000

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lifetimeRange

```TypeScript
lifetimeRange?: number
```

Random integer within the range of [lifetime – lifetimeRange, lifetime + lifetimeRange]. After lifetimeRange is set, the particle lifecycle is a random integer within the range. The default value is 0. The value range is from 0 to positive infinity. If it is set to a negative value, the default value is used.

**Type:** number

**Default:** 0

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: PARTICLE
```

Particle type, which can be **IMAGE** or **POINT**.

**Type:** PARTICLE

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
