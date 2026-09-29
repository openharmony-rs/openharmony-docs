# XmlSerializer

```TypeScript
class XmlSerializer
```

The XmlSerializer interface is used to generate an xml file.

**Since:** 8

<!--Device-xml-class XmlSerializer--><!--Device-xml-class XmlSerializer-End-->

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { xml } from '@kit.ArkTS';
```

## addEmptyElement

```TypeScript
addEmptyElement(name: string): void
```

Adds an empty element.

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-XmlSerializer-addEmptyElement(name: string): void--><!--Device-XmlSerializer-addEmptyElement(name: string): void-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the empty element to add. |

**Examples**

```TypeScript
import { util } from '@kit.ArkTS';

let arrayBuffer = new ArrayBuffer(2048);
let thatSer = new xml.XmlSerializer(arrayBuffer);
thatSer.addEmptyElement("d");
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <d/>
```

## constructor

```TypeScript
constructor(buffer: ArrayBuffer | DataView, encoding?: string)
```

A constructor used to create an XmlSerializer instance.

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-XmlSerializer-constructor(buffer: ArrayBuffer | DataView, encoding?: string)--><!--Device-XmlSerializer-constructor(buffer: ArrayBuffer | DataView, encoding?: string)-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buffer | ArrayBuffer &#124; DataView | Yes | ArrayBuffer or DataView for storing the XML information to set. |
| encoding | string | No | Encoding format. The default value is 'utf-8' (the only format currently supported). |

**Examples**

```TypeScript
let arrayBuffer = new ArrayBuffer(2048);
let thatSer = new xml.XmlSerializer(arrayBuffer, "utf-8");
```

## endElement

```TypeScript
endElement(): void
```

Writes the end tag of the element.

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-XmlSerializer-endElement(): void--><!--Device-XmlSerializer-endElement(): void-End-->

**System capability:** SystemCapability.Utils.Lang

**Examples**

```TypeScript
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

## setAttributes

```TypeScript
setAttributes(name: string, value: string): void
```

Sets an attribute.

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-XmlSerializer-setAttributes(name: string, value: string): void--><!--Device-XmlSerializer-setAttributes(name: string, value: string): void-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Key of the attribute. |
| value | string | Yes | Value of the attribute. |

**Examples**

```TypeScript
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

## setCDATA

```TypeScript
setCDATA(text: string): void
```

Adds data to the CDATA tag. The structure of the generated CDATA tag is "&lt;! &lt;![CDATA["+ Data added + "]]&gt;".

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-XmlSerializer-setCDATA(text: string): void--><!--Device-XmlSerializer-setCDATA(text: string): void-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | CDATA data to set. |

**Examples**

```TypeScript
import { util } from '@kit.ArkTS';

let arrayBuffer = new ArrayBuffer(2048);
let thatSer = new xml.XmlSerializer(arrayBuffer);
thatSer.setCDATA('root SYSTEM')
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <![CDATA[root SYSTEM]]>
```

## setComment

```TypeScript
setComment(text: string): void
```

Sets a comment.

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-XmlSerializer-setComment(text: string): void--><!--Device-XmlSerializer-setComment(text: string): void-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Comment to set. |

**Examples**

```TypeScript
import { util } from '@kit.ArkTS';

let arrayBuffer = new ArrayBuffer(2048);
let thatSer = new xml.XmlSerializer(arrayBuffer);
thatSer.setComment("Hello, World!");
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <!--Hello, World!-->
```

## setDeclaration

```TypeScript
setDeclaration(): void
```

Sets a file declaration with encoding.

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-XmlSerializer-setDeclaration(): void--><!--Device-XmlSerializer-setDeclaration(): void-End-->

**System capability:** SystemCapability.Utils.Lang

**Examples**

```TypeScript
import { util } from '@kit.ArkTS';

let arrayBuffer = new ArrayBuffer(2048);
let thatSer = new xml.XmlSerializer(arrayBuffer);
thatSer.setDeclaration();
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result);
// <?xml version="1.0" encoding="utf-8"?>
```

## setDocType

```TypeScript
setDocType(text: string): void
```

Sets a document type.

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-XmlSerializer-setDocType(text: string): void--><!--Device-XmlSerializer-setDocType(text: string): void-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Content of DocType to set. |

**Examples**

```TypeScript
import { util } from '@kit.ArkTS';

let arrayBuffer = new ArrayBuffer(2048);
let thatSer = new xml.XmlSerializer(arrayBuffer);
thatSer.setDocType('root SYSTEM "http://www.test.org/test.dtd"');
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <!DOCTYPE root SYSTEM "http://www.test.org/test.dtd">
```

## setNamespace

```TypeScript
setNamespace(prefix: string, namespace: string): void
```

Sets the namespace for an element tag.

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-XmlSerializer-setNamespace(prefix: string, namespace: string): void--><!--Device-XmlSerializer-setNamespace(prefix: string, namespace: string): void-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| prefix | string | Yes | Prefix of the element and its child elements. |
| namespace | string | Yes | Namespace to set. |

**Examples**

```TypeScript
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

## setText

```TypeScript
setText(text: string): void
```

Sets a tag value.

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-XmlSerializer-setText(text: string): void--><!--Device-XmlSerializer-setText(text: string): void-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Tag value to set, which is the content of the text attribute. |

**Examples**

```TypeScript
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

## startElement

```TypeScript
startElement(name: string): void
```

Writes the start tag based on the given element name.

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-XmlSerializer-startElement(name: string): void--><!--Device-XmlSerializer-startElement(name: string): void-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the element. |

**Examples**

```TypeScript
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
