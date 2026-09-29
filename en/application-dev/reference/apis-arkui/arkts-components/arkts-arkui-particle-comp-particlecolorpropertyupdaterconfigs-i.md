# ParticleColorPropertyUpdaterConfigs

```TypeScript
interface ParticleColorPropertyUpdaterConfigs
```

Sets the configuration of the particle color attribute updater.

**Since:** 10

<!--Device-unnamed-interface ParticleColorPropertyUpdaterConfigs--><!--Device-unnamed-interface ParticleColorPropertyUpdaterConfigs-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## [ParticleUpdater.CURVE]

```TypeScript
[ParticleUpdater.CURVE]: Array<ParticlePropertyAnimation<ResourceColor>>
```

Indicates the configuration of color change when the change mode is curve. The array type indicates that the current property can be set with multiple animation segments, for example, **0ms-3000ms**, **3000ms-5000ms**, and **5000ms-8000ms** are set as separate animations.

**Type:** Array&lt;[ParticlePropertyAnimation](arkts-arkui-particle-comp-particlepropertyanimation-i.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt;&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ParticleColorPropertyUpdaterConfigs-[ParticleUpdater.CURVE]: Array<ParticlePropertyAnimation<ResourceColor>>--><!--Device-ParticleColorPropertyUpdaterConfigs-[ParticleUpdater.CURVE]: Array<ParticlePropertyAnimation<ResourceColor>>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## [ParticleUpdater.NONE]

```TypeScript
[ParticleUpdater.NONE]: void
```

The color does not change.

**Type:** void

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ParticleColorPropertyUpdaterConfigs-[ParticleUpdater.NONE]: void--><!--Device-ParticleColorPropertyUpdaterConfigs-[ParticleUpdater.NONE]: void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## [ParticleUpdater.RANDOM]

```TypeScript
[ParticleUpdater.RANDOM]: ParticleColorOptions
```

Indicates that when the change mode is random, a difference value is randomly generated for each particle within the change range. The r, g, b, and a color channels each use the difference value to overlay the current color value per second to generate the target color value, achieving the effect of random color change.

**Type:** [ParticleColorOptions](arkts-arkui-particle-comp-particlecoloroptions-i.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ParticleColorPropertyUpdaterConfigs-[ParticleUpdater.RANDOM]: ParticleColorOptions--><!--Device-ParticleColorPropertyUpdaterConfigs-[ParticleUpdater.RANDOM]: ParticleColorOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
