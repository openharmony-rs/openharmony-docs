# XmlPullParser

```TypeScript
class XmlPullParser
```

The XmlPullParser interface is used to parse the existing xml file.

**Since:** 8

<!--Device-xml-class XmlPullParser--><!--Device-xml-class XmlPullParser-End-->

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { xml } from '@kit.ArkTS';
```

## constructor

```TypeScript
constructor(buffer: ArrayBuffer | DataView, encoding?: string)
```

Creates and returns an XmlPullParser object.

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-XmlPullParser-constructor(buffer: ArrayBuffer | DataView, encoding?: string)--><!--Device-XmlPullParser-constructor(buffer: ArrayBuffer | DataView, encoding?: string)-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buffer | ArrayBuffer &#124; DataView | Yes | A instance, the new XmlPullParser with. |
| encoding | string | No | [encoding='utf8'] this is its encoding. |

**Examples**

```TypeScript
import { util } from '@kit.ArkTS';

let strXml = '<title>Happy</title>'
let textEncoder = new util.TextEncoder();
let uint8Array = textEncoder.encodeInto(strXml);
let that = new xml.XmlPullParser(uint8Array.buffer as object as ArrayBuffer, 'UTF-8');
```

## parseXml

```TypeScript
parseXml(option: ParseOptions): void
```

Parses XML information.

**Since:** 14

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 14.

<!--Device-XmlPullParser-parseXml(option: ParseOptions): void--><!--Device-XmlPullParser-parseXml(option: ParseOptions): void-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| option | [ParseOptions](arkts-arkts-xml-parseoptions-i.md) | Yes | XML parsing options. |

## parse

```TypeScript
parse(option: ParseOptions): void
```

Starts parsing the XML file.

**Since:** 8

**Deprecated since:** 14

**Substitutes:** [parseXml](#parsexml)

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-XmlPullParser-parse(option: ParseOptions): void--><!--Device-XmlPullParser-parse(option: ParseOptions): void-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| option | [ParseOptions](arkts-arkts-xml-parseoptions-i.md) | Yes | Parse options for XmlPullParser, the interface including two Boolean variables and three callback functions. |

**Examples**

```TypeScript
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
let str = '';
function func(name: string, value: string) {
  str = name + value;
  console.info(str);
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
