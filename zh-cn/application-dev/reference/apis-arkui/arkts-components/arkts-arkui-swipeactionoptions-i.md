# SwipeActionOptions

start和end对应的@builder函数中顶层必须是单个组件（如果顶层是if/else、ForEach等渲染控制语句，则必须保证其仅能生成单个组件），否则会引发未定义行为。滑动手势只在ListItem区域上生效，如果子组件滑出ListItem区域外，在ListItem以外部分不会响应滑动手势。所以在多列模式下，建议不要将划出组件设置太宽。

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## onOffsetChange

```TypeScript
onOffsetChange?: (offset: number) => void
```

当列表项向左或向右滑动（当列表方向为"垂直"时），向上或向下滑动（当列表方向为"水平"时）位置发生变化触发。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 是 |  |

## edgeEffect

```TypeScript
edgeEffect?: SwipeEdgeEffect
```

滑动效果。

**类型：** [SwipeEdgeEffect](arkts-arkui-swipeedgeeffect-e.md)

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end?: CustomBuilder | SwipeActionItem
```

ListItem向左划动时item右边的组件（List垂直布局时）或ListItem向上划动时item下方的组件（List水平布局时）。

**类型：** [CustomBuilder](arkts-arkui-custombuilder-t.md) \| [SwipeActionItem](arkts-arkui-swipeactionitem-i.md)

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: CustomBuilder | SwipeActionItem
```

ListItem向右划动时item左边的组件（List垂直布局时）或ListItem向下划动时item上方的组件（List水平布局时）。

**类型：** [CustomBuilder](arkts-arkui-custombuilder-t.md) \| [SwipeActionItem](arkts-arkui-swipeactionitem-i.md)

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
