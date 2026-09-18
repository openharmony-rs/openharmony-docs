# getSupportedModes (System API)

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## getSupportedModes

```TypeScript
function getSupportedModes(portId: number): PortModeType
```

Obtains the mask combination for the supported mode list of a given USB port. This method is applicable when the system app needs to query the USB-C port capabilities to determine whether a specific mode (such as UFP, DFP, or DRP) is supported. The return value is the mask combination of **PortModeType**. You can determine whether the port supports a specific mode using bitwise operations. The **PortModeType** values are as follows: **NONE (0)**: no mode; **UFP (1)**: upstream port mode, **dataRole** is **DEVICE**; **DFP (2)**: downstream port mode, **dataRole** is **HOST**; **DRP (3)**: dual-role mode, which can switch between **UFP** and **DFP**; **NUM_MODES (4)**: not supported currently. You can determine whether the port supports the combination of power roles and data transfer roles based on the return value.

**Since:** 9

**Deprecated since:** 12

**Substitutes:** [getPortSupportModes](arkts-basicservices-usbmanager-getportsupportmodes-f-sys.md)(portId: number)

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| portId | number | Yes | USB port number. The value is a non-negative integer, which can be obtained from the port list returned by [getPortList](arkts-basicservices-usbmanager-getportlist-f-sys.md). |

**Return value:**

| Type | Description |
| --- | --- |
| [PortModeType](arkts-basicservices-usbmanager-portmodetype-e-sys.md) | Mask combination for the supported mode list. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
