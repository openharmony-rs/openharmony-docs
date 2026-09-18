# getSerialPortList

## Modules to Import

```TypeScript
import { serial } from '@kit.BasicServicesKit';
```

## getSerialPortList

```TypeScript
function getSerialPortList(): Promise<SerialPort[]>
```

Obtains the serial port list. This API uses a promise to return the result, which is a list of [SerialPort](arkts-basicservices-serial-serialport-i.md) objects. This API is used to identify available serial port devices in scenarios such as industrial device connection, IoT device management, and embedded system debugging.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[SerialPort](arkts-basicservices-serial-serialport-i.md)[]&gt; | Promise that returns a list of serial ports. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [203](../../errorcode-universal.md#203-system-function-prohibited-by-enterprise-management-policies) | This function is prohibited by enterprise management policies. |
| [35700001](../errorcode-busmanager-serial.md#35700001-abnormal-service) | Service error. |

**Examples**

```TypeScript
// Import BusinessError from @kit.BasicServicesKit.
// Obtain the serial port list.
serial.getSerialPortList().then((portList: serial.SerialPort[]) => {
  console.info(`getSerialPortList success, length: ${portList.length}`);
  if (portList.length > 0) {
    let portInfo: serial.SerialPortInfo = portList[0].portInfo;
    console.info(`portName: ${portInfo.portName}`);
  }
}).catch((error: BusinessError) => {
  console.error(`Failed to get serial port list. Code: ${error.code}, message: ${error.message}`);
});
```
