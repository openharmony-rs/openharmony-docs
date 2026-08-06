# BadgeParam

包含用于创建Badge组件的基础参数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface BadgeParam--><!--Device-unnamed-export declare interface BadgeParam-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## position

```TypeScript
position?: BadgePosition | Position
```

设置提示点显示位置。 默认值：BadgePosition.RightTop。 undefined **说明：** 对于位置类型，不支持百分比值。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_如果设置了无效值，则使用默认值（0,0）。 表示组件的左上角，将使用。 \_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_使用BadgePosition类型时，位置将基于方向属性进行镜像。

**类型：** BadgePosition \| Position

**默认值：** BadgePosition.RightTop

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BadgeParam-position?: BadgePosition | Position--><!--Device-BadgeParam-position?: BadgePosition | Position-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style: BadgeStyle
```

Badge组件可设置样式，支持设置文本颜色、尺寸、圆点颜色和尺寸。

**类型：** BadgeStyle

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BadgeParam-style: BadgeStyle--><!--Device-BadgeParam-style: BadgeStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

