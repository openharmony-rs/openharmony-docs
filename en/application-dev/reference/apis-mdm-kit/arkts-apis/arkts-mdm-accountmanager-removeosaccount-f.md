# removeOsAccount

## Modules to Import

```TypeScript
import { accountManager } from '@kit.MDMKit';
```

## removeOsAccount

```TypeScript
function removeOsAccount(admin: Want, accountId: number): Promise<void>
```

Removes a system account. Currently, this API is supported only on phones and tablets. It can remove normal system accounts (of the normal type) created via [createNormalOsAccount](arkts-mdm-accountmanager-createnormalosaccount-f.md) and system accounts (of the admin, normal, and guest types) created via [addOsAccountAsync](arkts-mdm-accountmanager-addosaccountasync-f.md). The default system account (ID: 100) cannot be removed.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_LOCAL_ACCOUNTS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| accountId | number | Yes | ID of the system account to be removed. The default system account (ID: 100) cannot be removed. Otherwise, error code 9201041 is reported. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. If the operation fails., an error object is thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-service-timeout) | Service timeout. |
| [9201041](../errorcode-enterpriseDeviceManager.md#9201041-system-account-type-restricted) | Restricted account. |
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

// Create a normal system account.
accountManager.createNormalOsAccount(wantTemp, "TestAccountName").then((accountInfo: osAccount.OsAccountInfo) => {
  console.info('Succeeded in creating normal os account, accountInfo: ' + JSON.stringify(accountInfo));
  // Remove the created account based on the system account ID.
  let accountId: number = accountInfo.localId;
  return accountManager.removeOsAccount(wantTemp, accountId);
}).then(() => {
  console.info('Succeeded in removing os account');
}).catch((err: BusinessError) => {
  console.error(`Failed to create and remove normal os account: code is ${err.code}, message is ${err.message}`);
});
```
