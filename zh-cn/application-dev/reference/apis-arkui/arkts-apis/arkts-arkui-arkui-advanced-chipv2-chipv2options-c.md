# ChipV2Options

ChipV2Options定义ChipV2的样式及具体样式参数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export class ChipV2Options--><!--Device-unnamed-export class ChipV2Options-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(config: IChipV2OptionsConfig)
```

ChipV2Options的构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-constructor(config: IChipV2OptionsConfig)--><!--Device-ChipV2Options-constructor(config: IChipV2OptionsConfig)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [IChipV2OptionsConfig](../../apis-na/arkts-apis/arkts-na-arkui-advanced-chipv2-ichipv2optionsconfig-i.md) | 是 | ChipV2样式配置，用于自定义ChipV2组件的外观和行为，包含label、prefixIcon、suffixIcon、allowClose、 activated、backgroundColor等配置项。 |

## accessibilityDescription

```TypeScript
@Trace
  public accessibilityDescription?: ResourceStr
```

ChipV2的无障碍描述。此描述用于向用户详细解释当前组件，开发人员应为组件的这一属性提供详尽的文本说明，以协助用户理解即将执行的操作及其可能产生的结果，特别是当这些结果无法仅从组件的属性和无障碍文本中直接获知时。如果组件同时具备 文本属性和无障碍说明属性，当组件被选中时，系统将首先播报组件的文本属性，随后播报无障碍说明属性的内容。 默认值：空字符串。 值为undefined时，按默认值处理。

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-@Trace  public accessibilityDescription?: ResourceStr--><!--Device-ChipV2Options-@Trace  public accessibilityDescription?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
@Trace
  public accessibilityLevel?: string
```

ChipV2的无障碍重要性。用于控制组件是否可被无障碍辅助服务所识别。 支持的值为： "auto"：当前组件会转换为"yes"。 "yes"：当前组件可被无障碍辅助服务所识别。 "no"：当前组件不可被无障碍辅助服务所识别。 "no-hide-descendants"：当前组件及其所有子组件不可被无障碍辅助服务所识别。 默认值："auto" 值为undefined时，按默认值处理。

**类型：** string

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-@Trace  public accessibilityLevel?: string--><!--Device-ChipV2Options-@Trace  public accessibilityLevel?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilitySelectedType

```TypeScript
@Trace
  public accessibilitySelectedType?: ChipV2AccessibilitySelectedType
```

ChipV2组件选中态类型。 默认值：当activated属性为true但未指定accessibilitySelectedType时，默认使用CHECKED类型。当activated属性为false或未设置时，默认使用CLICKED类型。 值为undefined时，按默认值处理。

**类型：** [ChipV2AccessibilitySelectedType](arkts-arkui-arkui-advanced-chipv2-chipv2accessibilityselectedtype-e.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-@Trace  public accessibilitySelectedType?: ChipV2AccessibilitySelectedType--><!--Device-ChipV2Options-@Trace  public accessibilitySelectedType?: ChipV2AccessibilitySelectedType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## activated

```TypeScript
@Trace
  public activated?: boolean
```

ChipV2是否为激活态。 默认值：false true：ChipV2为激活态；false：ChipV2为非激活态。 值为undefined时，按默认值处理。

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-@Trace  public activated?: boolean--><!--Device-ChipV2Options-@Trace  public activated?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## activatedBackgroundColor

```TypeScript
@Trace
  public activatedBackgroundColor?: ColorMetrics
```

ChipV2激活时的背景颜色。 默认值：\$r('sys.color.chip_container_activated_color') 值为undefined时，按默认值处理。 值为非法值时，背景颜色透明。

**类型：** ColorMetrics

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-@Trace  public activatedBackgroundColor?: ColorMetrics--><!--Device-ChipV2Options-@Trace  public activatedBackgroundColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## activatedBackgroundSystemMaterial

```TypeScript
@Trace
  public activatedBackgroundSystemMaterial?: uiMaterial.Material
```

设置组件激活状态下的系统材质样式。不同材质具有不同的效果，能够影响组件的背景色backgroundColor、 边框颜色borderColor、边框宽度borderWidth、阴影 shadow效果、材质层滤镜效果 materialFilter。 默认值：undefined，不应用材质样式。

**类型：** uiMaterial.Material

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-@Trace  public activatedBackgroundSystemMaterial?: uiMaterial.Material--><!--Device-ChipV2Options-@Trace  public activatedBackgroundSystemMaterial?: uiMaterial.Material-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## allowClose

```TypeScript
@Trace
  public allowClose?: boolean
```

是否显示关闭图标。 当`suffixIcon`有传入参数时，`allowClose`不生效；`suffixIcon`没有传入参数时，`allowClose`决定是否显示关闭图标。 默认值：true true：关闭图标显示；false：关闭图标不显示。 值为undefined时，按默认值处理。

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-@Trace  public allowClose?: boolean--><!--Device-ChipV2Options-@Trace  public allowClose?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
@Trace
  public backgroundColor?: ColorMetrics
```

ChipV2背景颜色。 默认值：\$r('sys.color.chip_background_color') 值为undefined时，按默认值处理。 值为非法值时，背景颜色透明。

**类型：** ColorMetrics

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-@Trace  public backgroundColor?: ColorMetrics--><!--Device-ChipV2Options-@Trace  public backgroundColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundSystemMaterial

```TypeScript
@Trace
  public backgroundSystemMaterial?: uiMaterial.Material
```

设置组件系统材质样式。不同材质具有不同的效果，能够影响组件的背景色backgroundColor、边框颜色 borderColor、边框宽度borderWidth、阴影 shadow效果、材质层滤镜效果 materialFilter。 默认值：undefined，不应用材质样式。

**类型：** uiMaterial.Material

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-@Trace  public backgroundSystemMaterial?: uiMaterial.Material--><!--Device-ChipV2Options-@Trace  public backgroundSystemMaterial?: uiMaterial.Material-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderRadius

```TypeScript
@Trace
  public borderRadius?: LengthMetrics
```

ChipV2背景圆角半径大小，不支持百分比。传入百分比时按默认值处理。 默认值： size为ChipV2Size.NORMAL时，borderRadius默认值为：`\$r('sys.float.chip_border_radius_normal')`。 size为ChipV2Size.SMALL时，borderRadius默认值为：`\$r('sys.float.chip_border_radius_small')` 单位：vp 值为undefined时，按默认值处理。

**类型：** LengthMetrics

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-@Trace  public borderRadius?: LengthMetrics--><!--Device-ChipV2Options-@Trace  public borderRadius?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## closeIcon

```TypeScript
@Trace
  public closeIcon?: ChipV2CloseIcon
```

关闭图标的配置，包括无障碍属性配置。当需要自定义关闭图标的大小或无障碍属性时设置此属性。 默认值： - 尺寸默认值：size为ChipV2Size.SMALL时，默认值为`\$r('sys.float.chip_small_font_size')`；其他情况默认值为 `\$r('sys.float.chip_normal_font_size')`。 - 无障碍默认值：无无障碍描述。 值为undefined时，按默认值处理。

**类型：** [ChipV2CloseIcon](arkts-arkui-arkui-advanced-chipv2-chipv2closeicon-c.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-@Trace  public closeIcon?: ChipV2CloseIcon--><!--Device-ChipV2Options-@Trace  public closeIcon?: ChipV2CloseIcon-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
@Trace
  public direction?: Direction
```

布局方向。 默认值：Direction.Auto 值为undefined时，按默认值处理。

**类型：** Direction

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-@Trace  public direction?: Direction--><!--Device-ChipV2Options-@Trace  public direction?: Direction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enabled

```TypeScript
@Trace
  public enabled?: boolean
```

ChipV2是否可用。 默认值：true true：ChipV2可用；false：ChipV2不可用。 值为undefined时，按默认值处理。

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-@Trace  public enabled?: boolean--><!--Device-ChipV2Options-@Trace  public enabled?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
@Trace
  public fontSize?: LengthMetrics
```

统一设置ChipV2组件的文本与图标的字体大小，不支持百分比。传入百分比时按默认值处理。 该fontSize的优先级低于prefixIcon、label、suffixIcon和closeIcon中的fontSize属性。 默认值： - size为ChipV2Size.SMALL时，文本默认值：`\$r('sys.float.chip_small_font_size')`；图标默认值：`\$r('sys.float.chip_small_icon_size')`。 - 其他情况下，文本默认值：`\$r('sys.float.chip_normal_font_size')`；图标默认值：`\$r('sys.float.chip_normal_icon_size')` 单位：fp 值为undefined时，按默认值处理。

**类型：** LengthMetrics

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-@Trace  public fontSize?: LengthMetrics--><!--Device-ChipV2Options-@Trace  public fontSize?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
@Trace
  public label: ChipV2Label
```

ChipV2前缀图标。 默认值：不显示前缀图标。 值为undefined时，按默认值处理。

**类型：** [ChipV2Label](arkts-arkui-arkui-advanced-chipv2-chipv2label-c.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-@Trace  public label: ChipV2Label--><!--Device-ChipV2Options-@Trace  public label: ChipV2Label-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxFontScale

```TypeScript
@Trace
  public maxFontScale?: number | Resource
```

ChipV2组件文本与图标的最大字体缩放倍数。 取值范围：[1, +∞) 设置的值小于1时，按值为1处理。异常值默认不生效。 默认值：1。 值为undefined时，按默认值处理。

**类型：** number \| Resource

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-@Trace  public maxFontScale?: number | Resource--><!--Device-ChipV2Options-@Trace  public maxFontScale?: number | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## minFontScale

```TypeScript
@Trace
  public minFontScale?: number | Resource
```

ChipV2组件文本与图标的最小字体缩放倍数。 取值范围：[0, 1] 设置的值小于0时，按值为0处理。设置的值大于1时，按值为1处理。异常值默认不生效。 默认值：1。 值为undefined时，按默认值处理。

**类型：** number \| Resource

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-@Trace  public minFontScale?: number | Resource--><!--Device-ChipV2Options-@Trace  public minFontScale?: number | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onClicked

```TypeScript
public onClicked?: Callback<void>
```

ChipV2点击事件回调函数。 当enabled为true时，点击ChipV2触发点击事件；当enabled为false时，不触发点击事件。 默认值：不执行该回调函数。 值为undefined时，按默认值处理。

**类型：** Callback&lt;void&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-public onClicked?: Callback<void>--><!--Device-ChipV2Options-public onClicked?: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onClose

```TypeScript
public onClose?: VoidCallback
```

默认关闭图标点击事件回调函数。 当allowClose为true且suffixIcon没有传入参数时，点击关闭图标执行此回调函数。 默认值：不执行该回调函数。 值为undefined时，按默认值处理。

**类型：** VoidCallback

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-public onClose?: VoidCallback--><!--Device-ChipV2Options-public onClose?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## padding

```TypeScript
@Trace
  public padding?: LocalizedPadding
```

ChipV2的内边距。 默认值： - size为ChipV2Size.SMALL并且activated为true时，默认值： `{ start: LengthMetrics.resource('sys.float.chip_activated_small_text_padding'), end: LengthMetrics.resource('sys.float.chip_activated_small_text_padding'), top: LengthMetrics.vp(4), bottom: LengthMetrics.vp(4)}`。 - size为ChipV2Size.SMALL并且activated为false时，默认值： `{ start: LengthMetrics.resource('sys.float.chip_small_text_padding'), end: LengthMetrics.resource('sys.float.chip_small_text_padding'), top: LengthMetrics.vp(4), bottom: LengthMetrics.vp(4)}`。 - size不为ChipV2Size.SMALL并且activated为true时，默认值： `{ start: LengthMetrics.resource('sys.float.chip_activated_normal_text_padding'), end: LengthMetrics.resource('sys.float.chip_activated_normal_text_padding'), top: LengthMetrics.vp(4), bottom: LengthMetrics.vp(4)}`。 - size不为ChipV2Size.SMALL并且activated为false时，默认值： `{ start: LengthMetrics.resource('sys.float.chip_normal_text_padding'), end: LengthMetrics.resource('sys.float.chip_normal_text_padding'), top: LengthMetrics.vp(4), bottom: LengthMetrics.vp(4)}`。 值为undefined时，按默认值处理。

**类型：** LocalizedPadding

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-@Trace  public padding?: LocalizedPadding--><!--Device-ChipV2Options-@Trace  public padding?: LocalizedPadding-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## prefixIcon

```TypeScript
@Trace
  public prefixIcon?: ChipV2Icon
```

ChipV2前缀图标。 默认值：不显示前缀图标。 值为undefined时，按默认值处理。

**类型：** [ChipV2Icon](arkts-arkui-arkui-advanced-chipv2-chipv2icon-c.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-@Trace  public prefixIcon?: ChipV2Icon--><!--Device-ChipV2Options-@Trace  public prefixIcon?: ChipV2Icon-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
@Trace
  public size?: ChipV2Size | SizeT<LengthMetrics>
```

ChipV2尺寸。 默认值：ChipV2Size.NORMAL SizeT&lt;LengthMetrics&gt;类型参数不支持百分比设置，异常值按默认值处理。 **说明：**[适老化](../../../ui/arkui-support-for-aging-adaptation.md)在size指定具体宽高时不生效，size设置为{ height: 0, width: 0 }除外。

**类型：** [ChipV2Size](arkts-arkui-arkui-advanced-chipv2-chipv2size-e.md) \| SizeT&lt;LengthMetrics&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-@Trace  public size?: ChipV2Size | SizeT<LengthMetrics>--><!--Device-ChipV2Options-@Trace  public size?: ChipV2Size | SizeT<LengthMetrics>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## suffixIcon

```TypeScript
@Trace
  public suffixIcon?: ChipV2Icon
```

ChipV2后缀图标。 默认值：不显示后缀图标。 值为undefined时，按默认值处理。 说明：当suffixIcon有传入参数时，allowClose属性不生效。

**类型：** [ChipV2Icon](arkts-arkui-arkui-advanced-chipv2-chipv2icon-c.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-@Trace  public suffixIcon?: ChipV2Icon--><!--Device-ChipV2Options-@Trace  public suffixIcon?: ChipV2Icon-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

