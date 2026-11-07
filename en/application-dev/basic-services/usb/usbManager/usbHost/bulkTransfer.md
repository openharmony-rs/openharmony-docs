# USB Bulk Transfer (ArkTS)

<!--Kit: Basic Services Kit-->
<!--Subsystem: USB-->
<!--Owner: @hwymlgitcode-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=4783193a2c38a164702de1ebb6fd94773c15aff1 translatedAt=2026-10-28T12:18:05.152Z pushedAt=2026-10-28T12:42:43.484Z nl=1 -->

## When to Use

Bulk transfer is used to transfer and receive a large amount of data without bandwidth or interval requirements, for example, file or image transfer. Devices such as printers and scanners support this type of transfer.

## Preparing the Environment

### Environment Requirements

- Development tool and configuration:

  DevEco Studio, as the driver development tool, allows you to develop, debug, and package drivers. [Download and install](https://developer.huawei.com/consumer/en/download/) DevEco Studio and verify basic operations to ensure that it can function properly. For details, see [Creating a Project](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-create-new-project) in [DevEco Studio User Guide](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-tools-overview).


- SDK version configuration:

  The ArkTS APIs provided by Extended Peripheral Management require SDK API version 16 or later.


- HDC configuration:

  HarmonyOS Device Connector (hdc) is a command-line tool for debugging. It can be used to interact with real devices or the Emulator on Windows, Linux, and macOS. For details about the configuration, see [hdc](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/hdc).

### Environment Setup

- Install [DevEco Studio](https://developer.huawei.com/consumer/en/download/) 4.1 or later on the PC.
- Update the public-SDK to API 16 or later<!--Del-->. For details about updating the SDK, see [Update Guide](../../../../faqs/full-sdk-switch-guide.md)<!--DelEnd-->.
- Install hdc on the PC. You can use it to interact with a real device or the Emulator on Windows, Linux, or macOS.
- Use a USB cable to connect a device to the PC.

## How to Develop

### Available APIs

| API                                                                                                              | Description                   |
|-------------------------------------------------------------------------------------------------------------------|-----------------------|
| bulkTransfer(pipe: USBDevicePipe, endpoint: USBEndpoint, buffer: Uint8Array, timeout ?: number): Promise&lt;number&gt;  | Performs bulk transfer.                |

For more details about the APIs for device management and transfer modes, see [@ohos.usbManager](../../../../reference/apis-basic-services-kit/js-apis-usbManager.md).

### Development Procedure

Connect a host to a device and use the **bulkTransfer** API to transfer data. The following steps describe how to implement a bulk transfer:

> **NOTE** 
>
> The following sample code shows only a basic process. You should execute the code in a specific method. When calling this method, you must comply with device protocols to ensure proper data transfer and device compatibility.

1. Import modules.

   <!-- @[head](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/USB/USBManagerSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // Import the usbManager module.
   import { usbManager, BusinessError } from '@kit.BasicServicesKit';
   import { JSON } from '@kit.ArkTS';
   ```

   
2. Obtain the USB device list.

   > **NOTE** 
   >
   > Bulk transfer can be performed only on the endpoint whose [transfer type](../../../../reference/apis-basic-services-kit/js-apis-usbManager.md#usbendpointtransfertype18) is **2**. If an incorrect endpoint type is used, an I/O error is returned.
   
   <!-- @[getDevices](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/USB/USBManagerSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // Obtain the USB device list.
   let deviceList: usbManager.USBDevice[] = [];
   try {
     deviceList = usbManager.getDevices();
   } catch (error) {
     let errorObj: BusinessError = error as BusinessError;
     console.error(`USB getDevices failed: code=${errorObj.code}, message=${errorObj.message}`);
     this.logInfo_ += '\n[ERROR] USB getDevices failed: code=' + errorObj.code + ', message=' + errorObj.message;
   }
   
   console.info(`deviceList: ${deviceList}`);
   this.logInfo_ += '\n[INFO] deviceList: ' + JSON.stringify(deviceList);
   if (deviceList === undefined || deviceList.length === 0) {
     console.error('deviceList is empty');
     this.logInfo_ += '\n[ERROR] deviceList is empty';
     return;
   }
   /*
     deviceList structure example
     [
       {
         name: '1-1',
         serial: '',
         manufacturerName: '',
         productName: '',
         version: '',
         vendorId: 7531,
         productId: 2,
         clazz: 9,
         subClass: 0,
         protocol: 1,
         devAddress: 1,
         busNum: 1,
         configs: [
           {
             id: 1,
             attributes: 224,
             isRemoteWakeup: true,
             isSelfPowered: true,
             maxPower: 0,
             name: '1-1',
             interfaces: [
               {
                 id: 0,
                 protocol: 0,
                 clazz: 9,
                 subClass: 0,
                 alternateSetting: 0,
                 name: '1-1',
                 endpoints: [
                   {
                     address: 129,
                     attributes: 3,
                     interval: 12,
                     maxPacketSize: 4,
                     direction: 128,
                     number: 1,
                     type: 3,
                     interfaceId: 0,
                   }
                 ]
               }
             ]
           }
         ]
       }
     ]
    */
   this.deviceList_ = deviceList;
   ```


3. Obtain the device operation permissions.

   <!-- @[requestRight](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/USB/USBManagerSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   if (this.deviceList_ === undefined || this.deviceList_.length === 0) {
     console.error('deviceList is empty');
     this.logInfo_ += '\n[ERROR] deviceList is empty';
     return;
   }
   let deviceList: usbManager.USBDevice[] = this.deviceList_;
   let deviceName: string = deviceList[0].name;
   // Request the permissions to operate a specified device.
   usbManager.requestRight(deviceName).then((hasRight: boolean) => {
     console.info('usb device request right result: ' + hasRight);
     this.logInfo_ += '\n[INFO] usb device request right result: ' + JSON.stringify(hasRight);
   }).catch((error: BusinessError) => {
     console.error(`usb device request right failed : code=${error.code}, message=${error.message}`);
     this.logInfo_ += '\n[ERROR] usb device request right failed: code=' + error.code + ', message=' + error.message;
   });
   ```


4. Open the device.

   <!-- @[connectDevice](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/USB/USBManagerSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   if (this.deviceList_ === undefined || this.deviceList_.length === 0) {
     console.error('deviceList is empty');
     this.logInfo_ += '\n[ERROR] deviceList is empty';
     return;
   }
   let deviceList: usbManager.USBDevice[] = this.deviceList_;
   try {
     if (!usbManager.hasRight(deviceList[0]?.name)) {
       console.error('permission denied');
       this.logInfo_ += '\n[ERROR] permission denied';
       return;
     }
     // Open the device and obtain the data transfer channel.
     let pipe: usbManager.USBDevicePipe = usbManager.connectDevice(deviceList[0]);
     if (!pipe) {
       console.error('connectDevice failed, pipe is undefined');
       this.logInfo_ += '\n[ERROR] connectDevice failed, pipe is undefined';
       return;
     }
     if (!deviceList?.[0]?.configs?.[0]?.interfaces?.[0]) {
       console.error('invalid interface');
       this.logInfo_ += '\n[ERROR] invalid interface';
       return;
     }
     let interface1: usbManager.USBInterface = deviceList?.[0]?.configs?.[0]?.interfaces?.[0];
     /*
       Open the corresponding interface and select the corresponding interface from the device information (deviceList).
       interface1 is an interface in the device configuration.
       When the switch is off, call claimInterface (shared occupation, returns 0 on success),
       When the switch is on, call claimInterfaceExclusive (exclusive occupation, throws BusinessError on failure).
      */
     if (this.isExclusiveClaim_) {
       usbManager.claimInterfaceExclusive(pipe, interface1, true, (conflict: usbManager.InterfaceConflictInfo) => {
         // Asynchronous conflict notification when another application claims the same interface
         const conflictMsg = `busNum = ${conflict.busNum}, devAddr = ${conflict.devAddr}, ` +
           `interfaceId = ${conflict.interfaceId}`;
         console.info(`interface conflict: ${conflictMsg}`);
         this.logInfo_ += `\n[INFO] interface conflict: ${conflictMsg}`;
       });
       console.info('claimInterfaceExclusive success');
       this.logInfo_ += '\n[INFO] claimInterfaceExclusive success';
     } else {
       let claimInterfaceResult: number = usbManager.claimInterface(pipe, interface1, true);
       if (claimInterfaceResult !== 0) {
         console.error(`claimInterface error = ${claimInterfaceResult}`);
         this.logInfo_ += '\n[ERROR] claimInterface error = ' + JSON.stringify(claimInterfaceResult);
         return;
       }
     }
     this.pipe_ = pipe;
     this.interface_ = interface1;
     console.info('open device success');
     this.logInfo_ += '\n[INFO] open device success';
   } catch (error) {
     let errorObj: BusinessError = error as BusinessError;
     console.error(`USB hasRight failed: code=${errorObj.code}, message=${errorObj.message}`);
     this.logInfo_ += '\n[ERROR] USB hasRight failed: code=' + errorObj.code + ', message=' + errorObj.message;
   }
   ```


5. Perform data transfer.

   > **NOTE**
   >
   > Before data transfer, obtain the type of the endpoint to which the interface belongs, and use the type to determine whether the interface supports the required transfer type.
   >
   > If the transfer API call fails, first check whether the device interface supports mode switching. If alternateSetting supports switching settings, call [usbManager.setInterface](../../../../reference/apis-basic-services-kit/js-apis-usbManager.md#usbmanagersetinterface) before the transfer to reset the interface so that the endpoint matches the transfer type and normal endpoint communication is ensured.

   <!-- @[bulkTransfer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/USB/USBManagerSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   if (this.pipe_ === undefined || this.interface_ === undefined) {
     console.error('pipe_ or interface_ is null');
     this.logInfo_ += '\n[ERROR] pipe_ or interface_ is null';
     return;
   }
   let pipe: usbManager.USBDevicePipe = this.pipe_;
   let interface1: usbManager.USBInterface = this.interface_;
   /*
     Read data, and select the endpoint for data reception from the device information for data transfer
    (endpoint.direction == 0x80); dataUint8Array is the data to read, of the Uint8Array type.
    */
   let inEndpoint: usbManager.USBEndpoint = interface1.endpoints?.[1];
   let outEndpoint: usbManager.USBEndpoint = interface1.endpoints?.[0];
   let dataUint8Array: Uint8Array = new Uint8Array(1024);
   if (inEndpoint !== undefined && inEndpoint.direction === 0x80) {
     usbManager.bulkTransfer(pipe, inEndpoint, dataUint8Array, 15000).then((dataLength: number) => {
       if (dataLength >= 0) {
         console.info(`usb readData result Length : ${dataLength}`);
         this.logInfo_ += '\n[INFO] usb readData result Length: ' + JSON.stringify(dataLength);
       } else {
         console.error('usb readData failed');
         this.logInfo_ += '\n[ERROR] usb readData failed';
       }
     }).catch((error: BusinessError) => {
       console.error(`usb readData error : code=${error.code}, message=${error.message}`);
       this.logInfo_ += '\n[ERROR] usb readData error: code=' + error.code + ', message=' + error.message;
     });
   }
   
   // Send data. Select the corresponding TX endpoint from deviceList for data transfer. (endpoint.direction == 0)
   if (outEndpoint !== undefined && outEndpoint.direction === 0) {
     usbManager.bulkTransfer(pipe, outEndpoint, dataUint8Array, 15000).then((dataLength: number) => {
       if (dataLength >= 0) {
         console.info(`usb writeData result write length : ${dataLength}`);
         this.logInfo_ += '\n[INFO] usb writeData result write length: ' + JSON.stringify(dataLength);
       } else {
         console.error('usb writeData failed');
         this.logInfo_ += '\n[ERROR] usb writeData failed';
       }
     }).catch((error: BusinessError) => {
       console.error(`usb writeData error : code=${error.code}, message=${error.message}`);
       this.logInfo_ += '\n[ERROR] usb writeData error: code=' + error.code + ', message=' + error.message;
     });
   }
   ```


6. Release the USB interface, and close the USB device pipe.

   <!-- @[closePipe](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/USB/USBManagerSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   if (this.pipe_ === undefined || this.interface_ === undefined) {
     console.error('pipe_ or interface_ is null');
     this.logInfo_ += '\n[ERROR] pipe_ or interface_ is null';
     return;
   }
   let pipe: usbManager.USBDevicePipe = this.pipe_;
   let interface1: usbManager.USBInterface = this.interface_;
   try {
     usbManager.releaseInterface(pipe, interface1);
     usbManager.closePipe(pipe);
   } catch (error) {
     let errorObj: BusinessError = error as BusinessError;
     console.error(`failed: code=${errorObj.code}, message=${errorObj.message}`);
     this.logInfo_ += '\n[ERROR] failed: code=' + errorObj.code + ', message=' + errorObj.message;
   }
   
   this.pipe_ = undefined;
   this.interface_ = undefined;
   console.info('close device success');
   this.logInfo_ += '\n[INFO] close device success';
   ```
