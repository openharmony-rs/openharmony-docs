# getApplicationWindowStates

## Modules to Import

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## getApplicationWindowStates

```TypeScript
function getApplicationWindowStates(admin: Want, bundleName: string, appIndex: number): Array<WindowStateInfo>
```

Queries the window state information list of the specified application. It can retrieve information such as whether the application is in the bottom dock and whether the application window is currently displayed in the foreground.

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

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[WindowStateInfo](arkts-mdm-applicationmanager-windowstateinfo-i.md)&gt; | Array of the application window state information. |

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
// Bundle name of the application to be queried. Replace it as required.
let bundleName: string = 'com.example.myapplication';
// Clone index of the queried application. Replace it as required.
let appIndex: number = 0;
try {
  let result: Array<applicationManager.WindowStateInfo> = applicationManager.getApplicationWindowStates(wantTemp, bundleName, appIndex);
  console.info(`Succeeded in getting application window states, result: ${JSON.stringify(result)}`);
} catch(err) {
  console.error(`Failed to get application window states. Code: ${err.code}, message: ${err.message}`);
}
```
