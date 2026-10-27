# PlaceholderOptions

```TypeScript
export interface PlaceholderOptions
```

Describes the placeholder to display for an item of a scrollable component while the real item is being created across frames.

**Since:** 26.1.0

<!--Device-unnamed-export interface PlaceholderOptions--><!--Device-unnamed-export interface PlaceholderOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { PlaceholderOptions, PlaceholderProvider, PlaceholderRegister } from '@kit.ArkUI';
```

## id

```TypeScript
id?: string
```

ID of the registered placeholder builder. The registry is obtained per UI instance through [getPlaceholderRegister()](arkts-arkui-arkui-uicontext-uicontext-c.md#getplaceholderregister), and the builder is registered through its **register** method. If **id** is omitted, empty, or not registered, the system default placeholder is used.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-PlaceholderOptions-id?: string--><!--Device-PlaceholderOptions-id?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: SizeOptions
```

Suggested layout size of the placeholder. The real item is re-laid out under the normal layout constraints of the item once it has been created, so a suggested size closer to the real size reduces the visual jump at replacement.

**Type:** [SizeOptions](arkts-arkui-sizeoptions-i.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-PlaceholderOptions-size?: SizeOptions--><!--Device-PlaceholderOptions-size?: SizeOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
