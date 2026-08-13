# ChipV2SymbolIcon

ChipV2SymbolIcon定义Symbol图标类。 继承自[ChipV2Icon](arkts-arkui-arkui-advanced-chipv2-chipv2icon-c.md#ChipV2Icon)。

**继承/实现关系：** ChipV2SymbolIcon extends [ChipV2Icon](arkts-arkui-arkui-advanced-chipv2-chipv2icon-c.md#ChipV2Icon)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export abstract class ChipV2SymbolIcon--><!--Device-unnamed-export abstract class ChipV2SymbolIcon-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(config: ChipV2SymbolIconConfig)
```

ChipV2SymbolIcon的构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2SymbolIcon-constructor(config: ChipV2SymbolIconConfig)--><!--Device-ChipV2SymbolIcon-constructor(config: ChipV2SymbolIconConfig)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [ChipV2SymbolIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2symboliconconfig-i.md) | 是 | Symbol图标属性配置，用于设置Symbol类型图标在不同状态下的显示属性，包含normal、activated等配置项。 |

## activated

```TypeScript
@Trace
  public activated?: SymbolGlyphModifier
```

激活时图标设定。 默认值：不显示前缀图标或后缀图标。 值为undefined时，按默认值处理。 不支持使用SymbolEffect修改动效类型及 effectStrategy设置动效。

**类型：** [SymbolGlyphModifier](../arkts-components/arkts-arkui-symbolglyphmodifier-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2SymbolIcon-@Trace  public activated?: SymbolGlyphModifier--><!--Device-ChipV2SymbolIcon-@Trace  public activated?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## normal

```TypeScript
@Trace
  public normal?: SymbolGlyphModifier
```

非激活时图标设定。 默认值：不显示前缀图标或后缀图标。 值为undefined时，按默认值处理。 不支持使用SymbolEffect修改动效类型及 effectStrategy设置动效。

**类型：** [SymbolGlyphModifier](../arkts-components/arkts-arkui-symbolglyphmodifier-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2SymbolIcon-@Trace  public normal?: SymbolGlyphModifier--><!--Device-ChipV2SymbolIcon-@Trace  public normal?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

