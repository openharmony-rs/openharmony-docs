# ChipGroupPaddingOptions

ChipGroupPaddingOptions定义了ChipGroup的上下内边距，用于控制其整体高度。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { IconOptions, LabelOptions as ChipItemLabelOptions, ChipGroupItemOptions, ChipItemStyle, ChipGroupSpaceOptions, IconItemOptions, IconGroupSuffix, ChipGroup, SuffixImageIconOptions, SymbolItemOptions } from '@kit.ArkUI';
```

## bottom

```TypeScript
bottom: Length
```

ChipGroup的下方内边距（不支持百分比）。传入负数、百分比或无效字符串格式时，使用默认值。默认值：14单位：vp值为undefined时，按默认值处理。

**类型：** [Length](arkts-arkui-length-t.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## top

```TypeScript
top: Length
```

ChipGroup的上方内边距（不支持百分比）。传入负数、百分比或无效字符串格式时，使用默认值。默认值：14单位：vp值为undefined时，按默认值处理。

**类型：** [Length](arkts-arkui-length-t.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
