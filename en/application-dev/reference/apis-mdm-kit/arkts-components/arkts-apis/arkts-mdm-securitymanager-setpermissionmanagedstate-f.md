# setPermissionManagedState

## Modules to Import

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## setPermissionManagedState

```TypeScript
function setPermissionManagedState(
    admin: Want,
    applicationInstance: ApplicationInstance,
    permissions: Array<string>,
    managedState: PermissionManagedState
  ): void
```

Sets the management policy for the [user_grant permission](../../apis-ability-kit/arkts-apis/arkts-ability-permissions-t.md) of a specified application. This is applicable to enterprise application batch deployment scenarios, such as granting permissions silently to reduce permission prompt interruptions, and unifying permission management policies for enterprise applications, thereby improving employee user experience and management efficiency.

**Since:** 20

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_USER_GRANT_PERMISSION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| applicationInstance | [ApplicationInstance](arkts-mdm-securitymanager-applicationinstance-i.md) | Yes | Application instance. |
| permissions | Array&lt;string&gt; | Yes | List of permissions to be managed. Only [user_grant permission](../../apis-ability-kit/arkts-apis/arkts-ability-permissions-t.md) is supported. The list is grouped by [application permission groups](../../../security/AccessToken/app-permission-group-list.md) and must include all permissions in the same permission group declared by the application in [module.json5](../../../quick-start/module-configuration-file.md). For example, if an application declares ohos.permission.READ_CALENDAR and ohos.permission.WRITE_CALENDAR in **module.json5**, the input permission list must contain both ohos.permission.READ_CALENDAR and ohos.permission.WRITE_CALENDAR. |
| managedState | [PermissionManagedState](arkts-mdm-securitymanager-permissionmanagedstate-e.md) | Yes | Management policy for application permissions. |

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
import { Want } from '@kit.AbilityKit';
import { securityManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let appInstanceTemp: securityManager.ApplicationInstance = {
  // Replace with actual values.
  appIdentifier: '736498586',
  appIndex: 0,
  accountId: 100
};
let permissionsTemp: Array<string> = ['ohos.permission.CAMERA', 'ohos.permission.LOCATION'];
try {
  securityManager.setPermissionManagedState(wantTemp, appInstanceTemp, permissionsTemp, securityManager.PermissionManagedState.GRANTED);
  console.info('Succeeded in setting permission managed state.');
} catch(err) {
  console.error(`Failed to set permission managed state.  Code: ${err.code}, message: ${err.message}`);
}
```
