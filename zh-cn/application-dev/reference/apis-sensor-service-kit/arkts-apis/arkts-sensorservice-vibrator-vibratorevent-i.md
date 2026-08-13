# VibratorEvent

振动事件。用于[VibratorPattern](arkts-sensorservice-vibrator-vibratorpattern-i.md#VibratorPattern)的events数组中定义具体的振动事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-vibrator-interface VibratorEvent--><!--Device-vibrator-interface VibratorEvent-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## duration

```TypeScript
duration?: int
```

可选参数，表示振动持续时间。单位：ms。取值范围：(0,5000]区间所有整数。默认值：短振默认48，长振默认1000。使用场景：适用于长振和短振交互反馈场景。不填写时使用对应类型的默认持续时间。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VibratorEvent-duration?: int--><!--Device-VibratorEvent-duration?: int-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## eventType

```TypeScript
eventType: VibratorEventType
```

振动事件类型。CONTINUOUS（0）表示长振，TRANSIENT（1）表示短振。

**类型：** [VibratorEventType](arkts-sensorservice-vibrator-vibratoreventtype-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VibratorEvent-eventType: VibratorEventType--><!--Device-VibratorEvent-eventType: VibratorEventType-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## frequency

```TypeScript
frequency?: int
```

可选参数，表示振动频率。取值范围：[0,100]区间内所有整数。默认值：50。不填写时默认使用中等频率。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VibratorEvent-frequency?: int--><!--Device-VibratorEvent-frequency?: int-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## index

```TypeScript
index?: int
```

可选参数，表示马达通道编号。取值范围：[0,2]区间内所有整数。默认值：0。使用场景：不同通道对应不同的马达器件，适用于多马达设备的精细控制场景。不填写时默认使用通道0。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VibratorEvent-index?: int--><!--Device-VibratorEvent-index?: int-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## intensity

```TypeScript
intensity?: int
```

可选参数，表示振动强度。取值范围：[0,100]区间所有整数。默认值：100。不填写时默认使用最大强度。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VibratorEvent-intensity?: int--><!--Device-VibratorEvent-intensity?: int-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## points

```TypeScript
points?: Array<VibratorCurvePoint>
```

可选参数，表示振动调节曲线数组。使用场景：适用于需要精细控制振动强度和频率变化趋势的交互反馈场景。数组中元素个数最少设置4个，最大设置16个。

**类型：** Array&lt;[VibratorCurvePoint](arkts-sensorservice-vibrator-vibratorcurvepoint-i.md)&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VibratorEvent-points?: Array<VibratorCurvePoint>--><!--Device-VibratorEvent-points?: Array<VibratorCurvePoint>-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## time

```TypeScript
time: int
```

振动起始时间。单位：ms。取值范围：[0,1800000]区间内所有整数。用于指定振动事件在序列中的起始时间点。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VibratorEvent-time: int--><!--Device-VibratorEvent-time: int-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

