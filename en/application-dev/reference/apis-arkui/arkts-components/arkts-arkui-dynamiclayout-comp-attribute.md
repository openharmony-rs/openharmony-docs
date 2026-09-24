# DynamicLayout properties/events

```TypeScript
export declare class DynamicLayoutAttribute extends CommonMethod<DynamicLayoutAttribute>
```

The [universal attributes](arkts-arkui-common-comp-commonmethod-c.md) are supported.

> **NOTE:** 
> 
> - When the layout algorithm is [RowLayoutAlgorithm](../arkts-apis/arkts-arkui-layoutalgorithm-rowlayoutalgorithm-c.md) or [ColumnLayoutAlgorithm](../arkts-apis/arkts-arkui-layoutalgorithm-columnlayoutalgorithm-c.md), the flex layout attributes set on child components take effect, while the [layoutGravity](arkts-arkui-common-comp-commonmethod-c.md#layoutgravity) attribute does not.
> 
> - When the layout algorithm is [StackLayoutAlgorithm](../arkts-apis/arkts-arkui-layoutalgorithm-stacklayoutalgorithm-c.md), the [layoutGravity](arkts-arkui-common-comp-commonmethod-c.md#layoutgravity) attribute set on child components takes effect, while the flex layout attributes do not.
> 
> - When the layout algorithm is [CustomLayoutAlgorithm](../arkts-apis/arkts-arkui-layoutalgorithm-customlayoutalgorithm-c.md),the setMeasuredSize method of the **DynamicLayout** component's FrameNode takes precedence over the size settings and border attributes, and the measure and layout methods of the child component's FrameNode take precedence over the ignoreLayoutSafeArea attribute.
> 
> - When the layout algorithm is [GridLayoutAlgorithm](../arkts-apis/arkts-arkui-layoutalgorithm-gridlayoutalgorithm-c.md), the flex layout attributes set on child components do not take effect, the [layoutGravity](arkts-arkui-common-comp-commonmethod-c.md#layoutgravity) attribute does not take effect, and the positions of child components are controlled by the **GridLayoutAlgorithm** parameters.

The [universal events](arkts-arkui-common-comp-commonmethod-c.md) are supported.

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
