# LocalizedSnapshotRegion

```TypeScript
interface LocalizedSnapshotRegion
```

Defines the rectangular region for capturing the component snapshot, with coordinates adjusted based on the layout direction (LTR or RTL).

> **NOTE:** 
> 
> Directly using **componentSnapshot** can lead to the issue of
> [ambiguous UI context](../../../ui/arkts-global-interface.md#ambiguous-ui-context). To avoid this, obtain a
> **UIContext** instance using **getUIContext()**, and then obtain the associated **componentSnapshot** object
> using
> [getComponentSnapshot](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getcomponentsnapshot12).

**Since:** 15

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { componentSnapshot } from '@kit.ArkUI';
```

## bottom

```TypeScript
bottom: number
```

Y-coordinate of the lower right corner of the rectangular region.

Unit: px.

Value range: [0, Component height].

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end: number
```

For LTR layouts: X-coordinate of the lower right corner of the rectangular region.

For RTL layouts: X-coordinate of the lower left corner of the rectangular region.

Unit: px.

Value range: [0, Component width].

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start: number
```

For LTR layouts: X-coordinate of the upper left corner of the rectangular region.

For RTL layouts: X-coordinate of the upper right corner of the rectangular region.

Unit: px.

Value range: [0, Component width].

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## top

```TypeScript
top: number
```

For LTR layouts: Y-coordinate of the upper left corner of the rectangular region.

For RTL layouts: Y-coordinate of the upper right corner of the rectangular region.

Unit: px.

Value range: [0, Component height].

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
