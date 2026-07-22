# ChipGroupV2Space

ChipGroupV2Space定义了ChipGroupV2左右内边距，以及Chip与Chip之间的间距。

**起始版本：** 26.0.0

**装饰器类型：** @ObservedV2

<!--Device-unnamed-export declare class ChipGroupV2Space--><!--Device-unnamed-export declare class ChipGroupV2Space-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ChipGroupV2ItemConfig, ChipGroupV2ItemStyleConfig, ChipGroupV2SpaceConfig, ChipGroupV2IconGroupSuffix, ChipGroupV2Items, ChipGroupV2Padding, ChipGroupV2Item, ChipGroupV2ItemStyle, ChipGroupV2, ChipGroupV2PaddingConfig, ChipGroupV2IconItemConfig, ChipGroupV2SymbolItemConfig, ChipGroupV2Space } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(config: ChipGroupV2SpaceConfig)
```

ChipGroupV2Space的构造函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2Space-constructor(config: ChipGroupV2SpaceConfig)--><!--Device-ChipGroupV2Space-constructor(config: ChipGroupV2SpaceConfig)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [ChipGroupV2SpaceConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2spaceconfig-i.md) | 是 | 芯片组间距配置。 |

## endSpace

```TypeScript
public endSpace?: Length
```

右侧内边距（不支持百分比）。

默认值：16

单位：vp

值为undefined时，按默认值处理。

**类型：** Length

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2Space-public endSpace?: Length--><!--Device-ChipGroupV2Space-public endSpace?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemSpace

```TypeScript
public itemSpace?: string | number
```

ChipV2与ChipV2之间的间距（不支持百分比）。

取值范围：

- number类型：[0, +∞)，如0、8、16、24.5。  
- string类型：单位为fp|vp|px|lpx且数值部分大于等于0的字符串，如"8vp"、"16fp"、"12px"、"10lpx"。  
- 不支持：负数、百分比单位、无效字符串格式。

默认值：8

单位：vp

值为undefined时，按默认值处理。

**类型：** string \| number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2Space-public itemSpace?: string | number--><!--Device-ChipGroupV2Space-public itemSpace?: string | number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## startSpace

```TypeScript
public startSpace?: Length
```

左侧内边距（不支持百分比）。

默认值：16

单位：vp

值为undefined时，按默认值处理。

**类型：** Length

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2Space-public startSpace?: Length--><!--Device-ChipGroupV2Space-public startSpace?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

