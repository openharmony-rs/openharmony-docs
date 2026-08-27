# ScrollBarOptions

滚动条组件参数。

> **说明：**
> 
> - ScrollBar组件用于显示并控制所绑定可滚动组件的滚动位置。设置子组件时，该子组件作为自定义滚动条滑块，并随可滚动组件的滚动位置移动。
> 
> - 滚动条组件与可滚动组件通过Scroller进行绑定，且只有当两者方向相同时，才能联动。一个可滚动组件可以绑定多个ScrollBar组件，一个ScrollBar组件只能绑定一个可滚动组件。
> 
> - 从API version 12开始，ScrollBar组件没有子节点时，支持显示默认样式的滚动条。
> 
> - ScrollBar组件的显隐是通过BarState设置，组件内部会自动根据BarState设置调整opacity来控制显隐，因此ScrollBar组件设置
> opacity属性不生效。

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## direction

```TypeScript
direction?: ScrollBarDirection
```

滚动条的方向，控制可滚动组件对应方向的滚动。默认值：ScrollBarDirection.Vertical

**类型：** [ScrollBarDirection](arkts-arkui-scrollbardirection-e.md)

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scroller

```TypeScript
scroller: Scroller
```

可滚动组件的控制器。用于与可滚动组件进行绑定。

**类型：** [Scroller](arkts-arkui-scroller-c.md)

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## state

```TypeScript
state?: BarState
```

滚动条状态。默认值：BarState.Auto

**类型：** [BarState](../arkts-apis/arkts-arkui-barstate-e.md)

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
