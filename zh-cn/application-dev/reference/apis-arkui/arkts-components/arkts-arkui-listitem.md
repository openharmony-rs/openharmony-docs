# ListItem

ListItem用于展示列表中的具体列表项，支持设置划出菜单、选中状态、鼠标框选和卡片样式等能力，必须配合List组件使用，适用于需要在列表中展示内容并对单个列表项进行交互操作（如滑动删除、选中标记）的场景。 > **说明：** > > - 该组件的父组件只能是List或者ListItemGroup。 > > - 当ListItem配合[LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)使用时，ListItem子组件在 > ListItem创建时创建。配合[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、 > [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)使用时，或父组件为List/ListItemGroup时，ListItem子组 > 件在ListItem布局时创建。

## 子组件 可以包含单个子组件。

## ListItem

```TypeScript
ListItem(value?: ListItemOptions)
```

创建ListItem组件。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-ListItemInterface-(value?: ListItemOptions): ListItemAttribute--><!--Device-ListItemInterface-(value?: ListItemOptions): ListItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ListItemOptions](arkts-arkui-listitemoptions-i.md) | 否 |  |

## ListItem

```TypeScript
ListItem(value?: string)
```

创建ListItem组件。 > **说明：** > > 从API version 7开始支持，从API version 10开始废弃。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** listItem/ListItemInterface

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ListItemInterface-(value?: string): ListItemAttribute--><!--Device-ListItemInterface-(value?: string): ListItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 否 |  |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [ListItemOptions](arkts-arkui-listitemoptions-i.md) | ListItem组件参数。 |
| [SwipeActionItem](arkts-arkui-swipeactionitem-i.md) | SwipeActionItem用于配置[SwipeActionOptions](arkts-arkui-swipeactionoptions-i.md)中的start或end划出项，包括划出时显示的操作项、长距离操作区域的距离阈值，以及进入、退出长距离操作 区域、抬手触发操作和状态变化时的回调。 作为start划出项时，List为垂直布局时显示在ListItem左侧，List为水平布局时显示在ListItem上方；作为end划出项时，List为垂直布局时显示在ListItem右侧，List为水平布局时显示在ListItem下 方。 |
| [SwipeActionOptions](arkts-arkui-swipeactionoptions-i.md) | start和end对应的@builder函数中顶层必须是单个组件（如果顶层是if/else、ForEach等渲染控制语句，则必须保证其仅能生成单个组件），否则会引发未定义行为。 滑动手势只在ListItem区域上生效，如果子组件滑出ListItem区域外，在ListItem以外部分不会响应滑动手势。所以在多列模式下，建议不要将划出组件设置太宽。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [EditMode](arkts-arkui-editmode-e.md) | ListItem元素编辑模式枚举。 |
| [ListItemStyle](arkts-arkui-listitemstyle-e.md) | ListItem组件卡片样式枚举。 |
| [ListItemSwipeActionDirection](arkts-arkui-listitemswipeactiondirection-e.md) | ListItem划出菜单的展开方向。 |
| [Sticky](arkts-arkui-sticky-e.md) | ListItem吸顶效果枚举。 |
| [SwipeActionState](arkts-arkui-swipeactionstate-e.md) | 列表项滑动状态枚举。 |
| [SwipeEdgeEffect](arkts-arkui-swipeedgeeffect-e.md) | 滑动效果枚举。 |

