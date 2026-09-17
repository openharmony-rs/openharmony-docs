# IsoDepTag

Provides APIs to access ISO-DEP (ISO 14443-4) properties and I/O operations on a tag. This class inherits from **TagSession**.

**TagSession** is the base class of all NFC tag technologies. It provides common interfaces for establishing connections and transferring data. For more details, see [TagSession](arkts-connectivity-tagsession-tagsession-i.md).

For details about how to obtain an **IsoDepTag** object, see [NFC Tag Read/Write Development](../../../connectivity/nfc/nfc-tag-access-guide.md).

The following describes the unique APIs of **IsoDepTag**.

**Inheritance/Implementation:** IsoDepTag extends [TagSession](arkts-connectivity-tagsession-tagsession-i.md)

**Since:** 9

**System capability:** SystemCapability.Communication.NFC.Tag

## getHiLayerResponse

```TypeScript
getHiLayerResponse(): number[]
```

Obtains the higher-layer response bytes for the given tag. This API applies only to the IsoDep tags that use the NFC-B technology.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Return value:**

| Type | Description |
| --- | --- |
| number[] | Higher-layer response bytes obtained, which consist of hexadecimal numbers ranging from **0x00** to **0xFF**. If the IsoDep tag uses the NFC-A technology, **null** will be returned. |

**Examples**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// Obtain the correct isoDep tag by using the tag.TagInfo API in @ohos.nfc.tag.
let hiLayerResponse : number[] = isoDep.getHiLayerResponse();
console.info("isoDep hiLayerResponse: " + hiLayerResponse);
```

## getHistoricalBytes

```TypeScript
getHistoricalBytes(): number[]
```

Obtains the historical bytes for the given tag. This API applies only to the IsoDep tags that use the NFC-A technology.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Return value:**

| Type | Description |
| --- | --- |
| number[] | Historical bytes obtained, which consist of hexadecimal numbers ranging from **0x00** to **0xFF**. If the IsoDep tag uses the NFC-B technology, **null** will be returned. |

**Examples**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// Obtain the correct isoDep tag by using the tag.TagInfo API in @ohos.nfc.tag.
let historicalBytes : number[] = isoDep.getHistoricalBytes();
console.info("isoDep historicalBytes: " + historicalBytes);
```

## isExtendedApduSupported

```TypeScript
isExtendedApduSupported(): Promise<boolean>
```

Checks whether extended APDUs are supported. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that extended APDUs are supported, and the value **false** indicates the opposite. |

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

// Obtain the correct isoDep tag by using the tag.TagInfo API in @ohos.nfc.tag.
function nfcTechDemo() {
    // Connect the tag if it has not been connected.
    if (!isoDep.isTagConnected()) {
        if (!isoDep.connectTag()) {
            console.error("isoDep connectTag failed.");
            return;
        }
    }

    try {
        isoDep.isExtendedApduSupported().then((response: boolean) => {
            console.info("isoDep isExtendedApduSupported Promise response: " + response);
        }).catch((err: BusinessError) => {
            console.error(`isoDep isExtendedApduSupported Promise Code: ${err.code}, message: ${err.message}`);
        });
    } catch (businessError) {
        console.error(`isoDep isExtendedApduSupported Promise Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

```TypeScript
import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the correct isoDep tag by using the tag.TagInfo API in @ohos.nfc.tag.
function nfcTechDemo() {
    // Connect the tag if it has not been connected.
    if (!isoDep.isTagConnected()) {
        if (!isoDep.connectTag()) {
            console.error("isoDep connectTag failed.");
            return;
        }
    }

    try {
        isoDep.isExtendedApduSupported((err: BusinessError, response: boolean) => {
            if (err) {
                console.error(`isoDep isExtendedApduSupported AsyncCallback Code: ${err.code}, message: ${err. message}`);
            } else {
                console.info("isoDep isExtendedApduSupported AsyncCallback response: " + response);
            }
        });
    } catch (businessError) {
        console.error(`isoDep isExtendedApduSupported AsyncCallback Code: ${(businessError as Business).code}, message: ${(businessError as Business).message}`);
    }
}
```

## isExtendedApduSupported

```TypeScript
isExtendedApduSupported(callback: AsyncCallback<boolean>): void
```

Checks whether extended APDUs are supported. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the operation result. The value **true** indicates that extended APDUs are supported, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [3100201](../errorcode-nfc.md#3100201-tag-readwrite-error) | The tag running state is abnormal in the service. |
| [3100204](../errorcode-nfc.md#3100204-nfc-chip-io-exception) | The Tag I/O operation failed.<br>**Applicable version:** 12 and later |

**Examples**

See [isExtendedApduSupported](#isextendedapdusupported)
