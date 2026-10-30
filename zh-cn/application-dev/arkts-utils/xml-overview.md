---
kits: ["ArkTS / 方舟编程语言"]
description: "介绍XML（可扩展标记语言）的基本概念：由元素、属性和内容组成文档结构，支持XML Schema与DTD结构校验、命名空间、实体引用等特性，并概述XML生成、解析、转换等基础类库能力。"
keywords: [XML概述, 标记语言, 元素, 属性, 命名空间, DTD, XML生成, XML解析, XML转换]
doctype: guide
status: active
---

# XML概述
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @Malzahar-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->


XML（可扩展标记语言）是一种用于描述数据的标记语言，提供通用的数据传输和存储方式。XML不预定义标记，因此更加灵活，适用于广泛的应用领域。


XML文档由元素（element）、属性（attribute）和内容（content）组成。


- 元素指的是标记对，包含文本、属性或其他元素。

- 属性提供了有关元素的其他信息。

- 内容则是元素包含的数据或子元素。


XML使用XML Schema或DTD（文档类型定义）定义文档结构，开发人员可以利用这些机制创建自定义规则，以验证XML文档的格式是否符合预期规范。


XML支持命名空间、实体引用、注释和处理指令，灵活适应各种数据需求。


语言基础类库提供了XML相关的基础能力，包括：[XML的生成](xml-generation.md)、[XML的解析](xml-parsing.md)和[XML的转换](xml-conversion.md)。

以下是一个简单的XML样例及对应说明，更多XML的接口和具体使用，请见[@ohos.xml](../reference/apis-arkts/js-apis-xml.md)。

```XML
<!-- 声明 -->
<?xml version="1.0" encoding="utf-8"?>
<!-- 处理指令 -->
<?xml-stylesheet type="text/css" href="style.css"?>
<!-- 元素、属性及属性值 -->
<note importance="high">
    <title>Happy</title>
    <!-- 实体引用 -->
    <todo>&amp;</todo>
    <!-- 命名空间的声明及统一资源标识符 -->
    <h:table xmlns:h="http://www.w3.org/TR/html4/">
        <h:tr>
            <h:td>Apples</h:td>
            <h:td>Bananas</h:td>
        </h:tr>
    </h:table>
</note>
```