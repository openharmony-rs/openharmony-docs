# NfcATag

Provides APIs to access NFC-A (ISO 14443-3A) properties and perform I/O operations on a tag. This class inherits from **[TagSession](arkts-connectivity-tagsession-tagsession-i.md)**.

**TagSession** is the base class of all NFC tag technologies. It provides common interfaces for establishing connections and transferring data. For more details, see [TagSession](arkts-connectivity-tagsession-tagsession-i.md).

For details about how to obtain an **NfcATag** object, see [NFC Tag Read/Write Development](../../../connectivity/nfc/nfc-tag-access-guide.md).

The following describes the unique APIs of **NfcATag**.

**Inheritance/Implementation:** NfcATag extends [TagSession](arkts-connectivity-tagsession-tagsession-i.md)

**Since:** 7

**System capability:** SystemCapability.Communication.NFC.Tag

## getAtqa

```TypeScript
getAtqa(): number[]
```

Obtains the ATQA value of this NFC-A tag.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Return value:**

| Type | Description |
| --- | --- |
| number[] | ATQA value obtained. Each number of the ATQA is a hexadecimal number ranging from **0x00** to **0xFF**. |

**Examples**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// Obtain the correct nfcA tag by using the tag.TagInfo API in @ohos.nfc.tag.
let atqa : number[] = nfcA.getAtqa();
console.info("nfcA atqa: " + atqa);
```

## getSak

```TypeScript
getSak(): number
```

Obtains the SAK value of this NFC-A tag.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Return value:**

| Type | Description |
| --- | --- |
| number | SAK value obtained. The SAK is a hexadecimal number ranging from **0x00** to **0xFF**. |

**Examples**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// Obtain the correct nfcA tag by using the tag.TagInfo API in @ohos.nfc.tag.
let sak : number = nfcA.getSak();
console.info("nfcA sak: " + sak);
```
