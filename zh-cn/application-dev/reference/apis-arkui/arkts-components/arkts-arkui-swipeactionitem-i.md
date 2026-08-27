# SwipeActionItem

SwipeActionItem用于配置[SwipeActionOptions](arkts-arkui-swipeactionoptions-i.md)中的start或end划出项，包括划出时显示的操作项、长距离操作区域的距离阈值，以及进入、退出长距离操作 区域、抬手触发操作和状态变化时的回调。作为start划出项时，List为垂直布局时显示在ListItem左侧，List为水平布局时显示在ListItem上方；作为end划出项时，List为垂直布局时显示在ListItem右侧，List为水平布局时显示在ListItem下 方。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## onAction

```TypeScript
onAction?: () => void
```

组件进入长距删除区后抬手时触发。 滑动后松手的位置超过或等于设置的距离阈值，并且设置的距离阈值有效时才会触发。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onEnterActionArea

```TypeScript
onEnterActionArea?: () => void
```

在滑动条目进入删除区域时调用，只触发一次，当再次进入时仍触发。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onExitActionArea

```TypeScript
onExitActionArea?: () => void
```

当滑动条目退出删除区域时调用，只触发一次，当再次退出时仍触发。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onStateChange

```TypeScript
onStateChange?: (state: SwipeActionState) => void
```

当列表项滑动状态变化时候触发。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | [SwipeActionState](arkts-arkui-swipeactionstate-e.md) | 是 |  |

## actionAreaDistance

```TypeScript
actionAreaDistance?: Length
```

设置组件长距离滑动删除距离阈值。即划出组件被完全滑进视窗后，继续滑动触发删除的距离阈值。 不支持设置百分比。 删除距离阈值大于item宽度减去划出组件宽度，或删除距离阈值小于等于0就不会设置删除区域。

**类型：** [Length](../arkts-apis/arkts-arkui-length-t.md)

**默认值：** 56vp

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## builder

```TypeScript
builder?: CustomBuilder
```

当列表项向左或向右滑动（当列表方向为"垂直"时），向上或向下滑动（当列表方向为"水平"时）时显示的操作项。

**类型：** [CustomBuilder](arkts-arkui-custombuilder-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## builderComponent

```TypeScript
builderComponent?: ComponentContent
```

当列表项向左或向右滑动（当列表方向为"垂直"时），向上或向下滑动（当列表方向为"水平"时）时显示的操作项。 该参数的优先级高于参数builder。即同时设置builder和builderComponent时，以builderComponent设置的值为准。 同一个builderComponent不推荐同时给不同的start/end使用，否则会导致显示问题。

**类型：** ComponentContent

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
