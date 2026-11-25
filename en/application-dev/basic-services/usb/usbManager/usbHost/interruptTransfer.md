# USB Interrupt Transfer (ArkTS)

<!--Kit: Basic Services Kit-->
<!--Subsystem: USB-->
<!--Owner: @hwymlgitcode-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=153a2d56058c66354e11239cdb98b8313af7ef4e translatedAt=2026-11-06T12:09:30.635Z pushedAt=2026-11-09T12:37:59.265Z nl=1 -->

## When to Use

The interrupt transfer is mainly used by the host to receive a data packet sent by a device. The endpoint mode of a device determines whether the interface supports interrupt reading or interrupt writing. This mode is applicable to the transfer of a small number of scattered and unpredictable data input by devices such as the mouse, keyboard, and joystick. In addition, the endpoints of these devices support only interrupt reading.

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

| API                                                                                                             | Description                                                     |
|------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------|
| usbSubmitTransfer(transfer: UsbDataTransferParams): void                                                         | Submits isochronous, bulk, or interrupt transfer in an asynchronous manner.                                  |
| usbCancelTransfer(transfer: UsbDataTransferParams): void                                                         | Cancels the submitted asynchronous transfer.                                            |

For more details about the APIs for device management and transfer modes, see [@ohos.usbManager](../../../../reference/apis-basic-services-kit/js-apis-usbManager.md).

### How to Develop

Connect a host to a device and use the **usbSubmitTransfer** API to transfer data. The following steps describe how to implement an interrupt transfer:

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


4. Obtain the endpoint for reading data through interrupt transfer.

   <!-- @[interruptTransfer_getEndpoint](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/USB/USBManagerSample/entry/src/main/ets/pages/Index.ets) --> 
   
   ``` TypeScript
   if (this.deviceList_ === undefined || this.deviceList_.length === 0) {
     console.error('deviceList is empty');
     this.logInfo_ += '\n[ERROR] deviceList is empty';
     return;
   }
   let usbDevice: usbManager.USBDevice = this.deviceList_[0];
   try {
     if (!usbManager.hasRight(usbDevice.name)) {
       console.error('permission denied');
       this.logInfo_ += '\n[ERROR] permission denied';
       return;
     }
   } catch (error) {
     let errorObj: BusinessError = error as BusinessError;
     console.error(`USB hasRight failed: code=${errorObj.code}, message=${errorObj.message}`);
     this.logInfo_ += '\n[ERROR] USB hasRight failed: code=' + errorObj.code + ', message=' + errorObj.message;
     return;
   }
   
   let devicePipe: usbManager.USBDevicePipe;
   try {
     devicePipe = usbManager.connectDevice(usbDevice);
     if (!devicePipe) {
       console.error('connectDevice failed, pipe is undefined');
       this.logInfo_ += '\n[ERROR] connectDevice failed, pipe is undefined';
       return;
     }
   } catch (error) {
     let errorObj: BusinessError = error as BusinessError;
     console.error(`USB connectDevice failed: code=${errorObj.code}, message=${errorObj.message}`);
     this.logInfo_ += '\n[ERROR] USB connectDevice failed: code=' + errorObj.code + ', message=' + errorObj.message;
     return;
   }
   
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
         return value.direction === 128 && value.type === usbManager.UsbEndpointTransferType.TRANSFER_TYPE_INTERRUPT;
       })
       if (usbEndpoint !== undefined) {
         usbInterface = usbInterfaces[j];
         break;
       }
     }
   }
   if (usbEndpoint === undefined) {
     console.error(`get usbEndpoint error`)
     this.logInfo_ += '\n[ERROR] get usbEndpoint error';
     return;
   }
   if (usbInterface === undefined) {
     console.error(`get usbInterface error`)
     this.logInfo_ += '\n[ERROR] get usbInterface error';
     return;
   }
   ```


5. Connect to the device and register the communication interface.

    <!-- @[interruptTransfer_claimInterface](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/USB/USBManagerSample/entry/src/main/ets/pages/Index.ets) --> 
    
    ``` TypeScript
    // Register the communication interface. 0 is returned if the registration is successful, and another error code is returned if the registration fails.
    try {
      if (this.isExclusiveClaim_) {
        usbManager.claimInterfaceExclusive(devicePipe, usbInterface, true,
          (conflict: usbManager.InterfaceConflictInfo) => {
          // Asynchronous conflict notification when another application claims the same interface
          const conflictMsg = `busNum = ${conflict.busNum}, devAddr = ${conflict.devAddr}, ` +
            `interfaceId = ${conflict.interfaceId}`;
          console.info(`interface conflict: ${conflictMsg}`);
          this.logInfo_ += `\n[INFO] interface conflict: ${conflictMsg}`;
        });
        console.info('claimInterfaceExclusive success');
        this.logInfo_ += '\n[INFO] claimInterfaceExclusive success';
      } else {
        let claimInterfaceResult: number = usbManager.claimInterface(devicePipe, usbInterface, true);
        if (claimInterfaceResult !== 0) {
          console.error(`claimInterface error = ${claimInterfaceResult}`)
          this.logInfo_ += '\n[ERROR] claimInterface error = ' + JSON.stringify(claimInterfaceResult);
          return;
        }
      }
    } catch (error) {
      let errorObj: BusinessError = error as BusinessError;
      console.error(`USB claimInterface failed: code=${errorObj.code}, message=${errorObj.message}`);
      this.logInfo_ += '\n[ERROR] USB claimInterface failed: code=' + errorObj.code + ', message=' + errorObj.message;
      return;
    }
    ```


6. Perform data transfer.

   <!-- @[interruptTransfer_interruptTransfer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/USB/USBManagerSample/entry/src/main/ets/pages/Index.ets) --> 
   
   ``` TypeScript
   let transferParams: usbManager.UsbDataTransferParams | undefined = undefined;
   try {
     // The communication interface is successfully registered and performs data transfer.
     transferParams = {
       devPipe: devicePipe,
       flags: usbManager.UsbTransferFlags.USB_TRANSFER_SHORT_NOT_OK,
       endpoint: usbEndpoint.address,
       type: usbManager.UsbEndpointTransferType.TRANSFER_TYPE_INTERRUPT,
       timeout: 2000,
       length: 10,
       callback: (err: BusinessError , callBackData: usbManager.SubmitTransferCallback) => {
         if (err) {
           console.error(`transfer error: ${err}`);
           this.logInfo_ += '\n[ERROR] transfer error: ' + JSON.stringify(err);
           return;
         }
         console.info(`callBackData = ${callBackData}`);
         this.logInfo_ += '\n[INFO] callBackData = ' + JSON.stringify(callBackData);
         console.info(`transfer success,result = ${transferParams?.buffer}`);
         this.logInfo_ += '\n[INFO] transfer success,result = ' + JSON.stringify(transferParams?.buffer);
       },
       userData: new Uint8Array(10),
       buffer: new Uint8Array(10),
       isoPacketCount: 2,
     };
     usbManager.usbSubmitTransfer(transferParams);
     console.info('USB transfer request submitted.');
     this.logInfo_ += '\n[INFO] USB transfer request submitted.';
   } catch (error) {
     let errorObj: BusinessError = error as BusinessError;
     console.error(`USB transfer failed: code=${errorObj.code}, message=${errorObj.message}`);
     this.logInfo_ += '\n[ERROR] USB transfer failed: code=' + errorObj.code + ', message=' + errorObj.message;
   }
   ```


7. Cancel the data transfer, releases the interface, and closes the USB device pipe.

   <!-- @[interruptTransfer_release](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/USB/USBManagerSample/entry/src/main/ets/pages/Index.ets) --> 
   
   ``` TypeScript
   try {
     if (transferParams) {
       usbManager.usbCancelTransfer(transferParams);
     }
   } catch (error) {
     let errorObj: BusinessError = error as BusinessError;
     console.error(`usbCancelTransfer failed: code=${errorObj.code}, message=${errorObj.message}`);
     this.logInfo_ += '\n[ERROR] usbCancelTransfer failed: code=' + errorObj.code + ', message=' + errorObj.message;
   }
   try {
     usbManager.releaseInterface(devicePipe, usbInterface);
   } catch (error) {
     let errorObj: BusinessError = error as BusinessError;
     console.error(`releaseInterface failed: code=${errorObj.code}, message=${errorObj.message}`);
     this.logInfo_ += '\n[ERROR] releaseInterface failed: code=' + errorObj.code + ', message=' + errorObj.message;
   }
   try {
     usbManager.closePipe(devicePipe);
   } catch (error) {
     let errorObj: BusinessError = error as BusinessError;
     console.error(`closePipe failed: code=${errorObj.code}, message=${errorObj.message}`);
     this.logInfo_ += '\n[ERROR] closePipe failed: code=' + errorObj.code + ', message=' + errorObj.message;
   }
   ```

   
### Verification

1. Connect the host to a terminal device (such as a mouse or a keyboard) that supports interrupt transfer through a USB interface.
2. Execute the preceding code.
3. Search for the keyword **transfer success** in the log. If the keyword is found, the interrupt transfer interface is successfully called.
