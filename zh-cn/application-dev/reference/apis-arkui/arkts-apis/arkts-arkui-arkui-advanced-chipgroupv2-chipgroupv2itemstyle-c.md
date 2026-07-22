# ChipGroupV2ItemStyle

ChipGroupV2ItemStyle定义了ChipV2的共通属性类。

**起始版本：** 26.0.0

**装饰器类型：** @ObservedV2

<!--Device-unnamed-export declare class ChipGroupV2ItemStyle--><!--Device-unnamed-export declare class ChipGroupV2ItemStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ChipGroupV2ItemConfig, ChipGroupV2ItemStyleConfig, ChipGroupV2SpaceConfig, ChipGroupV2IconGroupSuffix, ChipGroupV2Items, ChipGroupV2Padding, ChipGroupV2Item, ChipGroupV2ItemStyle, ChipGroupV2, ChipGroupV2PaddingConfig, ChipGroupV2IconItemConfig, ChipGroupV2SymbolItemConfig, ChipGroupV2Space } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(config: ChipGroupV2ItemStyleConfig)
```

ChipGroupV2ItemStyle的构造函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemStyle-constructor(config: ChipGroupV2ItemStyleConfig)--><!--Device-ChipGroupV2ItemStyle-constructor(config: ChipGroupV2ItemStyleConfig)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [ChipGroupV2ItemStyleConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2itemstyleconfig-i.md) | 是 | 芯片组项样式配置。 |

## backgroundColor

```TypeScript
public backgroundColor?: ColorMetrics
```

ChipV2背景颜色。

默认值：$r('sys.color.ohos_id_color_button_normal')

值为undefined时，按默认值处理。

**类型：** ColorMetrics

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemStyle-public backgroundColor?: ColorMetrics--><!--Device-ChipGroupV2ItemStyle-public backgroundColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundSystemMaterial

```TypeScript
public backgroundSystemMaterial?: uiMaterial.Material
```

设置组件系统材质样式。不同材质具有不同的效果，能够影响组件的背景色[backgroundColor](../arkts-components/arkts-arkui-commonmethod-c.md#backgroundcolor)、边框颜色[borderColor](../arkts-components/arkts-arkui-commonmethod-c.md#bordercolor)、边框宽度[borderWidth](../arkts-components/arkts-arkui-commonmethod-c.md#borderwidth)、阴影[shadow](../arkts-components/arkts-arkui-commonmethod-c.md#shadow)效果、材质层滤镜效果[materialFilter](../arkts-components/arkts-arkui-commonmethod-c.md#materialfilter)。

默认值：undefined，不应用材质样式。

**类型：** uiMaterial.Material

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemStyle-public backgroundSystemMaterial?: uiMaterial.Material--><!--Device-ChipGroupV2ItemStyle-public backgroundSystemMaterial?: uiMaterial.Material-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
public fontColor?: ColorMetrics
```

ChipV2文字颜色。

默认值：$r('sys.color.ohos_id_color_text_primary')

值为undefined时，按默认值处理。

**类型：** ColorMetrics

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemStyle-public fontColor?: ColorMetrics--><!--Device-ChipGroupV2ItemStyle-public fontColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedBackgroundColor

```TypeScript
public selectedBackgroundColor?: ColorMetrics
```

ChipV2激活时的背景颜色。

默认值：$r('sys.color.ohos_id_color_emphasize')

值为undefined时，按默认值处理。

**类型：** ColorMetrics

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemStyle-public selectedBackgroundColor?: ColorMetrics--><!--Device-ChipGroupV2ItemStyle-public selectedBackgroundColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedBackgroundSystemMaterial

```TypeScript
public selectedBackgroundSystemMaterial?: uiMaterial.Material
```

设置组件选中状态下的系统材质样式。不同材质具有不同的效果，能够影响组件的背景色[backgroundColor](../arkts-components/arkts-arkui-commonmethod-c.md#backgroundcolor)、边框颜色[borderColor](../arkts-components/arkts-arkui-commonmethod-c.md#bordercolor)、边框宽度[borderWidth](../arkts-components/arkts-arkui-commonmethod-c.md#borderwidth)、阴影[shadow](../arkts-components/arkts-arkui-commonmethod-c.md#shadow)效果、材质层滤镜效果[materialFilter](../arkts-components/arkts-arkui-commonmethod-c.md#materialfilter)。

默认值：undefined，不应用材质样式。

**类型：** uiMaterial.Material

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemStyle-public selectedBackgroundSystemMaterial?: uiMaterial.Material--><!--Device-ChipGroupV2ItemStyle-public selectedBackgroundSystemMaterial?: uiMaterial.Material-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedFontColor

```TypeScript
public selectedFontColor?: ColorMetrics
```

ChipV2激活时的文字颜色。

默认值：$r('sys.color.ohos_id_color_text_primary_contrary')

值为undefined时，按默认值处理。

**类型：** ColorMetrics

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemStyle-public selectedFontColor?: ColorMetrics--><!--Device-ChipGroupV2ItemStyle-public selectedFontColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
public size?: ChipV2Size | SizeT<LengthMetrics>
```

ChipV2尺寸。

默认值：ChipV2Size.NORMAL

值为undefined时，按默认值处理。

**类型：** ChipV2Size \| SizeT&lt;LengthMetrics&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemStyle-public size?: ChipV2Size | SizeT<LengthMetrics>--><!--Device-ChipGroupV2ItemStyle-public size?: ChipV2Size | SizeT<LengthMetrics>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

