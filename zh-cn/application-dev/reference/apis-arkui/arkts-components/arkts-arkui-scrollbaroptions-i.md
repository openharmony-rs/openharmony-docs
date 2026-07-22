# ScrollBarOptions

滚动条组件参数。
> **说明：**  
>  
> - ScrollBar组件负责定义可滚动区域的行为样式，ScrollBar的子节点负责定义滚动条的行为样式。  
>  
> - 滚动条组件与可滚动组件通过Scroller进行绑定，且只有当两者方向相同时，才能联动，ScrollBar与可滚动组件仅支持一对一绑定。  
>  
> - 从API version 12开始，ScrollBar组件没有子节点时，支持显示默认样式的滚动条。  
>  
> - ScrollBar组件的显隐是通过BarState设置，组件内部会自动根据BarState设置调整opacity来控制显隐，因此ScrollBar组件设置  
> [opacity](arkts-arkui-commonmethod-c.md#opacity)属性不生效。

**起始版本：** 8

<!--Device-unnamed-declare interface ScrollBarOptions--><!--Device-unnamed-declare interface ScrollBarOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: ScrollBarDirection
```

滚动条的方向，控制可滚动组件对应方向的滚动。<br/>默认值：ScrollBarDirection.Vertical

**类型：** ScrollBarDirection

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollBarOptions-direction?: ScrollBarDirection--><!--Device-ScrollBarOptions-direction?: ScrollBarDirection-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scroller

```TypeScript
scroller: Scroller
```

可滚动组件的控制器。用于与可滚动组件进行绑定。

**类型：** Scroller

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollBarOptions-scroller: Scroller--><!--Device-ScrollBarOptions-scroller: Scroller-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## state

```TypeScript
state?: BarState
```

滚动条状态。<br/>默认值：BarState.Auto

**类型：** BarState

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollBarOptions-state?: BarState--><!--Device-ScrollBarOptions-state?: BarState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

