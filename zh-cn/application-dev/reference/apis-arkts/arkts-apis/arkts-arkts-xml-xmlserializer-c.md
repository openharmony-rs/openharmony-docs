# XmlSerializer

XmlSerializer接口用于生成XML文件。

**起始版本：** 8

<!--Device-xml-class XmlSerializer--><!--Device-xml-class XmlSerializer-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { xml } from '@kit.ArkTS';
```

<a id="addemptyelement"></a>
## addEmptyElement

```TypeScript
addEmptyElement(name: string): void
```

添加一个空元素。

> **说明：**  
>  
> 该接口对所添加数据不做标准XML校验处理，确保所添加的数据符合标准XML规范。例如不允许添加数字开头的元素名称。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-XmlSerializer-addEmptyElement(name: string): void--><!--Device-XmlSerializer-addEmptyElement(name: string): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 元素的名称。 |

**示例：**

```TypeScript
import { util } from '@kit.ArkTS';

let arrayBuffer = new ArrayBuffer(2048);
let thatSer = new xml.XmlSerializer(arrayBuffer);
thatSer.addEmptyElement("d");
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <d/>

```

<a id="constructor"></a>
## constructor

```TypeScript
constructor(buffer: ArrayBuffer | DataView, encoding?: string)
```

XmlSerializer的构造函数。

> **说明：**  
>  
> buffer是开发者根据需要自定义大小的缓存区域，用于临时存储生成的XML文本。在使用过程中必须确保缓存区域足以容纳生成的文本内容。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-XmlSerializer-constructor(buffer: ArrayBuffer | DataView, encoding?: string)--><!--Device-XmlSerializer-constructor(buffer: ArrayBuffer | DataView, encoding?: string)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | ArrayBuffer \| DataView | 是 | 用于接收写入XML信息的ArrayBuffer或DataView内存。 |
| encoding | string | 否 | 编码格式，默认'utf-8'（目前仅支持'utf-8'）。 |

**示例：**

```TypeScript
let arrayBuffer = new ArrayBuffer(2048);
let xmlSerializer = new xml.XmlSerializer(arrayBuffer, "utf-8");

```

<a id="endelement"></a>
## endElement

```TypeScript
endElement(): void
```

添加元素结束标记。

> **说明：**  
>  
> 调用该接口前必须先调用[startElement](arkts-arkts-xml-xmlserializer-c.md#startelement-1)接口写入元素开始标记。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-XmlSerializer-endElement(): void--><!--Device-XmlSerializer-endElement(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**示例：**

```TypeScript
import { util } from '@kit.ArkTS';

let arrayBuffer = new ArrayBuffer(2048);
let thatSer = new xml.XmlSerializer(arrayBuffer);
thatSer.startElement("note");
thatSer.setText("Happy");
thatSer.endElement();
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result);
// <note>Happy</note>

```

<a id="setattributes"></a>
## setAttributes

```TypeScript
setAttributes(name: string, value: string): void
```

添加元素的属性和属性值。

> **说明：**  
>  
> 该接口对所添加数据不做标准XML校验处理，确保所添加的数据符合标准XML规范。例如不允许添加数字开头的属性名称以及添加多个同名的属性名称。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-XmlSerializer-setAttributes(name: string, value: string): void--><!--Device-XmlSerializer-setAttributes(name: string, value: string): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 属性。 |
| value | string | 是 | 属性值。 |

**示例：**

```TypeScript
import { util } from '@kit.ArkTS';

let arrayBuffer = new ArrayBuffer(2048);
let thatSer = new xml.XmlSerializer(arrayBuffer);
thatSer.startElement("note");
thatSer.setAttributes("importance", "high");
thatSer.endElement();
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <note importance="high"/>

```

<a id="setcdata"></a>
## setCDATA

```TypeScript
setCDATA(text: string): void
```

提供在CDATA标签中添加数据的能力，所生成的CDATA标签结构为："\<!\[CDATA\[" + 所添加的数据 + "\]\]\>"。

> **说明：**  
>  
> 该接口对所添加数据不做标准XML校验处理，请确保所添加的数据符合标准XML规范。比如不允许在CDATA标签中添加包含"\]\]\>"字符串的数据。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-XmlSerializer-setCDATA(text: string): void--><!--Device-XmlSerializer-setCDATA(text: string): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | CDATA属性的内容。 |

**示例：**

```TypeScript
import { util } from '@kit.ArkTS';

let arrayBuffer = new ArrayBuffer(2048);
let thatSer = new xml.XmlSerializer(arrayBuffer);
thatSer.setCDATA('root SYSTEM')
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <![CDATA[root SYSTEM]]>

```

<a id="setcomment"></a>
## setComment

```TypeScript
setComment(text: string): void
```

添加注释内容。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-XmlSerializer-setComment(text: string): void--><!--Device-XmlSerializer-setComment(text: string): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 当前元素的注释内容。 |

**示例：**

```TypeScript
import { util } from '@kit.ArkTS';

let arrayBuffer = new ArrayBuffer(2048);
let thatSer = new xml.XmlSerializer(arrayBuffer);
thatSer.setComment("Hello, World!");
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <!--Hello, World!-->

```

<a id="setdeclaration"></a>
## setDeclaration

```TypeScript
setDeclaration(): void
```

设置带有编码信息的文件声明。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-XmlSerializer-setDeclaration(): void--><!--Device-XmlSerializer-setDeclaration(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**示例：**

```TypeScript
import { util } from '@kit.ArkTS';

let arrayBuffer = new ArrayBuffer(2048);
let thatSer = new xml.XmlSerializer(arrayBuffer);
thatSer.setDeclaration();
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result);
// <?xml version="1.0" encoding="utf-8"?>

```

<a id="setdoctype"></a>
## setDocType

```TypeScript
setDocType(text: string): void
```

添加文档类型。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-XmlSerializer-setDocType(text: string): void--><!--Device-XmlSerializer-setDocType(text: string): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | DocType属性的内容。 |

**示例：**

```TypeScript
import { util } from '@kit.ArkTS';

let arrayBuffer = new ArrayBuffer(2048);
let thatSer = new xml.XmlSerializer(arrayBuffer);
thatSer.setDocType('root SYSTEM "http://www.test.org/test.dtd"');
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <!DOCTYPE root SYSTEM "http://www.test.org/test.dtd">

```

<a id="setnamespace"></a>
## setNamespace

```TypeScript
setNamespace(prefix: string, namespace: string): void
```

添加当前元素标记的命名空间。

> **说明：**  
>  
> 该接口对所添加数据不做标准XML校验处理，请确保所添加的数据符合标准XML规范。例如禁止添加数字开头的前缀以及为同一个元素设置多个命名空间。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-XmlSerializer-setNamespace(prefix: string, namespace: string): void--><!--Device-XmlSerializer-setNamespace(prefix: string, namespace: string): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| prefix | string | 是 | 当前元素及其子元素的前缀。 |
| namespace | string | 是 | 当前元素及其子元素的命名空间。 |

**示例：**

```TypeScript
import { util } from '@kit.ArkTS';

let arrayBuffer = new ArrayBuffer(2048);
let thatSer = new xml.XmlSerializer(arrayBuffer);
thatSer.setNamespace("h", "http://www.w3.org/TR/html4/");
thatSer.startElement("note");
thatSer.endElement();
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result);
// <h:note xmlns:h="http://www.w3.org/TR/html4/"/>

```

<a id="settext"></a>
## setText

```TypeScript
setText(text: string): void
```

添加标签值。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-XmlSerializer-setText(text: string): void--><!--Device-XmlSerializer-setText(text: string): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | text属性的内容。 |

**示例：**

```TypeScript
import { util } from '@kit.ArkTS';

let arrayBuffer = new ArrayBuffer(2048);
let thatSer = new xml.XmlSerializer(arrayBuffer);
thatSer.startElement("note");
thatSer.setAttributes("importance", "high");
thatSer.setText("Happy");
thatSer.endElement();
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result); // <note importance="high">Happy</note>

```

<a id="startelement"></a>
## startElement

```TypeScript
startElement(name: string): void
```

根据给定名称添加元素开始标记。

> **说明：**  
>  
> - 调用该接口后须调用[endElement](arkts-arkts-xml-xmlserializer-c.md#endelement-1)写入元素结束标记，以确保节点正确闭合。  
>  
> - 该接口对所添加数据不做标准XML校验处理，请确保所添加的数据符合标准XML规范。比如不允许添加数字开头的元素名称。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-XmlSerializer-startElement(name: string): void--><!--Device-XmlSerializer-startElement(name: string): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 当前元素的元素名。 |

**示例：**

```TypeScript
import { util } from '@kit.ArkTS';

let arrayBuffer = new ArrayBuffer(2048);
let thatSer = new xml.XmlSerializer(arrayBuffer);
thatSer.startElement("note");
thatSer.setText("Happy");
thatSer.endElement();
let uint8 = new Uint8Array(arrayBuffer);
let result = util.TextDecoder.create().decodeToString(uint8);
console.info(result);
// <note>Happy</note>

```

