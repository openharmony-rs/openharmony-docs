# messageToBytes

## Modules to Import

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## messageToBytes

```TypeScript
function messageToBytes(ndefMessage: NdefMessage): number[]
```

Converts an NDEF message to bytes.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ndefMessage | NdefMessage | Yes | NDEF message to convert. |

**Return value:**

| Type | Description |
| --- | --- |
| number[] | NDEF message in bytes, which consists of hexadecimal numbers ranging from **0x00** to **0xFF**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
