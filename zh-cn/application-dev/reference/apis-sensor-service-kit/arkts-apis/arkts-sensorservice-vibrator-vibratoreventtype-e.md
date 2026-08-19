# VibratorEventType

振动事件类型。用于[VibratorEvent](arkts-sensorservice-vibrator-vibratorevent-i.md)的eventType字段指定振动事件的类型。

**起始版本：** 23

<!--Device-vibrator-enum VibratorEventType--><!--Device-vibrator-enum VibratorEventType-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## CONTINUOUS

```TypeScript
CONTINUOUS = 0
```

表示长振。适用于需要持续振动反馈的场景（如引擎振动、拉弓振动等）。

**起始版本：** 23

<!--Device-VibratorEventType-CONTINUOUS = 0--><!--Device-VibratorEventType-CONTINUOUS = 0-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## TRANSIENT

```TypeScript
TRANSIENT = 1
```

表示短振。适用于需要短暂振动反馈的场景（如点击、按键反馈等）。

**起始版本：** 23

<!--Device-VibratorEventType-TRANSIENT = 1--><!--Device-VibratorEventType-TRANSIENT = 1-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

