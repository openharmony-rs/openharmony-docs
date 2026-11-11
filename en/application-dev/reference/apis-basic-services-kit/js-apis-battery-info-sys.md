# @ohos.batteryInfo (Battery Information) (System API)

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=2a67e7451b3dfcc746ff67349e2b0b9474fa54f8 translatedAt=2026-11-06T01:37:21.424Z pushedAt=2026-11-09T01:35:49.393Z nl=1 -->

This module provides APIs for setting and querying battery configurations by scenario, as well as querying key attributes such as the estimated battery charging time, total capacity, and remaining capacity. This module is applicable to system application development that requires real-time battery information or management of charging scenarios.

> **NOTE**
>
> The initial APIs of this module are supported since API version 6. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This topic describes only the system APIs provided by this module. For details about its public APIs, see [@ohos.batteryInfo (Battery Information)](js-apis-battery-info.md).


## Modules to Import

```js
import { batteryInfo } from '@kit.BasicServicesKit';
```

## batteryInfo.setBatteryConfig<sup>11+</sup>

setBatteryConfig(sceneName: string, sceneValue: string): number

Sets the battery configuration by scenario name. After this API is called, the system modifies the corresponding battery charging configuration based on the passed scenario name and scenario value, affecting the device charging behavior.

**System API**: This is a system API.

**System capability:** SystemCapability.PowerManager.BatteryManager.Core

**Parameters**

| Name    | Type  | Mandatory| Description        |
| ---------- | ------ | ---- | ------------ |
| sceneName  | string | Yes  | Scenario name of the battery charging configuration, which is used to identify a specific charging configuration scenario. The supported scenario names are system-defined. |
| sceneValue | string | Yes  | Value of the battery charging configuration scenario, which is used to specify the configuration parameters of the scenario. The value is system-defined. For example, **0** indicates that the charging configuration of the scenario is disabled. |

**Return value**

| Type  | Description                                                      |
| ------ | ---------------------------------------------------------- |
| number | Whether the battery configuration is successful. The value **0** indicates that the setting is successful, and a non-zero value indicates a failure. |

**Error codes**

For details about the error codes, see [Battery Info Error Codes](errorcode-battery-info.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 5100101 | Failed to connect to the service. |
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 202     | Permission verification failed. A non-system application calls a system API. |

**Example**

  ```ts
  import { batteryInfo } from '@kit.BasicServicesKit';

  let sceneName = 'xxx';
  let sceneValue = '0';
  let result = batteryInfo.setBatteryConfig(sceneName, sceneValue);

  console.info('The result is: ' + result);
  ```

## batteryInfo.getBatteryConfig<sup>11+</sup>

getBatteryConfig(sceneName: string): string

Obtains the battery configuration by scenario name. After this API is called, the system searches for and returns the corresponding battery charging configuration value based on the passed scenario name.

**System API**: This is a system API.

**System capability:** SystemCapability.PowerManager.BatteryManager.Core

**Parameters**

| Name   | Type  | Mandatory| Description        |
| --------- | ------ | ---- | ------------ |
| sceneName | string | Yes | Scenario name of the battery charging configuration, which is used to query a specific charging configuration scenario. The supported scenario names are system-defined. |

**Return value**

| Type  | Description                          |
| ------ | ------------------------------ |
| string | Battery charging configuration of the specified scenario. An empty string is returned if the scenario does not exist or is not configured. |

**Error codes**

For details about the error codes, see [Battery Info Error Codes](errorcode-battery-info.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 5100101 | Failed to connect to the service. |
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 202     | Permission verification failed. A non-system application calls a system API. |

**Example**

  ```ts
  import { batteryInfo } from '@kit.BasicServicesKit';

  let sceneName = 'xxx';
  let result = batteryInfo.getBatteryConfig(sceneName);

  console.info('The result is: ' + result);
  ```

## batteryInfo.isBatteryConfigSupported<sup>11+</sup>

isBatteryConfigSupported(sceneName: string): boolean

Checks whether the battery configuration is enabled by scenario name. After this API is called, the system determines whether the current device supports the specified charging scenario configuration and returns the check result.

**System API**: This is a system API.

**System capability:** SystemCapability.PowerManager.BatteryManager.Core

**Parameters**

| Name   | Type  | Mandatory| Description        |
| --------- | ------ | ---- | ------------ |
| sceneName | string | Yes | Scenario name of the battery charging configuration, which is used to check whether the charging configuration scenario is supported. The supported scenario names are system-defined. |

**Return value**

| Type   | Description                                             |
| ------- | ------------------------------------------------- |
| boolean | The value **true** indicates that the device supports the battery configuration of the scenario; **false** indicates otherwise. |

**Error codes**

For details about the error codes, see [Battery Info Error Codes](errorcode-battery-info.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 5100101 | Failed to connect to the service. |
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 202     | Permission verification failed. A non-system application calls a system API. |

**Example**

  ```ts
  import { batteryInfo } from '@kit.BasicServicesKit';

  let sceneName = 'xxx';
  let result = batteryInfo.isBatteryConfigSupported(sceneName);

  console.info('The result is: ' + result);
  ```

## Constants

Describes battery information.

**System capability**: SystemCapability.PowerManager.BatteryManager.Core

| Name     | Type       | Read-Only|  Description    |
| --------------- | ------------------- | ---- | ---------------------|
| estimatedRemainingChargeTime<sup>9+</sup> | number                                         | Yes  | Estimated time for fully charging the current device, in milliseconds. This is a system API.         |
| totalEnergy<sup>9+</sup>                  | number                                         | Yes  | Total battery capacity of the device, in mAh. This is a system API.  |
| remainingEnergy<sup>9+</sup>              | number                                         | Yes  | Remaining battery capacity of the device, in mAh. This is a system API.|

**Example**
  ```ts
  import { batteryInfo } from '@kit.BasicServicesKit';

  let estimatedRemainingChargeTimeInfo: number = batteryInfo.estimatedRemainingChargeTime;
  console.info('The estimatedRemainingChargeTimeInfo is: ' + estimatedRemainingChargeTimeInfo);

  let totalEnergyInfo: number = batteryInfo.totalEnergy;
  console.info('The totalEnergyInfo is: ' + totalEnergyInfo);

  let remainingEnergyInfo: number = batteryInfo.remainingEnergy;
  console.info('The remainingEnergyInfo is: ' + remainingEnergyInfo);
  ```

