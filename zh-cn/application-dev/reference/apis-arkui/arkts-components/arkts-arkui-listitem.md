# ListItem

ListItem用于展示列表中的具体列表项，支持设置划出菜单、选中状态、鼠标框选和卡片样式等能力，必须配合List组件使用，适用于需要在列表中展示内容并对单个列表项进行交互操作（如滑动删除、选中标记）的场景。 > **说明：** > > - 该组件的父组件只能是List或者ListItemGroup。 > > - 当ListItem配合[LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)使用时，ListItem子组件在 > ListItem创建时创建。配合[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、 > [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)使用时，或父组件为List/ListItemGroup时，ListItem子组 > 件在ListItem布局时创建。

## 子组件 可以包含单个子组件。

## ListItem

```TypeScript
ListItem(value?: ListItemOptions)
```

创建ListItem组件。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

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

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

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

- [ListItemOptions](arkts-arkui-listitemoptions-i.md)
- [SwipeActionItem](arkts-arkui-swipeactionitem-i.md)
- [SwipeActionOptions](arkts-arkui-swipeactionoptions-i.md)
- [EditMode](arkts-arkui-editmode-e.md)
- [ListItemStyle](arkts-arkui-listitemstyle-e.md)
- [ListItemSwipeActionDirection](arkts-arkui-listitemswipeactiondirection-e.md)
- [Sticky](arkts-arkui-sticky-e.md)
- [SwipeActionState](arkts-arkui-swipeactionstate-e.md)
- [SwipeEdgeEffect](arkts-arkui-swipeedgeeffect-e.md)
