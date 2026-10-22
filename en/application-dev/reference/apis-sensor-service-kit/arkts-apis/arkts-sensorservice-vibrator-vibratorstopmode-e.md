# VibratorStopMode

```TypeScript
enum VibratorStopMode
```

Enumerates vibration stop modes. This type is used to specify the vibration stop mode when the [vibrator.stopVibration<sup>9+</sup>](arkts-sensorservice-vibrator-stopvibration-f.md#stopvibration-2) or [vibrator.stopVibration<sup>9+</sup>](arkts-sensorservice-vibrator-stopvibration-f.md#stopvibration-1) API is called. The stop mode must match that delivered in [VibrateEffect<sup>9+</sup>](arkts-sensorservice-vibrator-vibrateeffect-t.md).

**Since:** 8

<!--Device-vibrator-enum VibratorStopMode--><!--Device-vibrator-enum VibratorStopMode-End-->

**System capability:** SystemCapability.Sensors.MiscDevice

## VIBRATOR_STOP_MODE_PRESET

```TypeScript
VIBRATOR_STOP_MODE_PRESET = 'preset'
```

The vibration to stop is in **EffectId** mode.

**Since:** 8

<!--Device-VibratorStopMode-VIBRATOR_STOP_MODE_PRESET = 'preset'--><!--Device-VibratorStopMode-VIBRATOR_STOP_MODE_PRESET = 'preset'-End-->

**System capability:** SystemCapability.Sensors.MiscDevice

## VIBRATOR_STOP_MODE_TIME

```TypeScript
VIBRATOR_STOP_MODE_TIME = 'time'
```

The vibration to stop is in **duration** mode.

**Since:** 8

<!--Device-VibratorStopMode-VIBRATOR_STOP_MODE_TIME = 'time'--><!--Device-VibratorStopMode-VIBRATOR_STOP_MODE_TIME = 'time'-End-->

**System capability:** SystemCapability.Sensors.MiscDevice
