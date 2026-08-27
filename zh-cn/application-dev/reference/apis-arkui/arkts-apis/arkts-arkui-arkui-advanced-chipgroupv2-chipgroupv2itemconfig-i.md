# ChipGroupV2ItemConfig

ChipGroupV2ItemConfig定义每个ChipV2的非通用属性配置。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ChipGroupV2ItemConfig, ChipGroupV2Item, ChipGroupV2Items, ChipGroupV2ItemStyleConfig, ChipGroupV2ItemStyle, ChipGroupV2SpaceConfig, ChipGroupV2Space, ChipGroupV2IconItemConfig, ChipGroupV2SymbolItemConfig, ChipGroupV2PaddingConfig, ChipGroupV2Padding, ChipGroupV2IconGroupSuffix, ChipGroupV2 } from '@kit.ArkUI';
```

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

ChipGroupV2中ChipV2项的无障碍描述。此描述用于向用户详细解释ChipGroupV2中ChipV2项，开发人员应为ChipGroupV2中ChipV2项的属性提供较为详尽的文本说明，以协助用户理解即将执行的操作及 其可能产生的结果，特别是当这些结果无法仅从ChipGroupV2中ChipV2项的属性和无障碍文本中直接获知时。如果ChipGroupV2中ChipV2项同时具备文本属性和无障碍说明属性，当ChipGroupV2中ChipV2 项被选中时，系统将首先播报ChipGroupV2中ChipV2项的文本属性，随后播报无障碍说明属性的内容。默认值：空字符串。值为undefined时，按默认值处理。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

ChipGroupV2中ChipV2项无障碍重要性。用于控制ChipGroupV2中ChipV2项是否可被无障碍辅助服务所识别。支持的值为："auto"：ChipGroupV2中ChipV2项会转换为"yes"。"yes"：ChipGroupV2中ChipV2项可被无障碍辅助服务所识别。"no"：ChipGroupV2中ChipV2项不可被无障碍辅助服务所识别。"no-hide-descendants"：ChipGroupV2中ChipV2项及其所有子组件不可被无障碍辅助服务所识别。传入不在支持范围内的值时，按默认值处理。默认值："auto"值为undefined时，按默认值处理。

**类型：** string

**默认值：** auto

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## allowClose

```TypeScript
allowClose?: boolean
```

关闭图标是否显示。取值原则：true表示关闭图标显示，false表示关闭图标不显示。当传入suffixIcon或suffixSymbolIcon参数时，allowClose不生效；未传入suffixIcon和suffixSymbolIcon参数时，allowClose决定是否显示关闭图标。默认值：false值为undefined时，按默认值处理。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## closeIcon

```TypeScript
closeIcon?: ChipV2CloseConfig
```

关闭图标的配置，包括无障碍属性配置。当需要自定义关闭图标的大小或无障碍属性时设置此属性。默认值：  
- fontSize默认值：size为ChipV2Size.SMALL时，默认值为`\$r('sys.float.chip_small_font_size')`；其他情况默认值为  
`\$r('sys.float.chip_normal_font_size')`。  
- 无障碍默认值：无无障碍描述。  
值为undefined时，按默认值处理。

**类型：** [ChipV2CloseConfig](arkts-arkui-arkui-advanced-chipv2-chipv2closeconfig-i.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
label: ChipV2LabelConfig
```

文本属性。

**类型：** [ChipV2LabelConfig](arkts-arkui-arkui-advanced-chipv2-chipv2labelconfig-i.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## prefixIcon

```TypeScript
prefixIcon?: ChipV2PrefixImageIconConfig
```

前缀Image图标属性，用于在ChipV2文本前显示Image图标。当需要在ChipV2左侧显示图标标识时设置此属性。默认值：没有前缀Image图标。值为undefined时，按默认值处理。

**类型：** [ChipV2PrefixImageIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2prefiximageiconconfig-i.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## prefixSymbolIcon

```TypeScript
prefixSymbolIcon?: ChipV2PrefixSymbolIconConfig
```

前缀Symbol图标属性，用于在ChipV2文本前显示Symbol图标。当需要在ChipV2左侧显示Symbol图标标识时设置此属性。默认值：没有前缀Symbol图标。值为undefined时，按默认值处理。

**类型：** [ChipV2PrefixSymbolIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2prefixsymboliconconfig-i.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## suffixIcon

```TypeScript
suffixIcon?: ChipV2SuffixImageIconConfig
```

后缀Image图标属性，用于在ChipV2文本后显示Image图标。设置该属性时，allowClose属性将不生效。默认值：不显示后缀Image图标。值为undefined时，按默认值处理。

**类型：** [ChipV2SuffixImageIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2suffiximageiconconfig-i.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## suffixSymbolIcon

```TypeScript
suffixSymbolIcon?: ChipV2SuffixSymbolIconConfig
```

后缀Symbol图标属性，用于在ChipV2文本后显示Symbol图标。设置该属性时，allowClose属性将不生效。默认值：不显示后缀Symbol图标。值为undefined时，按默认值处理。

**类型：** [ChipV2SuffixSymbolIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2suffixsymboliconconfig-i.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
