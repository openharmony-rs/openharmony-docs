# getDeviceFunctions (System API)

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## getDeviceFunctions

```TypeScript
function getDeviceFunctions(): FunctionType
```

Obtains the numeric mask combination for the USB function list in Device mode. This API can be used to check the USB function state, confirm the function configuration, or compare the status before and after function switching. When the developer mode is disabled, **undefined** is returned if no device is connected. Check whether the return value of the API is empty.

**Since:** 12

**Required permissions:** ohos.permission.MANAGE_USB_CONFIG

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [FunctionType](arkts-basicservices-usbmanager-functiontype-e-sys.md) | Numeric mask combination for the USB function list. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 18 and later |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied. Normal application do not have permission to use system api. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |
