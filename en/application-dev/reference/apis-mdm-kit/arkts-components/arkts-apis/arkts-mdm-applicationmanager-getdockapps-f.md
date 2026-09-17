# getDockApps

## Modules to Import

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## getDockApps

```TypeScript
function getDockApps(admin: Want): Array<DockInfo>
```

Obtains the list of applications in the shortcut bar currently.

**Since:** 24

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[DockInfo](arkts-mdm-applicationmanager-dockinfo-i.md)&gt; | Array of application information in the shortcut bar. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |

**Examples**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  let result: Array<applicationManager.DockInfo> = applicationManager.getDockApps(wantTemp);
  console.info(`Succeeded in getting dock apps, result : ${JSON.stringify(result)}`);
} catch(err) {
  console.error(`Failed to get dock apps. Code: ${err.code}, message: ${err.message}`);
}
```

```TypeScript
// Return value example.
[
  {
    "bundleName": "com.example.edmtest",
    "abilityName": "EntryAbility",
    "index": 5
  },
  // ...
]
```
