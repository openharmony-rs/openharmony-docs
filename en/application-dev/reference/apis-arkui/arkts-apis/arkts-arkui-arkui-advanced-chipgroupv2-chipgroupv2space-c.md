# ChipGroupV2Space

```TypeScript
export declare class ChipGroupV2Space
```

Defines the left and right padding of **ChipGroupV2** and the spacing between **ChipV2** components.

**Since:** 26.0.0

**Decorator:** @ObservedV2

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ChipGroupV2ItemConfig, ChipGroupV2Item, ChipGroupV2Items, ChipGroupV2ItemStyleConfig, ChipGroupV2ItemStyle, ChipGroupV2SpaceConfig, ChipGroupV2Space, ChipGroupV2IconItemConfig, ChipGroupV2SymbolItemConfig, ChipGroupV2PaddingConfig, ChipGroupV2Padding, ChipGroupV2IconGroupSuffix, ChipGroupV2 } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(config: ChipGroupV2SpaceConfig)
```

A constructor used to create a **ChipGroupV2Space** object.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [ChipGroupV2SpaceConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2spaceconfig-i.md) | Yes | Spacing configuration of **ChipGroupV2**. |

## endSpace

```TypeScript
public endSpace?: Length
```

Right padding (percentage not supported).

Default value: **16**

Unit: vp

If the value is **undefined**, the default value is used.

Decorator: **@Trace**

**Type:** [Length](arkts-arkui-length-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemSpace

```TypeScript
public itemSpace?: string | number
```

Spacing between **ChipV2** components (percentage not supported). Increasing the spacing makes adjacent **ChipV2** components more dispersed and the overall layout looser; decreasing the spacing makes **ChipV2** components more compact.

Value range:

- number type: [0, +∞), for example, 0, 8, 16, 24.5.  
- string type: a string in fp | vp | px | lpx units with a numeric value greater than or equal to 0, for example,  
"8vp", "16fp", "12px", "10lpx".  
- Not supported: negative numbers, percentage units, invalid string formats.

If a value outside the valid range or in an unsupported format is passed, the default value is used.

Default value: **8**

Unit: vp

If the value is **undefined**, the default value is used.

Decorator: **@Trace**

**Type:** string &#124; number

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## startSpace

```TypeScript
public startSpace?: Length
```

Left padding (percentage not supported).

Default value: **16**

Unit: vp

If the value is **undefined**, the default value is used.

Decorator: **@Trace**

**Type:** [Length](arkts-arkui-length-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
