# NdefMessage

Provides methods for Message of NDEF.

**Since:** 9

**System capability:** SystemCapability.Communication.NFC.Tag

## getNdefRecords

```TypeScript
getNdefRecords(): tag.NdefRecord[]
```

Obtains all NDEF records.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Return value:**

| Type | Description |
| --- | --- |
| [tag.NdefRecord](arkts-connectivity-tag-ndefrecord-i.md)[] | List of NDEF records obtained. For details, see *NFCForum-TS-NDEF_1.0*. |

**Examples**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// Obtain ndefMessage from tag.ndef.createNdefMessage or ndefTag.getNdefMessage.
// let ndefMessage : tag.NdefMessage = tag.ndef.createNdefMessage(...);
// let ndefMessage : tag.NdefMessage = ndefTag.getNdefMessage();

let ndefRecords : tag.NdefRecord[] = ndefMessage.getNdefRecords();
console.info("ndef ndefRecords number: " + ndefRecords.length);
```
