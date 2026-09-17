# DynamicLayoutAttribute

The [universal attributes](../arkts-components/arkts-arkui-commonmethod-c.md) are supported.

> **NOTE:** 
> 
> - When the layout algorithm is [RowLayoutAlgorithm](arkts-arkui-layoutalgorithm-rowlayoutalgorithm-c.md) or [ColumnLayoutAlgorithm](arkts-arkui-layoutalgorithm-columnlayoutalgorithm-c.md),the [Flex layout](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-flex-layout.md) attributes set for child components take effect.
> 
> - When the layout algorithm is [StackLayoutAlgorithm](arkts-arkui-layoutalgorithm-stacklayoutalgorithm-c.md),the [layoutGravity](../arkts-components/arkts-arkui-commonmethod-c.md#layoutgravity) attribute set for child components takes effect.
> 
> - When the layout algorithm is [CustomLayoutAlgorithm](arkts-arkui-layoutalgorithm-customlayoutalgorithm-c.md),the [setMeasuredSize](arkts-arkui-framenode-c.md#setmeasuredsize) method of the [FrameNode](arkts-arkui-framenode-c.md) component of **DynamicLayout** has a higher priority than the sizing and [border styling](../arkts-components/arkts-arkui-commonmethod-c.md#border) attributes. The [measure](arkts-arkui-framenode-c.md#measure) and [layout](arkts-arkui-framenode-c.md#layout) methods of the child component [FrameNode](arkts-arkui-framenode-c.md) have a higher priority than the ignoreLayoutSafeArea attribute.

The [universal events](../../../reference/apis-arkui/arkui-ts/ts-component-general-events.md) are supported.

**Inheritance/Implementation:** DynamicLayoutAttribute extends CommonMethod<DynamicLayoutAttribute>

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { DynamicLayout, DynamicLayoutAttribute } from '@kit.ArkUI';
```
