# EffectId

```TypeScript
enum EffectId
```

Enumerates the preset vibration effect IDs. This type is used when the [vibrator.startVibration&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-startvibration-f.md) or [vibrator.stopVibration&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-stopvibration-f.md) API is called to deliver the [VibratePreset](arkts-sensorservice-vibrator-vibratepreset-i.md) vibration. This parameter supports a variety of values, such as **haptic.clock.timer**. [HapticFeedback&lt;sup&gt;12+&lt;/sup&gt;](arkts-sensorservice-vibrator-hapticfeedback-e.md) provides several frequently used **EffectId** values.

> **NOTE:** 
> 
> Preset effects vary according to devices. You are advised to call
> [vibrator.isSupportEffect](arkts-sensorservice-vibrator-issupporteffect-f.md#issupporteffect-1)&lt;sup&gt;10+&lt;/sup&gt; to check whether the
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
