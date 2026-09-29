# XmlSAXHandler

```TypeScript
interface XmlSAXHandler
```

A simple API for XML handling

**Since:** 24

<!--Device-xml-interface XmlSAXHandler--><!--Device-xml-interface XmlSAXHandler-End-->

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { xml } from '@kit.ArkTS';
```

## characters

```TypeScript
characters(content: string): void
```

CallBack function triggered by the text content

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-XmlSAXHandler-characters(content: string): void--><!--Device-XmlSAXHandler-characters(content: string): void-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | string | Yes | literal content |

## endDocument

```TypeScript
endDocument(): void
```

CallBack function triggered at the end of the document

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-XmlSAXHandler-endDocument(): void--><!--Device-XmlSAXHandler-endDocument(): void-End-->

**System capability:** SystemCapability.Utils.Lang

## endElement

```TypeScript
endElement(elementName: string, namespaceURI: string | undefined, qName: string | undefined): void
```

CallBack function triggered at the end of the element

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-XmlSAXHandler-endElement(elementName: string, namespaceURI: string | undefined, qName: string | undefined): void--><!--Device-XmlSAXHandler-endElement(elementName: string, namespaceURI: string | undefined, qName: string | undefined): void-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| elementName | string | Yes | Name of the element |
| namespaceURI | string &#124; undefined | Yes | URI of the namespace |
| qName | string &#124; undefined | Yes | Fully qualified name with namespace |

## startDocument

```TypeScript
startDocument(): void
```

CallBack function triggered at the beginning of the document

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-XmlSAXHandler-startDocument(): void--><!--Device-XmlSAXHandler-startDocument(): void-End-->

**System capability:** SystemCapability.Utils.Lang

## startElement

```TypeScript
startElement(elementName: string, namespaceURI: string | undefined, qName: string | undefined, attributes: Map<string,string>): void
```

CallBack function triggered at the beginning of the element

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-XmlSAXHandler-startElement(elementName: string, namespaceURI: string | undefined, qName: string | undefined, attributes: Map<string,string>): void--><!--Device-XmlSAXHandler-startElement(elementName: string, namespaceURI: string | undefined, qName: string | undefined, attributes: Map<string,string>): void-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| elementName | string | Yes | Name of the element |
| namespaceURI | string &#124; undefined | Yes | URI of the namespace |
| qName | string &#124; undefined | Yes | Fully qualified name with namespace |
| attributes | Map&lt;string, string&gt; | Yes | attributes mapping |
