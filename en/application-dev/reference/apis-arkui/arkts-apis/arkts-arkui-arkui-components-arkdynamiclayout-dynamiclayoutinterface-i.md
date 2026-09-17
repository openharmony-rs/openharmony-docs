# DynamicLayoutInterface

Defines the dynamic layout container.

**Since:** 24

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { DynamicLayout, DynamicLayoutAttribute } from '@kit.ArkUI';
```

## [[Call]]

```TypeScript
(algorithm: LayoutAlgorithm): DynamicLayoutAttribute
```

Defines the dynamic layout container.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| algorithm | [LayoutAlgorithm](arkts-arkui-layoutalgorithm-i.md) | Yes | Layout algorithm of the dynamic layout component. If an invalid value is used, the child components are stacked and arranged according to [StackLayoutAlgorithm](../../../reference/apis-arkui/js-apis-arkui-layoutAlgorithm.md#stacklayoutalgorithm). |

**Return value:**

| Type | Description |
| --- | --- |
| [DynamicLayoutAttribute](arkts-arkui-arkui-components-arkdynamiclayout-dynamiclayoutattribute-c.md) |  |
