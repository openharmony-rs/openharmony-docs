# XML生成
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @xliu-huanwei; @shilei123; @huanghello-->
<!--Designer: @yuanyao14-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->


XML可以作为数据交换格式，被各种系统和应用程序支持。例如Web服务，可以将结构化数据以XML格式进行传递。


XML还可以作为消息传递格式，用于分布式系统中不同节点的通信。


## 注意事项

- XML标签必须成对出现，生成开始标签就要生成结束标签。

- XML标签对大小写敏感，开始标签与结束标签大小写要一致。


## 开发步骤

XML模块提供`XmlSerializer`及`XmlDynamicSerializer`类来生成XML数据，使用`XmlSerializer`需传入固定长度的`ArrayBuffer`或`DataView`对象作为输出缓冲区，用于存储序列化后的XML数据。

`XmlDynamicSerializer`类动态扩容，程序根据实际生成的数据大小自动创建`ArrayBuffer`。

调用不同的方法写入不同的内容，如startElement(name: string)写入元素开始标记，setText(text: string)写入标签值。

XML模块的API接口可以参考[@ohos.xml](../reference/apis-arkts/js-apis-xml.md)的详细描述，按需求调用相应的函数可以生成一份完整的XML数据。

使用XmlSerializer生成XML示例如下：

1. 引入模块。

   <!-- @[xmlSerializer_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsCommonLibrary/XmlGenerationParsingAndConversion/XMLGeneration/entry/src/main/ets/pages/XmlSerializer.ets) -->
   
   ``` TypeScript
   import { xml, util } from '@kit.ArkTS';
   ```

2. 创建缓冲区，构造XmlSerializer对象。可以基于ArrayBuffer构造XmlSerializer对象，也可以基于DataView构造XmlSerializer对象。

   方式1：基于ArrayBuffer构造XmlSerializer对象

   <!-- @[xmlSerializer_new](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsCommonLibrary/XmlGenerationParsingAndConversion/XMLGeneration/entry/src/main/ets/pages/XmlSerializer.ets) -->
   
   ``` TypeScript
   let arrayBuffer: ArrayBuffer = new ArrayBuffer(2048); // 创建一个2048字节的缓冲区
   let serializer: xml.XmlSerializer = new xml.XmlSerializer(arrayBuffer); // 基于ArrayBuffer构造XmlSerializer对象
   ```

   方式2：基于DataView构造XmlSerializer对象

   <!-- @[xmlSerializer_differentFunction](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsCommonLibrary/XmlGenerationParsingAndConversion/XMLGeneration/entry/src/main/ets/pages/XmlSerializer.ets) -->

3. 调用XML元素生成函数。

   <!-- @[xmlSerializer_function](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsCommonLibrary/XmlGenerationParsingAndConversion/XMLGeneration/entry/src/main/ets/pages/XmlSerializer.ets) -->

4. 使用Uint8Array操作ArrayBuffer，并调用TextDecoder对Uint8Array解码后输出。

   <!-- @[xmlSerializer_console](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsCommonLibrary/XmlGenerationParsingAndConversion/XMLGeneration/entry/src/main/ets/pages/XmlSerializer.ets) -->

   输出结果如下：

   ```xml
   <?xml version="1.0" encoding="utf-8"?><bookstore>
     <book category="COOKING">
       <title lang="en">Everyday</title>
       <author>Giana</author>
       <year>2005</year>
     </book>
   </bookstore>
   ```

使用`XmlDynamicSerializer`生成XML示例如下：

1. 引入模块。

   <!-- @[xmlDySerializer_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsCommonLibrary/XmlGenerationParsingAndConversion/XMLGeneration/entry/src/main/ets/pages/XmlDynamicSerializer.ets) -->

2. 调用XML元素生成函数。

   <!-- @[xmlDySerializer_function](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsCommonLibrary/XmlGenerationParsingAndConversion/XMLGeneration/entry/src/main/ets/pages/XmlDynamicSerializer.ets) -->

3. 使用Uint8Array操作ArrayBuffer，并调用TextDecoder对Uint8Array解码后输出。

   <!-- @[xmlDySerializer_console](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsCommonLibrary/XmlGenerationParsingAndConversion/XMLGeneration/entry/src/main/ets/pages/XmlDynamicSerializer.ets) -->

   输出结果如下：

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <bookstore>
     <book category="COOKING">
       <title lang="en">Everyday</title>
       <author>Giana</author>
       <year>2005</year>
     </book>
   </bookstore>
   ```