# TransientParam

瞬态振动参数。用于[VibratorPatternBuilder.addTransientEvent]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的 options参数，指定短振事件的振动强度、频率和通道编号。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-vibrator-interface TransientParam--><!--Device-vibrator-interface TransientParam-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## frequency

```TypeScript
frequency?: int
```

可选参数，表示振动频率。取值范围：[0,100]区间内所有整数。默认值：50。不填写时默认使用中等频率。

**类型：** int

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-TransientParam-frequency?: int--><!--Device-TransientParam-frequency?: int-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## index

```TypeScript
index?: int
```

可选参数，表示马达通道编号。取值范围：[0,2]区间内所有整数。默认值：0。使用场景：不同通道对应不同的马达器件，适用于多马达设备的精细控制场景。不填写时默认使用通道0。

**类型：** int

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-TransientParam-index?: int--><!--Device-TransientParam-index?: int-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## intensity

```TypeScript
intensity?: int
```

可选参数，表示振动强度。取值范围：[0,100]区间所有整数。默认值：100。不填写时默认使用最大强度。

**类型：** int

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-TransientParam-intensity?: int--><!--Device-TransientParam-intensity?: int-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

