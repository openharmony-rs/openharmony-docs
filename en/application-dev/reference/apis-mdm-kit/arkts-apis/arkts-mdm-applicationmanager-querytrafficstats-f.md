# queryTrafficStats

## Modules to Import

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## queryTrafficStats

```TypeScript
function queryTrafficStats(
    admin: Want,
    bundleName: string,
    appIndex: number,
    accountId: number,
    networkInfo: statistics.NetworkInfo
  ): Promise<statistics.NetStatsInfo>
```

Queries the data usage of a specified application within a specified period for the current user. This API uses a promise to return the result.

> **NOTE:** 
> 
> The input network type (**networkInfo.type**) can only be **connection.NetBearType.BEARER_CELLULAR** or
> **connection.NetBearType.BEARER_WIFI**. If any other value is passed, the API returns error code 9200012.
> 
> The input start time (**networkInfo.startTime**) and end time (**networkInfo.endTime**) are second-level
> timestamps. If the input start time and end time are negative numbers or the start time is later than the end
> time, the API returns error code 9200012.
> 
> If the input user ID (**accountId**) is not the ID of the current user, the API returns error code 9200012.
> 
> It is advised that the query interval (end time – start time) be 1 to 30 days. If the interval is too short, the
> query result may be inaccurate. If the interval is too long, the query will take a long time.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| bundleName | string | Yes | Bundle name of the application. |
| appIndex | number | Yes | Index of the application clone. The value is an integer greater than or equal to 0. <br> You can call [getAppCloneIdentity](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getappcloneidentity-f.md) of @ohos.bundle.bundleManager to obtain the index. |
| accountId | number | Yes | Account ID. The value is an integer greater than or equal to 0. <br> You can call [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid) of @ohos.account.osAccount to obtain the ID. |
| networkInfo | [statistics.NetworkInfo](../../apis-network-kit/arkts-apis/arkts-network-statistics-networkinfo-i.md) | Yes | Network information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[statistics.NetStatsInfo](../../apis-network-kit/arkts-apis/arkts-network-statistics-netstatsinfo-i.md)&gt; | Promise used to return the historical traffic information object. |

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
import { connection, statistics } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

async function queryTrafficStats() {
  let wantTemp: Want = {
    // Replace it as required.
    bundleName: 'com.example.myapplication',
    abilityName: 'EnterpriseAdminAbility'
  };
  // Replace it as required.
  let bundleName: string = 'com.example.test';
  let appIndex: number = 0;
  let accountId: number = 100;
  // In the sample code, sim.getSimAccountInfo is used to obtain the SIM ID.
  let slotId: number = 0;
  let simId: number = 0;
  await sim.getSimAccountInfo(slotId).then((data: sim.IccAccountInfo) => {
    simId = data.simId;
  }).catch((err: BusinessError) => {
    console.error(`getSimAccountInfo failed, promise: err->${JSON.stringify(err)}`);
  });
  let networkInfo: statistics.NetworkInfo = {
    // Replace it as required.
    type: connection.NetBearType.BEARER_CELLULAR,
    // Query data from 2026/4/15 00:00:00.000 to 2026/4/16 00:00:00.000. (The month starts from 0.)
    startTime: Math.floor(new Date(2026, 3, 15, 0, 0, 0, 0).getTime() / 1000),
    endTime: Math.floor(new Date(2026, 3, 16, 0, 0, 0, 0).getTime() / 1000),
    // If the network type is BEARER_CELLULAR, simId needs to be passed. If the network type is BEARER_WIFI, simId does not need to be passed.
    simId: simId
  }
  await applicationManager.queryTrafficStats(wantTemp, bundleName, appIndex, accountId, networkInfo)
    .then(result => {
      console.info('Succeeded in querying traffic stats.');
    }).catch((error: BusinessError) => {
      console.error(`Failed to query traffic stats. Code is ${error.code}, message is ${error.message}`);
    })
}
```
