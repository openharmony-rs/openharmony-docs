# @ohos.xml(XML Parsing and Generation)

The xml module provides utilities for converting XML text to Javascript object, XML generation and parsing.

**Since:** 8

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { xml } from '@kit.ArkTS';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [XmlDynamicSerializer](arkts-arkts-xml-xmldynamicserializer-c.md) | The XmlDynamicSerializer interface is used to dynamically generate an xml file. |
| [XmlPullParser](arkts-arkts-xml-xmlpullparser-c.md) | The XmlPullParser interface is used to parse the existing xml file. |
| [XmlSAXParser](arkts-arkts-xml-xmlsaxparser-c.md) | The XmlSAXParser provides the capability of parsing XML in a streaming manner. |
| [XmlSerializer](arkts-arkts-xml-xmlserializer-c.md) | The XmlSerializer interface is used to generate an xml file. |

### Interfaces

| Name | Description |
| --- | --- |
| [ParseInfo](arkts-arkts-xml-parseinfo-i.md) | The current parse info. |
| [ParseOptions](arkts-arkts-xml-parseoptions-i.md) | Parse options for XmlPullParser. |
| [XmlSAXHandler](arkts-arkts-xml-xmlsaxhandler-i.md) | A simple API for XML handling |

### Enums

| Name | Description |
| --- | --- |
| [EventType](arkts-arkts-xml-eventtype-e.md) | The event types represented by XML elements. |

### Types

| Name | Description |
| --- | --- |
| [AttributeWithTagCb](arkts-arkts-xml-attributewithtagcb-t.md) | The type of ParseOptions attributeWithTagCallbackFunction. |
