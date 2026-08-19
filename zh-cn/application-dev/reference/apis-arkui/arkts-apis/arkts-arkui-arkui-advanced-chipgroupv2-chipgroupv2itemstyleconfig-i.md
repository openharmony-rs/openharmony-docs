# ChipGroupV2ItemStyleConfig

ChipGroupV2ItemStyleConfig定义了ChipV2的共通属性配置。

**起始版本：** 26.0.0

<!--Device-unnamed-export interface ChipGroupV2ItemStyleConfig--><!--Device-unnamed-export interface ChipGroupV2ItemStyleConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ChipGroupV2ItemConfig, ChipGroupV2Item, ChipGroupV2Items, ChipGroupV2ItemStyleConfig, ChipGroupV2ItemStyle, ChipGroupV2SpaceConfig, ChipGroupV2Space, ChipGroupV2IconItemConfig, ChipGroupV2SymbolItemConfig, ChipGroupV2PaddingConfig, ChipGroupV2Padding, ChipGroupV2IconGroupSuffix, ChipGroupV2 } from '@kit.ArkUI';
```

## backgroundColor

```TypeScript
backgroundColor?: ColorMetrics
```

ChipV2背景颜色。 默认值：\$r('sys.color.ohos_id_color_button_normal') 值为undefined时，按默认值处理。

**类型：** ColorMetrics

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemStyleConfig-backgroundColor?: ColorMetrics--><!--Device-ChipGroupV2ItemStyleConfig-backgroundColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundSystemMaterial

```TypeScript
backgroundSystemMaterial?: uiMaterial.Material
```

设置组件系统材质样式。不同材质具有不同的效果，能够影响组件的背景色backgroundColor、边框颜色 borderColor、边框宽度borderWidth、阴影 shadow效果、材质层滤镜效果 materialFilter。 默认值：undefined，不应用材质样式。

**类型：** uiMaterial.Material

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemStyleConfig-backgroundSystemMaterial?: uiMaterial.Material--><!--Device-ChipGroupV2ItemStyleConfig-backgroundSystemMaterial?: uiMaterial.Material-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ColorMetrics
```

ChipV2文字颜色。 默认值：\$r('sys.color.ohos_id_color_text_primary') 值为undefined时，按默认值处理。

**类型：** ColorMetrics

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemStyleConfig-fontColor?: ColorMetrics--><!--Device-ChipGroupV2ItemStyleConfig-fontColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor?: ColorMetrics
```

ChipV2选中时的背景颜色。设置后，当ChipV2被选中时，背景会填充此颜色，替代未选中状态下的backgroundColor。 默认值：\$r('sys.color.ohos_id_color_emphasize') 值为undefined时，按默认值处理。

**类型：** ColorMetrics

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemStyleConfig-selectedBackgroundColor?: ColorMetrics--><!--Device-ChipGroupV2ItemStyleConfig-selectedBackgroundColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedBackgroundSystemMaterial

```TypeScript
selectedBackgroundSystemMaterial?: uiMaterial.Material
```

设置组件选中状态下的系统材质样式。设置后，当ChipV2被选中时，应用此材质样式，替代未选中状态下的backgroundSystemMaterial。不同材质具有不同的效果，能够影响组件的背景色 backgroundColor、边框颜色 borderColor、边框宽度borderWidth、阴影 shadow效果、材质层滤镜效果 materialFilter。 默认值：undefined，不应用材质样式。

**类型：** uiMaterial.Material

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemStyleConfig-selectedBackgroundSystemMaterial?: uiMaterial.Material--><!--Device-ChipGroupV2ItemStyleConfig-selectedBackgroundSystemMaterial?: uiMaterial.Material-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedFontColor

```TypeScript
selectedFontColor?: ColorMetrics
```

ChipV2选中时的文字颜色。设置后，当ChipV2被选中时，label文本会显示此颜色，替代未选中状态下的fontColor。 默认值：\$r('sys.color.ohos_id_color_text_primary_contrary') 值为undefined时，按默认值处理。

**类型：** ColorMetrics

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemStyleConfig-selectedFontColor?: ColorMetrics--><!--Device-ChipGroupV2ItemStyleConfig-selectedFontColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: ChipV2Size | SizeT<LengthMetrics>
```

ChipV2尺寸，使用时需要从ChipV2组件引入ChipV2Size类型。 默认值：ChipV2Size.NORMAL 值为undefined时，按默认值处理。

**类型：** [ChipV2Size](arkts-arkui-arkui-advanced-chipv2-chipv2size-e.md) \| SizeT&lt;LengthMetrics&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemStyleConfig-size?: ChipV2Size | SizeT<LengthMetrics>--><!--Device-ChipGroupV2ItemStyleConfig-size?: ChipV2Size | SizeT<LengthMetrics>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

