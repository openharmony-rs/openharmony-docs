# TransientParam

瞬态振动参数。用于[VibratorPatternBuilder.addTransientEvent](arkts-sensorservice-vibrator-vibratorpatternbuilder-c.md#addtransientevent)的 options参数，指定短振事件的振动强度、频率和通道编号。

**起始版本：** 18

**系统能力：** SystemCapability.Sensors.MiscDevice

## 导入模块

```TypeScript
```

## frequency

```TypeScript
frequency?: number
```

可选参数，表示振动频率。取值范围：[0,100]区间内所有整数。默认值：50。不填写时默认使用中等频率。

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.Sensors.MiscDevice

## index

```TypeScript
index?: number
```

可选参数，表示马达通道编号。取值范围：[0,2]区间内所有整数。默认值：0。使用场景：不同通道对应不同的马达器件，适用于多马达设备的精细控制场景。不填写时默认使用通道0。

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.Sensors.MiscDevice

## intensity

```TypeScript
intensity?: number
```

可选参数，表示振动强度。取值范围：[0,100]区间所有整数。默认值：100。不填写时默认使用最大强度。

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.Sensors.MiscDevice
