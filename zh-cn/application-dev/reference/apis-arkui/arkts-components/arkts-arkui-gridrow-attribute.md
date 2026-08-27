# GridRow属性/事件

除支持通用属性外，还支持以下属性：除支持通用事件外，还支持以下事件：

**继承/实现关系：** GridRowAttribute extends CommonMethod<GridRowAttribute>

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## alignItems

```TypeScript
alignItems(value: ItemAlign)
```

设置GridRow中的GridCol交叉轴方向对齐方式。GridCol本身也可通过alignSelf([ItemAlign](../arkts-apis/arkts-arkui-itemalign-e.md))设置自身对齐方式。当上述两种对齐方式都设置时，以GridCol自身设置 为准。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ItemAlign](../arkts-apis/arkts-arkui-itemalign-e.md) | 是 | GridRow中的GridCol交叉轴方向对齐方式。 默认值：ItemAlign.Start 非法值：按默认值处理。    **说明：** ItemAlign支持的枚举：ItemAlign.Start、ItemAlign.Center、ItemAlign.End、ItemAlign.Stretch。 |

## onBreakpointChange

```TypeScript
onBreakpointChange(callback: (breakpoints: string) => void)
```

断点发生变化时触发回调。回调函数接收到的breakpoints参数表示当前断点值（取值为`"xs"`、`"sm"`、`"md"`、`"lg"`、`"xl"`、`"xxl"`），开发者可在回调中根据断点值执行相应的UI布局调整或业务 逻辑处理。

> **说明：**
> 
> - 当[断点参照物](../../../reference/apis-arkui/arkui-ts/ts-container-gridrow.md#breakpointsreference枚举说明)设置为
> BreakpointsReference.ComponentSize时，不要在onBreakpointChange回调中动态修改GridRow组件的padding或
> margin属性值，否则可能导致组件尺寸计算循环触发、布局抖动或渲染性能下降。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (breakpoints: string) = & gt; void | 是 | 断点变化时触发的回调函数。参数breakpoints表示当前断点值，取值为`"xs"`、`"sm"`、`"md"`、`"lg"`、`"xl"`、`"xxl"`。 |
