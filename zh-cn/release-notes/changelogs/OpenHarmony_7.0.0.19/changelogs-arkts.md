# ArkTS方舟编程语言Changelog

## cl.arkts.1 ConvertXML的fastConvertToJSObject接口解析时丢失同级text节点

**访问级别**

公开接口

**变更原因**

ConvertXML的[fastConvertToJSObject](../../../application-dev/reference/apis-arkts/js-apis-convertxml.md#fastconverttojsobject14)接口在解析XML时，若XML内容包含子元素、与子元素同级的文本节点，会丢失与子元素同级的文本节点。

**变更影响**

此变更涉及应用适配。

变更前：fastConvertToJSObject接口在解析XML时，若XML内容包含子元素、与子元素同级的文本节点，会丢失与子元素同级的文本节点。例如解析 `<root>text1<child>子元素</child>text2</root>` 时，与子元素同级的文本节点"text1"和"text2"会丢失。

变更后：fastConvertToJSObject接口在解析XML时，若XML内容包含子元素、与子元素同级的文本节点，会正确保留与子元素同级的文本节点。

**起始 API Level**

14

**变更发生版本**

从OpenHarmony SDK 7.0.0.19 版本开始。

**变更的接口/组件**

fastConvertToJSObject(xml: string, options?: ConvertOptions) : Object;

**适配指导**

排查应用中是否使用了fastConvertToJSObject接口解析XML内容有包含子元素、与子元素同级的文本节点数据，并检查解析结果是否依赖原有的丢失同级文本节点的行为。

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

本变更修复该问题，fastConvertToJSObject接口现在能够正确解析并保留与子元素同级的文本节点。

## cl.arkts.2 LRUCache模块afterRemoval回调方法入参类型变更

**访问级别**

公开接口

**变更原因**

变更前继承[LRUCache](../../../application-dev/reference/apis-arkts/js-apis-util.md#lrucache9)类型后重写afterRemoval回调方法，在调用clear、updateCapacity接口触发删除操作时，传入回调的入参类型与接口定义不符，无法正常使用。

**变更影响**

变更后需排查应用中继承LRUCache容器并重写了afterRemoval回调方法的场景，在回调中如果将入参的key value作为MapIterator使用时应更改调整为正常LRUCache容器中元素类型。

变更前：在执行clear()和updateCapacity()方法删除元素时传入afterRemoval回调的入参类型为MapIterator。

变更后：在执行clear()和updateCapacity()方法删除元素时传入afterRemoval回调的入参类型为LRUCache中的正常元素类型。


**起始 API Level**

API 12

**变更发生版本**

从OpenHarmony SDK 7.0.0.19 版本开始。

**变更的接口/组件**

afterRemoval(isEvict: boolean, key: K, value: V, newValue: V): void

**适配指导**

变更后需排查应用中继承LRUCache容器并重写了afterRemoval回调方法的场景，在回调中如果将入参的key value作为MapIterator使用时应更改调整为正常LRUCache容器中元素类型。
