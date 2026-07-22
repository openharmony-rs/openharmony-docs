# XmlSAXHandler

XmlSAXHandler定义了SAX解析xml文本时的回调方法。开发者需要实现这些回调方法来处理xml文本的不同部分。这些回调方法会在xml解析过程的对应时机触发。startDocument会在开始解析文档时触发，endDocument会在结束文档解析时触发，startElement会在开始解析元素时触发，endElement会在结束解析元素时触发，characters则会在解析元素间文本内容时触发。

**起始版本：** 24

<!--Device-xml-interface XmlSAXHandler--><!--Device-xml-interface XmlSAXHandler-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { xml } from '@kit.ArkTS';
```

## characters

```TypeScript
characters(content: string): void
```

当解析器在XML元素内部遇到文本内容时调用的回调函数。该回调函数需要开发者自行实现。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-XmlSAXHandler-characters(content: string): void--><!--Device-XmlSAXHandler-characters(content: string): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | string | 是 | 解析器回传元素中的文本内容。 |

**示例：**

```TypeScript
import { xml, stream } from '@kit.ArkTS';

class TestReadable extends stream.Readable {
  constructor() {
    super();
  }

  doRead(size: number) {
  }
}

const saxHandler: xml.XmlSAXHandler = {
  startDocument() {
    console.info("startDocument");
  },
  endDocument() {
    console.info("endDocument");
  },
  startElement(elementName: string, namespaceURI: string | undefined, qName: string | undefined,
    attributes: Map<string, string>) {
    console.info("startElement elementName:", elementName);
    console.info("startElement namespaceURI:", namespaceURI);
    console.info("startElement qName:", qName);
    if (attributes) {
      attributes.forEach((value, key) => {
        console.info("startElement attribute:", key, "=", value);
      });
    }
  },
  endElement(elementName: string, namespaceURI: string | undefined, qName: string | undefined) {
    console.info("endElement elementName:", elementName);
  },
  characters(content: string) {
    console.info("characters:", content);
  }
};

let readableStream = new TestReadable();
let saxParser = new xml.XmlSAXParser(readableStream);
saxParser.parse(saxHandler);

let testData = '<?xml version="1.0" encoding="UTF-8"?>\n' +
  '<root xmlns:ns1="http://example.com/ns1">\n' +
  '  <ns1:child ns1:attr1="value1" attr2="value2">Text content</ns1:child>\n' +
  '</root>';

readableStream.push(testData);
readableStream.push(null);
// 输出示例：
// startDocument
// startElement elementName: root
// startElement namespaceURI: undefined
// startElement qName: undefined
// characters: 
// 
// startElement elementName: child
// startElement namespaceURI: http://example.com/ns1
// startElement qName: ns1:child
// startElement attribute: attr2 = value2
// startElement attribute: ns1:attr1 = value1
// characters: Text content
// endElement elementName: child
// characters: 
// endElement elementName: root
// endDocument

```

## endDocument

```TypeScript
endDocument(): void
```

当解析器在XML文本结束解析时触发的回调函数。该回调函数需要开发者自行实现。具体使用示例可见[characters<sup>24+</sup>](arkts-arkts-xml-xmlsaxhandler-i.md#characters)。
> **说明：**  
>  
> 当可读流结束时触发此回调。在stream中调用push()，传入null值，从而触发该回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-XmlSAXHandler-endDocument(): void--><!--Device-XmlSAXHandler-endDocument(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

## endElement

```TypeScript
endElement(elementName: string, namespaceURI: string | undefined, qName: string | undefined): void
```

当解析器在XML文本中元素结束解析触发的回调函数。该回调函数需要开发者自行实现。具体使用示例可见[characters<sup>24+</sup>](arkts-arkts-xml-xmlsaxhandler-i.md#characters)。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-XmlSAXHandler-endElement(elementName: string, namespaceURI: string | undefined, qName: string | undefined): void--><!--Device-XmlSAXHandler-endElement(elementName: string, namespaceURI: string | undefined, qName: string | undefined): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementName | string | 是 | 解析器回传的元素名称（不包含命名空间前缀）。例如，对于`&lt;ns2:child&gt;`，elementName为"child"。 |
| namespaceURI | string \| undefined | 是 | 解析器回传的命名空间URI。例如，对于`xmlns:ns2="http://example.com/ns2"`，namespaceURI为`"http://example.com/ns2"`。如果元素没有命名空间则为undefined。 |
| qName | string \| undefined | 是 | 解析器回传的元素限定名（包含命名空间前缀）。例如，对于`&lt;ns2:child&gt;`，qName为"ns2:child"。如果元素没有命名空间则qName为undefined。 |

## startDocument

```TypeScript
startDocument(): void
```

当解析器在XML文本开始解析时触发的回调函数。该回调函数需要开发者自行实现。具体使用示例可见[characters<sup>24+</sup>](arkts-arkts-xml-xmlsaxhandler-i.md#characters)。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-XmlSAXHandler-startDocument(): void--><!--Device-XmlSAXHandler-startDocument(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

## startElement

```TypeScript
startElement(elementName: string, namespaceURI: string | undefined, qName: string | undefined, attributes: Map<string,string>): void
```

当解析器在XML文本中元素开始解析时触发的回调函数。该回调函数需要开发者自行实现。具体使用示例可见[characters<sup>24+</sup>](arkts-arkts-xml-xmlsaxhandler-i.md#characters)。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-XmlSAXHandler-startElement(elementName: string, namespaceURI: string | undefined, qName: string | undefined, attributes: Map<string,string>): void--><!--Device-XmlSAXHandler-startElement(elementName: string, namespaceURI: string | undefined, qName: string | undefined, attributes: Map<string,string>): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementName | string | 是 | 解析器回传的元素名称（不包含命名空间前缀）。例如，对于`&lt;ns2:child&gt;`，elementName为"child"。 |
| namespaceURI | string \| undefined | 是 | 解析器回传的命名空间URI。例如，对于`xmlns:ns2="http://example.com/ns2"`，namespaceURI为`"http://example.com/ns2"`。如果元素没有命名空间则为undefined。 |
| qName | string \| undefined | 是 | 解析器回传的元素限定名（包含命名空间前缀）。例如，对于`&lt;ns2:child&gt;`，qName为"ns2:child"。如果元素没有命名空间则qName为undefined。 |
| attributes | Map&lt;string,string&gt; | 是 | 解析器回传的元素的属性映射表，键为属性名（可能包含命名空间前缀，如"ns2:attrA"），值为属性值。 |

