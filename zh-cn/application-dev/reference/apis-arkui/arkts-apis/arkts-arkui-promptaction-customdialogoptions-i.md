# CustomDialogOptions

自定义弹窗的内容，继承自[BaseDialogOptions](arkts-arkui-promptaction-basedialogoptions-i.md)。

**继承/实现关系：** CustomDialogOptions extends [BaseDialogOptions](arkts-arkui-promptaction-basedialogoptions-i.md)

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { promptAction, LevelMode, ImmersiveMode, LevelOrder } from '@kit.ArkUI';
```

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

弹窗背板模糊材质。<br>默认值：从API版本26.0.0开始，为BlurStyle.NONE，API版本26.0.0之前，为BlurStyle.COMPONENT_ULTRA_THICK。<br>**说明：** <br>设置为BlurStyle.NONE即可关闭背景虚化。当设置了backgroundBlurStyle为非NONE值时，则不要设置backgroundColor，否则颜色显示将不符合预期效果。

**类型：** [BlurStyle](../arkts-components/arkts-arkui-blurstyle-e.md)

**默认值：** BlurStyle.COMPONENT_ULTRA_THICK

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

设置弹窗背板颜色。<br>默认值：Color.Transparent <br>**说明：** <br>当设置了backgroundColor为非透明色时，backgroundBlurStyle需要设置为BlurStyle.NONE，否则颜色显示将不符合预期效果。

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderColor

```TypeScript
borderColor?: ResourceColor | EdgeColors
```

设置弹窗背板的边框颜色。<br>默认值：Color.Black <br> 如果使用borderColor属性，需要和borderWidth属性一起使用。

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md) &#124; EdgeColors

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderStyle

```TypeScript
borderStyle?: BorderStyle | EdgeStyles
```

设置弹窗背板的边框样式。<br>默认值：BorderStyle.Solid <br> 如果使用borderStyle属性，需要和borderWidth属性一起使用。

**类型：** [BorderStyle](arkts-arkui-borderstyle-e.md) &#124; EdgeStyles

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderWidth

```TypeScript
borderWidth?: Dimension | EdgeWidths
```

设置弹窗背板的边框宽度。<br>可分别设置4个边框宽度。<br>默认值：0 <br>单位：vp <br> 百分比参数方式：以父元素弹窗宽的百分比来设置弹窗的边框宽度。<br>当弹窗左边框和右边框大于弹窗宽度，弹窗上边框和下边框大于弹窗高度，显示可能不符合预期。

**类型：** [Dimension](arkts-arkui-dimension-t.md) &#124; EdgeWidths

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## builder

```TypeScript
builder: CustomBuilder
```

设置自定义弹窗的内容。<br>**说明：** <br>builder需要赋值为箭头函数，格式如下：() =&gt; { this.XXX() }，其中XXX是内部builder名。<br>全局builder需要在组件内部创建，并在内部builder中调用。<br>builder根节点宽高百分比相对弹窗容器大小。<br>builder非根节点宽高百分比相对父节点大小。

**类型：** [CustomBuilder](../arkts-components/arkts-arkui-custombuilder-t.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## cornerRadius

```TypeScript
cornerRadius?: Dimension | BorderRadiuses
```

设置背板的圆角半径。<br>可分别设置4个圆角的半径。<br>默认值：{ topLeft: '32vp', topRight: '32vp', bottomLeft: '32vp', bottomRight: '32vp' } <br> 圆角大小受组件尺寸限制，最大值为组件宽或高的一半，若值为负，则按照默认值处理。<br> 百分比参数方式：以父元素弹窗宽和高的百分比来设置弹窗的圆角。

**类型：** [Dimension](arkts-arkui-dimension-t.md) &#124; [BorderRadiuses](arkts-arkui-borderradiuses-t.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: Dimension
```

设置弹窗背板的高度。<br>**说明：** <br>- 弹窗高度默认最大值：0.9 *（窗口高度 - 安全区域）。<br>- 百分比参数方式：弹窗参考高度为（窗口高度 - 安全区域），在此基础上调小或调大。

**类型：** [Dimension](arkts-arkui-dimension-t.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: ShadowOptions | ShadowStyle
```

设置弹窗背板的阴影。<br>当设备为2in1时，默认场景下获焦阴影值为ShadowStyle.OUTER_FLOATING_MD，失焦为ShadowStyle.OUTER_FLOATING_SM。其他设备默认无阴影。

**类型：** [ShadowOptions](../arkts-components/arkts-arkui-shadowoptions-i.md) &#124; [ShadowStyle](../arkts-components/arkts-arkui-shadowstyle-e.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Dimension
```

设置弹窗背板的宽度。<br>**说明：** <br>- 弹窗宽度默认最大值：400vp <br>- 百分比参数方式：弹窗参考宽度基于所在窗口的宽度的基础上调整。

**类型：** [Dimension](arkts-arkui-dimension-t.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
