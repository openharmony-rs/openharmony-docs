# DialogOptions

自定义弹窗的内容，继承自[BaseDialogOptions](arkts-arkui-promptaction-basedialogoptions-i.md)，用于配置自定义弹窗的显示参数和行为。

**继承/实现关系：** DialogOptions extends [BaseDialogOptions](arkts-arkui-promptaction-basedialogoptions-i.md)

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { promptAction, LevelMode, ImmersiveMode, LevelOrder } from '@kit.ArkUI';
```

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

弹窗背板模糊材质。 默认值：从API版本26.0.0开始，为BlurStyle.NONE，API版本26.0.0之前，为BlurStyle.COMPONENT_ULTRA_THICK。   
**说明：** 设置为BlurStyle.NONE即可关闭背景虚化。当设置了backgroundBlurStyle为非NONE值时，则不要设置backgroundColor，否则颜色显示将不符合预期效果。

**类型：** BlurStyle

**默认值：** BlurStyle.COMPONENT_ULTRA_THICK

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

设置弹窗背板颜色。 默认值：Color.Transparent   
**说明：** backgroundColor会与模糊属性backgroundBlurStyle叠加产生效果，如果不符合预期，可将backgroundBlurStyle设置为BlurStyle.NONE，即可取消模糊。

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderColor

```TypeScript
borderColor?: DialogOptionsBorderColor
```

设置弹窗背板的边框颜色。 默认值：Color.Black 如果使用borderColor属性，需要和borderWidth属性一起使用。

**类型：** [DialogOptionsBorderColor](arkts-arkui-promptaction-dialogoptionsbordercolor-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderStyle

```TypeScript
borderStyle?: DialogOptionsBorderStyle
```

设置弹窗背板的边框样式。 默认值：BorderStyle.Solid。 如果使用borderStyle属性，需要和borderWidth属性一起使用。

**类型：** [DialogOptionsBorderStyle](arkts-arkui-promptaction-dialogoptionsborderstyle-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderWidth

```TypeScript
borderWidth?: DialogOptionsBorderWidth
```

设置弹窗背板的边框宽度。 可分别设置4个边框宽度。 默认值：0 单位：vp 百分比参数方式：以父元素弹窗宽的百分比来设置弹窗的边框宽度。 当弹窗左边框和右边框大于弹窗宽度，弹窗上边框和下边框大于弹窗高度，显示可能不符合预期。

**类型：** [DialogOptionsBorderWidth](arkts-arkui-promptaction-dialogoptionsborderwidth-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## cornerRadius

```TypeScript
cornerRadius?: DialogOptionsCornerRadius
```

设置弹窗背板的圆角半径。 可分别设置4个圆角的半径。 默认值：{ topLeft: '32vp', topRight: '32vp', bottomLeft: '32vp', bottomRight: '32vp' } 圆角大小受组件尺寸限制，最大值为组件宽或高的一半，若值为负，则按照默认值处理。 百分比参数方式：以父元素弹窗宽和高的百分比来设置弹窗的圆角。

**类型：** [DialogOptionsCornerRadius](arkts-arkui-promptaction-dialogoptionscornerradius-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: Dimension
```

设置弹窗背板的高度。   
**说明：**
- 默认最大值：0.9 *（窗口高度 - 安全区域）。
- 百分比参数方式：弹窗参考高度为（窗口高度 - 安全区域），在此基础上调小或调大。

**类型：** [Dimension](arkts-arkui-dimension-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: DialogOptionsShadow
```

设置弹窗背板的阴影。 当设备为2in1时，默认场景下获焦阴影值为ShadowStyle.OUTER_FLOATING_MD，失焦为ShadowStyle.OUTER_FLOATING_SM。其他设备默认无阴影。

**类型：** [DialogOptionsShadow](arkts-arkui-promptaction-dialogoptionsshadow-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Dimension
```

设置弹窗背板的宽度。   
**说明：**
- 默认最大值：400vp
- 百分比参数方式：弹窗参考宽度基于所在窗口宽度调整。

**类型：** [Dimension](arkts-arkui-dimension-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
