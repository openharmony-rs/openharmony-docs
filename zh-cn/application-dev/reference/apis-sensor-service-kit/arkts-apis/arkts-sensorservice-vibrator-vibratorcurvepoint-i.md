# VibratorCurvePoint

相对事件振动强度的增益。用于[ContinuousParam](arkts-sensorservice-vibrator-continuousparam-i.md#ContinuousParam)和[VibratorEvent](arkts-sensorservice-vibrator-vibratorevent-i.md#VibratorEvent)的 points字段，精细控制振动强度和频率的变化趋势。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-vibrator-interface VibratorCurvePoint--><!--Device-vibrator-interface VibratorCurvePoint-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## frequency

```TypeScript
frequency?: int
```

可选参数，相对事件振动频率变化。取值范围：[-100,100]内所有整数。默认值：0。使用场景：适用于精细调节振动频率的交互反馈场景，正值频率升高，负值频率降低。不填写时默认不改变频率。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VibratorCurvePoint-frequency?: int--><!--Device-VibratorCurvePoint-frequency?: int-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## intensity

```TypeScript
intensity?: double
```

可选参数，相对事件振动强度增益。取值范围：[0,1]。默认值：1。使用场景：适用于精细调节振动强度的交互反馈场景，值越大振动越强。不填写时默认使用最大增益。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VibratorCurvePoint-intensity?: double--><!--Device-VibratorCurvePoint-intensity?: double-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## time

```TypeScript
time: int
```

起始时间偏移。单位：ms。用于指定振动调节曲线中该调节点的时间位置。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VibratorCurvePoint-time: int--><!--Device-VibratorCurvePoint-time: int-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

