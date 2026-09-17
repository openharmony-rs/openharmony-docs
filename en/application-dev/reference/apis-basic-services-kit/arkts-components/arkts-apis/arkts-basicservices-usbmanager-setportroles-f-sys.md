# setPortRoles (System API)

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## setPortRoles

```TypeScript
function setPortRoles(portId: number, powerRole: PowerRoleType, dataRole: DataRoleType): Promise<void>
```

Sets the roles of a specified port, including **powerRole** (for charging) and **dataRole** (for data transfer). This API uses a promise to return the result. After this API is successfully called, the port role will be switched to the specified role. This API can be used to dynamically switch the role of a USB port. When developer mode is disabled, the operation may fail if no device is connected. In this case, an exception is thrown.

**Since:** 9

**Deprecated since:** 12

**Substitutes:** [setPortRoleTypes](arkts-basicservices-usbmanager-setportroletypes-f-sys.md)(portId: number, powerRole: PowerRoleType, dataRole: DataRoleType)

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| portId | number | Yes | USB port number. The value is a non-negative integer, which can be obtained from the port list returned by [getPortList](arkts-basicservices-usbmanager-getportlist-f-sys.md). |
| powerRole | [PowerRoleType](arkts-basicservices-usbmanager-powerroletype-e-sys.md) | Yes | Power role type. The options are **NONE**, **SOURCE** (providing power), and **SINK** (requiring external power supply). |
| dataRole | [DataRoleType](arkts-basicservices-usbmanager-dataroletype-e-sys.md) | Yes | Data transfer role. The options are **NONE**, **HOST**, and **DEVICE**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. If the API is called successfully, no value is returned. If the call fails, an exception is thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
