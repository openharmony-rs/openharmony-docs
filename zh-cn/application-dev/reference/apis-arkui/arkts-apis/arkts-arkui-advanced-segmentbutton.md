# @ohos.arkui.advanced.SegmentButton

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [SegmentButtonItemOptions](arkts-arkui-segmentbuttonitemoptions-c.md) | 分段按钮中的按钮选项。<br/> |
| [SegmentButtonItemOptionsArray](arkts-arkui-segmentbuttonitemoptionsarray-c.md) | 用于保存按钮信息的数组。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; SegmentButtonItemOptionsArray仅支持保存2到5个按钮信息元素。<br/> |
| [SegmentButtonOptions](arkts-arkui-segmentbuttonoptions-c.md) | &gt; **说明：**<br/>&gt;<br/>&gt; 不支持设置字体类型。<br/><br/>分段按钮选项类用于提供初始数据和自定义属性。<br/> |
| <!--DelRow-->[SegmentButtonOptions](arkts-arkui-segmentbuttonoptions-c-sys.md) | &gt; **说明：**<br/>&gt;<br/>&gt; 不支持设置字体类型。<br/><br/>分段按钮选项类用于提供初始数据和自定义属性。<br/> |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [SegmentButton](arkts-arkui-segmentbutton-s.md) | 分段按钮组件包含页签类分段按钮、胶囊类单选分段按钮和胶囊类多选分段按钮。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 分段按钮不支持[通用属性](ts-component-general-attributes.md)。分段按钮使用当前区域可使用的最大宽度作为组件宽度，并且根据按钮个数平均分配每个按钮宽度；分段按钮高度根据按钮内容（文本及图片）自动适应，其最小高度为28vp。<br/>&gt;<br/>&gt; - @Prop装饰的属性为可选参数，仅当与@Require装饰器联合使用时，才必须在构造时传入对应参数。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CapsuleSegmentButtonConstructionOptions](arkts-arkui-capsulesegmentbuttonconstructionoptions-i.md) | 用于构建胶囊类的SegmentButtonOptions对象。<br/><br/>继承[CommonSegmentButtonOptions](arkts-arkui-commonsegmentbuttonoptions-i.md#CommonSegmentButtonOptions)。<br/> |
| [CapsuleSegmentButtonOptions](arkts-arkui-capsulesegmentbuttonoptions-i.md) | 胶囊类分段按钮选项。继承自[CapsuleSegmentButtonConstructionOptions](arkts-arkui-capsulesegmentbuttonconstructionoptions-i.md#CapsuleSegmentButtonConstructionOptions)。<br/> |
| [CommonSegmentButtonOptions](arkts-arkui-commonsegmentbuttonoptions-i.md) | 定义分段按钮组件的可自定义的属性。<br/> |
| <!--DelRow-->[CommonSegmentButtonOptions](arkts-arkui-commonsegmentbuttonoptions-i-sys.md) | 定义分段按钮组件的可自定义的属性。<br/> |
| [SegmentButtonIconItem](arkts-arkui-segmentbuttoniconitem-i.md) | 图标按钮信息。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 未选中态的图标`icon`和选中态的图标`selectedIcon`都需设置，单独设置无效。<br/> |
| [SegmentButtonIconTextItem](arkts-arkui-segmentbuttonicontextitem-i.md) | 图标与文本按钮信息。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 未选中态的图标`icon`和选中态的图标`selectedIcon`都需设置，单独设置无效。<br/> |
| [SegmentButtonItemOptionsConstructorOptions](arkts-arkui-segmentbuttonitemoptionsconstructoroptions-i.md) | 构造参数用于SegmentButtonItemOptions。<br/> |
| [SegmentButtonTextItem](arkts-arkui-segmentbuttontextitem-i.md) | 文本按钮信息。<br/> |
| [TabSegmentButtonConstructionOptions](arkts-arkui-tabsegmentbuttonconstructionoptions-i.md) | 构建页签类的SegmentButtonOptions对象。<br/><br/>继承[CommonSegmentButtonOptions](arkts-arkui-commonsegmentbuttonoptions-i.md#CommonSegmentButtonOptions)。<br/> |
| [TabSegmentButtonOptions](arkts-arkui-tabsegmentbuttonoptions-i.md) | 页签类分段按钮选项。继承自[TabSegmentButtonConstructionOptions](arkts-arkui-tabsegmentbuttonconstructionoptions-i.md#TabSegmentButtonConstructionOptions)。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BorderRadiusMode](arkts-arkui-borderradiusmode-e.md) | 边框圆角模式枚举，用于控制分段按钮的圆角计算方式。<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |
| [DimensionNoPercentage](arkts-arkui-dimensionnopercentage-t.md) | 不支持百分比类型的长度联合类型。<br/> |
| [ItemRestriction](arkts-arkui-itemrestriction-t.md) | 保存按钮信息的元组类型。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 分段按钮组件仅支持2到5个按钮。<br/> |
| [SegmentButtonItemArray](arkts-arkui-segmentbuttonitemarray-t.md) | 用于保存按钮信息的数组的联合类型。<br/> |
| [SegmentButtonItemTuple](arkts-arkui-segmentbuttonitemtuple-t.md) | 用于保存按钮信息的元组的联合类型。<br/> |

