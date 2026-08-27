# VibrateFromFile

自定义振动类型。仅部分设备支持高清振动的设备可用，当设备不支持此振动类型时，返回错误码801。当调用 [vibrator.startVibration&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-startvibration-f.md) 或 [vibrator.startVibration&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-startvibration-f.md) 时，[VibrateEffect&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-vibrateeffect-t.md)参数的值可以为VibrateFromFile，表示触发自定义振动类型。适用于匹配复杂场景效果的交互反馈（如表情 包触发的拟真效果、游戏场景/操作反馈）。 适用于需要按照振动配置文件定制精细振动效果的交互反馈场景。建议先通过[vibrator.isHdHapticSupported](arkts-sensorservice-vibrator-ishdhapticsupported-f.md)确认设备是否支持高清振动。

**起始版本：** 10

**系统能力：** SystemCapability.Sensors.MiscDevice

## 导入模块

```TypeScript
```

## hapticFd

```TypeScript
hapticFd: HapticFileDescriptor
```

振动配置文件的描述符。需确保文件可用且格式正确，振动序列存储格式请参考[振动效果说明](../../../device/sensor/vibrator-guidelines.md#振动效果说明)。

**类型：** [HapticFileDescriptor](arkts-sensorservice-vibrator-hapticfiledescriptor-i.md)

**起始版本：** 10

**系统能力：** SystemCapability.Sensors.MiscDevice

## type

```TypeScript
type: 'file'
```

值为'file'，按照振动配置文件触发马达振动。固定值，不可更改。

**类型：** 'file'

**起始版本：** 10

**系统能力：** SystemCapability.Sensors.MiscDevice
