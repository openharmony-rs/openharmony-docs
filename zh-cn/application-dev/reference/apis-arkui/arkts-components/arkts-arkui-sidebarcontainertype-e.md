# SideBarContainerType

容器内侧边栏样式枚举。

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Embed

```TypeScript
Embed = 0
```

侧边栏嵌入到组件内，和内容区并列显示。

整体容器大小不变时，显示侧边栏会导致内容区缩小，隐藏侧边栏会扩大内容区。

组件尺寸小于[minContentWidth](SideBarContainerAttribute#minContentWidth) +
[minSideBarWidth](SideBarContainerAttribute#minSideBarWidth(value: number))，并且未设置showSideBar时，侧边栏自动隐藏。

未设置minSideBarWidth或者minContentWidth采用未设置接口的默认值进行计算。

组件在自动隐藏后，如果通过点击控制按钮唤出侧边栏，则侧边栏悬浮在内容区上显示。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Overlay

```TypeScript
Overlay = 1
```

侧边栏浮在内容区上面，不会影响内容区的大小。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## AUTO

```TypeScript
AUTO = 2
```

组件尺寸大于等于minSideBarWidth + minContentWidth时，采用Embed模式显示。

组件尺寸小于minSideBarWidth + minContentWidth时，采用Overlay模式显示。

未设置minSideBarWidth或minContentWidth时，会使用未设置接口的默认值进行计算，若计算的值小于600vp，则使用600vp做为模式切换的断点值。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DISPLACE

```TypeScript
DISPLACE = 3
```

侧边栏和内容区并列显示，内容区超出部分移出组件外。侧边栏展开时，内容区显示灰色蒙层（颜色为#33000000）并被禁用事件，点击内容区可收起侧边栏。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

