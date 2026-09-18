# setPortRoleTypes (System API)

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## setPortRoleTypes

```TypeScript
function setPortRoleTypes(portId: number, powerRole: PowerRoleType, dataRole: DataRoleType): Promise<void>
```

Sets the role types of a specified port, including **powerRole** (for charging) and **dataRole** (for data transfer). This API uses a promise to return the result. After the API is successfully called, the power role and data transfer role of the port are switched to the specified roles. This API can be used to dynamically switch the role of a USB port. When developer mode is disabled, the operation may fail if no device is connected. In this case, an exception is thrown. For details about role constraints, see [USBPortStatus](arkts-basicservices-usbmanager-usbportstatus-i-sys.md).

**Since:** 12

**Required permissions:** ohos.permission.MANAGE_USB_CONFIG

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| portId | number | Yes | Port number. The value can be obtained from the port list returned by [getPortList](arkts-basicservices-usbmanager-getportlist-f-sys.md). |
| powerRole | [PowerRoleType](arkts-basicservices-usbmanager-powerroletype-e-sys.md) | Yes | Power role type. The options are **NONE**, **SOURCE** (providing power), and **SINK** (requiring external power supply). |
| dataRole | [DataRoleType](arkts-basicservices-usbmanager-dataroletype-e-sys.md) | Yes | Data transfer role. The options are **NONE**, **HOST**, and **DEVICE**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. If the API is called successfully, no value is returned. If the call fails, an exception is thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 18 and later |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied. Normal application do not have permission to use system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |
| [14400003](../errorcode-usb.md#14400003-port-role-switching-unsupported) | Unsupported operation. The current device does not support port role switching. |
