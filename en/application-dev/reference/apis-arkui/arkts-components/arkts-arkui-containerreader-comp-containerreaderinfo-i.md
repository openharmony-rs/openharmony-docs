# ContainerReaderInfo

```TypeScript
export interface ContainerReaderInfo
```

Defines the configuration options for the **ContainerReader** component, used to specify parameters for reading container size and obtaining breakpoint values. The component size and breakpoint values cannot be changed through this parameter.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ContainerReader, ContainerReaderAttribute, BreakpointOptions } from '@kit.ArkUI';
```

## heightBreakpoint

```TypeScript
heightBreakpoint?: HeightBreakpoint
```

Height breakpoint of the container, which is the height breakpoint enum value of the **ContainerReader** component under different aspect ratio thresholds.

Note:

This parameter supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md#two-way-binding-between-built-in-component-parameters). After binding, when the component height breakpoint value changes, the bound variable of **heightBreakpoint** automatically updates.

**Type:** [HeightBreakpoint](../arkts-apis/arkts-arkui-heightbreakpoint-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size: Size
```

Size of the **ContainerReader** component, used for layout analysis and breakpoint calculation.

Note:

This parameter supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md#two-way-binding-between-built-in-component-parameters). After binding, when the component size value changes, the bound variable of **size** automatically updates.

**Type:** Size

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## widthBreakpoint

```TypeScript
widthBreakpoint?: WidthBreakpoint
```

Width breakpoint of the container, which is the obtained width breakpoint enum value of the **ContainerReader** component.

Note:

This parameter supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md#two-way-binding-between-built-in-component-parameters). After binding, when the component width breakpoint value changes, the bound variable of **widthBreakpoint** automatically updates.

**Type:** [WidthBreakpoint](../arkts-apis/arkts-arkui-widthbreakpoint-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
