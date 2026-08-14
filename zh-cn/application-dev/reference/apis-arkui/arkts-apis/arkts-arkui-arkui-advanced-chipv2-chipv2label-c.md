# ChipV2Label

ChipV2Label定义文本属性类。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare class ChipV2Label--><!--Device-unnamed-export declare class ChipV2Label-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(config: ChipV2LabelConfig)
```

ChipV2Label的构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Label-constructor(config: ChipV2LabelConfig)--><!--Device-ChipV2Label-constructor(config: ChipV2LabelConfig)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [ChipV2LabelConfig](arkts-arkui-arkui-advanced-chipv2-chipv2labelconfig-i.md) | 是 | 文本属性配置，用于设置ChipV2的文本显示属性，包含text、fontSize、fontColor、activatedFontColor、 fontFamily等配置项。 |

## activatedFontColor

```TypeScript
@Trace
  public activatedFontColor?: ColorMetrics
```

ChipV2激活时的文字颜色。 默认值：\$r('sys.color.chip_activated_fontcolor') 值为undefined时，按默认值处理。 值为非法值时，按默认值处理。

**类型：** ColorMetrics

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Label-@Trace  public activatedFontColor?: ColorMetrics--><!--Device-ChipV2Label-@Trace  public activatedFontColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
@Trace
  public fontColor?: ColorMetrics
```

文字颜色。 默认值：\$r('sys.color.chip_font_color') 值为undefined时，按默认值处理。 值为非法值时，按默认值处理。

**类型：** ColorMetrics

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Label-@Trace  public fontColor?: ColorMetrics--><!--Device-ChipV2Label-@Trace  public fontColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontFamily

```TypeScript
@Trace
  public fontFamily?: string
```

文字字体。 默认值："HarmonyOS Sans" 值为undefined时，按默认值处理。

**类型：** string

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Label-@Trace  public fontFamily?: string--><!--Device-ChipV2Label-@Trace  public fontFamily?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
@Trace
  public fontSize?: LengthMetrics
```

文字字号，不支持百分比。传入百分比时按默认值处理。 默认值： size为ChipV2Size.SMALL时，默认值：\$r('sys.float.chip_small_font_size')。 其他情况下，默认值：\$r('sys.float.chip_normal_font_size') 单位：fp 值为undefined时，按默认值处理。

**类型：** LengthMetrics

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Label-@Trace  public fontSize?: LengthMetrics--><!--Device-ChipV2Label-@Trace  public fontSize?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## labelMargin

```TypeScript
@Trace
  public labelMargin?: ChipV2LabelMarginConfig
```

文本与左右侧图标之间间距。 默认值： size为ChipV2Size.SMALL时，默认值：{ left: 4, right: 4 }。 size为ChipV2Size.NORMAL时，默认值：{ left: 6, right: 6 }。 值为undefined时，按默认值处理。

**类型：** [ChipV2LabelMarginConfig](arkts-arkui-arkui-advanced-chipv2-chipv2labelmarginconfig-i.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Label-@Trace  public labelMargin?: ChipV2LabelMarginConfig--><!--Device-ChipV2Label-@Trace  public labelMargin?: ChipV2LabelMarginConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## localizedLabelMargin

```TypeScript
@Trace
  public localizedLabelMargin?: ChipV2LocalizedLabelMarginConfig
```

本地化文本与左右侧图标之间间距。 默认值： size为ChipV2Size.SMALL时，默认值： `{ start: LengthMetrics.resource(\$r('sys.float.chip_small_text_margin')), end: LengthMetrics.resource(\$r('sys.float.chip_small_text_margin')) }`。 size为ChipV2Size.NORMAL时，默认值： `{ start: LengthMetrics.resource(\$r('sys.float.chip_normal_text_margin')), end: LengthMetrics.resource(\$r('sys.float.chip_normal_text_margin')) }`。 值为undefined时，按默认值处理。

**类型：** [ChipV2LocalizedLabelMarginConfig](arkts-arkui-arkui-advanced-chipv2-chipv2localizedlabelmarginconfig-i.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Label-@Trace  public localizedLabelMargin?: ChipV2LocalizedLabelMarginConfig--><!--Device-ChipV2Label-@Trace  public localizedLabelMargin?: ChipV2LocalizedLabelMarginConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## modifier

```TypeScript
@Trace
  public modifier?: TextModifier
```

文本修饰器，用于设置文本的通用属性。当需要通过modifier动态修改文本属性（如fontWeight、fontStyle等）时传入此参数。不传入或传入undefined时，不应用修饰器，文本使用默认属性设置。 默认值：undefined，不应用修饰器。

**类型：** TextModifier

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Label-@Trace  public modifier?: TextModifier--><!--Device-ChipV2Label-@Trace  public modifier?: TextModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
@Trace
  public text: string
```

文本文字内容。

**类型：** string

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Label-@Trace  public text: string--><!--Device-ChipV2Label-@Trace  public text: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

