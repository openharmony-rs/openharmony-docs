# makeMimeRecord

## Modules to Import

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## makeMimeRecord

```TypeScript
function makeMimeRecord(mimeType: string, mimeData: number[]): NdefRecord
```

Creates an NDEF record based on the specified MIME data and type.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mimeType | string | Yes | MIME type that complies with RFC rules, for example, **text/plain** or **image/jpeg**. |
| mimeData | number[] | Yes | MIME data, which consists of hexadecimal numbers ranging from **0x00** to **0xFF**. |

**Return value:**

| Type | Description |
| --- | --- |
| [NdefRecord](arkts-connectivity-tag-ndefrecord-i.md) | NDEF record created. For details, see *NFCForum-TS-NDEF_1.0*. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
