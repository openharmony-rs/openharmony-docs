# ListItem

用来展示列表具体item，必须配合[List]{@link list}来使用。

> **说明：**
>
> *
>
> * 该组件的父组件只能是[List]{@link list}或者[ListItemGroup]{@link list_item_group}。
>
> * 当ListItem配合LazyForEach使用时，ListItem子组件在ListItem创建时创建。配合if/else、ForEach使用时，或父组件为List/ListItemGroup时，ListItem子组件在ListItem布局时创建。

## 子组件

可以包含单个子组件。

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

创建ListItem组件。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** <!--SUBSTITUTE_API-->listItem/ListItemInterface<!--/SUBSTITUTE_API-->

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ListItemInterface-(value?: string): ListItemAttribute--><!--Device-ListItemInterface-(value?: string): ListItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 否 |  |

## 汇总

- [ListItemOptions](arkts-arkui-listitem-listitemoptions-i.md)
- [SwipeActionItem](arkts-arkui-listitem-swipeactionitem-i.md)
- [SwipeActionOptions](arkts-arkui-listitem-swipeactionoptions-i.md)
- [EditMode](arkts-arkui-listitem-editmode-e.md)
- [ListItemStyle](arkts-arkui-listitem-listitemstyle-e.md)
- [ListItemSwipeActionDirection](arkts-arkui-listitem-listitemswipeactiondirection-e.md)
- [Sticky](arkts-arkui-listitem-sticky-e.md)
- [SwipeActionState](arkts-arkui-listitem-swipeactionstate-e.md)
- [SwipeEdgeEffect](arkts-arkui-listitem-swipeedgeeffect-e.md)
