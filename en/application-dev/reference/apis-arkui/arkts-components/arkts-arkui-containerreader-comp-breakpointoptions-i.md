# BreakpointOptions

```TypeScript
export interface BreakpointOptions
```

Defines the breakpoint configuration options, which are used to specify threshold parameters for container size analysis.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ContainerReader, ContainerReaderAttribute, BreakpointOptions } from '@kit.ArkUI';
```

## height

```TypeScript
height?: Array<number>
```

Array of height breakpoint values. The height breakpoint value is the ratio of the component's height to its width. No unit. The array must be monotonically increasing.

Default value: **[0.8, 1.2]**, consistent with the default window height breakpoints.

Note:

A maximum of 3 breakpoints are supported, meaning the maximum array length is 2.

**Type:** Array&lt;number&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Array<number>
```

Array of width breakpoint values. The array must be monotonically increasing.

Default value: **[320, 600, 840, 1440]**, in vp, consistent with the default window width breakpoints.

Note:

A maximum of 5 breakpoints are supported, meaning the maximum array length is 4.

**Type:** Array&lt;number&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
