# open

## Modules to Import

```TypeScript
import { serialManager } from '@kit.BasicServicesKit';
```

## open

```TypeScript
function open(portId: number): void
```

Opens a serial port device. Before calling this API, you need to call [requestSerialRight](arkts-basicservices-serialmanager-requestserialright-f.md) to request the permission. After calling this API, you need to call [close](arkts-basicservices-serialmanager-close-f.md) to close the serial port. After the API is successfully called, you can perform operations such as read/write and parameter configuration on the serial port.

**Prerequisites**  
- You have called getPortList to obtain the port number.  
- Call requestSerialRight to request the access permission.

**API called in pairs**  
- This API must be used with close in pairs.  
- After the serial port is opened, you must call **close()** to close the serial port and release resources.

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
| [31400002](../errorcode-usb.md#31400002-no-serial-port-device-access-permission) |  |
| [31400003](../errorcode-usb.md#31400003-port-number-not-exist) |  |
| [31400004](../errorcode-usb.md#31400004-port-in-use) |  |

**Examples**

```TypeScript
> NOTE
> 
> The following sample code shows the basic process for calling the open API and it needs to be executed in a specific method. In actual calling, you must comply with the device-related protocols.
```
