# ContinuousParam

连续振动参数。用于[VibratorPatternBuilder.addContinuousEvent]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的 options参数，指定长振事件的振动强度、频率、振动调节曲线和通道编号。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-vibrator-interface ContinuousParam--><!--Device-vibrator-interface ContinuousParam-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## frequency

```TypeScript
frequency?: int
```

可选参数，表示振动频率。取值范围：[0,100]区间内所有整数。默认值：50。不填写时默认使用中等频率。

**类型：** int

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-ContinuousParam-frequency?: int--><!--Device-ContinuousParam-frequency?: int-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## index

```TypeScript
index?: int
```

可选参数，表示马达通道编号。取值范围：[0,2]区间内所有整数。默认值：0。使用场景：不同通道对应不同的马达器件，适用于多马达设备的精细控制场景。不填写时默认使用通道0。

**类型：** int

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-ContinuousParam-index?: int--><!--Device-ContinuousParam-index?: int-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## intensity

```TypeScript
intensity?: int
```

可选参数，表示振动强度。取值范围：[0,100]区间所有整数。默认值：100。不填写时默认使用最大强度。

**类型：** int

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-ContinuousParam-intensity?: int--><!--Device-ContinuousParam-intensity?: int-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## points

```TypeScript
points?: VibratorCurvePoint[]
```

可选参数，表示振动调节曲线数组。使用场景：适用于需要精细控制振动强度和频率变化趋势的交互反馈场景。数组中元素个数最少设置4个，最大设置16个。

**类型：** VibratorCurvePoint[]

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-ContinuousParam-points?: VibratorCurvePoint[]--><!--Device-ContinuousParam-points?: VibratorCurvePoint[]-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

