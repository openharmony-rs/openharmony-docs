# connectDevice

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## connectDevice

```TypeScript
function connectDevice(device: USBDevice): Readonly<USBDevicePipe>
```

Connects to the USB device based on the device information returned by **getDevices()**. After the API is called successfully, a device connection channel is established for subsequent data transmission and device control operations. After using the channel, you can call [usbManager.closePipe](arkts-basicservices-usbmanager-closepipe-f.md) to disable the USB connection channel. If the USB service is abnormal, **undefined** is returned. Check whether the return value of the API is empty.

1. Call [usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md) to obtain the USB device
information and the **USBDevice** value.
2. Call [usbManager.requestRight](arkts-basicservices-usbmanager-requestright-f.md) to request the device
access permission.

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| device | [USBDevice](arkts-basicservices-usbmanager-usbdevice-i.md) | Yes | USB device. The **busNum** and **devAddress** parameters obtained by [getDevices](arkts-basicservices-usbmanager-getdevices-f.md) are used to determine a USB device. Other attributes (such as **name** and **vendorId**) are not involved in device matching. |

**Return value:**

| Type | Description |
| --- | --- |
| Readonly&lt;[USBDevicePipe](arkts-basicservices-usbmanager-usbdevicepipe-i.md)&gt; | **USBDevicePipe** object, which is used in subsequent data transfer and device control. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |
| [14400001](../errorcode-usb.md#14400001-usb-device-connection-denied) | Access right denied. Call requestRight to get the USBDevicePipe access right first. |
| [14400004](../errorcode-usb.md#14400004-service-exception) |  |
| [14400012](../errorcode-usb.md#14400012-io-error) |  |

**Examples**

```TypeScript
async function connectDevice() {
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
  if (devicePipe == undefined) {
    console.error(`connect device failed`);
    return;
  }
  console.info(`devicePipe = ${devicePipe}`);
  usbManager.closePipe(devicePipe);
}
```
