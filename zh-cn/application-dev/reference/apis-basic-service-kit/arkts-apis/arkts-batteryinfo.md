# @ohos.batteryInfo

该模块主要提供电池状态和充放电状态的查询接口。

**起始版本：** 6

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[getBatteryConfig](arkts-basicservices-batteryinfo-getbatteryconfig-f-sys.md#getBatteryConfig-1) | 按场景名称查询电池配置。<br/> |
| <!--DelRow-->[isBatteryConfigSupported](arkts-basicservices-batteryinfo-isbatteryconfigsupported-f-sys.md#isBatteryConfigSupported-1) | 检查是否按场景名称启用电池配置。<br/> |
| <!--DelRow-->[setBatteryConfig](arkts-basicservices-batteryinfo-setbatteryconfig-f-sys.md#setBatteryConfig-1) | 按场景名称设置电池配置。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BatteryCapacityLevel](arkts-basicservices-batteryinfo-batterycapacitylevel-e.md) | 表示电池电量等级的枚举。<br/> |
| [BatteryChargeState](arkts-basicservices-batteryinfo-batterychargestate-e.md) | 表示电池充电状态的枚举。<br/> |
| [BatteryHealthState](arkts-basicservices-batteryinfo-batteryhealthstate-e.md) | 表示电池健康状态的枚举。<br/> |
| [BatteryPluggedType](arkts-basicservices-batteryinfo-batterypluggedtype-e.md) | 表示连接的充电器类型的枚举。<br/> |
| [CommonEventBatteryChangedKey](arkts-basicservices-batteryinfo-commoneventbatterychangedkey-e.md) | 表示COMMON_EVENT_BATTERY_CHANGED通用事件附加信息的查询键。<br/> |

### 常量

| 名称 | 说明 |
| --- | --- |
| [batteryCapacityLevel](arkts-basicservices-batteryinfo-con.md#batteryCapacityLevel) | 表示当前设备电池电量的等级。<br/> |
| [batterySOC](arkts-basicservices-batteryinfo-con.md#batterySOC) | 表示当前设备剩余电池电量百分比，取值范围是[0，100]。<br/> |
| [batteryTemperature](arkts-basicservices-batteryinfo-con.md#batteryTemperature) | 表示当前设备电池的温度，单位0.1摄氏度。<br/> |
| [chargingStatus](arkts-basicservices-batteryinfo-con.md#chargingStatus) | 表示当前设备电池的充电状态。<br/> |
| <!--DelRow-->[estimatedRemainingChargeTime](arkts-basicservices-batteryinfo-con-sys.md#estimatedRemainingChargeTime) | 表示当前设备充满电的预估时间，单位毫秒。此接口为系统接口。<br/> |
| [healthStatus](arkts-basicservices-batteryinfo-con.md#healthStatus) | 表示当前设备电池的健康状态。<br/> |
| [isBatteryPresent](arkts-basicservices-batteryinfo-con.md#isBatteryPresent) | 表示当前设备是否支持电池或者电池是否在位。true表示支持电池或电池在位，false表示不支持电池或电池不在位，默认为false。<br/> |
| [nowCurrent](arkts-basicservices-batteryinfo-con.md#nowCurrent) | 表示当前设备电池的电流，单位毫安。<br/> |
| [pluggedType](arkts-basicservices-batteryinfo-con.md#pluggedType) | 表示当前设备连接的充电器类型。<br/> |
| <!--DelRow-->[remainingEnergy](arkts-basicservices-batteryinfo-con-sys.md#remainingEnergy) | 表示当前设备电池的剩余容量，单位毫安时。此接口为系统接口。<br/> |
| [technology](arkts-basicservices-batteryinfo-con.md#technology) | 表示当前设备电池的技术型号。<br/> |
| <!--DelRow-->[totalEnergy](arkts-basicservices-batteryinfo-con-sys.md#totalEnergy) | 表示当前设备电池的总容量，单位毫安时。此接口为系统接口。<br/> |
| [voltage](arkts-basicservices-batteryinfo-con.md#voltage) | 表示当前设备电池的电压，单位微伏。<br/> |

