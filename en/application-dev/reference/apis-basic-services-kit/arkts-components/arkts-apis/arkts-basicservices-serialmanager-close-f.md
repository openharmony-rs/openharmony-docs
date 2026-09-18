# close

## Modules to Import

```TypeScript
import { serialManager } from '@kit.BasicServicesKit';
```

## close

```TypeScript
function close(portId: number): void
```

Closes the serial port device. Call [requestSerialRight](arkts-basicservices-serialmanager-requestserialright-f.md) to request the permission and then call [open](arkts-basicservices-serialmanager-open-f.md) to open the serial port. Generally, this API is called when the application exits, the device is disconnected, or serial port resources need to be released. Closing the serial port does not remove the access permission. To remove the permission, call **cancelSerialRight**.

**API called in pairs**  
- This API must be used with open in pairs.  
- After the serial port is opened, you must call this method to close the serial port and release resources.

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
> The following sample code shows the basic process for calling the close API and it needs to be executed in a specific method. In actual calling, you must comply with the device-related protocols.
```
