# closeAccessory

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## closeAccessory

```TypeScript
function closeAccessory(accessoryHandle: USBAccessoryHandle): void
```

Closes the accessory file descriptor.

You need to call [usbManager.getAccessoryList](arkts-basicservices-usbmanager-getaccessorylist-f.md) to obtain the accessory list, and then call [usbManager.requestAccessoryRight](arkts-basicservices-usbmanager-requestaccessoryright-f.md) to request the permission to access the accessory. After the permission is granted, call [usbManager.openAccessory](arkts-basicservices-usbmanager-openaccessory-f.md) to obtain the accessory handle. The obtained [USBAccessoryHandle](arkts-basicservices-usbmanager-usbaccessoryhandle-i.md) is used as a parameter.

**Since:** 14

**System capability:** SystemCapability.USB.USBManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accessoryHandle | [USBAccessoryHandle](arkts-basicservices-usbmanager-usbaccessoryhandle-i.md) | Yes | USB accessory handle, which must be obtained through [openAccessory](arkts-basicservices-usbmanager-openaccessory-f.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified.  <br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |
| [14400004](../errorcode-usb.md#14400004-service-exception) | Service exception. Possible causes:<br>1. No accessory is plugged in. |

**Examples**

```TypeScript
async function closeAccessory() {
  try {
    let accList: usbManager.USBAccessory[] = usbManager.getAccessoryList();
    let flag = await usbManager.requestAccessoryRight(accList?.[0]);
    if (!flag) {
      return;
    }
    let handle = usbManager.openAccessory(accList?.[0]);
    usbManager.closeAccessory(handle);
    console.info(`closeAccessory success`);
  } catch (error) {
    console.error(`closeAccessory error ${error.code}, message is ${error.message}`);
  }
}
```
