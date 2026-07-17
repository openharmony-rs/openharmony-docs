# DividerStyle

设置分割线的样式。

> **说明：**

> 针对侧边栏子组件设置[通用属性宽高](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)时，宽高都不生效。

> 针对侧边栏内容区设置[通用属性宽高](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)时，宽高都不生效，默认占满SideBarContainer的剩余空间。

> 当[showSideBar](SideBarContainerAttribute#showSideBar)属性未设置时，依据组件大小进行自动显示：

> - 小于[minSideBarWidth](SideBarContainerAttribute#minSideBarWidth(value: number)) +  
> [minContentWidth](SideBarContainerAttribute#minContentWidth)：默认不显示侧边栏。  
>  
> - 大于等于minSideBarWidth + minContentWidth：默认显示侧边栏。

**起始版本：** 10

<!--Device-unnamed-interface DividerStyle--><!--Device-unnamed-interface DividerStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

分割线的颜色。

默认值：#000000，3%，黑色。

**类型：** ResourceColor

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DividerStyle-color?: ResourceColor--><!--Device-DividerStyle-color?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## endMargin

```TypeScript
endMargin?: Length
```

分割线与侧边栏底端的距离。

默认值：0

单位：vp

取值范围：[0, +∞)

异常值时取默认值。

**类型：** Length

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DividerStyle-endMargin?: Length--><!--Device-DividerStyle-endMargin?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## startMargin

```TypeScript
startMargin?: Length
```

分割线与侧边栏顶端的距离。

默认值：0

单位：vp

取值范围：[0, +∞)

异常值时取默认值。

**类型：** Length

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DividerStyle-startMargin?: Length--><!--Device-DividerStyle-startMargin?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth: Length
```

分割线的线宽。

默认值：1vp

单位：vp

取值范围：[0, +∞)

异常值时取默认值。

**说明**：

分割线的宽度不支持百分比设置。优先级低于[通用属性height](arkts-arkui-common-commonmethod-c.md#height-1)，超过通用属性设置大小时，按照通用属性进行裁切。部分设备硬件中存在1像素取整后分割线不显示问题，建议使用2像素。

**类型：** Length

**默认值：** 1vp

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DividerStyle-strokeWidth: Length--><!--Device-DividerStyle-strokeWidth: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

