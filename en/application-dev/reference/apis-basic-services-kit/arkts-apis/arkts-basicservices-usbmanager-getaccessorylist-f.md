# getAccessoryList

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## getAccessoryList

```TypeScript
function getAccessoryList(): Array<Readonly<USBAccessory>>
```

Obtains the list of USB accessories connected to the host.

**Since:** 14

**System capability:** SystemCapability.USB.USBManager

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;Readonly&lt;[USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md)&gt;&gt; | List of USB accessories (read-only), including all available USB accessories. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |
| [14400004](../errorcode-usb.md#14400004-service-exception) | Service exception. Possible causes:<br>1. No accessory is plugged in. |

**Examples**

```TypeScript
try {
  let accList: usbManager.USBAccessory[] = usbManager.getAccessoryList();
  console.info(`getAccessoryList success, accList: ${JSON.stringify(accList)}`);
} catch (error) {
  console.error(`getAccessoryList error ${error.code}, message is ${error.message}`);
}
```
