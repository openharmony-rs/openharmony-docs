# BarMode

TabBar布局模式枚举。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Scrollable

```TypeScript
Scrollable = 0
```

每一个TabBar均使用实际布局宽度，超过总长度（横向Tabs的[barWidth](arkts-arkui-tabs-attribute.md#barwidth)，纵向Tabs的 [barHeight](arkts-arkui-tabs-attribute.md#barheight)）后可滑动。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Fixed

```TypeScript
Fixed = 1
```

所有TabBar平均分配barWidth宽度（纵向时平均分配barHeight高度）。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
