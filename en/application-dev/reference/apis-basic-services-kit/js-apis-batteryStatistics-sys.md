# @ohos.batteryStatistics (Battery Statistics) (System API)

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=6dc527860f3765d2a9feee01626042c27a272bab translatedAt=2026-11-06T01:40:11.068Z pushedAt=2026-11-09T02:05:02.430Z nl=1 -->

This module provides APIs for querying the battery statistics of software and hardware. It supports querying the power consumption and power consumption percentage of apps and hardware units. It can be used to monitor and analyze the power consumption of devices, helping identify apps or hardware components with high power consumption and optimize the energy consumption performance of apps accordingly.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs provided by this module are system APIs.

## Modules to Import

```js
import { batteryStats, BusinessError } from '@kit.BasicServicesKit';
```

## batteryStats.getBatteryStats

getBatteryStats(): Promise<Array&lt;BatteryStatsInfo&gt;>

Obtains an array of the power consumption information. This method can be used by battery monitoring apps to view the power consumption of each app and hardware unit. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.PowerManager.BatteryStatistics

**Return value**

| Type                                                 | Description                           |
| ----------------------------------------------------- | ------------------------------- |
| Promise<Array<[BatteryStatsInfo](#batterystatsinfo)>> | Promise used to return the power consumption information list.|

**Error codes**

For details about the error codes, see [Power Consumption Statistics Error Codes](errorcode-batteryStatistics.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 4600101 | Failed to connect to the service. |
| 202     | Permission verification failed. A non-system application calls a system API.  |

**Example**

```js
batteryStats.getBatteryStats()
.then((data: batteryStats.BatteryStatsInfo[]) => {
    console.info('battery statistics info: ' + data);
})
.catch((err: BusinessError) => {
    console.error(`Failed to get battery statistics. Code: ${err.code}, message: ${err.message}`);
});
```

## batteryStats.getBatteryStats

getBatteryStats(callback: AsyncCallback<Array&lt;BatteryStatsInfo&gt;>): void

Obtains an array of the power consumption information. This method can be used by battery monitoring apps to view the power consumption of each app and hardware unit. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.PowerManager.BatteryStatistics

**Parameters**

| Name  | Type                                                       | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback<Array<[BatteryStatsInfo](#batterystatsinfo)>> | Yes  | Callback used to return the result. If the operation is successful, **err** is undefined and **data** is the obtained Array<[BatteryStatsInfo](#batterystatsinfo)>. Otherwise, **err** is an error object. **AsyncCallback** has encapsulated an API of the **BatteryStatsInfo** class.|

**Error codes**

For details about the error codes, see [Power Consumption Statistics Error Codes](errorcode-batteryStatistics.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 4600101 | Failed to connect to the service. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 202     | Permission verification failed. A non-system application calls a system API.  |

**Example**

```js
batteryStats.getBatteryStats((err: BusinessError, data: batteryStats.BatteryStatsInfo[]) => {
    if (err) {
        console.error(`Failed to get battery statistics. Code: ${err.code}, message: ${err.message}`);
    } else {
        console.info('battery statistics info: ' + data);
    }
});
```

## batteryStats.getAppPowerValue

getAppPowerValue(uid: number): number

Obtains the power consumption of an app, in mAh. This API is applicable to scenarios where precise power consumption values are required. To compare the power consumption proportions of different apps, use **getAppPowerPercent** to obtain the relative percentage.

**System API**: This is a system API.

**System capability**: SystemCapability.PowerManager.BatteryStatistics

**Parameters**

| Name| Type  | Mandatory| Description       |
| ------ | ------ | ---- | ----------- |
| uid    | number | Yes   | App UID, which specifies the target app whose power consumption is to be queried. It can be obtained using [bundleManager.getBundleInfoForSelf](../apis-ability-kit/js-apis-bundleManager.md#bundlemanagergetbundleinfoforself). |

**Return value**

| Type  | Description                             |
| ------ | --------------------------------- |
| number | Power consumption of the application with this UID, in unit of mAh.|

**Error codes**

For details about the error codes, see [Power Consumption Statistics Error Codes](errorcode-batteryStatistics.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 4600101 | Failed to connect to the service. |
| 202     | Permission verification failed. A non-system application calls a system API.  |
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```js
try {
    let value = batteryStats.getAppPowerValue(10021); // 10021 is a sample UID. In actual use, obtain the application UID through APIs such as bundleManager.getBundleInfoForSelf.
    console.info('battery statistics value of app is: ' + value);
} catch (err) {
    console.error(`Failed to get battery statistics value of app. Code: ${err.code}, message: ${err.message}`);
}
```

## batteryStats.getAppPowerPercent

getAppPowerPercent(uid: number): number

Obtains the power consumption percentage of an app. This percentage indicates the proportion of the power consumption by this app to the total power consumption.

**System API**: This is a system API.

**System capability**: SystemCapability.PowerManager.BatteryStatistics

**Parameters**

| Name| Type  | Mandatory| Description       |
| ------ | ------ | ---- | ----------- |
| uid    | number | Yes   | UID of the app, which specifies the target app whose power consumption percentage is to be queried. The app UID can be obtained using APIs such as [bundleManager.getBundleInfoForSelf](../apis-ability-kit/js-apis-bundleManager.md#bundlemanagergetbundleinfoforself). |

**Return value**

| Type  | Description                     |
| ------ | ------------------------- |
| number | Proportion of the power consumption by the app with the specified UID. The value range is [0.00, 1.00]. |

**Error codes**

For details about the error codes, see [Power Consumption Statistics Error Codes](errorcode-batteryStatistics.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 4600101 | Failed to connect to the service. |
| 202     | Permission verification failed. A non-system application calls a system API.  |
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```js
try {
    let percent = batteryStats.getAppPowerPercent(10021); // 10021 is a sample UID. In actual use, obtain the app UID using APIs such as bundleManager.getBundleInfoForSelf.
    console.info('battery statistics percent of app is: ' + percent);
} catch (err) {
    console.error(`Failed to get battery statistics percent of app. Code: ${err.code}, message: ${err.message}`);
}
```

## batteryStats.getHardwareUnitPowerValue

getHardwareUnitPowerValue(type: ConsumptionType): number

Obtains the power consumption of a hardware unit based on the consumption type, in mAh. This API is applicable to scenarios where precise power consumption values are required. To compare the power consumption proportions of different hardware units, use **getHardwareUnitPowerPercent** to obtain the relative percentage.

**System API**: This is a system API.

**System capability**: SystemCapability.PowerManager.BatteryStatistics

**Parameters**

| Name| Type                               | Mandatory| Description          |
| ------ | ----------------------------------- | ---- | -------------- |
| type   | [ConsumptionType](#consumptiontype) | Yes   | Power consumption type, which specifies the hardware power consumption type to query. For the available values, see [ConsumptionType](#consumptiontype). For example, **CONSUMPTION_TYPE_SCREEN** queries the screen power consumption, **CONSUMPTION_TYPE_BLUETOOTH** queries the Bluetooth power consumption, and **CONSUMPTION_TYPE_WIFI** queries the Wi-Fi power consumption. |

**Return value**

| Type  | Description                                      |
| ------ | ------------------------------------------ |
| number | Power consumption of the hardware unit corresponding to the power consumption type, in unit of mAh.|

**Error codes**

For details about the error codes, see [Power Consumption Statistics Error Codes](errorcode-batteryStatistics.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 4600101 | Failed to connect to the service. |
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 202     | Permission verification failed. A non-system application calls a system API.  |

**Example**

```js
try {
    let powerValue = batteryStats.getHardwareUnitPowerValue(batteryStats.ConsumptionType.CONSUMPTION_TYPE_SCREEN);
    console.info('battery statistics value of hardware is: ' + powerValue);
} catch (err) {
    console.error(`Failed to get battery statistics value of hardware. Code: ${err.code}, message: ${err.message}`);
}
```

## batteryStats.getHardwareUnitPowerPercent

getHardwareUnitPowerPercent(type: ConsumptionType): number

Obtains the power consumption percentage of a hardware unit based on the consumption type. This percentage indicates the proportion of the power consumption by the specified hardware unit to the total power consumption.

**System API**: This is a system API.

**System capability**: SystemCapability.PowerManager.BatteryStatistics

**Parameters**

| Name| Type                               | Mandatory| Description          |
| ------ | ----------------------------------- | ---- | -------------- |
| type   | [ConsumptionType](#consumptiontype) | Yes   | Power consumption type of the hardware unit to query. For the available values, see [ConsumptionType](#consumptiontype). For example, **CONSUMPTION_TYPE_SCREEN** queries the screen power consumption percentage, **CONSUMPTION_TYPE_BLUETOOTH** queries the Bluetooth power consumption percentage, and **CONSUMPTION_TYPE_WIFI** queries the Wi-Fi power consumption percentage. |

**Return value**

| Type  | Description                              |
| ------ | ---------------------------------- |
| number | Proportion of the power consumption by the hardware unit with the specified power consumption type. The value range is [0.00, 1.00]. |

**Error codes**

For details about the error codes, see [Power Consumption Statistics Error Codes](errorcode-batteryStatistics.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 4600101 | Failed to connect to the service. |
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 202     | Permission verification failed. A non-system application calls a system API. |

**Example**

```js
try {
    let percent = batteryStats.getHardwareUnitPowerPercent(batteryStats.ConsumptionType.CONSUMPTION_TYPE_SCREEN);
    console.info('battery statistics percent of hardware is: ' + percent);
} catch (err) {
    console.error(`Failed to get battery statistics percent of hardware. Code: ${err.code}, message: ${err.message}`);
}
```

## BatteryStatsInfo

Describes the battery statistics information of the device software and hardware.

**System API**: This is a system API.

**System capability**: SystemCapability.PowerManager.BatteryStatistics

### Attributes

| Name | Type                               | Read-Only| Optional| Description                  |
| ----- | ----------------------------------- | ---- | ---- | ---------------------- |
| uid   | number                              | No   | No   | UID of the app with the specified power consumption.  |
| type  | [ConsumptionType](#consumptiontype) | No   | No   | Power consumption type.   |
| power | number                              | No  | No  | Power consumption, in unit of mAh.|

## ConsumptionType

Enumerates power consumption types.

**System API**: This is a system API.

**System capability**: SystemCapability.PowerManager.BatteryStatistics

| Name                      | Value  | Description                         |
| -------------------------- | ---- | ----------------------------- |
| CONSUMPTION_TYPE_INVALID   | -17  | Unknown type.       |
| CONSUMPTION_TYPE_APP       | -16  | Power consumption of an application.     |
| CONSUMPTION_TYPE_BLUETOOTH | -15  | Power consumption of Bluetooth.     |
| CONSUMPTION_TYPE_IDLE      | -14  | Power consumption when the CPU is idle.|
| CONSUMPTION_TYPE_PHONE     | -13  | Power consumption of a phone call.  |
| CONSUMPTION_TYPE_RADIO     | -12  | Power consumption of cellular communication.  |
| CONSUMPTION_TYPE_SCREEN    | -11  | Power consumption of the screen.     |
| CONSUMPTION_TYPE_USER      | -10  | Power consumption of the user.     |
| CONSUMPTION_TYPE_WIFI      | -9   | Power consumption of Wi-Fi.   |
