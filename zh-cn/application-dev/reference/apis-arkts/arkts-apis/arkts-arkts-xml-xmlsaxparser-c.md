# XmlSAXParser

XmlSAXParser类用于以流式方式解析XML文本。适用于需要边读取边处理的场景，支持从[stream.Readable](arkts-arkts-stream-readable-c.md) 流中读取XML数据并进行解析。

> **说明：**  
>  
> - 本接口采用流式解析的方式，理论上可以解析任意大小的XML文本。但考虑到实际性能表现，建议单次解析的数据大小不超过300MB，以避免解析时间过长影响使用体验。

**起始版本：** 24

<!--Device-xml-class XmlSAXParser--><!--Device-xml-class XmlSAXParser-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { xml } from '@kit.ArkTS';
```

<a id="constructor"></a>
## constructor

```TypeScript
constructor(inputStream: stream.Readable, encoding?: string)
```

XmlSAXParser的构造函数。

> **说明：**  
>  
> - `inputStream`参数必须传入继承自[Readable](arkts-arkts-stream-readable-c.md)且实现  
> [Doread](arkts-arkts-stream-readable-c.md#doread-1)的类。可以传入其他模块中满足该条件的类，如  
> [ReadStream](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-readstream-c.md)。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-XmlSAXParser-constructor(inputStream: stream.Readable, encoding?: string)--><!--Device-XmlSAXParser-constructor(inputStream: stream.Readable, encoding?: string)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inputStream | stream.Readable | 是 | 用于读取XML数据的可读流实例。 |
| encoding | string | 否 | 编码格式，默认为'utf-8'（目前仅支持'utf-8'）。 |

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

let readableStream = new TestReadable();
let saxParser = new xml.XmlSAXParser(readableStream, 'utf-8');

```

<a id="parse"></a>
## parse

```TypeScript
parse(xmlSAXHandler: XmlSAXHandler): void
```

使用SAX（Simple API for XML）方式解析XML数据。

> **说明：**  
>  
> - 在调用parse函数后，用户可以通过控制流的方式来控制解析进度。任意数据块被推入后，解析器会解析相应的进度。具体流控制方式详见  
> [@ohos.util.stream (数据流基类stream)](arkts-util-stream.md)。  
>  
> - 可以配合自动控制数据的流使用，如[ReadStream](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-readstream-c.md)，此时用户不再需要手动控制数据。  
>  
> - parse接口注册了流的on监听器，会自动读取流中的数据。不建议再对流的监听器进行操作或者读取数据，以免发生冲突导致接口能力失效。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-XmlSAXParser-parse(xmlSAXHandler: XmlSAXHandler): void--><!--Device-XmlSAXParser-parse(xmlSAXHandler: XmlSAXHandler): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| xmlSAXHandler | [XmlSAXHandler](arkts-arkts-xml-xmlsaxhandler-i.md) | 是 | SAX处理器对象。 |

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

let readableStream = new TestReadable();
let saxParser = new xml.XmlSAXParser(readableStream);

let handler: xml.XmlSAXHandler = {
  startDocument: () => {
  },
  endDocument: () => {
  },
  startElement: (elementName: string, namespaceURI: string | undefined, qName: string | undefined,
    attributes: Map<string, string>) => {
  },
  endElement: (elementName: string, namespaceURI: string | undefined, qName: string | undefined) => {
  },
  characters: (content: string) => {
  }
};

saxParser.parse(handler);

```

