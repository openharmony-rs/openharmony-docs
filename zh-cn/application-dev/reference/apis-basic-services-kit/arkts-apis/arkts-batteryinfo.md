# @ohos.batteryInfo

该模块提供按场景设置和查询电池配置的能力，还提供电池预估充电时间、总容量、剩余容量等关键属性的查询，适用于需要实时获取电池信息或管理充电场景的系统应用开发。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-declare namespace batteryInfo--><!--Device-unnamed-declare namespace batteryInfo-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

## 导入模块

```TypeScript
import { batteryInfo } from '@kit.BasicServicesKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [batteryCapacityLevel](arkts-basicservices-batteryinfo-batterycapacitylevel-f.md) | 表示当前设备电池电量的等级。 |
| [batterySOC](arkts-basicservices-batteryinfo-batterysoc-f.md) | 表示当前设备剩余电池电量百分比，取值范围是[0，100]。 |
| [batteryTemperature](arkts-basicservices-batteryinfo-batterytemperature-f.md) | 表示当前设备电池的温度，单位0.1摄氏度。 |
| [chargingStatus](arkts-basicservices-batteryinfo-chargingstatus-f.md) | 表示当前设备电池的充电状态。 |
| [healthStatus](arkts-basicservices-batteryinfo-healthstatus-f.md) | 表示当前设备电池的健康状态。 |
| [isBatteryPresent](arkts-basicservices-batteryinfo-isbatterypresent-f.md) | 表示当前设备是否支持电池以及电池是否在位。true表示设备支持电池且电池在位，false表示设备不支持电池或电池不在位，默认为false。 |
| [nowCurrent](arkts-basicservices-batteryinfo-nowcurrent-f.md) | 表示当前设备电池的电流，单位毫安。 |
| [pluggedType](arkts-basicservices-batteryinfo-pluggedtype-f.md) | 表示当前设备连接的充电器类型。 |
| [technology](arkts-basicservices-batteryinfo-technology-f.md) | 表示当前设备电池的技术型号。 |
| [voltage](arkts-basicservices-batteryinfo-voltage-f.md) | 表示当前设备电池的电压，单位微伏。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [estimatedRemainingChargeTime](arkts-basicservices-batteryinfo-estimatedremainingchargetime-f-sys.md) | 获取当前设备充满电的预估时间，单位毫秒。 |
| [getBatteryConfig](arkts-basicservices-batteryinfo-getbatteryconfig-f-sys.md) | 按场景名称查询电池配置。调用该接口后，系统将根据传入的场景名称查找并返回对应的电池充电配置值。 |
| [isBatteryConfigSupported](arkts-basicservices-batteryinfo-isbatteryconfigsupported-f-sys.md) | 检查是否按场景名称启用电池配置。调用该接口后，系统将判断当前设备是否支持指定的充电场景配置，并返回检查结果。 |
| [remainingEnergy](arkts-basicservices-batteryinfo-remainingenergy-f-sys.md) | 获取当前设备电池的剩余容量，单位毫安时。 |
| [setBatteryConfig](arkts-basicservices-batteryinfo-setbatteryconfig-f-sys.md) | 按场景名称设置电池配置。调用该接口后，系统将根据传入的场景名称和场景值修改对应的电池充电配置，影响设备充电行为。 |
| [totalEnergy](arkts-basicservices-batteryinfo-totalenergy-f-sys.md) | 获取当前设备电池的总容量，单位毫安时。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BatteryCapacityLevel](arkts-basicservices-batteryinfo-batterycapacitylevel-e.md) | 表示电池电量等级的枚举。可用于根据电量等级执行差异化策略，例如在低电量（LEVEL_LOW）或极低电量（LEVEL_CRITICAL）时限制后台任务和高功耗功能，在满电量（LEVEL_FULL）时解除限制。 |
| [BatteryChargeState](arkts-basicservices-batteryinfo-batterychargestate-e.md) | 表示电池充电状态的枚举。 |
| [BatteryHealthState](arkts-basicservices-batteryinfo-batteryhealthstate-e.md) | 表示电池健康状态的枚举。 |
| [BatteryPluggedType](arkts-basicservices-batteryinfo-batterypluggedtype-e.md) | 表示连接的充电器类型的枚举。 |
| [CommonEventBatteryChangedKey](arkts-basicservices-batteryinfo-commoneventbatterychangedkey-e.md) | 表示COMMON_EVENT_BATTERY_CHANGED通用事件附加信息的查询键。 开发者需先订阅[COMMON_EVENT_BATTERY_CHANGED公共事件](../../../reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_battery_changed)， 在事件回调中通过这些查询键从事件附加数据中提取对应的电池状态信息。 详细使用方法请参见[@ohos.commonEventManager (公共事件模块)](arkts-commoneventmanager.md)。 |

