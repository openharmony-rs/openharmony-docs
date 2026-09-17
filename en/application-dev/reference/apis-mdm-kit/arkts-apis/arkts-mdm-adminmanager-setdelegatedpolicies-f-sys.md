# setDelegatedPolicies (System API)

## Modules to Import

```TypeScript
import { adminManager } from '@kit.MDMKit';
```

## setDelegatedPolicies

```TypeScript
function setDelegatedPolicies(bundleName: string, accountId: number, policies: Array<string>): void
```

Delegates other applications to set device management policies. The applications must request the permissions required.

**Since:** 20

**Required permissions:** ohos.permission.MANAGE_ENTERPRISE_DEVICE_ADMIN

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the app to be delegated. The distribution type of the delegated app must be **enterprise_normal** or **enterprise_mdm**. You can call the [bundleManager.getBundleInfoForSelf](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfoforself-f.md) API to query the app **BundleInfo**. **BundleInfo.appInfo.appDistributionType** indicates the app distribution type. |
| accountId | number | Yes | User ID, which must be greater than or equal to 0. You can use [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid) to obtain the user ID. |
| policies | Array&lt;string&gt; | Yes | [Delegable policy list](../../../mdm/mdm-kit-appendix.md#delegable-policy-list). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200009](../errorcode-enterpriseDeviceManager.md#9200009-failed-to-grant-permissions-to-an-application) | Failed to grant the permission to the application. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { adminManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let admin: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let policies: Array<string> = ["disabled_hdc"];

try {
  // Replace parameters with actual values.
  adminManager.setDelegatedPolicies(admin, "com.example.enterprise.xxx", policies);
  console.info('Succeeded in setting delegated policies.');
} catch (err) {
  console.error(`Failed to set delegated policies. Code: ${err.code}, message: ${err.message}`);
}
```

```TypeScript
import { adminManager } from '@kit.MDMKit';
import { common, Want } from '@kit.AbilityKit';

// Replace with actual values.
let bundleName = 'com.example.myapplication';
let userId = 100;
let policies: Array<string> = ["disabled_hdc"];

try {
  adminManager.setDelegatedPolicies(bundleName, userId, policies);
  console.info(`Succeeded in setting delegated policies.`);
} catch (err) {
  console.error(`Failed to set delegated policies. Code: ${err.code}, message: ${err.message}`);
}
```
