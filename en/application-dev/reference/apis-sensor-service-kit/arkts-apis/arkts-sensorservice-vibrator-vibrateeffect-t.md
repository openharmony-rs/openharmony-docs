# VibrateEffect

```TypeScript
type VibrateEffect = VibrateTime | VibratePreset | VibrateFromFile | VibrateFromPattern
```

Defines the vibration effect. This parameter is required for [vibrator.startVibration9+](arkts-sensorservice-vibrator-startvibration-f.md) or [vibrator.startVibration9+](arkts-sensorservice-vibrator-startvibration-f.md#startvibration-1).

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-vibrator-type VibrateEffect = VibrateTime | VibratePreset | VibrateFromFile | VibrateFromPattern--><!--Device-vibrator-type VibrateEffect = VibrateTime | VibratePreset | VibrateFromFile | VibrateFromPattern-End-->

**System capability:** SystemCapability.Sensors.MiscDevice

| Type | Description |
| --- | --- |
| [VibrateTime](arkts-sensorservice-vibrator-vibratetime-i.md) | Triggers vibration based on a specified duration.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| [VibratePreset](arkts-sensorservice-vibrator-vibratepreset-i.md) | Triggers vibration based on a preset effect. |
| [VibrateFromFile](arkts-sensorservice-vibrator-vibratefromfile-i.md) | Triggers vibration based on a custom vibration configuration file. [since 10] |
| [VibrateFromPattern](arkts-sensorservice-vibrator-vibratefrompattern-i.md) | Triggers vibration based on a custom effect. [since 18] |
