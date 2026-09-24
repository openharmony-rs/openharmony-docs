# usbCancelTransfer

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## usbCancelTransfer

```TypeScript
function usbCancelTransfer(transfer: UsbDataTransferParams): void
```

Cancels an asynchronous USB data transfer request. This API can be used to proactively terminate an ongoing USB data transfer, for example, when a user manually cancels a long-time data transfer, when an error occurs after a transfer times out, or when the current transfer needs to be terminated during an app switch.

> **NOTE:** 
> 
> This API can be used to proactively cancel an unfinished USB data transfer request, such as
> the request submitted by usbSubmitTransfer.
> 
> Before calling this API, call the [usbManager.claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md)
> API to claim a communication interface.

**Since:** 18

**System capability:** SystemCapability.USB.USBManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| transfer | [UsbDataTransferParams](arkts-basicservices-usbmanager-usbdatatransferparams-i.md) | Yes | Parameter whose transfer is canceled. The value of this parameter is the same as that of the **transfer** parameter in the [usbManager.usbSubmitTransfer](arkts-basicservices-usbmanager-usbsubmittransfer-f.md) API. Before calling this API, call the [usbManager.claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md) API to claim a communication interface. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [14400001](../errorcode-usb.md#14400001-usb-device-connection-denied) | Access right denied. Call requestRight to get the USBDevicePipe access right first. |
| [14400008](../errorcode-usb.md#14400008-no-device-disconnected) | No such device (it may have been disconnected). |
| [14400010](../errorcode-usb.md#14400010-unrecognized-error) | Other USB error. Possible causes:<br>1.Unrecognized discard error code. |
| [14400011](../errorcode-usb.md#14400011-no-ongoing-transfer-found) | The transfer is not in progress, or is already complete or cancelled. |

**Examples**

> NOTE
> 
> The following sample code is only a basic process for calling the usbCancelTransfer API. When calling this API, you must comply with the protocol specifications of the target USB device to ensure proper data transfer and device compatibility. For details about the protocol requirements, see the technical documentation of the device.

```TypeScript
// Call usbManager.getDevices to obtain a data set. Then, obtain a USB device and its access permission.
// Pass the obtained USB device as a parameter to usbManager.connectDevice. Then, call usbManager.connectDevice to connect the USB device.
// Call usbManager.claimInterface to claim a USB interface. After that, call usbManager.bulkTransfer to start bulk transfer.
async function usbCancelTransfer() {
  let devicesList: Array<usbManager.USBDevice> = usbManager.getDevices();
  if (!devicesList || devicesList.length == 0) {
    console.info(`device list is empty`);
    return;
  }
  let device: usbManager.USBDevice = devicesList?.[0];
  let rightResult = await usbManager.requestRight(device.name);
  if (!rightResult) {
    console.error(`request right failed`);
    return;
  }
  let devicePipe: usbManager.USBDevicePipe = usbManager.connectDevice(device);
  if (devicePipe === undefined) {
    console.info(`connect device fail`);
    return;
  }
  // Obtain the endpoint address.
  let endpoint = device.configs?.[0]?.interfaces?.[0]?.endpoints.find((value) => {
    return value.direction === 0 && value.type === 2;
  });
  if (endpoint === undefined) {
    console.info(`invalid endpoint`);
    return;
  }
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
    transferParams.callback = (err, callbackData: usbManager.SubmitTransferCallback)=>{
      console.info('callbackData =' + JSON.stringify(callbackData));
    };
    usbManager.usbSubmitTransfer(transferParams);
    usbManager.usbCancelTransfer(transferParams);
    console.info('USB transfer request submitted.');
  } catch (error) {
    console.error(`USB transfer failed. Code: ${error.code}, message: ${error.message}`);
  }
  ret = usbManager.releaseInterface(devicePipe, interfaces);
  console.info(`releaseInterface = ${ret}`);
  usbManager.closePipe(devicePipe);
}
```
