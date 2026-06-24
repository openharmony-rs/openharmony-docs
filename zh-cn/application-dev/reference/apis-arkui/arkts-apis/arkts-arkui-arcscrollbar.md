# @ohos.arkui.ArcScrollBar

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ArcScrollBarAttribute](arkts-arkui-arcscrollbarattribute-c.md) |  |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ArcScrollBarInterface](arkts-arkui-arcscrollbarinterface-i.md) | 弧形滚动条组件ArcScrollBar，用于配合可滚动组件使用，如[ArcList](arkts-arkui-arclist.md)、[List](arkts-arkui-list.md)、<br/>[Grid](arkts-arkui-grid.md)、[Scroll](arkts-arkui-scroll.md)、<br/>[WaterFlow](arkts-arkui-waterflow.md)。<br/><br/>&gt; **说明：**<br/><br/>&gt; - 该组件从API version 18开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。<br/>&gt;<br/>&gt; - ArcScrollBar不设置宽高时，采用父组件[LayoutConstraint](arkts-arkui-layoutconstraint-i.md#LayoutConstraint)中的maxSize作为宽高。如果ArcScrollBar的<br/>&gt; 父组件存在可滚动组件，如[ArcList](arkts-arkui-arclist.md)、[List](arkts-arkui-list.md)、<br/>&gt; [Grid](arkts-arkui-grid.md)、[Scroll](arkts-arkui-scroll.md)、<br/>&gt; [WaterFlow](arkts-arkui-waterflow.md)，建议设置ArcScrollBar宽高，否则ArcScrollBar的宽高可能为无穷大。<br/>&gt;<br/>&gt; - 该组件支持在Phone、PC/2in1、Tablet、TV、Wearable设备上使用。API version 22及以前版本，在Phone、PC/2in1、Tablet、TV上使用会编译告警，但可以正常运行。<br/> |
| [ArcScrollBarOptions](arkts-arkui-arcscrollbaroptions-i.md) | ArcScrollBar的构造函数参数。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; ArcScrollBar与可滚动组件需通过scroller进行绑定后方能实现联动，且ArcScrollBar与可滚动组件仅限于一对一的绑定方式。<br/> |

### 常量

| 名称 | 说明 |
| --- | --- |
| [ArcScrollBar](arkts-arkui-arkui-arcscrollbar-con.md#ArcScrollBar) | 弧形滚动条组件ArcScrollBar，用于配合可滚动组件使用，如[ArcList](arkts-arkui-arclist.md)、[List](arkts-arkui-list.md)、<br/>[Grid](arkts-arkui-grid.md)、[Scroll](arkts-arkui-scroll.md)、<br/>[WaterFlow](arkts-arkui-waterflow.md)。<br/><br/>&gt; **说明：**<br/><br/>&gt; - 该组件从API version 18开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。<br/>&gt;<br/>&gt; - ArcScrollBar不设置宽高时，采用父组件[LayoutConstraint](arkts-arkui-layoutconstraint-i.md#LayoutConstraint)中的maxSize作为宽高。如果ArcScrollBar的<br/>&gt; 父组件存在可滚动组件，如[ArcList](arkts-arkui-arclist.md)、[List](arkts-arkui-list.md)、<br/>&gt; [Grid](arkts-arkui-grid.md)、[Scroll](arkts-arkui-scroll.md)、<br/>&gt; [WaterFlow](arkts-arkui-waterflow.md)，建议设置ArcScrollBar宽高，否则ArcScrollBar的宽高可能为无穷大。<br/>&gt;<br/>&gt; - 该组件支持在Phone、PC/2in1、Tablet、TV、Wearable设备上使用。API version 22及以前版本，在Phone、PC/2in1、Tablet、TV上使用会编译告警，但可以正常运行。<br/><br/>###### 子组件<br/><br/>不包含子组件。<br/> |
| [ArcScrollBarInstance](arkts-arkui-arkui-arcscrollbar-con.md#ArcScrollBarInstance) | 定义ArcScrollBar组件实例。<br/> |

