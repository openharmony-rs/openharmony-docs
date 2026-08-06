# VibratorPattern

马达振动序列，每个events代表一个振动事件。通过[VibratorPatternBuilder.build]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_方法生成，作为 [VibrateFromPattern]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_的pattern参数传入 [startVibration]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_ 接口触发振动。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-vibrator-interface VibratorPattern--><!--Device-vibrator-interface VibratorPattern-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## events

```TypeScript
events: Array<VibratorEvent>
```

振动事件数组。由[VibratorPatternBuilder]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的addContinuousEvent和addTransientEvent方法添加后 通过build方法生成。同一VibratorPattern中多个VibratorEvent的time值不能重叠。

**类型：** Array&lt;VibratorEvent&gt;

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-VibratorPattern-events: Array<VibratorEvent>--><!--Device-VibratorPattern-events: Array<VibratorEvent>-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## time

```TypeScript
time: int
```

振动绝对起始时间。单位：ms。

**类型：** int

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-VibratorPattern-time: int--><!--Device-VibratorPattern-time: int-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

