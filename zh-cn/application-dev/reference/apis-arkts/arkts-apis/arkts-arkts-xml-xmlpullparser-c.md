# XmlPullParser

XmlPullParser接口用于解析现有的XML文件。

**起始版本：** 8

<!--Device-xml-class XmlPullParser--><!--Device-xml-class XmlPullParser-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { xml } from '@kit.ArkTS';
```

<a id="constructor"></a>
## constructor

```TypeScript
constructor(buffer: ArrayBuffer | DataView, encoding?: string)
```

构造并返回一个XmlPullParser对象。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-XmlPullParser-constructor(buffer: ArrayBuffer | DataView, encoding?: string)--><!--Device-XmlPullParser-constructor(buffer: ArrayBuffer | DataView, encoding?: string)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | ArrayBuffer \| DataView | 是 | 用于解析的XML文本信息。 |
| encoding | string | 否 | 编码格式，默认'utf-8'（目前仅支持'utf-8'）。 |

**示例：**

```TypeScript
import { util } from '@kit.ArkTS';

let strXml = '<title>Happy</title>'
let textEncoder = new util.TextEncoder();
let uint8Array = textEncoder.encodeInto(strXml);
let xmlParser = new xml.XmlPullParser(uint8Array.buffer as object as ArrayBuffer, 'UTF-8');

```

<a id="parse"></a>
## parse

```TypeScript
parse(option: ParseOptions): void
```

该接口用于解析XML。

**起始版本：** 8

**废弃版本：** 14

**替代接口：** parseXml

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-XmlPullParser-parse(option: ParseOptions): void--><!--Device-XmlPullParser-parse(option: ParseOptions): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | [ParseOptions](arkts-arkts-json-parseoptions-i.md) | 是 | XML解析选项。 |

**示例：**

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

<a id="parsexml"></a>
## parseXml

```TypeScript
parseXml(option: ParseOptions): void
```

解析XML。

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-XmlPullParser-parseXml(option: ParseOptions): void--><!--Device-XmlPullParser-parseXml(option: ParseOptions): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | [ParseOptions](arkts-arkts-json-parseoptions-i.md) | 是 | XML解析选项。 |

