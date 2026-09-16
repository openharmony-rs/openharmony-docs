# BuilderNode

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [BuilderNode](arkts-arkui-buildernode-c.md) | 提供能够挂载系统组件的自定义节点BuilderNode。BuilderNode仅可作为叶子节点使用，支持通过@Builder生成组件树、实现组件复用与回收、跨节点事件分发以及状态同步，适用于在应用内动态创建和管理自定义组件节点的场景。使用方式参考[BuilderNode开发指南](../../../ui/arkts-user-defined-arktsNode-builderNode.md)。 |
| [ReactiveBuilderNode](arkts-arkui-buildernode-reactivebuildernode-c.md) | ReactiveBuilderNode支持通过无状态的UI方法[@Builder](../../../ui/state-management/arkts-builder.md)生成组件树，并持有该组件树的根节点，不支持定义为状态变量。ReactiveBuilderNode中持有的FrameNode仅用于将此ReactiveBuilderNode作为子节点挂载到其他FrameNode上。对ReactiveBuilderNode持有的FrameNode进行属性设置与子节点操作可能会导致未定义行为，因此不建议通过ReactiveBuilderNode的[getFrameNode](arkts-arkui-buildernode-c.md#getframenode)方法和FrameNode节点的[getRenderNode](arkts-arkui-framenode-c.md#getrendernode)方法获取RenderNode，并通过[RenderNode](arkts-arkui-rendernode-c.md)的接口对其进行属性设置与子节点操作。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [BuildOptions](arkts-arkui-buildernode-buildoptions-i.md) | build的可选参数。 |
| [RenderOptions](arkts-arkui-buildernode-renderoptions-i.md) | 创建BuilderNode时的可选参数。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [NodeRenderType](arkts-arkui-buildernode-noderendertype-e.md) | 节点渲染类型枚举。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [InputEventType](arkts-arkui-inputeventtype-t.md) | [postInputEvent](arkts-arkui-buildernode-c.md#postinputevent)的参数，定义要发送的输入事件类型。 |

## 示例

```TypeScript
### 示例1（BuilderNode中鼠标事件）

该示例演示了在自定义组件中截获鼠标事件并进行坐标转换的完整流程。组件通过[onMouse](../arkui-ts/ts-universal-mouse-key.md#onmouse)回调读取本地x/y，再结合FrameNode.getPositionToParent()得到的偏移量，调用vp2px将相对坐标转换为像素坐标，更新[MouseEvent](../arkui-ts/ts-universal-mouse-key.md#mouseevent对象说明)的windowX/windowY、displayX/displayY。最后通过rootNode.postInputEvent(event)将转换后的鼠标事件分发给子节点进行处理。


```

```TypeScript
### 示例2（BuilderNode中触摸事件）

该示例演示了在自定义组件中截获触摸事件并对触点坐标进行转换的完整流程。在[onTouch](../arkui-ts/ts-universal-events-touch.md#ontouch)回调中，遍历[TouchEvent](../arkui-ts/ts-universal-events-touch.md#touchevent对象说明)的changedTouches和touches数组，对每个触点的x/y加上组件偏移量并调用vp2px转换为像素，更新各自的windowX/windowY、displayX/displayY。最后同样通过rootNode.postInputEvent(event)将转换后的触摸事件分发给子节点处理。


```

```TypeScript
### 示例3（BuilderNode中轴事件）

该示例演示了在自定义组件中截获滚轮或触控板轴事件并进行坐标转换的完整流程。在[onAxisEvent](../arkui-ts/ts-universal-events-axis.md#onaxisevent)回调中，先获取事件的相对x/y，再加上组件偏移量后调用vp2px转换为像素，更新AxisEvent的windowX/windowY、displayX/displayY，最后通过rootNode.postInputEvent(event)将转换后的轴事件分发给子节点进行处理。


```

```TypeScript
### 示例4（BuilderNode共享localStorage）

该示例演示了如何通过BuilderNode的build方法传入外部[localStorage](../arkui-ts/ts-state-management.md#localstorage9)，此时挂载在BuilderNode的所有自定义组件共享该localStorage。
```

```TypeScript
### 示例5（BuilderNode支持内部@Consume接收外部的@Provide数据）

设置BuilderNode的[BuildOptions](arkts-arkui-buildernode-buildoptions-i.md)中enableProvideConsumeCrossing为true，以实现BuilderNode内部自定义组件的@Consume与所在自定义组件的@Provide双向同步。


```

```TypeScript
### 示例6（BuilderNode支持内部@Consumer接收外部的@Provider数据）

> 说明：
> 
> 从API version 23开始，支持跨BuilderNode配对@Provider和@Consumer。

设置BuilderNode的[BuildOptions](arkts-arkui-buildernode-buildoptions-i.md)中enableProvideConsumeCrossing为true，以实现BuilderNode内部自定义组件的@Consumer变量与所在自定义组件的@Provider装饰的状态变量双向同步。


```

```TypeScript
### 示例7（BuilderNode上下树时的同步关系变化）

> 说明：
> 
> 从API version 23开始，支持跨BuilderNode配对@Provider和@Consumer。

该示例演示了BuilderNode挂载到组件树和从组件树卸载时，@Consumer与@Provider的同步关系变化。
```

```TypeScript
### 示例8（BuilderNode上树后再上另一棵树时的同步关系变化）

> 说明：
> 
> 从API version 23开始，支持跨BuilderNode配对@Provider和@Consumer。

该示例演示了BuilderNode挂载到组件树后，再挂载到另一个组件树时，@Consumer与@Provider的同步关系变化。
```

```TypeScript
### 示例9（BuilderNode互相嵌套的场景下的同步关系变化）

> 说明：
> 
> 从API version 23开始，支持跨BuilderNode配对@Provider和@Consumer。

该示例演示了BuilderNode互相嵌套场景下@Consumer和@Provider的同步关系变化。
```

```TypeScript
### 示例10（BuilderNode下的@Consumer所在组件还有其他子组件时的同步关系）

> 说明：
> 
> 从API version 23开始，支持跨BuilderNode配对@Provider和@Consumer。

该示例演示了当@Consumer所在的自定义组件在BuilderNode下且该自定义组件存在子组件时，@Consumer和@Provider之间的同步关系。
```

```TypeScript
### 示例11（组件树为@Provider-@Consumer-BuilderNode-@Consumer时的同步关系）

> 说明：
> 
> 从API version 23开始，支持跨BuilderNode配对@Provider和@Consumer。

该示例演示了组件树为@Provider-@Consumer-BuilderNode-@Consumer的情况时，@Consumer和@Provider之间的同步关系。
```

```TypeScript
### 示例12（组件树为@Provider-BuilderNode-@Provider-@Consumer时的同步关系）

> 说明：
> 
> 从API version 23开始，支持跨BuilderNode配对@Provider和@Consumer。

该示例演示了组件树为@Provider-BuilderNode-@Provider-@Consumer的情况时，@Consumer和@Provider之间的同步关系。
```

```TypeScript
### 示例13（ReactiveBuilderNode中鼠标事件）

从API version 22版本开始支持。

该示例演示了在自定义组件中截获鼠标事件并进行坐标转换的完整流程。组件通过[onMouse](../arkui-ts/ts-universal-mouse-key.md#onmouse)回调读取本地x/y坐标，再结合FrameNode.getPositionToParent()得到的偏移量，调用[vp2px](./arkts-apis-uicontext-uicontext.md#vp2px12)将相对坐标转换为像素坐标，更新[MouseEvent](../arkui-ts/ts-universal-mouse-key.md#mouseevent对象说明)的windowX/windowY、displayX/displayY。最后通过rootNode.postInputEvent将转换后的鼠标事件分发给子节点进行处理。


```

```TypeScript
### 示例14（ReactiveBuilderNode中触摸事件）

从API version 22版本开始支持。

该示例演示了在自定义组件中截获触摸事件并对触点坐标进行转换的完整流程。在[onTouch](../arkui-ts/ts-universal-events-touch.md#ontouch)回调中，遍历[TouchEvent](../arkui-ts/ts-universal-events-touch.md#touchevent对象说明)的changedTouches和touches数组，对每个触点的x/y坐标加上组件偏移量并调用[vp2px](./arkts-apis-uicontext-uicontext.md#vp2px12)转换为像素，更新各自的windowX/windowY、displayX/displayY。最后同样通过rootNode.postInputEvent将转换后的触摸事件分发给子节点处理。


```

```TypeScript
### 示例15（ReactiveBuilderNode中轴事件）

从API version 22版本开始支持。

该示例演示了在自定义组件中截获滚轮或触控板轴事件并进行坐标转换的完整流程。在[onAxisEvent](../arkui-ts/ts-universal-events-axis.md#onaxisevent)回调中，先获取事件的相对x/y坐标，再加上组件偏移量后调用[vp2px](./arkts-apis-uicontext-uicontext.md#vp2px12)转换为像素，更新AxisEvent的windowX/windowY、displayX/displayY，最后通过rootNode.postInputEvent将转换后的轴事件分发给子节点进行处理。


```

```TypeScript
### 示例16（BuilderNode中带竞争策略的鼠标事件）

从API version 24开始，新增postInputEventWithStrategy接口。

该示例演示了在自定义组件中截获鼠标事件并进行坐标转换的完整流程。组件通过[onMouse](../arkui-ts/ts-universal-mouse-key.md#onmouse)回调读取当前触点坐标x/y，再结合FrameNode.getPositionToParent得到的偏移量，调用[vp2px](./arkts-apis-uicontext-uicontext.md#vp2px12)将相对坐标转换为像素坐标，更新[MouseEvent](../arkui-ts/ts-universal-mouse-key.md#mouseevent对象说明)的windowX/windowY、displayX/displayY。选择不同的手势竞争策略[CompetitionStrategy](../arkui-ts/ts-appendix-enums.md#competitionstrategy24)，最后通过rootNode.postInputEventWithStrategy将转换后的鼠标事件分发给子节点进行处理。
```

```TypeScript
### 示例17（BuilderNode中带竞争策略的触摸事件）

从API version 24开始，新增postInputEventWithStrategy接口。

该示例演示了在自定义组件中截获触摸事件并对触点坐标进行转换的完整流程。在[onTouch](../arkui-ts/ts-universal-events-touch.md#ontouch)回调中，遍历[TouchEvent](../arkui-ts/ts-universal-events-touch.md#touchevent对象说明)的changedTouches和touches数组，对每个触点的x/y加上组件偏移量并调用[vp2px](./arkts-apis-uicontext-uicontext.md#vp2px12)转换为像素，更新每个触点的windowX/windowY、displayX/displayY。选择不同的手势竞争策略[CompetitionStrategy](../arkui-ts/ts-appendix-enums.md#competitionstrategy24)，最后同样通过rootNode.postInputEventWithStrategy将转换后的触摸事件分发给子节点处理。
```

```TypeScript
### 示例18（BuilderNode中带竞争策略的轴事件）

从API version 24开始，新增postInputEventWithStrategy接口。

该示例演示了在自定义组件中截获滚轮或触控板轴事件并进行坐标转换的完整流程。在[onAxisEvent](../arkui-ts/ts-universal-events-axis.md#onaxisevent)回调中，先获取事件的相对x/y，再加上组件偏移量后调用[vp2px](./arkts-apis-uicontext-uicontext.md#vp2px12)转换为像素，更新AxisEvent的windowX/windowY、displayX/displayY，选择不同的手势竞争策略[CompetitionStrategy](../arkui-ts/ts-appendix-enums.md#competitionstrategy24)，最后通过rootNode.postInputEventWithStrategy将转换后的轴事件分发给子节点进行处理。
```
