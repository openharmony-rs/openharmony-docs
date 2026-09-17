# openAccessory

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## openAccessory

```TypeScript
function openAccessory(accessory: USBAccessory): USBAccessoryHandle
```

Obtains the accessory handle and opens the accessory file descriptor. Then, the host can communicate with the accessory through the **read** and **write** APIs provided by Core File Kit. After using the accessory, call [closeAccessory](arkts-basicservices-usbmanager-closeaccessory-f.md) to close the file descriptor.

You need to call [usbManager.getAccessoryList](arkts-basicservices-usbmanager-getaccessorylist-f.md) to obtain the accessory list and use [USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md) as a parameter. Before calling this API, call [usbManager.requestAccessoryRight](arkts-basicservices-usbmanager-requestaccessoryright-f.md) to request the permission to access the accessory. This API can be called only after the permission is granted (**true** is returned).

**Since:** 14

**System capability:** SystemCapability.USB.USBManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accessory | [USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md) | Yes | USB accessory, which needs to be obtained through [getAccessoryList](arkts-basicservices-usbmanager-getaccessorylist-f.md). |

**Return value:**

| Type | Description |
| --- | --- |
| [USBAccessoryHandle](arkts-basicservices-usbmanager-usbaccessoryhandle-i.md) | Describes the USB accessory handle. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified.  <br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |
| [14400001](../errorcode-usb.md#14400001-usb-device-connection-denied) | Access right denied. Call requestRight to get the USBDevicePipe access right first. |
| [14400004](../errorcode-usb.md#14400004-service-exception) | Service exception. Possible causes:<br>1. No accessory is plugged in. |
| [14401001](../errorcode-usb.md#14401001-target-usb-accessory-unmatched) | The target USBAccessory not matched. |
| [14401002](../errorcode-usb.md#14401002-failed-to-open-the-native-accessory-node) | Failed to open the native accessory node. |
| [14401003](../errorcode-usb.md#14401003-accessory-opened-repeatedly) | Cannot reopen the accessory. |

**Examples**

```TypeScript
import { fileIo } from '@kit.CoreFileKit';
async function openAccessory() {
  try {
    let accList: usbManager.USBAccessory[] = usbManager.getAccessoryList();
    let flag = await usbManager.requestAccessoryRight(accList?.[0]);
    if (!flag) {
      return;
    }
    let handle = usbManager.openAccessory(accList?.[0]);
    console.info(`openAccessory success`);
    let arrayBuffer = new ArrayBuffer(4096);
    let readLength = fileIo.readSync(handle.accessoryFd, arrayBuffer, {offset: 0, length: 4096});
    console.info('readSync ret: ' + readLength.toString(10));
    usbManager.closeAccessory(handle);
  } catch (error) {
    console.error(`openAccessory error ${error.code}, message is ${error.message}`);
  }
}
```
