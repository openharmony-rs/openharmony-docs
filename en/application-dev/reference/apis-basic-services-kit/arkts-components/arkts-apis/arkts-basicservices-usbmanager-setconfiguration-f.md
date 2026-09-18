# setConfiguration

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## setConfiguration

```TypeScript
function setConfiguration(pipe: USBDevicePipe, config: USBConfiguration): number
```

Sets the device configuration. This API can be used to switch the working mode of a multi-functional USB device. For example, it can be used to switch to the printing mode or scanning mode for a device combining the printer and scanner functions, or switch a device from a low-power configuration to a high-power configuration to enable all functions. After the API is successfully called, the device configuration is switched to the specified configuration. Subsequent data transfer and device operations are performed based on the new configuration.

> **NOTE:** 
> 
> Before calling this API, call the [usbManager.claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md)
> API to claim a communication interface.

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pipe | [USBDevicePipe](arkts-basicservices-usbmanager-usbdevicepipe-i.md) | Yes | USB device pipe, which is used to determine the bus address and device address. You need to call [connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md) to obtain its value. |
| config | [USBConfiguration](arkts-basicservices-usbmanager-usbconfiguration-i.md) | Yes | USB configuration. You can use [getDevices](arkts-basicservices-usbmanager-getdevices-f.md) to obtain device information and identify the configuration based on its **id**. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Result of the USB configuration. Returns **0** if the device configuration is set successfully; returns an error code otherwise. The error codes are as follows: <br>- 88080389: The service is not started. Possible causes: 1. No device is inserted; 2. The service exits abnormally. <br>- 88080486: The service is being initialized. Try again later. <br>- 88080488: No permission to access the device. Call [requestRight](arkts-basicservices-usbmanager-requestright-f.md) to request authorization first. <br>- -1: The driver is abnormal. Possible causes: 1. The device connection is unstable or the device is disconnected. 2. The USB driver fails to be loaded. 3. The kernel USB module is abnormal. <br>- -17: I/O failure. Possible causes: 1. The I/O operation fails due to abnormal device communication. 2. The data transfer is interrupted. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |

**Examples**

```TypeScript
async function setConfiguration() {
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
  let config: usbManager.USBConfiguration = device.configs?.[0];
  let ret: number = usbManager.setConfiguration(devicePipe, config);
  console.info(`setConfiguration = ${ret}`);
  usbManager.closePipe(devicePipe);
}
```
