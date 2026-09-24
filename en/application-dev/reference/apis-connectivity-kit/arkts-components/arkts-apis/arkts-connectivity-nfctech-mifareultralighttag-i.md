# MifareUltralightTag

```TypeScript
export interface MifareUltralightTag extends TagSession
```

Provides APIs to access MIFARE Ultralight properties and perform I/O operations on a tag. This class inherits from **TagSession**.

**TagSession** is the base class of all NFC tag technologies. It provides common interfaces for establishing connections and transferring data. For more details, see [TagSession](arkts-connectivity-tagsession-tagsession-i.md).

For details about how to obtain a **MifareUltralightTag** object, see [NFC Tag Read/Write Development](../../../connectivity/nfc/nfc-tag-access-guide.md).

The following describes the unique APIs of **MifareUltralightTag**.

**Inheritance/Implementation:** MifareUltralightTag extends [TagSession](arkts-connectivity-tagsession-tagsession-i.md)

**Since:** 9

**System capability:** SystemCapability.Communication.NFC.Tag

## getType

```TypeScript
getType(): tag.MifareUltralightType
```

Obtains the type of this MIFARE Ultralight tag.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Return value:**

| Type | Description |
| --- | --- |
| [tag.MifareUltralightType](arkts-connectivity-tag-mifareultralighttype-e.md) | Type of the MIFARE Ultralight tag obtained. |

**Examples**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// Obtain the correct MIFARE Ultralight tag by using the tag.TagInfo API in @ohos.nfc.tag.
let getType : tag.MifareUltralightType = mifareUltralight.getType();
console.info("mifareUltralight getType: " + getType);
```

## readMultiplePages

```TypeScript
readMultiplePages(pageIndex: number): Promise<number[]>
```

Reads four pages of data (16 bytes in total) from the tag. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pageIndex | number | Yes | Index of the first page to read. The page indexes start from **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number[]&gt; | Promise used to return the data read. |

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

// Obtain the correct MIFARE Ultralight tag by using the tag.TagInfo API in @ohos.nfc.tag.

function nfcTechDemo() {
    // Connect the tag if it has not been connected.
    if (!mifareUltralight.isTagConnected()) {
        if (!mifareUltralight.connectTag()) {
            console.error("mifareUltralight connectTag failed.");
            return;
        }
    }

    try {
        let pageIndex = 1; // Set a correct index.
        mifareUltralight.readMultiplePages(pageIndex).then((data : number[]) => {
            console.info("mifareUltralight readMultiplePages Promise data = " + data);
        }).catch((err : BusinessError)=> {
            console.error(`mifareUltralight readMultiplePages Promise Code: ${err.code}, message: ${err.message}`);
        });
    } catch (businessError) {
        console.error(`mifareUltralight readMultiplePages Promise catch businessError Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

<a id="readmultiplepages-1"></a>

## readMultiplePages

```TypeScript
readMultiplePages(pageIndex: number, callback: AsyncCallback<number[]>): void
```

Reads four pages of data (16 bytes in total) from the tag. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pageIndex | number | Yes | Index of the first page to read. The page indexes start from **0**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number[]&gt; | Yes | Callback used to return the data (16 bytes in size) read. |

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

// Obtain the correct MIFARE Ultralight tag by using the tag.TagInfo API in @ohos.nfc.tag.

function nfcTechDemo() {
    // Connect the tag if it has not been connected.
    if (!mifareUltralight.isTagConnected()) {
        if (!mifareUltralight.connectTag()) {
            console.error("mifareUltralight connectTag failed.");
            return;
        }
    }

    try {
        let pageIndex = 1; // Set a correct index.
        mifareUltralight.readMultiplePages(pageIndex, (err : BusinessError, data : number[])=> {
            if (err) {
                console.error(`mifareUltralight readMultiplePages AsyncCallback Code: ${err.code}, message: ${err.message}`);
            } else {
                console.info("mifareUltralight readMultiplePages AsyncCallback data: " + data);
            }
        });
    } catch (businessError) {
        console.error(`mifareUltralight readMultiplePages AsyncCallback catch Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

## writeSinglePage

```TypeScript
writeSinglePage(pageIndex: number, data: number[]): Promise<void>
```

Writes one page (4 bytes) of data to this tag. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pageIndex | number | Yes | Index of the page to write. The page indexes start from **0**. |
| data | number[] | Yes | 4-byte data to write. |

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

// Obtain the correct MIFARE Ultralight tag by using the tag.TagInfo API in @ohos.nfc.tag.

function nfcTechDemo() {
    // Connect the tag if it has not been connected.
    if (!mifareUltralight.isTagConnected()) {
        if (!mifareUltralight.connectTag()) {
            console.error("mifareUltralight connectTag failed.");
            return;
        }
    }

    try {
        let pageIndex = 1; // Set a correct index.
        let rawData = [0x01, 0x02, 0x03, 0x04]; // Set the correct data. The value must contain 4 bytes.
        mifareUltralight.writeSinglePage(pageIndex, rawData).then(() => {
            console.info("mifareUltralight writeSinglePage Promise success.");
        }).catch((err : BusinessError)=> {
            console.error(`mifareUltralight writeSinglePage Promise err Code: ${err.code}, message: ${err.message}`);
        });
    } catch (businessError) {
        console.error(`mifareUltralight writeSinglePage Promise catch Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

<a id="writesinglepage-1"></a>

## writeSinglePage

```TypeScript
writeSinglePage(pageIndex: number, data: number[], callback: AsyncCallback<void>): void
```

Writes one page (4 bytes) of data to this tag. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pageIndex | number | Yes | Index of the page to write. The page indexes start from **0**. |
| data | number[] | Yes | 4-byte data to write. |
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

// Obtain the correct MIFARE Ultralight tag by using the tag.TagInfo API in @ohos.nfc.tag.

function nfcTechDemo() {
    // Connect the tag if it has not been connected.
    if (!mifareUltralight.isTagConnected()) {
        if (!mifareUltralight.connectTag()) {
            console.error("mifareUltralight connectTag failed.");
            return;
        }
    }

    try {
        let pageIndex = 1; // Set a correct index.
        let rawData = [0x01, 0x02, 0x03, 0x04];  // Set the correct data. The value must contain 4 bytes.
        mifareUltralight.writeSinglePage(pageIndex, rawData, (err : BusinessError)=> {
        if (err) {
                console.error(`mifareUltralight writeSinglePage AsyncCallback Code: ${err.code}, message: ${err.message}`);
            } else {
                console.info("mifareUltralight writeSinglePage AsyncCallback success.");
            }
        });
    } catch (businessError) {
        console.error(`mifareUltralight writeSinglePage AsyncCallback catch Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```
