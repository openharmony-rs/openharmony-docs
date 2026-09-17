# startCollectLog

## Modules to Import

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## startCollectLog

```TypeScript
function startCollectLog(admin: Want): Promise<void>
```

Starts to collect the fault logs of the [FaultType](../../apis-performance-analysis-kit/arkts-apis/arkts-performanceanalysis-faultlogger-faulttype-e.md) type that have been generated and stored on the device's hard disk. The fault logs, application service logs, and system runtime logs that are not stored on the hard disk cannot be collected.

- After the API is called, the system starts a log collection task. The API returns a response immediately after  
the task is started. The task may fail due to system performance constraints.  
- This API can be called by multiple MDM apps. Logs collected by different MDM apps under different users are saved  
separately and do not affect each other. Only one MDM app can start a log collection task at a time. If this API is called before the task is complete, the error code 9201009 is returned, and other MDM apps may call the API only after the task finishes.  
- Upon task completion, the MDM app is notified via the [EnterpriseAdminExtensionAbility.onLogCollected](arkts-mdm-enterprise-enterpriseadminextensionability-enterpriseadminextensionability-c.md#onlogcollected) callback. The system mounts the collected log files to the MDM app sandbox path, enabling the MDM app to read the logs within the callback.  
- If the log collection task takes more than 5 minutes, the [EnterpriseAdminExtensionAbility.onLogCollected](arkts-mdm-enterprise-enterpriseadminextensionability-enterpriseadminextensionability-c.md#onlogcollected) callback returns a task execution failure message.  
- After the app obtains the logs, you are advised to call [systemManager.finishLogCollected](arkts-mdm-systemmanager-finishlogcollected-f.md) to remove the collected logs.

**Since:** 23

**Required permissions:** ohos.permission.ENTERPRISE_READ_LOG

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. When a log collection task fails to be created, an error object is thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9201009](../errorcode-enterpriseDeviceManager.md#9201009-failed-to-create-a-log-collection-task) | Collecting logs, please try again later. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |

**Examples**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { systemManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

systemManager.startCollectLog(wantTemp).then(() => {
  console.info('Succeeded in starting collect log');
}).catch((err: BusinessError) => {
  console.error(`Failed to start collect log. Code: ${err.code}, message: ${err.message}`);
});
```
