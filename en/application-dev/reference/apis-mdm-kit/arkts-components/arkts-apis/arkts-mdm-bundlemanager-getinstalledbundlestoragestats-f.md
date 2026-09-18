# getInstalledBundleStorageStats

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.MDMKit';
```

## getInstalledBundleStorageStats

```TypeScript
function getInstalledBundleStorageStats(admin: Want, bundleNames: Array<string>, accountId: number): Promise<Array<BundleStorageStats>>
```

Obtains the storage usage of installed applications of a specified user on a device. This API uses a promise to return the result.

> **NOTE:** 
> 
> 1. Only the storage usage of installed applications can be obtained.
> 
> 2. If **bundleNames** is empty or all bundle names passed are of uninstalled applications, error code 9200012will be returned.
> 
> 3. If some of the applications specified in the **bundleNames** parameter are installed and some are not, the API returns normally. For installed applications, their actual storage usage information is returned. For uninstalled applications, **0** is returned as their storage usage.
> 
> 4. This API supports cross-user queries. For example, user 100 can query the storage usage of some applications of user 101.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ENTERPRISE_GET_ALL_BUNDLE_INFO

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| bundleNames | Array&lt;string&gt; | Yes | Application bundle name list. The list must contain no more than 200 bundle names. |
| accountId | number | Yes | User ID, which must be greater than or equal to 0. <br> You can call [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid) of **@ohos.account.osAccount** to obtain the user ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[BundleStorageStats](arkts-mdm-bundlemanager-bundlestoragestats-i.md)&gt;&gt; | Promise used to return the storage usage information of the installed applications. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |

**Examples**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { bundleManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let bundleNames: Array<string> = ['com.example.app1', 'com.example.app2'];
let accountId: number = 100;
bundleManager.getInstalledBundleStorageStats(wantTemp, bundleNames, accountId).then((result) => {
  console.info('Succeeded in getting installed bundle storage stats.');
}).catch((err: BusinessError) => {
  console.error(`Failed to get installed bundle storage stats. Code is ${err.code}, message is ${err.message}`);
});
```

```TypeScript
// Return value example.
[
  {
    "bundleName": "com.example.edmtest",
    "appSize": 38185408,
    "dataSize": 1216566
  },
  // ...
]
```
