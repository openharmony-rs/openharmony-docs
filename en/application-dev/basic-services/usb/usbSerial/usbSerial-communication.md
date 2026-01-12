# USB Serial Communication Management

<!--Kit: Basic Services Kit-->
<!--Subsystem: USB-->
<!--Owner: @hwymlgitcode-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @w_Machine_cc-->

## Overview

In the USB serial communication service, the USB port of the host is connected to the serial port of the serial port device for serial data transmission. The core objective of communication management is to implement efficient and stable data transmission and collaborative control between devices. It is mainly used in scenarios such as industrial automation and remote management, IoT device interconnection, and medical device management.

## Preparing the Environment

For details, see [Preparing the Environment](usbSerial-overview.md#preparing-the-environment) in *USB Serial Communication Development Overview*.

## How to Develop

### Available APIs

| API                                                                         | Description                      |
|------------------------------------------------------------------------------|--------------------------|
| getPortList(): Readonly&lt;SerialPort&gt;[]                                        | Obtains the serial port device list.               |
| hasSerialRight(portId: number): boolean                                      | Checks whether the application has the permission to access the serial port device.    |
| requestSerialRight(portId: number): Promise&lt;boolean&gt;                         | Requests the permission to access the serial port device.           |
| open(portId: number): void                                                   | Opens a serial port device.                 |
| close(portId: number): void                                                  | Closes a serial port device.                 |
| read(portId: number, buffer: Uint8Array, timeout?: number): Promise&lt;number&gt;  | Reads data from a serial port device. This API uses a promise to return the result.|
| readSync(portId: number, buffer: Uint8Array, timeout?: number): number       | Reads data from a serial port device in a synchronous manner.         |
| write(portId: number, buffer: Uint8Array, timeout?: number): Promise&lt;number&gt; | Writes data to a serial port device. This API uses a promise to return the result.|
| writeSync(portId: number, buffer: Uint8Array, timeout?: number): number      | Writes data to a serial port device in a synchronous manner.         |


### Development Procedure

You can read and write data as follows:

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


5. Read data through the serial port.

   <!-- @[serialRead](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/USB/USBManagerSerialSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   let portId: number = this.portId_;
   // Read data asynchronously.
   let readBuffer: Uint8Array = new Uint8Array(64);
   serialManager.read(portId, readBuffer, 2000).then((size: number) => {
     console.info(`readAsync usbSerial success, readAsyncBuffer: ${readBuffer}`);
     this.logInfo_ += '\n[INFO] readAsync usbSerial success, readAsyncBuffer: ' + JSON.stringify(readBuffer);
   }).catch((error: Error) => {
     console.error(`readAsync usbSerial error: ${error}`);
     this.logInfo_ += '\n[ERROR] readAsync usbSerial error: ' + JSON.stringify(error);
   })
   
   // Read data synchronously.
   let readSyncBuffer: Uint8Array = new Uint8Array(64);
   try {
     serialManager.readSync(portId, readSyncBuffer, 2000);
     console.info(`readSync usbSerial success, readSyncBuffer: ${readSyncBuffer}`);
     this.logInfo_ += '\n[INFO] readSync usbSerial success, readSyncBuffer: ' + JSON.stringify(readSyncBuffer);
   } catch (error) {
     console.error(`readSync usbSerial error: ${error}`);
     this.logInfo_ += '\n[ERROR] readSync usbSerial error: ' + JSON.stringify(error);
   }
   ```


6. Write data through the serial port.

   <!-- @[serialWrite](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/USB/USBManagerSerialSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   let portId: number = this.portId_;
   // Write data asynchronously.
   let writeBuffer: Uint8Array = new Uint8Array(buffer.from('Hello World', 'utf-8').buffer)
   serialManager.write(portId, writeBuffer, 2000).then((size: number) => {
     console.info(`writeAsync usbSerial success, writeAsyncBuffer: ${writeBuffer}`);
     this.logInfo_ += '\n[INFO] writeAsync usbSerial success, writeAsyncBuffer: ' + JSON.stringify(writeBuffer);
   }).catch((error: Error) => {
     console.error(`writeAsync usbSerial error: ${error}`);
     this.logInfo_ += '\n[ERROR] writeAsync usbSerial error: ' + JSON.stringify(error);
   })
   
   // Write data synchronously.
   let writeSyncBuffer: Uint8Array = new Uint8Array(buffer.from('Hello World', 'utf-8').buffer)
   try {
     serialManager.writeSync(portId, writeSyncBuffer, 2000);
     console.info(`writeSync usbSerial success, writeSyncBuffer: ${writeSyncBuffer}`);
     this.logInfo_ += '\n[INFO] writeSync usbSerial success, writeSyncBuffer: ' + JSON.stringify(writeSyncBuffer);
   } catch (error) {
     console.error(`writeSync usbSerial error: ${error}`);
     this.logInfo_ += '\n[ERROR] writeSync usbSerial error: ' + JSON.stringify(error);
   }
   ```

   
7. Close a serial port device.

   <!-- @[closeSerialDevice](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/USB/USBManagerSerialSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   let portId: number = this.portId_;
   try {
     serialManager.close(portId);
     console.info(`close usbSerial success, portId: ${portId}`);
     this.logInfo_ += '\n[INFO] close usbSerial success, portId: ' + JSON.stringify(portId);
   } catch (error) {
     console.error(`close usbSerial error: ${error}`);
     this.logInfo_ += '\n[ERROR] close usbSerial error: ' + JSON.stringify(error);
   }
   ```

### Debugging and Verification

1. Prepare a USB-to-serial cable. Connect the USB port and the serial port of the cable to that of the OpenHarmony device.
2. Execute the preceding sample code on the OpenHarmony device.
3. Return **usbSerial success** if the related API is successfully called and the serial port communication of the device runs properly; return **usbSerial error** otherwise.
