# 基础库常见问题
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @lijiamin2025-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->


## 解析大文件xml发生内存溢出（Out of Memory）

由于ArkTS侧提供的XML解析接口暂不支持流式解析模式，建议通过Native工程调用第三方C/C++库来实现。推荐使用**libxml2**库，该库具有成熟稳定、性能优越的特点，能够完美支持SAX等流式解析方式，有效降低内存占用。

具体实施步骤如下：
1. **创建Native工程**：在OpenHarmony项目中创建C++模块。
2. **集成libxml2**：下载并配置libxml2库源码或预编译库，在`CMakeLists.txt`中进行引用。
3. **编写解析代码**：使用libxml2提供的API实现流式解析逻辑。
4. **XML对象处理**：当XML文件大小超过100MB时，建议在Native侧处理。

关于如何在ArkTS侧引用编译生成的三方so库，请参考文档：[如何在ArkTS侧引用其他三方so库](https://developer.huawei.com/consumer/cn/doc/harmonyos-faqs/faqs-ndk-21)。

libxml2库支持的回调函数主要如下所示：
| 回调函数指针 | 触发时机 | 用途 |
| :--- | :--- | :--- |
| `startDocument` | 文档开始时 | 初始化环境，分配资源。 |
| `endDocument` | 文档结束时 | 释放资源，打印统计信息。 |
| `startElement` | 读到开始标签（如`<tag>`） | 获取标签名及其属性。 |
| `endElement` | 读到结束标签（如`</tag>`） | 处理标签结束逻辑，如出栈。 |
| `characters` | 读到标签间的文本内容 | 处理文本数据（注意可能被多次调用）。 |

代码示例：

```c
// 用户自定义数据
ParseContext context;

// 初始化SAX Handler结构体
xmlSAXHandler SAXHandler = { 0 };

// 绑定回调函数，用于在解析过程中处理XML数据
SAXHandler.startDocument = startDocument;
SAXHandler.endDocument = endDocument;
SAXHandler.startElement = startElement;
SAXHandler.endElement = endElement;
SAXHandler.characters = characters;

// 解析文件
// 用户自定义数据指针
int ret = xmlSAXUserParseFile(&SAXHandler, &context, xmlFileName);

if (ret != 0) {
    printf("Failed to parse XML file.\n");
    return 1;
}

// 清理libxml2全局状态
xmlCleanupParser();
```