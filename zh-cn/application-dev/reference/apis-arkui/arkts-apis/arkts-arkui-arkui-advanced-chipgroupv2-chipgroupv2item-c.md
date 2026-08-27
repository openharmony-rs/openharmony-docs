# ChipGroupV2Item

ChipGroupV2Item定义了ChipGroupV2组件中的单个操作块项。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ChipGroupV2ItemConfig, ChipGroupV2Item, ChipGroupV2Items, ChipGroupV2ItemStyleConfig, ChipGroupV2ItemStyle, ChipGroupV2SpaceConfig, ChipGroupV2Space, ChipGroupV2IconItemConfig, ChipGroupV2SymbolItemConfig, ChipGroupV2PaddingConfig, ChipGroupV2Padding, ChipGroupV2IconGroupSuffix, ChipGroupV2 } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(config: ChipGroupV2ItemConfig)
```

ChipGroupV2Item的构造函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [ChipGroupV2ItemConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2itemconfig-i.md) | 是 | ChipGroupV2项配置。 |

## accessibilityDescription

```TypeScript
public accessibilityDescription?: ResourceStr
```

ChipGroupV2中ChipV2项的无障碍描述。此描述用于向用户详细解释ChipGroupV2中ChipV2项，开发人员应为ChipGroupV2中ChipV2项的属性提供较为详尽的文本说明，以协助用户理解即将执行的操作及 其可能产生的结果，特别是当这些结果无法仅从ChipGroupV2中ChipV2项的属性和无障碍文本中直接获知时。如果ChipGroupV2中ChipV2项同时具备文本属性和无障碍说明属性，当ChipGroupV2中ChipV2 项被选中时，系统将首先播报ChipGroupV2中ChipV2项的文本属性，随后播报无障碍说明属性的内容。默认值：空字符串。值为undefined时，按默认值处理。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
public accessibilityLevel?: string
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
public allowClose?: boolean
```

关闭图标是否显示。取值原则：true表示关闭图标显示，false表示关闭图标不显示。当传入suffixIcon或suffixSymbolIcon参数时，allowClose不生效；未传入suffixIcon和 suffixSymbolIcon参数时，allowClose决定是否显示关闭图标。默认值：false值为undefined时，按默认值处理。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## closeIcon

```TypeScript
public closeIcon?: ChipV2CloseConfig
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
public label: ChipV2Label
```

ChipV2文本属性。

**类型：** [ChipV2Label](arkts-arkui-arkui-advanced-chipv2-chipv2label-c.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## prefixIcon

```TypeScript
public prefixIcon?: ChipV2PrefixImageIcon
```

前缀Image图标属性，用于在ChipV2文本前显示Image图标。当需要在ChipV2左侧显示图标标识时设置此属性。默认值：没有前缀Image图标。值为undefined时，按默认值处理。

**类型：** [ChipV2PrefixImageIcon](arkts-arkui-arkui-advanced-chipv2-chipv2prefiximageicon-c.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## prefixSymbolIcon

```TypeScript
public prefixSymbolIcon?: ChipV2PrefixSymbolIcon
```

前缀Symbol图标属性，用于在ChipV2文本前显示Symbol图标。当需要在ChipV2左侧显示Symbol图标标识时设置此属性。默认值：没有前缀Symbol图标。值为undefined时，按默认值处理。

**类型：** [ChipV2PrefixSymbolIcon](arkts-arkui-arkui-advanced-chipv2-chipv2prefixsymbolicon-c.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## suffixIcon

```TypeScript
public suffixIcon?: ChipV2SuffixImageIcon
```

后缀Image图标属性，用于在ChipV2文本后显示Image图标。设置该属性时，allowClose属性将不生效。默认值：不显示后缀Image图标。值为undefined时，按默认值处理。

**类型：** [ChipV2SuffixImageIcon](arkts-arkui-arkui-advanced-chipv2-chipv2suffiximageicon-c.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## suffixSymbolIcon

```TypeScript
public suffixSymbolIcon?: ChipV2SuffixSymbolIcon
```

后缀Symbol图标属性，用于在ChipV2文本后显示Symbol图标。设置该属性时，allowClose属性将不生效。默认值：不显示后缀Symbol图标。值为undefined时，按默认值处理。

**类型：** [ChipV2SuffixSymbolIcon](arkts-arkui-arkui-advanced-chipv2-chipv2suffixsymbolicon-c.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
