# @ohos.convertxml (XML-to-JavaScript Conversion)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @xliu-huanwei; @shilei123; @huanghello-->
<!--Designer: @yuanyao14-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

The convertxml module provides APIs for converting XML text into JavaScript objects.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import

```ts
import { convertxml } from '@kit.ArkTS';
```

## ConvertXML

### fastConvertToJSObject<sup>14+</sup>

fastConvertToJSObject(xml: string, options?: ConvertOptions) : Object

Converts an XML text to an object of the object type.

> **NOTE**
>
> - This API cannot parse XML files with a large amount of data. If the text content of a single element exceeds 10 MB, an error message is displayed and an object that contains only the XML tag header will be returned.
>
> - In Windows, a newline is usually represented by the carriage return (CR) followed by the line feed (LF). However, the object obtained by calling this API uses only the LF to indicate a new line.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type                             | Mandatory| Description           |
| ------- | --------------------------------- | ---- | --------------- |
| xml     | string                            | Yes  | XML text to convert. If the XML text contains the ampersand (&), replace it with the entity reference **\&amp;**.|
| options | [ConvertOptions](#convertoptions) | No  | Options for conversion. The default value is a **ConvertOptions** object, which consists of the default values of the attributes in the object.|

**Return value**

| Type  | Description                        |
| ------ | ---------------------------- |
| Object | JavaScript object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 10200002 | Invalid xml string. |

**Example**

```ts
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

### largeConvertToJSObject<sup>23+</sup>

largeConvertToJSObject(xml: string, options?: ConvertOptions): Object

Converts XML text to an object of the object type. This method can parse large XML text whose size of a single node exceeds 10 MB.

> **NOTE**
>
> In Windows, a new line is usually represented by the carriage return (CR) followed by the line feed (LF). However, the object obtained by calling this API uses only the LF to indicate a new line.

**Atomic service API**: This API can be used in atomic services since API version 23.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type                             | Mandatory| Description           |
| ------- | --------------------------------- | ---- | --------------- |
| xml     | string                            | Yes  | XML text to convert. If the XML text contains the ampersand (&), replace it with the entity reference **\&amp;**.|
| options | [ConvertOptions](#convertoptions) | No  | Options for conversion. The default value is a **ConvertOptions** object, which consists of the default values of the attributes in the object.|

**Return value**

| Type  | Description                        |
| ------ | ---------------------------- |
| Object | JavaScript object.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200002 | Invalid xml string. |

**Example**

```ts
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

### convertToJSObject<sup>(deprecated)</sup>

convertToJSObject(xml: string, options?: ConvertOptions) : Object

Converts an XML text to an object of the object type.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 14. You are advised to use [fastConvertToJSObject<sup>14+</sup>](#fastconverttojsobject14) instead.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type                             | Mandatory| Description           |
| ------- | --------------------------------- | ---- | --------------- |
| xml     | string                            | Yes  | If the XML text to convert contains the ampersand (&), replace it with the entity reference **\&amp;**.|
| options | [ConvertOptions](#convertoptions) | No  | Options for conversion. The default value is a **ConvertOptions** object, which consists of the default values of the attributes in the object.|

**Return value**

| Type  | Description                        |
| ------ | ---------------------------- |
| Object | JavaScript object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 10200002 | Invalid xml string. |

**Example**

```ts
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

### convert<sup>(deprecated)</sup>

convert(xml: string, options?: ConvertOptions) : Object

Converts an XML text to a JavaScript object.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [fastConvertToJSObject<sup>14+</sup>](#fastconverttojsobject14) instead.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type                             | Mandatory| Description           |
| ------- | --------------------------------- | ---- | --------------- |
| xml     | string                            | Yes  | Input XML text.|
| options | [ConvertOptions](#convertoptions) | No  | Options for conversion. The default value is a **ConvertOptions** object, which consists of the default values of the attributes in the object. |

**Return value**

| Type  | Description                        |
| ------ | ---------------------------- |
| Object | JavaScript object.|

**Example**

```ts
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

## ConvertOptions

Options for conversion.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

| Name             | Type| Read-Only| Optional| Description                                                       |
| ----------------- | -------- | ---- | ---- | ----------------------------------------------------------- |
| trim              | boolean  | No  | No  | Whether to trim the whitespace characters before and after the text. The value **true** means to trim the whitespace characters before and after the text, and **false** means to keep them.  |
| ignoreDeclaration | boolean  | No  | Yes  | Whether to ignore the XML declaration. The value **true** means to ignore the XML declaration, and **false** means the opposite. The default value is **false**.                       |
| ignoreInstruction | boolean  | No  | Yes  | Whether to ignore the XML processing instruction. The value **true** means to ignore the XML processing instruction, and **false** means the opposite. The default value is **false**.                     |
| ignoreAttributes  | boolean  | No  | Yes  | Whether to ignore the element's attribute information. The value **true** means to ignore the element's attribute information, and **false** means the opposite. The default value is **false**.                  |
| ignoreComment     | boolean  | No  | Yes  | Whether to ignore element comments. The value **true** means to ignore element comments, and **false** means the opposite. The default value is **false**.                        |
| ignoreCDATA       | boolean  | No  | Yes  | Whether to ignore the element's CDATA information. The value **true** means to ignore the element's CDATA information, and **false** means the opposite. The default value is **false**.                       |
| ignoreDoctype     | boolean  | No  | Yes  | Whether to ignore the element's Doctype information. The value **true** means to ignore the element's Doctype information, and **false** means the opposite. The default value is **false**.                     |
| ignoreText        | boolean  | No  | Yes  | Whether to ignore the element's text information. The value **true** means to ignore the element's text information, and **false** means the opposite. The default value is **false**.                        |
| declarationKey    | string   | No  | No  | Name of the attribute key for **declaration** in the output object.|
| instructionKey    | string   | No  | No  | Name of the attribute key for **instruction** in the output object.|
| attributesKey     | string   | No  | No  | Name of the attribute key for **attributes** in the output object.  |
| textKey           | string   | No  | No  | Name of the attribute key for **text** in the output object.              |
| cdataKey          | string   | No  | No  | Name of the attribute key for **cdata** in the output object.            |
| doctypeKey        | string   | No  | No  | Name of the attribute key for **doctype** in the output object.        |
| commentKey        | string   | No  | No  | Name of the attribute key for **comment** in the output object.        |
| parentKey         | string   | No  | No  | Name of the attribute key for **parent** in the output object.          |
| typeKey           | string   | No  | No  | Name of the attribute key for **type** in the output object.              |
| nameKey           | string   | No  | No  | Name of the attribute key for **name** in the output object.              |
| elementsKey       | string   | No  | No  | Name of the attribute key for **elements** in the output object.      |
