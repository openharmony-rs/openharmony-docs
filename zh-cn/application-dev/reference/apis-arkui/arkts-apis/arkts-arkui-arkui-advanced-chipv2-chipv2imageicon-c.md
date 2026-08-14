# ChipV2ImageIcon

ChipV2ImageIcon定义图标图片的基类。 继承自[ChipV2Icon](arkts-arkui-arkui-advanced-chipv2-chipv2icon-c.md#ChipV2Icon)。

**继承/实现关系：** ChipV2ImageIcon extends [ChipV2Icon](arkts-arkui-arkui-advanced-chipv2-chipv2icon-c.md#ChipV2Icon)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export abstract class ChipV2ImageIcon--><!--Device-unnamed-export abstract class ChipV2ImageIcon-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(config: ChipV2ImageIconConfig)
```

ChipV2ImageIcon的构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2ImageIcon-constructor(config: ChipV2ImageIconConfig)--><!--Device-ChipV2ImageIcon-constructor(config: ChipV2ImageIconConfig)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [ChipV2ImageIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2imageiconconfig-i.md) | 是 | 图标共通属性配置，用于设置Image类型图标的基本显示属性，包含src、size、fillColor、activatedFillColor等配置 项。 |

## activatedFillColor

```TypeScript
@Trace
  public activatedFillColor?: ColorMetrics
```

ChipV2激活时图标填充颜色。 默认值：\$r('sys.color.chip_active_icon_color')，非SVG图片不应用默认值。 值为undefined时，按默认值处理。 仅在图片格式为SVG时，activatedFillColor属性才生效。

**类型：** ColorMetrics

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2ImageIcon-@Trace  public activatedFillColor?: ColorMetrics--><!--Device-ChipV2ImageIcon-@Trace  public activatedFillColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fillColor

```TypeScript
@Trace
  public fillColor?: ColorMetrics
```

图标填充颜色。 默认值：\$r('sys.color.chip_usually_icon_color')，非SVG图片不应用默认值。 值为undefined时，按默认值处理。 仅在图片格式为SVG时，fillColor属性才生效。

**类型：** ColorMetrics

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2ImageIcon-@Trace  public fillColor?: ColorMetrics--><!--Device-ChipV2ImageIcon-@Trace  public fillColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## modifier

```TypeScript
@Trace
  public modifier?: ImageModifier
```

图标修饰器，用于设置图标的通用属性。当需要通过modifier动态修改图标属性（如opacity、objectFit等）时传入此参数。不传入或传入undefined时，不应用修饰器，图标使用默认属性设置。 默认值：undefined，不应用修饰器。

**类型：** [ImageModifier](../arkts-components/arkts-arkui-imagemodifier-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2ImageIcon-@Trace  public modifier?: ImageModifier--><!--Device-ChipV2ImageIcon-@Trace  public modifier?: ImageModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
@Trace
  public size?: SizeT<LengthMetrics>
```

图标大小，不支持百分比。传入百分比时按默认值处理。 默认值： - 当ChipV2Options.size为ChipV2Size.SMALL时，默认值为：{width: \$r('sys.float.chip_small_icon_size'), height: \$r(' sys.float.chip_small_icon_size')}。 - 当ChipV2Options.size为ChipV2Size.NORMAL时，默认值为：{width: \$r('sys.float.chip_normal_icon_size'), height: \$r(' sys.float.chip_normal_icon_size')}。 单位：vp 值为undefined时，按默认值处理。

**类型：** SizeT&lt;LengthMetrics&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2ImageIcon-@Trace  public size?: SizeT<LengthMetrics>--><!--Device-ChipV2ImageIcon-@Trace  public size?: SizeT<LengthMetrics>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## src

```TypeScript
@Trace
  public src: ResourceStr
```

图标图片或图片地址引用。

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2ImageIcon-@Trace  public src: ResourceStr--><!--Device-ChipV2ImageIcon-@Trace  public src: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

