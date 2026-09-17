# @ohos.xml (XML Parsing and Generation)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong; @lijin1039-->
<!--Designer: @Malzahar; @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=58e0aac1ecb6b253638163c0254ed24f4d229ae6 translatedAt=2026-09-09T03:19:24.317Z pushedAt=2026-09-09T04:22:37.559Z -->

This module provides APIs for generating and parsing XML. It supports generating and parsing XML text in multiple ways, helping developers efficiently process structured XML data.

The module offers two methods for generating XML files:
* [XmlSerializer](#xmlserializer): suitable for scenarios where the size of the XML text is known in advance. Developers need to create an ArrayBuffer as the buffer area and ensure that the buffer is large enough to hold the generated text.
* [XmlDynamicSerializer<sup>20+</sup>](#xmldynamicserializer20): suitable for scenarios where the size of the XML text is not known in advance. There is no need to create an ArrayBuffer, and the program expands the buffer dynamically. However, the maximum length of the serialized result string is 100000.

This module provides two methods for parsing XML files:
* [XmlPullParser](#xmlpullparser): suitable for scenarios where random access and flexible parsing of XML text are required.
* [XmlSAXParser<sup>24+</sup>](#xmlsaxparser24): suitable for streaming parsing of XML text. When the XML text is large and other parsing methods consume more memory, streaming parsing is recommended.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import

```ts
import { xml } from '@kit.ArkTS';
```

## XmlSerializer

The XmlSerializer API is used to generate XML files. Based on a pre-allocated ArrayBuffer buffer area, this API writes XML text into the buffer by sequentially calling element writing methods such as startElement, setAttributes, setText, and endElement.

### constructor

constructor(buffer: ArrayBuffer | DataView, encoding?: string)

Constructs and returns an XmlSerializer object, which is used to write XML information into the specified ArrayBuffer or DataView memory.

> **NOTE**
>
> The buffer is a buffer whose size can be customized by developers as needed. It is used to temporarily store the generated XML text. During use, ensure that the buffer is large enough to hold the generated text.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name  | Type                             | Mandatory| Description                                            |
| -------- | --------------------------------- | ---- | ------------------------------------------------ |
| buffer   | ArrayBuffer \| DataView | Yes   | ArrayBuffer or DataView memory used to receive the written XML information. Ensure that the buffer area is large enough to hold the generated text content. |
| encoding | string                            | No  | Encoding format. The default value is **'utf-8'** (the only format currently supported).              |

**Example**

```ts
let arrayBuffer = new ArrayBuffer(2048);
let xmlSerializer = new xml.XmlSerializer(arrayBuffer, "utf-8");
```

### setAttributes

setAttributes(name: string, value: string): void

Sets an attribute.

> **NOTE**
>
> This API must be called after [startElement](#startelement) to set attributes for the currently opened element. Calling this API before the element start tag is written will produce invalid XML.
>
> This API does not perform standard XML validation on the added data. Ensure that the added data complies with the standard XML specification. For example, attribute names starting with a digit and multiple attributes with the same name are not allowed.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description           |
| ------ | ------ | ---- | --------------- |
| name   | string | Yes   | Attribute name of the XML element.   |
| value  | string | Yes   | Attribute value of the XML element, corresponding to the attribute name specified by the name parameter. |

**Example**

```ts
import { util } from '@kit.ArkTS';

let arrayBuffer = new ArrayBuffer(2048);
let thatSer = new xml.XmlSerializer(arrayBuffer);
thatSer.startElement("note");
thatSer.setAttributes("importance", "high");
thatSer.endElement();
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <note importance="high"/>
```

### addEmptyElement

addEmptyElement(name: string): void

Adds an empty element.

> **NOTE**
>
> This API does not perform standard XML validation on the added data. Ensure that the added data complies with standard XML specifications. For example, element names starting with a digit are not allowed.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description              |
| ------ | ------ | ---- | ------------------ |
| name   | string | Yes   | Element name. Value rule: must not start with a digit. |

**Example**

```ts
import { util } from '@kit.ArkTS';

let arrayBuffer = new ArrayBuffer(2048);
let thatSer = new xml.XmlSerializer(arrayBuffer);
thatSer.addEmptyElement("d");
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <d/>
```

### setDeclaration

setDeclaration(): void

Sets the file declaration with encoding information. After this API is called, a declaration in the `<?xml version="1.0" encoding="utf-8"?>` format is generated in the XML text.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Example**

```ts
import { util } from '@kit.ArkTS';

let arrayBuffer = new ArrayBuffer(2048);
let thatSer = new xml.XmlSerializer(arrayBuffer);
thatSer.setDeclaration();
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result);
// <?xml version="1.0" encoding="utf-8"?>
```

### startElement

startElement(name: string): void

Adds the start tag based on the given element name.

> **NOTE**
>
>- After calling this API, you must call [endElement](#endelement) to write the end tag of the element to ensure that the node is properly closed.
>
>- This API does not perform standard XML validation on the added data. Ensure that the added data complies with standard XML specifications. For example, element names starting with a digit are not allowed.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description              |
| ------ | ------ | ---- | ------------------ |
| name   | string | Yes  | Name of the element.|

**Example**

```ts
import { util } from '@kit.ArkTS';

let arrayBuffer = new ArrayBuffer(2048);
let thatSer = new xml.XmlSerializer(arrayBuffer);
thatSer.startElement("note");
thatSer.setText("Happy");
thatSer.endElement();
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result);
// <note>Happy</note>
```

### endElement

endElement(): void

Adds the end tag of the element.

> **NOTE**
>
> Before calling this API, you must call [startElement](#startelement) to write the start flag.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Example**

```ts
import { util } from '@kit.ArkTS';

let arrayBuffer = new ArrayBuffer(2048);
let thatSer = new xml.XmlSerializer(arrayBuffer);
thatSer.startElement("note");
thatSer.setText("Happy");
thatSer.endElement();
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result);
// <note>Happy</note>
```

### setNamespace

setNamespace(prefix: string, namespace: string): void

Adds a namespace for the current element tag. This is applicable to scenarios where elements from different vocabularies or schemas need to be distinguished in the same XML document, such as documents that mix multiple XML standards.

> **NOTE**
>
> This API should be called before [startElement](#startelement) to set the namespace prefix for the element to be opened. Call sequence: call setNamespace to set the namespace first, and then call startElement to open the element.
>
> This API does not perform standard XML validation on the added data. Ensure that the added data complies with standard XML specifications. For example, prefixes starting with a digit and setting multiple namespaces for the same element are prohibited.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name   | Type  | Mandatory| Description                          |
| --------- | ------ | ---- | ------------------------------ |
| prefix    | string | Yes  | Prefix of the element and its child elements.    |
| namespace | string | Yes  | Namespace to set.|

**Example**

```ts
import { util } from '@kit.ArkTS';

let arrayBuffer = new ArrayBuffer(2048);
let thatSer = new xml.XmlSerializer(arrayBuffer);
thatSer.setNamespace("h", "http://www.w3.org/TR/html4/");
thatSer.startElement("note");
thatSer.endElement();
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result);
// <h:note xmlns:h="http://www.w3.org/TR/html4/"/>
```

### setComment

setComment(text: string): void

Adds comment content. The generated comment structure is: `<!--` + comment content + `-->`.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description                |
| ------ | ------ | ---- | -------------------- |
| text   | string | Yes  | Comment to set.|

**Example**

```ts
import { util } from '@kit.ArkTS';

let arrayBuffer = new ArrayBuffer(2048);
let thatSer = new xml.XmlSerializer(arrayBuffer);
thatSer.setComment("Hello, World!");
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <!--Hello, World!-->
```

### setCDATA

setCDATA(text: string): void

Provides the capability to add data within a CDATA tag. This is applicable to scenarios where special characters (such as <, &, etc.) in XML content need to be preserved as-is without being processed by the XML parser. The generated CDATA tag structure is: `<![CDATA[` + the added data + `]]>`.

> **NOTE**
>
> This API does not perform standard XML validation on the added data. Ensure that the added data complies with standard XML specifications. For example, data containing the "\]\]\>" string is not allowed in a CDATA tag.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description             |
| ------ | ------ | ---- | ----------------- |
| text   | string | Yes   | Data content in the CDATA tag. |

**Example**

```ts
import { util } from '@kit.ArkTS';

let arrayBuffer = new ArrayBuffer(2048);
let thatSer = new xml.XmlSerializer(arrayBuffer);
thatSer.setCDATA('root SYSTEM');
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <![CDATA[root SYSTEM]]>
```

### setText

setText(text: string): void

Adds a tag value. The tag value is used as the text content of the current element and is written between the start tag and the end tag of the element.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description            |
| ------ | ------ | ---- | ---------------- |
| text   | string | Yes   | Tag text content of the XML element. |

**Example**

```ts
import { util } from '@kit.ArkTS';

let arrayBuffer = new ArrayBuffer(2048);
let thatSer = new xml.XmlSerializer(arrayBuffer);
thatSer.startElement("note");
thatSer.setAttributes("importance", "high");
thatSer.setText("Happy");
thatSer.endElement();
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <note importance="high">Happy</note>
```

### setDocType

setDocType(text: string): void

Adds a document type. After this API is called, a document type declaration in the `<!DOCTYPE ...>` format is generated in the XML text.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description               |
| ------ | ------ | ---- | ------------------- |
| text   | string | Yes   | Content of the document type declaration. |

**Example**

```ts
import { util } from '@kit.ArkTS';

let arrayBuffer = new ArrayBuffer(2048);
let thatSer = new xml.XmlSerializer(arrayBuffer);
thatSer.setDocType('root SYSTEM "http://www.test.org/test.dtd"');
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <!DOCTYPE root SYSTEM "http://www.test.org/test.dtd">
```

## XmlDynamicSerializer<sup>20+</sup>

The **XmlDynamicSerializer** class is used to dynamically generate XML strings. It is recommended when the length of the XML content cannot be determined in advance.

> **NOTE**
>
> Objects constructed from this class do not require manual creation of an ArrayBuffer. You can continuously add XML elements, and the upper limit for the length of the final serialized string result is 100,000 characters.

### constructor<sup>20+</sup>

constructor(encoding?: string)

Constructs and returns an XmlDynamicSerializer object, which supports dynamically expanding the buffer to generate XML strings without specifying the buffer size in advance.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name  | Type                             | Mandatory| Description                                            |
| -------- | --------------------------------- | ---- | ------------------------------------------------ |
| encoding | string                            | No   | Encoding format. The default value is 'utf-8' (currently only 'utf-8' is supported).          |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200066 | Incorrect encoding format, only support utf-8. |

**Example**

```ts
let serializer = new xml.XmlDynamicSerializer('utf-8');
```

### getOutput<sup>20+</sup>

getOutput(): ArrayBuffer

Obtains the ArrayBuffer of the XML string.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type  | Description                |
| ------ | -------------------- |
| ArrayBuffer | ArrayBuffer for storing the XML information to set.|

**Example**

```ts
import { util } from '@kit.ArkTS';

let serializer = new xml.XmlDynamicSerializer('utf-8');
serializer.startElement("note");
serializer.setText("Happy");
serializer.endElement();
let arr = serializer.getOutput();
let uint8 = new Uint8Array(arr);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <note>Happy</note>
```

### setAttributes<sup>20+</sup>

setAttributes(name: string, value: string): void

Sets an attribute.

> **NOTE**
>
> This API must be called after [startElement<sup>20+</sup>](#startelement20) to set attributes for the currently opened element.
>
> This API does not perform standard XML validation on the data to add. Ensure that the data complies with the XML specifications. For example, attribute names starting with a digit and multiple attributes with the same name are not allowed.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description           |
| ------ | ------ | ---- | --------------- |
| name   | string | Yes   | Attribute name. The total length of the composed XML must not exceed 100000, and it must not be an empty string.|
| value  | string | Yes   | Attribute value. The total length of the composed XML must not exceed 100000 characters.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200062 | The cumulative length of xml has exceeded the upper limit 100000. |
| 10200063 | Illegal position for xml. |
| 10200064 | Cannot be an empty string. |

**Example**

```ts
import { util } from '@kit.ArkTS';

let serializer = new xml.XmlDynamicSerializer('utf-8');
serializer.startElement("note");
serializer.setAttributes("importance", "high");
serializer.endElement();
let arrayBuffer = serializer.getOutput();
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <note importance="high"/>
```

### addEmptyElement<sup>20+</sup>

addEmptyElement(name: string): void

Adds an empty element.

> **NOTE**
>
> This API does not perform standard XML validation on the data to add. Ensure that the data complies with the XML specifications. For example, element names starting with a digit are not allowed.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description              |
| ------ | ------ | ---- | ------------------ |
| name   | string | Yes   | Element name of the empty element. The length of the XML composed must not exceed 100000.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200062 | The cumulative length of xml has exceeded the upper limit 100000. |
| 10200064 | Cannot be an empty string. |

**Example**

```ts
import { util } from '@kit.ArkTS';

let serializer = new xml.XmlDynamicSerializer('utf-8');
serializer.addEmptyElement("d");
let arrayBuffer = serializer.getOutput();
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <d/>
```

### setDeclaration<sup>20+</sup>

setDeclaration(): void

Writes a file declaration with encoding. After this API is called, a declaration in the format of `<?xml version="1.0" encoding="utf-8"?>` is generated in the XML text.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200062 | The cumulative length of xml has exceeded the upper limit 100000. |
| 10200063 | Illegal position for xml. |

**Example**

```ts
import { util } from '@kit.ArkTS';

let serializer = new xml.XmlDynamicSerializer('utf-8');
serializer.setDeclaration();
let arrayBuffer = serializer.getOutput();
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <?xml version="1.0" encoding="utf-8"?>
```

### startElement<sup>20+</sup>

startElement(name: string): void

Writes the start tag of the element.

> **NOTE**
>
>- After calling this API, you must call [endElement<sup>20+</sup>](#endelement20) to write the end tag of the element to ensure that the node is properly closed.
>
>- This API does not perform standard XML validation on the data to add. Ensure that the data complies with the XML specifications. For example, element names starting with a digit are not allowed.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description              |
| ------ | ------ | ---- | ------------------ |
| name   | string | Yes   | Element name of the current element. The total length of the composed XML must not exceed 100000, and the value must not be empty. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200062 | The cumulative length of xml has exceeded the upper limit 100000. |
| 10200064 | Cannot be an empty string. |

**Example**

```ts
import { util } from '@kit.ArkTS';

let serializer = new xml.XmlDynamicSerializer('utf-8');
serializer.startElement("note");
serializer.setText("Happy");
serializer.endElement();
let arrayBuffer = serializer.getOutput();
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <note>Happy</note>
```

### endElement<sup>20+</sup>

endElement(): void

Writes the end tag of the element.

> **NOTE**
>
> Before calling this API, you must call [startElement<sup>20+</sup>](#startelement20) to write the start tag of the element.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200062 | The cumulative length of xml has exceeded the upper limit 100000. |
| 10200065 | There is no match between the startElement and the endElement. |

**Example**

```ts
import { util } from '@kit.ArkTS';

let serializer = new xml.XmlDynamicSerializer('utf-8');
serializer.startElement("note");
serializer.setText("Happy");
serializer.endElement();
let arrayBuffer = serializer.getOutput();
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <note>Happy</note>
```

### setNamespace<sup>20+</sup>

setNamespace(prefix: string, namespace: string): void

Sets the namespace for an element tag.

> **NOTE**
>
> This API should be called before [startElement<sup>20+</sup>](#startelement20) to set the namespace prefix for the element to be opened. Call sequence: call setNamespace to set the namespace first, and then call startElement to open the element.
>
> This API does not perform standard XML validation on the data to add. Ensure that the data complies with the XML specifications. For example, prefixes starting with a digit and setting multiple namespaces for the same element are not allowed.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name   | Type  | Mandatory| Description                          |
| --------- | ------ | ---- | ------------------------------ |
| prefix    | string | Yes   | Prefix of the current element and its child elements. The total length of the composed XML must not exceed 100000, and it must not be an empty string. |
| namespace | string | Yes   | Namespace of the current element and its child elements. The total length of the composed XML must not exceed 100000, and it must not be an empty string. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200062 | The cumulative length of xml has exceeded the upper limit 100000. |
| 10200064 | Cannot be an empty string. |

**Example**

```ts
import { util } from '@kit.ArkTS';

let serializer = new xml.XmlDynamicSerializer('utf-8');
serializer.setNamespace("h", "http://www.w3.org/TR/html4/");
serializer.startElement("note");
serializer.endElement();
let arrayBuffer = serializer.getOutput();
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <h:note xmlns:h="http://www.w3.org/TR/html4/"/>
```

### setComment<sup>20+</sup>

setComment(text: string): void

Writes comment content. The generated comment structure is: `<!--` + comment content + `-->`.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description                |
| ------ | ------ | ---- | -------------------- |
| text   | string | Yes   | Comment content of the current element. The total length of the composed XML must not exceed 100000, and the content must not be empty. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200062 | The cumulative length of xml has exceeded the upper limit 100000. |
| 10200064 | Cannot be an empty string. |

**Example**

```ts
import { util } from '@kit.ArkTS';

let serializer = new xml.XmlDynamicSerializer('utf-8');
serializer.setComment("Hello, World!");
let arrayBuffer = serializer.getOutput();
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <!--Hello, World!-->
```

### setCdata<sup>20+</sup>

setCdata(text: string): void

Provides the capability to add data in a CDATA tag. The generated CDATA tag structure is: `<![CDATA[` + the added data + `]]>`.

> **NOTE**
>
> This API does not perform standard XML validation on the data to add. Ensure that the data complies with the XML specifications. For example, adding data containing the `"\]\]\>"` string in a CDATA tag is not allowed.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description             |
| ------ | ------ | ---- | ----------------- |
| text   | string | Yes   | Data content in the CDATA tag. The length of the composed XML must not exceed 100000. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200062 | The cumulative length of xml has exceeded the upper limit 100000. |
| 10200064 | Cannot be an empty string. |

**Example**

```ts
import { util } from '@kit.ArkTS';

let serializer = new xml.XmlDynamicSerializer('utf-8');
serializer.setCdata('root SYSTEM')
let arrayBuffer = serializer.getOutput();
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <![CDATA[root SYSTEM]]>
```

### setText<sup>20+</sup>

setText(text: string): void

Sets a tag value.

> **NOTE**
>
> This API must be called after [startElement<sup>20+</sup>](#startelement20) and before [endElement<sup>20+</sup>](#endelement20) to set the text content of the current element.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description            |
| ------ | ------ | ---- | ---------------- |
| text   | string | Yes   | Tag value. The total length of the composed XML must not exceed 100000, and the value must not be an empty string. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200062 | The cumulative length of xml has exceeded the upper limit 100000. |
| 10200064 | Cannot be an empty string. |

**Example**

```ts
import { util } from '@kit.ArkTS';

let serializer = new xml.XmlDynamicSerializer('utf-8');
serializer.startElement("note");
serializer.setAttributes("importance", "high");
serializer.setText("Happy");
serializer.endElement();
let arrayBuffer = serializer.getOutput();
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <note importance="high">Happy</note>
```

### setDocType<sup>20+</sup>

setDocType(text: string): void

Sets a document type.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description               |
| ------ | ------ | ---- | ------------------- |
| text   | string | Yes   | Content of the document type declaration. The total length of the XML must not exceed 100000. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200062 | The cumulative length of xml has exceeded the upper limit 100000. |
| 10200064 | Cannot be an empty string. |

**Example**

```ts
import { util } from '@kit.ArkTS';

let serializer = new xml.XmlDynamicSerializer('utf-8');
serializer.setDocType('root SYSTEM "http://www.test.org/test.dtd"');
let arrayBuffer = serializer.getOutput();
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <!DOCTYPE root SYSTEM "http://www.test.org/test.dtd">
```

## XmlPullParser

The XmlPullParser interface is used to parse existing XML files, and is suitable for scenarios that require random access and flexible parsing of XML text.

### constructor

constructor(buffer: ArrayBuffer | DataView, encoding?: string)

Creates and returns an **XmlPullParser** object.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name  | Type                             | Mandatory| Description                                      |
| -------- | --------------------------------- | ---- | ------------------------------------------ |
| buffer   | ArrayBuffer \| DataView | Yes   | The ArrayBuffer or DataView memory where the XML text data to be parsed resides. |
| encoding | string                            | No  | Encoding format. The default value is **'utf-8'** (the only format currently supported).        |

**Example**

```ts
import { util } from '@kit.ArkTS';

let strXml = '<title>Happy</title>'
let textEncoder = new util.TextEncoder();
let uint8Array = textEncoder.encodeInto(strXml);
let xmlParser = new xml.XmlPullParser(uint8Array.buffer as object as ArrayBuffer, 'UTF-8');
```

### parseXml<sup>14+</sup>

parseXml(option: ParseOptions): void

Parses the XML. After this API is called, the corresponding parsing events are triggered based on the callback functions configured in ParseOptions, and parsing information such as tags, attributes, and text is passed through the callback functions.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type                         | Mandatory| Description         |
| ------ | ----------------------------- | ---- | ------------- |
| option | [ParseOptions](#parseoptions) | Yes  | XML parsing options.|

**Example**
For specific usage scenarios, see [Parsing XML Tags and Tag Values](../../arkts-utils/xml-parsing.md) and [Parsing XML Attributes and Attribute Values](../../arkts-utils/xml-parsing.md).

```ts
import { xml, util } from '@kit.ArkTS';

let strXml =
  '<?xml version="1.0" encoding="utf-8"?>' +
    '<note importance="high" logged="true">' +
    '    <title><![CDATA[Test\nTest]]></title>' +
    '</note>';
let textEncoder = new util.TextEncoder();
let uint8 = textEncoder.encodeInto(strXml);

function onParseEvent(key: xml.EventType, value: xml.ParseInfo) {
  if (key == xml.EventType.CDSECT) {
    console.info(JSON.stringify(value.getText()));
  }
  return true;
}
let options: xml.ParseOptions = {supportDoctype: true, ignoreNameSpace: true, tokenValueCallbackFunction: onParseEvent}
let pullParser = new xml.XmlPullParser(uint8.buffer as object as ArrayBuffer);
pullParser.parseXml(options);
// "Test\nTest"
```

### parse<sup>(deprecated)</sup>

parse(option: ParseOptions): void

This API is used to parse XML text based on the specified parsing options.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 14. You are advised to use [parseXml<sup>14+</sup>](#parsexml14) instead.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type                         | Mandatory| Description                            |
| ------ | ----------------------------- | ---- | -------------------------------- |
| option | [ParseOptions](#parseoptions) | Yes  | XML parsing options.|

**Example**

```ts
import { util } from '@kit.ArkTS';

let strXml =
  '<?xml version="1.0" encoding="utf-8"?>' +
  '<note importance="high" logged="true">' +
    '<company>John &amp; Hans</company>' +
    '<title>Happy</title>' +
  '</note>';
let textEncoder = new util.TextEncoder();
let arrBuffer = textEncoder.encodeInto(strXml);
let that = new xml.XmlPullParser(arrBuffer.buffer as object as ArrayBuffer, 'UTF-8');
let parseResult = '';
function func(name: string, value: string) {
  parseResult = name + value;
  console.info(parseResult);
  return true;
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:true, tagValueCallbackFunction:func}
that.parse(options);
// note
// company
// John & Hans
// company
// title
// Happy
// title
// note
```

## AttributeWithTagCb<sup>20+</sup>

type AttributeWithTagCb = (tagName: string, key: string, value: string) => boolean

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name  |  Type | Mandatory|  Description  |
| ------- | -------| ---- | ------ |
| tagName | string | Yes  | Tag name.|
| key     | string | Yes  | Attribute name.|
| value   | string | Yes  | Attribute value.|

**Return value**

| Type   | Description                                                                      |
| ------- | ------------------------------------------------------------------------- |
| boolean | A Boolean value that indicates whether to continue parsing the tag name, attribute name, and attribute value. The value **true** indicates that the parsing continues, and the value **false** indicates that the parsing stops.|

## ParseOptions

XML parsing options, used to configure the parsing behavior of XmlPullParser. Developers can control the parsing scope through supportDoctype and ignoreNameSpace, and receive different types of parsing events by registering callback functions (tagValueCallbackFunction, attributeValueCallbackFunction, tokenValueCallbackFunction, etc.).


**System capability**: SystemCapability.Utils.Lang


| Name                          | Type                                                        | Read-Only| Optional| Description                                   |
| ------------------------------ | ------------------------------------------------------------ | ---- | ---- | --------------------------------------- |
| supportDoctype                 | boolean                                                      | No   | Yes   | Whether to parse the document type. false means not parsing the document type, and true means parsing the document type. The default value is false.  <br/>**Atomic service API**: Since API version 11, this API is supported in atomic services.|
| ignoreNameSpace                | boolean                                                      | No   | Yes   | Whether to ignore the namespace. After the namespace is ignored, it will not be parsed. true means ignoring the namespace, and false means not ignoring the namespace. The default value is false. <br/>**Atomic service API**: Since API version 11, this API is supported in atomic services.|
| tagValueCallbackFunction       | (name: string, value: string) =&gt; boolean | No   | Yes   | Parses the start tag, tag value, and end tag. Returning true means continuing parsing, and returning false means stopping parsing. The default value is undefined, which means no parsing. <br/>**Atomic service API**: Since API version 11, this API is supported in atomic services.|
| attributeValueCallbackFunction | (name: string, value: string) =&gt; boolean | No   | Yes   | Parses attributes and attribute values. Returning true means continuing parsing, and returning false means stopping parsing. The default value is undefined, which means no parsing. <br/>**Atomic service API**: Since API version 11, this API is supported in atomic services.|
| tokenValueCallbackFunction     | (eventType: [EventType](#eventtype), value: [ParseInfo](#parseinfo)) =&gt; boolean | No   | Yes   | Parses the element event type ([EventType](#eventtype)) and [ParseInfo](#parseinfo) attributes. The default value is undefined, which means no parsing. <br/>**Atomic service API**: Since API version 11, this API is supported in atomic services.|
| attributeWithTagCallbackFunction<sup>20+</sup> | [AttributeWithTagCb](#attributewithtagcb20) | No| Yes  | Tag name, attribute name, and attribute value of parsing. The default value is **undefined**, indicating that no parsing is performed.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|

## ParseInfo

Provides APIs to manage the parsed XML information.


### getColumnNumber

getColumnNumber(): number

Obtains the current column number, starting from 1.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type  | Description          |
| ------ | -------------- |
| number | Column number of the current element (starting from 1), used to locate the XML parsing position. |

**Example**

```ts
import { util } from '@kit.ArkTS';

let strXml = '<?xml version="1.0" encoding="utf-8"?><note>Happy</note>';
let textEncoder = new util.TextEncoder();
let arrBuffer = textEncoder.encodeInto(strXml);
let that = new xml.XmlPullParser(arrBuffer.buffer as object as ArrayBuffer);
let str = "";
function func(key: xml.EventType, value: xml.ParseInfo) {
  str += 'key:' + key + ' value:' + value.getColumnNumber() + ' ';
  return true; // Determine whether to continue parsing, used to continue or terminate parsing.
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:true, tokenValueCallbackFunction:func}
that.parseXml(options);
console.info(str);
// key:0 value:1 key:2 value:45 key:4 value:50 key:3 value:57 key:1 value:57
```

### getDepth

getDepth(): number

Obtains the depth of this element.

> **NOTE**
>
> The depth of the whitespace character event in the tag is the same as the depth of the tag.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type  | Description                |
| ------ | -------------------- |
| number | Nesting depth of the element (starting from 0), used to determine the XML hierarchy. |

**Example**

```ts
import { util } from '@kit.ArkTS';

let strXml =
  '<?xml version="1.0" encoding="utf-8"?>' +
  '<note importance="high">' +
    '<title>Happy</title>' +
  '</note>';
let textEncoder = new util.TextEncoder();
let arrBuffer = textEncoder.encodeInto(strXml);
let that = new xml.XmlPullParser(arrBuffer.buffer as object as ArrayBuffer);
let str = "";
function func(key: xml.EventType, value: xml.ParseInfo) {
  str += 'key:' + key + ' value:' + value.getDepth() + ' ';
  return true; // Determines whether to continue parsing, used to continue or terminate parsing.
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:true, tokenValueCallbackFunction:func}
that.parseXml(options);
console.info(str);
// key:0 value:0 key:2 value:1 key:2 value:2 key:4 value:2 key:3 value:2 key:3 value:1 key:1 value:0
```

### getLineNumber

getLineNumber(): number

Obtains the current line number, starting from 1.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type  | Description          |
| ------ | -------------- |
| number | Line number of the current element (starting from 1), used to locate the XML parsing position. |

**Example**

```ts
import { util } from '@kit.ArkTS';

let strXml = '<?xml version="1.0" encoding="utf-8"?><note>Work</note>';
let textEncoder = new util.TextEncoder();
let arrBuffer = textEncoder.encodeInto(strXml);
let that = new xml.XmlPullParser(arrBuffer.buffer as object as ArrayBuffer);
let str = "";
function func(key: xml.EventType, value: xml.ParseInfo) {
  str += 'key:' + key + ' value:' + value.getLineNumber() + ' ';
  return true; // Determine whether to continue parsing, used to continue or terminate parsing.
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:true, tokenValueCallbackFunction:func}
that.parseXml(options);
console.info(str);
// key:0 value:1 key:2 value:1 key:4 value:1 key:3 value:1 key:1 value:1
```

### getName

getName(): string

Obtains the name of this element.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type  | Description              |
| ------ | ------------------ |
| string | Name of the current element (excluding the namespace prefix), used to identify the XML element. |

**Example**

```ts
import { util } from '@kit.ArkTS';

let strXml = '<?xml version="1.0" encoding="utf-8"?><note>Happy</note>';
let textEncoder = new util.TextEncoder();
let arrBuffer = textEncoder.encodeInto(strXml);
let that = new xml.XmlPullParser(arrBuffer.buffer as object as ArrayBuffer);
let str = "";
function func(key: xml.EventType, value: xml.ParseInfo) {
  str += 'key:' + key + ' value:' + value.getName() + ' ';
  return true; // Determine whether to continue parsing, used to continue or terminate parsing.
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:true, tokenValueCallbackFunction:func}
that.parseXml(options);
console.info(str);
// key:0 value: key:2 value:note key:4 value: key:3 value:note key:1 value:
```
### getNamespace

getNamespace(): string

Obtains the namespace of this element.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| string | Namespace obtained.|

**Example**

```ts
import { util } from '@kit.ArkTS';

let strXml =
  '<?xml version="1.0" encoding="utf-8"?>' +
  '<note xmlns:h="http://www.w3.org">' +
    '<h:title>Happy</h:title>' +
  '</note>';
let textEncoder = new util.TextEncoder();
let arrBuffer = textEncoder.encodeInto(strXml);
let that = new xml.XmlPullParser(arrBuffer.buffer as object as ArrayBuffer);
let str = "";
function func(key: xml.EventType, value: xml.ParseInfo) {
  str += 'key:' + key + ' value:' + value.getNamespace() + ' ';
  return true; // Determine whether to continue parsing, used to continue or terminate parsing.
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:false, tokenValueCallbackFunction:func}
that.parseXml(options);
console.info(str);
// key:0 value: key:2 value: key:2 value:http://www.w3.org key:4 value: key:3 value:http://www.w3.org key:3 value: key:1 value:
```
### getPrefix

getPrefix(): string

Obtains the namespace prefix of the current element.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type  | Description              |
| ------ | ------------------ |
| string | Returns the namespace prefix of the current element. If the element has no namespace prefix, an empty string is returned. |

**Example**

```ts
import { util } from '@kit.ArkTS';

let strXml =
  '<?xml version="1.0" encoding="utf-8"?>' +
  '<note xmlns:h="http://www.w3.org/TR/html4">' +
    '<h:title>Happy</h:title>' +
  '</note>';
let textEncoder = new util.TextEncoder();
let arrBuffer = textEncoder.encodeInto(strXml);
let that = new xml.XmlPullParser(arrBuffer.buffer as object as ArrayBuffer);
let str = "";
function func(key: xml.EventType, value: xml.ParseInfo) {
  str += 'key:' + key + ' value:' + value.getPrefix() + ' ';
  return true; // Determines whether to continue parsing, used to continue or terminate parsing.
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:false, tokenValueCallbackFunction:func}
that.parseXml(options);
console.info(str);
// key:0 value: key:2 value: key:2 value:h key:4 value: key:3 value:h key:3 value: key:1 value:
```

### getText

getText(): string

Obtains the text of the current event.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| string | Text content of the current event (such as tag values, comments, etc.), used to obtain the parsed XML data. |

**Example**

```ts
import { util } from '@kit.ArkTS';

let strXml = '<?xml version="1.0" encoding="utf-8"?><note>Happy</note>';
let textEncoder = new util.TextEncoder();
let arrBuffer = textEncoder.encodeInto(strXml);
let that = new xml.XmlPullParser(arrBuffer.buffer as object as ArrayBuffer);
let str = "";
function func(key: xml.EventType, value: xml.ParseInfo) {
  str += 'key:' + key + ' value:' + value.getText() + ' ';
  return true; // Determines whether to continue parsing, used to continue or terminate parsing.
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:true, tokenValueCallbackFunction:func}
that.parseXml(options);
console.info(str);
// key:0 value: key:2 value: key:4 value:Happy key:3 value: key:1 value:
```
### isEmptyElementTag

isEmptyElementTag(): boolean

Checks whether the current element is empty.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type   | Description                        |
| ------- | ---------------------------- |
| boolean | If **true** is returned, the current element is empty. If **false** is returned, the current element is not empty.|

**Example**

```ts
import { util } from '@kit.ArkTS';

let strXml =
  '<?xml version="1.0" encoding="utf-8"?>' +
  '<note importance="high" logged="true">' +
    '<title/>' +
  '</note>';
let textEncoder = new util.TextEncoder();
let arrBuffer = textEncoder.encodeInto(strXml);
let that = new xml.XmlPullParser(arrBuffer.buffer as object as ArrayBuffer);
let str = "";
function func(key: xml.EventType, value: xml.ParseInfo) {
  str += 'key:' + key + ' value:' + value.isEmptyElementTag() + ' ';
  return true; // Determine whether to continue parsing, used to continue or terminate parsing.
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:true, tokenValueCallbackFunction:func}
that.parseXml(options);
console.info(str);
// key:0 value:false key:2 value:false key:2 value:true key:3 value:false key:3 value:false key:1 value:false
```
### isWhitespace

isWhitespace(): boolean

Checks whether the current event contains only whitespace characters.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type   | Description                                  |
| ------- | -------------------------------------- |
| boolean | Check result. The value **true** is returned if the text event contains only whitespace characters; otherwise, **false** is returned.|

**Example**

```ts
import { util } from '@kit.ArkTS';

let strXml =
  '<?xml version="1.0" encoding="utf-8"?>' +
  '<note importance="high" logged="true">' +
    '<title> </title>' +
  '</note>';
let textEncoder = new util.TextEncoder();
let arrBuffer = textEncoder.encodeInto(strXml);
let that = new xml.XmlPullParser(arrBuffer.buffer as object as ArrayBuffer);
let str = "";
function func(key: xml.EventType, value: xml.ParseInfo) {
  str += 'key:' + key + ' value:' + value.isWhitespace() + ' ';
  return true; // Determines whether to continue parsing, used to continue or terminate parsing.
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:true, tokenValueCallbackFunction:func}
that.parseXml(options);
console.info(str);
// key:0 value:true key:2 value:false key:2 value:true key:10 value:true key:3 value:true key:3 value:true key:1 value:true
```
### getAttributeCount

getAttributeCount(): number

Obtains the number of attributes in the current start tag.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Return value**
| Type  | Description                  |
| ------ | ---------------------- |
| number | Number of attributes of the current start tag, used to traverse and process XML attributes. |

**Example**

```ts
import { util } from '@kit.ArkTS';

let strXml = '<?xml version="1.0" encoding="utf-8"?><note importance="high" logged="true"/>';
let textEncoder = new util.TextEncoder();
let arrBuffer = textEncoder.encodeInto(strXml);
let that = new xml.XmlPullParser(arrBuffer.buffer as object as ArrayBuffer);
let str = "";
function func(key: xml.EventType, value: xml.ParseInfo) {
  str += 'key:' + key + ' value:' + value.getAttributeCount() + ' ';
  return true; // Determine whether to continue parsing, used to continue or terminate parsing.
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:true, tokenValueCallbackFunction:func}
that.parseXml(options);
console.info(str);
// key:0 value:0 key:2 value:2 key:3 value:2 key:1 value:0
```

## EventType

Event type enumeration, which defines the various events that XmlPullParser may trigger during XML parsing. During parsing, events are triggered in sequence such as START_DOCUMENT→START_TAG→TEXT/CDSECT→END_TAG→END_DOCUMENT. Developers can receive the corresponding events through the tokenValueCallbackFunction callback.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

| Name            | Value  | Description                 |
| ---------------- | ---- | --------------------- |
| START_DOCUMENT   | 0    | Start document event.       |
| END_DOCUMENT     | 1    | End document event.       |
| START_TAG        | 2    | Start tag event.       |
| END_TAG          | 3    | End tag event.       |
| TEXT             | 4    | Text event.           |
| CDSECT           | 5    | CDATA section event.          |
| COMMENT          | 6    | XML comment event.        |
| DOCDECL          | 7    | XML document type declaration event.|
| INSTRUCTION      | 8    | XML processing instruction event.|
| ENTITY_REFERENCE | 9    | Entity reference event.       |
| WHITESPACE       | 10   | Whitespace character event.           |

## XmlSAXParser<sup>24+</sup>

The XmlSAXParser class is used to parse XML text in streaming mode. It is suitable for scenarios where data needs to be read and processed simultaneously, and supports reading XML data from a [stream.Readable](js-apis-stream.md#readable) stream for parsing.

> **NOTE**
>
> - This API uses streaming parsing and can theoretically parse XML text of any size. However, considering actual performance, it is recommended that the data size of a single parse not exceed 300 MB to avoid excessively long parsing time that affects user experience.

### constructor<sup>24+</sup>

constructor(inputStream: stream.Readable, encoding?: string)

Constructs and returns an XmlSAXParser object for streaming XML text parsing from a readable stream in SAX mode.

> **NOTE**
>
> - The `inputStream` parameter must be a class that inherits from [Readable](js-apis-stream.md#readable) and implements [doRead](js-apis-stream.md#doread). You can pass in a class from another module that meets this condition, such as [ReadStream](../apis-core-file-kit/js-apis-file-fs.md#readstream12).


**Atomic service API**: This API can be used in atomic services since API version 24.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name       | Type             | Mandatory | Description                                             |
| ---------- | ---------------- | --------- | ------------------------------------------------------- |
| inputStream  | [stream.Readable](js-apis-stream.md#readable)  | Yes   | Readable stream instance used to read XML data.                    |
| encoding     | string           | No   | Encoding format. The default value is 'utf-8' (currently only 'utf-8' is supported).     |

**Example**

```ts
import { xml, stream } from '@kit.ArkTS';

class TestReadable extends stream.Readable {
  constructor() {
    super();
  }

  doRead(size: number) {
  }
}

let readableStream = new TestReadable();
let saxParser = new xml.XmlSAXParser(readableStream, 'utf-8');
```

### parse<sup>24+</sup>

parse(xmlSAXHandler: XmlSAXHandler): void

Parses XML data using SAX (Simple API for XML).

> **NOTE**
>
> - After the parse function is called, you can control the parsing progress through control flow. After any data block is pushed in, the parser parses the corresponding progress. For details about the stream control method, see [@ohos.util.stream (Data Stream Base Class stream)](js-apis-stream.md).
> - It can be used with streams that automatically control data, such as [ReadStream](../apis-core-file-kit/js-apis-file-fs.md#readstream12). In this case, you no longer need to manually control the data.
> - The parse API registers the on listener of the stream and automatically reads data from the stream. It is not recommended to operate the stream listener or read data again, to avoid conflicts that may cause the API capability to fail.

**Atomic service API**: This API can be used in atomic services since API version 24.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name         | Type                               | Mandatory | Description                    |
| -------------- | ---------------------------------- | ---- | ----------------------- |
| xmlSAXHandler  | [XmlSAXHandler](#xmlsaxhandler24)  | Yes   | SAX handler object.         |

**Example**

```ts
import { xml, stream } from '@kit.ArkTS';

class TestReadable extends stream.Readable {
  constructor() {
    super();
  }

  doRead(size: number) {
  }
}

let readableStream = new TestReadable();
let saxParser = new xml.XmlSAXParser(readableStream);

let handler: xml.XmlSAXHandler = {
  startDocument: () => {
  },
  endDocument: () => {
  },
  startElement: (elementName: string, namespaceURI: string | undefined, qName: string | undefined,
    attributes: Map<string, string>) => {
  },
  endElement: (elementName: string, namespaceURI: string | undefined, qName: string | undefined) => {
  },
  characters: (content: string) => {
  }
};

saxParser.parse(handler);
```

## XmlSAXHandler<sup>24+</sup>

XmlSAXHandler defines the callback methods for SAX parsing of XML text. Developers need to implement these callback methods to process different parts of the XML text. These callback methods are triggered at the corresponding stages of the XML parsing process. startDocument is triggered when document parsing begins, endDocument is triggered when document parsing ends, startElement is triggered when element parsing begins, endElement is triggered when element parsing ends, and characters is triggered when parsing text content between elements.

### startDocument<sup>24+</sup>

startDocument(): void

Callback function triggered when the parser starts parsing the XML text. This callback function needs to be implemented by the developer. For a specific usage example, see [characters<sup>24+</sup>](#characters24).

**Atomic service API**: This API can be used in atomic services since API version 24.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Utils.Lang

### endDocument<sup>24+</sup>

endDocument(): void

Callback function triggered when the parser finishes parsing the XML text. This callback function needs to be implemented by the developer. For a specific usage example, see [characters<sup>24+</sup>](#characters24).

> **NOTE**
>
> This callback is triggered when the readable stream ends. Call push() in the stream and pass in a null value to trigger this callback.

**Atomic service API**: This API can be used in atomic services since API version 24.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Utils.Lang

### startElement<sup>24+</sup>

startElement(elementName: string, namespaceURI: string | undefined, qName: string | undefined, attributes: Map<string, string>): void

Callback function triggered when the parser encounters the start tag of an XML element. This callback function needs to be implemented by the developer. For a specific usage example, see [characters<sup>24+</sup>](#characters24).

**Atomic service API**: This API can be used in atomic services since API version 24.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name          | Type                      | Mandatory | Description                                   |
| ------------- | ------------------------- | ---- | -------------------------------------- |
| elementName   | string                    | Yes   | Element name returned by the parser (excluding the namespace prefix). For example, for `<ns2:child>`, elementName is "child". |
| namespaceURI  | string \| undefined       | Yes   | Namespace URI returned by the parser. For example, for `xmlns:ns2="http://example.com/ns2"`, namespaceURI is `"http://example.com/ns2"`. If the element has no namespace, it is undefined. |
| qName        | string \| undefined       | Yes   | Qualified name of the element returned by the parser (including the namespace prefix). For example, for `<ns2:child>`, qName is "ns2:child". If the element has no namespace, qName is undefined. |
| attributes    | Map<string, string>       | Yes   | Attribute map of the element returned by the parser, where the key is the attribute name (which may include a namespace prefix, such as "ns2:attrA") and the value is the attribute value. |

### endElement<sup>24+</sup>

endElement(elementName: string, namespaceURI: string | undefined, qName: string | undefined): void

Callback function triggered when the parser encounters the end tag of an XML element. This callback function needs to be implemented by the developer. For a specific usage example, see [characters<sup>24+</sup>](#characters24).

**Atomic service API**: This API can be used in atomic services since API version 24.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name        | Type                      | Mandatory | Description                                   |
| ------------- | ------------------------- | ---- | -------------------------------------- |
| elementName   | string                    | Yes   | Element name returned by the parser (excluding the namespace prefix). For example, for `<ns2:child>`, elementName is "child". |
| namespaceURI  | string \| undefined       | Yes   | Namespace URI returned by the parser. For example, for `xmlns:ns2="http://example.com/ns2"`, namespaceURI is `"http://example.com/ns2"`. If the element has no namespace, it is undefined. |
| qName        | string \| undefined       | Yes   | Qualified name of the element returned by the parser (including the namespace prefix). For example, for `<ns2:child>`, qName is "ns2:child". If the element has no namespace, qName is undefined. |

### characters<sup>24+</sup>

characters(content: string): void

Callback function invoked when the parser encounters text content inside an XML element. This callback function must be implemented by the developer.

**Atomic service API**: This API can be used in atomic services since API version 24.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name    | Type   | Mandatory | Description             |
| ------- | ------ | --------- | ----------------------- |
| content | string | Yes       | Text content within the element returned by the parser. |

**Example**

```ts
import { xml, stream } from '@kit.ArkTS';

class TestReadable extends stream.Readable {
  constructor() {
    super();
  }

  doRead(size: number) {
  }
}

const saxHandler: xml.XmlSAXHandler = {
  startDocument() {
    console.info("startDocument");
  },
  endDocument() {
    console.info("endDocument");
  },
  startElement(elementName: string, namespaceURI: string | undefined, qName: string | undefined,
    attributes: Map<string, string>) {
    console.info("startElement elementName:", elementName);
    console.info("startElement namespaceURI:", namespaceURI);
    console.info("startElement qName:", qName);
    if (attributes) {
      attributes.forEach((value, key) => {
        console.info("startElement attribute:", key, "=", value);
      });
    }
  },
  endElement(elementName: string, namespaceURI: string | undefined, qName: string | undefined) {
    console.info("endElement elementName:", elementName);
  },
  characters(content: string) {
    console.info("characters:", content);
  }
};

let readableStream = new TestReadable();
let saxParser = new xml.XmlSAXParser(readableStream);
saxParser.parse(saxHandler);

let testData = '<?xml version="1.0" encoding="UTF-8"?>\n' +
  '<root xmlns:ns1="http://example.com/ns1">\n' +
  '  <ns1:child ns1:attr1="value1" attr2="value2">Text content</ns1:child>\n' +
  '</root>';

readableStream.push(testData);
readableStream.push(null);
// Output example:
// startDocument
// startElement elementName: root
// startElement namespaceURI: undefined
// startElement qName: undefined
// characters: 
// 
// startElement elementName: child
// startElement namespaceURI: http://example.com/ns1
// startElement qName: ns1:child
// startElement attribute: attr2 = value2
// startElement attribute: ns1:attr1 = value1
// characters: Text content
// endElement elementName: child
// characters: 
// endElement elementName: root
// endDocument
```