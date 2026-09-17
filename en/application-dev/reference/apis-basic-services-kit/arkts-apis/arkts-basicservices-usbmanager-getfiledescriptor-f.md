# getFileDescriptor

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## getFileDescriptor

```TypeScript
function getFileDescriptor(pipe: USBDevicePipe): number
```

Obtains a file descriptor. If the USB service is abnormal, an error code may be returned. Check whether the return value of the API is empty or check the error code.

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pipe | [USBDevicePipe](arkts-basicservices-usbmanager-usbdevicepipe-i.md) | Yes | USB device pipe, which is used to determine the bus address and device address. You need to call [connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md) to obtain its value. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the file descriptor corresponding to the device. If the operation fails, one of the following error codes is returned: <br>- 88080486: The service is being initialized. Try again later. <br>- 88080488: No permission to access the device. Call [requestRight](arkts-basicservices-usbmanager-requestright-f.md) to request authorization first. <br>- -1: The driver is abnormal. Possible causes: 1. The device connection is unstable or the device is disconnected. 2. The USB driver fails to be loaded. 3. The kernel USB module is abnormal. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |

**Examples**

```TypeScript
async function getFileDescriptor() {
  let devicesList: Array<usbManager.USBDevice> = usbManager.getDevices();
  if (!devicesList || devicesList.length == 0) {
    console.info(`device list is empty`);
    return;
  }

  let rightResult = await usbManager.requestRight(devicesList?.[0]?.name);
  if (!rightResult) {
    console.error(`request right failed`);
    return;
  }
  let devicePipe: usbManager.USBDevicePipe = usbManager.connectDevice(devicesList?.[0]);
  if (devicePipe == undefined) {
    console.error(`connect device failed`);
    return;
  }
  let ret: number = usbManager.getFileDescriptor(devicePipe);
  console.info(`getFileDescriptor = ${ret}`);
  let closeRet: number = usbManager.closePipe(devicePipe);
  console.info(`closePipe = ${closeRet}`);
}
```
