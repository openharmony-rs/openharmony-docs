# VibratorStopMode

停止振动的模式。在调用[vibrator.stopVibration&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-stopvibration-f.md)或[vibrator.stopVibration&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-stopvibration-f.md)接口时，需要使用此参数类型指定停止的振动模式。停止模式和[VibrateEffect&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-vibrateeffect-t.md)中下发的模式为对应关系：VIBRATOR_STOP_MODE_TIME对应VibrateTime类型，VIBRATOR_STOP_MODE_PRESET对应VibratePreset类型。

**起始版本：** 8

**系统能力：** SystemCapability.Sensors.MiscDevice

## VIBRATOR_STOP_MODE_TIME

```TypeScript
VIBRATOR_STOP_MODE_TIME = 'time'
```

停止[VibrateTime](arkts-sensorservice-vibrator-vibratetime-i.md)类型（duration模式）的振动。需与startVibration时使用的VibrateTime类型对应。

**起始版本：** 8

**系统能力：** SystemCapability.Sensors.MiscDevice

## VIBRATOR_STOP_MODE_PRESET

```TypeScript
VIBRATOR_STOP_MODE_PRESET = 'preset'
```

停止[VibratePreset](arkts-sensorservice-vibrator-vibratepreset-i.md)类型（预置EffectId模式）的振动。需与startVibration时使用的VibratePreset类型对应。

**起始版本：** 8

**系统能力：** SystemCapability.Sensors.MiscDevice
