# VibratorCurvePoint

相对事件振动强度的增益。用于[ContinuousParam](arkts-sensorservice-vibrator-continuousparam-i.md)和[VibratorEvent](arkts-sensorservice-vibrator-vibratorevent-i.md)的 points字段，精细控制振动强度和频率的变化趋势。

**起始版本：** 18

**系统能力：** SystemCapability.Sensors.MiscDevice

## 导入模块

```TypeScript
```

## frequency

```TypeScript
frequency?: number
```

可选参数，相对事件振动频率变化。取值范围：[-100,100]内所有整数。默认值：0。使用场景：适用于精细调节振动频率的交互反馈场景，正值频率升高，负值频率降低。不填写时默认不改变频率。

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.Sensors.MiscDevice

## intensity

```TypeScript
intensity?: number
```

可选参数，相对事件振动强度增益。取值范围：[0,1]。默认值：1。使用场景：适用于精细调节振动强度的交互反馈场景，值越大振动越强。不填写时默认使用最大增益。

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.Sensors.MiscDevice

## time

```TypeScript
time: number
```

起始时间偏移。单位：ms（毫秒）。用于指定振动调节曲线中该调节点的时间位置。

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.Sensors.MiscDevice
