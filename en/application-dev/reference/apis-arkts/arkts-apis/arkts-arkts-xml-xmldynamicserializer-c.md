# XmlDynamicSerializer

The XmlDynamicSerializer interface is used to dynamically generate an xml file.

**Since:** 20

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { xml } from '@kit.ArkTS';
```

## addEmptyElement

```TypeScript
addEmptyElement(name: string): void
```

Add an empty element.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the element. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200062](../errorcode-utils.md#10200062-xml-cumulative-length-exceeded) | The cumulative length of xml has exceeded the upper limit 100000. |
| [10200064](../errorcode-utils.md#10200064-input-string-cannot-be-empty) | Cannot be an empty string. |

**Examples**

```TypeScript
import { util } from '@kit.ArkTS';

let serializer = new xml.XmlDynamicSerializer('utf-8');
serializer.addEmptyElement("d");
let arrayBuffer = serializer.getOutput();
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <d/>
```

## constructor

```TypeScript
constructor(encoding?: string)
```

A parameterized constructor used to create a new XmlDynamicSerializer instance. The input parameter is an encoding format of string type.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| encoding | string | No | [encoding='utf8'] this is its encoding, only support utf-8. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200066](../errorcode-utils.md#10200066-incorrect-encoding-format) | Incorrect encoding format, only support utf-8. |

**Examples**

```TypeScript
let serializer = new xml.XmlDynamicSerializer('utf-8');
```

## endElement

```TypeScript
endElement(): void
```

Writes end tag of the element.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200062](../errorcode-utils.md#10200062-xml-cumulative-length-exceeded) | The cumulative length of xml has exceeded the upper limit 100000. |
| [10200065](../errorcode-utils.md#10200065-mismatched-element-start-and-end-tags) | There is no match between the startElement and the endElement. |

**Examples**

```TypeScript
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

## getOutput

```TypeScript
getOutput(): ArrayBuffer
```

Get an ArrayBuffer from a XmlDynamicSerializer instance.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| ArrayBuffer | Returns ArrayBuffer result from a XmlDynamicSerializer instance. |

**Examples**

```TypeScript
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

## setAttributes

```TypeScript
setAttributes(name: string, value: string): void
```

Write an attribute to xml element.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Key name of the attribute. Cannot be an empty string. |
| value | string | Yes | Values of attribute. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200062](../errorcode-utils.md#10200062-xml-cumulative-length-exceeded) | The cumulative length of xml has exceeded the upper limit 100000. |
| [10200063](../errorcode-utils.md#10200063-xml-declaration-or-attribute-position-error) | Illegal position for xml. |
| [10200064](../errorcode-utils.md#10200064-input-string-cannot-be-empty) | Cannot be an empty string. |

**Examples**

```TypeScript
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

## setCdata

```TypeScript
setCdata(text: string): void
```

Writes the CDATA.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Values of CDATA. Cannot be an empty string. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200062](../errorcode-utils.md#10200062-xml-cumulative-length-exceeded) | The cumulative length of xml has exceeded the upper limit 100000. |
| [10200064](../errorcode-utils.md#10200064-input-string-cannot-be-empty) | Cannot be an empty string. |

**Examples**

```TypeScript
import { util } from '@kit.ArkTS';

let serializer = new xml.XmlDynamicSerializer('utf-8');
serializer.setCdata('root SYSTEM')
let arrayBuffer = serializer.getOutput();
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <![CDATA[root SYSTEM]]>
```

## setComment

```TypeScript
setComment(text: string): void
```

Writes the comment to xml.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Values of comment. Cannot be an empty string. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200062](../errorcode-utils.md#10200062-xml-cumulative-length-exceeded) | The cumulative length of xml has exceeded the upper limit 100000. |
| [10200064](../errorcode-utils.md#10200064-input-string-cannot-be-empty) | Cannot be an empty string. |

**Examples**

```TypeScript
import { util } from '@kit.ArkTS';

let serializer = new xml.XmlDynamicSerializer('utf-8');
serializer.setComment("Hello, World!");
let arrayBuffer = serializer.getOutput();
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <!--Hello, World!-->
```

## setDeclaration

```TypeScript
setDeclaration(): void
```

Writes xml declaration with encoding. For example: &lt;?xml version="1.0" encoding="utf-8"?&gt;.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200062](../errorcode-utils.md#10200062-xml-cumulative-length-exceeded) | The cumulative length of xml has exceeded the upper limit 100000. |
| [10200063](../errorcode-utils.md#10200063-xml-declaration-or-attribute-position-error) | Illegal position for xml. |

**Examples**

```TypeScript
import { util } from '@kit.ArkTS';

let serializer = new xml.XmlDynamicSerializer('utf-8');
serializer.setDeclaration();
let arrayBuffer = serializer.getOutput();
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <?xml version="1.0" encoding="utf-8"?>
```

## setDocType

```TypeScript
setDocType(text: string): void
```

Writes the DOCTYPE.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Values of docType. Cannot be an empty string. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200062](../errorcode-utils.md#10200062-xml-cumulative-length-exceeded) | The cumulative length of xml has exceeded the upper limit 100000. |
| [10200064](../errorcode-utils.md#10200064-input-string-cannot-be-empty) | Cannot be an empty string. |

**Examples**

```TypeScript
import { util } from '@kit.ArkTS';

let serializer = new xml.XmlDynamicSerializer('utf-8');
serializer.setDocType('root SYSTEM "http://www.test.org/test.dtd"');
let arrayBuffer = serializer.getOutput();
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <!DOCTYPE root SYSTEM "http://www.test.org/test.dtd">
```

## setNamespace

```TypeScript
setNamespace(prefix: string, namespace: string): void
```

Writes the namespace of the current element tag.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| prefix | string | Yes | Values name of the prefix. Cannot be an empty string. |
| namespace | string | Yes | Values of namespace. Cannot be an empty string. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200062](../errorcode-utils.md#10200062-xml-cumulative-length-exceeded) | The cumulative length of xml has exceeded the upper limit 100000. |
| [10200064](../errorcode-utils.md#10200064-input-string-cannot-be-empty) | Cannot be an empty string. |

**Examples**

```TypeScript
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

## setText

```TypeScript
setText(text: string): void
```

Writes the text to xml element.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Values of text. Cannot be an empty string. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200062](../errorcode-utils.md#10200062-xml-cumulative-length-exceeded) | The cumulative length of xml has exceeded the upper limit 100000. |
| [10200064](../errorcode-utils.md#10200064-input-string-cannot-be-empty) | Cannot be an empty string. |

**Examples**

```TypeScript
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

## startElement

```TypeScript
startElement(name: string): void
```

Writes a element start tag with the given name.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the element. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200062](../errorcode-utils.md#10200062-xml-cumulative-length-exceeded) | The cumulative length of xml has exceeded the upper limit 100000. |
| [10200064](../errorcode-utils.md#10200064-input-string-cannot-be-empty) | Cannot be an empty string. |

**Examples**

```TypeScript
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
