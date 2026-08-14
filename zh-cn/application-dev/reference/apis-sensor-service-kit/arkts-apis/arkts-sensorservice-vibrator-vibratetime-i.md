# VibrateTime

指定时长振动类型。仅对振动时长进行启动或停止控制，满足基础功能，无法对振动强度、频率等维度进行个性化设置。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-vibrator-interface VibrateTime--><!--Device-vibrator-interface VibrateTime-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## duration

```TypeScript
duration: int
```

马达持续振动时长。单位：ms。取值范围：(0,1800000]区间内所有整数。由于实际产品厂商驱动对器件保护设计规格不同，不同设备实际最大振动时长会有差异。建议值：单次触发长振动一般建议不超过10000（10秒），以最大化用户 体验。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VibrateTime-duration: int--><!--Device-VibrateTime-duration: int-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## type

```TypeScript
type: 'time'
```

值为'time'，按照指定时长触发马达振动。固定值，不可更改。

**类型：** 'time'

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VibrateTime-type: 'time'--><!--Device-VibrateTime-type: 'time'-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

