# ChipGroupV2ItemConfig

ChipGroupV2ItemConfig定义每个ChipV2的非通用属性配置。

**起始版本：** 26.0.0

<!--Device-unnamed-export interface ChipGroupV2ItemConfig--><!--Device-unnamed-export interface ChipGroupV2ItemConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ChipGroupV2ItemConfig, ChipGroupV2ItemStyleConfig, ChipGroupV2SpaceConfig, ChipGroupV2IconGroupSuffix, ChipGroupV2Items, ChipGroupV2Padding, ChipGroupV2Item, ChipGroupV2ItemStyle, ChipGroupV2, ChipGroupV2PaddingConfig, ChipGroupV2IconItemConfig, ChipGroupV2SymbolItemConfig, ChipGroupV2Space } from '@kit.ArkUI';
```

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

无障碍描述。此描述用于向用户详细解释当前组件，开发人员应为组件的这一属性提供较为详尽的文本说明，以协助用户理解即将执行的操作及其可能产生的结果。特别是当这些结果无法仅从组件的属性和无障碍文本中直接获知时。如果组件同时具备文本属性和无障碍说明属性，当组件被选中时，系统将首先播报组件的文本属性，随后播报无障碍说明属性的内容。

默认值：空字符串。

值为undefined时，按默认值处理。

**类型：** ResourceStr

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemConfig-accessibilityDescription?: ResourceStr--><!--Device-ChipGroupV2ItemConfig-accessibilityDescription?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

无障碍重要性。用于控制组件是否可被无障碍辅助服务所识别。

支持的值为：

"auto"：当前组件会转化为"yes"。

"yes"：当前组件可被无障碍辅助服务所识别。

"no"：当前组件不可被无障碍辅助服务所识别。

"no-hide-descendants"：当前组件及其所有子组件不可被无障碍辅助服务所识别。

默认值："auto"

值为undefined时，按默认值处理。

**类型：** string

**默认值：** auto

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemConfig-accessibilityLevel?: string--><!--Device-ChipGroupV2ItemConfig-accessibilityLevel?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## allowClose

```TypeScript
allowClose?: boolean
```

删除图标是否显示。

true表示删除图标显示，false表示删除图标不显示。

默认值：false

值为undefined时，按默认值处理。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemConfig-allowClose?: boolean--><!--Device-ChipGroupV2ItemConfig-allowClose?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## closeIcon

```TypeScript
closeIcon?: ChipV2CloseConfig
```

关闭图标的配置，包括无障碍属性配置。

默认值：

- 尺寸默认值：size为ChipV2Size.SMALL时，默认值为`$r('sys.float.chip_small_font_size')`；其他情况默认值为`$r('sys.float.chip_normal_font_size')`。  
- 无障碍默认值：无无障碍描述。

值为undefined时，按默认值处理。

**类型：** ChipV2CloseConfig

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemConfig-closeIcon?: ChipV2CloseConfig--><!--Device-ChipGroupV2ItemConfig-closeIcon?: ChipV2CloseConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
label: ChipV2LabelConfig
```

文本属性。

**类型：** ChipV2LabelConfig

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemConfig-label: ChipV2LabelConfig--><!--Device-ChipGroupV2ItemConfig-label: ChipV2LabelConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## prefixIcon

```TypeScript
prefixIcon?: ChipV2PrefixImageIconConfig
```

前缀图标属性。

默认值：没有前缀Image图标。

值为undefined时，按默认值处理。

**类型：** ChipV2PrefixImageIconConfig

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemConfig-prefixIcon?: ChipV2PrefixImageIconConfig--><!--Device-ChipGroupV2ItemConfig-prefixIcon?: ChipV2PrefixImageIconConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## prefixSymbolIcon

```TypeScript
prefixSymbolIcon?: ChipV2PrefixSymbolIconConfig
```

前缀Symbol图标属性。

默认值：没有前缀Symbol图标。

值为undefined时，按默认值处理。

**类型：** ChipV2PrefixSymbolIconConfig

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemConfig-prefixSymbolIcon?: ChipV2PrefixSymbolIconConfig--><!--Device-ChipGroupV2ItemConfig-prefixSymbolIcon?: ChipV2PrefixSymbolIconConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## suffixIcon

```TypeScript
suffixIcon?: ChipV2SuffixImageIconConfig
```

后缀图标属性。

默认值：不显示后缀Image图标。

值为undefined时，按默认值处理。

**类型：** ChipV2SuffixImageIconConfig

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemConfig-suffixIcon?: ChipV2SuffixImageIconConfig--><!--Device-ChipGroupV2ItemConfig-suffixIcon?: ChipV2SuffixImageIconConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## suffixSymbolIcon

```TypeScript
suffixSymbolIcon?: ChipV2SuffixSymbolIconConfig
```

后缀Symbol图标属性。

默认值：不显示后缀Symbol图标。

值为undefined时，按默认值处理。

**类型：** ChipV2SuffixSymbolIconConfig

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2ItemConfig-suffixSymbolIcon?: ChipV2SuffixSymbolIconConfig--><!--Device-ChipGroupV2ItemConfig-suffixSymbolIcon?: ChipV2SuffixSymbolIconConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

