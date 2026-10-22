# EffectId

```TypeScript
enum EffectId
```

Enumerates the preset vibration effect IDs. This type is used when the [vibrator.startVibration<sup>9+</sup>](arkts-sensorservice-vibrator-startvibration-f.md#startvibration-1) or [vibrator.stopVibration<sup>9+</sup>](arkts-sensorservice-vibrator-stopvibration-f.md#stopvibration-1) API is called to deliver the [VibratePreset](arkts-sensorservice-vibrator-vibratepreset-i.md) vibration. This parameter supports a variety of values, such as **haptic.clock.timer**. [HapticFeedback<sup>12+</sup>](arkts-sensorservice-vibrator-hapticfeedback-e.md) provides several frequently used **EffectId** values.

> **NOTE:** 
> 
> Preset effects vary according to devices. You are advised to call
> [vibrator.isSupportEffect](arkts-sensorservice-vibrator-issupporteffect-f.md#issupporteffect-2)<sup>10+</sup> to check whether the
> device supports the preset effect before use.

**Since:** 8

<!--Device-vibrator-enum EffectId--><!--Device-vibrator-enum EffectId-End-->

**System capability:** SystemCapability.Sensors.MiscDevice

## EFFECT_CLOCK_TIMER

```TypeScript
EFFECT_CLOCK_TIMER = 'haptic.clock.timer'
```

Vibration effect when a user adjusts the timer.

**Since:** 8

<!--Device-EffectId-EFFECT_CLOCK_TIMER = 'haptic.clock.timer'--><!--Device-EffectId-EFFECT_CLOCK_TIMER = 'haptic.clock.timer'-End-->

**System capability:** SystemCapability.Sensors.MiscDevice
