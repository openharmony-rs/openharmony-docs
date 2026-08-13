# ChipGroupV2ItemStyle

ChipGroupV2ItemStyleConfig定义了ChipV2的共通属性配置。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare class ChipGroupV2ItemStyle--><!--Device-unnamed-export declare class ChipGroupV2ItemStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(config: ChipGroupV2ItemStyleConfig)
```

ChipGroupV2ItemStyle的构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemStyle-constructor(config: ChipGroupV2ItemStyleConfig)--><!--Device-ChipGroupV2ItemStyle-constructor(config: ChipGroupV2ItemStyleConfig)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [ChipGroupV2ItemStyleConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2itemstyleconfig-i.md) | 是 | ChipGroupV2项样式配置。 |

## backgroundColor

```TypeScript
@Trace
  public backgroundColor?: ColorMetrics
```

ChipV2背景颜色。 默认值：\$r('sys.color.ohos_id_color_button_normal') 值为undefined时，按默认值处理。

**类型：** ColorMetrics

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemStyle-@Trace  public backgroundColor?: ColorMetrics--><!--Device-ChipGroupV2ItemStyle-@Trace  public backgroundColor?: ColorMetrics-End-->

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

<!--Device-ChipGroupV2ItemStyle-@Trace  public backgroundSystemMaterial?: uiMaterial.Material--><!--Device-ChipGroupV2ItemStyle-@Trace  public backgroundSystemMaterial?: uiMaterial.Material-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
@Trace
  public fontColor?: ColorMetrics
```

ChipV2文字颜色。 默认值：\$r('sys.color.ohos_id_color_text_primary') 值为undefined时，按默认值处理。

**类型：** ColorMetrics

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemStyle-@Trace  public fontColor?: ColorMetrics--><!--Device-ChipGroupV2ItemStyle-@Trace  public fontColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedBackgroundColor

```TypeScript
@Trace
  public selectedBackgroundColor?: ColorMetrics
```

ChipV2选中时的背景颜色。设置后，当ChipV2被选中时，背景会填充此颜色，替代未选中状态下的backgroundColor。 默认值：\$r('sys.color.ohos_id_color_emphasize') 值为undefined时，按默认值处理。

**类型：** ColorMetrics

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemStyle-@Trace  public selectedBackgroundColor?: ColorMetrics--><!--Device-ChipGroupV2ItemStyle-@Trace  public selectedBackgroundColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedBackgroundSystemMaterial

```TypeScript
@Trace
  public selectedBackgroundSystemMaterial?: uiMaterial.Material
```

设置组件选中状态下的系统材质样式。设置后，当ChipV2被选中时，应用此材质样式，替代未选中状态下的backgroundSystemMaterial。不同材质具有不同的效果，能够影响组件的背景色 backgroundColor、边框颜色 borderColor、边框宽度borderWidth、阴影 shadow效果、材质层滤镜效果 materialFilter。 默认值：undefined，不应用材质样式。

**类型：** uiMaterial.Material

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemStyle-@Trace  public selectedBackgroundSystemMaterial?: uiMaterial.Material--><!--Device-ChipGroupV2ItemStyle-@Trace  public selectedBackgroundSystemMaterial?: uiMaterial.Material-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedFontColor

```TypeScript
@Trace
  public selectedFontColor?: ColorMetrics
```

ChipV2选中时的文字颜色。设置后，当ChipV2被选中时，label文本会显示此颜色，替代未选中状态下的fontColor。 默认值：\$r('sys.color.ohos_id_color_text_primary_contrary') 值为undefined时，按默认值处理。

**类型：** ColorMetrics

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemStyle-@Trace  public selectedFontColor?: ColorMetrics--><!--Device-ChipGroupV2ItemStyle-@Trace  public selectedFontColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
@Trace
  public size?: ChipV2Size | SizeT<LengthMetrics>
```

ChipV2尺寸，使用时需要从ChipV2组件引入ChipV2Size类型。 默认值：ChipV2Size.NORMAL 值为undefined时，按默认值处理。

**类型：** [ChipV2Size](arkts-arkui-arkui-advanced-chipv2-chipv2size-e.md) \| SizeT&lt;LengthMetrics&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemStyle-@Trace  public size?: ChipV2Size | SizeT<LengthMetrics>--><!--Device-ChipGroupV2ItemStyle-@Trace  public size?: ChipV2Size | SizeT<LengthMetrics>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

