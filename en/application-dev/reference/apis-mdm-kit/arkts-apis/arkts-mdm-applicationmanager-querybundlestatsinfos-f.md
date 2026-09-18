# queryBundleStatsInfos

## Modules to Import

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## queryBundleStatsInfos

```TypeScript
function queryBundleStatsInfos(admin: Want, startTime: number, endTime: number, accountId: number): Array<BundleStatsInfo>
```

Queries the accumulated foreground runtime statistics of applications under a specified user account within a given time period. The minimum query granularity is one day. The API requires the start time (**startTime**), end time (**endTime**), and target user account ID (**accountId**) to be passed in. **startTime** and **endTime** are millisecond-level timestamps. The caller can pass custom values. The default value of **startTime** is 00:00:00.000 of the current day, and the default of **endTime** is 24:00:00.000 of the current day (that is, 00:00:00 of the following day). The API returns an array of **BundleStatsInfo**, where each element contains the bundle name of an application, its clone index, and the foreground usage duration (in milliseconds) within the specified time period. If **startTime** is set to **0**, the query starts from the device's first boot time. If **startTime** is later than **endTime**, the API returns error code 9200012.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| startTime | number | Yes | Query start time, in milliseconds (timestamp).<br>Value range: [0, +∞). |
| endTime | number | Yes | Query end time, in milliseconds (timestamp).<br>Value range: [0, +∞). |
| accountId | number | Yes | Account ID. The value is an integer greater than or equal to 0. <br> You can call [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid) of @ ohos.account.osAccount to obtain the ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[BundleStatsInfo](arkts-mdm-applicationmanager-bundlestatsinfo-i.md)&gt; | Array of application bundle statistics. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |

**Examples**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // Query data from 2026/4/15 00:00:00.000 to 2026/4/16 23:59:59.999. (The month starts from 0.)
  let startTime: number = new Date(2026, 3, 15, 0, 0, 0, 0).getTime();
  let endTime: number = new Date(2026, 3, 16, 23, 59, 59, 999).getTime();
  let accountId: number = 100;
  let result: Array<applicationManager.BundleStatsInfo> = applicationManager.queryBundleStatsInfos(wantTemp, startTime, endTime, accountId);
  console.info(`Succeeded in querying bundle stats infos, result : ${JSON.stringify(result)}`);
} catch(err) {
  console.error(`Failed to query bundle stats infos. Code: ${err.code}, message: ${err.message}`);
}
```

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // Query data of the last month.
  // Obtain the current date.
  let currentDate: Date = new Date();
  // Calculate the first day of the last month. (The month starts from 0. Therefore, subtract 1 from the current month.)
  let lastMonthFirstDay: Date = new Date(currentDate.getFullYear(), currentDate.getMonth() - 1, 1, 0, 0, 0, 0);
  // Calculate the last day of the last month. (The 0th day of the next month is the last day of the current month.)
  let lastMonthLastDay: Date = new Date(currentDate.getFullYear(), currentDate.getMonth(), 0, 23, 59, 59, 999);
  
  let startTime: number = lastMonthFirstDay.getTime();
  let endTime: number = lastMonthLastDay.getTime();
  let accountId: number = 100;
  let result: Array<applicationManager.BundleStatsInfo> = applicationManager.queryBundleStatsInfos(wantTemp, startTime, endTime, accountId);
  console.info(`Succeeded in querying bundle stats infos, result : ${JSON.stringify(result)}`);
} catch(err) {
  console.error(`Failed to query bundle stats infos. Code: ${err.code}, message: ${err.message}`);
}
```
