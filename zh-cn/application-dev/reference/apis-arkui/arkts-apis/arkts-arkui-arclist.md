# @ohos.arkui.ArcList

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ArcListAttribute](arkts-arkui-arclistattribute-c.md) | 除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md#common)外，还支持以下属性：<br/> |
| [ArcListItemAttribute](arkts-arkui-arclistitemattribute-c.md) | 除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md#common)外，还支持以下属性：<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ArcListInterface](arkts-arkui-arclistinterface-i.md) | 弧形列表包含一系列列表项。适合连续、多行呈现同类数据，例如图片和文本。<br/> |
| [ArcListItemInterface](arkts-arkui-arclistiteminterface-i.md) | 用来展示列表具体子组件，必须配合[ArcList](arkts-arkui-arclist.md)来使用。<br/><br/>&gt; **说明：**<br/><br/>&gt; - 该组件的父组件只能是[ArcList](arkts-arkui-arclist.md)。<br/>&gt;<br/>&gt; - 当ArcListItem配合[LazyForEach](../../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)使用时，ArcListItem<br/>&gt; 子组件在ArcListItem创建时创建。配合[if/else](../../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、<br/>&gt; [ForEach](../../../../ui/rendering-control/arkts-rendering-control-foreach.md)使用时，或父组件为<br/>&gt; [ArcList](arkts-arkui-arclist.md)时，ArcListItem子组件在ArcListItem布局时创建。<br/>&gt;<br/>&gt; - 该组件支持在Phone、PC/2in1、Tablet、TV、Wearable设备上使用。API version 22及以前版本，在Phone、PC/2in1、Tablet、TV上使用会编译告警，但可以正常运行。<br/> |
| [ArkListOptions](arkts-arkui-arklistoptions-i.md) | 包含创建ArcList组件的基础参数。<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ArcScrollIndexHandler](arkts-arkui-arcscrollindexhandler-t.md) | 有子组件划入或划出ArcList显示区域时触发的回调。<br/> |

### 常量

| 名称 | 说明 |
| --- | --- |
| [ArcList](arkts-arkui-arkui-arclist-con.md#ArcList) | 弧形列表包含一系列列表项。适合连续、多行呈现同类数据，例如图片和文本。<br/><br/>&gt; **说明：**<br/><br/>&gt; - 该组件从API version 18开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。<br/>&gt;<br/>&gt; - 该组件支持在Phone、PC/2in1、Tablet、TV、Wearable设备上使用。API version 22及以前版本，在Phone、PC/2in1、Tablet、TV上使用会编译告警，但可以正常运行。<br/><br/>###### 子组件<br/><br/>仅支持[ArcListItem](arkts-arkui-arclist.md)子组件。<br/> |
| [ArcListInstance](arkts-arkui-arkui-arclist-con.md#ArcListInstance) | 定义ArcList组件实例。<br/> |
| [ArcListItem](arkts-arkui-arkui-arclist-con.md#ArcListItem) | 用来展示列表具体子组件，必须配合[ArcList](arkts-arkui-arclist.md)来使用。<br/><br/>&gt; **说明：**<br/><br/>&gt; - 该组件的父组件只能是[ArcList](arkts-arkui-arclist.md)。<br/>&gt;<br/>&gt; - 当ArcListItem配合[LazyForEach](../../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)使用时，ArcListItem<br/>&gt; 子组件在ArcListItem创建时创建。配合[if/else](../../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、<br/>&gt; [ForEach](../../../../ui/rendering-control/arkts-rendering-control-foreach.md)使用时，或父组件为<br/>&gt; [ArcList](arkts-arkui-arclist.md)时，ArcListItem子组件在ArcListItem布局时创建。<br/>&gt;<br/>&gt; - 该组件支持在Phone、PC/2in1、Tablet、TV、Wearable设备上使用。API version 22及以前版本，在Phone、PC/2in1、Tablet、TV上使用会编译告警，但可以正常运行。<br/><br/>###### 子组件<br/><br/>可以包含单个子组件。<br/> |
| [ArcListItemInstance](arkts-arkui-arkui-arclist-con.md#ArcListItemInstance) | 定义ArcListItem组件实例。<br/> |

