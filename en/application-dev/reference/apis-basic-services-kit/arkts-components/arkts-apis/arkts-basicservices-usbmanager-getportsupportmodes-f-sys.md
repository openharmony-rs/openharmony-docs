# getPortSupportModes (System API)

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## getPortSupportModes

```TypeScript
function getPortSupportModes(portId: number): PortModeType
```

Obtains the mask combination for the supported mode list of a given USB port. This method is applicable when the system app needs to query the USB-C port capabilities to determine whether a specific mode (such as UFP, DFP, or DRP) is supported. When the developer mode is disabled, **undefined** is returned if no device is connected. Check whether the return value of the API is empty. For details about the enumerated values, see [PortModeType](arkts-basicservices-usbmanager-portmodetype-e-sys.md).

**Since:** 12

**Required permissions:** ohos.permission.MANAGE_USB_CONFIG

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| portId | number | Yes | USB port number. The value can be obtained from the port list returned by [getPortList](arkts-basicservices-usbmanager-getportlist-f-sys.md). |

**Return value:**

| Type | Description |
| --- | --- |
| [PortModeType](arkts-basicservices-usbmanager-portmodetype-e-sys.md) | Mask combination for the supported mode list. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 18 and later |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied. Normal application do not have permission to use system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |
