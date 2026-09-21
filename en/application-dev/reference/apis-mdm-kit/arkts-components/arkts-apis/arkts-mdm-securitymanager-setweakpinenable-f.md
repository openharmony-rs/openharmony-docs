# setWeakPinEnable

## Modules to Import

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## setWeakPinEnable

```TypeScript
function setWeakPinEnable(isEnable: boolean, fd?: number): void
```

Sets the weak PIN enable status.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isEnable | boolean | Yes | isEnable indicates whether to enable weak PIN verification. **true** means enable, **false** means disable. |
| fd | number | No | fd indicate the file descriptor of the weak PIN file. Required when enable the weak PIN verification, ignored when disable the weak PIN verification. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-service-timeout) | Service timeout. |
