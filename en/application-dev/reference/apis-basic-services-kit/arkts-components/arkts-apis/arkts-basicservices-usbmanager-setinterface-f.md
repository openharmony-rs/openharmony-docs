# setInterface

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## setInterface

```TypeScript
function setInterface(pipe: USBDevicePipe, iface: USBInterface): number
```

Sets a USB interface. After the API is successfully called, the specified alternate setting is switched for the interfaces, and the endpoint configuration changes accordingly to match the transmission type.

> **NOTE:** 
> 
> A USB interface may have multiple selection modes and supports dynamic switching. It is used
> to reset the endpoint to match the transmission type during data transmission.
> 
> Before calling this API, call the [usbManager.claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md)
> API to claim a communication interface.

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pipe | [USBDevicePipe](arkts-basicservices-usbmanager-usbdevicepipe-i.md) | Yes | USB device pipe, which is used to determine the bus address and device address. You need to call [connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md) to obtain its value. |
| iface | [USBInterface](arkts-basicservices-usbmanager-usbinterface-i.md) | Yes | USB interface. You can use [getDevices](arkts-basicservices-usbmanager-getdevices-f.md) to obtain device information and identify the USB interface based on its **id** and **alternateSetting**. **id** is the unique identifier of the interface. **alternateSetting** is used to switch between optional modes of the same interface. If **alternateSetting* is **0**, optional modes are not supported. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Result of the device interface setting. Returns **0** if the interface is set successfully; returns an error code otherwise. The error codes are as follows: <br>- 88080389: The service is not started. Possible causes: 1. No device is inserted; 2. The service exits abnormally. <br>- 88080486: The service is being initialized. Try again later. <br>- 88080488: No permission to access the device. Call [requestRight](arkts-basicservices-usbmanager-requestright-f.md) to request authorization first. <br>- -1: The driver is abnormal. Possible causes: 1. The device connection is unstable or the device is disconnected. 2. The USB driver fails to be loaded. 3. The kernel USB module is abnormal. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |

**Examples**

```TypeScript
async function setInterface() {
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
  let interfaces: usbManager.USBInterface = device.configs?.[0]?.interfaces?.[0];
  let ret: number = usbManager.claimInterface(devicePipe, interfaces);
  if (ret !== 0) {
    console.error(`claim interface failed`);
    usbManager.closePipe(devicePipe);
    return;
  }
  ret = usbManager.setInterface(devicePipe, interfaces);
  console.info(`setInterface = ${ret}`);
  ret = usbManager.releaseInterface(devicePipe, interfaces);
  console.info(`releaseInterface = ${ret}`);
  usbManager.closePipe(devicePipe);
}
```
