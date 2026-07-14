# ContextMenuOptions

菜单项的信息。

**表1：同时设置offset与placement时菜单的偏移位置**

| placement设置的值 | 菜单的偏移量说明 |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Placement.TopLeft、Placement.Top、Placement.TopRight | offset的x为正数，菜单相对组件向右进行偏移，offset的y为正数，菜单相对组件向上进行偏移。 |
| Placement.BottomLeft、Placement.Bottom、Placement.BottomRight | offset的x为正数，菜单相对组件向左进行偏移，offset的y为正数，菜单相对组件向下进行偏移。 |
| Placement.RightTop、Placement.Right、Placement.RightBottom | offset的x为正数，菜单相对组件向右进行偏移，offset的y为正数，菜单相对组件向下进行偏移。 |

**表2：同时设置arrowOffset与placement时菜单箭头的默认位置**

| placement设置的值 | 菜单箭头的位置说明 |
| ------------------------------------------- | ------------------------------------------------------------ |
| Placement.Top、Placement.Bottom | 箭头显示在水平方向且默认居中，且距离菜单左侧边缘距离为箭头安全距离。 |
| Placement.Left、Placement.Right | 箭头显示在垂直方向且默认居中，且距离菜单上侧距离为箭头安全距离。 |
| Placement.TopLeft、Placement.BottomLeft | 箭头默认显示在水平方向，且距离菜单左侧边缘距离为箭头安全距离。 |
| Placement.TopRight、Placement.BottomRight | 箭头默认显示在水平方向，且距离菜单右侧距离为箭头安全距离。 |
| Placement.LeftTop、Placement.RightTop | 箭头默认显示在垂直方向，且距离菜单上侧距离为箭头安全距离。 |
| Placement.LeftBottom、Placement.RightBottom | 箭头默认显示在垂直方向，且距离菜单下侧距离为箭头安全距离。 |

**表3：enableArrow为true且placement未设置或者值为非法值的菜单默认位置**
| 接口 | 菜单默认位置 |
|------|-------------|
| [bindMenu](arkts-arkui-commonmethod-c.md#bindmenu-1) | Placement.BottomLeft |
| [bindMenu<sup>11+</sup>](arkts-arkui-commonmethod-c.md#bindmenu-2) | Placement.BottomLeft |
| [bindContextMenu<sup>8+</sup>](arkts-arkui-commonmethod-c.md#bindcontextmenu-1) | Placement.Top |
| [bindContextMenu<sup>12+</sup>](arkts-arkui-commonmethod-c.md#bindcontextmenu-2) | Placement.BottomLeft |
| [bindContextMenuWithResponse<sup>23+</sup>](arkts-arkui-commonmethod-c.md#bindcontextmenuwithresponse-1) | Placement.Top |

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## distortionMode

```TypeScript
distortionMode?: DistortionMode
```

设置菜单的非线性形变动画模式。

**类型：** DistortionMode

**默认值：** DistortionMode.DISTORTION_AUTO

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

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

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## systemMaterial

```TypeScript
systemMaterial?: SystemUiMaterial
```

设置菜单的系统材质。不同系统材质对应不同的属性影响效果，该接口影响背景色[backgroundColor](arkts-arkui-commonmethod-c.md#backgroundcolor-1)、边框颜
色[borderColor](arkts-arkui-commonmethod-c.md#bordercolor-1)、边框宽度[borderWidth](arkts-arkui-commonmethod-c.md#borderwidth-1)、阴影
[shadow](arkts-arkui-commonmethod-c.md#shadow-1)，不建议与上述接口一起使用。材质设置为非法值、undefined时，按照不设置系统材质处
理。

默认值： undefined

**类型：** SystemUiMaterial

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

