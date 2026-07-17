# GridRow属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

除支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下事件：

**继承/实现关系：** GridRowAttribute extends [CommonMethod<GridRowAttribute>](CommonMethod<GridRowAttribute>)

**起始版本：** 9

<!--Device-unnamed-declare class GridRowAttribute extends CommonMethod<GridRowAttribute>--><!--Device-unnamed-declare class GridRowAttribute extends CommonMethod<GridRowAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## alignItems

```TypeScript
alignItems(value: ItemAlign)
```

设置GridRow中的GridCol垂直主轴方向对齐方式。GridCol本身也可通过alignSelf([ItemAlign](../arkts-apis/arkts-arkui-enums-itemalign-e.md))设置自身对齐方式。当上述两种对齐方式都设置时，以GridCol自身设置为准。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-GridRowAttribute-alignItems(value: ItemAlign): GridRowAttribute--><!--Device-GridRowAttribute-alignItems(value: ItemAlign): GridRowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ItemAlign](../arkts-apis/arkts-arkui-enums-itemalign-e.md) | 是 | GridRow中的GridCol垂直主轴方向对齐方式。<br/>默认值：ItemAlign.Start <br />非法值：按默认值处理。<br/>**说明**：<br/>ItemAlign支持的枚举：ItemAlign.Start、ItemAlign.Center、ItemAlign.End、ItemAlign.Stretch。 |

## onBreakpointChange

```TypeScript
onBreakpointChange(callback: (breakpoints: string) => void)
```

断点发生变化时触发回调。

> **说明：**  
>  
> - 当[断点参照物](arkts-arkui-grid-row-breakpointsreference-e.md)设置为BreakpointsReference.ComponentSize时，不建议在onBreakpointChange回调中动态修改GridRow  
> 组件的[padding](arkts-arkui-common-commonmethod-c.md#padding-1)或[margin](arkts-arkui-common-commonmethod-c.md#margin-1)属性值。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-GridRowAttribute-onBreakpointChange(callback: (breakpoints: string) => void): GridRowAttribute--><!--Device-GridRowAttribute-onBreakpointChange(callback: (breakpoints: string) => void): GridRowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (breakpoints: string) => void | 是 | breakpoints取值为`"xs"`、`"sm"`、`"md"`、`"lg"`、`"xl"`、`"xxl"`。 |

