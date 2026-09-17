# PasteDataRecord

Provides **PasteDataRecord** APIs. A **PasteDataRecord** is an abstract definition of the content in the pasteboard. The pasteboard content consists of one or more plain text, HTML, URI, or Want records. After creating a PasteDataRecord, it is not supported to modify the value of the default data type of the PasteDataRecord. The correct value for the default data type should be specified when creating the PasteDataRecord. If you need to refresh the attribute value of the PasteDataRecord, please use [addEntry](#addentry).

**Since:** 7

**System capability:** SystemCapability.MiscServices.Pasteboard

## Modules to Import

```TypeScript
import { pasteboard } from '@kit.BasicServicesKit';
```

## addEntry

```TypeScript
addEntry(type: string, value: ValueType): void
```

Adds PasteData of an extra type to **PasteDataRecord**. The type added using this method is not the default type of **Record**. You can only use the [getData](#getdata) API to read the corresponding data.

**Since:** 14

**System capability:** SystemCapability.MiscServices.Pasteboard

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Type of extra data. The value can be a predefined MIME type listed in [Constants](../../../reference/apis-basic-services-kit/js-apis-pasteboard.md#constants), including HTML, Want, plain text, URI, and PixelMap, or a custom type. The value of **mimeType** cannot exceed 1024 bytes. |
| value | [ValueType](arkts-basicservices-pasteboard-valuetype-t.md) | Yes | Content of extra data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed. |

**Examples**

```TypeScript
// Build an HTML string.
let html = "<!DOCTYPE html>\n" + "<html>\n" + "<head>\n" + "<meta charset=\"utf-8\">\n" + "<title>HTML-PASTEBOARD_HTML</title>\n" + "</head>\n" + "<body>\n" + "    <h1>HEAD</h1>\n" + "    <p></p>\n" + "</body>\n" + "</html>";
// Create an URI data record.
let record: pasteboard.PasteDataRecord = pasteboard.createRecord(pasteboard.MIMETYPE_TEXT_URI, 'dataability:///com.example.myapplication1/user.txt');
// Add plain text data.
record.addEntry(pasteboard.MIMETYPE_TEXT_PLAIN, 'hello');
// Add HTML data.
record.addEntry(pasteboard.MIMETYPE_TEXT_HTML, html);
```

## convertToText

```TypeScript
convertToText(callback: AsyncCallback<string>): void
```

Forcibly converts the content in a **PasteData** object to text. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [toPlainText](#toplaintext)()

**System capability:** SystemCapability.MiscServices.Pasteboard

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Possible causes: Incorrect parameters types. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let record: pasteboard.PasteDataRecord = pasteboard.createUriRecord('dataability:///com.example.myapplication1/user.txt');
record.convertToText((err: BusinessError, data: string) => {
    if (err) {
        console.error(`Failed to convert to text. errorCode: ${err.code}, errorMessage: ${err.message}.`);
        return;
    }
    console.info(`Succeeded in converting to text. Data: ${data}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let record: pasteboard.PasteDataRecord = pasteboard.createUriRecord('dataability:///com.example.myapplication1/user.txt');
record.convertToText().then((data: string) => {
    console.info(`Succeeded in converting to text. Data: ${data}`);
}).catch((err: BusinessError) => {
    console.error(`Failed to convert to text. errorCode: ${err.code}, errorMessage: ${err.message}.`);
});
```

## convertToText

```TypeScript
convertToText(): Promise<string>
```

Forcibly converts the content in a **PasteData** object to text. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [toPlainText](#toplaintext)()

**System capability:** SystemCapability.MiscServices.Pasteboard

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the text obtained from the conversion. |

**Examples**

See [convertToText](#converttotext)

## getData

```TypeScript
getData(type: string): Promise<ValueType>
```

Obtains data of the specified type from **PasteDataRecord**.

**Since:** 14

**System capability:** SystemCapability.MiscServices.Pasteboard

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | type of PasteData, which cannot exceed 1024 bytes. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ValueType](arkts-basicservices-pasteboard-valuetype-t.md)&gt; | Promise used to return the data of the specified type in **PasteDataRecord**. If **PasteDataRecord** contains data of multiple types, the non-**PasteDataRecord** data of the default type can be obtained only through this API. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let html = "<!DOCTYPE html>\n" + "<html>\n" + "<head>\n" + "<meta charset=\"utf-8\">\n" + "<title>HTML-PASTEBOARD_HTML</title>\n" + "</head>\n" + "<body>\n" + "    <h1>HEAD</h1>\n" + "    <p></p>\n" + "</body>\n" + "</html>";
let record: pasteboard.PasteDataRecord = pasteboard.createRecord(pasteboard.MIMETYPE_TEXT_URI, 'dataability:///com.example.myapplication1/user.txt');
record.addEntry(pasteboard.MIMETYPE_TEXT_PLAIN, 'hello');
record.addEntry(pasteboard.MIMETYPE_TEXT_HTML, html);
record.getData(pasteboard.MIMETYPE_TEXT_PLAIN).then((value: pasteboard.ValueType) => {
    let textPlainContent = value as string;
    console.info('Success to get text/plain value. value is: ' + textPlainContent);
}).catch((err: BusinessError) => {
    console.error(`Failed to get text/plain value. errorCode: ${err.code}, errorMessage: ${err.message}.`);
});
record.getData(pasteboard.MIMETYPE_TEXT_URI).then((value: pasteboard.ValueType) => {
    let uri = value as string;
    console.info('Success to get text/uri value. value is: ' + uri);
}).catch((err: BusinessError) => {
    console.error(`Failed to get text/uri value. errorCode: ${err.code}, errorMessage: ${err.message}.`);
});
```

## getValidTypes

```TypeScript
getValidTypes(types: Array<string>): Array<string>
```

Obtains the intersection of the input types and the types of the PasteData.

**Since:** 14

**System capability:** SystemCapability.MiscServices.Pasteboard

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| types | Array&lt;string&gt; | Yes | List of the types. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | Intersection of the input types and the types of the PasteData obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed. |

**Examples**

```TypeScript
let html = "<!DOCTYPE html>\n" + "<html>\n" + "<head>\n" + "<meta charset=\"utf-8\">\n" + "<title>HTML-PASTEBOARD_HTML</title>\n" + "</head>\n" + "<body>\n" + "    <h1>HEAD</h1>\n" + "    <p></p>\n" + "</body>\n" + "</html>";
let record: pasteboard.PasteDataRecord = pasteboard.createRecord(pasteboard.MIMETYPE_TEXT_URI, 'dataability:///com.example.myapplication1/user.txt');
record.addEntry(pasteboard.MIMETYPE_TEXT_PLAIN, 'hello');
record.addEntry(pasteboard.MIMETYPE_TEXT_HTML, html);
let types: string[] = record.getValidTypes([
    pasteboard.MIMETYPE_TEXT_PLAIN,
    pasteboard.MIMETYPE_TEXT_HTML,
    pasteboard.MIMETYPE_TEXT_URI,
    pasteboard.MIMETYPE_TEXT_WANT,
    pasteboard.MIMETYPE_PIXELMAP
]);
```

## toPlainText

```TypeScript
toPlainText(): string
```

Forcibly converts HTML, plain, and URI content in a **PasteDataRecord** to the plain text.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.MiscServices.Pasteboard

**Return value:**

| Type | Description |
| --- | --- |
| string | Plain text. |

**Examples**

```TypeScript
let record: pasteboard.PasteDataRecord = pasteboard.createRecord(pasteboard.MIMETYPE_TEXT_HTML, '<html>hello</html>');
let text: string = record.toPlainText();
console.info(`Succeeded in converting to text. Text: ${text}`);
```

## data

```TypeScript
data: Record<string, ArrayBuffer>
```

Content of custom data. Modifications to this attribute are ineffective.

**Type:** Record&lt;string, ArrayBuffer&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.MiscServices.Pasteboard

## htmlText

```TypeScript
htmlText: string
```

HTML content, must conform to standard HTML format. Modifications to this attribute are ineffective. To refresh the attribute value, please use [addEntry](#addentry).

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.MiscServices.Pasteboard

## mimeType

```TypeScript
mimeType: string
```

Default type of PasteDataRecord. Modifications to this attribute are ineffective.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.MiscServices.Pasteboard

## pixelMap

```TypeScript
pixelMap: image.PixelMap
```

PixelMap content. Modifications to this attribute are ineffective. To refresh the attribute value, please use [addEntry](#addentry).

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.MiscServices.Pasteboard

## plainText

```TypeScript
plainText: string
```

Plain text. Modifications to this attribute are ineffective. To refresh the attribute value, please use [addEntry](#addentry).

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.MiscServices.Pasteboard

## uri

```TypeScript
uri: string
```

URI content, must conform to standard URI format. Modifications to this attribute are ineffective. To refresh the attribute value, please use [addEntry](#addentry).

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.MiscServices.Pasteboard

## want

```TypeScript
want: Want
```

Want content. Modifications to this attribute are ineffective. To refresh the attribute value, please use [addEntry](#addentry).

**Type:** [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.MiscServices.Pasteboard
