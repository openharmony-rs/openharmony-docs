# createNormalOsAccount

## Modules to Import

```TypeScript
import { accountManager } from '@kit.MDMKit';
```

## createNormalOsAccount

```TypeScript
function createNormalOsAccount(admin: Want, name: string): Promise<osAccount.OsAccountInfo>
```

Creates a normal system account. A maximum of two normal system accounts ([osAccount.OsAccountType](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-osaccounttype-e.md)) can be created.

> **NOTE:** 
> 
> The account creation process is time-consuming. Subsequent calls to other synchronous APIs in the application
> main thread must wait for the asynchronous return of this API.
> 
> Creating a system account has a significant impact on device performance. This API is supported only on phones
> and tablets with 12 GB or more of RAM.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_LOCAL_ACCOUNTS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| name | string | Yes | System account name. The system account name must be unique and cannot be empty. Otherwise, error code 9200012 is reported. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[osAccount.OsAccountInfo](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-osaccountinfo-i.md)&gt; | Promise used to return the information about the created system account. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [9201003](../errorcode-enterpriseDeviceManager.md#9201003-failed-to-add-an-account) | Failed to add an OS account. |
| [9201040](../errorcode-enterpriseDeviceManager.md#9201040-system-account-count-has-reached-the-upper-limit) | The number of accounts reaches the upper limit. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [204](../../errorcode-universal.md#204-access-denied-by-user-access-control-policy) | Access denied due to user access control policy. Possible causes: 1. The operation is restricted by the OS-account constraint. 2. The required privilege for the operation has not been granted. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |

**Examples**

```TypeScript
import { accountManager } from '@kit.MDMKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { osAccount } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

// Create a normal system account. The account name needs to be passed.
accountManager.createNormalOsAccount(wantTemp, "TestAccountName").then((accountInfo: osAccount.OsAccountInfo) => {
  console.info('Succeeded in creating normal os account, accountInfo: ' + JSON.stringify(accountInfo));
}).catch((err: BusinessError) => {
  console.error(`Failed to create normal os account: code is ${err.code}, message is ${err.message}`);
});
```
