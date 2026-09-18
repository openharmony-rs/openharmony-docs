# XmlSAXParser

The XmlSAXParser provides the capability of parsing XML in a streaming manner.

**Since:** 24

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { xml } from '@kit.ArkTS';
```

## constructor

```TypeScript
constructor(inputStream: stream.Readable, encoding?: string)
```

Creates and returns an XmlSAXParser instance.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| inputStream | [stream.Readable](arkts-arkts-stream-readable-c.md) | Yes | An instance, of stream.Readable for the new XmlSAXParser. |
| encoding | string | No | [encoding='utf8'] this is its encoding. |

## parse

```TypeScript
parse(xmlSAXHandler: XmlSAXHandler): void
```

Creates and returns an XmlSAXParser instance.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| xmlSAXHandler | [XmlSAXHandler](arkts-arkts-xml-xmlsaxhandler-i.md) | Yes | The simple API for XML handler. |
