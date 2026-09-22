# usbSubmitTransfer

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## usbSubmitTransfer

```TypeScript
function usbSubmitTransfer(transfer: UsbDataTransferParams): void
```

Submits an asynchronous transfer request. The result is returned immediately after this API is called. This API uses a callback to rerturn the actual read/write operation result. You can call [usbCancelTransfer](arkts-basicservices-usbmanager-usbcanceltransfer-f.md) to cancel an asynchronous transfer request.

> **NOTE:** 
> 
> This API uses an asynchronous callback to return the result.
> 
> Before calling this API, call the [usbManager.claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md)
> API to claim a communication interface.

**Since:** 18

**System capability:** SystemCapability.USB.USBManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| transfer | [UsbDataTransferParams](arkts-basicservices-usbmanager-usbdatatransferparams-i.md) | Yes | As a USB data transfer interface, it is required for a client to initiate a transfer request. Before calling this API, call the [usbManager.claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md) API to claim a communication interface. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [14400001](../errorcode-usb.md#14400001-usb-device-connection-denied) | Access right denied. Call requestRight to get the USBDevicePipe access right first. |
| [14400007](../errorcode-usb.md#14400007-resource-busy) | Resource busy. Possible causes:<br>1. The transfer has already been submitted.  <br>2. The interface is claimed by another program or driver. |
| [14400008](../errorcode-usb.md#14400008-no-device-disconnected) | No such device (it may have been disconnected). |
| [14400009](../errorcode-usb.md#14400009-insufficient-memory) | Insufficient memory. Possible causes:<br>1. Memory allocation failed. |
| [14400012](../errorcode-usb.md#14400012-io-error) | Transmission I/O error. |

**Examples**

> NOTE
> 
> The following sample code is only a basic process for calling the usbSubmitTransfer API. When calling this API, you must comply with the protocol specifications of the target USB device to ensure proper data transfer and device compatibility. For details about the protocol requirements, see the technical documentation of the device.

```TypeScript
// Call usbManager.getDevices to obtain a data set. Then, obtain a USB device and its access permission.
//  Pass the obtained USB device as a parameter to usbManager.connectDevice. Then, call usbManager.connectDevice to connect the USB device.
// Call usbManager.claimInterface to claim a USB interface. After that, call usbManager.bulkTransfer to start bulk transfer.
async function usbSubmitTransfer() {
  let devicesList: Array<usbManager.USBDevice> = usbManager.getDevices();
  if (!devicesList || devicesList.length == 0) {
    console.info(`device list is empty`);
    return;
  }
  let device: usbManager.USBDevice = devicesList?.[0];
  await usbManager.requestRight(device.name);
  if (!usbManager.hasRight(device.name)) {
    console.info(`request right fail`);
    return;
  }
  let devicePipe: usbManager.USBDevicePipe = usbManager.connectDevice(device);
  if (devicePipe == undefined) {
    console.error(`connect device failed`);
    return;
  }
  // Obtain the endpoint address.
  let endpoint = device.configs?.[0]?.interfaces?.[0]?.endpoints.find((value) => {
    return value.direction === 0 && value.type === 2;
  });
  // Claim control over the interface. If force is set to true, the interface control is forcibly claimed.
  let ret: number = usbManager.claimInterface(devicePipe, device.configs?.[0]?.interfaces?.[0], true);
  if (ret !== 0) {
    console.error(`claim interface failed`);
    usbManager.closePipe(devicePipe);
    return;
  }

  let transferParams: usbManager.UsbDataTransferParams = {
    devPipe: devicePipe,
    flags: usbManager.UsbTransferFlags.USB_TRANSFER_SHORT_NOT_OK,
    endpoint: 1,
    type: usbManager.UsbEndpointTransferType.TRANSFER_TYPE_BULK,
    timeout: 2000,
    length: 10, 
    callback: () => {},
    userData: new Uint8Array(10),
    buffer: new Uint8Array(10),
    isoPacketCount: 0,
  };
  try {
    transferParams.endpoint = endpoint?.address as number;
    transferParams.callback = (err, callbackData: usbManager.SubmitTransferCallback) => {
      let relIntfRet: number = usbManager.releaseInterface(devicePipe, interfaces);
      console.info(`releaseInterface = ${relIntfRet}`);
      usbManager.closePipe(devicePipe);
      if (err) {
        console.error(`USB transfer failed. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info('callbackData =' + JSON.stringify(callbackData));
    };
    usbManager.usbSubmitTransfer(transferParams); 
    console.info('USB transfer request submitted.');
  } catch (error) {
    console.error(`USB transfer failed. Code: ${error.code}, message: ${error.message}`);
  }
}
```
