# writeSync

## Modules to Import

```TypeScript
import { serialManager } from '@kit.BasicServicesKit';
```

## writeSync

```TypeScript
function writeSync(portId: number, buffer: Uint8Array, timeout?: number): number
```

Writes data to the serial port device synchronously. Before calling this API, call [open](arkts-basicservices-serialmanager-open-f.md) to open the serial port device first. The length of data written each time cannot exceed 4 KB. Otherwise, data loss may occur. You are advised to write long data in multiple packets. This API is applicable to scenarios where data needs to be written in blocking mode, important commands need to be sent, or the write sequence must be strictly followed.

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
| buffer | Uint8Array | Yes | Buffer for writing data, including the binary data to be sent to the serial port device. The length of data written each time cannot exceed 4 KB; otherwise, data loss may occur. You are advised to write long data in multiple packets. |
| timeout | number | No | Timeout interval, in milliseconds. When writing data, this API waits until the buffer is writable and returns the result after the specified time. The default value is **0**. If the default value is used or the parameter is not specified, it indicates that the API returns the result without waiting. If a negative number is passed, a parameter error is thrown. Set this parameter based on the device response speed and data volume. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Length of the data written, in bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) |  |
| [31400001](../errorcode-usb.md#31400001-serial-port-service-error) |  |
| [31400003](../errorcode-usb.md#31400003-port-number-not-exist) |  |
| [31400005](../errorcode-usb.md#31400005-device-not-opened) |  |
| [31400006](../errorcode-usb.md#31400006-data-transfer-timeout) |  |
| [31400007](../errorcode-usb.md#31400007-io-exception) |  |

**Examples**

```TypeScript
> NOTE
> 
> The following sample code shows the basic process for calling the writeSync API and it needs to be executed in a specific method. In actual calling, you must comply with the device-related protocols.
```
