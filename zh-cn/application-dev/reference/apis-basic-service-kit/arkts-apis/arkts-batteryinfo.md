# @ohos.batteryInfo

该模块主要提供电池状态和充放电状态的查询接口。

**起始版本：** 6

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getBatteryConfig](arkts-basicservices-getbatteryconfig-f-sys.md#getbatteryconfig-1) | 按场景名称查询电池配置。 |
| [isBatteryConfigSupported](arkts-basicservices-isbatteryconfigsupported-f-sys.md#isbatteryconfigsupported-1) | 检查是否按场景名称启用电池配置。 |
| [setBatteryConfig](arkts-basicservices-setbatteryconfig-f-sys.md#setbatteryconfig-1) | 按场景名称设置电池配置。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BatteryCapacityLevel](arkts-basicservices-batterycapacitylevel-e.md) | 表示电池电量等级的枚举。 |
| [BatteryChargeState](arkts-basicservices-batterychargestate-e.md) | 表示电池充电状态的枚举。 |
| [BatteryHealthState](arkts-basicservices-batteryhealthstate-e.md) | 表示电池健康状态的枚举。 |
| [BatteryPluggedType](arkts-basicservices-batterypluggedtype-e.md) | 表示连接的充电器类型的枚举。 |
| [CommonEventBatteryChangedKey](arkts-basicservices-commoneventbatterychangedkey-e.md) | 表示COMMON_EVENT_BATTERY_CHANGED通用事件附加信息的查询键。 |

### 常量

| 名称 | 说明 |
| --- | --- |
| [batteryCapacityLevel](arkts-basicservices-batteryinfo-con.md#batterycapacitylevel) | 表示当前设备电池电量的等级。 |
| [batterySOC](arkts-basicservices-batteryinfo-con.md#batterysoc) | 表示当前设备剩余电池电量百分比，取值范围是[0，100]。 |
| [batteryTemperature](arkts-basicservices-batteryinfo-con.md#batterytemperature) | 表示当前设备电池的温度，单位0.1摄氏度。 |
| [chargingStatus](arkts-basicservices-batteryinfo-con.md#chargingstatus) | 表示当前设备电池的充电状态。 |
| [healthStatus](arkts-basicservices-batteryinfo-con.md#healthstatus) | 表示当前设备电池的健康状态。 |
| [isBatteryPresent](arkts-basicservices-batteryinfo-con.md#isbatterypresent) | 表示当前设备是否支持电池或者电池是否在位。true表示支持电池或电池在位，false表示不支持电池或电池不在位，默认为false。 |
| [nowCurrent](arkts-basicservices-batteryinfo-con.md#nowcurrent) | 表示当前设备电池的电流，单位毫安。 |
| [pluggedType](arkts-basicservices-batteryinfo-con.md#pluggedtype) | 表示当前设备连接的充电器类型。 |
| [technology](arkts-basicservices-batteryinfo-con.md#technology) | 表示当前设备电池的技术型号。 |
| [voltage](arkts-basicservices-batteryinfo-con.md#voltage) | 表示当前设备电池的电压，单位微伏。 |

<!--Del-->
### 常量（系统接口）

| 名称 | 说明 |
| --- | --- |
| [estimatedRemainingChargeTime](arkts-basicservices-batteryinfo-con-sys.md#estimatedremainingchargetime) | 表示当前设备充满电的预估时间，单位毫秒。此接口为系统接口。 |
| [remainingEnergy](arkts-basicservices-batteryinfo-con-sys.md#remainingenergy) | 表示当前设备电池的剩余容量，单位毫安时。此接口为系统接口。 |
| [totalEnergy](arkts-basicservices-batteryinfo-con-sys.md#totalenergy) | 表示当前设备电池的总容量，单位毫安时。此接口为系统接口。 |
<!--DelEnd-->

