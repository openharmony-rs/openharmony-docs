# MifareClassicTag

```TypeScript
export interface MifareClassicTag extends TagSession
```

Provides APIs to access MIFARE Classic properties and perform I/O operations on a tag. This class inherits from [TagSession](arkts-connectivity-tagsession-tagsession-i.md).

**TagSession** is the base class of all NFC tag technologies. It provides common interfaces for establishing connections and transferring data. For more details, see [TagSession](arkts-connectivity-tagsession-tagsession-i.md).

For details about how to obtain a **MifareClassicTag** object, see [NFC Tag Read/Write Development](../../../connectivity/nfc/nfc-tag-access-guide.md).

The following describes the unique APIs of **MifareClassicTag**.

**Inheritance/Implementation:** MifareClassicTag extends [TagSession](arkts-connectivity-tagsession-tagsession-i.md)

**Since:** 9

**System capability:** SystemCapability.Communication.NFC.Tag

## authenticateSector

```TypeScript
authenticateSector(sectorIndex: number, key: number[], isKeyA: boolean): Promise<void>
```

Authenticates a sector using a key. The sector can be accessed only after the authentication is successful. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sectorIndex | number | Yes | Index of the sector to authenticate. The sector indexes start from **0**. |
| key | number[] | Yes | Key (6 bytes) used for sector authentication. |
| isKeyA | boolean | Yes | Whether the key is key A. The value **true** indicates key A, and **false** indicates key B. |

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

// Obtain the correct MIFARE Classic tag by using the tag.TagInfo API in @ohos.nfc.tag.

function nfcTechDemo() {
    // Connect the tag if it has not been connected.
    if (!mifareClassic.isTagConnected()) {
        if (!mifareClassic.connectTag()) {
            console.error("mifareClassic connectTag failed.");
            return;
        }
    }

    try {
        let sectorIndex = 1; // Set a correct index.
        let key = [0x01, 0x02, 0x03, 0x04, 0x05, 0x06];  // Set a correct key. The value must contain six bytes. 
        mifareClassic.authenticateSector(sectorIndex, key, true).then(() => {
            console.info("mifareClassic authenticateSector Promise success.");
        }).catch((err : BusinessError)=> {
            console.error("mifareClassic authenticateSector Promise errCode: ${err.code}, " + "message: ${err.message}");
        });
    } catch (businessError) {
        console.error(`mifareClassic authenticateSector Promise catch businessError Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

<a id="authenticatesector-1"></a>

## authenticateSector

```TypeScript
authenticateSector(sectorIndex: number, key: number[], isKeyA: boolean, callback: AsyncCallback<void>): void
```

Authenticates a sector using a key. The sector can be accessed only after the authentication is successful. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sectorIndex | number | Yes | Index of the sector to authenticate. The sector indexes start from **0**. |
| key | number[] | Yes | Key (6 bytes) used for sector authentication. |
| isKeyA | boolean | Yes | Whether the key is key A. The value **true** indicates key A, and **false** indicates key B. |
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

// Obtain the correct MIFARE Classic tag by using the tag.TagInfo API in @ohos.nfc.tag.

function nfcTechDemo() {
    // Connect the tag if it has not been connected.
    if (!mifareClassic.isTagConnected()) {
        if (!mifareClassic.connectTag()) {
            console.error("mifareClassic connectTag failed.");
            return;
        }
    }

    try {
        let sectorIndex = 1; // Set a correct index.
        let key = [0x01, 0x02, 0x03, 0x04, 0x05, 0x06];  // Set a correct key. The value must contain six bytes. 
        mifareClassic.authenticateSector(sectorIndex, key, true, (err : BusinessError)=> {
            if (err) {
                console.error(`mifareClassic authenticateSector AsyncCallback errCode: ${err.code}, message: ${err.message}`);
            } else {
                console.info("mifareClassic authenticateSector AsyncCallback success.");
            }
        });
    } catch (businessError) {
        console.error(`mifareClassic authenticateSector AsyncCallback catch Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

## decrementBlock

```TypeScript
decrementBlock(blockIndex: number, value: number): Promise<void>
```

Decrements a block with the specified value and saves the result in a buffer for internal transmission. This API uses a promise to return the result. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| blockIndex | number | Yes | Index of the block to increment. The block indexes start from **0**. |
| value | number | Yes | Block data to decrement. The value cannot be a negative number. |

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

// Obtain the correct MIFARE Classic tag by using the tag.TagInfo API in @ohos.nfc.tag.

function nfcTechDemo() {
    // Connect the tag if it has not been connected.
    if (!mifareClassic.isTagConnected()) {
        if (!mifareClassic.connectTag()) {
            console.error("mifareClassic connectTag failed.");
            return;
        }
    }

    try {
        let blockIndex = 1; // Set a correct index.
        let value = 0x20; // Set the correct data.
        mifareClassic.decrementBlock(blockIndex, value).then(() => {
            console.info("mifareClassic decrementBlock Promise success.");
        }).catch((err : BusinessError)=> {
            console.error("mifareClassic decrementBlock Promise errCode: ${err.code}, message: ${err.message}");
        });
    } catch (businessError) {
        console.error(`mifareClassic decrementBlock Promise catch businessError: Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

<a id="decrementblock-1"></a>

## decrementBlock

```TypeScript
decrementBlock(blockIndex: number, value: number, callback: AsyncCallback<void>): void
```

Decrements a block with the specified value. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| blockIndex | number | Yes | Index of the block to increment. The block indexes start from **0**. |
| value | number | Yes | Block data to decrement. The value cannot be a negative number. |
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

// Obtain the correct MIFARE Classic tag by using the tag.TagInfo API in @ohos.nfc.tag.

function nfcTechDemo() {
    // Connect the tag if it has not been connected.
    if (!mifareClassic.isTagConnected()) {
        if (!mifareClassic.connectTag()) {
            console.error("mifareClassic connectTag failed.");
            return;
        }
    }

    try {
        let blockIndex = 1; // Set a correct index.
        let value = 0x20; // Set the correct data.
        mifareClassic.decrementBlock(blockIndex, value, (err : BusinessError)=> {
            if (err) {
                console.error("mifareClassic decrementBlock AsyncCallback errCode:" + 
                  "${err.code}, message: ${err.message}");
            } else {
                console.info("mifareClassic decrementBlock AsyncCallback success.");
            }
        });
    } catch (businessError) {
        console.error(`mifareClassic decrementBlock AsyncCallback catch Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

## getBlockCountInSector

```TypeScript
getBlockCountInSector(sectorIndex: number): number
```

Obtains the number of blocks in a sector.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sectorIndex | number | Yes | Index of the target sector. The sector indexes start from **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of blocks obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

**Examples**

```TypeScript
import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the correct MIFARE Classic tag by using the tag.TagInfo API in @ohos.nfc.tag.

try {
    let sectorIndex = 1; // Set a correct index.
    let blockCnt : number = mifareClassic.getBlockCountInSector(sectorIndex);
    console.info("mifareClassic blockCnt: " + blockCnt);
} catch (businessError) {
    console.error(`mifareClassic getBlockCountInSector catch businessError Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
}
```

## getBlockIndex

```TypeScript
getBlockIndex(sectorIndex: number): number
```

Obtains the index of the first block in a sector.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sectorIndex | number | Yes | Index of the target sector. The sector indexes start from **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Index of the first block obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

**Examples**

```TypeScript
import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the correct MIFARE Classic tag by using the tag.TagInfo API in @ohos.nfc.tag.

try {
    let sectorIndex = 1; // Set a correct index.
    let blockIndex : number = mifareClassic.getBlockIndex(sectorIndex);
    console.info("mifareClassic blockIndex: " + blockIndex);
} catch (businessError) {
    console.error(`mifareClassic getBlockIndex catch businessError Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
}
```

## getSectorCount

```TypeScript
getSectorCount(): number
```

Obtains the number of sectors in this MIFARE Classic tag.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of sectors obtained. |

**Examples**

```TypeScript
import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the correct MIFARE Classic tag by using the tag.TagInfo API in @ohos.nfc.tag.
let sectorCount : number = mifareClassic.getSectorCount();
console.info("mifareClassic sectorCount: " + sectorCount);
```

## getSectorIndex

```TypeScript
getSectorIndex(blockIndex: number): number
```

Obtains the index of the sector that holds the specified block.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| blockIndex | number | Yes | Index of the block. The block indexes start from **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Index of the sector obtained. The sector indexes start from **0**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

**Examples**

```TypeScript
import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the correct MIFARE Classic tag by using the tag.TagInfo API in @ohos.nfc.tag.

try {
    let blockIndex = 1; // Set a correct index.
    let sectorIndex : number = mifareClassic.getSectorIndex(blockIndex);
    console.info("mifareClassic sectorIndex: " + sectorIndex);
} catch (businessError) {
    console.error(`mifareClassic getSectorIndex catch businessError Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
}
```

## getTagSize

```TypeScript
getTagSize(): number
```

Obtains the size of this tag. For details, see [MifareClassicSize](arkts-connectivity-tag-mifareclassicsize-e.md).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Return value:**

| Type | Description |
| --- | --- |
| number | Tag size obtained, in bytes. For details, see [MifareClassicSize](arkts-connectivity-tag-mifareclassicsize-e.md). |

**Examples**

```TypeScript
import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the correct MIFARE Classic tag by using the tag.TagInfo API in @ohos.nfc.tag.
let tagSize : number = mifareClassic.getTagSize();
console.info("mifareClassic tagSize: " + tagSize);
```

## getType

```TypeScript
getType(): tag.MifareClassicType
```

Obtains the type of this MIFARE Classic tag.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Return value:**

| Type | Description |
| --- | --- |
| [tag.MifareClassicType](arkts-connectivity-tag-mifareclassictype-e.md) | Type of the MIFARE Classic tag obtained. |

**Examples**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// Obtain the correct MIFARE Classic tag by using the tag.TagInfo API in @ohos.nfc.tag.
let getType : tag.MifareClassicType = mifareClassic.getType();
console.info("mifareClassic getType: " + getType);
```

## incrementBlock

```TypeScript
incrementBlock(blockIndex: number, value: number): Promise<void>
```

Increments a block with the specified value and saves the result in a buffer for internal transmission. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| blockIndex | number | Yes | Index of the block to increment. The block indexes start from **0**. |
| value | number | Yes | Block data to increment. The value cannot be a negative number. |

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

// Obtain the correct MIFARE Classic tag by using the tag.TagInfo API in @ohos.nfc.tag.

function nfcTechDemo() {
    // Connect the tag if it has not been connected.
    if (!mifareClassic.isTagConnected()) {
        if (!mifareClassic.connectTag()) {
            console.error("mifareClassic connectTag failed.");
            return;
        }
    }

    try {
        let blockIndex = 1; // Set a correct index.
        let value = 0x20; // Set the correct data.
        mifareClassic.incrementBlock(blockIndex, value).then(() => {
            console.info("mifareClassic incrementBlock Promise success.");
        }).catch((err : BusinessError)=> {
            console.error(`mifareClassic incrementBlock Promise err Code: ${err.code}, message: ${err.message}`);
        });
    } catch (businessError) {
        console.error(`mifareClassic incrementBlock Promise catch Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

<a id="incrementblock-1"></a>

## incrementBlock

```TypeScript
incrementBlock(blockIndex: number, value: number, callback: AsyncCallback<void>): void
```

Increments a block with the specified value and saves the result in a buffer for internal transmission. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| blockIndex | number | Yes | Index of the block to increment. The block indexes start from **0**. |
| value | number | Yes | Block data to increment. The value cannot be a negative number. |
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

// Obtain the correct MIFARE Classic tag by using the tag.TagInfo API in @ohos.nfc.tag.

function nfcTechDemo() {
    // Connect the tag if it has not been connected.
    if (!mifareClassic.isTagConnected()) {
        if (!mifareClassic.connectTag()) {
            console.error("mifareClassic connectTag failed.");
            return;
        }
    }

    try {
        let blockIndex = 1; // Set a correct index.
        let value = 0x20; // Set the correct data.
        mifareClassic.incrementBlock(blockIndex, value, (err : BusinessError)=> {
            if (err) {
                console.error(`mifareClassic incrementBlock AsyncCallback err Code: ${err.code}, message: ${err.message}`);
            } else {
                console.info("mifareClassic incrementBlock AsyncCallback success.");
            }
        });
    } catch (businessError) {
        console.error(`mifareClassic incrementBlock AsyncCallback catch businessError Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

## isEmulatedTag

```TypeScript
isEmulatedTag(): boolean
```

Checks whether it is an emulated tag.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the tag is an emulated tag; returns **false** otherwise. |

**Examples**

```TypeScript
import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the correct MIFARE Classic tag by using the tag.TagInfo API in @ohos.nfc.tag.
let isEmulatedTag : boolean = mifareClassic.isEmulatedTag();
console.info("mifareClassic isEmulatedTag: " + isEmulatedTag);
```

## readSingleBlock

```TypeScript
readSingleBlock(blockIndex: number): Promise<number[]>
```

Reads a block (16 bytes) on this tag. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| blockIndex | number | Yes | Index of the block to read. The block indexes start from **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number[]&gt; | Promise used to return the read block data. |

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

// Obtain the correct MIFARE Classic tag by using the tag.TagInfo API in @ohos.nfc.tag.

function nfcTechDemo() {
    // Connect the tag if it has not been connected.
    if (!mifareClassic.isTagConnected()) {
        if (!mifareClassic.connectTag()) {
            console.error("mifareClassic connectTag failed.");
            return;
        }
    }

    try {
        let blockIndex = 1; // Set a correct index.
        mifareClassic.readSingleBlock(blockIndex).then((data : number[]) => {
            console.info("mifareClassic readSingleBlock Promise data: " + data);
        }).catch((err : BusinessError)=> {
            console.error(`mifareClassic readSingleBlock Promise errCode: ${err.code}, message: ${err.message}`);
        });
    } catch (businessError) {
        console.error(`mifareClassic readSingleBlock Promise catch businessError Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

<a id="readsingleblock-1"></a>

## readSingleBlock

```TypeScript
readSingleBlock(blockIndex: number, callback: AsyncCallback<number[]>): void
```

Reads a block (16 bytes) on this tag. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| blockIndex | number | Yes | Index of the block to read. The block indexes start from **0**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number[]&gt; | Yes | Callback used to return the block data read. |

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

// Obtain the correct MIFARE Classic tag by using the tag.TagInfo API in @ohos.nfc.tag.

function nfcTechDemo() {
    // Connect the tag if it has not been connected.
    if (!mifareClassic.isTagConnected()) {
        if (!mifareClassic.connectTag()) {
            console.error("mifareClassic connectTag failed.");
            return;
        }
    }

    try {
        let blockIndex = 1;  // Set a correct index.
        mifareClassic.readSingleBlock(blockIndex, (err : BusinessError, data : number[])=> {
            if (err) {
                console.error("mifareClassic readSingleBlock AsyncCallback err: " + err);
            } else {
                console.info("mifareClassic readSingleBlock AsyncCallback data: " + data);
            }
        });
    } catch (businessError) {
        console.error(`mifareClassic readSingleBlock AsyncCallback catch businessError Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

## restoreFromBlock

```TypeScript
restoreFromBlock(blockIndex: number): Promise<void>
```

Restores data in the temporary register from a block. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| blockIndex | number | Yes | Index of the destination block. The value starts form **0**. |

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

// Obtain the correct MIFARE Classic tag by using the tag.TagInfo API in @ohos.nfc.tag.

function nfcTechDemo() {
    // Connect the tag if it has not been connected.
    if (!mifareClassic.isTagConnected()) {
        if (!mifareClassic.connectTag()) {
            console.error("mifareClassic connectTag failed.");
            return;
        }   
    }

    try {
        let blockIndex = 1; // Set a correct index.
        mifareClassic.restoreFromBlock(blockIndex).then(() => {
            console.info("mifareClassic restoreFromBlock Promise success.");
        }).catch((err : BusinessError)=> {
            console.error(`mifareClassic restoreFromBlock Promise errCode: ${err.code}, message: ${err.message}`);
        });
    } catch (businessError) {
        console.error(`mifareClassic restoreFromBlock Promise catch businessError Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

<a id="restorefromblock-1"></a>

## restoreFromBlock

```TypeScript
restoreFromBlock(blockIndex: number, callback: AsyncCallback<void>): void
```

Restores data in the temporary register from a block. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| blockIndex | number | Yes | Index of the destination block. The value starts form **0**. |
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

// Obtain the correct MIFARE Classic tag by using the tag.TagInfo API in @ohos.nfc.tag.

function nfcTechDemo() {
    // Connect the tag if it has not been connected.
    if (!mifareClassic.isTagConnected()) {
        if (!mifareClassic.connectTag()) {
            console.error("mifareClassic connectTag failed.");
            return;
        }
    }

    try {
        let blockIndex = 1; // Set a correct index.
        mifareClassic.restoreFromBlock(blockIndex, (err : BusinessError)=> {
            if (err) {
                console.error(`mifareClassic restoreFromBlock AsyncCallback err Code: ${err.code}, message: ${err.message}`);
            } else {
                console.info("mifareClassic restoreFromBlock AsyncCallback success.");
            }
        });
    } catch (businessError) {
        console.error(`mifareClassic restoreFromBlock AsyncCallback catch Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

## transferToBlock

```TypeScript
transferToBlock(blockIndex: number): Promise<void>
```

Transfers data from the temporary register to a block. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| blockIndex | number | Yes | Index of the destination block. The value starts form **0**. |

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

// Obtain the correct MIFARE Classic tag by using the tag.TagInfo API in @ohos.nfc.tag.

function nfcTechDemo() {
    // Connect the tag if it has not been connected.
    if (!mifareClassic.isTagConnected()) {
        if (!mifareClassic.connectTag()) {
            console.error("mifareClassic connectTag failed.");
            return;
        }
    }

    try {
        let blockIndex = 1; // Set a correct index.
        mifareClassic.transferToBlock(blockIndex).then(() => {
            console.info("mifareClassic transferToBlock Promise success.");
        }).catch((err : BusinessError)=> {
            console.error(`mifareClassic transferToBlock Promise err Code: ${err.code}, message: ${err.message}`);
        });
    } catch (businessError) {
        console.error(`mifareClassic transferToBlock Promise catch Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

<a id="transfertoblock-1"></a>

## transferToBlock

```TypeScript
transferToBlock(blockIndex: number, callback: AsyncCallback<void>): void
```

Transfers data from the temporary register to a block. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| blockIndex | number | Yes | Index of the destination block. The value starts form **0**. |
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

// Obtain the correct MIFARE Classic tag by using the tag.TagInfo API in @ohos.nfc.tag.

function nfcTechDemo() {
    // Connect the tag if it has not been connected.
    if (!mifareClassic.isTagConnected()) {
        if (!mifareClassic.connectTag()) {
            console.error("mifareClassic connectTag failed.");
            return;
        }
    }

    try {
        let blockIndex = 1; // Set a correct index.
        mifareClassic.transferToBlock(blockIndex, (err : BusinessError)=> {
            if (err) {
                console.error(`mifareClassic transferToBlock AsyncCallback errCode: ${err.code}, message: ${err.message}`);
            } else {
                console.info("mifareClassic transferToBlock AsyncCallback success.");
            }
        });
    } catch (businessError) {
        console.error(`mifareClassic transferToBlock AsyncCallback catch Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

## writeSingleBlock

```TypeScript
writeSingleBlock(blockIndex: number, data: number[]): Promise<void>
```

Writes data to a block on this tag. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| blockIndex | number | Yes | Index of the block to write. The block indexes start from **0**. |
| data | number[] | Yes | 16-byte data to write. |

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

// Obtain the correct MIFARE Classic tag by using the tag.TagInfo API in @ohos.nfc.tag.

function nfcTechDemo() {
    // Connect the tag if it has not been connected.
    if (!mifareClassic.isTagConnected()) {
        if (!mifareClassic.connectTag()) {
            console.error("mifareClassic connectTag failed.");
            return;
        }
    }

    try {
        let blockIndex = 1; // Set a correct index.
        let rawData = [0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x0A,
            0x0B, 0x0C, 0x0D, 0x0E, 0x0F, 0x10]; // Set a correct key. The value must contain 16 bytes.
        mifareClassic.writeSingleBlock(blockIndex, rawData).then(() => {
            console.info("mifareClassic writeSingleBlock Promise success.");
        }).catch((err : BusinessError)=> {
            console.error("mifareClassic writeSingleBlock Promise errCode: ${err.code}, message: ${err.message}");
        });
    } catch (businessError) {
        console.error(`mifareClassic writeSingleBlock Promise catch businessError Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

<a id="writesingleblock-1"></a>

## writeSingleBlock

```TypeScript
writeSingleBlock(blockIndex: number, data: number[], callback: AsyncCallback<void>): void
```

Writes data to a block on this tag. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| blockIndex | number | Yes | Index of the block to write. The block indexes start from **0**. |
| data | number[] | Yes | 16-byte data to write. |
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

// Obtain the correct MIFARE Classic tag by using the tag.TagInfo API in @ohos.nfc.tag.

function nfcTechDemo() {
    // Connect the tag if it has not been connected.
    if (!mifareClassic.isTagConnected()) {
        if (!mifareClassic.connectTag()) {
            console.error("mifareClassic connectTag failed.");
            return;
        }
    }

    try {
        let blockIndex = 1; // Set a correct index.
        let rawData = [0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x0A,
            0x0B, 0x0C, 0x0D, 0x0E, 0x0F, 0x10]; // Set the correct data. The value must contain 16 bytes.
        mifareClassic.writeSingleBlock(blockIndex, rawData, (err : BusinessError)=> {
            if (err) {
                console.error(`mifareClassic writeSingleBlock AsyncCallback err Code: ${err.code}, message: ${err.message}`);
            } else {
                console.info("mifareClassic writeSingleBlock AsyncCallback success.");
            }
        });
    } catch (businessError) {
        console.error(`mifareClassic writeSingleBlock AsyncCallback catch Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```
