# NfcBTag

Provides APIs to access NFC-B (ISO 14443-3B) properties and perform I/O operations on a tag. This class inherits from **TagSession**.

**TagSession** is the base class of all NFC tag technologies. It provides common interfaces for establishing connections and transferring data. For more details, see [TagSession](arkts-connectivity-tagsession-tagsession-i.md).

For details about how to obtain an **NfcBTag** object, see [NFC Tag Read/Write Development](../../../connectivity/nfc/nfc-tag-access-guide.md).

The following describes the unique APIs of **NfcBTag**.

**Inheritance/Implementation:** NfcBTag extends [TagSession](arkts-connectivity-tagsession-tagsession-i.md)

**Since:** 7

**System capability:** SystemCapability.Communication.NFC.Tag

## getRespAppData

```TypeScript
getRespAppData(): number[]
```

Obtains the application data of this NFC-B tag.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Return value:**

| Type | Description |
| --- | --- |
| number[] | Application data obtained, which consists of hexadecimal numbers ranging from **0x00** to **0xFF**. |

**Examples**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// Obtain the correct nfcB tag by using the tag.TagInfo API in @ohos.nfc.tag.
let respAppData : number[] = nfcB.getRespAppData();
console.info("nfcB respAppData: " + respAppData);
```

## getRespProtocol

```TypeScript
getRespProtocol(): number[]
```

Obtains the protocol information of this NFC-B tag.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Return value:**

| Type | Description |
| --- | --- |
| number[] | Protocol information obtained, which consists of hexadecimal numbers ranging from **0x00** to **0xFF**. |

**Examples**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// Obtain the correct nfcB tag by using the tag.TagInfo API in @ohos.nfc.tag.
let respProtocol : number[] = nfcB.getRespProtocol();
console.info("nfcB respProtocol: " + respProtocol);
```
