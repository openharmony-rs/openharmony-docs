# read

## Modules to Import

```TypeScript
import { serialManager } from '@kit.BasicServicesKit';
```

## read

```TypeScript
function read(portId: number, buffer: Uint8Array, timeout?: number): Promise<number>
```

Reads data from the serial port device asynchronously. The read data is stored in the **buffer** parameter. Before calling this API, call [open](arkts-basicservices-serialmanager-open-f.md) to open the serial port device first. This API uses a promise to return the length of the data that is actually read. This API can be used to receive data reported by sensors, read response data returned by devices, and receive device status information.

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
| buffer | Uint8Array | Yes | Buffer for storing the binary data read from the serial port device. The buffer size should be determined based on the expected amount of data to be read. After the read operation is successful, the return value indicates the length of the data that is actually read. |
| timeout | number | No | Timeout interval, in milliseconds. If there is no data in the buffer of the target port, this API returns the result after waiting for the specified time. The default value is **0**. If the default value is used or the parameter is not specified, it indicates that the API returns the result without waiting. If a negative number is passed, a parameter error is thrown. Set this parameter based on the device response speed and data volume. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the length of the data read, in bytes. |

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
> The following sample code shows the basic process for calling the read API and it needs to be executed in a specific method. In actual calling, you must comply with the device-related protocols.
```
