# IconOptions

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

Icon size. This parameter cannot be set in percentage.

Default value: **undefined**

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
