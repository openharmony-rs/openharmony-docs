# isUsbInterceptEnable

## Modules to Import

```TypeScript
import { usbManager } from '@kit.MDMKit';
```

## isUsbInterceptEnable

```TypeScript
function isUsbInterceptEnable(): boolean
```

Checks whether the USB interception is enabled.

**Since:** 26.1.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_USB

**Model restriction:** This API can be used only in the stage model.

<!--Device-usbManager-function isUsbInterceptEnable(): boolean--><!--Device-usbManager-function isUsbInterceptEnable(): boolean-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns true if the USB interception is enabled; returns false otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-service-timeout) | Service timeout. |
