# addOsAccountAsync

## Modules to Import

```TypeScript
import { accountManager } from '@kit.MDMKit';
```

## addOsAccountAsync

```TypeScript
function addOsAccountAsync(admin: Want, name: string, type: osAccount.OsAccountType): Promise<osAccount.OsAccountInfo>
```

Adds an account in the background. This API uses a promise to return the result. This API is applicable to scenarios where enterprises need to create accounts in batches or remotely manage accounts. Accounts can be created without user interaction, improving management efficiency.

> **NOTE:** 
> 
> This API is time-consuming. Subsequent calls to other synchronous APIs in the application main thread must wait
> for the asynchronous return of this API.

**Since:** 12

**Required permissions:** ohos.permission.ENTERPRISE_SET_ACCOUNT_POLICY

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| name | string | Yes | Account name, which is the name of the account to be added. An account with a duplicate name or an empty name cannot be created. An attempt to create a duplicate-name account will result in error code 9201003, and an attempt to create an account with an empty name will result in error code 401. |
| type | [osAccount.OsAccountType](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-osaccounttype-e.md) | Yes | Type of the account to add.<br>The value can be any of the following: <br>· **ADMIN**: administrator account. <br>· **NORMAL**: normal account. <br>· **GUEST**: guest account. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[osAccount.OsAccountInfo](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-osaccountinfo-i.md)&gt; | Promise used to return the added account information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9201003](../errorcode-enterpriseDeviceManager.md#9201003-failed-to-add-an-account) | Failed to add an OS account. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { accountManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError, osAccount } from '@kit.BasicServicesKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

// Replace parameters with actual values.
accountManager.addOsAccountAsync(wantTemp, "TestAccountName", osAccount.OsAccountType.NORMAL).then((info) => {
  console.info(`Succeeded in creating os account: ${JSON.stringify(info)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to create os account. Code: ${err.code}, message: ${err.message}`);
});
```
