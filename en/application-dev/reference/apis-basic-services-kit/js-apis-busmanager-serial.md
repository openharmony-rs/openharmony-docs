# @ohos.busManager.serial (Serial Port Management)

<!--Kit: Basic Services Kit-->
<!--Subsystem: BusManager-->
<!--Owner: @hwymlgitcode-->
<!--Designer: @hwymlgitcode-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->

This module provides APIs for serial port management, including obtaining the serial port list, enabling and disabling a serial port, reading and writing data, and hardware-based flow control for signal management.

**Since:** 26.0.0

## Modules to Import

```ts
import { serial } from "@kit.BasicServicesKit";
```

## serial.getSerialPortList

getSerialPortList(): Promise&lt;[SerialPort](#serialport)[]&gt;

Obtains the serial port list. This API uses a promise to return the result, which is a list of [SerialPort](#serialport) objects.  

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

**Return value**

| Type                                     | Description               |
|-----------------------------------------|-------------------|
| Promise&lt;[SerialPort](#serialport)[]&gt; | Promise that returns a list of serial ports.|

**Error codes**

For details about the error codes, see [Common Error Codes](../errorcode-universal.md) and [Serial Port Management Error Codes](errorcode-busmanager-serial.md).

| Error Code| Error Message                                        |
| -------- | ------------------------------------------------ |
| 203      | This function is prohibited by enterprise management policies. |
| 35700001 | Service error.                                   |

**Example**

```ts
import { serial } from "@kit.BasicServicesKit";

// Obtain the serial port list.
serial.getSerialPortList().then((portList: serial.SerialPort[]) => {
  console.info(`getSerialPortList success, length: ${portList.length}`);
  if (portList.length > 0) {
    let portInfo: serial.SerialPortInfo = portList[0].portInfo;
    console.info(`portName: ${portInfo.portName}`);
  }
}).catch((error: Error) => {
  console.error(`getSerialPortList error: ${JSON.stringify(error)}`);
});
```

## SerialPort

Defines a serial port object, which provides information about the serial port device and the communication capability.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

### Properties

| Name      | Type                                      | Read-Only| Optional| Description        |
| ---------- | ------------------------------------------ | ---- | ---- | ------------ |
| portInfo   | [SerialPortInfo](#serialportinfo)          | Yes  | No  | Serial port information.|

### open

open(config?: [SerialConfigs](#serialconfigs)): Promise&lt;void&gt;

Opens a serial port device. When a serial port is opened for the first time, the system displays a dialog box asking the user to authorize access to the target serial port. If the user rejects the request, error code 35700007 is thrown. The authorization expires upon removal of the USB virtual serial port, system user switching, or restart of the device. Re-authorization is required in this case. This API uses a promise to return the result.

**Since:** 26.0.0

**System capability:** SystemCapability.BusManager.Serial

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name| Type                                     | Mandatory| Description                                      |
| ------ | ----------------------------------------- | ---- | ------------------------------------------ |
| config | [SerialConfigs](#serialconfigs)           | No  | Communication parameters of the serial port. For details about the default values, see [SerialConfigs](#serialconfigs).|

**Return value**

| Type               | Description                   |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Serial Port Management Error Codes](errorcode-busmanager-serial.md).

| Error Code| Error Message                         |
| -------- | --------------------------------- |
| 35700001 | Service error.                    |
| 35700002 | Invalid parameter.                |
| 35700003 | Virtual serial port disconnected. |
| 35700004 | Port already in use.              |
| 35700007 | User authorization required.      |

**Example**

```ts
import { serial } from "@kit.BasicServicesKit";

// Obtain the serial port list and open the first serial port.
serial.getSerialPortList().then(async (portList: serial.SerialPort[]) => {
  if (portList.length === 0) {
    console.error('portList is empty');
    return;
  }
  let port: serial.SerialPort = portList[0];
  let config: serial.SerialConfigs = {
    baudRate: 115200,
    dataBits: serial.DataBits.EIGHT,
    stopBits: serial.StopBits.ONE,
    parity: serial.Parity.NONE
  };
  await port.open(config);
  console.info('open success');
}).catch((error: Error) => {
  console.error(`error: ${JSON.stringify(error)}`);
});
```

### close

close(): Promise&lt;void&gt;

Closes a serial port device. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

**Return value**

| Type               | Description                   |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Serial Port Management Error Codes](errorcode-busmanager-serial.md).

| Error Code| Error Message            |
| -------- | -------------------- |
| 35700001 | Service error.       |
| 35700005 | Port not open.       |

**Example**

```ts
import { serial } from "@kit.BasicServicesKit";

// Close the serial port device.
port.close().then(() => {
  console.info('close success');
}).catch((error: Error) => {
  console.error(`close error: ${JSON.stringify(error)}`);
});
```

### write

write(data: Uint8Array, timeout?: number): Promise&lt;number&gt;

Writes data to a serial port device. The value range of the data length is (0, 4096]. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

**Parameters**

| Name  | Type        | Mandatory| Description                                                                                                    |
| -------- | ------------ | ---- | -------------------------------------------------------------------------------------------------------- |
| data     | Uint8Array   | Yes  | Data to be written. Length range: (0, 4096].                                                                       |
| timeout  | number       | No  | Timeout interval, in milliseconds. The value must be an integer within the range of [0, 300000]. The default value **0** is returned when data cannot be written into the target port.|

**Return value**

| Type                   | Description                       |
| ----------------------- | --------------------------- |
| Promise&lt;number&gt;   | Promise used to return the length of the data written.|

**Error codes**

For details about the error codes, see [Serial Port Management Error Codes](errorcode-busmanager-serial.md).

| Error Code| Error Message                         |
| -------- | --------------------------------- |
| 35700001 | Service error.                    |
| 35700002 | Invalid parameter.                |
| 35700003 | Virtual serial port disconnected. |
| 35700005 | Port not open.                    |
| 35700006 | Transmission timeout.             |

**Example**

```ts
import { buffer } from '@kit.ArkTS';
import { serial } from "@kit.BasicServicesKit";

// Write data to a serial port device.
let writeData: Uint8Array = new Uint8Array(buffer.from('Hello World', 'utf-8').buffer);
port.write(writeData, 2000).then((size: number) => {
  console.info('write success, size: ' + size);
}).catch((error: Error) => {
  console.error(`write error: ${JSON.stringify(error)}`);
});
```

### onDataRead

onDataRead(callback: Callback&lt;Uint8Array&gt;): void

Listens for data receiving events on the serial port. This API uses an asynchronous callback to return the received data. After [close](#close) is called, the callback registration will be cleared.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

**Parameters**

| Name  | Type                      | Mandatory| Description                            |
| -------- | -------------------------- | ---- | -------------------------------- |
| callback | Callback&lt;Uint8Array&gt; | Yes  | Callback used to return the data received by the serial port.|

**Error codes**

For details about the error codes, see [Serial Port Management Error Codes](errorcode-busmanager-serial.md).

| Error Code| Error Message                         |
| -------- | --------------------------------- |
| 35700001 | Service error.                    |
| 35700003 | Virtual serial port disconnected. |
| 35700005 | Port not open.                    |

**Example**

```ts
import { serial } from "@kit.BasicServicesKit";

// Listen for data receiving events on the serial port.
port.onDataRead((data: Uint8Array) => {
  console.info(`onDataRead, length: ${data.length}`);
});
```

### offDataRead

offDataRead(callback?: Callback&lt;Uint8Array&gt;): void

Cancels listening for data receiving events on the serial port. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

**Parameters**

| Name  | Type                      | Mandatory| Description                                                  |
| -------- | -------------------------- | ---- | ------------------------------------------------------ |
| callback | Callback&lt;Uint8Array&gt; | No  | Callback used to return the result. If no callback is passed, the listener for data receiving events on the serial port is canceled.|

**Error codes**

For details about the error codes, see [Serial Port Management Error Codes](errorcode-busmanager-serial.md).

| Error Code| Error Message            |
| -------- | -------------------- |
| 35700001 | Service error.       |
| 35700005 | Port not open.       |

**Example**

```ts
import { serial } from "@kit.BasicServicesKit";

// Cancel listening for data receiving events on the serial port.
port.offDataRead();

// Cancel the specified listener callback.
let callback = (data: Uint8Array) => {
  console.info(`received data length: ${data.length}`);
};
port.offDataRead(callback);
```

### flush

flush(): Promise&lt;void&gt;

Flushes the serial port buffer, including the read buffer and write buffer. Data in the buffer will be directly discarded and will not be sent or read. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

**Return value**

| Type               | Description                   |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Serial Port Management Error Codes](errorcode-busmanager-serial.md).

| Error Code| Error Message                         |
| -------- | --------------------------------- |
| 35700001 | Service error.                    |
| 35700003 | Virtual serial port disconnected. |
| 35700005 | Port not open.                    |

**Example**

```ts
import { serial } from "@kit.BasicServicesKit";

// Flush the serial port buffer.
port.flush().then(() => {
  console.info('flush success');
}).catch((error: Error) => {
  console.error(`flush error: ${JSON.stringify(error)}`);
});
```

### drain

drain(): Promise&lt;void&gt;

Waits until all write requests are complete. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

**Return value**

| Type               | Description                   |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Serial Port Management Error Codes](errorcode-busmanager-serial.md).

| Error Code| Error Message                         |
| -------- | --------------------------------- |
| 35700001 | Service error.                    |
| 35700003 | Virtual serial port disconnected. |
| 35700005 | Port not open.                    |

**Example**

```ts
import { serial } from "@kit.BasicServicesKit";

// Wait until all write requests are complete.
port.drain().then(() => {
  console.info('drain success');
}).catch((error: Error) => {
  console.error(`drain error: ${JSON.stringify(error)}`);
});
```

### setRts

setRts(enable: boolean): Promise&lt;void&gt;

Sets the status of the Request to Send (RTS) signal. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

**Parameters**

| Name| Type    | Mandatory| Description                                      |
| ------ | -------- | ---- | ------------------------------------------ |
| enable | boolean  | Yes  | RTS signal status. The value **true** indicates requesting to send data, and the value **false** indicates otherwise.|

**Return value**

| Type               | Description                   |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Serial Port Management Error Codes](errorcode-busmanager-serial.md).

| Error Code| Error Message                         |
| -------- | --------------------------------- |
| 35700001 | Service error.                    |
| 35700003 | Virtual serial port disconnected. |
| 35700005 | Port not open.                    |

**Example**

```ts
import { serial } from "@kit.BasicServicesKit";

// Set the RTS signal.
port.setRts(true).then(() => {
  console.info('setRts success');
}).catch((error: Error) => {
  console.error(`setRts error: ${JSON.stringify(error)}`);
});
```

### getCts

getCts(): Promise&lt;boolean&gt;

Obtains the status of the Clear to Send (CTS) signal. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

**Return value**

| Type                    | Description                                            |
| ------------------------ | ------------------------------------------------ |
| Promise&lt;boolean&gt;   | Promise used to return the CTS signal status. The value **true** indicates that data can be sent, and the value **false** indicates otherwise.|

**Error codes**

For details about the error codes, see [Serial Port Management Error Codes](errorcode-busmanager-serial.md).

| Error Code| Error Message                         |
| -------- | --------------------------------- |
| 35700001 | Service error.                    |
| 35700003 | Virtual serial port disconnected. |
| 35700005 | Port not open.                    |

**Example**

```ts
import { serial } from "@kit.BasicServicesKit";

// Obtain the CTS signal status.
port.getCts().then((cts: boolean) => {
  console.info('getCts success, cts: ' + cts);
}).catch((error: Error) => {
  console.error(`getCts error: ${JSON.stringify(error)}`);
});
```

### sendBrk

sendBrk(): Promise&lt;void&gt;

Sends a BRK signal. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

**Return value**

| Type               | Description                   |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Serial Port Management Error Codes](errorcode-busmanager-serial.md).

| Error Code| Error Message                         |
| -------- | --------------------------------- |
| 35700001 | Service error.                    |
| 35700003 | Virtual serial port disconnected. |
| 35700005 | Port not open.                    |

**Example**

```ts
import { serial } from "@kit.BasicServicesKit";

// Send a BRK signal.
port.sendBrk().then(() => {
  console.info('sendBrk success');
}).catch((error: Error) => {
  console.error(`sendBrk error: ${JSON.stringify(error)}`);
});
```

### setDtr

setDtr(enable: boolean): Promise&lt;void&gt;

Sets the status of the data terminal ready (DTR) signal. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

**Parameters**

| Name| Type    | Mandatory| Description                                      |
| ------ | -------- | ---- | ------------------------------------------ |
| enable | boolean  | Yes  | DTR signal status. The value **true** indicates that the data terminal is ready, and the value **false** indicates that the data terminal is not ready.|

**Return value**

| Type               | Description                   |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Serial Port Management Error Codes](errorcode-busmanager-serial.md).

| Error Code| Error Message                         |
| -------- | --------------------------------- |
| 35700001 | Service error.                    |
| 35700003 | Virtual serial port disconnected. |
| 35700005 | Port not open.                    |

**Example**

```ts
import { serial } from "@kit.BasicServicesKit";

// Set the DTR signal.
port.setDtr(true).then(() => {
  console.info('setDtr success');
}).catch((error: Error) => {
  console.error(`setDtr error: ${JSON.stringify(error)}`);
});
```

### getDsr

getDsr(): Promise&lt;boolean&gt;

Obtains the status of the data set ready (DSR) signal. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

**Return value**

| Type                    | Description                                            |
| ------------------------ | ------------------------------------------------ |
| Promise&lt;boolean&gt;   | Promise used to return the DSR signal status. The value **true** indicates that the data device is ready, and the value **false** indicates that the data device is not ready.|

**Error codes**

For details about the error codes, see [Serial Port Management Error Codes](errorcode-busmanager-serial.md).

| Error Code| Error Message                         |
| -------- | --------------------------------- |
| 35700001 | Service error.                    |
| 35700003 | Virtual serial port disconnected. |
| 35700005 | Port not open.                    |

**Example**

```ts
import { serial } from "@kit.BasicServicesKit";

// Obtain the DSR signal status.
port.getDsr().then((dsr: boolean) => {
  console.info('getDsr success, dsr: ' + dsr);
}).catch((error: Error) => {
  console.error(`getDsr error: ${JSON.stringify(error)}`);
});
```

### onDisconnect

onDisconnect(callback: Callback&lt;void&gt;): void

Subscribes to serial port disconnection events. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

**Parameters**

| Name  | Type                 | Mandatory| Description                            |
| -------- | --------------------- | ---- | -------------------------------- |
| callback | Callback&lt;void&gt;  | Yes  | Callback used to return the result, which is triggered when the serial port is disconnected.|

**Error codes**

For details about the error codes, see [Serial Port Management Error Codes](errorcode-busmanager-serial.md).

| Error Code| Error Message            |
| -------- | -------------------- |
| 35700001 | Service error.       |
| 35700005 | Port not open.       |

**Example**

```ts
import { serial } from "@kit.BasicServicesKit";

// Subscribe to serial port disconnection events.
port.onDisconnect(() => {
  console.info('serial port disconnected');
});
```

### offDisconnect

offDisconnect(callback?: Callback&lt;void&gt;): void

Unsubscribes from serial port disconnection events.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

**Parameters**

| Name  | Type                 | Mandatory| Description                                                  |
| -------- | --------------------- | ---- | ------------------------------------------------------ |
| callback | Callback&lt;void&gt;  | No  | Callback used to return the result. If no callback is passed, the listener for all serial port disconnection events is canceled.|

**Error codes**

For details about the error codes, see [Serial Port Management Error Codes](errorcode-busmanager-serial.md).

| Error Code| Error Message            |
| -------- | -------------------- |
| 35700001 | Service error.       |
| 35700005 | Port not open.       |

**Example**

```ts
import { serial } from "@kit.BasicServicesKit";

// Unsubscribe from serial port disconnection events.
port.offDisconnect();

// Cancel the specified listener callback.
let disconnectedCallback = () => {
  console.info('serial port disconnected');
};
port.offDisconnect(disconnectedCallback);
```

## SerialPortInfo

Describes the serial port information.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

| Name         | Type    | Read-Only| Optional| Description                       |
| ------------- | -------- | ---- | ---- | --------------------------- |
| portName      | string   | No  | No  | Port name.                 |
| vendorId      | number   | No  | Yes  | Vendor ID of the USB virtual serial port.      |
| productId     | number   | No  | Yes  | Product ID of the USB virtual serial port.  |
| manufacturer  | string   | No  | Yes  | Manufacturer name of the USB virtual serial port.|

## DataBits

Enumerates the number of data bits.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

| Name  | Value| Description             |
| ------ | -- | ----------------- |
| FIVE   | 5  | Five data bits.      |
| SIX    | 6  | Six data bits.      |
| SEVEN  | 7  | Seven data bits.      |
| EIGHT  | 8  | Eight data bits.      |

## StopBits

Enumerates the number of stop bits.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

| Name| Value| Description             |
| ---- | -- | ----------------- |
| ONE  | 1  | One stop bit.      |
| TWO  | 2  | Two stop bits.      |

## Parity

Enumerates the number of parity bits.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

| Name | Value      | Description                   |
| ----- | -------- | ----------------------- |
| NONE  | 'none'   | No parity.               |
| EVEN  | 'even'   | Even parity.               |
| ODD   | 'odd'    | Odd parity.               |
| MARK  | 'mark'   | Mark parity. The parity bit is always **1**.|
| SPACE | 'space'  | Space parity. The parity bit is always **0**.|

## SerialConfigs

Defines the communication parameters of the serial port.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

| Name    | Type                    | Read-Only| Optional| Description                                                                 |
| -------- | ------------------------ | ---- | ---- | --------------------------------------------------------------------- |
| baudRate | number                   | No  | Yes  | Baud rate. The value must be a positive integer. Whether non-standard baud rates are supported depends on the hardware. Unit: bit/s. The default value is **115200**.      |
| dataBits | [DataBits](#databits)    | No  | Yes  | Data bits. The default value is **EIGHT**.                                               |
| stopBits | [StopBits](#stopbits)    | No  | Yes  | Stop bits. The default value is **ONE**.                                                 |
| parity   | [Parity](#parity)        | No  | Yes  | Parity bit. The default value is **NONE**.                                                |
| rtscts   | boolean                  | No  | Yes  | Whether to enable hardware-based automatic flow control via RTS/CTS. The default value is **false**. **true** to enable; **false** otherwise.                                  |
| xon      | boolean                  | No  | Yes  | Whether to enable XON to control the sending of flows. The default value is **false**. **true** to enable; **false** otherwise.                                 |
| xoff     | boolean                  | No  | Yes  | Whether to enable XOFF to control the reception of flows. The default value is **false**. **true** to enable; **false** otherwise.                                |
| xany     | boolean                  | No  | Yes  | Whether to enable XANY to control the flow. The default value is **false**. **true** to enable; **false** otherwise.                                    |
