# LevelOrder

Defines the display order of a dialog box.

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { promptAction, LevelMode, ImmersiveMode, LevelOrder } from '@kit.ArkUI';
```

## clamp

```TypeScript
static clamp(order: number): LevelOrder
```

Creates a dialog box level with the specified order.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| order | number | Yes | Display order of the dialog box. The value range is [-100000.0, +100000.0]. Values outside this range are clamped to the nearest limit. |

**Return value:**

| Type | Description |
| --- | --- |
| [LevelOrder](arkts-arkui-promptaction-levelorder-c.md) | Current instance. |

## getOrder

```TypeScript
getOrder(): number
```

Obtains the display order of this dialog box.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Display order of the dialog box. |
