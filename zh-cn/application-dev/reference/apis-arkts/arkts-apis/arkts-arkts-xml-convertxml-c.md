# ConvertXML

ConvertXML 表示可扩展标记语言。

**起始版本：** 8

<!--Device-xml-class ConvertXML--><!--Device-xml-class ConvertXML-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { convertxml } from '@kit.ArkTS';
```

<a id="convert"></a>
## convert

```TypeScript
convert(xml: string, options?: ConvertOptions): Object
```

转换XML文本为JavaScript对象。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [fastConvertToJSObject](arkts-arkts-xml-convertxml-c.md#fastconverttojsobject-1)

<!--Device-ConvertXML-convert(xml: string, options?: ConvertOptions): Object--><!--Device-ConvertXML-convert(xml: string, options?: ConvertOptions): Object-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| xml | string | 是 | 传入的XML文本。 |
| options | [ConvertOptions](arkts-arkts-xml-convertoptions-i.md) | 否 | 转换选项，默认值是ConvertOptions对象，由其中各个属性的默认值组成。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | 处理后返回的JavaScript对象。 |

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

<a id="converttojsobject"></a>
## convertToJSObject

```TypeScript
convertToJSObject(xml: string, options?: ConvertOptions): Object
```

转换XML文本为Object类型对象。

**起始版本：** 9

**废弃版本：** 14

**替代接口：** [fastConvertToJSObject](arkts-arkts-xml-convertxml-c.md#fastconverttojsobject-1)

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConvertXML-convertToJSObject(xml: string, options?: ConvertOptions): Object--><!--Device-ConvertXML-convertToJSObject(xml: string, options?: ConvertOptions): Object-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| xml | string | 是 | 传入的XML文本，若包含"&"字符，请使用实体引用 **&amp;** 替换。 |
| options | [ConvertOptions](arkts-arkts-xml-convertoptions-i.md) | 否 | 转换选项，默认值是ConvertOptions对象，由其中各个属性的默认值组成。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | 处理后返回的JavaScript对象。 |

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

<a id="fastconverttojsobject"></a>
## fastConvertToJSObject

```TypeScript
fastConvertToJSObject(xml: string, options?: ConvertOptions): Object
```

转换XML文本为Object类型对象。

> **说明**  
>  
> - 该接口无法满足解析大数据量的XML文件，当单元素文本内容超过10M时，会打印异常信息并返回一个仅包含XML标签头的基础Object对象。  
>  
> - 在Windows环境中，通常以回车符（CR）和换行符（LF）一对字符来表示换行。fastConvertToJSObject接口转换后的对象以换行符（LF）表示换行。

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-ConvertXML-fastConvertToJSObject(xml: string, options?: ConvertOptions): Object--><!--Device-ConvertXML-fastConvertToJSObject(xml: string, options?: ConvertOptions): Object-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| xml | string | 是 | XML文本，若包含"&"字符，请使用实体引用 **&amp;** 替换。 |
| options | [ConvertOptions](arkts-arkts-xml-convertoptions-i.md) | 否 | 转换选项，默认值是ConvertOptions对象，由其中各个属性的默认值组成。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | 转换后的JavaScript对象。 |

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

<a id="largeconverttojsobject"></a>
## largeConvertToJSObject

```TypeScript
largeConvertToJSObject(xml: string, options?: ConvertOptions): Object
```

将XML文本转换为Object类型对象，此方法支持解析单个节点大小超过10M的大型XML文本。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ConvertXML-largeConvertToJSObject(xml: string, options?: ConvertOptions): Object--><!--Device-ConvertXML-largeConvertToJSObject(xml: string, options?: ConvertOptions): Object-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| xml | string | 是 | XML文本，若包含"&"字符，请使用实体引用 &amp; 替换。 |
| options | [ConvertOptions](arkts-arkts-xml-convertoptions-i.md) | 否 | 转换选项，默认值是ConvertOptions对象，由其中各个属性的默认值组成。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | 转换后的JavaScript对象。 |

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

