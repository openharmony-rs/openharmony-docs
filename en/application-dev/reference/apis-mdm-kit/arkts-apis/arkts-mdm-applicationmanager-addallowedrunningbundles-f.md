# addAllowedRunningBundles

## Modules to Import

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## addAllowedRunningBundles

```TypeScript
function addAllowedRunningBundles(admin: Want, appIdentifiers: Array<string>, accountId: number): void
```

Adds applications to the application running trustlist. Only applications in the trustlist are allowed to run under the specified user.

> **NOTE:** 
> 
> 1. Most APIs provided by MDM Kit are available only to MDM applications. When using this API, add the MDM application to the application running trustlist. Otherwise, the MDM application will be prohibited from running,blocking the API call. For details about whether the API is open only to MDM applications, see the module description.
> 
> 2. If the application running blocklist is not empty, this API cannot be used to add applications to the running trustlist. Otherwise, the error code 9200010 is reported. APIs related to the application running blocklist include [addDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-adddisallowedrunningbundlessync-f.md).
> 
> 3. This API only takes effect for third-party applications. System applications are not subject to this list and are allowed to run by default.

**Since:** 21

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| appIdentifiers | Array&lt;string&gt; | Yes | Array of application [unique identifiers](../../../quick-start/common-problem-of-application.md#what-is-appidentifier). You can obtain **bundleInfo.signatureInfo.appIdentifier** through the [bundleManager.getInstalledBundleList](arkts-mdm-bundlemanager-getinstalledbundlelist-f.md) API. <br>Value range: <br> - The total number of entries in this list for a single user must not exceed 200. For example, if 50 entries have been set for user 100 and none for user 101, user 100 can add 150 more entries, while user 101 can add up to 200 entries. |
| accountId | number | Yes | Account ID, which must be greater than or equal to 0. <br> You can call [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid) of @ ohos.account.osAccount to obtain the ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200010](../errorcode-enterpriseDeviceManager.md#9200010-policy-conflict) | A conflict policy has been configured. |
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
// Replace it as required.
let appIdentifiers: Array<string> = ['0123456789123456789'];

try {
  applicationManager.addAllowedRunningBundles(wantTemp, appIdentifiers, 100);
  console.info('Succeeded in adding allowed running bundles.');
} catch (err) {
  console.error(`Failed to add allowed running bundles. Code is ${err.code}, message is ${err.message}`);
}
```
