# convertUuid

## Modules to Import

```TypeScript
import { access } from '@kit.ConnectivityKit';
```

## convertUuid

```TypeScript
function convertUuid(uuid: string): string
```

Convert 2-byte and 4-byte UUID strings to the 16-byte UUID string standard used in Bluetooth.

**Since:** 22

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uuid | string | Yes | 2-byte, 4-byte, 16-byte UUID string data. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Return the converted 16-byte UUID string. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let inputUuid: string = '1801';
    let convertedUuid: string = access.convertUuid(inputUuid);
    console.info("convertedUuid: " + convertedUuid);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
