# @ohos.batteryInfo (电量信息)(系统接口)

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->

该模块提供按场景设置和查询电池配置的能力，还提供电池预估充电时间、总容量、剩余容量等关键属性的查询，适用于需要实时获取电池信息或管理充电场景的系统应用开发。

> **说明：**
>
> 本模块首批接口从 API version 6开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
>当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.batteryInfo (电量信息)](js-apis-battery-info.md)。


## 导入模块

```js
import { batteryInfo } from '@kit.BasicServicesKit';
```

## batteryInfo.setBatteryConfig<sup>11+</sup>

setBatteryConfig(sceneName: string, sceneValue: string): number

按场景名称设置电池配置。调用该接口后，系统将根据传入的场景名称和场景值修改对应的电池充电配置，影响设备充电行为。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.PowerManager.BatteryManager.Core

**参数**：

| 参数名     | 类型   | 必填 | 说明         |
| ---------- | ------ | ---- | ------------ |
| sceneName  | string | 是   | 电池充电配置的场景名称，用于标识特定的充电配置场景。支持的场景名称由系统定义。 |
| sceneValue | string | 是   | 电池充电配置场景的值，用于指定场景的具体配置参数。取值由系统定义，例如'0'表示关闭该场景的充电配置。 |

**返回值**：

| 类型   | 说明                                                       |
| ------ | ---------------------------------------------------------- |
| number | 返回设置电池配置的结果。返回0表示设置成功，返回非0表示设置失败。 |

**错误码：**

以下错误码的详细介绍请参见[电量信息错误码](errorcode-battery-info.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息    |
|---------|---------|
| 5100101 | Failed to connect to the service. |
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 202     | Permission verification failed. A non-system application calls a system API. |

**示例**：

  ```ts
  import { batteryInfo } from '@kit.BasicServicesKit';

  let sceneName = 'xxx';
  let sceneValue = '0';
  let result = batteryInfo.setBatteryConfig(sceneName, sceneValue);

  console.info('The result is: ' + result);
  ```

## batteryInfo.getBatteryConfig<sup>11+</sup>

getBatteryConfig(sceneName: string): string

按场景名称查询电池配置。调用该接口后，系统将根据传入的场景名称查找并返回对应的电池充电配置值。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.PowerManager.BatteryManager.Core

**参数**：

| 参数名    | 类型   | 必填 | 说明         |
| --------- | ------ | ---- | ------------ |
| sceneName | string | 是   | 电池充电配置的场景名称，用于查询特定的充电配置场景。支持的场景名称由系统定义。 |

**返回值**：

| 类型   | 说明                           |
| ------ | ------------------------------ |
| string | 返回指定场景的电池充电配置值；如果该场景不存在或未配置，则返回空字符串。 |

**错误码：**

以下错误码的详细介绍请参见[电量信息错误码](errorcode-battery-info.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息    |
|---------|---------|
| 5100101 | Failed to connect to the service. |
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 202     | Permission verification failed. A non-system application calls a system API. |

**示例**：

  ```ts
  import { batteryInfo } from '@kit.BasicServicesKit';

  let sceneName = 'xxx';
  let result = batteryInfo.getBatteryConfig(sceneName);

  console.info('The result is: ' + result);
  ```

## batteryInfo.isBatteryConfigSupported<sup>11+</sup>

isBatteryConfigSupported(sceneName: string): boolean

检查是否按场景名称启用电池配置。调用该接口后，系统将判断当前设备是否支持指定的充电场景配置，并返回检查结果。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.PowerManager.BatteryManager.Core

**参数**：

| 参数名    | 类型   | 必填 | 说明         |
| --------- | ------ | ---- | ------------ |
| sceneName | string | 是   | 电池充电配置的场景名称，用于检查是否支持该充电配置场景。支持的场景名称由系统定义。 |

**返回值**：

| 类型    | 说明                                              |
| ------- | ------------------------------------------------- |
| boolean | 如果设备支持该场景的电池配置，则返回true，否则返回false。 |

**错误码：**

以下错误码的详细介绍请参见[电量信息错误码](errorcode-battery-info.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息    |
|---------|---------|
| 5100101 | Failed to connect to the service. |
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 202     | Permission verification failed. A non-system application calls a system API. |

**示例**：

  ```ts
  import { batteryInfo } from '@kit.BasicServicesKit';

  let sceneName = 'xxx';
  let result = batteryInfo.isBatteryConfigSupported(sceneName);

  console.info('The result is: ' + result);
  ```

## 常量

描述电池信息。

**系统能力**：SystemCapability.PowerManager.BatteryManager.Core

| 名称      | 类型        | 只读 |  说明     |
| --------------- | ------------------- | ---- | ---------------------|
| estimatedRemainingChargeTime<sup>9+</sup> | number                                         | 是   | 表示当前设备充满电的预估时间，单位毫秒。此接口为系统接口。          |
| totalEnergy<sup>9+</sup>                  | number                                         | 是   | 表示当前设备电池的总容量，单位毫安时。此接口为系统接口。   |
| remainingEnergy<sup>9+</sup>              | number                                         | 是   | 表示当前设备电池的剩余容量，单位毫安时。此接口为系统接口。 |

**示例**：
  ```ts
  import { batteryInfo } from '@kit.BasicServicesKit';

  let estimatedRemainingChargeTimeInfo: number = batteryInfo.estimatedRemainingChargeTime;
  console.info('The estimatedRemainingChargeTimeInfo is: ' + estimatedRemainingChargeTimeInfo);

  let totalEnergyInfo: number = batteryInfo.totalEnergy;
  console.info('The totalEnergyInfo is: ' + totalEnergyInfo);

  let remainingEnergyInfo: number = batteryInfo.remainingEnergy;
  console.info('The remainingEnergyInfo is: ' + remainingEnergyInfo);
  ```

