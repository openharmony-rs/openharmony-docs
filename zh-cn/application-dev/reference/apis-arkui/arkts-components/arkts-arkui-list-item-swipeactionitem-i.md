# SwipeActionItem

List垂直布局，ListItem向右滑动时，item左边的长距离滑动删除选项。向左滑动时，item右边的长距离滑动删除选项。List水平布局，ListItem向上滑动时，item下边的长距离滑动删除选项。向下滑动时，item上边的长距离滑动删除选项。

**起始版本：** 10

<!--Device-unnamed-declare interface SwipeActionItem--><!--Device-unnamed-declare interface SwipeActionItem-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## actionAreaDistance

```TypeScript
actionAreaDistance?: Length
```

设置组件长距离滑动删除距离阈值。即划出组件被完全滑进视窗后，继续滑动触发删除的距离阈值。不支持设置百分比。删除距离阈值大于item宽度减去划出组件宽度，或删除距离阈值小于等于0就不会设置删除区域。

**类型：** Length

**默认值：** 56vp

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SwipeActionItem-actionAreaDistance?: Length--><!--Device-SwipeActionItem-actionAreaDistance?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## builder

```TypeScript
builder?: CustomBuilder
```

当列表项向左或向右滑动（当列表方向为"垂直"时），向上或向下滑动（当列表方向为"水平"时）时显示的操作项。

**类型：** CustomBuilder

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SwipeActionItem-builder?: CustomBuilder--><!--Device-SwipeActionItem-builder?: CustomBuilder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## builderComponent

```TypeScript
builderComponent?: ComponentContent
```

当列表项向左或向右滑动（当列表方向为"垂直"时），向上或向下滑动（当列表方向为"水平"时）时显示的操作项。该参数的优先级高于参数builder。即同时设置builder和builderComponent时，以builderComponent设置的值为准。同一个builderComponent不推荐同时给不同的start/end使用，否则会导致显示问题。

**类型：** ComponentContent

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SwipeActionItem-builderComponent?: ComponentContent--><!--Device-SwipeActionItem-builderComponent?: ComponentContent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onAction

```TypeScript
onAction?: () => void
```

组件进入长距删除区后抬手时触发。滑动后松手的位置超过或等于设置的距离阈值，并且设置的距离阈值有效时才会触发。

**类型：** () => void

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SwipeActionItem-onAction?: () => void--><!--Device-SwipeActionItem-onAction?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onEnterActionArea

```TypeScript
onEnterActionArea?: () => void
```

在滑动条目进入删除区域时调用，只触发一次，当再次进入时仍触发。

**类型：** () => void

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SwipeActionItem-onEnterActionArea?: () => void--><!--Device-SwipeActionItem-onEnterActionArea?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onExitActionArea

```TypeScript
onExitActionArea?: () => void
```

当滑动条目退出删除区域时调用，只触发一次，当再次退出时仍触发。

**类型：** () => void

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SwipeActionItem-onExitActionArea?: () => void--><!--Device-SwipeActionItem-onExitActionArea?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onStateChange

```TypeScript
onStateChange?: (state: SwipeActionState) => void
```

当列表项滑动状态变化时候触发。

**类型：** (state: SwipeActionState) => void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SwipeActionItem-onStateChange?: (state: SwipeActionState) => void--><!--Device-SwipeActionItem-onStateChange?: (state: SwipeActionState) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

