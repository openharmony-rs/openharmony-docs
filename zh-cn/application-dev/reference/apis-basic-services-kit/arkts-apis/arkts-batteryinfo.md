# @ohos.batteryInfo

该模块主要提供电池状态和充放电状态的查询接口， 支持查询剩余电量、充电状态、健康状态、充电器类型、电压、电流、温度等电池信息， 适用于需要根据电池状态调整应用行为（如低电量时降低功耗、充电时启动高耗能任务）的场景， 可帮助开发者实时感知设备电池状况，优化应用功耗策略并提升用户体验。

**起始版本：** 6

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

## 导入模块

```TypeScript
import { batteryInfo } from '@kit.BasicServicesKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getBatteryConfig](arkts-basicservices-batteryinfo-getbatteryconfig-f-sys.md) | 按场景名称查询电池配置。调用该接口后，系统将根据传入的场景名称查找并返回对应的电池充电配置值。 |
| [isBatteryConfigSupported](arkts-basicservices-batteryinfo-isbatteryconfigsupported-f-sys.md) | 检查是否按场景名称启用电池配置。调用该接口后，系统将判断当前设备是否支持指定的充电场景配置，并返回检查结果。 |
| [setBatteryConfig](arkts-basicservices-batteryinfo-setbatteryconfig-f-sys.md) | 按场景名称设置电池配置。调用该接口后，系统将根据传入的场景名称和场景值修改对应的电池充电配置，影响设备充电行为。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BatteryCapacityLevel](arkts-basicservices-batteryinfo-batterycapacitylevel-e.md) | 表示电池电量等级的枚举。可用于根据电量等级执行差异化策略，例如在低电量（LEVEL_LOW）或极低电量（LEVEL_CRITICAL）时限制后台任务和高功耗功能，在满电量（LEVEL_FULL）时解除限制。 |
| [BatteryChargeState](arkts-basicservices-batteryinfo-batterychargestate-e.md) | 表示电池充电状态的枚举。 |
| [BatteryHealthState](arkts-basicservices-batteryinfo-batteryhealthstate-e.md) | 表示电池健康状态的枚举。 |
| [BatteryPluggedType](arkts-basicservices-batteryinfo-batterypluggedtype-e.md) | 表示连接的充电器类型的枚举。 |
| [CommonEventBatteryChangedKey](arkts-basicservices-batteryinfo-commoneventbatterychangedkey-e.md) | 表示COMMON_EVENT_BATTERY_CHANGED通用事件附加信息的查询键。 开发者需先订阅COMMON_EVENT_BATTERY_CHANGED公共事件， 在事件回调中通过这些查询键从事件附加数据中提取对应的电池状态信息。 详细使用方法请参见@ohos.commonEventManager (公共事件模块)。 |

### 常量

| 名称 | 说明 |
| --- | --- |
| [batteryCapacityLevel](arkts-basicservices-batteryinfo-con.md#batterycapacitylevel) | 表示当前设备电池电量的等级。 |
| [batterySOC](arkts-basicservices-batteryinfo-con.md#batterysoc) | 表示当前设备剩余电池电量百分比，取值范围是[0，100]。 |
| [batteryTemperature](arkts-basicservices-batteryinfo-con.md#batterytemperature) | 表示当前设备电池的温度，单位0.1摄氏度。 |
| [chargingStatus](arkts-basicservices-batteryinfo-con.md#chargingstatus) | 表示当前设备电池的充电状态。 |
| [healthStatus](arkts-basicservices-batteryinfo-con.md#healthstatus) | 表示当前设备电池的健康状态。 |
| [isBatteryPresent](arkts-basicservices-batteryinfo-con.md#isbatterypresent) | 表示当前设备是否支持电池以及电池是否在位。true表示设备支持电池且电池在位，false表示设备不支持电池或电池不在位，默认为false。 |
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
