# EffectId

```TypeScript
enum EffectId
```

预置的振动效果。在调用[vibrator.startVibration<sup>9+</sup>](arkts-sensorservice-vibrator-startvibration-f.md#startvibration-1)或[vibrator.stopVibration<sup>9+</sup>](arkts-sensorservice-vibrator-stopvibration-f.md#stopvibration-1)接口下发[VibratePreset](arkts-sensorservice-vibrator-vibratepreset-i.md)形式振动的时候需要使用此参数类型。此参数值种类多样，'haptic.clock.timer'为其中一种。[HapticFeedback<sup>12+</sup>](arkts-sensorservice-vibrator-hapticfeedback-e.md)展示了几种常用的EffectId值。

> **说明：** 
> 
> 由于设备存在多样性，不同的设备可能预置不同的效果，建议使用预置效果前先使用
> [vibrator.isSupportEffect<sup>10+</sup>](arkts-sensorservice-vibrator-issupporteffect-f.md#issupporteffect-1)
> 或[vibrator.isSupportEffectSync](arkts-sensorservice-vibrator-issupporteffectsync-f.md)接口查询当前设备是否支持该预置效果。

**起始版本：** 8

<!--Device-vibrator-enum EffectId--><!--Device-vibrator-enum EffectId-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## EFFECT_CLOCK_TIMER

```TypeScript
EFFECT_CLOCK_TIMER = 'haptic.clock.timer'
```

描述用户调整计时器时的振动效果。

**起始版本：** 8

<!--Device-EffectId-EFFECT_CLOCK_TIMER = 'haptic.clock.timer'--><!--Device-EffectId-EFFECT_CLOCK_TIMER = 'haptic.clock.timer'-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice
