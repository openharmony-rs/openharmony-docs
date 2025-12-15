# USB Serial Configuration Management

<!--Kit: Basic Services Kit-->
<!--Subsystem: USB-->
<!--Owner: @hwymlgitcode-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @w_Machine_cc-->

## Overview

In the USB serial configuration management, the baud rate, data bit, parity bit, and stop bit are the core parameters of the serial port communication protocol. They define the format and rules of data transmission. By properly setting these parameters, you can significantly improve the reliability and efficiency of serial port communication.

### Basic Concepts

Before developing the USB serial port, you should have a basic understanding of the following concepts:

- Baud rate

  The baud rate indicates the number of symbols transmitted by a serial port device per second. A symbol is a binary bit, including the data bit, start bit, stop bit, and parity bit. The unit is baud. For example, 9600 baud indicates that 9600 symbols are transmitted per second. The sender and receiver must use the same baud rate. Otherwise, data cannot be correctly parsed.


- Data bit

  The data bit indicates the number of valid binary bits actually transmitted in each data packet, which determines the data capacity of a single character. Commonly, a data bit may consist of five to eight digits. The data bit determines the amount of information transmitted at a time. The more the data bits, the larger the amount of information transmitted at a time, but more time is required for synchronization.


- Parity bit

  A parity bit is a 1-bit binary value appended to a data frame. It is generated based on the content of the data bit according to specific rules. Commonly, for an odd parity check, the total number of **1** in the data bits and parity bit is an odd number; for an even parity check, the total number of **1** is an even number; for no parity check, no parity bit is added to the data bit. By verifying the number of **1** in the data bit, the parity bit determines whether errors such as bit flipping and noise interference occur during data transfer. Increasing the parity bit slightly reduces the transfer efficiency but improves the error tolerance.


- Stop bit

  The stop bit is located at the end of a data frame. It is a logic high-level signal and is used to identify the end of a character (data packet) transfer. Its length can be 1 bit or 2 bits. (In actual development, 1 bit is most commonly used and 2 bits are mainly used in anti-interference scenarios.) A core function of this bit is to provide a space to tolerate the errors that may occur during time-sequence synchronization for a receiver and ensure data integrity.


## Preparing the Environment

For details, see [Preparing the Environment](usbSerial-overview.md#preparing-the-environment) in *USB Serial Communication Development Overview*.

## How to Develop

### Available APIs

| API                                                                         | Description       |
|------------------------------------------------------------------------------|-----------|
| getAttribute(portId: number): Readonly&lt;SerialAttribute&gt;                      | Obtains the serial port device configuration.|
| setAttribute(portId: number, attribute: SerialAttribute): void               | Sets the serial port device configuration.|

### Development Procedure

You can obtain and set the serial port configuration as follows:

> **NOTE**
>
> The following sample code shows only a basic process. You should execute the code in a specific method.

1. Import the **usbManager** module.

   <!-- @[head](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/USB/USBManagerSerialSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // Import the usbManager module.
   import { serialManager } from '@kit.BasicServicesKit';
   import { BusinessError } from '@kit.BasicServicesKit'
   import { buffer } from '@kit.ArkTS';
   import { JSON } from '@kit.ArkTS';
   ```

2. Obtain the USB device list.

   <!-- @[getPortList](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/USB/USBManagerSerialSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // Obtain the list of USB devices connected to the host.
   let portList: serialManager.SerialPort[] = serialManager.getPortList();
   console.info(`usbSerial portList: ${portList}`);
   this.logInfo_ += '\n[INFO] usbSerial portList: ' + JSON.stringify(portList);
   if (portList === undefined || portList.length === 0) {
     console.error('usbSerial portList is empty');
     this.logInfo_ += '\n[ERROR] usbSerial portList is empty';
     return;
   }
   this.portList_ = portList;
   ```


3. Obtain the device operation permissions.

   <!-- @[requestSerialRight](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/USB/USBManagerSerialSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   if (this.portList_ === undefined || this.portList_.length === 0) {
     console.error('usbSerial portList is empty');
     this.logInfo_ += '\n[ERROR] usbSerial portList is empty';
     return;
   }
   let portList: serialManager.SerialPort[] = this.portList_;
   let portId: number = portList[0].portId;
   if (!serialManager.hasSerialRight(portId)) {
     serialManager.requestSerialRight(portId).then((result: boolean) => {
       console.info('serial device request right result: ' + result);
       this.logInfo_ += '\n[INFO] serial device request right result: ' + JSON.stringify(result);
     }).catch((error: BusinessError) => {
       console.error(`usb device request right failed : ${error}`);
       this.logInfo_ += '\n[ERROR] usb device request right failed: ' + JSON.stringify(error);
     });
   } else {
     console.info('serial device already request right');
     this.logInfo_ += '\n[INFO] serial device already request right';
   }
   this.portId_ = portId;
   ```

4. Open the device based on the serial port.

   <!-- @[openSerialDevice](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/USB/USBManagerSerialSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   let portId: number = this.portId_;
   try {
     serialManager.open(portId)
     console.info(`open usbSerial success, portId: ${portId}`);
     this.logInfo_ += '\n[INFO] open usbSerial success, portId: ' + JSON.stringify(portId);
   } catch (error) {
     console.error(`open usbSerial error: ${error}`);
     this.logInfo_ += '\n[ERROR] open usbSerial error: ' + JSON.stringify(error);
   }
   ```

5. Obtain and modify serial port configurations.

   <!-- @[getSerialConfig](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/USB/USBManagerSerialSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   let portId: number = this.portId_;
   // Obtain the serial port configuration.
   try {
     let attribute: serialManager.SerialAttribute = serialManager.getAttribute(portId);
     if (attribute === undefined) {
       console.error('getAttribute usbSerial error, attribute is undefined');
       this.logInfo_ += '\n[ERROR] getAttribute usbSerial error, attribute is undefined';
     } else {
       console.info(`getAttribute usbSerial success, attribute: ${attribute}`);
       this.logInfo_ += '\n[INFO] getAttribute usbSerial success, attribute: ' + JSON.stringify(attribute);
     }
   } catch (error) {
     console.error(`getAttribute usbSerial error: ${error}`);
     this.logInfo_ += '\n[ERROR] getAttribute usbSerial error: ' + JSON.stringify(error);
   }
   ```

   <!-- @[setSerialConfig](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/USB/USBManagerSerialSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   let portId: number = this.portId_;
   // Set the serial port configuration.
   try {
     let attribute: serialManager.SerialAttribute = {
       baudRate: serialManager.BaudRates.BAUDRATE_9600,
       dataBits: serialManager.DataBits.DATABIT_8,
       parity: serialManager.Parity.PARITY_NONE,
       stopBits: serialManager.StopBits.STOPBIT_1
     }
     serialManager.setAttribute(portId, attribute);
     console.info(`setAttribute usbSerial success, attribute: ${attribute}`);
     this.logInfo_ += '\n[INFO] setAttribute usbSerial success, attribute: ' + JSON.stringify(attribute);
   } catch (error) {
     console.error(`setAttribute usbSerial error: ${error}`);
     this.logInfo_ += '\n[ERROR] setAttribute usbSerial error: ' + JSON.stringify(error);
   }
   ```

### Debugging and Verification

1. Prepare a USB-to-serial cable. Connect the USB port and the serial port of the cable to that of the OpenHarmony device.
2. Execute the preceding sample code on the OpenHarmony device.
3. Return **getAttribute usbSerial success** and **setAttribute usbSerial success** if related APIs are successfully called. You can view the current serial port configuration.
