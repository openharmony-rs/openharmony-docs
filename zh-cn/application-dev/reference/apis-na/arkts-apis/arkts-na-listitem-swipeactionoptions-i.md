# SwipeActionOptions

swipeAction属性的滑动操作选项。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface SwipeActionOptions--><!--Device-unnamed-export declare interface SwipeActionOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## edgeEffect

```TypeScript
edgeEffect?: SwipeEdgeEffect
```

滑动效果。

**类型：** [SwipeEdgeEffect](arkts-na-listitem-swipeedgeeffect-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwipeActionOptions-edgeEffect?: SwipeEdgeEffect--><!--Device-SwipeActionOptions-edgeEffect?: SwipeEdgeEffect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end?: CustomBuilder | SwipeActionItem
```

ListItem向左划动时item右边的组件（List垂直布局时）或ListItem向上划动时item下方的组件（List水平布局时）。

**类型：** CustomBuilder \| [SwipeActionItem](arkts-na-listitem-swipeactionitem-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwipeActionOptions-end?: CustomBuilder | SwipeActionItem--><!--Device-SwipeActionOptions-end?: CustomBuilder | SwipeActionItem-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onOffsetChange

```TypeScript
onOffsetChange?: (offset: double) => void
```

当列表项向左或向右滑动（当列表方向为"垂直"时），向上或向下滑动（当列表方向为"水平"时）位置发生变化触发。

**类型：** (offset: double) =&gt; void

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwipeActionOptions-onOffsetChange?: (offset: double) => void--><!--Device-SwipeActionOptions-onOffsetChange?: (offset: double) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: CustomBuilder | SwipeActionItem
```

当列表项向左或向右滑动（当列表方向为"垂直"时），向上或向下滑动（当列表方向为"水平"时）时显示的操作项。

**类型：** CustomBuilder \| [SwipeActionItem](arkts-na-listitem-swipeactionitem-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwipeActionOptions-start?: CustomBuilder | SwipeActionItem--><!--Device-SwipeActionOptions-start?: CustomBuilder | SwipeActionItem-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

