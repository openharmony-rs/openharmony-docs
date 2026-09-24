# SerialPort

```TypeScript
interface SerialPort
```

Defines a serial port object, which provides information about the serial port device and the communication capability.

**Since:** 26.0.0

**System capability:** SystemCapability.BusManager.Serial

## Modules to Import

```TypeScript
import { serial } from '@kit.BasicServicesKit';
```

## close

```TypeScript
close(): Promise<void>
```

Closes a serial port device. This API uses a promise to return the result. This method is used to disconnect from a serial port device, for example, when an application exits, a device is switched, or serial port resources are released after a task is complete. This method must be called after the serial port is opened.

**API called in pairs**  
- You must call **open()** to open the serial port before calling **close()** to close the serial port.  
- After **close()** is called, the serial port resources are released. To use the serial port again,  
you need to call **open()** again.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [35700001](../errorcode-busmanager-serial.md#35700001-abnormal-service) | Service error. |
| [35700005](../errorcode-busmanager-serial.md#35700005-port-not-opened) | Port not open. |

**Examples**

```TypeScript
// Import BusinessError from @kit.BasicServicesKit.
// port is a serial port object, which needs to be obtained through serial.getSerialPortList().
// Close the serial port device.
port.close().then(() => {
  console.info('close success');
}).catch((error: BusinessError) => {
  console.error(`Failed to close serial port. Code: ${error.code}, message: ${error.message}`);
});
```

## drain

```TypeScript
drain(): Promise<void>
```

Waits until all write requests are complete. This API uses a promise to return the result. This method must be called after the serial port is opened. This method is used to ensure that the follow-up procedure is performed only after all data is written. For example, the serial port is closed after data transmission is complete, or the hardware response is received after data is sent.

**Calling sequence**  
- You must call **open()** to open the serial port before calling **drain()**.  
- Call **drain()** after **write()** to ensure that all written data is sent.  
- You are advised to call **drain()** before **close()** to ensure that all data is transferred before the  
serial port is closed.  
- If **drain()** is called before **open()**, error code 35700005 (Port not open) will be thrown.

The differences between **drain()** and **flush()** are as follows:  
- **drain()** waits until the data in the write buffer is sent completely, which is suitable for scenarios  
where complete data transmission is required. **flush()** directly discards all data in the buffer, which is suitable for scenarios where the buffer needs to be quickly cleared or invalid data needs to be discarded.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [35700001](../errorcode-busmanager-serial.md#35700001-abnormal-service) | Service error. |
| [35700003](../errorcode-busmanager-serial.md#35700003-virtual-serial-port-disconnected) | Virtual serial port disconnected. |
| [35700005](../errorcode-busmanager-serial.md#35700005-port-not-opened) | Port not open. |

**Examples**

```TypeScript
// Import BusinessError from @kit.BasicServicesKit.
// port is a serial port object, which needs to be obtained through serial.getSerialPortList().
// Wait until all write requests are complete.
port.drain().then(() => {
  console.info('drain success');
}).catch((error: BusinessError) => {
  console.error(`Failed to drain serial port. Code: ${error.code}, message: ${error.message}`);
});
```

## flush

```TypeScript
flush(): Promise<void>
```

Flushes the serial port buffer, including the read buffer and write buffer. Data in the buffer will be directly discarded and will not be sent or read. This API uses a promise to return the result. This method must be called after the serial port is opened. This method is used to discard invalid or outdated data in the buffer, for example, when the buffer needs to be cleared and data needs to be retransmitted due to a transmission error, or when old data needs to be cleared during a communication protocol switch.

**Calling sequence**  
- You must call **open()** to open the serial port before calling **flush()** to clear the buffer.  
- If **flush()** is called before **open()**, error code 35700005 (Port not open) will be thrown.

Difference between **flush()** and **drain()**: **flush()** directly discards all data in the buffer and is suitable for scenarios where the buffer needs to be quickly cleared or invalid data needs to be discarded. **drain()** waits until the data in the write buffer is completely sent and is suitable for scenarios where complete data transmission is required.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [35700001](../errorcode-busmanager-serial.md#35700001-abnormal-service) | Service error. |
| [35700003](../errorcode-busmanager-serial.md#35700003-virtual-serial-port-disconnected) | Virtual serial port disconnected. |
| [35700005](../errorcode-busmanager-serial.md#35700005-port-not-opened) | Port not open. |

**Examples**

```TypeScript
// Import BusinessError from @kit.BasicServicesKit.
// port is a serial port object, which needs to be obtained through serial.getSerialPortList().
// Flush the serial port buffer.
port.flush().then(() => {
  console.info('flush success');
}).catch((error: BusinessError) => {
  console.error(`Failed to flush serial port. Code: ${error.code}, message: ${error.message}`);
});
```

## getCts

```TypeScript
getCts(): Promise<boolean>
```

Obtains the status of the Clear to Send (CTS) signal. This API uses a promise to return the result. This method must be called after the serial port is opened. This method is used to query the CTS signal status for hardware-based flow control to determine whether data can be sent. For example, you can use this method to check the transmission permission when hardware-based flow control via RTS/CTS is enabled or check the status before communicating with a device that supports hardware-based flow control.

**Calling sequence**  
- You must call **open()** to open the serial port before calling **getCts()** to obtain the CTS signal.  
- If **getCts()** is called before **open()**, error code 35700005 (Port not open) will be thrown.

The differences between **getCts()** and **getDsr()** are as follows:  
- **getCts()** queries the CTS signal, and the RTS/CTS signal is used to implement hardware-based flow  
control and determine whether data can be sent. **getDsr()** queries the DSR signal, and the DTR/DSR signal is used to determine whether the communication device is ready.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the CTS signal status. The value **true** indicates that data can be sent, and the value **false** indicates otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [35700001](../errorcode-busmanager-serial.md#35700001-abnormal-service) | Service error. |
| [35700003](../errorcode-busmanager-serial.md#35700003-virtual-serial-port-disconnected) | Virtual serial port disconnected. |
| [35700005](../errorcode-busmanager-serial.md#35700005-port-not-opened) | Port not open. |

**Examples**

```TypeScript
// Import BusinessError from @kit.BasicServicesKit.
// port is a serial port object, which needs to be obtained through serial.getSerialPortList().
// Obtain the CTS signal status.
port.getCts().then((cts: boolean) => {
  console.info('getCts success, cts: ' + cts);
}).catch((error: BusinessError) => {
  console.error(`Failed to get CTS. Code: ${error.code}, message: ${error.message}`);
});
```

## getDsr

```TypeScript
getDsr(): Promise<boolean>
```

Obtains the status of the data set ready (DSR) signal. This API uses a promise to return the result. This method must be called after the serial port is opened. This method queries the status of the DSR signal to determine whether the communication device is ready, for example, checking the device connection status or starting communication after the device is ready.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the DSR signal status. The value **true** indicates that the data device is ready, and the value **false** indicates that the data device is not ready. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [35700001](../errorcode-busmanager-serial.md#35700001-abnormal-service) | Service error. |
| [35700003](../errorcode-busmanager-serial.md#35700003-virtual-serial-port-disconnected) | Virtual serial port disconnected. |
| [35700005](../errorcode-busmanager-serial.md#35700005-port-not-opened) | Port not open. |

**Examples**

```TypeScript
// Import BusinessError from @kit.BasicServicesKit.
// port is a serial port object, which needs to be obtained through serial.getSerialPortList().
// Obtain the DSR signal status.
port.getDsr().then((dsr: boolean) => {
  console.info('getDsr success, dsr: ' + dsr);
}).catch((error: BusinessError) => {
  console.error(`Failed to get DSR. Code: ${error.code}, message: ${error.message}`);
});
```

## offDataRead

```TypeScript
offDataRead(callback?: Callback<Uint8Array>): void
```

Cancels listening for data receiving events on the serial port. This API is used to release resources when listening for data receiving events on the serial port is no longer required, for example, when the application switches to another function or the connection is proactively disconnected.

**API called in pairs**  
- This API is used in pairs with **onDataRead()** to unregister the listener registered by **onDataRead()**.  
- You can unregister all listeners or a specified listener.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;Uint8Array&gt; | No | Callback used to return the result. If a callback is passed, the listener for data receiving events on the specified serial port is unregistered. If no callback is passed, the listeners for data receiving events on all serial ports are unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [35700001](../errorcode-busmanager-serial.md#35700001-abnormal-service) | Service error. |
| [35700005](../errorcode-busmanager-serial.md#35700005-port-not-opened) | Port not open. |

**Examples**

```TypeScript
// port is a serial port object, which needs to be obtained through serial.getSerialPortList().
// Cancel listening for data receiving events on the serial port.
port.offDataRead();

// Cancel the specified listener callback.
let callback = (data: Uint8Array) => {
  console.info(`received data length: ${data.length}`);
};
port.offDataRead(callback);
```

## offDisconnect

```TypeScript
offDisconnect(callback?: Callback<void>): void
```

Unsubscribes from serial port disconnection events. This method must be called after the serial port is opened. This API is used to release resources when listening for serial port disconnection events is no longer required, for example, when the application switches to another function or the connection is proactively disconnected.

**Calling sequence**  
- You must call **open()** to open the serial port before calling **offDisconnect()** to cancel listening.  
- If **offDisconnect()** is called before **open()**, error code 35700005 (Port not open) will be thrown.

**API called in pairs**  
- This API is used in pairs with **onDisconnect()** to unregister the listener registered by  
**onDisconnect()**.  
- You can unregister all listeners or a specified listener.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;void&gt; | No | Callback used to return the result, which can be unregistered only after being registered using **onDisconnect()**. If a callback is passed, the listener for disconnection events on the specified serial port is unregistered. If no callback is passed, the listeners for disconnection events on all serial ports are unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [35700001](../errorcode-busmanager-serial.md#35700001-abnormal-service) | Service error. |
| [35700005](../errorcode-busmanager-serial.md#35700005-port-not-opened) | Port not open. |

**Examples**

```TypeScript
// port is a serial port object, which needs to be obtained through serial.getSerialPortList().
// Unsubscribe from serial port disconnection events.
port.offDisconnect();

// Cancel the specified listener callback.
let disconnectedCallback = () => {
  console.info('serial port disconnected');
};
port.offDisconnect(disconnectedCallback);
```

## onDataRead

```TypeScript
onDataRead(callback: Callback<Uint8Array>): void
```

Listens for data receiving events on the serial port. This API uses an asynchronous callback to return the received data. This API must be called after the serial port is opened. After [close](#close) is called, all callback registrations will be cleared. This API is used to receive data sent by serial port devices in real time, such as sensor data monitoring, device status feedback, and real-time data collection.

**API called in pairs**  
- This API is used in pairs with **offDataRead()**, which is used to unregister the listener.  
- You are advised to call **offDataRead()** to release resources when the listener is no longer needed.

**Calling sequence**  
- You must call **open()** to open the serial port before calling **onDataRead()** to listen for data.  
- If **onDataRead()** is called before **open()**, error code 35700005 (Port not open) will be thrown.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;Uint8Array&gt; | Yes | Callback used to return the data received by the serial port. This callback is used to listen for data receiving events on the serial port. After the callback is registered, it will be triggered when the serial port receives data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [35700001](../errorcode-busmanager-serial.md#35700001-abnormal-service) | Service error. |
| [35700003](../errorcode-busmanager-serial.md#35700003-virtual-serial-port-disconnected) | Virtual serial port disconnected. |
| [35700005](../errorcode-busmanager-serial.md#35700005-port-not-opened) | Port not open. |

**Examples**

```TypeScript
// port is a serial port object, which needs to be obtained through serial.getSerialPortList().
// Listen for data receiving events on the serial port.
port.onDataRead((data: Uint8Array) => {
  console.info(`onDataRead, length: ${data.length}`);
});
```

## onDisconnect

```TypeScript
onDisconnect(callback: Callback<void>): void
```

Subscribes to serial port disconnection events. This API uses an asynchronous callback to return the result. After **close()** is called, all callbacks will be unregistered. This method subscribes to serial port disconnection events, such as removal of a USB virtual serial port, device power-off, or connection interruption. This allows you to handle exceptions in a timely manner, notify users, or attempt to reconnect.

**API called in pairs**  
- This API is used in pairs with **offDisconnect()**, which is used to unregister the listener.  
- You are advised to call **offDisconnect()** to release resources when the listener is no longer needed.

**Calling sequence**  
- You must call **open()** to open the serial port before calling **onDisconnect()** to listen for the  
disconnect event.  
- If **onDisconnect()** is called before **open()**, error code 35700005 (Port not open) will be thrown.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | Callback used to return the result, which is triggered when the serial port is disconnected. This callback is used to listen for disconnection events on the serial port. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [35700001](../errorcode-busmanager-serial.md#35700001-abnormal-service) | Service error. |
| [35700005](../errorcode-busmanager-serial.md#35700005-port-not-opened) | Port not open. |

**Examples**

```TypeScript
// port is a serial port object, which needs to be obtained through serial.getSerialPortList().
// Subscribe to serial port disconnection events.
port.onDisconnect(() => {
  console.info('serial port disconnected');
});
```

## open

```TypeScript
open(config?: SerialConfigs): Promise<void>
```

Opens a serial port device. This API uses a promise to return the result. This API is used to establish a communication connection with a serial port device, for example, to collect sensor data, send device control commands, or use a serial port printer.

**API called in pairs**  
- After calling **open()**, you must call **close()** to release the serial port resources after use.  
- Without doing so, serial port resources will be leaked.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [SerialConfigs](arkts-basicservices-serial-serialconfigs-i.md) | No | Communication parameters of the serial port. If the **config** parameter is not passed, the default configuration of **SerialConfigs** is used to open the serial port. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [35700001](../errorcode-busmanager-serial.md#35700001-abnormal-service) | Service error. |
| [35700002](../errorcode-busmanager-serial.md#35700002-parameter-error) | Invalid parameter. |
| [35700003](../errorcode-busmanager-serial.md#35700003-virtual-serial-port-disconnected) | Virtual serial port disconnected. |
| [35700004](../errorcode-busmanager-serial.md#35700004-port-in-use) | Port already in use. |
| [35700007](../errorcode-busmanager-serial.md#35700007-user-authorization-rejected) | User authorization required. |

**Examples**

```TypeScript
// Import BusinessError from @kit.BasicServicesKit.
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
  // Call port.close() to release resources after the serial port is used.
  await port.close();
}).catch((error: BusinessError) => {
  console.error(`Failed to open serial port. Code: ${error.code}, message: ${error.message}`);
});
```

## sendBrk

```TypeScript
sendBrk(): Promise<void>
```

Sends a BRK signal. This API uses a promise to return the result. This method must be called after the serial port is opened. This method is used to send an interrupt signal to a device, for example, to stop device communication immediately, notify the device to reset, or perform signal interaction required by a special protocol.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [35700001](../errorcode-busmanager-serial.md#35700001-abnormal-service) | Service error. |
| [35700003](../errorcode-busmanager-serial.md#35700003-virtual-serial-port-disconnected) | Virtual serial port disconnected. |
| [35700005](../errorcode-busmanager-serial.md#35700005-port-not-opened) | Port not open. |

**Examples**

```TypeScript
// Import BusinessError from @kit.BasicServicesKit.
// port is a serial port object, which needs to be obtained through serial.getSerialPortList().
// Send a BRK signal.
port.sendBrk().then(() => {
  console.info('sendBrk success');
}).catch((error: BusinessError) => {
  console.error(`Failed to send BRK. Code: ${error.code}, message: ${error.message}`);
});
```

## setDtr

```TypeScript
setDtr(enable: boolean): Promise<void>
```

Sets the status of the data terminal ready (DTR) signal. This API uses a promise to return the result. This method must be called after the serial port is opened. This method is used to control the DTR signal. For example, it can be used to notify a device that the terminal is ready, control device power-on or reset through the DTR signal, or communicate with a device that requires DTR signal detection.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | DTR signal status. The value **true** indicates that the data terminal is ready, and the value **false** indicates that the data terminal is not ready. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [35700001](../errorcode-busmanager-serial.md#35700001-abnormal-service) | Service error. |
| [35700003](../errorcode-busmanager-serial.md#35700003-virtual-serial-port-disconnected) | Virtual serial port disconnected. |
| [35700005](../errorcode-busmanager-serial.md#35700005-port-not-opened) | Port not open. |

**Examples**

```TypeScript
// Import BusinessError from @kit.BasicServicesKit.
// port is a serial port object, which needs to be obtained through serial.getSerialPortList().
// Set the DTR signal.
port.setDtr(true).then(() => {
  console.info('setDtr success');
}).catch((error: BusinessError) => {
  console.error(`Failed to set DTR. Code: ${error.code}, message: ${error.message}`);
});
```

## setRts

```TypeScript
setRts(enable: boolean): Promise<void>
```

Sets the status of the Request to Send (RTS) signal. This API uses a promise to return the result. This method must be called after the serial port is opened. This method is used to control the request sending signal for hardware-based flow control, such as the transmission permission when hardware-based flow control via RTS/CTS is enabled or communication with devices that support hardware-based flow control.

**Calling sequence**  
- You must call **open()** to open the serial port before calling **setRts()** to set the RTS signal.  
- If **setRts()** is called before **open()**, error code 35700005 (Port not open) will be thrown.

Difference between **setRts()** and **setDtr()**: **setRts()** controls the RTS/CTS signal, while **setDtr()** controls the DTR/DSR signal. RTS/CTS is mainly used for data flow control, and automatic flow control can be enabled through **SerialConfigs.rtscts**. DTR/DSR is mainly used for device status control and detection, and is used for special protocols or device status management.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | RTS signal status. The value **true** indicates requesting to send data, and the value **false** indicates otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [35700001](../errorcode-busmanager-serial.md#35700001-abnormal-service) | Service error. |
| [35700003](../errorcode-busmanager-serial.md#35700003-virtual-serial-port-disconnected) | Virtual serial port disconnected. |
| [35700005](../errorcode-busmanager-serial.md#35700005-port-not-opened) | Port not open. |

**Examples**

```TypeScript
// Import BusinessError from @kit.BasicServicesKit.
// port is a serial port object, which needs to be obtained through serial.getSerialPortList().
// Set the RTS signal.
port.setRts(true).then(() => {
  console.info('setRts success');
}).catch((error: BusinessError) => {
  console.error(`Failed to set RTS. Code: ${error.code}, message: ${error.message}`);
});
```

## write

```TypeScript
write(data: Uint8Array, timeout?: number): Promise<number>
```

Writes data to a serial port device. The value range of the data length is (0, 4096]. This API uses a promise to return the result. This API is used to send control commands, data packets, and configuration parameters to a connected serial port device, for example, in industrial control, device debugging, and data collection scenarios. This method must be called after the serial port is opened.

**Calling sequence**  
- You must call **open()** to open the serial port before calling **write()** to send data.  
- If **write()** is called before **open()**, error code 35700005 (Port not open) will be thrown.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | Uint8Array | Yes | Data to be written. Length range: (0, 4096]. If the data to be sent exceeds 4096 bytes, you are advised to call the **write** method multiple times. |
| timeout | number | No | Timeout interval, in milliseconds. The value must be an integer within the range of [0, 300000]. The default value **0** is returned when data cannot be written into the target port. If a negative number, a non-integer, or a number greater than 300000 is passed, error code 35700002 is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the length of the data written. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [35700001](../errorcode-busmanager-serial.md#35700001-abnormal-service) | Service error. |
| [35700002](../errorcode-busmanager-serial.md#35700002-parameter-error) | Invalid parameter. |
| [35700003](../errorcode-busmanager-serial.md#35700003-virtual-serial-port-disconnected) | Virtual serial port disconnected. |
| [35700005](../errorcode-busmanager-serial.md#35700005-port-not-opened) | Port not open. |
| [35700006](../errorcode-busmanager-serial.md#35700006-transmission-timeout) | Transmission timeout. |

**Examples**

```TypeScript
// Import buffer from @kit.ArkTS.
// Import BusinessError from @kit.BasicServicesKit.
// port is a serial port object, which needs to be obtained through serial.getSerialPortList().
// Write data to a serial port device.
let writeData: Uint8Array = new Uint8Array(buffer.from('Hello World', 'utf-8').buffer);
port.write(writeData, 2000).then((size: number) => {
  console.info('write success, size: ' + size);
}).catch((error: BusinessError) => {
  console.error(`Failed to write to serial port. Code: ${error.code}, message: ${error.message}`);
});
```

## portInfo

```TypeScript
readonly portInfo: SerialPortInfo
```

Serial port information.

**Type:** [SerialPortInfo](arkts-basicservices-serial-serialportinfo-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial
