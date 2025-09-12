# @ohos.xml (XML Parsing and Generation)

The xml module provides APIs for generating and parsing XML files.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import

```
import { xml } from '@kit.ArkTS';
```

## XmlSerializer

**XmlSerializer** provides APIs to generate an XML file.

### constructor

constructor(buffer: ArrayBuffer | DataView, encoding?: string)

A constructor used to create an **XmlSerializer** instance.

> **NOTE**
>
> The buffer is used to temporarily store XML text generated. Its size can be customized. Ensure that the buffer is large enough to hold the generated text.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name  | Type                             | Mandatory| Description                                            |
| -------- | --------------------------------- | ---- | ------------------------------------------------ |
| buffer   | ArrayBuffer \| DataView | Yes  | ArrayBuffer or DataView for storing the XML information to set.|
| encoding | string                            | No  | Encoding format. The default value is **'utf-8'** (the only format currently supported).              |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
let arrayBuffer = new ArrayBuffer(2048);
let thatSer = new xml.XmlSerializer(arrayBuffer, "utf-8");
```

### setAttributes

setAttributes(name: string, value: string): void

Sets an attribute.

> **NOTE**
>
> This API does not perform standard XML verification on the data to add. Ensure that the data complies with the XML specifications. For example, as stipulated in the specifications, you are not allowed to add an attribute name starting with a digit or add multiple attributes with the same name.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description           |
| ------ | ------ | ---- | --------------- |
| name   | string | Yes  | Key of the attribute.  |
| value  | string | Yes  | Value of the attribute.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

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
console.log(result); // <note importance="high"/>
```

### addEmptyElement

addEmptyElement(name: string): void

Adds an empty element.

> **NOTE**
>
> This API does not perform standard XML verification on the data to add. Ensure that the data complies with the XML specifications. For example, as stipulated in the specifications, you are not allowed to add an attribute name starting with a digit.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description              |
| ------ | ------ | ---- | ------------------ |
| name   | string | Yes  | Name of the element.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { util } from '@kit.ArkTS';

let arrayBuffer = new ArrayBuffer(2048);
let thatSer = new xml.XmlSerializer(arrayBuffer);
thatSer.addEmptyElement("d");
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.log(result); // <d/>
```

### setDeclaration

setDeclaration(): void

Sets a file declaration.

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
console.log(result);
// <?xml version="1.0" encoding="utf-8"?>
```

### startElement

startElement(name: string): void

Adds the start tag based on the given element name.

> **NOTE**
>
>- After calling this API, you must call [endElement](#endelement) to write the end flag to ensure that the node is closed correctly.
>
>- This API does not perform standard XML verification on the data to add. Ensure that the data complies with the XML specifications. For example, as stipulated in the specifications, you are not allowed to add an attribute name starting with a digit.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description              |
| ------ | ------ | ---- | ------------------ |
| name   | string | Yes  | Name of the element.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

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
console.log(result);
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
console.log(result);
// <note>Happy</note>
```

### setNamespace

setNamespace(prefix: string, namespace: string): void

Sets the namespace for an element tag.

> **NOTE**
>
> This API does not perform standard XML verification on the data to add. Ensure that the data complies with the XML specifications. For example, as stipulated in the specifications, you are not allowed to add a namespace starting with a digit or set multiple namespaces for the same element.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name   | Type  | Mandatory| Description                          |
| --------- | ------ | ---- | ------------------------------ |
| prefix    | string | Yes  | Prefix of the element and its child elements.    |
| namespace | string | Yes  | Namespace to set.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

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
console.log(result);
// <h:note xmlns:h="http://www.w3.org/TR/html4/"/>
```

### setComment

setComment(text: string): void

Sets a comment.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description                |
| ------ | ------ | ---- | -------------------- |
| text   | string | Yes  | Comment to set.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { util } from '@kit.ArkTS';

let arrayBuffer = new ArrayBuffer(2048);
let thatSer = new xml.XmlSerializer(arrayBuffer);
thatSer.setComment("Hello, World!");
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.log(result); // <!--Hello, World!-->
```

### setCDATA

setCDATA(text: string): void

Adds data to the CDATA tag. The structure of the generated CDATA tag is "\<! <![CDATA\["+ Data added + "\]\]\>".

> **NOTE**
>
> This API does not perform standard XML verification on the data to add. Ensure that the data complies with the XML specifications. For example, as stipulated in the specifications, you are not allowed to add data that contains the string \]\]\> to the CDATA tag.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description             |
| ------ | ------ | ---- | ----------------- |
| text   | string | Yes  | CDATA data to set.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { util } from '@kit.ArkTS';

let arrayBuffer = new ArrayBuffer(2048);
let thatSer = new xml.XmlSerializer(arrayBuffer);
thatSer.setCDATA('root SYSTEM')
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.log(result); // <![CDATA[root SYSTEM]]>
```

### setText

setText(text: string): void

Sets a tag value.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description            |
| ------ | ------ | ---- | ---------------- |
| text   | string | Yes  | Tag value to set, which is the content of the **text** attribute.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

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
console.log(result); // <note importance="high">Happy</note>
```

### setDocType

setDocType(text: string): void

Sets a document type.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description               |
| ------ | ------ | ---- | ------------------- |
| text   | string | Yes  | Content of **DocType** to set.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { util } from '@kit.ArkTS';

let arrayBuffer = new ArrayBuffer(2048);
let thatSer = new xml.XmlSerializer(arrayBuffer);
thatSer.setDocType('root SYSTEM "http://www.test.org/test.dtd"');
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.log(result); // <!DOCTYPE root SYSTEM "http://www.test.org/test.dtd">
```

## XmlPullParser

Implements XML file parsing.

### constructor

constructor(buffer: ArrayBuffer | DataView, encoding?: string)

Creates and returns an **XmlPullParser** object.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name  | Type                             | Mandatory| Description                                      |
| -------- | --------------------------------- | ---- | ------------------------------------------ |
| buffer   | ArrayBuffer \| DataView | Yes  | XML text information to be parsed.|
| encoding | string                            | No  | Encoding format. The default value is **'utf-8'** (the only format currently supported).        |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { util } from '@kit.ArkTS';

let strXml = '<title>Happy</title>'
let textEncoder = new util.TextEncoder();
let uint8Array = textEncoder.encodeInto(strXml);
let that = new xml.XmlPullParser(uint8Array.buffer as object as ArrayBuffer, 'UTF-8');
```

### parseXml<sup>14+</sup>

parseXml(option: ParseOptions): void

Parses XML information.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type                         | Mandatory| Description         |
| ------ | ----------------------------- | ---- | ------------- |
| option | [ParseOptions](#parseoptions) | Yes  | XML parsing options.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**
For details, see [Parsing XML Tags and Values](../../arkts-utils/xml-parsing.md#parsing-xml-tags-and-values) and [Parsing XML Attributes and Values](../../arkts-utils/xml-parsing.md#parsing-xml-attributes-and-values).

```ts
import { xml, util } from '@kit.ArkTS';

let strxml =
  '<?xml version="1.0" encoding="utf-8"?>' +
    '<note importance="high" logged="true">' +
    '    <title><![CDATA[Test\nTest]]></title>' +
    '</note>';
let textEncoder = new util.TextEncoder();
let uint8 = textEncoder.encodeInto(strxml);

function func(key: xml.EventType, value: xml.ParseInfo) {
  if (key == xml.EventType.CDSECT) {
    console.log(JSON.stringify(value.getText()));
  }
  return true;
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:true, tokenValueCallbackFunction:func}
let pullParser = new xml.XmlPullParser(uint8.buffer as object as ArrayBuffer);
pullParser.parseXml(options);
// "Test\nTest"
```

### parse<sup>(deprecated)</sup>

parse(option: ParseOptions): void

Parses XML information.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 14. You are advised to use [parseXml<sup>14+</sup>](#parsexml14) instead.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type                         | Mandatory| Description                            |
| ------ | ----------------------------- | ---- | -------------------------------- |
| option | [ParseOptions](#parseoptions) | Yes  | XML parsing options.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

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
let arrbuffer = textEncoder.encodeInto(strXml);
let that = new xml.XmlPullParser(arrbuffer.buffer as object as ArrayBuffer, 'UTF-8');
let str = '';
function func(name: string, value: string) {
  str = name + value;
  console.log(str);
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

## ParseOptions

Defines the XML parsing options.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang


| Name                          | Type                                                        | Mandatory| Description                                   |
| ------------------------------ | ------------------------------------------------------------ | ---- | --------------------------------------- |
| supportDoctype                 | boolean                                                      | No  | Whether to parse the document type. The value **true** means to parse the document type, and **false** means the opposite. The default value is **false**.|
| ignoreNameSpace                | boolean                                                      | No  | Whether to ignore the namespace. If the namespace is ignored, it will not be parsed. The value **true** means to ignore the namespace, and **false** means the opposite. The default value is **false**.|
| tagValueCallbackFunction       | (name: string, value: string) =&gt; boolean | No  | Start tag, tag value, and end tag of parsing. The default value is **undefined**, indicating no parsing.|
| attributeValueCallbackFunction | (name: string, value: string) =&gt; boolean | No  | Parsing attribute and attribute value. The default value is **undefined**, indicating no parsing.|
| tokenValueCallbackFunction     | (eventType: [EventType](#eventtype), value: [ParseInfo](#parseinfo)) =&gt; boolean | No  | Parsing element's [EventType](#eventtype) and [ParseInfo](#parseinfo). The default value is **undefined**, indicating no parsing.|

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
| number | Column number obtained.|

**Example**

```ts
import { util } from '@kit.ArkTS';

let strXml = '<?xml version="1.0" encoding="utf-8"?><note>Happy</note>';
let textEncoder = new util.TextEncoder();
let arrbuffer = textEncoder.encodeInto(strXml);
let that = new xml.XmlPullParser(arrbuffer.buffer as object as ArrayBuffer);
let str = "";
function func(key: xml.EventType, value: xml.ParseInfo) {
  str += 'key:' + key + ' value:' + value.getColumnNumber() + ' ';
  return true; // Determines whether to continually parse, which is used to continue or terminate parsing.
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:true, tokenValueCallbackFunction:func}
that.parseXml(options);
console.log(str);
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
| number | Depth obtained.|

**Example**

```ts
import { util } from '@kit.ArkTS';

let strXml =
  '<?xml version="1.0" encoding="utf-8"?>' +
  '<note importance="high">' +
    '<title>Happy</title>' +
  '</note>';
let textEncoder = new util.TextEncoder();
let arrbuffer = textEncoder.encodeInto(strXml);
let that = new xml.XmlPullParser(arrbuffer.buffer as object as ArrayBuffer);
let str = "";
function func(key: xml.EventType, value: xml.ParseInfo) {
  str += 'key:' + key + ' value:' + value.getDepth() + ' ';
  return true; // Determines whether to continually parse, which is used to continue or terminate parsing.
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:true, tokenValueCallbackFunction:func}
that.parseXml(options);
console.log(str);
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
| number | Line number obtained.|

**Example**

```ts
import { util } from '@kit.ArkTS';

let strXml = '<?xml version="1.0" encoding="utf-8"?><note>Work</note>';
let textEncoder = new util.TextEncoder();
let arrbuffer = textEncoder.encodeInto(strXml);
let that = new xml.XmlPullParser(arrbuffer.buffer as object as ArrayBuffer);
let str = "";
function func(key: xml.EventType, value: xml.ParseInfo) {
  str += 'key:' + key + ' value:' + value.getLineNumber() + ' ';
  return true; // Determines whether to continually parse, which is used to continue or terminate parsing.
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:true, tokenValueCallbackFunction:func}
that.parseXml(options);
console.log(str);
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
| string | Element name obtained.|

**Example**

```ts
import { util } from '@kit.ArkTS';

let strXml = '<?xml version="1.0" encoding="utf-8"?><note>Happy</note>';
let textEncoder = new util.TextEncoder();
let arrbuffer = textEncoder.encodeInto(strXml);
let that = new xml.XmlPullParser(arrbuffer.buffer as object as ArrayBuffer);
let str = "";
function func(key: xml.EventType, value: xml.ParseInfo) {
  str += 'key:' + key + ' value:' + value.getName() + ' ';
  return true; // Determines whether to continually parse, which is used to continue or terminate parsing.
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:true, tokenValueCallbackFunction:func}
that.parseXml(options);
console.log(str);
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
let arrbuffer = textEncoder.encodeInto(strXml);
let that = new xml.XmlPullParser(arrbuffer.buffer as object as ArrayBuffer);
let str = "";
function func(key: xml.EventType, value: xml.ParseInfo) {
  str += 'key:' + key + ' value:' + value.getNamespace() + ' ';
  return true; // Determines whether to continually parse, which is used to continue or terminate parsing.
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:false, tokenValueCallbackFunction:func}
that.parseXml(options);
console.log(str);
// key:0 value: key:2 value: key:2 value:http://www.w3.org key:4 value: key:3 value:http://www.w3.org key:3 value: key:1 value:
```
### getPrefix

getPrefix(): string

Obtains the prefix of this element.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type  | Description              |
| ------ | ------------------ |
| string | Element prefix obtained.|

**Example**

```ts
import { util } from '@kit.ArkTS';

let strXml =
  '<?xml version="1.0" encoding="utf-8"?>' +
  '<note xmlns:h="http://www.w3.org/TR/html4">' +
    '<h:title>Happy</h:title>' +
  '</note>';
let textEncoder = new util.TextEncoder();
let arrbuffer = textEncoder.encodeInto(strXml);
let that = new xml.XmlPullParser(arrbuffer.buffer as object as ArrayBuffer);
let str = "";
function func(key: xml.EventType, value: xml.ParseInfo) {
  str += 'key:' + key + ' value:' + value.getPrefix() + ' ';
  return true; // Determines whether to continually parse, which is used to continue or terminate parsing.
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:false, tokenValueCallbackFunction:func}
that.parseXml(options);
console.log(str);
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
| string | Text content obtained.|

**Example**

```ts
import { util } from '@kit.ArkTS';

let strXml = '<?xml version="1.0" encoding="utf-8"?><note>Happy</note>';
let textEncoder = new util.TextEncoder();
let arrbuffer = textEncoder.encodeInto(strXml);
let that = new xml.XmlPullParser(arrbuffer.buffer as object as ArrayBuffer);
let str = "";
function func(key: xml.EventType, value: xml.ParseInfo) {
  str += 'key:' + key + ' value:' + value.getText() + ' ';
  return true; // Determines whether to continually parse, which is used to continue or terminate parsing.
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:true, tokenValueCallbackFunction:func}
that.parseXml(options);
console.log(str);
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
| boolean | If **true** is returned, the current element is empty.|

**Example**

```ts
import { util } from '@kit.ArkTS';

let strXml =
  '<?xml version="1.0" encoding="utf-8"?>' +
  '<note importance="high" logged="true">' +
    '<title/>' +
  '</note>';
let textEncoder = new util.TextEncoder();
let arrbuffer = textEncoder.encodeInto(strXml);
let that = new xml.XmlPullParser(arrbuffer.buffer as object as ArrayBuffer);
let str = "";
function func(key: xml.EventType, value: xml.ParseInfo) {
  str += 'key:' + key + ' value:' + value.isEmptyElementTag() + ' ';
  return true; // Determines whether to continually parse, which is used to continue or terminate parsing.
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:true, tokenValueCallbackFunction:func}
that.parseXml(options);
console.log(str);
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
| boolean | Check result. The value **true** is returned if the text event contains only whitespace characters.|

**Example**

```ts
import { util } from '@kit.ArkTS';

let strXml =
  '<?xml version="1.0" encoding="utf-8"?>' +
  '<note importance="high" logged="true">' +
    '<title> </title>' +
  '</note>';
let textEncoder = new util.TextEncoder();
let arrbuffer = textEncoder.encodeInto(strXml);
let that = new xml.XmlPullParser(arrbuffer.buffer as object as ArrayBuffer);
let str = "";
function func(key: xml.EventType, value: xml.ParseInfo) {
  str += 'key:' + key + ' value:' + value.isWhitespace() + ' ';
  return true; // Determines whether to continually parse, which is used to continue or terminate parsing.
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:true, tokenValueCallbackFunction:func}
that.parseXml(options);
console.log(str);
// key:0 value:true key:2 value:false key:2 value:true key:10 value:true key:3 value:true key:3 value:true key:1 value:true
```
### getAttributeCount

getAttributeCount(): number

Obtains the number of attributes for the current start tag.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Return value**
| Type  | Description                  |
| ------ | ---------------------- |
| number | Number of attributes obtained.|

**Example**

```ts
import { util } from '@kit.ArkTS';

let strXml = '<?xml version="1.0" encoding="utf-8"?><note importance="high" logged="true"/>';
let textEncoder = new util.TextEncoder();
let arrbuffer = textEncoder.encodeInto(strXml);
let that = new xml.XmlPullParser(arrbuffer.buffer as object as ArrayBuffer);
let str = "";
function func(key: xml.EventType, value: xml.ParseInfo) {
  str += 'key:' + key + ' value:' + value.getAttributeCount() + ' ';
  return true; // Determines whether to continually parse, which is used to continue or terminate parsing.
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:true, tokenValueCallbackFunction:func}
that.parseXml(options);
console.log(str);
// key:0 value:0 key:2 value:2 key:3 value:2 key:1 value:0
```

## EventType

Enumerates the event types.

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
