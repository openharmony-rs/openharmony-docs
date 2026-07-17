# ChipGroupSpaceOptions

ChipGroupSpaceOptions 定义了ChipGroup左右内边距，以及Chip与Chip之间的间距。

**起始版本：** 12

<!--Device-unnamed-export interface ChipGroupSpaceOptions--><!--Device-unnamed-export interface ChipGroupSpaceOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ChipItemLabelOptions, ChipGroupSpaceOptions, SymbolItemOptions, SuffixImageIconOptions, IconGroupSuffix, IconItemOptions, ChipItemStyle, ChipGroupItemOptions, ChipGroup, IconOptions } from '@kit.ArkUI';
```

## endSpace

```TypeScript
endSpace?: Length
```

右侧内边距（不支持百分比）。

默认值：16

单位：vp

如果为undefined，则使用默认值。

**类型：** Length

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupSpaceOptions-endSpace?: Length--><!--Device-ChipGroupSpaceOptions-endSpace?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemSpace

```TypeScript
itemSpace?: string | number
```

Chip与Chip之间的间距（不支持百分比）。

取值范围：

number类型: ≥ 0 的数值（如：0、8、16、24.5）。

string类型: 单位为fp|vp|px|lpx且数值部分 ≥ 0 的字符串（如："8vp"、"16fp"、"12px"、"10lpx"）。

不支持: 负数、百分比单位、无效字符串格式。

默认值：8

单位：vp

为undefined时，itemSpace采取默认值。

**类型：** string | number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupSpaceOptions-itemSpace?: string | number--><!--Device-ChipGroupSpaceOptions-itemSpace?: string | number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## startSpace

```TypeScript
startSpace?: Length
```

左侧内边距（不支持百分比）。

默认值：16

单位：vp

为undefined时，startSpace取默认值。

**类型：** Length

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupSpaceOptions-startSpace?: Length--><!--Device-ChipGroupSpaceOptions-startSpace?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

