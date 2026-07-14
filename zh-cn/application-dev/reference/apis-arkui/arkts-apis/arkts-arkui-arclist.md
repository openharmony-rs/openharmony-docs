# @ohos.arkui.ArcList

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ArcListAttribute](arkts-arkui-arclistattribute-c.md) | 除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性： |
| [ArcListItemAttribute](arkts-arkui-arclistitemattribute-c.md) | 除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性： |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ArcListInterface](arkts-arkui-arclistinterface-i.md) | 弧形列表包含一系列列表项。适合连续、多行呈现同类数据，例如图片和文本。 |
| [ArcListItemInterface](arkts-arkui-arclistiteminterface-i.md) | 用来展示列表具体子组件，必须配合[ArcList](arkts-arkui-arclist.md)来使用。@link @ohos.arkui.ArcList}。&gt;&gt; - 当ArcListItem配合[LazyForEach](../../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)使用时，ArcListItem&gt; 子组件在ArcListItem创建时创建。配合[if/else](../../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、&gt; [ForEach](../../../../ui/rendering-control/arkts-rendering-control-foreach.md)使用时，或父组件为&gt; [ArcList](arkts-arkui-arclist.md)时，ArcListItem子组件在ArcListItem布局时创建。&gt;&gt; - 该组件支持在Phone、PC/2in1、Tablet、TV、Wearable设备上使用。API version 22及以前版本，在Phone、PC/2in1、Tablet、TV上使用会编译告警，但可以正常运行。 |
| [ArkListOptions](arkts-arkui-arklistoptions-i.md) | 包含创建ArcList组件的基础参数。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ArcScrollIndexHandler](arkts-arkui-arcscrollindexhandler-t.md) | 有子组件划入或划出ArcList显示区域时触发的回调。 |

### 常量

| 名称 | 说明 |
| --- | --- |
| [ArcList](arkts-arkui-arkui-arclist-con.md#arclist) | 弧形列表包含一系列列表项。适合连续、多行呈现同类数据，例如图片和文本。@link @ohos.arkui.ArcList}子组件。 |
| [ArcListInstance](arkts-arkui-arkui-arclist-con.md#arclistinstance) | 定义ArcList组件实例。 |
| [ArcListItem](arkts-arkui-arkui-arclist-con.md#arclistitem) | 用来展示列表具体子组件，必须配合[ArcList](arkts-arkui-arclist.md)来使用。@link @ohos.arkui.ArcList}。&gt;&gt; - 当ArcListItem配合[LazyForEach](../../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)使用时，ArcListItem&gt; 子组件在ArcListItem创建时创建。配合[if/else](../../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、&gt; [ForEach](../../../../ui/rendering-control/arkts-rendering-control-foreach.md)使用时，或父组件为&gt; [ArcList](arkts-arkui-arclist.md)时，ArcListItem子组件在ArcListItem布局时创建。&gt;&gt; - 该组件支持在Phone、PC/2in1、Tablet、TV、Wearable设备上使用。API version 22及以前版本，在Phone、PC/2in1、Tablet、TV上使用会编译告警，但可以正常运行。###### 子组件可以包含单个子组件。 |
| [ArcListItemInstance](arkts-arkui-arkui-arclist-con.md#arclistiteminstance) | 定义ArcListItem组件实例。 |

