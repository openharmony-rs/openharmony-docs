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
| [SegmentButton](arkts-arkui-arkui-advanced-segmentbutton-segmentbutton-s.md) | 分段按钮组件包含页签类分段按钮和胶囊类分段按钮。页签类分段按钮适用于页面或内容区域的切换场景；胶囊类分段按钮适用于单选或多选的选择场景，包含胶囊类单选分段按钮和胶囊类多选分段按钮。该组件支持自定义文本颜色、字体大小、字体粗细、背景色、图片尺寸、内边距、背景模糊材质等外观属性，支持仅文本、仅图标和图标+文本三种按钮样式，并提供无障碍朗读、布局方向镜像、自定义圆角、属性动画等能力，适用于需要快速构建符合设计规范的分段选择界面的场景。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CapsuleSegmentButtonConstructionOptions](arkts-arkui-arkui-advanced-segmentbutton-capsulesegmentbuttonconstructionoptions-i.md) | 用于构建胶囊类的SegmentButtonOptions对象。 |
| [CapsuleSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-capsulesegmentbuttonoptions-i.md) | 胶囊类分段按钮选项。继承自[CapsuleSegmentButtonConstructionOptions](arkts-arkui-arkui-advanced-segmentbutton-capsulesegmentbuttonconstructionoptions-i.md)。 |
| [CommonSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-commonsegmentbuttonoptions-i.md) | 定义分段按钮组件的可自定义的属性。 |
| [SegmentButtonIconItem](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttoniconitem-i.md) | 图标按钮信息。 |
| [SegmentButtonIconTextItem](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonicontextitem-i.md) | 图标与文本按钮信息。 |
| [SegmentButtonItemOptionsConstructorOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptionsconstructoroptions-i.md) | 构造参数用于SegmentButtonItemOptions。 |
| [SegmentButtonTextItem](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttontextitem-i.md) | 文本按钮信息。 |
| [TabSegmentButtonConstructionOptions](arkts-arkui-arkui-advanced-segmentbutton-tabsegmentbuttonconstructionoptions-i.md) | 构建页签类的SegmentButtonOptions对象。 |
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

## 示例

```TypeScript
### 示例1（设置分段按钮的类型）

通过配置SegmentButtonOptions的tab和capsule，创建两种不同类型的分段按钮。


```

```TypeScript
### 示例2（设置分段按钮样式）

通过配置CommonSegmentButtonOptions，实现自定义分段按钮的文本以及背景板样式。


```

```TypeScript
### 示例3（分段按钮数组处理）

该示例通过pop、shift、unshift等函数实现分段按钮数组的添加、移除等操作。


```

```TypeScript
### 示例4（设置镜像效果）

该示例通过配置direction属性设置分段按钮的布局方向，实现镜像效果。


```

```TypeScript
### 示例5（设置无障碍朗读）

通过配置accessibilityLevel和selectedIconAccessibilityText等属性，实现了分段按钮的无障碍朗读功能。


```

```TypeScript
### 示例6（设置自定义圆角）

该示例演示了如何为分段按钮组件设置自定义的边框圆角半径。


```

```TypeScript
### 示例7（开启SegmentButton的属性动画）

本示例展示了SegmentButton开启属性动画，即enableStateAnimation设置为true后，修改选中项编号selectedIndexes值会触发按钮切换动画。并且选中项编号相同的两个SegmentButton组件，是否开启属性动画，也会呈现不同的切换动画。

从API version 24开始，[SegmentButton](#segmentbutton-1)新增enableStateAnimation属性。


```

```TypeScript
### 示例8（设置背景板材质）

以下示例通过backgroundSystemMaterial属性，为分段按钮设置了透明的背景板材质、开启自动反色和交互形变效果，并自定义反馈光感的颜色。

从API版本26.0.0开始，[SegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonoptions-c.md)和[CommonSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-commonsegmentbuttonoptions-i.md)中新增backgroundSystemMaterial属性。

该示例配图为高算力设备强档效果。


```

```TypeScript
### 示例9（监听SegmentButtonOptions内属性的变化）

[SegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonoptions-c.md)使用了@Observed装饰器，SegmentButton组件通过@ObjectLink接收该对象。对于SegmentButtonOptions的一层基本类型属性（如fontColor、backgroundColor等），@Observed与@ObjectLink的联动机制已能观测到属性变化并触发UI刷新，无需额外处理。但对于SegmentButtonOptions中对象类型属性（如imageSize、buttonPadding等）的内部属性（如imageSize的width、height），属于更深层的嵌套属性，@State仅能观测到一层赋值变化，无法感知这类深层属性的修改，导致修改对象类型属性的内部属性时UI不会自动刷新。使用makeObserved接口对对象类型属性（如imageSize）进行包裹，可以为该对象的内部属性补充深度观察能力，使得修改内部属性（如width、height）时，框架能够监听到变化并触发UI刷新。makeObserved接口的详细说明请参考[makeObserved接口：将非观察数据变为可观察数据](../../../ui/state-management/arkts-new-makeObserved.md)。

以下示例对比了两种场景：点击“修改fontColor颜色”按钮修改iconTextCapsuleOptions的fontColor属性（一层基本类型属性，已通过@Observed与@ObjectLink支持观测），UI自动刷新；点击“修改图标大小”按钮修改iconTextCapsuleOptions.imageSize的width和height属性（imageSize对象的内部属性，需通过UIUtils.makeObserved包裹imageSize才能观测），UI同样自动刷新。
```
