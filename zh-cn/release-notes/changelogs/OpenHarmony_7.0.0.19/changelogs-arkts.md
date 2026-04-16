# ArkTS方舟编程语言Changelog

## cl.arkts.1 ConvertXML的fastConvertToJSObject接口解析时丢失同级text节点

**访问级别**

公开接口

**变更原因**

ConvertXML的fastConvertToJSObject接口在解析XML时，当元素包含同级文本节点和子元素时，会丢失同级文本节点内容。

**变更影响**

此变更涉及应用适配。

变更前：fastConvertToJSObject接口在解析包含同级文本节点和子元素的XML时，会丢失同级文本节点。例如解析 `<root>text1<child/>text2</root>` 时，"text1"和"text2"文本节点会丢失。

变更后：fastConvertToJSObject接口在解析包含同级文本节点和子元素的XML时，会正确保留同级文本节点。

**起始 API Level**

14

**变更发生版本**

从OpenHarmony SDK 7.0.0.19 版本开始。

**变更的接口/组件**

fastConvertToJSObject(xml: string, options?: ConvertOptions) : Object;

**适配指导**

排查应用中是否使用了fastConvertToJSObject接口解析包含同级文本节点和子元素的XML数据，并检查解析结果是否依赖原有的丢失同级文本节点的行为。

例如：

```typescript
import { convertxml } from '@kit.ArkTS';

let xml = '<wrapper>前缀文本<child>子内容</child>后缀文本</wrapper>';
let conv = new convertxml.ConvertXML();
let result = JSON.stringify(conv.fastConvertToJSObject(xml));
console.info(result);
```

变更前该用例输出为：

```json
{"_elements":[{"_type":"element","_name":"wrapper","_elements":[{"_type":"element","_name":"child","_parent":"wrapper","_elements":[{"_type":"text","_text":"子内容"}]}]}]}
```

变更后该用例输出为：

```json
{"_elements":[{"_type":"element","_name":"wrapper","_elements":[{"_type":"text","_text":"前缀文本"},{"_type":"element","_name":"child","_parent":"wrapper","_elements":[{"_type":"text","_text":"子内容"}]},{"_type":"text","_text":"后缀文本"}]}]}
```

本变更修复该问题，fastConvertToJSObject接口现在能够正确解析并保留同级文本节点。
