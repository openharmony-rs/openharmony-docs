# readSync

## Modules to Import

```TypeScript
import { serialManager } from '@kit.BasicServicesKit';
```

## readSync

```TypeScript
function readSync(portId: number, buffer: Uint8Array, timeout?: number): number
```

Reads data from the serial port device synchronously. The read data is stored in the **buffer** parameter. The actual length of the data read is returned. Before calling this API, call [open](arkts-basicservices-serialmanager-open-f.md) to open the serial port device first. This method is applicable to simple communication scenarios where data needs to be read in blocking mode, the read sequence must be strictly followed, or there is no high requirement on real-time performance.

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
| number | Length of the data read, in bytes. |

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

> NOTE
> 
> The following sample code shows the basic process for calling the readSync API and it needs to be executed in a specific method. In actual calling, you must comply with the device-related protocols.

```TypeScript
import { JSON } from '@kit.ArkTS';
import { serialManager } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the serial port list.
async function readSyncExample() {
  let portList: serialManager.SerialPort[] = serialManager.getPortList();
  console.info('usbSerial portList: ' + JSON.stringify(portList));
  if (!portList || portList.length === 0) {
    console.error('usbSerial portList is empty');
    return;
  }
  let portId: number = portList[0].portId;

  // Check whether the device can be accessed by the application.
  if (!serialManager.hasSerialRight(portId)) {
    let result = await serialManager.requestSerialRight(portId);
    if (!result) {
      // If the app does not have the access permission and the user does not grant the permission, the app exits.
      console.error('user is not granted the operation permission');
      return;
    } else {
      console.info('grant permission successfully');
    }
  }

  // Open a serial port device.
  try {
    serialManager.open(portId);
    console.info('open usbSerial success, portId: ' + portId);
  } catch (error) {
    const err: BusinessError = error as BusinessError;
    console.error(`Failed to open usbSerial. Code: ${err.code}, message: ${err.message}`);
  }

  // Read data synchronously.
  let readSyncBuffer: Uint8Array = new Uint8Array(64);
  try {
    serialManager.readSync(portId, readSyncBuffer, 2000);
    console.info('readSync usbSerial success, readSyncBuffer: ' + readSyncBuffer.toString());
  } catch (error) {
    const err: BusinessError = error as BusinessError;
    console.error(`Failed to readSync usbSerial. Code: ${err.code}, message: ${err.message}`);
  }

  // Close the serial port device.
  try {
    serialManager.close(portId);
    console.info('close usbSerial success, portId: ' + portId);
  } catch (error) {
    const err: BusinessError = error as BusinessError;
    console.error(`Failed to close usbSerial. Code: ${err.code}, message: ${err.message}`);
  }
}
```
