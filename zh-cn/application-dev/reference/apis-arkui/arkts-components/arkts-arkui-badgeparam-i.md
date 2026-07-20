# BadgeParam

包含用于创建Badge组件的基础参数。

**起始版本：** 7

<!--Device-unnamed-declare interface BadgeParam--><!--Device-unnamed-declare interface BadgeParam-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## position

```TypeScript
position?: BadgePosition | Position
```

设置提示点显示位置。

默认值：BadgePosition.RightTop

**说明：**

Position作为入参，不支持设置百分比；设置为非法值时，默认(0,0)处理。(0,0)为组件左上角位置。

BadgePosition作为入参时，会跟随[Direction](../arkts-apis/arkts-arkui-direction-e.md)属性控制镜像显示。

**类型：** BadgePosition \| Position

**默认值：** BadgePosition.RightTop

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-BadgeParam-position?: BadgePosition | Position--><!--Device-BadgeParam-position?: BadgePosition | Position-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style: BadgeStyle
```

Badge组件可设置样式，支持设置文本颜色、尺寸、圆点颜色和尺寸。

**类型：** BadgeStyle

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-BadgeParam-style: BadgeStyle--><!--Device-BadgeParam-style: BadgeStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

