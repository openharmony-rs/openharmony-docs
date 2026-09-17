# hasAccessoryRight

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## hasAccessoryRight

```TypeScript
function hasAccessoryRight(accessory: USBAccessory): boolean
```

Checks whether the app has the permission to access USB accessories.

You need to call [usbManager.getAccessoryList](arkts-basicservices-usbmanager-getaccessorylist-f.md) to obtain the accessory list and use [USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md) as a parameter.

**Since:** 14

**System capability:** SystemCapability.USB.USBManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accessory | [USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md) | Yes | USB accessory, which can be obtained through [getAccessoryList](arkts-basicservices-usbmanager-getaccessorylist-f.md). |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | The value **true** indicates that the app has the permission to access USB accessories; **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified.  <br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |
| [14401001](../errorcode-usb.md#14401001-target-usb-accessory-unmatched) | The target USBAccessory not matched. |
| [14400004](../errorcode-usb.md#14400004-service-exception) | Service exception. Possible causes:<br>1. No accessory is plugged in. |
| [14400005](../errorcode-usb.md#14400005-database-operation-exception) | Database operation exception. |

**Examples**

```TypeScript
try {
  let accList: usbManager.USBAccessory[] = usbManager.getAccessoryList();
  let flag = usbManager.hasAccessoryRight(accList?.[0]);
  console.info(`hasAccessoryRight success, ret:${flag}`);
} catch (error) {
  console.error(`hasAccessoryRight error ${error.code}, message is ${error.message}`);
}
```
