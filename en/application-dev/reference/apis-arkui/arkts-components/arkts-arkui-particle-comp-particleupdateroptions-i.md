# ParticleUpdaterOptions

```TypeScript
interface ParticleUpdaterOptions<TYPE, UPDATER extends ParticleUpdater>
```

Defines the property change configuration.

> **NOTE:** 
> 
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18.
> While historical version information is preserved for anonymous objects, there may be cases where the outer element
> 's

**Since:** 18

<!--Device-unnamed-interface ParticleUpdaterOptions<TYPE, UPDATER extends ParticleUpdater>--><!--Device-unnamed-interface ParticleUpdaterOptions<TYPE, UPDATER extends ParticleUpdater>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## config

```TypeScript
config: ParticlePropertyUpdaterConfigs<TYPE>[UPDATER]
```

Property change configuration. The property change type has three categories:

1. When **type** is **ParticleUpdater.NONE**, it indicates no change, and **config** is of type
[ParticlePropertyUpdaterConfigs](arkts-arkui-particle-comp-particlepropertyupdaterconfigs-i.md)[ParticleUpdater.NONE].
2. When type is **ParticleUpdater.RANDOM**, it indicates the change type is random, and **config** is of type
[ParticlePropertyUpdaterConfigs](arkts-arkui-particle-comp-particlepropertyupdaterconfigs-i.md)[ParticleUpdater.RANDOM].
3. When **type** is **ParticleUpdater.CURVE**, it indicates the change type is curve, and **config** is of type
[ParticlePropertyUpdaterConfigs](arkts-arkui-particle-comp-particlepropertyupdaterconfigs-i.md)[ParticleUpdater.CURVE]. **Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** [ParticlePropertyUpdaterConfigs](arkts-arkui-particle-comp-particlepropertyupdaterconfigs-i.md)&lt;TYPE&gt;[UPDATER]

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ParticleUpdaterOptions-config: ParticlePropertyUpdaterConfigs<TYPE>[UPDATER]--><!--Device-ParticleUpdaterOptions-config: ParticlePropertyUpdaterConfigs<TYPE>[UPDATER]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: UPDATER
```

Property change type.

Default value: **type** defaults to **ParticleUpdater.NONE**. **Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** UPDATER

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ParticleUpdaterOptions-type: UPDATER--><!--Device-ParticleUpdaterOptions-type: UPDATER-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
