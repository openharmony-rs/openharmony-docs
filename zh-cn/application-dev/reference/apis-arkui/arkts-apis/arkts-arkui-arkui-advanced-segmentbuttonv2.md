# @ohos.arkui.advanced.SegmentButtonV2(api/@ohos.arkui.advanced.SegmentedButton.d.ts)

## 导入模块

```TypeScript
import { SegmentButtonV2ItemOptions, OnSelectedIndexChange, OnSelectedIndexesChange, SegmentButtonV2Item, SegmentButtonV2Items, TabSegmentButtonV2, CapsuleSegmentButtonV2, MultiCapsuleSegmentButtonV2 } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [SegmentButtonV2Item](arkts-arkui-arkui-advanced-segmentbuttonv2-segmentbuttonv2item-c.md) |  |
| [SegmentButtonV2Items](arkts-arkui-arkui-advanced-segmentbuttonv2-segmentbuttonv2items-c.md) | 分段按钮选项集合。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [CapsuleSegmentButtonV2](arkts-arkui-arkui-advanced-segmentbuttonv2-capsulesegmentbuttonv2-s.md) | 分段按钮组件用于创建页签型、单选或多选的胶囊型分段按钮，支持文本、图标、Symbol等多种选项类型及图文混合配置，可自定义字体、颜色、圆角等样式。页签型分段按钮适用于页签切换场景，单选胶囊型分段按钮适用于单选切换场景，多选胶囊型分段按钮适用于多选筛选场景。 |
| [MultiCapsuleSegmentButtonV2](arkts-arkui-arkui-advanced-segmentbuttonv2-multicapsulesegmentbuttonv2-s.md) | 分段按钮组件用于创建页签型、单选或多选的胶囊型分段按钮，支持文本、图标、Symbol等多种选项类型及图文混合配置，可自定义字体、颜色、圆角等样式。页签型分段按钮适用于页签切换场景，单选胶囊型分段按钮适用于单选切换场景，多选胶囊型分段按钮适用于多选筛选场景。 |
| [TabSegmentButtonV2](arkts-arkui-arkui-advanced-segmentbuttonv2-tabsegmentbuttonv2-s.md) | 分段按钮组件用于创建页签型、单选或多选的胶囊型分段按钮，支持文本、图标、Symbol等多种选项类型及图文混合配置，可自定义字体、颜色、圆角等样式。页签型分段按钮适用于页签切换场景，单选胶囊型分段按钮适用于单选切换场景，多选胶囊型分段按钮适用于多选筛选场景。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [SegmentButtonV2ItemOptions](arkts-arkui-arkui-advanced-segmentbuttonv2-segmentbuttonv2itemoptions-i.md) | 配置分段按钮选项参数。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnSelectedIndexChange](arkts-arkui-onselectedindexchange-t.md) | 单选分段按钮选中项变更时调用的回调函数类型。 |
| [OnSelectedIndexesChange](arkts-arkui-onselectedindexeschange-t.md) | 多选分段按钮选中项变更时调用的回调函数类型。 |

## 示例

```TypeScript
### 示例1（页签型分段按钮）

此示例说明页签型分段按钮的基本用法。


```

```TypeScript
### 示例2（单选的胶囊型分段按钮）

该示例介绍单选胶囊型分段按钮的基本用法。


```

```TypeScript
### 示例3（多选的胶囊型分段按钮）

该示例介绍多选胶囊型分段按钮的基本用法。


```

```TypeScript
### 示例4（分段按钮Modifier的基本用法）

该示例介绍页签型分段按钮、单选的胶囊型分段按钮、多选的胶囊型分段按钮的Modifier基本用法。


```

```TypeScript
### 示例5（开启SegmentButtonV2的属性动画）

此示例展示了SegmentButtonV2开启enableStateAnimation后，在通过状态变量修改selectedIndex的值时，按钮切换也具有动画效果。

从API version 24开始，[TabSegmentButtonV2](arkts-arkui-arkui-advanced-segmentbuttonv2-tabsegmentbuttonv2-s.md)和[CapsuleSegmentButtonV2](arkts-arkui-arkui-advanced-segmentbuttonv2-capsulesegmentbuttonv2-s.md)新增enableStateAnimation属性。


```

```TypeScript
### 示例6（设置背景板材质）

以下示例通过backgroundSystemMaterial属性，为分段按钮设置了透明的背景板材质、开启自动反色和交互形变效果，并自定义反馈光感的颜色。

从API版本26.0.0开始，[TabSegmentButtonV2](arkts-arkui-arkui-advanced-segmentbuttonv2-tabsegmentbuttonv2-s.md)和[CapsuleSegmentButtonV2](arkts-arkui-arkui-advanced-segmentbuttonv2-capsulesegmentbuttonv2-s.md)中新增backgroundSystemMaterial属性。

该示例配图为高算力设备强档效果。


```

```TypeScript
### 示例7（监听对象类型属性内部属性的变化）

[SegmentButtonV2Item](arkts-arkui-arkui-advanced-segmentbuttonv2-segmentbuttonv2item-c.md)使用了@ObservedV2装饰器，SegmentButtonV2组件通过@Param接收各个属性参数。对于@Trace装饰的基本类型属性，@Param已能观测到属性变化并触发UI刷新。但对于对象类型属性（如itemIconSize、itemPadding等）的内部属性（如itemIconSize的width、height，itemPadding的top、bottom、start、end），这些对象类型本身未被@ObservedV2装饰，其内部属性变化无法被@Param感知。因此，修改内部属性时UI不会自动刷新。使用makeObserved接口对对象类型属性（如itemIconSize）进行包裹，可以为该对象的内部属性补充深度观察能力，使得修改内部属性（如width、height）时，框架能够监听到变化并触发UI刷新。makeObserved接口的详细说明请参考[makeObserved接口：将非观察数据变为可观察数据](../../../ui/state-management/arkts-new-makeObserved.md)。

以下示例使用UIUtils.makeObserved包裹itemIconSize，并通过Button修改itemIconSize的width和height属性，验证对象类型属性内部属性变化能够触发SegmentButtonV2的UI刷新。
```
