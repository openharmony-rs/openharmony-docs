# Slider属性/事件

支持除触摸热区以外的通用属性。除支持通用事件外，还支持以下事件：

**继承/实现关系：** SliderAttribute extends CommonMethod<SliderAttribute>

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## blockBorderColor

```TypeScript
blockBorderColor(value: ResourceColor)
```

设置滑块描边颜色。当滑块形状设置为SliderBlockType.DEFAULT时，blockBorderColor可设置默认圆形滑块描边颜色。当滑块形状设置为SliderBlockType.IMAGE时，滑块无描边，设置blockBorderColor不生效。当滑块形状设置为SliderBlockType.SHAPE时，blockBorderColor可设置自定义形状中线的颜色。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 滑块描边颜色。默认值：'#00000000' |

## blockBorderWidth

```TypeScript
blockBorderWidth(value: Length)
```

设置滑块描边粗细。当滑块形状设置为SliderBlockType.DEFAULT时，blockBorderWidth可设置默认圆形滑块描边粗细。当滑块形状设置为SliderBlockType.IMAGE时，滑块无描边，设置blockBorderWidth不生效。当滑块形状设置为SliderBlockType.SHAPE时，blockBorderWidth可设置自定义形状中线的粗细。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 滑块描边粗细。   **说明：** 设置string类型时，不支持百分比。 |

## blockColor

```TypeScript
blockColor(value: ResourceColor)
```

设置滑块的颜色。当滑块形状设置为SliderBlockType.DEFAULT时，blockColor可设置默认圆形滑块颜色。当滑块形状设置为SliderBlockType.IMAGE时，滑块无填充，设置blockColor不生效。当滑块形状设置为SliderBlockType.SHAPE时，blockColor可设置自定义形状的填充颜色。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 滑块的颜色。 默认值：`\\$r('sys.color.ohos_id_color_foreground_contrary')` |

## blockColor

```TypeScript
blockColor(value: ResourceColor | LinearGradient)
```

设置Slider滑块的颜色，支持渐变色。与blockColor相比，新增LinearGradient类型支持。当滑块形状设置为SliderBlockType.DEFAULT时，blockColor可设置默认圆形滑块颜色。当滑块形状设置为SliderBlockType.IMAGE时，滑块无填充，设置blockColor不生效。当滑块形状设置为SliderBlockType.SHAPE时，blockColor可设置自定义形状的填充颜色。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本21开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) \| LinearGradient | 是 | 滑块的颜色。 默认值： `\\$r('sys.color.ohos_id_color_foreground_contrary')` |

## blockSize

```TypeScript
blockSize(value: SizeOptions)
```

设置滑块大小。当滑块形状设置为SliderBlockType.DEFAULT时，取宽高的最小值作为圆形半径。当滑块形状设置为SliderBlockType.IMAGE时，用于设置图片的尺寸大小，图片采用ObjectFit.Cover策略进行缩放。当滑块形状设置为SliderBlockType.SHAPE时，用于设置自定义形状的大小，自定义形状也会采用ObjectFit.Cover策略进行缩放。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SizeOptions](../arkts-apis/arkts-arkui-sizeoptions-i.md) | 是 | 滑块大小。默认值：当参数style的值设置为[SliderStyle](arkts-arkui-sliderstyle-e.md).OutSet时为{width: 18, height: 18}，当参数style的值设置为[SliderStyle](arkts-arkui-sliderstyle-e.md).InSet时为{width: 12, height: 12}，当参数style的值设置为 [SliderStyle](arkts-arkui-sliderstyle-e.md).NONE时，此字段不生效。当设置的blockSize的宽高值不相等时，取较小值的尺寸，当设置的宽高值中有一个或两个都小于等于0的时候，取默认 值。 |

## blockStyle

```TypeScript
blockStyle(value: SliderBlockStyle)
```

设置滑块形状参数。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SliderBlockStyle](arkts-arkui-sliderblockstyle-i.md) | 是 | 滑块形状参数。默认值：SliderBlockType.DEFAULT，滑块形状为圆形。 |

## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<SliderConfiguration>)
```

定制Slider内容区的方法。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [ContentModifier](arkts-arkui-contentmodifier-i.md)&lt;[SliderConfiguration](arkts-arkui-sliderconfiguration-i.md)&gt; | 是 | 在Slider组件上，定制内容区的方法。ContentModifier为内容修改器，需自定义class实现该接口。 |

## digitalCrownSensitivity

```TypeScript
digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>)
```

设置旋转表冠灵敏度。

> **说明：**
> 
> 该接口不支持在attributeModifier中调用。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sensitivity | [Optional](arkts-arkui-optional-t.md)&lt;[CrownSensitivity](../arkts-apis/arkts-arkui-crownsensitivity-e.md)&gt; | 是 | 旋转表冠灵敏度。默认值：CrownSensitivity.MEDIUM |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(enabled: boolean)
```

设置是否开启触控反馈。开启触控反馈时，需要在工程的[module.json5](../../../quick-start/module-configuration-file.md)中配置requestPermissions字段开启振动权限，配置如 下：

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 是否开启触控反馈。true：开启触控反馈；false：不开启触控反馈。默认值：true |

## maxLabel

```TypeScript
maxLabel(value: string)
```

设置最大值标签的文本内容。

> **说明：**
> 
> 从API version 7开始支持，从API version 9开始废弃，建议使用max替代。max是[SliderOptions](arkts-arkui-slideroptions-i.md)中的属性。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** max

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | 最大值标签文本。 |

## minLabel

```TypeScript
minLabel(value: string)
```

设置最小值标签的文本内容。

> **说明：**
> 
> 从API version 7开始支持，从API version 9开始废弃，建议使用min替代。min是[SliderOptions](arkts-arkui-slideroptions-i.md)中的属性。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** min

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | 最小值标签文本。 |

## minResponsiveDistance

```TypeScript
minResponsiveDistance(value: number)
```

设置滑块开始滑动的最小响应距离。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 设置滑块开始滑动的最小响应距离。默认值：0   **说明：** 单位与 [SliderOptions](arkts-arkui-slideroptions-i.md)中的属性min以及属性max一致。当value小于0、大于max-min或非法值时，取默认值。 |

## onChange

```TypeScript
onChange(callback: (value: number, mode: SliderChangeMode) => void)
```

Slider拖动或点击时触发事件回调。Begin和End状态在点击时触发，Moving和Click状态在value值变化时触发。连贯拖动动作不触发Click状态。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (value: number, mode: SliderChangeMode) =&gt; void | 是 |  |

## prefix

```TypeScript
prefix(content: ComponentContent, options?: SliderPrefixOptions)
```

设置滑动条的前缀。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ComponentContent | 是 | 滑块前缀的可视化内容，显示在滑块起始位置。 |
| options | [SliderPrefixOptions](arkts-arkui-sliderprefixoptions-i.md) | 否 | 滑块前缀的配置选项，用于设置与无障碍功能相关的属性。 默认值：null |

## selectedBorderRadius

```TypeScript
selectedBorderRadius(value: Dimension)
```

设置已滑动部分（高亮）圆角半径。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | 是 | 已选择部分的圆角半径。默认值：当style值为SliderStyle.InSet或SliderStyle.OutSet时，跟随底板圆角；当style值为 SliderStyle.NONE时，为0。   **说明：** 不支持Percentage类型。设定值小于0时取默认值。 |

## selectedColor

```TypeScript
selectedColor(value: ResourceColor)
```

设置滑轨的已滑动部分颜色。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 滑轨的已滑动部分颜色。 默认值：`\\$r('sys.color.ohos_id_color_emphasize')` |

## selectedColor

```TypeScript
selectedColor(selectedColor: ResourceColor | LinearGradient)
```

设置滑轨的已滑动部分颜色。与[selectedColor](#selectedcolor)相比，新增了LinearGradient类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectedColor | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) \| LinearGradient | 是 | 滑轨的已滑动部分颜色。默认值： `\\$r('sys.color.ohos_id_color_emphasize')`    **说明：** 设置渐变色时，若颜色断点颜色值为非法值或者渐变色断点为空时，渐变色不起效果。 |

## showSteps

```TypeScript
showSteps(value: boolean)
```

设置是否显示步长刻度值。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否显示步长刻度值。true：显示刻度值；false：不显示刻度值。默认值：false |

## showSteps

```TypeScript
showSteps(value: boolean, options?: SliderShowStepOptions)
```

设置当前是否显示步长刻度值。支持设置每个刻度点的无障碍文本信息，不设置时默认使用当前刻度点的值作为无障碍文本信息。当显示步长时，设置的刻度点无障碍文本信息生效。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否显示步长刻度值。true：显示刻度值；false：不显示刻度值。默认值：false |
| options | [SliderShowStepOptions](arkts-arkui-slidershowstepoptions-i.md) | 否 | 刻度点无障碍文本的配置选项，用于设置与无障碍功能相关的属性。默认值：null |

## showTips

```TypeScript
showTips(value: boolean, content?: ResourceStr)
```

设置滑动时是否显示气泡提示。当direction的值为Axis.Horizontal时，气泡提示显示在滑块上方；若上方空间不足以显示完整气泡提示，则在下方显示。当值为Axis.Vertical时，气泡提示显示在滑块左边；若左边空间不足以显示完整气泡提示，则在右边显示。当未设置周边边距或边距小于气泡提示所需空间时，气泡提示会被截断。气泡提示的绘制区域为Slider自身节点的overlay。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 滑动时是否显示气泡提示。true：显示气泡；false：不显示气泡。默认值：false |
| content | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 否 | 气泡提示的文本内容。传入时显示自定义文本（当需要展示特定格式或额外信息时使用），不传入时默认显示当前百分比数值。<br>**起始版本：** 10 |

## slideRange

```TypeScript
slideRange(value: SlideRange)
```

设置有效滑动区间。设置后滑块滑动范围被限制在[from, to]区间内，区间外的点击和手势不会触发滑动；value初始值若超出区间会自动调整到区间边界。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SlideRange](arkts-arkui-sliderange-i.md) | 是 | 有效滑动区间 |

## sliderInteractionMode

```TypeScript
sliderInteractionMode(value: SliderInteraction)
```

设置用户与滑动条组件交互方式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SliderInteraction](arkts-arkui-sliderinteraction-e.md) | 是 | 用户与滑动条组件交互方式。 默认值：SliderInteraction.SLIDE_AND_CLICK。 |

## stepColor

```TypeScript
stepColor(value: ResourceColor)
```

设置刻度颜色。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 刻度颜色。默认值：`\\$r('sys.color.ohos_id_color_foreground')`混合`\\$r('sys.color.ohos_id_alpha_normal_bg')`透明度的颜色 |

## stepSize

```TypeScript
stepSize(value: Length)
```

设置刻度大小（直径）。当值为0时，刻度点不显示，当值小于0时，取默认值。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 刻度大小（直径）。 默认值：'4vp'取值范围： [0, [trackThickness](#trackthickness)) |

## suffix

```TypeScript
suffix(content: ComponentContent, options?: SliderSuffixOptions)
```

设置滑动条的后缀。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ComponentContent | 是 | 滑块后缀的可视化内容，显示在滑块结束位置。 |
| options | [SliderSuffixOptions](arkts-arkui-slidersuffixoptions-i.md) | 否 | 滑块后缀的配置选项，用于设置与无障碍功能相关的属性。 默认值：null |

## trackBorderRadius

```TypeScript
trackBorderRadius(value: Length)
```

设置底板圆角半径。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 底板圆角半径。默认值：style值为SliderStyle.OutSet时默认值为'2vp'。style值为SliderStyle.InSet时默认 值为'10vp'。   **说明：** 设定值小于0时取默认值。 |

## trackColor

```TypeScript
trackColor(value: ResourceColor | LinearGradient)
```

设置滑轨的背景颜色。从API version 12开始，支持使用LinearGradient类型设置滑轨的渐变色。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) \| LinearGradient | 是 | 滑轨的背景颜色。默认值：`\\$r('sys.color.ohos_id_color_component_normal')`    **说明：** 1. 设置渐变色时，如果颜色断点颜色值为非法值或渐变色断点为空，渐变色将不起效果。 2. 该接口中的LinearGradient类型不支持在原子化服务中使用。<br>**起始版本：** 12 |

## trackColorMetrics

```TypeScript
trackColorMetrics(color: ColorMetricsLinearGradient)
```

设置滑轨轨道的线性渐变背景颜色。与trackColorMetrics相比，使用ColorMetricsLinearGradient类型支持指定色域的渐变。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [ColorMetricsLinearGradient](arkts-arkui-colormetricslineargradient-c.md) | 是 | 滑轨轨道的线性渐变背景颜色。设置渐变色时，如果color的值为undefined，渐变色设置无效，轨道背景颜色默认取值为： `\\$r('sys.color.ohos_id_color_component_normal')`。 |

## trackThickness

```TypeScript
trackThickness(value: Length)
```

设置滑轨的粗细。设置小于等于0的值时，取默认值。为保证滑块和滑轨的[SliderStyle](arkts-arkui-sliderstyle-e.md)样式，[blockSize](#blocksize)跟随trackThickness同比例增减。当style为[SliderStyle](arkts-arkui-sliderstyle-e.md).OutSet时，trackThickness ：[blockSize](#blocksize) = 1 ： 4，当style为[SliderStyle](arkts-arkui-sliderstyle-e.md).InSet时，trackThickness ：[blockSize](#blocksize) = 5 ： 3。trackThickness或[blockSize](#blocksize)的大小超过Slider组件的宽度或高度时，取默认值。当[SliderStyle](arkts-arkui-sliderstyle-e.md)设置为OutSet时，尽管trackThickness的大小没超过Slider组件的宽度或高度，但是 [blockSize](#blocksize)超过了，取默认值。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 滑轨的粗细。默认值：当参数style的值设置[SliderStyle](arkts-arkui-sliderstyle-e.md).OutSet 时为 4.0vp， [SliderStyle](arkts-arkui-sliderstyle-e.md).InSet时为20.0vp。 |
