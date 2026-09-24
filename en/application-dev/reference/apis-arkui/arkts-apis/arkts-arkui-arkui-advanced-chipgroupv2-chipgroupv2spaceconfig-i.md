# ChipGroupV2SpaceConfig

```TypeScript
export interface ChipGroupV2SpaceConfig
```

Defines the left and right padding of **ChipGroupV2** and the spacing configuration between **ChipV2** components.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ChipGroupV2ItemConfig, ChipGroupV2Item, ChipGroupV2Items, ChipGroupV2ItemStyleConfig, ChipGroupV2ItemStyle, ChipGroupV2SpaceConfig, ChipGroupV2Space, ChipGroupV2IconItemConfig, ChipGroupV2SymbolItemConfig, ChipGroupV2PaddingConfig, ChipGroupV2Padding, ChipGroupV2IconGroupSuffix, ChipGroupV2 } from '@kit.ArkUI';
```

## endSpace

```TypeScript
endSpace?: Length
```

Right padding (percentage not supported).

Default value: **16**

Unit: vp

If the value is **undefined**, the default value is used.

**Type:** [Length](arkts-arkui-length-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemSpace

```TypeScript
itemSpace?: string | number
```

Spacing between **ChipV2** components (percentage not supported).

Value range:

- number type: [0, +∞), for example, 0, 8, 16, 24.5.  
- string type: a string in fp | vp | px | lpx units with a numeric value greater than or equal to 0, for example,  
"8vp", "16fp", "12px", "10lpx".  
- Not supported: negative numbers, percentage units, invalid string formats.

If a value outside the valid range or in an unsupported format is passed, the default value is used.

Default value: **8**

Unit: vp

If the value is undefined, the default value is used.

**Type:** string &#124; number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## startSpace

```TypeScript
startSpace?: Length
```

Left padding (percentage not supported).

Default value: **16**

Unit: vp

If the value is **undefined**, the default value is used.

**Type:** [Length](arkts-arkui-length-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
