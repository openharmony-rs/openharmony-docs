# @ohos.convertxml

本模块提供将XML文本转换为JavaScript对象的解析能力，适用于XML配置文件解析、XML格式网络数据处理、数据迁移与格式转换等场景。 转换过程中，XML的各类组件（声明、指令、元素、属性、文本、CDATA、注释和Doctype等）会按照ConvertOptions中配置的键名映射为JavaScript对象的属性， 形成层级嵌套的对象结构，简化了XML数据的处理流程，支持通过ConvertOptions自定义键名映射实现灵活的输出结构。

**起始版本：** 8

<!--Device-unnamed-declare namespace xml--><!--Device-unnamed-declare namespace xml-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { convertxml } from '@kit.ArkTS';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ConvertXML](arkts-arkts-xml-convertxml-c.md) | ConvertXML类提供将XML文本转换为JavaScript对象的能力。 推荐使用[fastConvertToJSObject&lt;sup&gt;14+&lt;/sup&gt;](arkts-arkts-xml-convertxml-c.md#fastconverttojsobject)进行常规XML文本解析， 当单元素文本内容超过10M时推荐使用[largeConvertToJSObject&lt;sup&gt;23+&lt;/sup&gt;](arkts-arkts-xml-convertxml-c.md#largeconverttojsobject)。 已废弃的[convertToJSObject](arkts-arkts-xml-convertxml-c.md#converttojsobject)和[convert](arkts-arkts-xml-convertxml-c.md#convert)方法不再维护， 建议使用[fastConvertToJSObject&lt;sup&gt;14+&lt;/sup&gt;](arkts-arkts-xml-convertxml-c.md#fastconverttojsobject)替代。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ConvertOptions](arkts-arkts-xml-convertoptions-i.md) | 转换选项，用于自定义XML到JavaScript对象的转换行为，如控制是否修剪空白字符、是否忽略特定组件（声明、指令、属性、注释、CDATA、Doctype和文本等）， 以及指定输出对象中各类型组件的属性键名称。 |

