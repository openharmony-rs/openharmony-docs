# VibrateTime

指定时长振动类型。仅对振动时长进行启动或停止控制，满足基础功能，无法对振动强度、频率等维度进行个性化设置。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.MiscDevice

## 导入模块

```TypeScript
```

## duration

```TypeScript
duration: number
```

马达持续振动时长。单位：ms（毫秒）。取值范围：(0,1800000]区间内所有整数。由于实际产品厂商驱动对器件保护设计规格不同，不同设备实际最大振动时长会有差异。建议值：单次触发长振动一般建议不超过10000（10秒），以最大化用户 体验。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Sensors.MiscDevice

## type

```TypeScript
type: 'time'
```

值为'time'，按照指定时长触发马达振动。固定值，不可更改。

**类型：** 'time'

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Sensors.MiscDevice
