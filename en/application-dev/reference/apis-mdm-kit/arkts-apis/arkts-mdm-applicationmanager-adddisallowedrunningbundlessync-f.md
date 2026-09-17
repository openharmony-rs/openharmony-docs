# addDisallowedRunningBundlesSync

## Modules to Import

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## addDisallowedRunningBundlesSync

```TypeScript
function addDisallowedRunningBundlesSync(
    admin: Want,
    appIds: Array<string>,
    accountId?: number
  ): void
```

Adds applications to the application running blocklist. Applications added to the blocklist are not allowed to run under the current or specified user. Since API version 21, if the application running trustlist [addAllowedRunningBundles](arkts-mdm-applicationmanager-addallowedrunningbundles-f.md) is not empty, the application running blocklist cannot be added via this API. Otherwise, the error code 9200010 is reported.

> **NOTE:** 
> 
> If a specified application is running, the system will immediately terminate the application process once it is
> added to the blocklist.

**Since:** 12

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| appIds | Array&lt;string&gt; | Yes | IDs of the applications to add. <br>**Note:**  From API version 21 onwards, the [appId](../../../quick-start/common-problem-of-application.md#what-is-appid) and [appIdentifier](../../../quick-start/common-problem-of-application.md#what-is-appidentifier) of the app can be passed. **appIdentifier** is recommended. In API version 20 and earlier versions, only **appId** can be passed. <br>Value range: <br> The total number of entries in this list for a single user must not exceed 200. For example, if 50 entries have been set for user 100 and none for user 101, user 100 can add 150 more entries, while user 101 can add up to 200 entries. |
| accountId | number | No | Account ID, which must be greater than or equal to 0. <br> You can call [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid) of @ ohos.account.osAccount to obtain the ID. <br> - If **accountId** is passed in, this API applies to the specified user. <br> - If **accountId** is not passed in, this API applies to the current user. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9200010](../errorcode-enterpriseDeviceManager.md#9200010-policy-conflict) | A conflict policy has been configured.<br>**Applicable version:** 21 and later |

**Examples**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace it as required.
let appIds: Array<string> = ['com.example.******_******/******5t5CoBM='];

try {
  applicationManager.addDisallowedRunningBundlesSync(wantTemp, appIds);
  console.info('Succeeded in adding disallowed running bundles.');
} catch (err) {
  console.error(`Failed to add disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
}
```
