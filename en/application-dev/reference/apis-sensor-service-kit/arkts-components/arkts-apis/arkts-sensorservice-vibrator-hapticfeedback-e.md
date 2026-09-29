# HapticFeedback

```TypeScript
enum HapticFeedback
```

Defines the vibration effect. The frequency of the same vibration effect may vary depending on the vibrator, but the frequency trend remains consistent. These vibration effects are specific values of the **EffectId** parameter. For details about how to use them, see the sample code for delivering the [VibratePreset](arkts-sensorservice-vibrator-vibratepreset-i.md) vibration effect using the [vibrator.startVibration&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-startvibration-f.md) or [vibrator.stopVibration&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-stopvibration-f.md) API.

**Since:** 12

<!--Device-vibrator-enum HapticFeedback--><!--Device-vibrator-enum HapticFeedback-End-->

**System capability:** SystemCapability.Sensors.MiscDevice

## EFFECT_SOFT

```TypeScript
EFFECT_SOFT = 'haptic.effect.soft'
```

Soft vibration, low frequency.

**Since:** 12

<!--Device-HapticFeedback-EFFECT_SOFT = 'haptic.effect.soft'--><!--Device-HapticFeedback-EFFECT_SOFT = 'haptic.effect.soft'-End-->

**System capability:** SystemCapability.Sensors.MiscDevice

## EFFECT_HARD

```TypeScript
EFFECT_HARD = 'haptic.effect.hard'
```

Hard vibration, medium frequency.

**Since:** 12

<!--Device-HapticFeedback-EFFECT_HARD = 'haptic.effect.hard'--><!--Device-HapticFeedback-EFFECT_HARD = 'haptic.effect.hard'-End-->

**System capability:** SystemCapability.Sensors.MiscDevice

## EFFECT_SHARP

```TypeScript
EFFECT_SHARP = 'haptic.effect.sharp'
```

Sharp vibration, high frequency.

**Since:** 12

<!--Device-HapticFeedback-EFFECT_SHARP = 'haptic.effect.sharp'--><!--Device-HapticFeedback-EFFECT_SHARP = 'haptic.effect.sharp'-End-->

**System capability:** SystemCapability.Sensors.MiscDevice

## EFFECT_NOTICE_SUCCESS

```TypeScript
EFFECT_NOTICE_SUCCESS = 'haptic.notice.success'
```

Vibration for a success notification.

**Since:** 18

<!--Device-HapticFeedback-EFFECT_NOTICE_SUCCESS = 'haptic.notice.success'--><!--Device-HapticFeedback-EFFECT_NOTICE_SUCCESS = 'haptic.notice.success'-End-->

**System capability:** SystemCapability.Sensors.MiscDevice

## EFFECT_NOTICE_FAILURE

```TypeScript
EFFECT_NOTICE_FAILURE = 'haptic.notice.fail'
```

Vibration for a failure notification.

**Since:** 18

<!--Device-HapticFeedback-EFFECT_NOTICE_FAILURE = 'haptic.notice.fail'--><!--Device-HapticFeedback-EFFECT_NOTICE_FAILURE = 'haptic.notice.fail'-End-->

**System capability:** SystemCapability.Sensors.MiscDevice

## EFFECT_NOTICE_WARNING

```TypeScript
EFFECT_NOTICE_WARNING = 'haptic.notice.warning'
```

Vibration for an alert.

**Since:** 18

<!--Device-HapticFeedback-EFFECT_NOTICE_WARNING = 'haptic.notice.warning'--><!--Device-HapticFeedback-EFFECT_NOTICE_WARNING = 'haptic.notice.warning'-End-->

**System capability:** SystemCapability.Sensors.MiscDevice
