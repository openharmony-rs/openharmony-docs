# PasteData

Implements a **PasteData** object. PasteData contains one or more data records ([PasteDataRecord](arkts-basicservices-pasteboard-pastedatarecord-i.md)) and property description objects ([PasteDataProperty](arkts-basicservices-pasteboard-pastedataproperty-i.md)). Before calling any API in **PasteData**, you must use ** [createData()](arkts-basicservices-pasteboard-createdata-f.md)** or ** [getData()](arkts-basicservices-pasteboard-systempasteboard-i.md#getdata)** to create a **PasteData** object.

**Since:** 6

**System capability:** SystemCapability.MiscServices.Pasteboard

## Modules to Import

```TypeScript
import { pasteboard } from '@kit.BasicServicesKit';
```

## addHtmlRecord

```TypeScript
addHtmlRecord(htmlText: string): void
```

Adds an HTML record to the PasteData, and adds **MIMETYPE_TEXT_HTML** to **mimeTypes** in [PasteDataProperty](arkts-basicservices-pasteboard-pastedataproperty-i.md). The parameters cannot be empty. Otherwise, the operation fails.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [addRecord](#addrecord-1)(mimeType: string, value: ValueType)

**System capability:** SystemCapability.MiscServices.Pasteboard

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| htmlText | string | Yes | HTML content. |

**Examples**

```TypeScript
let pasteData: pasteboard.PasteData = pasteboard.createPlainTextData('hello');
let html: string = "<!DOCTYPE html>\n" + "<html>\n" + "<head>\n" + "<meta charset=\"utf-8\">\n" + "<title>HTML-PASTEBOARD_HTML</title>\n" + "</head>\n" + "<body>\n" + "    <h1>HEAD</h1>\n" + "    <p></p>\n" + "</body>\n" + "</html>";
pasteData.addHtmlRecord(html);
```

## addRecord

```TypeScript
addRecord(record: PasteDataRecord): void
```

Adds a data record to the PasteData, and adds its type to **mimeTypes** in [PasteDataProperty](arkts-basicservices-pasteboard-pastedataproperty-i.md). The parameters cannot be empty. Otherwise, the operation fails.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.MiscServices.Pasteboard

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| record | [PasteDataRecord](arkts-basicservices-pasteboard-pastedatarecord-i.md) | Yes | Record to add. |

**Examples**

```TypeScript
// Create a PasteData object of the URI type.
let pasteData: pasteboard.PasteData = pasteboard.createData(pasteboard.MIMETYPE_TEXT_URI, 'dataability:///com.example.myapplication1/user.txt');
// Create a data record of the plain text type.
let textRecord: pasteboard.PasteDataRecord = pasteboard.createRecord(pasteboard.MIMETYPE_TEXT_PLAIN, 'hello');
let html: string = "<!DOCTYPE html>\n" + "<html>\n" + "<head>\n" + "<meta charset=\"utf-8\">\n" + "<title>HTML-PASTEBOARD_HTML</title>\n" + "</head>\n" + "<body>\n" + "    <h1>HEAD</h1>\n" + "    <p></p>\n" + "</body>\n" + "</html>";
let htmlRecord: pasteboard.PasteDataRecord = pasteboard.createRecord(pasteboard.MIMETYPE_TEXT_HTML, html);
pasteData.addRecord(textRecord);
pasteData.addRecord(htmlRecord);
```

```TypeScript
let pasteData: pasteboard.PasteData = pasteboard.createData(pasteboard.MIMETYPE_TEXT_URI, 'dataability:///com.example.myapplication1/user.txt');
// Create ArrayBuffer data.
let dataXml = new ArrayBuffer(256);
pasteData.addRecord('app/xml', dataXml);
```

## addRecord

```TypeScript
addRecord(mimeType: string, value: ValueType): void
```

Adds a data record to the PasteData, and adds its type to **mimeTypes** in [PasteDataProperty](arkts-basicservices-pasteboard-pastedataproperty-i.md). The parameters cannot be empty. Otherwise, the operation fails.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.MiscServices.Pasteboard

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mimeType | string | Yes | MIME type of PasteData. The length cannot exceed 1024 bytes. |
| value | [ValueType](arkts-basicservices-pasteboard-valuetype-t.md) | Yes | Data content. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed. |
| [12900002](../errorcode-pasteboard.md#12900002-maximum-number-of-records-reached) | The number of records exceeds the upper limit.<br>**Applicable version:** 9 |

**Examples**

See [addRecord](#addrecord)

## addTextRecord

```TypeScript
addTextRecord(text: string): void
```

Adds a plain text record to the PasteData, and adds **MIMETYPE_TEXT_PLAIN** to **mimeTypes** in [PasteDataProperty](arkts-basicservices-pasteboard-pastedataproperty-i.md). The parameters cannot be empty. Otherwise, the operation fails.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [addRecord](#addrecord-1)(mimeType: string, value: ValueType)

**System capability:** SystemCapability.MiscServices.Pasteboard

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Plain text. |

**Examples**

```TypeScript
let pasteData: pasteboard.PasteData = pasteboard.createPlainTextData('hello');
pasteData.addTextRecord('good');
```

## addUriRecord

```TypeScript
addUriRecord(uri: string): void
```

Adds a URI record to the PasteData, and adds **MIMETYPE_TEXT_URI** to **mimeTypes** in [PasteDataProperty](arkts-basicservices-pasteboard-pastedataproperty-i.md). The parameters cannot be empty. Otherwise, the operation fails.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [addRecord](#addrecord-1)(mimeType: string, value: ValueType)

**System capability:** SystemCapability.MiscServices.Pasteboard

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI content. |

**Examples**

```TypeScript
let pasteData: pasteboard.PasteData = pasteboard.createPlainTextData('hello');
pasteData.addUriRecord('dataability:///com.example.myapplication1/user.txt');
```

## addWantRecord

```TypeScript
addWantRecord(want: Want): void
```

Adds a Want record to the PasteData, and adds **MIMETYPE_TEXT_WANT** to **mimeTypes** in [PasteDataProperty](arkts-basicservices-pasteboard-pastedataproperty-i.md). The parameters cannot be empty. Otherwise, the operation fails.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [addRecord](#addrecord-1)(mimeType: string, value: ValueType)

**System capability:** SystemCapability.MiscServices.Pasteboard

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Want object. |

**Examples**

```TypeScript
import { Want } from '@kit.AbilityKit';

let pasteData: pasteboard.PasteData = pasteboard.createPlainTextData('hello');
let object: Want = {
    bundleName: "com.example.aafwk.test",
    abilityName: "com.example.aafwk.test.TwoAbility"
};
pasteData.addWantRecord(object);
```

## getMimeTypes

```TypeScript
getMimeTypes(): Array<string>
```

Obtains types of [PasteDataProperty](arkts-basicservices-pasteboard-pastedataproperty-i.md) of the PasteData.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.MiscServices.Pasteboard

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | Data types of the PasteData. |

**Examples**

```TypeScript
let pasteData: pasteboard.PasteData = pasteboard.createData(pasteboard.MIMETYPE_TEXT_PLAIN, 'hello');
let types: string[] = pasteData.getMimeTypes();
```

## getPrimaryHtml

```TypeScript
getPrimaryHtml(): string
```

Obtains the HTML content of the primary record.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.MiscServices.Pasteboard

**Return value:**

| Type | Description |
| --- | --- |
| string | HTML content. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
systemPasteboard.getData().then((pasteData: pasteboard.PasteData) => {
    let htmlText: string = pasteData.getPrimaryHtml();
}).catch((err: BusinessError) => {
    console.error(`Failed to get PasteData. errorCode: ${err.code}, errorMessage: ${err.message}.`);
});
```

## getPrimaryMimeType

```TypeScript
getPrimaryMimeType(): string
```

Obtains the data type of the primary record in the pasteboard.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.MiscServices.Pasteboard

**Return value:**

| Type | Description |
| --- | --- |
| string | Data type of the primary record. |

**Examples**

```TypeScript
let pasteData: pasteboard.PasteData = pasteboard.createData(pasteboard.MIMETYPE_TEXT_PLAIN, 'hello');
let type: string = pasteData.getPrimaryMimeType();
```

## getPrimaryPixelMap

```TypeScript
getPrimaryPixelMap(): image.PixelMap
```

Obtains the PixelMap of the primary record.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.MiscServices.Pasteboard

**Return value:**

| Type | Description |
| --- | --- |
| [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | PixelMap. |

**Examples**

```TypeScript
import { image } from '@kit.ImageKit';

// Create a buffer for storing image data.
let buffer = new ArrayBuffer(128);
// Define the image size.
let realSize: image.Size = { height: 3, width: 5 };
let opt: image.InitializationOptions = {
    size: realSize,
    pixelFormat: 3,
    editable: true,
    alphaType: 1,
    scaleMode: 1
};
image.createPixelMap(buffer, opt).then((pixelMap: image.PixelMap) => {
    let pasteData: pasteboard.PasteData = pasteboard.createData(pasteboard.MIMETYPE_PIXELMAP, pixelMap);
    let PixelMap: image.PixelMap = pasteData.getPrimaryPixelMap();
});
```

## getPrimaryText

```TypeScript
getPrimaryText(): string
```

Obtains the plain text of the primary record.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.MiscServices.Pasteboard

**Return value:**

| Type | Description |
| --- | --- |
| string | Plain text. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the SystemPasteboard object.
const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
// Asynchronously read the pasteboard data.
systemPasteboard.getData().then((pasteData: pasteboard.PasteData) => {
    // Obtain the plain text content from the pasteboard.
    let text: string = pasteData.getPrimaryText();
}).catch((err: BusinessError) => {
    // Handle the failure of obtaining the content.
    console.error(`Failed to get PasteData. errorCode: ${err.code}, errorMessage: ${err.message}.`);
});
```

## getPrimaryUri

```TypeScript
getPrimaryUri(): string
```

Obtains the URI of the primary record.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.MiscServices.Pasteboard

**Return value:**

| Type | Description |
| --- | --- |
| string | URI content. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
systemPasteboard.getData().then((pasteData: pasteboard.PasteData) => {
    let uri: string = pasteData.getPrimaryUri();
}).catch((err: BusinessError) => {
    console.error(`Failed to get PasteData. errorCode: ${err.code}, errorMessage: ${err.message}.`);
});
```

## getPrimaryWant

```TypeScript
getPrimaryWant(): Want
```

Obtains the **Want** object of the primary record.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.MiscServices.Pasteboard

**Return value:**

| Type | Description |
| --- | --- |
| [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Want object. |

**Examples**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
systemPasteboard.getData().then((pasteData: pasteboard.PasteData) => {
    let want: Want = pasteData.getPrimaryWant();
}).catch((err: BusinessError) => {
    console.error(`Failed to get PasteData. errorCode: ${err.code}, errorMessage: ${err.message}.`);
});
```

## getProperty

```TypeScript
getProperty(): PasteDataProperty
```

Obtains the property of the PasteData.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.MiscServices.Pasteboard

**Return value:**

| Type | Description |
| --- | --- |
| [PasteDataProperty](arkts-basicservices-pasteboard-pastedataproperty-i.md) | Property of the PasteData. |

**Examples**

```TypeScript
let pasteData: pasteboard.PasteData = pasteboard.createData(pasteboard.MIMETYPE_TEXT_PLAIN, 'hello');
let property: pasteboard.PasteDataProperty = pasteData.getProperty();
```

## getRecord

```TypeScript
getRecord(index: number): PasteDataRecord
```

Obtains the record with a specific index in PasteData.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.MiscServices.Pasteboard

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the target record. |

**Return value:**

| Type | Description |
| --- | --- |
| [PasteDataRecord](arkts-basicservices-pasteboard-pastedatarecord-i.md) | Record with the specified index. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [12900001](../errorcode-pasteboard.md#12900001-index-out-of-range) | The index is out of range. |

**Examples**

```TypeScript
let pasteData: pasteboard.PasteData = pasteboard.createData(pasteboard.MIMETYPE_TEXT_PLAIN, 'hello');
let record: pasteboard.PasteDataRecord = pasteData.getRecord(0);
```

## getRecordAt

```TypeScript
getRecordAt(index: number): PasteDataRecord
```

Obtains the record with a specific index in PasteData.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getRecord](#getrecord)(index: number)

**System capability:** SystemCapability.MiscServices.Pasteboard

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the target record. |

**Return value:**

| Type | Description |
| --- | --- |
| [PasteDataRecord](arkts-basicservices-pasteboard-pastedatarecord-i.md) | Record with the specified index. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |

**Examples**

```TypeScript
let pasteData: pasteboard.PasteData = pasteboard.createPlainTextData('hello');
let record: pasteboard.PasteDataRecord = pasteData.getRecordAt(0);
```

## getRecordCount

```TypeScript
getRecordCount(): number
```

Obtains the number of records in a PasteData object.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.MiscServices.Pasteboard

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of records. |

**Examples**

```TypeScript
let pasteData: pasteboard.PasteData = pasteboard.createData(pasteboard.MIMETYPE_TEXT_PLAIN, 'hello');
let count: number = pasteData.getRecordCount();
```

## getTag

```TypeScript
getTag(): string
```

Obtains the custom tag from the PasteData. If no custom tag is set, an empty string is returned.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.MiscServices.Pasteboard

**Return value:**

| Type | Description |
| --- | --- |
| string | Custom tag. If no custom tag is set, an empty string is returned. |

**Examples**

```TypeScript
let pasteData: pasteboard.PasteData = pasteboard.createData(pasteboard.MIMETYPE_TEXT_PLAIN, 'hello');
let tag: string = pasteData.getTag();
```

## hasMimeType

```TypeScript
hasMimeType(mimeType: string): boolean
```

Checks whether the PasteData contains data of the specified type.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [hasType](#hastype)(mimeType: string)

**System capability:** SystemCapability.MiscServices.Pasteboard

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mimeType | string | Yes | Type of the data to query. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the specified data type exists; returns **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |

**Examples**

```TypeScript
let pasteData: pasteboard.PasteData = pasteboard.createPlainTextData('hello');
let hasType: boolean = pasteData.hasMimeType(pasteboard.MIMETYPE_TEXT_PLAIN);
```

## hasType

```TypeScript
hasType(mimeType: string): boolean
```

Checks whether the PasteData contains data of the specified MIME type.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.MiscServices.Pasteboard

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mimeType | string | Yes | Type of the data to query. The value can be a predefined type listed in [Constants](../../../reference/apis-basic-services-kit/js-apis-pasteboard.md#constants), including HTML, Want, plain text, URI, and PixelMap, or a custom type. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the specified data type exists; returns **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |

**Examples**

```TypeScript
let pasteData: pasteboard.PasteData = pasteboard.createData(pasteboard.MIMETYPE_TEXT_PLAIN, 'hello');
let hasType: boolean = pasteData.hasType(pasteboard.MIMETYPE_TEXT_PLAIN);
```

## pasteComplete

```TypeScript
pasteComplete(): void
```

Invoked to notify pasteboard service the utilization of PasteData has completed and occupied resources can be released for further usage

**Since:** 12

**System capability:** SystemCapability.MiscServices.Pasteboard

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
systemPasteboard.getData((err: BusinessError, pasteData: pasteboard.PasteData) => {
    if (err) {
        console.error(`Failed to get PasteData. errorCode: ${err.code}, errorMessage: ${err.message}.`);
        return;
    }
    pasteData.pasteStart();
    console.info(`using data: ${pasteData.getPrimaryText()}`);
    pasteData.pasteComplete();
});
```

## pasteStart

```TypeScript
pasteStart(): void
```

Notifies the pasteboard service to retain the cross-device channel before reading data from the pasteboard.

**Since:** 12

**System capability:** SystemCapability.MiscServices.Pasteboard

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
systemPasteboard.getData((err: BusinessError, pasteData: pasteboard.PasteData) => {
    if (err) {
        console.error(`Failed to get PasteData. errorCode: ${err.code}, errorMessage: ${err.message}.`);
        return;
    }
    pasteData.pasteStart();
    console.info(`using data: ${pasteData.getPrimaryText()}`);
    pasteData.pasteComplete();
});
```

## removeRecord

```TypeScript
removeRecord(index: number): void
```

Removes the record with a specific index in PasteData.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.MiscServices.Pasteboard

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Specified index. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [12900001](../errorcode-pasteboard.md#12900001-index-out-of-range) | The index is out of range. |

**Examples**

```TypeScript
let pasteData: pasteboard.PasteData = pasteboard.createData(pasteboard.MIMETYPE_TEXT_PLAIN, 'hello');
pasteData.removeRecord(0);
```

## removeRecordAt

```TypeScript
removeRecordAt(index: number): boolean
```

Removes the record with a specific index in PasteData.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [removeRecord](#removerecord)(index: number)

**System capability:** SystemCapability.MiscServices.Pasteboard

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Specified index. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |

**Examples**

```TypeScript
let pasteData: pasteboard.PasteData = pasteboard.createPlainTextData('hello');
let isRemove: boolean = pasteData.removeRecordAt(0);
```

## replaceRecord

```TypeScript
replaceRecord(index: number, record: PasteDataRecord): void
```

Replaces the record with a specific index in PasteData.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.MiscServices.Pasteboard

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Specified index. |
| record | [PasteDataRecord](arkts-basicservices-pasteboard-pastedatarecord-i.md) | Yes | New record. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [12900001](../errorcode-pasteboard.md#12900001-index-out-of-range) | The index is out of range. |

**Examples**

```TypeScript
let pasteData: pasteboard.PasteData = pasteboard.createData(pasteboard.MIMETYPE_TEXT_PLAIN, 'hello');
let record: pasteboard.PasteDataRecord = pasteboard.createRecord(pasteboard.MIMETYPE_TEXT_URI, 'file://com.example.myapplication1/data/storage/el2/base/files/file.txt');
pasteData.replaceRecord(0, record);
```

## replaceRecordAt

```TypeScript
replaceRecordAt(index: number, record: PasteDataRecord): boolean
```

Replaces the record with a specific index in PasteData.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [replaceRecord](#replacerecord)(index: number, record: PasteDataRecord)

**System capability:** SystemCapability.MiscServices.Pasteboard

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Specified index. |
| record | [PasteDataRecord](arkts-basicservices-pasteboard-pastedatarecord-i.md) | Yes | New record. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise. |

**Examples**

```TypeScript
let pasteData: pasteboard.PasteData = pasteboard.createPlainTextData('hello');
let record: pasteboard.PasteDataRecord = pasteboard.createUriRecord('dataability:///com.example.myapplication1/user.txt');
let isReplace: boolean = pasteData.replaceRecordAt(0, record);
```

## setProperty

```TypeScript
setProperty(property: PasteDataProperty): void
```

Sets a [PasteDataProperty](arkts-basicservices-pasteboard-pastedataproperty-i.md) object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.MiscServices.Pasteboard

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| property | [PasteDataProperty](arkts-basicservices-pasteboard-pastedataproperty-i.md) | Yes | Property of the PasteData. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |

**Examples**

```TypeScript
// Define the type of the additional property.
type AdditionType = Record<string, Record<string, Object>>;

// Create a PasteData object of the HTML type.
let pasteData: pasteboard.PasteData = pasteboard.createData(pasteboard.MIMETYPE_TEXT_HTML, 'application/xml');
// Obtain a PasteDataProperty object.
let prop: pasteboard.PasteDataProperty = pasteData.getProperty();
prop.shareOption = pasteboard.ShareOption.INAPP;
// Note that attributes cannot be added to additions. Attributes can be added only by re-assigning values.
prop.additions = { 'TestOne': { 'Test': 123 }, 'TestTwo': { 'Test': 'additions' } } as AdditionType;
prop.tag = 'TestTag';
pasteData.setProperty(prop);
```

```TypeScript
The localOnly and shareOption attributes of [PasteDataProperty](arkts-basicservices-pasteboard-pastedataproperty-i.md) are mutually exclusive. The shareOption attribute is prioritized, and its value affects the value of localOnly.
```
