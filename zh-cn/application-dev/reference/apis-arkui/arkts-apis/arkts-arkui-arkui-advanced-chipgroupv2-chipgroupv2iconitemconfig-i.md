# ChipGroupV2IconItemConfig

ChipGroupV2IconItemConfig定义了尾部builder接口配置，针对背板大小及颜色设置限制。

**起始版本：** 26.0.0

<!--Device-unnamed-export interface ChipGroupV2IconItemConfig--><!--Device-unnamed-export interface ChipGroupV2IconItemConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ChipGroupV2ItemConfig, ChipGroupV2ItemStyleConfig, ChipGroupV2SpaceConfig, ChipGroupV2IconGroupSuffix, ChipGroupV2Items, ChipGroupV2Padding, ChipGroupV2Item, ChipGroupV2ItemStyle, ChipGroupV2, ChipGroupV2PaddingConfig, ChipGroupV2IconItemConfig, ChipGroupV2SymbolItemConfig, ChipGroupV2Space } from '@kit.ArkUI';
```

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

尾部图标无障碍描述。此描述用于向用户详细解释尾部图标，开发人员应为尾部图标的这一属性提供较为详尽的文本说明，以协助用户理解即将执行的操作及其可能产生的后果。特别是当这些后果无法仅从尾部图标的属性和无障碍文本中直接获知时。如果尾部图标同时具备文本属性和无障碍说明属性，当尾部图标被选中时，系统将首先播报尾部图标的文本属性，随后播报无障碍说明属性的内容。

默认值：空字符串。

值为undefined时，按默认值处理。

**类型：** ResourceStr

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2IconItemConfig-accessibilityDescription?: ResourceStr--><!--Device-ChipGroupV2IconItemConfig-accessibilityDescription?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

尾部图标无障碍重要性。用于控制尾部图标是否可被无障碍辅助服务所识别。

支持的值为：

"auto"：尾部图标转化为"yes"。

"yes"：尾部图标可被无障碍辅助服务所识别。

"no"：尾部图标不可被无障碍辅助服务所识别。

"no-hide-descendants"：尾部图标及其所有子组件不可被无障碍辅助服务所识别。

默认值："auto"

值为undefined时，按默认值处理。

**类型：** string

**默认值：** auto

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2IconItemConfig-accessibilityLevel?: string--><!--Device-ChipGroupV2IconItemConfig-accessibilityLevel?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
accessibilityText?: ResourceStr
```

尾部图标无障碍文本属性。用于为用户进一步说明尾部图标，开发人员可为尾部图标的该属性设置相对较详细的解释文本，帮助用户理解将要执行的操作。如帮助用户理解将要执行的操作可能导致什么后果，尤其是当这些后果无法从尾部图标本身属性与无障碍文本中了解到时。若尾部图标既拥有文本属性又拥有无障碍说明属性，则尾部图标被选中时，先播报尾部图标的文本属性，再播报无障碍说明属性的内容。

默认值：空字符串。

值为undefined时，按默认值处理。

**类型：** ResourceStr

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2IconItemConfig-accessibilityText?: ResourceStr--><!--Device-ChipGroupV2IconItemConfig-accessibilityText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action: Callback<void>
```

自定义尾部图标的响应事件。

**类型：** Callback<void>

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2IconItemConfig-action: Callback<void>--><!--Device-ChipGroupV2IconItemConfig-action: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon: ChipV2ImageIconConfig
```

自定义尾部图标。

Chip大小是ChipV2Size.SMALL时，图标尺寸为：{ width: 16, height: 16 }。

Chip大小是ChipV2Size.NORMAL时，图标尺寸为：{ width: 24, height: 24 }。</br> 如果想动态修改图标尺寸，那么必须在引入[ChipGroupV2IconGroupSuffix](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2icongroupsuffix-s.md)时，使用[SymbolGlyphModifier](./arkui/SymbolGlyphModifier:SymbolGlyphModifier)类型。

**类型：** ChipV2ImageIconConfig

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2IconItemConfig-icon: ChipV2ImageIconConfig--><!--Device-ChipGroupV2IconItemConfig-icon: ChipV2ImageIconConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

