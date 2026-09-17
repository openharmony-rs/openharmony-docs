# BarcodeTag

Provides the capability of reading barcode label attributes and accessing I/O operations. It is inherited from **TagSession**.

**TagSession** is the base class of all NFC tag technologies. It provides common interfaces for establishing connections and transferring data. For more details, see [TagSession](arkts-connectivity-tagsession-tagsession-i.md).

For details about how to obtain a **BarcodeTag** object, see [NFC Tag Read/Write Development](../../../connectivity/nfc/nfc-tag-access-guide.md).

The following describes the unique APIs of **BarcodeTag**.

**Inheritance/Implementation:** BarcodeTag extends [TagSession](arkts-connectivity-tagsession-tagsession-i.md)

**Since:** 18

**System capability:** SystemCapability.Communication.NFC.Tag

## getBarcode

```TypeScript
getBarcode(): Promise<ArrayBuffer>
```

Obtains a complete barcode tag. This API uses a promise to return the result.

**Since:** 18

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Communication.NFC.Tag

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;ArrayBuffer&gt; | Promise used to return the barcode tag read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [3100201](../errorcode-nfc.md#3100201-tag-readwrite-error) | The tag running state is abnormal in the service. |
| [3100204](../errorcode-nfc.md#3100204-nfc-chip-io-exception) | The tag I/O operation failed. |
