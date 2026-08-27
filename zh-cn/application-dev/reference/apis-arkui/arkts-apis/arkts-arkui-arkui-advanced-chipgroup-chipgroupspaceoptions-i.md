# ChipGroupSpaceOptions

ChipGroupSpaceOptions 定义了ChipGroup左右内边距，以及Chip与Chip之间的间距。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { IconOptions, LabelOptions as ChipItemLabelOptions, ChipGroupItemOptions, ChipItemStyle, ChipGroupSpaceOptions, IconItemOptions, IconGroupSuffix, ChipGroup, SuffixImageIconOptions, SymbolItemOptions } from '@kit.ArkUI';
```

## endSpace

```TypeScript
endSpace?: Length
```

右侧内边距（不支持百分比）。传入负数、百分比或无效字符串格式时，使用默认值。默认值：16单位：vp值为undefined时，按默认值处理。

**类型：** [Length](arkts-arkui-length-t.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemSpace

```TypeScript
itemSpace?: string | number
```

Chip与Chip之间的间距（不支持百分比）。取值范围：number类型：大于等于0的数值（如：0、8、16、24.5）。string类型：单位为fp | vp | px | lpx且数值部分大于等于0的字符串（如："8vp"、"16fp"、"12px"、"10lpx"）。  
**说明：**传入负数、百分比或无效字符串格式时，使用默认值。默认值：8单位：vp值为undefined时，按默认值处理。

**类型：** string \| number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## startSpace

```TypeScript
startSpace?: Length
```

左侧内边距（不支持百分比）。传入负数、百分比或无效字符串格式时，使用默认值。默认值：16单位：vp值为undefined时，按默认值处理。

**类型：** [Length](arkts-arkui-length-t.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
