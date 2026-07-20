# ChipGroupV2ItemStyleConfig

ChipGroupV2ItemStyle定义了ChipV2的共通属性类。

**起始版本：** 26.0.0

<!--Device-unnamed-export interface ChipGroupV2ItemStyleConfig--><!--Device-unnamed-export interface ChipGroupV2ItemStyleConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ChipGroupV2ItemConfig, ChipGroupV2ItemStyleConfig, ChipGroupV2SpaceConfig, ChipGroupV2IconGroupSuffix, ChipGroupV2Items, ChipGroupV2Padding, ChipGroupV2Item, ChipGroupV2ItemStyle, ChipGroupV2, ChipGroupV2PaddingConfig, ChipGroupV2IconItemConfig, ChipGroupV2SymbolItemConfig, ChipGroupV2Space } from '@kit.ArkUI';
```

## backgroundColor

```TypeScript
backgroundColor?: ColorMetrics
```

ChipV2背景颜色。

默认值：$r('sys.color.ohos_id_color_button_normal')

值为undefined时，按默认值处理。

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

设置组件系统材质样式。不同材质具有不同的效果，能够影响组件的背景色[backgroundColor](../arkts-components/arkts-arkui-commonmethod-c.md#backgroundcolor-1)、边框颜色[borderColor](../arkts-components/arkts-arkui-commonmethod-c.md#bordercolor-1)、边框宽度[borderWidth](../arkts-components/arkts-arkui-commonmethod-c.md#borderwidth-1)、阴影[shadow](../arkts-components/arkts-arkui-commonmethod-c.md#shadow-1)效果、材质层滤镜效果[materialFilter](../arkts-components/arkts-arkui-commonmethod-c.md#materialfilter-1)。

默认值：undefined，不应用材质样式。

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

ChipV2文字颜色。

默认值：$r('sys.color.ohos_id_color_text_primary')

值为undefined时，按默认值处理。

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

ChipV2激活时的背景颜色。

默认值：$r('sys.color.ohos_id_color_emphasize')

值为undefined时，按默认值处理。

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

设置组件选中状态下的系统材质样式。不同材质具有不同的效果，能够影响组件的背景色[backgroundColor](../arkts-components/arkts-arkui-commonmethod-c.md#backgroundcolor-1)、边框颜色[borderColor](../arkts-components/arkts-arkui-commonmethod-c.md#bordercolor-1)、边框宽度[borderWidth](../arkts-components/arkts-arkui-commonmethod-c.md#borderwidth-1)、阴影[shadow](../arkts-components/arkts-arkui-commonmethod-c.md#shadow-1)效果、材质层滤镜效果[materialFilter](../arkts-components/arkts-arkui-commonmethod-c.md#materialfilter-1)。

默认值：undefined，不应用材质样式。

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

ChipV2激活时的文字颜色。

默认值：$r('sys.color.ohos_id_color_text_primary_contrary')

值为undefined时，按默认值处理。

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

ChipV2尺寸。

默认值：ChipV2Size.NORMAL

值为undefined时，按默认值处理。

**类型：** ChipV2Size \| SizeT&lt;LengthMetrics&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemStyleConfig-size?: ChipV2Size | SizeT<LengthMetrics>--><!--Device-ChipGroupV2ItemStyleConfig-size?: ChipV2Size | SizeT<LengthMetrics>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

