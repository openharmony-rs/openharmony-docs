# @ohos.xml

本模块提供XML生成和解析的接口。

本模块提供了两种生成XML文件的方式:

* [XmlSerializer](arkts-arkts-xml-xmlserializer-c.md)：适用于已知XML文本大小的情况。* [XmlDynamicSerializer<sup>20+</sup>](arkts-arkts-xml-xmldynamicserializer-c.md)：适用于未知XML文本大小的情况。

本模块提供了两种解析XML文件的方式:

* [XmlPullParser](arkts-arkts-xml-xmlpullparser-c.md)：适用于对xml文本进行随机访问和灵活解析的场景。* [XmlSAXParser<sup>24+</sup>](arkts-arkts-xml-xmlsaxparser-c.md)：适用于流式解析xml文本的场景，当xml文本较大，其他解析方式会消耗较多内存，建议采用流式解析。

> **说明：**  
>  
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。

**起始版本：** 8

<!--Device-unnamed-declare namespace xml--><!--Device-unnamed-declare namespace xml-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { xml } from '@kit.ArkTS';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [XmlDynamicSerializer](arkts-arkts-xml-xmldynamicserializer-c.md) | XmlDynamicSerializer类用于动态生成XML字符串。当无法确定XML内容长度时，推荐使用该类。 |
| [XmlPullParser](arkts-arkts-xml-xmlpullparser-c.md) | XmlPullParser接口用于解析现有的XML文件。 |
| [XmlSAXParser](arkts-arkts-xml-xmlsaxparser-c.md) | XmlSAXParser类用于以流式方式解析XML文本。适用于需要边读取边处理的场景，支持从[stream.Readable](arkts-arkts-stream-readable-c.md) 流中读取XML数据并进行解析。 |
| [XmlSerializer](arkts-arkts-xml-xmlserializer-c.md) | XmlSerializer接口用于生成XML文件。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ParseInfo](arkts-arkts-xml-parseinfo-i.md) | 当前XML解析信息。 |
| [ParseOptions](arkts-arkts-xml-parseoptions-i.md) | XML解析选项。 |
| [XmlSAXHandler](arkts-arkts-xml-xmlsaxhandler-i.md) | XmlSAXHandler定义了SAX解析xml文本时的回调方法。开发者需要实现这些回调方法来处理xml文本的不同部分。这些回调方法会在xml解析过程的对应时机触发。startDocument会在开始解析文档时触发，endDocument会在结束文档解析时触发，startElement会在开始解析元素时触发，endElement会在结束解析元素时触发，characters则会在解析元素间文本内容时触发。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [EventType](arkts-arkts-xml-eventtype-e.md) | 事件类型枚举。**ArkTS-Dyn起始版本：** 8**ArkTS-Sta起始版本：** 23 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [AttributeWithTagCb](arkts-arkts-xml-attributewithtagcb-t.md) | ParseOptions中attributeWithTagCallbackFunction的回调方法，三个字符串参数都是由XML解析器在解析过程中自动提取的，开发者无法直接自定义这些值。开发者只能在回调函数中通过返回值来决定如何处理这些已存在的属性。 |

