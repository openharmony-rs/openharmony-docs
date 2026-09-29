# ParticleColorUpdaterOptions

```TypeScript
interface ParticleColorUpdaterOptions<UPDATER extends ParticleUpdater>
```

How the color property is updated.

> **NOTE:** 
> 
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18.
> While historical version information is preserved for anonymous objects, there may be cases where the outer element
> 's

**Since:** 18

<!--Device-unnamed-interface ParticleColorUpdaterOptions<UPDATER extends ParticleUpdater>--><!--Device-unnamed-interface ParticleColorUpdaterOptions<UPDATER extends ParticleUpdater>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## config

```TypeScript
config: ParticleColorPropertyUpdaterConfigs[UPDATER]
```

The color property change type has three categories:

1. When **type** is **ParticleUpdater.NONE**, it indicates no change, and the **config** type is
[ParticleColorPropertyUpdaterConfigs](arkts-arkui-particle-comp-particlecolorpropertyupdaterconfigs-i.md)[ParticleUpdater.NONE].
2. When **type** is **ParticleUpdater.RANDOM**, it indicates random uniform change, and the **config** type is
[ParticleColorPropertyUpdaterConfigs](arkts-arkui-particle-comp-particlecolorpropertyupdaterconfigs-i.md)[ParticleUpdater.RANDOM].
3. When **type** is **ParticleUpdater.CURVE**, it indicates change following the animation curve, and the **config** type is
[ParticleColorPropertyUpdaterConfigs](arkts-arkui-particle-comp-particlecolorpropertyupdaterconfigs-i.md)[ParticleUpdater.CURVE].

**NOTE:** 

When **type** is **ParticleUpdater.RANDOM** or **ParticleUpdater.CURVE**, the color configuration in **updater** takes precedence over the color configuration in **range**. Within the animation time period configured in updater, the color changes according to the color configuration in **updater**; outside the animation time period configured in **updater**, the color changes according to the color configuration in **range**.

**Atomic service API:** This API is supported in atomic services since API version 11.

**Type:** ParticleColorPropertyUpdaterConfigs[UPDATER]

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ParticleColorUpdaterOptions-config: ParticleColorPropertyUpdaterConfigs[UPDATER]--><!--Device-ParticleColorUpdaterOptions-config: ParticleColorPropertyUpdaterConfigs[UPDATER]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: UPDATER
```

Change type of the color property.

Default value: **type** defaults to **ParticleUpdater.NONE**.

**Atomic service API:** This API is supported in atomic services since API version 11.

**Type:** UPDATER

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ParticleColorUpdaterOptions-type: UPDATER--><!--Device-ParticleColorUpdaterOptions-type: UPDATER-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
