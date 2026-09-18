# getPortList (System API)

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## getPortList

```TypeScript
function getPortList(): Array<USBPort>
```

Obtains the list of all physical USB ports. This API can be used to enumerate USB ports, perform port management, diagnose the device connection status, or query the port configuration information. When the developer mode is disabled, **undefined** is returned if no device is connected. Check whether the return value of the API is empty.

**Since:** 12

**Required permissions:** ohos.permission.MANAGE_USB_CONFIG

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[USBPort](arkts-basicservices-usbmanager-usbport-i-sys.md)&gt; | List of physical USB ports. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 18 and later |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied. Normal application do not have permission to use system api. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |
| [14400004](../errorcode-usb.md#14400004-service-exception) |  |
