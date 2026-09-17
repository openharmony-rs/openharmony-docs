# requestRight

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## requestRight

```TypeScript
function requestRight(deviceName: string): Promise<boolean>
```

Requests the temporary permission for the app to access the device. This API uses a promise to return the result. System apps are granted the device access permission by default, and you do not need to call this API to request the permission.

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceName | string | Yes | Device name, which is the name of the USBDevice in the device list obtained by [getDevices](arkts-basicservices-usbmanager-getdevices-f.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise object that returns the result of the temporary permission request. The value true indicates that the temporary permission request is successful; the value false indicates that the temporary permission request fails. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |

**Examples**

```TypeScript
import {BusinessError} from '@kit.BasicServicesKit';
function requestRight() {
  let devicesList: Array<usbManager.USBDevice> = usbManager.getDevices();
  if (!devicesList || devicesList.length == 0) {
    console.info(`device list is empty`);
    return;
  }

  let device: usbManager.USBDevice = devicesList?.[0];
  usbManager.requestRight(device.name).then(ret => {
    console.info(`requestRight = ${ret}`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to request right. Code: ${error.code}, message: ${error.message}`);
  });
}
```
