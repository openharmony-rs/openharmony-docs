# VibrateFromPattern

自定义振动效果触发马达振动。适用于需要灵活组合振动事件的交互反馈场景（如表情包拟真效果、游戏场景/操作反馈）。与VibrateFromFile相比，VibrateFromFile是面向文件中提前定制好的效果，将振动事件以文件描述符 形式传递；VibrateFromPattern提供更加灵活的振动事件排列组合，将振动事件以振动事件数组的形式传递。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-vibrator-interface VibrateFromPattern--><!--Device-vibrator-interface VibrateFromPattern-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## pattern

```TypeScript
pattern: VibratorPattern
```

振动事件数组。由[VibratorPatternBuilder](arkts-sensorservice-vibrator-vibratorpatternbuilder-c.md#VibratorPatternBuilder)的addContinuousEvent和addTransientEvent方法添加后 通过build方法生成。同一VibratorPattern中多个VibratorEvent的time值不能重叠。

**类型：** [VibratorPattern](arkts-sensorservice-vibrator-vibratorpattern-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VibrateFromPattern-pattern: VibratorPattern--><!--Device-VibrateFromPattern-pattern: VibratorPattern-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## type

```TypeScript
type: 'pattern'
```

值为'pattern'，根据组合模式触发马达振动。固定值，不可更改。

**类型：** 'pattern'

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VibrateFromPattern-type: 'pattern'--><!--Device-VibrateFromPattern-type: 'pattern'-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

