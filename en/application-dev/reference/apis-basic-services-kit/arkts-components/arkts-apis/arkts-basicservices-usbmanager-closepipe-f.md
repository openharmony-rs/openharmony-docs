# closePipe

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## closePipe

```TypeScript
function closePipe(pipe: USBDevicePipe): number
```

Closes the USB device pipe.

1. Call [usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md) to obtain the device list;
2. Call [usbManager.requestRight](arkts-basicservices-usbmanager-requestright-f.md) to request the device access
permission.
3. Call [usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md) to obtain **devicepipe** as an
input parameter.

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pipe | [USBDevicePipe](arkts-basicservices-usbmanager-usbdevicepipe-i.md) | Yes | USB device pipe, which is used to determine the bus address and device address. You need to call [connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md) to obtain its value. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns **0** if the USB device pipe is closed successfully; returns an error code otherwise. The error codes are as follows:<br>- 22: The service is abnormal. Possible causes: 1. The USB service is abnormal. 2. The USB device pipe is abnormal. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |

**Examples**

```TypeScript
async function closePipe() {
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
  let ret: number = usbManager.closePipe(devicePipe);
  console.info(`closePipe = ${ret}`);
}
```
