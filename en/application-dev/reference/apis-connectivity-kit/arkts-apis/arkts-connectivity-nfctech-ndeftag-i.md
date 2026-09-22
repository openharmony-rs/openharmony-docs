# NdefTag

```TypeScript
export interface NdefTag extends TagSession
```

Provides APIs to access the tags in the NFC Data Exchange Format (NDEF). This class inherits from **TagSession**.

**TagSession** is the base class of all NFC tag technologies. It provides common interfaces for establishing connections and transferring data. For more details, see [TagSession](arkts-connectivity-tagsession-tagsession-i.md).

For details about how to obtain an **NdefTag** object, see [NFC Tag Read/Write Development](../../../connectivity/nfc/nfc-tag-access-guide.md).

The following describes the unique APIs of **NdefTag**.

**Inheritance/Implementation:** NdefTag extends [TagSession](arkts-connectivity-tagsession-tagsession-i.md)

**Since:** 9

**System capability:** SystemCapability.Communication.NFC.Tag

## canSetReadOnly

```TypeScript
canSetReadOnly(): boolean
```

Checks whether this NDEF tag can be set to read-only.

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the tag can be set to read-only; returns **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [3100201](../errorcode-nfc.md#3100201-tag-readwrite-error) | The tag running state is abnormal in the service. |

**Examples**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// Obtain the correct ndefTag tag by using the tag.TagInfo API in @ohos.nfc.tag.
let canSetReadOnly : boolean = ndefTag.canSetReadOnly();
console.info("ndef canSetReadOnly: " + canSetReadOnly);
```

## getNdefMessage

```TypeScript
getNdefMessage(): NdefMessage
```

Obtains the NDEF message from this NDEF tag.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Return value:**

| Type | Description |
| --- | --- |
| [NdefMessage](arkts-connectivity-nfctech-ndefmessage-i.md) | NDEF message created. For details, see *NFCForum-TS-NDEF_1.0*. |

**Examples**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// Obtain the correct ndefTag tag by using the tag.TagInfo API in @ohos.nfc.tag.
let ndefMessage : tag.NdefMessage = ndefTag.getNdefMessage();
console.info("ndef ndefMessage: " + ndefMessage);
```

## getNdefTagType

```TypeScript
getNdefTagType(): tag.NfcForumType
```

Obtains the NDEF tag type.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Return value:**

| Type | Description |
| --- | --- |
| [tag.NfcForumType](arkts-connectivity-tag-nfcforumtype-e.md) | NDEF tag type obtained. It can be NFC FORUM TYPE 1, 2, 3, or 4. |

**Examples**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// Obtain the correct ndefTag tag by using the tag.TagInfo API in @ohos.nfc.tag.
let ndefTagType : tag.NfcForumType = ndefTag.getNdefTagType();
console.info("ndef ndefTagType: " + ndefTagType);
```

## getNdefTagTypeString

```TypeScript
getNdefTagTypeString(type: tag.NfcForumType): string
```

Converts an NFC Forum Type tag to a string defined in the NFC Forum.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [tag.NfcForumType](arkts-connectivity-tag-nfcforumtype-e.md) | Yes | NDEF tag type. It can be NFC FORUM type 1, 2, 3, or 4. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Byte array obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

**Examples**

```TypeScript
import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the correct ndefTag tag by using the tag.TagInfo API in @ohos.nfc.tag.

try {
    let ndefTypeString : string = ndefTag.getNdefTagTypeString(tag.NfcForumType.NFC_FORUM_TYPE_1);
    console.info("ndef ndefTypeString: " + ndefTypeString);
} catch (businessError) {
    console.error(`ndef getNdefTagTypeString catch businessError Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
}
```

## isNdefWritable

```TypeScript
isNdefWritable(): boolean
```

Check whether this NDEF tag is writable. Before calling the data write API, check whether the write operation is supported.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Promise used to return the result. If the tag is writable, **true** is returned; otherwise, **false** is returned. |

**Examples**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// Obtain the correct ndefTag tag by using the tag.TagInfo API in @ohos.nfc.tag.
let isWritable : boolean = ndefTag.isNdefWritable();
console.info("ndef isNdefWritable: " + isWritable);
```

## readNdef

```TypeScript
readNdef(): Promise<NdefMessage>
```

Reads the NDEF message from the NDEF tag. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[NdefMessage](arkts-connectivity-nfctech-ndefmessage-i.md)&gt; | Promise used to return the **Message** object read from the NDEF tag. |

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

// Obtain the correct ndefTag tag by using the tag.TagInfo API in @ohos.nfc.tag.
function nfcTechDemo(){
    // Connect the tag if it has not been connected.
    if (!ndefTag.isTagConnected()) {
        if (!ndefTag.connectTag()) {
            console.error("ndefTag connectTag failed.");
            return;
        }
    }

    try {
        ndefTag.readNdef().then((ndefmessage : tag.NdefMessage) => {
            console.info("ndef readNdef Promise ndefmessage: " + ndefmessage);
        }).catch((err : BusinessError)=> {
            console.error(`ndef readNdef Promise err Code: ${err.code}, message: ${err.message}`);
        });
    } catch (businessError) {
        console.error(`ndef readNdef Promise catch businessError Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

```TypeScript
import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the correct ndefTag tag by using the tag.TagInfo API in @ohos.nfc.tag.
function nfcTechDemo() {
    // Connect the tag if it has not been connected.
    if (!ndefTag.isTagConnected()) {
        if (!ndefTag.connectTag()) {
            console.error("ndefTag connectTag failed.");
            return;
        }
    }

    try {
        ndefTag.readNdef((err : BusinessError, ndefmessage : tag.NdefMessage)=> {
            if (err) {
                console.error(`ndef readNdef AsyncCallback err Code: ${err.code}, message: ${err.message}`);
            } else {
                console.info("ndef readNdef AsyncCallback ndefmessage: " + ndefmessage);
            }
        });
    } catch (businessError) {
        console.error(`ndef readNdef AsyncCallback catch Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

<a id="readndef-1"></a>

## readNdef

```TypeScript
readNdef(callback: AsyncCallback<NdefMessage>): void
```

Reads the NDEF message from the NDEF tag. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[NdefMessage](arkts-connectivity-nfctech-ndefmessage-i.md)&gt; | Yes | Callback used to return the NDEF message read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [3100201](../errorcode-nfc.md#3100201-tag-readwrite-error) | The tag running state is abnormal in the service. |
| [3100204](../errorcode-nfc.md#3100204-nfc-chip-io-exception) | The Tag I/O operation failed.<br>**Applicable version:** 12 and later |

**Examples**

See [readNdef](#readndef)

## setReadOnly

```TypeScript
setReadOnly(): Promise<void>
```

Sets the NDEF tag to read-only. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

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

// Obtain the correct ndefTag tag by using the tag.TagInfo API in @ohos.nfc.tag.

function nfcTechDemo() {
    // Connect the tag if it has not been connected.
    if (!ndefTag.isTagConnected()) {
        if (!ndefTag.connectTag()) {
            console.error("ndefTag connectTag failed.");
            return;
        }
    }

    try {
        ndefTag.setReadOnly().then(() => {
            console.info("ndef setReadOnly Promise success.");
        }).catch((err : BusinessError)=> {
            console.error("ndef setReadOnly Promise err Code: ${err.code}, message: ${err.message}");
        });
    } catch (businessError) {
        console.error(`ndef setReadOnly Promise catch businessError Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

<a id="setreadonly-1"></a>

## setReadOnly

```TypeScript
setReadOnly(callback: AsyncCallback<void>): void
```

Sets the NDEF tag to read-only. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the operation result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [3100201](../errorcode-nfc.md#3100201-tag-readwrite-error) | The tag running state is abnormal in the service. |
| [3100204](../errorcode-nfc.md#3100204-nfc-chip-io-exception) | The Tag I/O operation failed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the correct ndefTag tag by using the tag.TagInfo API in @ohos.nfc.tag.

function nfcTechDemo() {
    // Connect the tag if it has not been connected.
    if (!ndefTag.isTagConnected()) {
        if (!ndefTag.connectTag()) {
            console.error("ndefTag connectTag failed.");
            return;
        }
    }

    try {
        ndefTag.setReadOnly((err : BusinessError)=> {
            if (err) {
                console.error(`ndef setReadOnly AsyncCallback err Code: ${err.code}, message: ${err.message}`);
            } else {
                console.info("ndef setReadOnly AsyncCallback success.");
            }
        });
    } catch (businessError) {
        console.error(`ndef setReadOnly AsyncCallback catch businessError Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

## writeNdef

```TypeScript
writeNdef(msg: NdefMessage): Promise<void>
```

Writes a **Message** object to the NDEF tag. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| msg | [NdefMessage](arkts-connectivity-nfctech-ndefmessage-i.md) | Yes | NDEF message to write. |

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

// Obtain the correct ndefTag tag by using the tag.TagInfo API in @ohos.nfc.tag.
// ndefMessage created from the raw data. For example:
let ndefMessage : tag.NdefMessage =
    tag.ndef.createNdefMessage([0xD1, 0x01, 0x03, 0x54, 0x4E, 0x46, 0x43]); // The NDEF data must be resolvable.
// Or create ndefMessage from tag.ndef.createNdefMessage (ndefRecords:NdefRecord[]).

function nfcTechDemo() {
    // Connect the tag if it has not been connected.
    if (!ndefTag.isTagConnected()) {
        if (!ndefTag.connectTag()) {
            console.error("ndefTag connectTag failed.");
            return;
        }
    }

    try {
        ndefTag.writeNdef(ndefMessage).then(() => {
            console.info("ndef writeNdef Promise success.");
        }).catch((err : BusinessError)=> {
            console.error(`ndef writeNdef err Code: ${err.code}, message: ${err.message}`);
        });
    } catch (businessError) {
        console.error(`ndef writeNdef Promise catch businessError Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

```TypeScript
import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the correct ndefTag tag by using the tag.TagInfo API in @ohos.nfc.tag.
// ndefMessage created from the raw data. For example:
let ndefMessage : tag.NdefMessage = 
    tag.ndef.createNdefMessage([0xD1, 0x01, 0x03, 0x54, 0x4E, 0x46, 0x43]); // The NDEF data must be resolvable.
// Or create ndefMessage from tag.ndef.createNdefMessage (ndefRecords:NdefRecord[]).

function nfcTechDemo() {
    // Connect the tag if it has not been connected.
    if (!ndefTag.isTagConnected()) {
        if (!ndefTag.connectTag()) {
            console.error("ndefTag connectTag failed.");
            return;
        }
    }

    try {
        ndefTag.writeNdef(ndefMessage, (err : BusinessError)=> {
            if (err) {
                console.error("ndef writeNdef AsyncCallback Code: ${err.code}, message: ${err.message}");
            } else {
                console.info("ndef writeNdef AsyncCallback success.");
            }
        }); 
    } catch (businessError) {
        console.error(`ndef writeNdef AsyncCallback catch businessError Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

<a id="writendef-1"></a>

## writeNdef

```TypeScript
writeNdef(msg: NdefMessage, callback: AsyncCallback<void>): void
```

Writes a **Message** object to the NDEF tag. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| msg | [NdefMessage](arkts-connectivity-nfctech-ndefmessage-i.md) | Yes | NDEF message to write. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the operation result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [3100201](../errorcode-nfc.md#3100201-tag-readwrite-error) | The tag running state is abnormal in the service. |
| [3100204](../errorcode-nfc.md#3100204-nfc-chip-io-exception) | The Tag I/O operation failed.<br>**Applicable version:** 12 and later |

**Examples**

See [writeNdef](#writendef)
