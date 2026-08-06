# DialogOptions

自定义弹窗的内容，继承自\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_，用于配置自定义弹窗的显示参数和行为。

**继承/实现关系：** DialogOptions extends [BaseDialogOptions](arkts-arkui-promptaction-basedialogoptions-i.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

<!--Device-promptAction-interface DialogOptions extends BaseDialogOptions--><!--Device-promptAction-interface DialogOptions extends BaseDialogOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

弹窗背板模糊材质。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_默认值：从API版本26.0.0开始，为BlurStyle.NONE，API版本26.0.0之前，为BlurStyle.COMPONENT\_ULTRA\_THICK。 \_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_**说明：** \_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_设置为BlurStyle.NONE即可关闭背景虚化。当设置了backgroundBlurStyle为非NONE值时，则不要设置backgroundColor，否则颜色显示将不符合预期效果。

**类型：** BlurStyle

**默认值：** BlurStyle.COMPONENT_ULTRA_THICK

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-DialogOptions-backgroundBlurStyle?: BlurStyle--><!--Device-DialogOptions-backgroundBlurStyle?: BlurStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

设置弹窗背板颜色。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_默认值：Color.Transparent \_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_**说明：** \_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_backgroundColor会与模糊属性backgroundBlurStyle叠加产生效果，如果不符合预期，可将backgroundBlurStyle设置为BlurStyle.NONE，即可取消模糊。

**类型：** ResourceColor

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-DialogOptions-backgroundColor?: ResourceColor--><!--Device-DialogOptions-backgroundColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderColor

```TypeScript
borderColor?: DialogOptionsBorderColor
```

设置弹窗背板的边框颜色。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_默认值：Color.Black \_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_ 如果使用borderColor属性，需要和borderWidth属性一起使用。

**类型：** DialogOptionsBorderColor

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-DialogOptions-borderColor?: DialogOptionsBorderColor--><!--Device-DialogOptions-borderColor?: DialogOptionsBorderColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderStyle

```TypeScript
borderStyle?: DialogOptionsBorderStyle
```

设置弹窗背板的边框样式。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_默认值：BorderStyle.Solid。 \_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_ 如果使用borderStyle属性，需要和borderWidth属性一起使用。

**类型：** DialogOptionsBorderStyle

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-DialogOptions-borderStyle?: DialogOptionsBorderStyle--><!--Device-DialogOptions-borderStyle?: DialogOptionsBorderStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderWidth

```TypeScript
borderWidth?: DialogOptionsBorderWidth
```

设置弹窗背板的边框宽度。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_可分别设置4个边框宽度。 \_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_默认值：0 \_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_单位：vp \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_ 百分比参数方式：以父元素弹窗宽的百分比来设置弹窗的边框宽度。 \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_当弹窗左边框和右边框大于弹窗宽度，弹窗上边框和下边框大于弹窗高度，显示可能不符合预期。

**类型：** DialogOptionsBorderWidth

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-DialogOptions-borderWidth?: DialogOptionsBorderWidth--><!--Device-DialogOptions-borderWidth?: DialogOptionsBorderWidth-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## cornerRadius

```TypeScript
cornerRadius?: DialogOptionsCornerRadius
```

设置弹窗背板的圆角半径。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_可分别设置4个圆角的半径。 \_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_默认值：{ topLeft: '32vp', topRight: '32vp', bottomLeft: '32vp', bottomRight: '32vp' } \_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_ 圆角大小受组件尺寸限制，最大值为组件宽或高的一半，若值为负，则按照默认值处理。 \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_ 百分比参数方式：以父元素弹窗宽和高的百分比来设置弹窗的圆角。

**类型：** DialogOptionsCornerRadius

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-DialogOptions-cornerRadius?: DialogOptionsCornerRadius--><!--Device-DialogOptions-cornerRadius?: DialogOptionsCornerRadius-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: Dimension
```

设置弹窗背板的高度。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_**说明：** \_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_- 默认最大值：0.9 *（窗口高度 - 安全区域）。 \_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_- 百分比参数方式：弹窗参考高度为（窗口高度 - 安全区域），在此基础上调小或调大。

**类型：** Dimension

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-DialogOptions-height?: Dimension--><!--Device-DialogOptions-height?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: DialogOptionsShadow
```

设置弹窗背板的阴影。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_当设备为2in1时，默认场景下获焦阴影值为ShadowStyle.OUTER\_FLOATING\_MD，失焦为ShadowStyle.OUTER\_FLOATING\_SM。其他设备默认无阴影。

**类型：** DialogOptionsShadow

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-DialogOptions-shadow?: DialogOptionsShadow--><!--Device-DialogOptions-shadow?: DialogOptionsShadow-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Dimension
```

设置弹窗背板的宽度。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_**说明：** \_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_- 默认最大值：400vp \_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_- 百分比参数方式：弹窗参考宽度基于所在窗口宽度调整。

**类型：** Dimension

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-DialogOptions-width?: Dimension--><!--Device-DialogOptions-width?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

