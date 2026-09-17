# resetUsbDevice

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## resetUsbDevice

```TypeScript
function resetUsbDevice(pipe: USBDevicePipe): boolean
```

Resets the USB device. This API is applicable to scenarios where the USB device needs to be restored due to communication exceptions. For example, the device needs to be reinitialized after a device firmware upgrade, the device status needs to be restored when it is abnormal, or the device status needs to be reset during debugging. After this API is successfully called, the device is reset to the initial state. The previously set configurations and interface settings are cleared, and the device needs to be reinitialized.

> **NOTE:** 
> 
> Previous configurations and interface settings will be reset after this API is called. Ensure
> that the related services have been completed before calling this API.

1. Call [usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md) to obtain the USB device list.
2. Call [usbManager.requestRight](arkts-basicservices-usbmanager-requestright-f.md) to request the device access
permission.
3. Call [usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md) to obtain **devicepipe** as an
input parameter.

**Since:** 20

**System capability:** SystemCapability.USB.USBManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pipe | [USBDevicePipe](arkts-basicservices-usbmanager-usbdevicepipe-i.md) | Yes | USB device pipe, which is used to determine the bus address and device address. You need to call [connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md) to obtain its value. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the device is reset successfully; returns **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [14400001](../errorcode-usb.md#14400001-usb-device-connection-denied) | Access right denied. Call requestRight to get the USBDevicePipe access right first. |
| [14400008](../errorcode-usb.md#14400008-no-device-disconnected) | No such device(it may have been disconnected). |
| [14400010](../errorcode-usb.md#14400010-unrecognized-error) | Other USB error. Possible causes:<br>1.Unrecognized discard error code. |
| [14400013](../errorcode-usb.md#14400013-parameter-validity-check-failed) | The USBDevicePipe validity check failed. Possible causes:<br>1.The input parameters fail the validation check.  <br>2.The call chain used to obtain the input parameters is not reasonable. |
| [14400004](../errorcode-usb.md#14400004-service-exception) |  |

**Examples**

```TypeScript
import {BusinessError} from '@kit.BasicServicesKit';
async function resetUsbDevice() {
  let devicesList: Array<usbManager.USBDevice> = usbManager.getDevices();
  if (!devicesList || devicesList.length == 0) {
    console.error(`device list is empty`);
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
  try {
    let ret: boolean = usbManager.resetUsbDevice(devicePipe);
    console.info(`resetUsbDevice  = ${ret}`);
  } catch (err) {
    console.error(`Failed to reset USB device. Code: ${err.code}, message: ${err.message}`);
  }
  usbManager.closePipe(devicePipe);
}
```
