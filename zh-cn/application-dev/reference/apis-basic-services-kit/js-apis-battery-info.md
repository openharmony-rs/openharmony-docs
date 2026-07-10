# @ohos.batteryInfo (电量信息)

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->

该模块主要提供电池状态和充放电状态的查询接口，支持查询剩余电量、充电状态、健康状态、充电器类型、电压、电流、温度等电池信息，适用于需要根据电池状态调整应用行为（如低电量时降低功耗、充电时启动高耗能任务）的场景，可帮助开发者实时感知设备电池状况，优化应用功耗策略并提升用户体验。

> **说明：**
>
> 本模块首批接口从API version 6开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。


## 导入模块

```js
import {batteryInfo} from '@kit.BasicServicesKit';
```

## 常量

描述电池信息。

**系统能力**：SystemCapability.PowerManager.BatteryManager.Core

| 名称      | 类型        | 只读 |  说明     |
| --------------- | ------------------- | ---- | ---------------------|
| batterySOC                                | number                                         | 是   | 表示当前设备剩余电池电量百分比，取值范围是[0，100]。<br>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。                           |
| chargingStatus                            | [BatteryChargeState](#batterychargestate)      | 是   | 表示当前设备电池的充电状态。<br>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。                               |
| healthStatus                              | [BatteryHealthState](#batteryhealthstate)      | 是   | 表示当前设备电池的健康状态。                               |
| pluggedType                               | [BatteryPluggedType](#batterypluggedtype)      | 是   | 表示当前设备连接的充电器类型。                             |
| voltage                                   | number                                         | 是   | 表示当前设备电池的电压，单位微伏。                         |
| technology                                | string                                         | 是   | 表示当前设备电池的技术型号。                               |
| batteryTemperature                        | number                                         | 是   | 表示当前设备电池的温度，单位0.1摄氏度。                    |
| isBatteryPresent<sup>7+</sup>             | boolean                                        | 是   | 表示当前设备是否支持电池以及电池是否在位。true表示设备支持电池且电池在位，false表示设备不支持电池或电池不在位，默认为false。|
| batteryCapacityLevel<sup>9+</sup>         | [BatteryCapacityLevel](#batterycapacitylevel9) | 是   | 表示当前设备电池电量的等级。                              |
| nowCurrent<sup>12+</sup>                  | number                                         | 是   | 表示当前设备电池的电流，单位毫安。                        |

**示例**：

  ```ts
  import {batteryInfo} from '@kit.BasicServicesKit';

  let batterySOCInfo: number = batteryInfo.batterySOC;
  console.info("The batterySOCInfo is: " + batterySOCInfo);

  let chargingStatusInfo = batteryInfo.chargingStatus;
  console.info("The chargingStatusInfo is: " + chargingStatusInfo);

  let healthStatusInfo = batteryInfo.healthStatus;
  console.info("The healthStatusInfo is: " + healthStatusInfo);

  let pluggedTypeInfo = batteryInfo.pluggedType;
  console.info("The pluggedTypeInfo is: " + pluggedTypeInfo);

  let voltageInfo: number = batteryInfo.voltage;
  console.info("The voltageInfo is: " + voltageInfo);

  let technologyInfo: string = batteryInfo.technology;
  console.info("The technologyInfo is: " + technologyInfo);

  let batteryTemperatureInfo: number = batteryInfo.batteryTemperature;
  console.info("The batteryTemperatureInfo is: " + batteryTemperatureInfo);

  let isBatteryPresentInfo: boolean = batteryInfo.isBatteryPresent;
  console.info("The isBatteryPresentInfo is: " + isBatteryPresentInfo);

  let batteryCapacityLevelInfo = batteryInfo.batteryCapacityLevel;
  console.info("The batteryCapacityLevelInfo is: " + batteryCapacityLevelInfo);

  let nowCurrentInfo: number = batteryInfo.nowCurrent;
  console.info("The nowCurrentInfo is: " + nowCurrentInfo);
  ```

## BatteryPluggedType

表示连接的充电器类型的枚举。

**系统能力**：SystemCapability.PowerManager.BatteryManager.Core

| 名称       | 值  | 说明              |
| -------- | ---- | ----------------- |
| NONE     | 0    | 表示未连接充电器。      |
| AC       | 1    | 表示连接的充电器类型为交流充电器。 |
| USB      | 2    | 表示连接的充电器类型为USB。   |
| WIRELESS | 3    | 表示连接的充电器类型为无线充电器。 |

## BatteryChargeState

表示电池充电状态的枚举。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.PowerManager.BatteryManager.Core

| 名称      | 值  | 说明            |
| ------- | ---- | --------------- |
| NONE    | 0    | 表示电池充电状态为未充电。     |
| ENABLE  | 1    | 表示电池充电状态为正在充电。  |
| DISABLE | 2    | 表示电池充电状态为充电禁用。  |
| FULL    | 3    | 表示电池充电状态为已充满状态。 |

## BatteryHealthState

表示电池健康状态的枚举。

**系统能力**：SystemCapability.PowerManager.BatteryManager.Core

| 名称          | 值  | 说明           |
| ----------- | ---- | -------------- |
| UNKNOWN     | 0    | 表示电池健康状态未知。    |
| GOOD        | 1    | 表示电池健康状态为正常。   |
| OVERHEAT    | 2    | 表示电池健康状态为过热。   |
| OVERVOLTAGE | 3    | 表示电池健康状态为过压。   |
| COLD        | 4    | 表示电池健康状态为低温。   |
| DEAD        | 5    | 表示电池健康状态为失效，即电池已无法正常使用。 |

## BatteryCapacityLevel<sup>9+</sup>

表示电池电量等级的枚举。可用于根据电量等级执行差异化策略，例如在低电量（LEVEL_LOW）或极低电量（LEVEL_CRITICAL）时限制后台任务和高功耗功能，在满电量（LEVEL_FULL）时解除限制。

**系统能力**：SystemCapability.PowerManager.BatteryManager.Core

| 名称           | 值 | 说明                       |
| -------------- | ------ | ---------------------------- |
| LEVEL_NONE<sup>23+</sup> | 0      | 表示电池电量等级为未知电量。说明系统无法获得当前的电池电量等级。 |
| LEVEL_FULL     | 1      | 表示电池电量等级为满电量。   |
| LEVEL_HIGH     | 2      | 表示电池电量等级为高电量。   |
| LEVEL_NORMAL   | 3      | 表示电池电量等级为正常电量。 |
| LEVEL_LOW      | 4      | 表示电池电量等级为低电量。   |
| LEVEL_WARNING  | 5      | 表示电池电量等级为告警电量。 |
| LEVEL_CRITICAL | 6      | 表示电池电量等级为极低电量。 |
| LEVEL_SHUTDOWN | 7      | 表示电池电量等级为关机电量。 |

## CommonEventBatteryChangedKey<sup>9+</sup>

表示COMMON_EVENT_BATTERY_CHANGED通用事件附加信息的查询键。开发者需先订阅COMMON_EVENT_BATTERY_CHANGED公共事件，在事件回调中通过这些查询键从事件附加数据中提取对应的电池状态信息。详细使用方法请参见[@ohos.commonEventManager (公共事件模块)](js-apis-commonEventManager.md)。

**系统能力**：SystemCapability.PowerManager.BatteryManager.Core

| 名称                 | 值 | 说明                                             |
| -------------------- | ------ | -------------------------------------------------- |
| EXTRA_SOC            | "soc" | 表示剩余电池电量百分比的查询键。                   |
| EXTRA_CHARGE_STATE   | "chargeState" | 表示当前设备电池充电状态的查询键。                 |
| EXTRA_HEALTH_STATE   | "healthState" | 表示当前设备电池健康状态的查询键。                 |
| EXTRA_PLUGGED_TYPE   | "pluggedType" | 表示当前设备连接的充电器类型的查询键。             |
| EXTRA_VOLTAGE        | "voltage" | 表示当前设备电池电压的查询键。                     |
| EXTRA_TECHNOLOGY     | "technology" | 表示当前设备电池技术型号的查询键。                 |
| EXTRA_TEMPERATURE    | "temperature" | 表示当前设备电池温度的查询键。                     |
| EXTRA_PRESENT        | "present" | 表示当前设备是否支持电池或者电池是否在位的查询键。 |
| EXTRA_CAPACITY_LEVEL | "capacityLevel" | 表示当前设备电池电量等级的查询键。                 |
