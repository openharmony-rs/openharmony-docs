# ConvertXML

ConvertXML类提供将XML文本转换为JavaScript对象的能力。 推荐使用[fastConvertToJSObject\_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_14+\_\_\_HTML\_TAG\_DESC\_USD\_6\_\_\_]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_进行常规XML文本解析， 当单元素文本内容超过10M时推荐使用[largeConvertToJSObject\_\_\_HTML\_TAG\_DESC\_USD\_7\_\_\_23+\_\_\_HTML\_TAG\_DESC\_USD\_8\_\_\_]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_。 已废弃的[convertToJSObject]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_和[convert]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_方法不再维护， 建议使用[fastConvertToJSObject\_\_\_HTML\_TAG\_DESC\_USD\_9\_\_\_14+\_\_\_HTML\_TAG\_DESC\_USD\_10\_\_\_]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

<!--Device-xml-class ConvertXML--><!--Device-xml-class ConvertXML-End-->

**系统能力：** SystemCapability.Utils.Lang

## convert

```TypeScript
convert(xml: string, options?: ConvertOptions): Object
```

将XML文本转换为Object类型对象。 > **说明：** > > 从API version 8开始支持，从API version 9开始废弃，建议使用 > [fastConvertToJSObject\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_14+\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [xml.ConvertXML#fastConvertToJSObject](arkts-arkts-xml-convertxml-c.md#fastconverttojsobject)

<!--Device-ConvertXML-convert(xml: string, options?: ConvertOptions): Object--><!--Device-ConvertXML-convert(xml: string, options?: ConvertOptions): Object-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| xml | string | 是 | XML文本，需符合XML语法规范，若包含"&"字符，请使用实体引用"&amp;"替换。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 转换选项，用于自定义XML转换行为。不传入时使用ConvertOptions各属性的默认值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | 转换后的JavaScript对象，包含解析后的XML结构信息，具体属性键名由ConvertOptions定义。 |

**示例：**

```TypeScript
let xml =
  '<?xml version="1.0" encoding="utf-8"?>' +
    '<note importance="high" logged="true">' +
    '    <title>Happy</title>' +
    '    <todo>Work</todo>' +
    '    <todo>Play</todo>' +
    '</note>';
// 创建ConvertXML转换实例
let converter = new convertxml.ConvertXML();
// 配置转换选项
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
// 调用convert接口转换XML文本（已废弃，建议使用fastConvertToJSObject）
let result = JSON.stringify(converter.convert(xml, options));
console.info(result);
// 输出(宽泛型)
// {"_declaration":{"_attributes":{"version":"1.0","encoding":"utf-8"}},"_elements":[{"_type":"element","_name":"note","_attributes":{"importance":"high","logged":"true"},"_elements":[{"_type":"element","_name":"title","_elements":[{"_type":"text","_text":"Happy"}]},{"_type":"element","_name":"todo","_elements":[{"_type":"text","_text":"Work"}]},{"_type":"element","_name":"todo","_elements":[{"_type":"text","_text":"Play"}]}]}]}
```

## convertToJSObject

```TypeScript
convertToJSObject(xml: string, options?: ConvertOptions): Object
```

将XML文本转换为Object类型对象，适用于XML配置文件解析、数据格式转换等场景。该方法将XML文本解析为层级嵌套结构，各XML组件按ConvertOptions中配置的键名映射为对象的属性。 > **说明：** > > 从API version 9开始支持，从API version 14开始废弃，建议使用 > [fastConvertToJSObject\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_14+\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_替代。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 14

**替代接口：** [xml.ConvertXML#fastConvertToJSObject](arkts-arkts-xml-convertxml-c.md#fastconverttojsobject)

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConvertXML-convertToJSObject(xml: string, options?: ConvertOptions): Object--><!--Device-ConvertXML-convertToJSObject(xml: string, options?: ConvertOptions): Object-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| xml | string | 是 | XML文本，需符合XML语法规范，若包含"&"字符，请使用实体引用"&amp;"替换。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 转换选项，用于自定义XML转换行为。不传入时使用ConvertOptions各属性的默认值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | 转换后的JavaScript对象，包含解析后的XML结构信息，具体属性键名由ConvertOptions定义。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200002](../errorcode-utils.md#10200002-参数解析错误) | Invalid xml string. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let xml =
    '<?xml version="1.0" encoding="utf-8"?>' +
      '<note importance="high" logged="true">' +
      '    <title>Happy</title>' +
      '    <todo>Work</todo>' +
      '    <todo>Play</todo>' +
      '</note>';
  // 创建ConvertXML转换实例
  let converter = new convertxml.ConvertXML();
  // 配置转换选项
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
  // 调用convertToJSObject接口转换XML文本（已废弃，建议使用fastConvertToJSObject）
  let result = JSON.stringify(converter.convertToJSObject(xml, options));
  console.info(result);
} catch (e) {
  let err: BusinessError = e as BusinessError;
  console.error(`Failed to convert XML text to JS object using convertToJSObject. Code: ${err.code}, message: ${err.message}`);
}
// 输出(宽泛型)
// {"_declaration":{"_attributes":{"version":"1.0","encoding":"utf-8"}},"_elements":[{"_type":"element","_name":"note","_attributes":{"importance":"high","logged":"true"},"_elements":[{"_type":"element","_name":"title","_elements":[{"_type":"text","_text":"Happy"}]},{"_type":"element","_name":"todo","_elements":[{"_type":"text","_text":"Work"}]},{"_type":"element","_name":"todo","_elements":[{"_type":"text","_text":"Play"}]}]}]}
```

## fastConvertToJSObject

```TypeScript
fastConvertToJSObject(xml: string, options?: ConvertOptions): Object
```

将XML文本转换为Object类型对象，适用于XML配置文件解析、数据报文处理等场景。该方法将XML文本解析为层级嵌套结构，各XML组件按ConvertOptions中配置的键名映射为对象的属性。 当单元素文本内容超过10M时，建议使用[largeConvertToJSObject\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_23+\_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_替代。 > **说明：** > > 该接口无法满足解析单元素文本内容超过10M的XML文件，当单元素文本内容超过10M时，会输出异常日志信息并返回一个仅包含XML声明的基础Object对象。 > 如需解析单元素文本内容超过10M的XML文本，建议使用[largeConvertToJSObject\_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_23+\_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ > 替代。 > > 在Windows环境中，通常以回车符（CR）和换行符（LF）一对字符来表示换行。fastConvertToJSObject接口转换后的对象以换行符（LF）表示换行。

**起始版本：** 14

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为14。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-ConvertXML-fastConvertToJSObject(xml: string, options?: ConvertOptions): Object--><!--Device-ConvertXML-fastConvertToJSObject(xml: string, options?: ConvertOptions): Object-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| xml | string | 是 | XML文本，需符合XML语法规范，若包含"&"字符，请使用实体引用"&amp;"替换。单元素文本内容超过10M时，输出异常日志并返回仅包含XML声明的基础Object，建议使用largeConvertToJSObject替代。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 转换选项，用于自定义XML转换行为。不传入时使用ConvertOptions各属性的默认值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | 转换后的JavaScript对象，用于提供解析后的XML结构信息，具体属性键名由ConvertOptions定义，可通过配置键名访问XML各组件的映射数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200002](../errorcode-utils.md#10200002-参数解析错误) | Invalid xml string. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let xml =
    '<?xml version="1.0" encoding="utf-8"?>' +
    '<note importance="high" logged="true">' +
    '   <title>Hello\r\nWorld</title>' +
    '   <todo><![CDATA[Work\r\n]]></todo>' +
    '</note>';
  // 创建ConvertXML转换实例
  let converter = new convertxml.ConvertXML();
  // 配置转换选项
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
  // 调用fastConvertToJSObject接口转换XML文本
  let result = JSON.stringify(converter.fastConvertToJSObject(xml, options));
  console.info(result);
} catch (e) {
  let err: BusinessError = e as BusinessError;
  console.error(`Failed to convert XML text to JS object using fastConvertToJSObject. Code: ${err.code}, message: ${err.message}`);
}
// 输出(宽泛型)
// {"_declaration":{"_attributes":{"version":"1.0","encoding":"utf-8"}},"_elements":[{"_type":"element","_name":"note","_attributes":{"importance":"high","logged":"true"},"_elements":[{"_type":"element","_name":"title","_elements":[{"_type":"text","_text":"Hello\nWorld"}]},{"_type":"element","_name":"todo","_elements":[{"_type":"cdata","_cdata":"Work\n"}]}]}]}
```

## largeConvertToJSObject

```TypeScript
largeConvertToJSObject(xml: string, options?: ConvertOptions): Object
```

将XML文本转换为Object类型对象，适用于XML日志文件、数据报文等大型XML解析场景。此方法支持解析单元素大小超过10M的大型XML文本，针对大文本场景进行了优化，可有效避免单元素文本过大导致的解析异常。 当[fastConvertToJSObject\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_14+\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_因单元素文本内容超过10M无法正常解析时， 可使用本方法作为替代方案。 > **说明：** > > 当传入的XML文本无法正确解析为Object类型对象时，输出异常日志信息并返回一个仅包含XML声明的基础Object对象。 > > 在Windows环境中，通常以回车符（CR）和换行符（LF）一对字符来表示换行。本接口转换后的对象以换行符（LF）表示换行。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ConvertXML-largeConvertToJSObject(xml: string, options?: ConvertOptions): Object--><!--Device-ConvertXML-largeConvertToJSObject(xml: string, options?: ConvertOptions): Object-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| xml | string | 是 | XML文本，需符合XML语法规范，若包含"&"字符，请使用实体引用"&amp;"替换。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 转换选项，用于自定义XML转换行为。不传入时使用ConvertOptions各属性的默认值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | 转换后的JavaScript对象，包含解析后的XML结构信息，具体属性键名由ConvertOptions定义。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200002](../errorcode-utils.md#10200002-参数解析错误) | Invalid xml string. |

**示例：**

```TypeScript
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
  // 创建ConvertXML转换实例
  let converter = new convertxml.ConvertXML();
  // 配置转换选项
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
  // 调用largeConvertToJSObject接口转换大型XML文本
  let result = JSON.stringify(converter.largeConvertToJSObject(xmlString, options));
  console.info(result);
} catch (e) {
  let err: BusinessError = e as BusinessError;
  console.error(`Failed to convert XML text to JS object using largeConvertToJSObject. Code: ${err.code}, message: ${err.message}`);
}
// 输出(宽泛型)
// {"_declaration":{"_attributes":{"version":"1.0","encoding":"utf-8"}},"_elements":[{"_type":"instruction","_name":"custom-pi","_instruction":"processing=\"example\""},{"_type":"element","_name":"catalog","_attributes":{"id":"books"},"_elements":[{"_type":"comment","_comment":" Bestseller Example "},{"_type":"element","_name":"book","_parent":"catalog","_attributes":{"category":"fiction","ref":"B101"},"_elements":[{"_type":"element","_name":"title","_parent":"book","_elements":[{"_type":"text","_text":"Echoes & Whispers"}]},{"_type":"element","_name":"price","_parent":"book","_attributes":{"unit":"USD"},"_elements":[{"_type":"text","_text":"19.99"}]},{"_type":"element","_name":"descr","_parent":"book","_elements":[{"_type":"cdata","_cdata":"<b>suspense</b>novel & Legendary Stories"}]},{"_type":"element","_name":"popular","_parent":"book"}]}]}]}
```

