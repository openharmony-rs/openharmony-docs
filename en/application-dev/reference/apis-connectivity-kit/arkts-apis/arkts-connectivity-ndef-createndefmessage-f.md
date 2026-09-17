# createNdefMessage

## Modules to Import

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## createNdefMessage

```TypeScript
function createNdefMessage(data: number[]): NdefMessage
```

Creates an NDEF message from raw byte data. The data must comply with the NDEF record format. Otherwise, the NDEF record list contained in the **NdefMessage** object will be empty.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | number[] | Yes | Raw byte data, which consists of hexadecimal numbers ranging from **0x00** to **0xFF**. The data must comply with the NDEF record format. |

**Return value:**

| Type | Description |
| --- | --- |
| NdefMessage | NDEF message created. For details, see *NFCForum-TS-NDEF_1.0*. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |


## createNdefMessage

```TypeScript
function createNdefMessage(ndefRecords: NdefRecord[]): NdefMessage
```

Creates an NDEF message from the NDEF records list.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ndefRecords | [NdefRecord](arkts-connectivity-tag-ndefrecord-i.md)[] | Yes | NDEF record list used to create the NDEF message. For details, see *NFCForum-TS-NDEF_1.0*. |

**Return value:**

| Type | Description |
| --- | --- |
| NdefMessage | NDEF message created. For details, see *NFCForum-TS-NDEF_1.0*. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
