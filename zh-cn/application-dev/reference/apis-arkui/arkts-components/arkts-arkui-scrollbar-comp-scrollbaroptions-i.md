# ScrollBarOptions

```TypeScript
declare interface ScrollBarOptions
```

滚动条组件参数。

> **说明：** 
> 
> - ScrollBar组件用于显示并控制所绑定可滚动组件的滚动位置。设置子组件时，该子组件作为自定义滚动条滑块，并随可滚动组件的滚动位置移动。
> 
> - 滚动条组件与可滚动组件通过Scroller进行绑定，且只有当两者方向相同时，才能联动。一个可滚动组件可以绑定多个ScrollBar组件，一个ScrollBar组件只能绑定一个可滚动组件。
> 
> - 从API version 12开始，ScrollBar组件没有子节点时，支持显示默认样式的滚动条。
> 
> - ScrollBar组件的显隐是通过BarState设置，组件内部会自动根据BarState设置调整opacity来控制显隐，因此ScrollBar组件设置[opacity](arkts-arkui-common-comp-commonmethod-c.md#opacity-1)属性不生效。

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: ScrollBarDirection
```

滚动条的方向，控制可滚动组件对应方向的滚动。可滚动内容为纵向布局时设置为ScrollBarDirection.Vertical；可滚动内容为横向布局时设置为ScrollBarDirection.Horizontal。<br>默认值：ScrollBarDirection.Vertical

**类型：** [ScrollBarDirection](arkts-arkui-scrollbar-comp-scrollbardirection-e.md)

**起始版本：** 8

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scroller

```TypeScript
scroller: Scroller
```

可滚动组件的控制器。用于与可滚动组件进行绑定，且仅当ScrollBar与可滚动组件方向相同时才能联动。一个可滚动组件可以绑定多个ScrollBar组件，一个ScrollBar组件只能绑定一个可滚动组件。

**类型：** [Scroller](arkts-arkui-scroll-comp-scroller-c.md)

**起始版本：** 8

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## state

```TypeScript
state?: BarState
```

滚动条状态。BarState.Auto表示按需显示，BarState.On表示常驻显示，BarState.Off表示不显示。<br>默认值：BarState.Auto

**类型：** [BarState](../arkts-apis/arkts-arkui-barstate-e.md)

**起始版本：** 8

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
