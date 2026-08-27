# @ohos.arkui.advanced.SegmentButton

## 导入模块

```TypeScript
import { SegmentButton, SegmentButtonOptions, SegmentButtonItemOptionsArray, TabSegmentButtonOptions, TabSegmentButtonConstructionOptions, CapsuleSegmentButtonOptions, CapsuleSegmentButtonConstructionOptions, SegmentButtonTextItem, SegmentButtonIconItem, SegmentButtonIconTextItem, DimensionNoPercentage, CommonSegmentButtonOptions, ItemRestriction, SegmentButtonItemTuple, SegmentButtonItemArray, SegmentButtonItemOptionsConstructorOptions, SegmentButtonItemOptions, BorderRadiusMode } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [SegmentButtonItemOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptions-c.md) | 分段按钮中的按钮选项。 |
| [SegmentButtonItemOptionsArray](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptionsarray-c.md) | 用于保存按钮信息的数组。 |
| [SegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonoptions-c.md) |  |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [SegmentButton](arkts-arkui-arkui-advanced-segmentbutton-segmentbutton-s.md) | 分段按钮组件包含页签类分段按钮和胶囊类分段按钮。页签类分段按钮适用于页面或内容区域的切换场景；胶囊类分段按钮适用于单选或多选的选择场景，包含胶囊类单选分段按钮和胶囊类多选分段按钮。该组件支持自定义文本颜色、字体大小、字体粗细、背景色、 图片尺寸、内边距、背景模糊材质等外观属性，支持仅文本、仅图标和图标+文本三种按钮样式，并提供无障碍朗读、布局方向镜像、自定义圆角、属性动画等能力，适用于需要快速构建符合设计规范的分段选择界面的场景。 |

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
