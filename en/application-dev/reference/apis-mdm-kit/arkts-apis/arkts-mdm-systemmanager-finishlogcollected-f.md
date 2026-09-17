# finishLogCollected

## Modules to Import

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## finishLogCollected

```TypeScript
function finishLogCollected(admin: Want): void
```

Deletes the device logs collected by the current MDM app under the current user.

> **NOTE:** 
> 
> After the app calls [startCollectLog](arkts-mdm-systemmanager-startcollectlog-f.md) to initiate log collection and
> receives the
> [EnterpriseAdminExtensionAbility.onLogCollected](arkts-mdm-enterprise-enterpriseadminextensionability-enterpriseadminextensionability-c.md#onlogcollected)
> callback, you are advised to immediately copy or process the logs, and then call this API to delete the collected
> logs.
> 
> If this API is not called, device logs will occupy the system storage space, which does not affect the next call
> of [startCollectLog](arkts-mdm-systemmanager-startcollectlog-f.md) to start a log collection task.

**Since:** 23

**Required permissions:** ohos.permission.ENTERPRISE_READ_LOG

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |

**Examples**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { systemManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  systemManager.finishLogCollected(wantTemp);
  console.info('Succeeded in finishing log collected.');
} catch (err) {
  console.error(`Failed to finish log collected. Code is ${err.code}, message is ${err.message}`);
}
```
