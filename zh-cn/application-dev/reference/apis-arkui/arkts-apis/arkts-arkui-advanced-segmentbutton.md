# @ohos.arkui.advanced.SegmentButton

## 导入模块

```TypeScript
import { CommonSegmentButtonOptions, SegmentButtonItemOptionsConstructorOptions, SegmentButtonIconTextItem, SegmentButtonItemOptions, SegmentButtonTextItem, CapsuleSegmentButtonOptions, SegmentButtonOptions, CapsuleSegmentButtonConstructionOptions, SegmentButtonItemTuple, SegmentButton, SegmentButtonItemArray, SegmentButtonItemOptionsArray, SegmentButtonIconItem, BorderRadiusMode, TabSegmentButtonConstructionOptions, TabSegmentButtonOptions, ItemRestriction, DimensionNoPercentage } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [SegmentButtonItemOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptions-c.md) | 分段按钮中的按钮选项。 |
| [SegmentButtonItemOptionsArray](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptionsarray-c.md) | 用于保存按钮信息的数组。 |
| [SegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonoptions-c.md) |  |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [SegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonoptions-c-sys.md) |  |
<!--DelEnd-->

### 结构体

| 名称 | 说明 |
| --- | --- |
| [SegmentButton](arkts-arkui-arkui-advanced-segmentbutton-segmentbutton-s.md) | 分段按钮组件包含页签类分段按钮、胶囊类单选分段按钮和胶囊类多选分段按钮。@Prop装饰的属性为可选参数，仅当与@Require装饰器联合使用时，才必须在构造时传入对应参数。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CapsuleSegmentButtonConstructionOptions](arkts-arkui-arkui-advanced-segmentbutton-capsulesegmentbuttonconstructionoptions-i.md) | 用于构建胶囊类的SegmentButtonOptions对象。继承[CommonSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-commonsegmentbuttonoptions-i.md)。 |
| [CapsuleSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-capsulesegmentbuttonoptions-i.md) | 胶囊类分段按钮选项。继承自[CapsuleSegmentButtonConstructionOptions](arkts-arkui-arkui-advanced-segmentbutton-capsulesegmentbuttonconstructionoptions-i.md)。 |
| [CommonSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-commonsegmentbuttonoptions-i.md) | 定义分段按钮组件的可自定义的属性。 |
| [SegmentButtonIconItem](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttoniconitem-i.md) | 图标按钮信息。 |
| [SegmentButtonIconTextItem](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonicontextitem-i.md) | 图标与文本按钮信息。 |
| [SegmentButtonItemOptionsConstructorOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptionsconstructoroptions-i.md) | 构造参数用于SegmentButtonItemOptions。 |
| [SegmentButtonTextItem](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttontextitem-i.md) | 文本按钮信息。 |
| [TabSegmentButtonConstructionOptions](arkts-arkui-arkui-advanced-segmentbutton-tabsegmentbuttonconstructionoptions-i.md) | 构建页签类的SegmentButtonOptions对象。继承[CommonSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-commonsegmentbuttonoptions-i.md)。 |
| [TabSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-tabsegmentbuttonoptions-i.md) | 页签类分段按钮选项。继承自[TabSegmentButtonConstructionOptions](arkts-arkui-arkui-advanced-segmentbutton-tabsegmentbuttonconstructionoptions-i.md)。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CommonSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-commonsegmentbuttonoptions-i-sys.md) | 定义分段按钮组件的可自定义的属性。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BorderRadiusMode](arkts-arkui-arkui-advanced-segmentbutton-borderradiusmode-e.md) | 边框圆角模式枚举，用于控制分段按钮的圆角计算方式。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [DimensionNoPercentage](arkts-arkui-dimensionnopercentage-t.md) | 不支持百分比类型的长度联合类型。 |
| [ItemRestriction](arkts-arkui-itemrestriction-t.md) | 保存按钮信息的元组类型。 |
| [SegmentButtonItemArray](arkts-arkui-segmentbuttonitemarray-t.md) | 用于保存按钮信息的数组的联合类型。 |
| [SegmentButtonItemTuple](arkts-arkui-segmentbuttonitemtuple-t.md) | 用于保存按钮信息的元组的联合类型。 |

