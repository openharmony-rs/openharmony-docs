# ContextMenuOptions

菜单项的信息。 **表1：同时设置offset与placement时菜单的偏移位置** | placement设置的值 | 菜单的偏移量说明 | | ------------------------------------------------------------ | ------------------------------------------------------------ | | Placement.TopLeft、Placement.Top、Placement.TopRight | offset的x为正数，菜单相对组件向右进行偏移，offset的y为正数，菜单相对组件向上进行偏移。 | | Placement.BottomLeft、Placement.Bottom、Placement.BottomRight | offset的x为正数，菜单相对组件向左进行偏移，offset的y为正数，菜单相对组件向下进行偏移。 | | Placement.RightTop、Placement.Right、Placement.RightBottom | offset的x为正数，菜单相对组件向右进行偏移，offset的y为正数，菜单相对组件向下进行偏移。 | **表2：同时设置arrowOffset与placement时菜单箭头的默认位置** | placement设置的值 | 菜单箭头的位置说明 | | ------------------------------------------- | ------------------------------------------------------------ | | Placement.Top、Placement.Bottom | 箭头显示在水平方向且默认居中，且距离菜单左侧边缘距离为箭头安全距离。 | | Placement.Left、Placement.Right | 箭头显示在垂直方向且默认居中，且距离菜单上侧距离为箭头安全距离。 | | Placement.TopLeft、Placement.BottomLeft | 箭头默认显示在水平方向，且距离菜单左侧边缘距离为箭头安全距离。 | | Placement.TopRight、Placement.BottomRight | 箭头默认显示在水平方向，且距离菜单右侧距离为箭头安全距离。 | | Placement.LeftTop、Placement.RightTop | 箭头默认显示在垂直方向，且距离菜单上侧距离为箭头安全距离。 | | Placement.LeftBottom、Placement.RightBottom | 箭头默认显示在垂直方向，且距离菜单下侧距离为箭头安全距离。 | **表3：enableArrow为true且placement未设置或者值为非法值的菜单默认位置** | 接口 | 菜单默认位置 | |------|-------------| | [bindMenu]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ | Placement.BottomLeft | | [bindMenu\_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_11+\_\_\_HTML\_TAG\_DESC\_USD\_6\_\_\_]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ | Placement.BottomLeft | | [bindContextMenu\_\_\_HTML\_TAG\_DESC\_USD\_7\_\_\_8+\_\_\_HTML\_TAG\_DESC\_USD\_8\_\_\_]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_ | Placement.Top | | [bindContextMenu\_\_\_HTML\_TAG\_DESC\_USD\_9\_\_\_12+\_\_\_HTML\_TAG\_DESC\_USD\_10\_\_\_]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_ | Placement.BottomLeft | | [bindContextMenuWithResponse\_\_\_HTML\_TAG\_DESC\_USD\_11\_\_\_23+\_\_\_HTML\_TAG\_DESC\_USD\_12\_\_\_]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_ | Placement.Top |

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-unnamed-declare interface ContextMenuOptions--><!--Device-unnamed-declare interface ContextMenuOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## distortionMode

```TypeScript
distortionMode?: DistortionMode
```

设置菜单的非线性形变动画模式。

**类型：** DistortionMode

**默认值：** DistortionMode.DISTORTION_AUTO

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContextMenuOptions-distortionMode?: DistortionMode--><!--Device-ContextMenuOptions-distortionMode?: DistortionMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## edgeLightMode

```TypeScript
edgeLightMode?: EdgeLightMode
```

设置菜单的流光动画模式。

**类型：** EdgeLightMode

**默认值：** EdgeLightMode.EDGELIGHT_DISABLED

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContextMenuOptions-edgeLightMode?: EdgeLightMode--><!--Device-ContextMenuOptions-edgeLightMode?: EdgeLightMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

