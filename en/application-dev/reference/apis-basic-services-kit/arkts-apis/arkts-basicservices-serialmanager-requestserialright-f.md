# requestSerialRight

## Modules to Import

```TypeScript
import { serialManager } from '@kit.BasicServicesKit';
```

## requestSerialRight

```TypeScript
function requestSerialRight(portId: number): Promise<boolean>
```

Requests the permission for the app to access the serial port device. After the app exits, the access permission on the serial port device is automatically removed. After the app is restarted, the app needs to request the permission again. This API uses a promise to return the result. Generally, this API is called to request authorization from the user when the application attempts to access the serial port for the first time and detects that it does not have the permission. You can call [cancelSerialRight](arkts-basicservices-serialmanager-cancelserialright-f.md) to remove the permission.

**Prerequisites**  
- You have called getPortList to obtain the port number.

**Since:** 19

**System capability:** SystemCapability.USB.USBManager.Serial

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| portId | number | Yes | Port number, which is obtained from the [SerialPort](arkts-basicservices-serialmanager-serialport-i.md) object returned by [getPortList](arkts-basicservices-serialmanager-getportlist-f.md). The value must be a valid port number returned by **getPortList**. If an invalid value is passed, error code 31400003 is thrown. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return a Boolean value. The value **true** indicates that the permission is successfully requested, and **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) |  |
| [14400005](../errorcode-usb.md#14400005-database-operation-exception) |  |
| [31400001](../errorcode-usb.md#31400001-serial-port-service-error) |  |
| [31400003](../errorcode-usb.md#31400003-port-number-not-exist) |  |

**Examples**

```TypeScript
> NOTE
> 
> The following sample code shows the basic process for calling the requestSerialRight API and it needs to be executed in a specific method. In actual calling, you must comply with the device-related protocols.
```
