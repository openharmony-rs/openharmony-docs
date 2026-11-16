# @ohos.convertxml (XML-to-JavaScript Conversion)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @Malzahar-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=fa87684a3d68d73092de76cbd3803fc3d90b97e4 translatedAt=2026-11-16T05:25:46.623Z pushedAt=2026-11-16T06:31:14.187Z nl=1 -->

This module provides the parsing capability to convert XML text into JavaScript objects, applicable to scenarios such as XML configuration file parsing, XML-format network data processing, data migration, and format conversion. During conversion, the various components of XML (declarations, instructions, elements, attributes, text, CDATA, comments, Doctype, and so on) are mapped to properties of a JavaScript object according to the key names configured in ConvertOptions, forming a hierarchically nested object structure. This simplifies the XML data processing flow and supports flexible output structures through custom key name mapping via ConvertOptions.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import

```ts
import { convertxml } from '@kit.ArkTS';
```

## ConvertXML

The ConvertXML class provides the capability to convert XML text into JavaScript objects. It is recommended to use [fastConvertToJSObject<sup>14+</sup>](#fastconverttojsobject14) for regular XML text parsing. When the text content of a single element exceeds 10M, it is recommended to use [largeConvertToJSObject<sup>23+</sup>](#largeconverttojsobject23). The deprecated [convertToJSObject](#converttojsobjectdeprecated) and [convert](#convertdeprecated) methods are no longer maintained. It is recommended to use [fastConvertToJSObject<sup>14+</sup>](#fastconverttojsobject14) instead.

### fastConvertToJSObject<sup>14+</sup>

fastConvertToJSObject(xml: string, options?: ConvertOptions) : Object

Converts XML text into an Object type object, applicable to scenarios such as XML configuration file parsing and data packet processing. This method parses XML text into a hierarchically nested structure, where each XML component is mapped to a property of the object according to the key names configured in ConvertOptions. When the text content of a single element exceeds 10M, it is recommended to use [largeConvertToJSObject<sup>23+</sup>](#largeconverttojsobject23) instead.

> **NOTE**
>
> This API cannot parse an XML file whose single-element text content exceeds 10M. When the single-element text content exceeds 10M, exception log information is output and a basic Object object containing only the XML declaration is returned. To parse XML text whose single-element text content exceeds 10M, it is recommended to use [largeConvertToJSObject<sup>23+</sup>](#largeconverttojsobject23) instead.
>
> In the Windows environment, a line break is usually represented by a pair of characters: carriage return (CR) and line feed (LF). The object converted by the fastConvertToJSObject API represents a line break with a line feed (LF).

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type                             | Mandatory| Description           |
| ------- | --------------------------------- | ---- | --------------- |
| xml     | string                            | Yes   | XML text, which must comply with the XML syntax specification. If it contains the "&" character, use the entity reference "\&amp;" instead. When the text content of a single element exceeds 10M, an exception log is output and a basic Object containing only the XML declaration is returned. It is recommended to use largeConvertToJSObject instead. |
| options | [ConvertOptions](#convertoptions) | No   | Conversion options, used to customize the XML conversion behavior. When not passed in, the default values of each ConvertOptions property are used. |

**Return value**

| Type  | Description                        |
| ------ | ---------------------------- |
| Object | Converted JavaScript object that provides the parsed XML structure information. The specific attribute key names are defined by ConvertOptions, and the mapping data of each XML component can be accessed through the configured key names. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200002 | Invalid xml string. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let xml =
    '<?xml version="1.0" encoding="utf-8"?>' +
    '<note importance="high" logged="true">' +
    '   <title>Hello\r\nWorld</title>' +
    '   <todo><![CDATA[Work\r\n]]></todo>' +
    '</note>';
  // Create a ConvertXML conversion instance.
  let converter = new convertxml.ConvertXML();
  // Configure conversion options.
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
  // Call the fastConvertToJSObject API to convert XML text.
  let result = JSON.stringify(converter.fastConvertToJSObject(xml, options));
  console.info(result);
} catch (e) {
  let err: BusinessError = e as BusinessError;
  console.error(`Failed to convert XML text to JS object using fastConvertToJSObject. Code: ${err.code}, message: ${err.message}`);
}
// Output (non-compact)
// {"_declaration":{"_attributes":{"version":"1.0","encoding":"utf-8"}},"_elements":[{"_type":"element","_name":"note","_attributes":{"importance":"high","logged":"true"},"_elements":[{"_type":"element","_name":"title","_elements":[{"_type":"text","_text":"Hello\nWorld"}]},{"_type":"element","_name":"todo","_elements":[{"_type":"cdata","_cdata":"Work\n"}]}]}]}
```

### largeConvertToJSObject<sup>23+</sup>

largeConvertToJSObject(xml: string, options?: ConvertOptions): Object

Converts XML text into an Object type object, applicable to large XML parsing scenarios such as XML log files and data packets. This method supports parsing large XML text whose single element exceeds 10M. It is optimized for large text scenarios and can effectively avoid parsing exceptions caused by oversized single-element text. When [fastConvertToJSObject<sup>14+</sup>](#fastconverttojsobject14) cannot parse normally because the text content of a single element exceeds 10M, this method can be used as an alternative.

> **NOTE**
>
> When the input XML text cannot be correctly parsed into an Object type object, an exception log is output and a basic Object object containing only the XML declaration is returned.
>
> In the Windows environment, a line break is usually represented by a pair of characters: carriage return (CR) and line feed (LF). The object converted by this API represents a line break with a line feed (LF).

**Atomic service API**: This API can be used in atomic services since API version 23.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type                             | Mandatory| Description           |
| ------- | --------------------------------- | ---- | --------------- |
| xml     | string                            | Yes   | XML text, which must comply with the XML syntax specification. If it contains the "&" character, use the entity reference "\&amp;" instead. |
| options | [ConvertOptions](#convertoptions) | No   | Conversion options, used to customize the XML conversion behavior. When not passed in, the default values of each ConvertOptions property are used. |

**Return value**

| Type  | Description                        |
| ------ | ---------------------------- |
| Object | Converted JavaScript object that contains the parsed XML structure information. The specific attribute key names are defined by ConvertOptions. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200002 | Invalid xml string. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let xmlString =
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
  // Create a ConvertXML conversion instance.
  let converter = new convertxml.ConvertXML();
  // Configure conversion options.
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
  // Call the largeConvertToJSObject API to convert large XML text.
  let result = JSON.stringify(converter.largeConvertToJSObject(xmlString, options));
  console.info(result);
} catch (e) {
  let err: BusinessError = e as BusinessError;
  console.error(`Failed to convert XML text to JS object using largeConvertToJSObject. Code: ${err.code}, message: ${err.message}`);
}
// Output (non-compact)
// {"_declaration":{"_attributes":{"version":"1.0","encoding":"utf-8"}},"_elements":[{"_type":"instruction","_name":"custom-pi","_instruction":"processing=\"example\""},{"_type":"element","_name":"catalog","_attributes":{"id":"books"},"_elements":[{"_type":"comment","_comment":" Bestseller Example "},{"_type":"element","_name":"book","_parent":"catalog","_attributes":{"category":"fiction","ref":"B101"},"_elements":[{"_type":"element","_name":"title","_parent":"book","_elements":[{"_type":"text","_text":"Echoes & Whispers"}]},{"_type":"element","_name":"price","_parent":"book","_attributes":{"unit":"USD"},"_elements":[{"_type":"text","_text":"19.99"}]},{"_type":"element","_name":"descr","_parent":"book","_elements":[{"_type":"cdata","_cdata":"<b>suspense</b>novel & Legendary Stories"}]},{"_type":"element","_name":"popular","_parent":"book"}]}]}]}
```

### convertToJSObject<sup>(deprecated)</sup>

convertToJSObject(xml: string, options?: ConvertOptions) : Object

Converts XML text into an Object type object, applicable to scenarios such as XML configuration file parsing and data format conversion. This method parses XML text into a hierarchically nested structure, where each XML component is mapped to a property of the object according to the key names configured in ConvertOptions.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9 and deprecated since API version 14. It is recommended to use [fastConvertToJSObject<sup>14+</sup>](#fastconverttojsobject14) instead.
>
> In the Windows environment, a line break is usually represented by a pair of characters: carriage return (CR) and line feed (LF). The object converted by this API represents a line break with a line feed (LF).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type                             | Mandatory| Description           |
| ------- | --------------------------------- | ---- | --------------- |
| xml     | string                            | Yes   | XML text, which must comply with the XML syntax specification. If it contains the "&" character, use the entity reference "\&amp;" instead. |
| options | [ConvertOptions](#convertoptions) | No   | Conversion options, used to customize the XML conversion behavior. When not passed in, the default values of each ConvertOptions property are used. |

**Return value**

| Type  | Description                        |
| ------ | ---------------------------- |
| Object | Converted JavaScript object that contains the parsed XML structure information. The specific attribute key names are defined by ConvertOptions. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200002 | Invalid xml string. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let xml =
    '<?xml version="1.0" encoding="utf-8"?>' +
      '<note importance="high" logged="true">' +
      '    <title>Happy</title>' +
      '    <todo>Work</todo>' +
      '    <todo>Play</todo>' +
      '</note>';
  // Create a ConvertXML conversion instance.
  let converter = new convertxml.ConvertXML();
  // Configure conversion options.
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
  // Call the convertToJSObject API to convert XML text (deprecated, recommended to use fastConvertToJSObject).
  let result = JSON.stringify(converter.convertToJSObject(xml, options));
  console.info(result);
} catch (e) {
  let err: BusinessError = e as BusinessError;
  console.error(`Failed to convert XML text to JS object using convertToJSObject. Code: ${err.code}, message: ${err.message}`);
}
// Output (non-compact)
// {"_declaration":{"_attributes":{"version":"1.0","encoding":"utf-8"}},"_elements":[{"_type":"element","_name":"note","_attributes":{"importance":"high","logged":"true"},"_elements":[{"_type":"element","_name":"title","_elements":[{"_type":"text","_text":"Happy"}]},{"_type":"element","_name":"todo","_elements":[{"_type":"text","_text":"Work"}]},{"_type":"element","_name":"todo","_elements":[{"_type":"text","_text":"Play"}]}]}]}
```

### convert<sup>(deprecated)</sup>

convert(xml: string, options?: ConvertOptions) : Object

Converts XML text into an Object type object.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [fastConvertToJSObject<sup>14+</sup>](#fastconverttojsobject14) instead.
>
> In the Windows environment, a line break is usually represented by a pair of characters: carriage return (CR) and line feed (LF). The object converted by this API uses line feed (LF) to represent a line break.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type                             | Mandatory| Description           |
| ------- | --------------------------------- | ---- | --------------- |
| xml     | string                            | Yes   | XML text, which must comply with the XML syntax specification. If it contains the "&" character, use the entity reference "\&amp;" instead. |
| options | [ConvertOptions](#convertoptions) | No   | Conversion options, used to customize the XML conversion behavior. When not passed in, the default values of each ConvertOptions property are used.  |

**Return value**

| Type  | Description                        |
| ------ | ---------------------------- |
| Object | Converted JavaScript object that contains the parsed XML structure information. The specific attribute key names are defined by ConvertOptions. |

**Example**

```ts
let xml =
  '<?xml version="1.0" encoding="utf-8"?>' +
    '<note importance="high" logged="true">' +
    '    <title>Happy</title>' +
    '    <todo>Work</todo>' +
    '    <todo>Play</todo>' +
    '</note>';
// Create a ConvertXML conversion instance.
let converter = new convertxml.ConvertXML();
// Configure conversion options.
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
// Call the convert API to convert XML text (deprecated, recommended to use fastConvertToJSObject).
let result = JSON.stringify(converter.convert(xml, options));
console.info(result);
// Output (non-compact)
// {"_declaration":{"_attributes":{"version":"1.0","encoding":"utf-8"}},"_elements":[{"_type":"element","_name":"note","_attributes":{"importance":"high","logged":"true"},"_elements":[{"_type":"element","_name":"title","_elements":[{"_type":"text","_text":"Happy"}]},{"_type":"element","_name":"todo","_elements":[{"_type":"text","_text":"Work"}]},{"_type":"element","_name":"todo","_elements":[{"_type":"text","_text":"Play"}]}]}]}
```

## ConvertOptions

Conversion options, used to customize the conversion behavior from XML to JavaScript objects, such as controlling whether to trim whitespace characters, whether to ignore specific components (declaration, instruction, attributes, comments, CDATA, Doctype, and text), and specifying the attribute key names of each type of component in the output object.

> **NOTE**
>
> The value of each key attribute (declarationKey, instructionKey, etc.) must be unique and cannot duplicate the values of other key attributes. Otherwise, key name conflicts may occur in the output object.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

| Name             | Type| Read-Only| Optional| Description                                                       |
| ----------------- | -------- | ---- | ---- | ----------------------------------------------------------- |
| trim              | boolean  | No   | No   | Whether to trim the whitespace characters before and after the text content. true indicates that the whitespace characters before and after the text content within an element will be trimmed, and false indicates that the whitespace characters will be retained. The default value is false.   |
| ignoreDeclaration | boolean  | No   | Yes   | Whether to ignore the XML declaration. true indicates ignoring the XML declaration, and false indicates retaining the XML declaration. The default value is false.                        |
| ignoreInstruction | boolean  | No   | Yes   | Whether to ignore the XML processing instruction. true indicates ignoring the XML processing instruction, and false indicates retaining the XML processing instruction. The default value is false.                      |
| ignoreAttributes  | boolean  | No   | Yes   | Whether to ignore the element attributes. true indicates ignoring the element attributes, and false indicates retaining the element attributes. The default value is false.                   |
| ignoreComment     | boolean  | No   | Yes   | Whether to ignore the element comments. true indicates ignoring the element comments, and false indicates retaining the element comments. The default value is false.                         |
| ignoreCDATA       | boolean  | No   | Yes   | Whether to ignore the CDATA (Character Data) information of the element. true indicates ignoring the CDATA information of the element, and false indicates retaining the CDATA information of the element. The default value is false.                        |
| ignoreDoctype     | boolean  | No   | Yes   | Whether to ignore the Doctype (Document Type Declaration) information. true indicates ignoring the Doctype information of the element, and false indicates retaining the Doctype information of the element. The default value is false.                      |
| ignoreText        | boolean  | No   | Yes   | Whether to ignore the element text. true indicates ignoring the element text, and false indicates retaining the element text. The default value is false.                         |
| declarationKey    | string   | No   | No   | Name of the attribute key for declaration in the output object. It takes effect only when ignoreDeclaration is false. |
| instructionKey    | string   | No   | No   | Name of the attribute key for instruction in the output object. It takes effect only when ignoreInstruction is false. |
| attributesKey     | string   | No   | No   | Name of the attribute key for attributes in the output object. It takes effect only when ignoreAttributes is false.   |
| textKey           | string   | No   | No   | Name of the attribute key for text in the output object. It takes effect only when ignoreText is false.               |
| cdataKey          | string   | No   | No   | Name of the attribute key for cdata in the output object. It takes effect only when ignoreCDATA is false.             |
| doctypeKey        | string   | No   | No   | Name of the attribute key for doctype in the output object. It takes effect only when ignoreDoctype is false.         |
| commentKey        | string   | No   | No   | Name of the attribute key for comment in the output object. It takes effect only when ignoreComment is false.         |
| parentKey         | string   | No   | No   | Name of the attribute key for parent in the output object. parent indicates the name of the parent element to which the current element belongs.           |
| typeKey           | string   | No   | No   | Name of the attribute key for type in the output object. type identifies the type of the XML component (such as element, text, cdata, comment, and instruction).               |
| nameKey           | string   | No  | No  | Name of the attribute key for **name** in the output object.              |
| elementsKey       | string   | No  | No  | Name of the attribute key for **elements** in the output object.      |