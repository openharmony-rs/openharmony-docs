# Serial Port Communication Development

<!--Kit: Basic Services Kit-->
<!--Subsystem: BusManager-->
<!--Owner: @hwymlgitcode-->
<!--Designer: @hwymlgitcode-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->

## Overview

The serial port communication module (`@ohos.busManager.serial`) provides object-oriented serial port management capabilities. It supports functions such as obtaining the list of available serial ports, enabling or disabling serial ports, reading and writing data, controlling hardware signals, and configuring flow control. This module is applicable to scenarios where data needs to be exchanged through serial ports, such as industrial automation, Internet of Things (IoT) device interconnection, embedded device debugging, and GPS module communication.

## Basic Concepts

When developing serial port communication, you need to understand the following basic concepts:

- **Serial port**

  It is an expansion interface that uses serial communication, where data is transmitted sequentially one bit at a time. The serial port features simple communication lines. Only one pair of transmission lines is required to implement a two-way communication in a long distance.

- **Baud rate**

  It indicates the number of bits transmitted per second and is a metric for measuring the serial port communication rate. Common baud rates include 9600, 19200, 38400, 57600, and 115200. Both communication parties must use the same baud rate to correctly send and receive data.

- **Data bits**

  It indicates the number of actual data bits in communication and can be set to 5, 6, 7, or 8 bits. The most commonly used data bit length is 8 bits.

- **Parity**

  It is used to check the correctness of data transmission. The following modes are supported: none (NONE), odd (ODD), even (EVEN), mark (MARK), and space (SPACE).

- **Stop bits**

  It is used to identify the end of a data packet and can be set to 1 or 2 bits. The most commonly used stop bit length is 1 bit.

- **Flow control**

  It is used to control the data transmission rate and prevent data loss. Common flow control modes include hardware flow control (RTS/CTS) and software flow control (XON/XOFF).

## Implementation Principle

The core process of the serial port communication service is as follows:

1. **Obtaining the serial port list**: The system enumerates the currently available serial port devices and returns the serial port object list.
2. **Opening a serial port**: Select the target serial port, configure communication parameters such as the baud rate, data bit, parity bit, and stop bit, and open the serial port. When the serial port is opened for the first time, the system displays a dialog box to request user authorization. The serial port device can be accessed only after the user approves the authorization. If the user rejects the authorization, error code 35700007 is thrown.
3. **Data transmission and reception**: Data is sent through the write interface, and data is received through the registered data callback listener.
4. **Hardware signal control**: Hardware flow control and status detection are performed through signal lines such as RTS/CTS.
5. **Disabling the serial port**: The serial port is disabled after the communication is complete to release resources.

**Figure 1** Data flow of serial port communication

``` txt
Data written by the application layer → Sent by the serial port driver → Physical serial cable → Peer serial port device
                                              ↓
Data read by the application layer ← Buffered by the serial port driver ← Physical serial cable ← Peer serial port device
```

## Constraints

- Before using the serial port communication function, ensure that the device is correctly connected to the serial port hardware.
- The length of the data to be written ranges from (0, 4096] bytes.
- If the configuration parameters are not set, the default configuration parameters are used (baud rate: 115200 bit/s; data bit: 8; stop bit: 1; parity bit: none; hardware automatic flow control: disabled; software flow control: disabled).
- A serial port can be opened by only one application at a time.
- User authorization becomes invalid in the following scenarios: the USB virtual serial port is removed, the system switches to another user, or the device is restarted. In these cases, re-authorization is required for accessing the serial port again.

## Preparing the Environment

### Environment Requirement

- **Development tool and configuration:**

  As a development tool, DevEco Studio is one of the prerequisites for serial port communication development. Developers can use DevEco Studio to perform development, debugging, and packaging. [Download and install](https://developer.huawei.com/consumer/en/download/) DevEco Studio and verify basic operations to ensure that it can function properly. For details, see [Creating a Project](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-create-new-project) in [DevEco Studio User Guide](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-tools-overview).

- **SDK version configuration:**

  The ArkTS APIs provided by this module require SDK API version 26.0.0 or later.

### Setting Up the Environment

- Install [DevEco Studio](https://developer.huawei.com/consumer/en/download/deveco-studio) 6.1 or later on the PC.
- Update public-SDK to API 26.0.0 or later <!--Del-->. For details about how to update the SDK, see [Update Guide](../../../tools/openharmony_sdk_upgrade_assistant.md)<!--DelEnd-->.
- Prepare a serial cable and connect the serial port of the OpenHarmony device to the serial port of the target device.

## Development Guide

### API Description

The following table describes the main APIs for serial port communication.

| API| Description|
|--------|------|
| [SerialPort.getSerialPortList](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#serialgetserialportlist)(): Promise&lt;[SerialPort](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#serialport)[]&gt; | Queries the serial port device list. The [SerialPort](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#serialport) object array is returned. This API uses a promise to return the result.|
| [SerialPort.open](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#open)(config?: [SerialConfigs](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#serialconfigs)): Promise&lt;void&gt; | Opens a serial port device. When a serial port device is opened for the first time, the system displays a dialog box asking the user to authorize access to the target serial port. If the user rejects the request, error code 35700007 is thrown. The authorization expires upon removal of the USB virtual serial port, system user switching, or restart of the device. Re-authorization is required in this case. This API uses a promise to return the result.|
| [SerialPort.close](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#close)(): Promise&lt;void&gt; | Closes a serial port device. This API uses a promise to return the result.|
| [SerialPort.write](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#write)(data: Uint8Array, timeout?: number): Promise&lt;number&gt; | Sends data to a serial port device. The length range of the data sent each time is (0, 4096]. This API uses a promise to return the result.|
| [SerialPort.onDataRead](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#ondataread)(callback: Callback&lt;Uint8Array&gt;): void | Listens for data receiving events on the serial port. This API uses an asynchronous callback to return the received data. After [close](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#close) is called, all callbacks are cleared.|
| [SerialPort.offDataRead](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#offdataread)(callback?: Callback&lt;Uint8Array&gt;): void | Cancels listening for data receiving events on the serial port. This API uses an asynchronous callback to return the result.|
| [SerialPort.flush](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#flush)(): Promise&lt;void&gt; | Flushes the serial port buffer, including the read buffer and write buffer. Data in the buffer will be directly discarded and will not be sent or read. This API uses a promise to return the result.|
| [SerialPort.drain](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#drain)(): Promise&lt;void&gt; | Waits until all write requests are complete. This API uses a promise to return the result.|
| [SerialPort.setRts](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#setrts)(enable: boolean): Promise&lt;void&gt; | Sets the status of the request to send (RTS) signal. This API uses a promise to return the result.|
| [SerialPort.getCts](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#getcts)(): Promise&lt;boolean&gt; |  Obtains the status of the clear to send (CTS) signal. This API uses a promise to return the result.|
| [SerialPort.sendBrk](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#sendbrk)(): Promise&lt;void&gt; | Sends a BRK signal. This API uses a promise to return the result.|

[SerialConfigs](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#serialconfigs) parameter description:

| Name| Type| Mandatory| Default Value| Description|
|--------|------|------|--------|------|
| baudRate | number | No| 115200 | Baud rate.|
| dataBits | [DataBits](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#databits) | No| DataBits.EIGHT | Data bits.|
| stopBits | [StopBits](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#stopbits) | No| StopBits.ONE | Stop bits.|
| parity | [Parity](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#parity) | No| Parity.NONE | Parity bit.|
| rtscts | boolean | No| false | Check whether RTS/CTS hardware automatic flow control is enabled. **true** to enable; **false** otherwise.|
| xon | boolean | No| false | Check whether XON software flow control is enabled. **true** to enable; **false** otherwise.|
| xoff | boolean | No| false | Check whether XOFF software flow control is enabled. **true** to enable; **false** otherwise.|
| xany | boolean | No| false | Check whether the software flow control restart for any character is enabled. **true** to enable; **false** otherwise.|

### Development Procedure

> **NOTE**
>
> The following sample code is only a necessary process for serial port communication and needs to be executed in a specific method.

1. Import the module.

   <!-- @[head](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Serial/SerialManagerSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   import { serial, BusinessError } from '@kit.BasicServicesKit';
   ```

2. Obtain the serial port device list.

   <!-- @[getSerialPortList](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Serial/SerialManagerSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   try {
     const portList = await serial.getSerialPortList();
     console.info(`${TAG} getSerialPortList success, count: ${portList.length}`);
     portList.forEach((port: serial.SerialPort, index: number) => {
       console.info(`${TAG}   [${index}] portName=${port.portInfo.portName}, vendorId=${port.portInfo.vendorId}, productId=${port.portInfo.productId}`);
     });
     if (portList.length > 0) {
       this.port = portList[0];
     }
   } catch (err) {
     const e = err as BusinessError;
     console.error(`${TAG} getSerialPortList failed, code: ${e.code}, message: ${e.message}`);
   }
   ```

3. Open the serial port device.

   <!-- @[open](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Serial/SerialManagerSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   try {
     if (!this.port) {
       console.error(`${TAG} No serial port found, please call getSerialPortList first`);
       return;
     }
     const config: serial.SerialConfigs = {
       baudRate: 115200,
       dataBits: serial.DataBits.EIGHT,
       stopBits: serial.StopBits.ONE,
       parity: serial.Parity.NONE
     };
     await this.port.open(config);
     console.info(`${TAG} open success`);
   } catch (err) {
     const e = err as BusinessError;
     console.error(`${TAG} open failed, code: ${e.code}, message: ${e.message}`);
   }
   ```

4. Register a callback to receive data and listen for serial port data.

   <!-- @[onDataRead](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Serial/SerialManagerSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   try {
     if (!this.port) {
       console.error(`${TAG} No serial port found, please call getSerialPortList first`);
       return;
     }
     this.dataCallback = (data: Uint8Array) => {
       console.info(`${TAG} onDataRead: ${Array.from(data).join(', ')}`);
     };
     this.port.onDataRead(this.dataCallback);
     console.info(`${TAG} onDataRead registered`);
   } catch (err) {
     const e = err as BusinessError;
     console.error(`${TAG} onDataRead failed, code: ${e.code}, message: ${e.message}`);
   }
   ```

5. Write data through the serial port.

   <!-- @[write](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Serial/SerialManagerSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   try {
     if (!this.port) {
       console.error(`${TAG} No serial port found, please call getSerialPortList first`);
       return;
     }
     const data = new Uint8Array([0x48, 0x65, 0x6C, 0x6C, 0x6F]);
     const writeLen = await this.port.write(data);
     console.info(`${TAG} write success, length: ${writeLen}`);
   } catch (err) {
     const e = err as BusinessError;
     console.error(`${TAG} write failed, code: ${e.code}, message: ${e.message}`);
   }
   ```

6. Refresh the buffer and wait until the sending is complete.

   <!-- @[flush](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Serial/SerialManagerSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   try {
     if (!this.port) {
       console.error(`${TAG} No serial port found, please call getSerialPortList first`);
       return;
     }
     await this.port.flush();
     console.info(`${TAG} flush success`);
   } catch (err) {
     const e = err as BusinessError;
     console.error(`${TAG} flush failed, code: ${e.code}, message: ${e.message}`);
   }
   ```

7. Hardware signal control.

   * Set the RTS signal to high level.

     <!-- @[setRts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Serial/SerialManagerSample/entry/src/main/ets/pages/Index.ets) -->
     
     ``` TypeScript
     try {
       if (!this.port) {
         console.error(`${TAG} No serial port found, please call getSerialPortList first`);
         return;
       }
       await this.port.setRts(true);
       console.info(`${TAG} setRts(true) success`);
     } catch (err) {
       const e = err as BusinessError;
       console.error(`${TAG} setRts failed, code: ${e.code}, message: ${e.message}`);
     }
     ```

   * Obtain the CTS signal status.

     <!-- @[getCts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Serial/SerialManagerSample/entry/src/main/ets/pages/Index.ets) -->
     
     ``` TypeScript
     try {
       if (!this.port) {
         console.error(`${TAG} No serial port found, please call getSerialPortList first`);
         return;
       }
       const ctsStatus = await this.port.getCts();
       console.info(`${TAG} getCts success, CTS: ${ctsStatus}`);
     } catch (err) {
       const e = err as BusinessError;
       console.error(`${TAG} getCts failed, code: ${e.code}, message: ${e.message}`);
     }
     ```

   * Send the break signal.

     <!-- @[sendBrk](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Serial/SerialManagerSample/entry/src/main/ets/pages/Index.ets) -->
     
     ``` TypeScript
     try {
       if (!this.port) {
         console.error(`${TAG} No serial port found, please call getSerialPortList first`);
         return;
       }
       await this.port.sendBrk();
       console.info(`${TAG} sendBrk success`);
     } catch (err) {
       const e = err as BusinessError;
       console.error(`${TAG} sendBrk failed, code: ${e.code}, message: ${e.message}`);
     }
     ```

8. Deregister the callback for receiving data and close the serial port device.

   <!-- @[close](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Serial/SerialManagerSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   try {
     if (!this.port) {
       console.error(`${TAG} No serial port found, please call getSerialPortList first`);
       return;
     }
     await this.port.close();
     console.info(`${TAG} close success`);
     this.port = null;
   } catch (err) {
     const e = err as BusinessError;
     console.error(`${TAG} close failed, code: ${e.code}, message: ${e.message}`);
   }
   ```

### Debugging and Verification

1. Prepare a serial cable and connect the serial port of the OpenHarmony device to the serial port of the target device.
2. Run the preceding sample code on the OpenHarmony device.
3. If the `success` log is returned, the related API is successfully called and the serial port communication capability of the device is normal. If the `failed` or `error` log is returned, the API fails to be called. In this case, check the hardware connection and parameter settings.
4. You can perform a loopback test (short-circuit the TX and RX of the serial port) to check whether the self-sending and self-receiving function of the data is normal.
<!--no_check-->