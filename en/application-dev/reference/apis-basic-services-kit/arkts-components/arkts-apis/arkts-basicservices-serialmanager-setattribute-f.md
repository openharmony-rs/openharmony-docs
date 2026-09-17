# setAttribute

## Modules to Import

```TypeScript
import { serialManager } from '@kit.BasicServicesKit';
```

## setAttribute

```TypeScript
function setAttribute(portId: number, attribute: SerialAttribute): void
```

Sets the parameters of the specified serial port. You need to call [open](arkts-basicservices-serialmanager-open-f.md) to open the serial port to set parameters. The configuration parameters include **baudRate** (mandatory), **dataBits** (optional) whose default value is **8**, **parity** (optional) whose default value is **PARITY_NONE**, and **stopBits** (optional) whose default value is 1. Generally, this API is called when the device is initialized, the communication protocol is switched, or the device requires non-default configuration parameters.

**Prerequisites**  
- You have called getPortList to obtain the port number.  
- You have called requestSerialRight to request the access permission.  
- You have called open to open the serial port.

**Since:** 19

**System capability:** SystemCapability.USB.USBManager.Serial

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| portId | number | Yes | Port number, which is obtained from the [SerialPort](arkts-basicservices-serialmanager-serialport-i.md) object returned by [getPortList](arkts-basicservices-serialmanager-getportlist-f.md). The value must be a valid port number returned by **getPortList**. If an invalid value is passed, error code 31400003 is thrown. |
| attribute | [SerialAttribute](arkts-basicservices-serialmanager-serialattribute-i.md) | Yes | Serial port configuration parameters. The parameters include **baudRate** (mandatory), **dataBits** (optional) whose default value is **8**, **parity** (optional) whose default value is **PARITY_NONE**, and **stopBits** (optional) whose default value is **1**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) |  |
| [31400001](../errorcode-usb.md#31400001-serial-port-service-error) |  |
| [31400003](../errorcode-usb.md#31400003-port-number-not-exist) |  |
| [31400005](../errorcode-usb.md#31400005-device-not-opened) |  |

**Examples**

```TypeScript
> NOTE
> 
> The following sample code shows the basic process for calling the setAttribute API and it needs to be executed in a specific method. In actual calling, you must comply with the device-related protocols.
```
