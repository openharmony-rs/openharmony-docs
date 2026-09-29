# ParticlePropertyUpdaterConfigs

```TypeScript
interface ParticlePropertyUpdaterConfigs<T>
```

Sets the particle property updater configuration.

**Since:** 10

<!--Device-unnamed-interface ParticlePropertyUpdaterConfigs<T>--><!--Device-unnamed-interface ParticlePropertyUpdaterConfigs<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## [ParticleUpdater.CURVE]

```TypeScript
[ParticleUpdater.CURVE]: Array<ParticlePropertyAnimation<T>>
```

Configuration of property change when the change mode is curve. The array type indicates that multiple animation segments can be set for the current property, for example, **0ms-3000ms**, **3000ms-5000ms**, and **5000ms-8000ms**. **T** is number.

**Type:** Array&lt;[ParticlePropertyAnimation](arkts-arkui-particle-comp-particlepropertyanimation-i.md)&lt;T&gt;&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ParticlePropertyUpdaterConfigs-[ParticleUpdater.CURVE]: Array<ParticlePropertyAnimation<T>>--><!--Device-ParticlePropertyUpdaterConfigs-[ParticleUpdater.CURVE]: Array<ParticlePropertyAnimation<T>>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## [ParticleUpdater.NONE]

```TypeScript
[ParticleUpdater.NONE]: void
```

No change.

**Type:** void

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ParticlePropertyUpdaterConfigs-[ParticleUpdater.NONE]: void--><!--Device-ParticlePropertyUpdaterConfigs-[ParticleUpdater.NONE]: void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## [ParticleUpdater.RANDOM]

```TypeScript
[ParticleUpdater.RANDOM]: ParticleTuple<T, T>
```

When the change mode is random, the change difference per second is a value randomly generated within the configured range.

The target property value is the current property value plus the change difference. For example, if the current property value is **0.2** and **config** is [0.1,1.0]:

1. If the change difference takes a random value 0.5 within the range [0.1,1.0], the target property value is 0.2 + 0.5 = 0.7.
2. The change difference can also be negative. For example, if the current property value is 0.2 and **config** is [-3.0,2.0],
and the change difference takes a random value -2.0 within the range [-3.0,2.0], the target property value is 0.2 - 2.0 = -1.8.

**Note:** 

**config** configures the value range of the change difference, and there is no constraint on the maximum and minimum values of the difference. However, if the current property value plus the difference is greater than the maximum property value, the target property value takes the maximum property value; if the current property value plus the difference is less than the minimum property value, the target property value takes the minimum property value. **T** is number.

For example, if the value range of **opacity** is [0.0,1.0], when the current property value plus the difference exceeds 1.0, 1.0 is used.

**Type:** [ParticleTuple](arkts-arkui-particle-comp-particletuple-t.md)&lt;T, T&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ParticlePropertyUpdaterConfigs-[ParticleUpdater.RANDOM]: ParticleTuple<T, T>--><!--Device-ParticlePropertyUpdaterConfigs-[ParticleUpdater.RANDOM]: ParticleTuple<T, T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
