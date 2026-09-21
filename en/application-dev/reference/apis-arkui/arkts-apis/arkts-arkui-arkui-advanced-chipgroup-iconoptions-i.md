# IconOptions

```TypeScript
export interface IconOptions
```

Defines the common attributes of icons.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { IconOptions, LabelOptions as ChipItemLabelOptions, ChipGroupItemOptions, ChipItemStyle, ChipGroupSpaceOptions, IconItemOptions, IconGroupSuffix, ChipGroup, SuffixImageIconOptions, SymbolItemOptions } from '@kit.ArkUI';
```

## size

```TypeScript
size?: SizeOptions
```

Icon size. Percentages are not supported. Set this parameter when you need to customize the icon size.

Default value:

- When **ChipItemStyle.size** is **ChipSize.SMALL**, the default value is:  
**{width: $r('sys.float.chip_small_icon_size'), height: $r('sys.float.chip_small_icon_size')}**  
- In other cases, the default value is:  
**{width: $r('sys.float.chip_normal_icon_size'), height: $r('sys.float.chip_normal_icon_size')}**

If the value is **undefined**, the default value is used.

**Type:** [SizeOptions](arkts-arkui-sizeoptions-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## src

```TypeScript
src: ResourceStr
```

Icon source, which can be a specific image resource or an image address reference. For details, see [Image](../../../reference/apis-arkui/arkui-ts/ts-basic-components-image.md#image-1).

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
