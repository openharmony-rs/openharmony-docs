# XML转换
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @xliu-huanwei; @shilei123; @huanghello-->
<!--Designer: @yuanyao14-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->


将XML文本转换为JavaScript对象，便于处理和操作数据，适用于JavaScript应用程序。


语言基础类库提供ConvertXML类，将XML文本转换为JavaScript对象，输入为待转换的XML字符串及转换选项，输出为转换后的JavaScript对象。具体转换选项可见[API参考@ohos.convertxml](../reference/apis-arkts/js-apis-convertxml.md)。


## 注意事项

XML解析及转换需要确保传入的XML数据符合XML标准格式。


## 开发步骤

以XML转换为JavaScript对象为例，说明如何获取标签值。

1. 引入所需的模块。

   <!-- @[xmlChange_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsCommonLibrary/XmlGenerationParsingAndConversion/XmlConversion/entry/src/main/ets/pages/Index.ets) -->

2. 输入待转换的XML，设置转换选项。支持的转换选项及含义，请参见[ConvertOptions](../reference/apis-arkts/js-apis-convertxml.md#convertoptions)。

   > **说明：**
   >
   > 请确保传入的XML文本符合标准格式，若包含“&”字符，请使用实体引用“\&amp;”替换。

   <!-- @[xmlChange_option](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsCommonLibrary/XmlGenerationParsingAndConversion/XmlConversion/entry/src/main/ets/pages/Index.ets) -->  

3. 调用fastConvertToJSObject函数并打印结果。

   <!-- @[xmlChange_console](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsCommonLibrary/XmlGenerationParsingAndConversion/XmlConversion/entry/src/main/ets/pages/Index.ets) -->  

   输出结果如下所示：

   ```json
   strRes:
   {"_declaration":{"_attributes":{"version":"1.0","encoding":"utf-8"}},"_elements":[{"_type":"element","_name":"note",
    "_attributes":{"importance":"high","logged":"true"},"_elements":[{"_type":"element","_name":"title","_parent":"note",
    "_elements":[{"_type":"text","_text":"Happy"}]},{"_type":"element","_name":"todo","_parent":"note","_elements":
    [{"_type":"text","_text":"Work"}]},{"_type":"element","_name":"todo","_parent":"note","_elements":[{"_type":"text",
    "_text":"Play"}]}]}]}
   ```
