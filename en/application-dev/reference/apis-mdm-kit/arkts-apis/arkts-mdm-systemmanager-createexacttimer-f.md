# createExactTimer

## Modules to Import

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## createExactTimer

```TypeScript
function createExactTimer(config: ExactTimerConfig): Promise<number>
```

Creates an exact timer. This API uses a promise to return the timer ID.

> **NOTE:** 
> 
> This API must be used together with [systemManager.destroyExactTimer](arkts-mdm-systemmanager-destroyexacttimer-f.md).
> Otherwise, memory leakage occurs. When the admin application is disabled or removed, the EDM service
> automatically destroys all timers created by the admin.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [ExactTimerConfig](arkts-mdm-systemmanager-exacttimerconfig-c.md) | Yes | Timer initialization configuration, including whether the timer is a repeating timer, interval, callback, and name. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the timer ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-service-timeout) | Service timeout. |
| 9201053 | The number of timers has reached the upper limit. |
