# startExactTimer

## Modules to Import

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## startExactTimer

```TypeScript
function startExactTimer(timer: number, triggerTime: number): Promise<void>
```

Starts an exact timer. This API uses a promise to return the result.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| timer | number | Yes | ID of the timer, which is obtained by calling [systemManager.createExactTimer](arkts-mdm-systemmanager-createexacttimer-f.md). |
| triggerTime | number | Yes | Time when the timer is triggered, in milliseconds. The value is the system startup time, which can be obtained by calling [systemDateTime.getUptime(STARTUP)](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-systemdatetime-getuptime-f.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-service-timeout) | Service timeout. |
| 9201054 | The specified timer does not exist or does not belong to the current administrator. |
