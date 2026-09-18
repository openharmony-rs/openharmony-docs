# ParticleUpdaterOptions

Defines the particle updater options.

> **NOTE:** 
> 
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18.
> While historical version information is preserved for anonymous objects, there may be cases where the outer element
> 's

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## config

```TypeScript
config: ParticlePropertyUpdaterConfigs<TYPE>[UPDATER]
```

How the property is updated. The available options of **type** are as follows:

1. **ParticleUpdater.NONE**: The property does not change. In this case, the **config** type is
[ParticlePropertyUpdaterConfigs](arkts-arkui-particlepropertyupdaterconfigs-i.md)[ParticleUpdater.NONE].
2. **ParticleUpdater.RANDOM**: The property changes randomly. In this case, the **config** type is
[ParticlePropertyUpdaterConfigs](arkts-arkui-particlepropertyupdaterconfigs-i.md)[ParticleUpdater.RANDOM].
3. **ParticleUpdater.CURVE**: The property changes with the animation curve. In this case,
the **config** type is [ParticlePropertyUpdaterConfigs](arkts-arkui-particlepropertyupdaterconfigs-i.md)[ParticleUpdater.CURVE].

**Type:** [ParticlePropertyUpdaterConfigs](arkts-arkui-particlepropertyupdaterconfigs-i.md)&lt;TYPE&gt;[UPDATER]

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: UPDATER
```

Particle updater type.

**Type:** UPDATER

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
