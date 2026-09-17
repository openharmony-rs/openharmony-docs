# XmlSAXHandler

A simple API for XML handling

**Since:** 24

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

**Atomic service API:** This API can be used in atomic services since API version 24.

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

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Utils.Lang

## endElement

```TypeScript
endElement(elementName: string, namespaceURI: string | undefined, qName: string | undefined): void
```

CallBack function triggered at the end of the element

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

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

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Utils.Lang

## startElement

```TypeScript
startElement(elementName: string, namespaceURI: string | undefined, qName: string | undefined, attributes: Map<string,string>): void
```

CallBack function triggered at the beginning of the element

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| elementName | string | Yes | Name of the element |
| namespaceURI | string &#124; undefined | Yes | URI of the namespace |
| qName | string &#124; undefined | Yes | Fully qualified name with namespace |
| attributes | Map&lt;string, string&gt; | Yes | attributes mapping |
