# ConvertXML

ConvertXML representation refers to extensible markup language.

**Since:** 8

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { convertxml } from '@kit.ArkTS';
```

## convert

```TypeScript
convert(xml: string, options?: ConvertOptions): Object
```

Converts an XML text to a JavaScript object.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [fastConvertToJSObject](#fastconverttojsobject)

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| xml | string | Yes | Input XML text. |
| options | [ConvertOptions](arkts-arkts-xml-convertoptions-i.md) | No | Options for conversion. The default value is a **ConvertOptions** object, which consists of the default values of the attributes in the object. |

**Return value:**

| Type | Description |
| --- | --- |
| Object | JavaScript object. |

**Examples**

```TypeScript
let xml =
  '<?xml version="1.0" encoding="utf-8"?>' +
    '<note importance="high" logged="true">' +
    '    <title>Happy</title>' +
    '    <todo>Work</todo>' +
    '    <todo>Play</todo>' +
    '</note>';
let conv = new convertxml.ConvertXML();
let options: convertxml.ConvertOptions = {
  trim: false,
  declarationKey: "_declaration",
  instructionKey: "_instruction",
  attributesKey: "_attributes",
  textKey: "_text",
  cdataKey: "_cdata",
  doctypeKey: "_doctype",
  commentKey: "_comment",
  parentKey: "_parent",
  typeKey: "_type",
  nameKey: "_name",
  elementsKey: "_elements"
};
let result = JSON.stringify(conv.convert(xml, options));
console.info(result);
// Output (non-compact)
// {"_declaration":{"_attributes":{"version":"1.0","encoding":"utf-8"}},"_elements":[{"_type":"element","_name":"note","_attributes":{"importance":"high","logged":"true"},"_elements":[{"_type":"element","_name":"title","_elements":[{"_type":"text","_text":"Happy"}]},{"_type":"element","_name":"todo","_elements":[{"_type":"text","_text":"Work"}]},{"_type":"element","_name":"todo","_elements":[{"_type":"text","_text":"Play"}]}]}]}
```

## convertToJSObject

```TypeScript
convertToJSObject(xml: string, options?: ConvertOptions): Object
```

Converts an XML text to an object of the object type.

**Since:** 9

**Deprecated since:** 14

**Substitutes:** [fastConvertToJSObject](#fastconverttojsobject)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| xml | string | Yes | If the XML text to convert contains the ampersand ( & ), replace it with the entity reference **&amp;**. |
| options | [ConvertOptions](arkts-arkts-xml-convertoptions-i.md) | No | Options for conversion. The default value is a **ConvertOptions** object, which consists of the default values of the attributes in the object. |

**Return value:**

| Type | Description |
| --- | --- |
| Object | JavaScript object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200002](../errorcode-utils.md#10200002-parameter-parsing-error) | Invalid xml string. |

**Examples**

```TypeScript
try {
  let xml =
    '<?xml version="1.0" encoding="utf-8"?>' +
      '<note importance="high" logged="true">' +
      '    <title>Happy</title>' +
      '    <todo>Work</todo>' +
      '    <todo>Play</todo>' +
      '</note>';
  let conv = new convertxml.ConvertXML();
  let options: convertxml.ConvertOptions = {
    trim: false,
    declarationKey: "_declaration",
    instructionKey: "_instruction",
    attributesKey: "_attributes",
    textKey: "_text",
    cdataKey: "_cdata",
    doctypeKey: "_doctype",
    commentKey: "_comment",
    parentKey: "_parent",
    typeKey: "_type",
    nameKey: "_name",
    elementsKey: "_elements"
  };
  let result = JSON.stringify(conv.convertToJSObject(xml, options));
  console.info(result);
} catch (e) {
  console.error((e as Object).toString());
}
// Output (non-compact)
// {"_declaration":{"_attributes":{"version":"1.0","encoding":"utf-8"}},"_elements":[{"_type":"element","_name":"note","_attributes":{"importance":"high","logged":"true"},"_elements":[{"_type":"element","_name":"title","_elements":[{"_type":"text","_text":"Happy"}]},{"_type":"element","_name":"todo","_elements":[{"_type":"text","_text":"Work"}]},{"_type":"element","_name":"todo","_elements":[{"_type":"text","_text":"Play"}]}]}]}
```

## fastConvertToJSObject

```TypeScript
fastConvertToJSObject(xml: string, options?: ConvertOptions): Object
```

Converts an XML text to an object of the object type.

> **NOTE:** 
> 
> - This API cannot parse XML files with a large amount of data. If the text content of a single element exceeds 10 MB, an error message is displayed and an object that contains only the XML tag header will be returned.
> 
> - In Windows, a newline is usually represented by the carriage return (CR) followed by the line feed (LF).However, the object obtained by calling this API uses only the LF to indicate a new line.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| xml | string | Yes | XML text to convert. If the XML text contains the ampersand ( & ), replace it with the entity reference **&amp;**. |
| options | [ConvertOptions](arkts-arkts-xml-convertoptions-i.md) | No | Options for conversion. The default value is a **ConvertOptions** object, which consists of the default values of the attributes in the object. |

**Return value:**

| Type | Description |
| --- | --- |
| Object | JavaScript object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200002](../errorcode-utils.md#10200002-parameter-parsing-error) | Invalid xml string. |

**Examples**

```TypeScript
try {
  let xml =
    '<?xml version="1.0" encoding="utf-8"?>' +
    '<note importance="high" logged="true">' +
    '   <title>Hello\r\nWorld</title>' +
    '   <todo><![CDATA[Work\r\n]]></todo>' +
    '</note>';
  let conv = new convertxml.ConvertXML();
  let options: convertxml.ConvertOptions = {
    trim: false,
    declarationKey: "_declaration",
    instructionKey: "_instruction",
    attributesKey: "_attributes",
    textKey: "_text",
    cdataKey: "_cdata",
    doctypeKey: "_doctype",
    commentKey: "_comment",
    parentKey: "_parent",
    typeKey: "_type",
    nameKey: "_name",
    elementsKey: "_elements"
  };
  let result = JSON.stringify(conv.fastConvertToJSObject(xml, options));
  console.info(result);
} catch (e) {
  console.error((e as Object).toString());
}
// Output (non-compact)
// {"_declaration":{"_attributes":{"version":"1.0","encoding":"utf-8"}},"_elements":[{"_type":"element","_name":"note","_attributes":{"importance":"high","logged":"true"},"_elements":[{"_type":"element","_name":"title","_elements":[{"_type":"text","_text":"Hello\nWorld"}]},{"_type":"element","_name":"todo","_elements":[{"_type":"cdata","_cdata":"Work\n"}]}]}]}
```

## largeConvertToJSObject

```TypeScript
largeConvertToJSObject(xml: string, options?: ConvertOptions): Object
```

Convert XML text to JavaScript objects, this method supports parsing large XML texts with a single node size exceeding 10M.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| xml | string | Yes | XML text to convert. If the XML text contains the ampersand ( & ), replace it with the entity reference &amp;. |
| options | [ConvertOptions](arkts-arkts-xml-convertoptions-i.md) | No | Options for conversion. The default value is a ConvertOptions object, which consists of the default values of the attributes in the object. |

**Return value:**

| Type | Description |
| --- | --- |
| Object | Returns a JavaScript object converting from XML text. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200002](../errorcode-utils.md#10200002-parameter-parsing-error) | Invalid xml string. |

**Examples**

```TypeScript
try {
  let xmlstr =
    '<?xml version="1.0" encoding="utf-8"?>' +
    '<?custom-pi processing="example"?>' +
    '<catalog id="books">' +
      '<!-- Bestseller Example -->' +
      '<book category="fiction" ref="B101">' +
        '<title>Echoes &amp; Whispers</title>' +
        '<price unit="USD">19.99</price>' +
        '<descr>' +
          '<![CDATA[<b>suspense</b>novel & Legendary Stories]]>' +
        '</descr>' +
        '<popular/>' +
      '</book>' +
    '</catalog>';
  let conv = new convertxml.ConvertXML();
  let options: convertxml.ConvertOptions = {
    trim: false,
    declarationKey: "_declaration",
    instructionKey: "_instruction",
    attributesKey: "_attributes",
    textKey: "_text",
    cdataKey: "_cdata",
    doctypeKey: "_doctype",
    commentKey: "_comment",
    parentKey: "_parent",
    typeKey: "_type",
    nameKey: "_name",
    elementsKey: "_elements"
  };
  let result = JSON.stringify(conv.largeConvertToJSObject(xmlstr, options));
  console.info(result);
} catch (e) {
  console.error((e as Object).toString());
}
// Output (non-compact)
// {"_declaration":{"_attributes":{"version":"1.0","encoding":"utf-8"}},"_elements":[{"_type":"instruction","_name":"custom-pi","_instruction":"processing=\"example\""},{"_type":"element","_name":"catalog","_attributes":{"id":"books"},"_elements":[{"_type":"comment","_comment":" Bestseller Example "},{"_type":"element","_name":"book","_parent":"catalog","_attributes":{"category":"fiction","ref":"B101"},"_elements":[{"_type":"element","_name":"title","_parent":"book","_elements":[{"_type":"text","_text":"Echoes & Whispers"}]},{"_type":"element","_name":"price","_parent":"book","_attributes":{"unit":"USD"},"_elements":[{"_type":"text","_text":"19.99"}]},{"_type":"element","_name":"descr","_parent":"book","_elements":[{"_type":"cdata","_cdata":"<b>suspense</b>novel & Legendary Stories"}]},{"_type":"element","_name":"popular","_parent":"book"}]}]}]}
```
