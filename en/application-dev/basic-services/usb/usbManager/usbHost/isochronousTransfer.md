# USB Isochronous Transfer

<!--Kit: Basic Services Kit-->
<!--Subsystem: USB-->
<!--Owner: @hwymlgitcode-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @w_Machine_cc-->

## When to Use

Isochronous transfer is a transfer mode in which data is transferred in a fixed time window through the USB protocol. This ensures the timing stability and low latency of data streams, but allows a small amount of data loss (such as video frame loss and audio noise). This transfer mode is applicable to scenarios that have high requirements on continuity and fault tolerance, such as USB headsets, USB speakers, and video conferencing devices.

## Preparing the Environment

### Environment Requirements

- Development tool and configuration:

  DevEco Studio, as the driver development tool, allows you to develop, debug, and package drivers. [Download and install](https://developer.huawei.com/consumer/en/download/) DevEco Studio and verify basic operations to ensure that it can function properly. For details, see [Creating a Project](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-create-new-project) in [DevEco Studio User Guide](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-tools-overview).


- SDK version configuration:

  The ArkTs APIs for peripheral management can be used only when the SDK is of API version 16 or later.


- HDC configuration:

  HarmonyOS Device Connector (hdc) is a command-line tool for debugging. It can be used to interact with real devices or the Emulators on Windows, Linux, and macOS. For details about the configuration, see [hdc](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/hdc).

### Environment Setup

- Install [DevEco Studio](https://developer.huawei.com/consumer/en/download/) 4.1 or later on the PC.
- Update the public SDK to API version 16 or later.<!--Del--> For details, see [Switching to Full SDK](../../../../faqs/full-sdk-switch-guide.md).<!--DelEnd-->
- Install hdc on the PC. You can use it to interact with a real device or the Emulator on Windows, Linux, or macOS.
- Use a USB cable to connect a device to the PC.

## How to Develop

### Available APIs

| API                                                                                                             | Description                                                     |
|------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------|
| usbSubmitTransfer(transfer: UsbDataTransferParams): void                                                         | Submits isochronous, bulk, or interrupt transfer in an asynchronous manner.                                  |
| usbCancelTransfer(transfer: UsbDataTransferParams): void                                                         | Cancels the submitted asynchronous transfer.                                            |

For details about the APIs of device management and transfer modes, see [@ohos.usbManager (USB Manager)](../../../../reference/apis-basic-services-kit/js-apis-usbManager.md).

### How to Develop

Connect a host to a device and use the **usbSubmitTransfer** API to transfer data. The following steps describe how to implement an interrupt transfer:

> **NOTE**
>
> The following sample code shows only a basic process. You should execute the code in a specific method. When calling this method, you must comply with device protocols to ensure proper data transfer and device compatibility.

1. Import modules.

   <!-- @[head](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/USB/USBManagerSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // Import the usbManager module.
   import { usbManager } from '@kit.BasicServicesKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { JSON } from '@kit.ArkTS';
   ```


2. Obtain the USB device list.

   <!-- @[getDevices](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/USB/USBManagerSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // Obtain the USB device list.
   let deviceList: usbManager.USBDevice[] = usbManager.getDevices();
   console.info(`deviceList: ${deviceList}`);
   this.logInfo_ += '\n[INFO] deviceList: ' + JSON.stringify(deviceList);
   if (deviceList === undefined || deviceList.length === 0) {
     console.error('deviceList is empty');
     this.logInfo_ += '\n[ERROR] deviceList is empty';
     return;
   }
   /*
   Example deviceList structure:
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
     console.error(`usb device request right failed : ${error}`);
     this.logInfo_ += '\n[ERROR] usb device request right failed: ' + JSON.stringify(error);
   });
   ```


4. Obtain the endpoint for reading data through interrupt transfer.

   <!-- @[isochronousTransfer_getEndpoint](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/USB/USBManagerSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   if (this.deviceList_ === undefined || this.deviceList_.length === 0) {
     console.error('deviceList_ is empty');
     this.logInfo_ += '\n[ERROR] deviceList_ is empty';
     return;
   }
   let usbDevice: usbManager.USBDevice = this.deviceList_[0];
   if (!usbManager.hasRight(usbDevice.name)) {
     console.error('permission denied');
     this.logInfo_ += '\n[ERROR] permission denied';
     return;
   }
   let devicePipe: usbManager.USBDevicePipe = usbManager.connectDevice(usbDevice);
   let usbConfigs: usbManager.USBConfiguration[] = usbDevice.configs;
   let usbInterfaces: usbManager.USBInterface[] = [];
   let usbInterface: usbManager.USBInterface | undefined = undefined;
   let usbEndpoints: usbManager.USBEndpoint[] = [];
   let usbEndpoint: usbManager.USBEndpoint | undefined = undefined;
   for (let i = 0; i < usbConfigs?.length; i++) {
     usbInterfaces = usbConfigs[i]?.interfaces;
     for (let j = 0; j < usbInterfaces?.length; j++) {
       usbEndpoints = usbInterfaces[j]?.endpoints;
       usbEndpoint = usbEndpoints?.find((value) => {
         // direction indicates the request direction. The value 0 indicates the written data, and the value 128 indicates the read data.
         return value.direction === 128 && value.type === usbManager.UsbEndpointTransferType.TRANSFER_TYPE_ISOCHRONOUS;
       })
       if (usbEndpoint !== undefined) {
         usbInterface = usbInterfaces[j];
         break;
       }
     }
   }
   if (usbEndpoint === undefined) {
     console.error(`get usbEndpoint error`);
     this.logInfo_ += '\n[ERROR] get usbEndpoint error';
     return;
   }
   ```

   
5. Connect to the device and register the communication interface.

   <!-- @[isochronousTransfer_claimInterface](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/USB/USBManagerSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // Register a communication interface. If the registration is successful, 0 is returned; otherwise, other error codes are returned.
   let claimInterfaceResult: number = usbManager.claimInterface(devicePipe, usbInterface, true);
   if (claimInterfaceResult !== 0) {
     console.error(`claimInterface error = ${claimInterfaceResult}`)
     this.logInfo_ += '\n[ERROR] claimInterface error = ' + JSON.stringify(claimInterfaceResult);
     return;
   }
   
   // When the transfer is of the isochronous type, you need to register a device interface. If the registration is successful, 0 is returned; otherwise, other error codes are returned.
   if (usbEndpoint.type === usbManager.UsbEndpointTransferType.TRANSFER_TYPE_ISOCHRONOUS) {
     let setInterfaceResult = usbManager.setInterface(devicePipe, usbInterface);
     if (setInterfaceResult !== 0) {
       console.error(`setInterfaceResult error = ${setInterfaceResult}`)
       this.logInfo_ += '\n[ERROR] setInterfaceResult error = ' + JSON.stringify(setInterfaceResult);
       return;
     }
   }
   ```


6. Perform data transfer.

   <!-- @[isochronousTransfer_isochronousTransfer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/USB/USBManagerSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   let transferParams: usbManager.UsbDataTransferParams | undefined = undefined;
   try {
     // The communication interface is successfully registered and performs data transfer.
     transferParams = {
       devPipe: devicePipe,
       flags: usbManager.UsbTransferFlags.USB_TRANSFER_SHORT_NOT_OK,
       endpoint: usbEndpoint.address,
       type: usbManager.UsbEndpointTransferType.TRANSFER_TYPE_ISOCHRONOUS,
       timeout: 2000,
       length: 10,
       callback: () => {
       },
       userData: new Uint8Array(10),
       buffer: new Uint8Array(10),
       isoPacketCount: 2,
     };
   
     transferParams.callback = (err: Error, callBackData: usbManager.SubmitTransferCallback) => {
       console.info(`callBackData = ${callBackData}`);
       this.logInfo_ += '\n[INFO] callBackData = ' + JSON.stringify(callBackData);
       console.info('transfer success,result = ' + transferParams?.buffer.toString());
       this.logInfo_ += '\n[INFO] transfer success,result = ' + transferParams?.buffer.toString();
     }
     usbManager.usbSubmitTransfer(transferParams);
     console.info('USB transfer request submitted.');
     this.logInfo_ += '\n[INFO] USB transfer request submitted.';
   } catch (error) {
     console.error(`USB transfer failed: ${error}`);
     this.logInfo_ += '\n[ERROR] USB transfer failed: ' + JSON.stringify(error);
   }
   ```


7. Cancel the data transfer, releases the interface, and closes the USB device pipe.

   <!-- @[isochronousTransfer_release](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/USB/USBManagerSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   try {
     usbManager.usbCancelTransfer(transferParams);
     usbManager.releaseInterface(devicePipe, usbInterface);
     usbManager.closePipe(devicePipe);
   } catch (error) {
     console.error(`release failed: ${error}`);
     this.logInfo_ += '\n[ERROR] release failed: ' + JSON.stringify(error);
   }
   ```


### Verification

1. Connect the host to a device (such as a USB headset) that supports isochronous transfer through a USB interface.
2. Execute the preceding code.
3. Search for the keyword **transfer success** in the log. If the keyword is found, the isochronous transfer interface is successfully called.
