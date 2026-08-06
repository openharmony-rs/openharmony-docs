# SwipeActionItem

SwipeActionOptions的滑动操作项。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface SwipeActionItem--><!--Device-unnamed-export declare interface SwipeActionItem-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## actionAreaDistance

```TypeScript
actionAreaDistance?: Length
```

设置组件长距离滑动删除距离阈值。

**类型：** Length

**默认值：** 56vp

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwipeActionItem-actionAreaDistance?: Length--><!--Device-SwipeActionItem-actionAreaDistance?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## builder

```TypeScript
builder?: CustomBuilder
```

当列表项向左或向右滑动（当列表方向为"垂直"时），向上或向下滑动（当列表方向为"水平"时）时显示的操作项。

**类型：** CustomBuilder

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwipeActionItem-builder?: CustomBuilder--><!--Device-SwipeActionItem-builder?: CustomBuilder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## builderComponent

```TypeScript
builderComponent?: ComponentContentBase
```

当列表项向左或向右滑动（当列表方向为"垂直"时），向上或向下滑动（当列表方向为"水平"时）时显示的操作项。

**类型：** ComponentContentBase

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwipeActionItem-builderComponent?: ComponentContentBase--><!--Device-SwipeActionItem-builderComponent?: ComponentContentBase-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onAction

```TypeScript
onAction?: () => void
```

组件进入长距删除区后抬手时触发。

**类型：** () =&gt; void

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwipeActionItem-onAction?: () => void--><!--Device-SwipeActionItem-onAction?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onEnterActionArea

```TypeScript
onEnterActionArea?: () => void
```

在滑动条目进入删除区域时调用。

**类型：** () =&gt; void

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwipeActionItem-onEnterActionArea?: () => void--><!--Device-SwipeActionItem-onEnterActionArea?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onExitActionArea

```TypeScript
onExitActionArea?: () => void
```

当滑动条目退出删除区域时调用。

**类型：** () =&gt; void

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwipeActionItem-onExitActionArea?: () => void--><!--Device-SwipeActionItem-onExitActionArea?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onStateChange

```TypeScript
onStateChange?: (state: SwipeActionState) => void
```

当列表项滑动状态变化时候触发。

**类型：** (state: SwipeActionState) =&gt; void

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwipeActionItem-onStateChange?: (state: SwipeActionState) => void--><!--Device-SwipeActionItem-onStateChange?: (state: SwipeActionState) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

