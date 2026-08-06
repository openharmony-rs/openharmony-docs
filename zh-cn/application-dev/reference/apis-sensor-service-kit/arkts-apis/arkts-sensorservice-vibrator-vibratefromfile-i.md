# VibrateFromFile

自定义振动类型。仅部分设备支持高清振动的设备可用，当设备不支持此振动类型时，返回错误码801。当调用 [vibrator.startVibration\_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_9+\_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 或 [vibrator.startVibration\_\_\_HTML\_TAG\_DESC\_USD\_6\_\_\_9+\_\_\_HTML\_TAG\_DESC\_USD\_7\_\_\_]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ 时，[VibrateEffect\_\_\_HTML\_TAG\_DESC\_USD\_8\_\_\_9+\_\_\_HTML\_TAG\_DESC\_USD\_9\_\_\_]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_参数的值可以为VibrateFromFile，表示触发自定义振动类型。适用于匹配复杂场景效果的交互反馈（如表情 包触发的拟真效果、游戏场景/操作反馈）。 适用于需要按照振动配置文件定制精细振动效果的交互反馈场景。建议先通过[vibrator.isHdHapticSupported]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_确认设备是否支持高清振动。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-vibrator-interface VibrateFromFile--><!--Device-vibrator-interface VibrateFromFile-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## hapticFd

```TypeScript
hapticFd: HapticFileDescriptor
```

振动配置文件的描述符。需确保文件可用且格式正确，振动序列存储格式请参考\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

**类型：** HapticFileDescriptor

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-VibrateFromFile-hapticFd: HapticFileDescriptor--><!--Device-VibrateFromFile-hapticFd: HapticFileDescriptor-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## type

```TypeScript
type: 'file'
```

值为'file'，按照振动配置文件触发马达振动。固定值，不可更改。

**类型：** 'file'

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-VibrateFromFile-type: 'file'--><!--Device-VibrateFromFile-type: 'file'-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

