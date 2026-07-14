# ArcScrollBarInterface

弧形滚动条组件ArcScrollBar，用于配合可滚动组件使用，如[ArcList](arkts-arkui-arclist.md)、[List](../arkts-components/arkts-arkui-list.md)、
[Grid](../arkts-components/arkts-arkui-grid.md)、[Scroll](../arkts-components/arkts-arkui-scroll.md)、
[WaterFlow](../arkts-components/arkts-arkui-waterflow.md)。

> **说明：**

> - 该组件从API version 18开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - ArcScrollBar不设置宽高时，采用父组件[LayoutConstraint](arkts-arkui-layoutconstraint-i.md)中的maxSize作为宽高。如果ArcScrollBar的
> 父组件存在可滚动组件，如[ArcList](arkts-arkui-arclist.md)、[List](../arkts-components/arkts-arkui-list.md)、
> [Grid](../arkts-components/arkts-arkui-grid.md)、[Scroll](../arkts-components/arkts-arkui-scroll.md)、
> [WaterFlow](../arkts-components/arkts-arkui-waterflow.md)，建议设置ArcScrollBar宽高，否则ArcScrollBar的宽高可能为无穷大。
>
> - 该组件支持在Phone、PC/2in1、Tablet、TV、Wearable设备上使用。API version 22及以前版本，在Phone、PC/2in1、Tablet、TV上使用会编译告警，但可以正常运行。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## constructor

```TypeScript
(options: ArcScrollBarOptions): ArcScrollBarAttribute
```

ArcScrollBar的构造函数。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | ArcScrollBarOptions | 是 | 滚动条组件参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcScrollBarAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

