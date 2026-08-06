# VibratorStopMode

停止振动的模式。在调用 [vibrator.stopVibration\_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_9+\_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 或[vibrator.stopVibration\_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_9+\_\_\_HTML\_TAG\_DESC\_USD\_6\_\_\_]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_接口时，需要使用此参数类型指定停止的振 动模式。停止模式和[VibrateEffect\_\_\_HTML\_TAG\_DESC\_USD\_7\_\_\_9+\_\_\_HTML\_TAG\_DESC\_USD\_8\_\_\_]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_中下发的模式为对应关系：VIBRATOR\_STOP\_MODE\_TIME对应VibrateTime 类型，VIBRATOR\_STOP\_MODE\_PRESET对应VibratePreset类型。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-vibrator-enum VibratorStopMode--><!--Device-vibrator-enum VibratorStopMode-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## VIBRATOR_STOP_MODE_TIME

```TypeScript
VIBRATOR_STOP_MODE_TIME = 'time'
```

停止[VibrateTime]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_类型（duration模式）的振动。需与startVibration时使用的VibrateTime类型对应。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-VibratorStopMode-VIBRATOR_STOP_MODE_TIME = 'time'--><!--Device-VibratorStopMode-VIBRATOR_STOP_MODE_TIME = 'time'-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## VIBRATOR_STOP_MODE_PRESET

```TypeScript
VIBRATOR_STOP_MODE_PRESET = 'preset'
```

停止[VibratePreset]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_类型（预置EffectId模式）的振动。需与startVibration时使用的VibratePreset类型对应。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-VibratorStopMode-VIBRATOR_STOP_MODE_PRESET = 'preset'--><!--Device-VibratorStopMode-VIBRATOR_STOP_MODE_PRESET = 'preset'-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

