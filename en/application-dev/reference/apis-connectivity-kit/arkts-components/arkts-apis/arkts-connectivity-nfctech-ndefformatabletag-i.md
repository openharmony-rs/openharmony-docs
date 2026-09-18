# NdefFormatableTag

Provides APIs for formatting NDEF formattable tags. This class inherits from **TagSession**.

**TagSession** is the base class of all NFC tag technologies. It provides common interfaces for establishing connections and transferring data. For more details, see [TagSession](arkts-connectivity-tagsession-tagsession-i.md).

For details about how to obtain an **NdefFormatableTag** object, see [NFC Tag Read/Write Development](../../../connectivity/nfc/nfc-tag-access-guide.md).

The following describes the unique APIs of **NdefFormatableTag**.

**Inheritance/Implementation:** NdefFormatableTag extends [TagSession](arkts-connectivity-tagsession-tagsession-i.md)

**Since:** 9

**System capability:** SystemCapability.Communication.NFC.Tag

## format

```TypeScript
format(message: NdefMessage): Promise<void>
```

Formats this tag as an NDEF tag, and writes an NDEF message to it. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| message | [NdefMessage](arkts-connectivity-nfctech-ndefmessage-i.md) | Yes | NDEF message to write. If this parameter is **null**, the tag is formatted only (no data will be written). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [3100201](../errorcode-nfc.md#3100201-tag-readwrite-error) | The tag running state is abnormal in the service. |
| [3100204](../errorcode-nfc.md#3100204-nfc-chip-io-exception) | The tag I/O operation failed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the correct NDEF formattable tag by using the tag.TagInfo API in @ohos.nfc.tag.

function nfcTechDemo() {
    // Connect the tag if it has not been connected.
    if (!ndefFormatable.isTagConnected()) {
        if (!ndefFormatable.connectTag()) {
            console.error("ndefFormatable connectTag failed.");
            return;
        }
    }

    try {
        // ndefMessage created from the raw data. For example:
        let ndefMessage = tag.ndef.createNdefMessage([0xD1, 0x01, 0x03, 0x54, 0x4E, 0x46, 0x43]);  
        // The NDEF data must be resolvable.
        // Or create ndefMessage from tag.ndef.createNdefMessage (ndefRecords:NdefRecord[]).

        ndefFormatable.format(ndefMessage).then(() => {
            console.info("ndefFormatable format Promise success.");
        }).catch((err : BusinessError)=> {
            console.error(`ndefFormatable format Promise err Code: ${err.code}, message: ${err.message}`);
        });
    } catch (businessError) {
        console.error(`ndefFormatable format Promise catch businessError Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

```TypeScript
import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the correct NDEF formattable tag by using the tag.TagInfo API in @ohos.nfc.tag.

function nfcTechDemo() {
    // Connect the tag if it has not been connected.
    if (!ndefFormatable.isTagConnected()) {
        if (!ndefFormatable.connectTag()) {
            console.error("ndefFormatable connectTag failed.");
            return;
        }
    }

    try {
        // ndefMessage created from the raw data. For example:
        let ndefMessage = tag.ndef.createNdefMessage([0xD1, 0x01, 0x03, 0x54, 0x4E, 0x46, 0x43]);  // The NDEF data must be resolvable.
        // Or create ndefMessage from tag.ndef.createNdefMessage (ndefRecords:NdefRecord[]).

        ndefFormatable.format(ndefMessage, (err : BusinessError)=> {
            if (err) {
                console.error(`ndefFormatable format AsyncCallback Code: ${err.code}, message: ${err.message}`);
            } else {
                console.info("ndefFormatable format AsyncCallback success.");
            }
        });
    } catch (businessError) {
        console.error(`ndefFormatable format AsyncCallback catch Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

## format

```TypeScript
format(message: NdefMessage, callback: AsyncCallback<void>): void
```

Formats this tag as an NDEF tag, and writes an NDEF message to it. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| message | [NdefMessage](arkts-connectivity-nfctech-ndefmessage-i.md) | Yes | NDEF message to write when the formatting is successful. If this parameter is **null**, the tag is formatted only (no data will be written). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the operation result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [3100201](../errorcode-nfc.md#3100201-tag-readwrite-error) | The tag running state is abnormal in the service. |
| [3100204](../errorcode-nfc.md#3100204-nfc-chip-io-exception) | The Tag I/O operation failed.<br>**Applicable version:** 12 and later |

**Examples**

See [format](#format)

## formatReadOnly

```TypeScript
formatReadOnly(message: NdefMessage): Promise<void>
```

Formats this tag as an NDEF tag, writes an NDEF message to it, and then sets the tag to read-only. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| message | [NdefMessage](arkts-connectivity-nfctech-ndefmessage-i.md) | Yes | NDEF message to write. If this parameter is **null**, the tag is formatted only (no data will be written). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [3100201](../errorcode-nfc.md#3100201-tag-readwrite-error) | The tag running state is abnormal in the service. |
| [3100204](../errorcode-nfc.md#3100204-nfc-chip-io-exception) | The tag I/O operation failed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the correct NDEF formattable tag by using the tag.TagInfo API in @ohos.nfc.tag.

function nfcTechDemo() {
    // Connect the tag if it has not been connected.
    if (!ndefFormatable.isTagConnected()) {
        if (!ndefFormatable.connectTag()) {
            console.error("ndefFormatable connectTag failed.");
            return;
        }
    }

    try {
        // ndefMessage created from the raw data. For example:
        let ndefMessage = tag.ndef.createNdefMessage([0xD1, 0x01, 0x03, 0x54, 0x4E, 0x46, 0x43]);
        // The NDEF data must be resolvable.
        // Or create ndefMessage from tag.ndef.createNdefMessage (ndefRecords:NdefRecord[]).

        ndefFormatable.formatReadOnly(ndefMessage).then(() => {
            console.info("ndefFormatable formatReadOnly Promise success.");
        }).catch((err : BusinessError)=> {
            console.error(`ndefFormatable formatReadOnly Promise Code: ${err.code}, message: ${err.message}`);
        });
    } catch (businessError) {
        console.error(`ndefFormatable formatReadOnly Promise catch Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

```TypeScript
import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the correct NDEF formattable tag by using the tag.TagInfo API in @ohos.nfc.tag.

function nfcTechDemo() {
    // Connect the tag if it has not been connected.
    if (!ndefFormatable.isTagConnected()) {
        if (!ndefFormatable.connectTag()) {
            console.error("ndefFormatable connectTag failed.");
            return;
        }
    }

    try {
        // ndefMessage created from the raw data. For example:
        let ndefMessage = tag.ndef.createNdefMessage([0xD1, 0x01, 0x03, 0x54, 0x4E, 0x46, 0x43]);
        // The NDEF data must be resolvable.
        // Or create ndefMessage from tag.ndef.createNdefMessage (ndefRecords:NdefRecord[]).

        ndefFormatable.formatReadOnly(ndefMessage, (err : BusinessError)=> {
            if (err) {
                console.error(`ndefFormatable formatReadOnly AsyncCallback err Code: ${err.code}, message: ${err.message}`);
            } else {
                console.info("ndefFormatable formatReadOnly AsyncCallback success.");
            }
        });
    } catch (businessError) {
        console.error(`ndefFormatable formatReadOnly AsyncCallback catch Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

## formatReadOnly

```TypeScript
formatReadOnly(message: NdefMessage, callback: AsyncCallback<void>): void
```

Formats this tag as an NDEF tag, writes an NDEF message to the NDEF tag, and then sets the tag to read-only. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| message | [NdefMessage](arkts-connectivity-nfctech-ndefmessage-i.md) | Yes | NDEF message to write. If this parameter is **null**, the tag is formatted only (no data will be written). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the operation result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [3100201](../errorcode-nfc.md#3100201-tag-readwrite-error) | The tag running state is abnormal in the service. |
| [3100204](../errorcode-nfc.md#3100204-nfc-chip-io-exception) | The Tag I/O operation failed.<br>**Applicable version:** 12 and later |

**Examples**

See [formatReadOnly](#formatreadonly)
