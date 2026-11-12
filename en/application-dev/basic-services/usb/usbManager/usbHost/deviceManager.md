# USB Device Management (ArkTS)

<!--Kit: Basic Services Kit-->
<!--Subsystem: USB-->
<!--Owner: @hwymlgitcode-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=153a2d56058c66354e11239cdb98b8313af7ef4e translatedAt=2026-11-06T12:08:38.118Z pushedAt=2026-11-09T12:37:29.178Z nl=1 -->

## When to Use

When a USB device is plugged in, you can use `usbManager` to obtain basic information about the USB device, such as the device type and supported functions. The host communicates with the USB device mainly through the encapsulated pipe. In the OpenHarmony system, the USB management service is a core component responsible for managing connections and communication with USB devices. Through the USB management service, applications can detect the connection and disconnection of USB devices, manage permission requests and device configuration for USB devices, and perform data transfer and device control.

## Preparing the Environment

### Environment Requirements

- Development tool and configuration:

  DevEco Studio, as the driver development tool, allows you to develop, debug, and package drivers. [Download and install](https://developer.huawei.com/consumer/en/download/) DevEco Studio and verify basic operations to ensure that it can function properly. For details, see [Creating a Project](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-create-new-project) in [DevEco Studio User Guide](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-tools-overview).


- SDK version configuration:

  The ArkTS APIs provided by Extended Peripheral Management require SDK API version 16 or later.


- HDC configuration:

  HarmonyOS Device Connector (hdc) is a command-line tool for debugging. It can be used to interact with real devices or the Emulator on Windows, Linux, and macOS. For details about the configuration, see [hdc](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/hdc).

### Environment Setup

- Install [DevEco Studio](https://developer.huawei.com/consumer/en/download/deveco-studio) 4.1 or later on the PC.
- Update the public-SDK to API 16 or later<!--Del-->. For details about updating the SDK, see [Update Guide](../../../../faqs/full-sdk-switch-guide.md)<!--DelEnd-->.
- Install hdc on the PC. You can use it to interact with a real device or the Emulator on Windows, Linux, or macOS.
- Use a USB cable to connect a device to the PC.

## How to Develop

### Available APIs

The main functions provided by USB device management include querying the USB device list, controlling USB device permissions, and setting USB device configuration.

The open capabilities of the USB class are as follows. For details, see [@ohos.usbManager](../../../../reference/apis-basic-services-kit/js-apis-usbManager.md).

**Table 1** Open capability APIs of the USB class

| API                                               | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| hasRight(deviceName: string): boolean                         | Checks whether the application has the permission to access the device. |
| requestRight(deviceName: string): Promise&lt;boolean&gt;       | Requests the temporary permission for a software package to access the device. This API uses a promise to return the result asynchronously.                        |
| removeRight(deviceName: string): boolean | Removes the permission for a software package to access the device.|
| connectDevice(device: USBDevice): Readonly&lt;USBDevicePipe&gt; | Opens a USB device based on the device information returned by `getDevices()`.                |
| getDevices(): Array&lt;Readonly&lt;USBDevice&gt;&gt;          | Obtains the list of USB devices connected to the host. If no device is connected, an empty list is returned.                                            |
| setConfiguration(pipe: USBDevicePipe, config: USBConfiguration): number | Sets the device configuration.                                             |
| setInterface(pipe: USBDevicePipe, iface: USBInterface): number   | Sets the device interface.                                             |
| claimInterface(pipe: USBDevicePipe, iface: USBInterface, force ?: boolean): number | Registers a communication interface.                                                   |
| claimInterfaceExclusive(pipe: USBDevicePipe, iface: USBInterface, force?: boolean, onConflict?: Callback&lt;InterfaceConflictInfo&gt;): void | Declares a USB device interface exclusively.                                                   |
| closePipe(pipe: USBDevicePipe): number                         | Closes the device message control channel.                                       |
| releaseInterface(pipe: USBDevicePipe, iface: USBInterface): number | Releases the registered communication interface.                                                   |
| getFileDescriptor(pipe: USBDevicePipe): number                 | Obtains the file descriptor.                                             |
| getRawDescriptor(pipe: USBDevicePipe): Uint8Array              | Obtains the raw USB descriptor.                                        |

### How to Develop

A USB device can act as a host to connect to a device for device management. The development example is as follows:


1. Import the **usbManager** module.

   <!-- @[head](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/USB/USBManagerSample/entry/src/main/ets/pages/Index.ets) --> 
   
   ``` TypeScript
   // Import the usbManager module.
   import { usbManager, BusinessError } from '@kit.BasicServicesKit';
   import { JSON } from '@kit.ArkTS';
   ```

2. Obtain the USB device list.

   <!-- @[getDevices](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/USB/USBManagerSample/entry/src/main/ets/pages/Index.ets) --> 
   
   ``` TypeScript
   // Obtain the device list.
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
   // Request the operation permission for the specified device.
   usbManager.requestRight(deviceName).then((hasRight: boolean) => {
     console.info('usb device request right result: ' + hasRight);
     this.logInfo_ += '\n[INFO] usb device request right result: ' + JSON.stringify(hasRight);
   }).catch((error: BusinessError) => {
     console.error(`usb device request right failed : code=${error.code}, message=${error.message}`);
     this.logInfo_ += '\n[ERROR] usb device request right failed: code=' + error.code + ', message=' + error.message;
   });
   ```


4. Open the Device.

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


5. Release the USB interface, and close the USB device pipe.

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


### Samples

For USB management development, the following related examples are available for reference:

- [`DeviceManagementCollection`: Device Management Collection (ArkTS) (API9)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/DeviceManagement/DeviceManagementCollection)