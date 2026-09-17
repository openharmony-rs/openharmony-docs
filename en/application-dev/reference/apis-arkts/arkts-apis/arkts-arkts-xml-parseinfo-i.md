# ParseInfo

The current parse info.

**Since:** 8

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { xml } from '@kit.ArkTS';
```

## getAttributeCount

```TypeScript
getAttributeCount(): number
```

Obtains the number of attributes for the current start tag.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| number |  |

**Examples**

```TypeScript
import { util } from '@kit.ArkTS';

let strXml = '<?xml version="1.0" encoding="utf-8"?><note importance="high" logged="true"/>';
let textEncoder = new util.TextEncoder();
let arrBuffer = textEncoder.encodeInto(strXml);
let that = new xml.XmlPullParser(arrBuffer.buffer as object as ArrayBuffer);
let str = "";
function func(key: xml.EventType, value: xml.ParseInfo) {
  str += 'key:' + key + ' value:' + value.getAttributeCount() + ' ';
  return true; // Determines whether to continually parse, which is used to continue or terminate parsing.
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:true, tokenValueCallbackFunction:func}
that.parseXml(options);
console.info(str);
// key:0 value:0 key:2 value:2 key:3 value:2 key:1 value:0
```

## getColumnNumber

```TypeScript
getColumnNumber(): number
```

Obtains the current column number, starting from 1.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| number |  |

**Examples**

```TypeScript
import { util } from '@kit.ArkTS';

let strXml = '<?xml version="1.0" encoding="utf-8"?><note>Happy</note>';
let textEncoder = new util.TextEncoder();
let arrBuffer = textEncoder.encodeInto(strXml);
let that = new xml.XmlPullParser(arrBuffer.buffer as object as ArrayBuffer);
let str = "";
function func(key: xml.EventType, value: xml.ParseInfo) {
  str += 'key:' + key + ' value:' + value.getColumnNumber() + ' ';
  return true; // Determines whether to continually parse, which is used to continue or terminate parsing.
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:true, tokenValueCallbackFunction:func}
that.parseXml(options);
console.info(str);
// key:0 value:1 key:2 value:45 key:4 value:50 key:3 value:57 key:1 value:57
```

## getDepth

```TypeScript
getDepth(): number
```

Obtains the depth of this element.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| number |  |

**Examples**

```TypeScript
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
  return true; // Determines whether to continually parse, which is used to continue or terminate parsing.
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:true, tokenValueCallbackFunction:func}
that.parseXml(options);
console.info(str);
// key:0 value:0 key:2 value:1 key:2 value:2 key:4 value:2 key:3 value:2 key:3 value:1 key:1 value:0
```

## getLineNumber

```TypeScript
getLineNumber(): number
```

Obtains the current line number, starting from 1.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| number |  |

**Examples**

```TypeScript
import { util } from '@kit.ArkTS';

let strXml = '<?xml version="1.0" encoding="utf-8"?><note>Work</note>';
let textEncoder = new util.TextEncoder();
let arrBuffer = textEncoder.encodeInto(strXml);
let that = new xml.XmlPullParser(arrBuffer.buffer as object as ArrayBuffer);
let str = "";
function func(key: xml.EventType, value: xml.ParseInfo) {
  str += 'key:' + key + ' value:' + value.getLineNumber() + ' ';
  return true; // Determines whether to continually parse, which is used to continue or terminate parsing.
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:true, tokenValueCallbackFunction:func}
that.parseXml(options);
console.info(str);
// key:0 value:1 key:2 value:1 key:4 value:1 key:3 value:1 key:1 value:1
```

## getName

```TypeScript
getName(): string
```

Obtains the name of this element.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| string |  |

**Examples**

```TypeScript
import { util } from '@kit.ArkTS';

let strXml = '<?xml version="1.0" encoding="utf-8"?><note>Happy</note>';
let textEncoder = new util.TextEncoder();
let arrBuffer = textEncoder.encodeInto(strXml);
let that = new xml.XmlPullParser(arrBuffer.buffer as object as ArrayBuffer);
let str = "";
function func(key: xml.EventType, value: xml.ParseInfo) {
  str += 'key:' + key + ' value:' + value.getName() + ' ';
  return true; // Determines whether to continually parse, which is used to continue or terminate parsing.
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:true, tokenValueCallbackFunction:func}
that.parseXml(options);
console.info(str);
// key:0 value: key:2 value:note key:4 value: key:3 value:note key:1 value:
```

## getNamespace

```TypeScript
getNamespace(): string
```

Obtains the namespace of this element.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| string |  |

**Examples**

```TypeScript
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
  return true; // Determines whether to continually parse, which is used to continue or terminate parsing.
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:false, tokenValueCallbackFunction:func}
that.parseXml(options);
console.info(str);
// key:0 value: key:2 value: key:2 value:http://www.w3.org key:4 value: key:3 value:http://www.w3.org key:3 value: key:1 value:
```

## getPrefix

```TypeScript
getPrefix(): string
```

Obtains the prefix of this element.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| string |  |

**Examples**

```TypeScript
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
  return true; // Determines whether to continually parse, which is used to continue or terminate parsing.
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:false, tokenValueCallbackFunction:func}
that.parseXml(options);
console.info(str);
// key:0 value: key:2 value: key:2 value:h key:4 value: key:3 value:h key:3 value: key:1 value:
```

## getText

```TypeScript
getText(): string
```

Obtains the text of the current event.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| string |  |

**Examples**

```TypeScript
import { util } from '@kit.ArkTS';

let strXml = '<?xml version="1.0" encoding="utf-8"?><note>Happy</note>';
let textEncoder = new util.TextEncoder();
let arrBuffer = textEncoder.encodeInto(strXml);
let that = new xml.XmlPullParser(arrBuffer.buffer as object as ArrayBuffer);
let str = "";
function func(key: xml.EventType, value: xml.ParseInfo) {
  str += 'key:' + key + ' value:' + value.getText() + ' ';
  return true; // Determines whether to continually parse, which is used to continue or terminate parsing.
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:true, tokenValueCallbackFunction:func}
that.parseXml(options);
console.info(str);
// key:0 value: key:2 value: key:4 value:Happy key:3 value: key:1 value:
```

## isEmptyElementTag

```TypeScript
isEmptyElementTag(): boolean
```

Checks whether the current element is empty.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean |  |

**Examples**

```TypeScript
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
  return true; // Determines whether to continually parse, which is used to continue or terminate parsing.
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:true, tokenValueCallbackFunction:func}
that.parseXml(options);
console.info(str);
// key:0 value:false key:2 value:false key:2 value:true key:3 value:false key:3 value:false key:1 value:false
```

## isWhitespace

```TypeScript
isWhitespace(): boolean
```

Checks whether the current event contains only whitespace characters.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean |  |

**Examples**

```TypeScript
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
  return true; // Determines whether to continually parse, which is used to continue or terminate parsing.
}
let options: xml.ParseOptions = {supportDoctype:true, ignoreNameSpace:true, tokenValueCallbackFunction:func}
that.parseXml(options);
console.info(str);
// key:0 value:true key:2 value:false key:2 value:true key:10 value:true key:3 value:true key:3 value:true key:1 value:true
```
