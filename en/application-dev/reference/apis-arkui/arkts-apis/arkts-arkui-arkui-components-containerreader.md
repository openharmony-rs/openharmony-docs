# @ohos.arkui.components.ContainerReader

## Modules to Import

```TypeScript
import { ContainerReader, ContainerReaderAttribute, BreakpointOptions } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [ContainerReaderAttribute](arkts-arkui-arkui-components-containerreader-containerreaderattribute-c.md) | Defines the ContainerReader attribute functions. Provides methods for configuring container reading parameters and breakpoint analysis properties. |

### Interfaces

| Name | Description |
| --- | --- |
| [BreakpointOptions](arkts-arkui-arkui-components-containerreader-breakpointoptions-i.md) | Defines the breakpoint configuration options for container dimension analysis. Specifies threshold values that trigger different layout behaviors based on container size. |
| [ContainerReaderInfo](arkts-arkui-arkui-components-containerreader-containerreaderinfo-i.md) | Defines the configuration options for ContainerReader component. Used to specify the parameters for container dimension reading and breakpoint analysis. |
| [ContainerReaderInterface](arkts-arkui-arkui-components-containerreader-containerreaderinterface-i.md) | Defines the ContainerReader Component. Used for reading and analyzing container layout information based on size breakpoints in dynamic scenarios. Provides container dimension analysis and breakpoint detection capabilities. |

### Constants

| Name | Description |
| --- | --- |
| [ContainerReader](arkts-arkui-arkui-components-containerreader-con.md) | Defines ContainerReader Component. A component that analyzes container dimensions and provides breakpoint information for responsive layouts. |
| [ContainerReaderInstance](arkts-arkui-arkui-components-containerreader-con.md#containerreaderinstance) | Defines ContainerReader Component instance. Provides access to ContainerReader component methods for container dimension analysis and breakpoint detection. |

## Examples

```TypeScript
### Example 1: Switching Layout Direction Based on ContainerReader Width Breakpoint

This example demonstrates how the [ContainerReader](#containerreader-1) component obtains container size and breakpoint information through two-way binding, and switches the layout direction based on the width breakpoint.

The ContainerReader component is added since API version 26.0.0.
```

```TypeScript
### Example 2: Configuring Custom Breakpoints

This example demonstrates how to customize breakpoint thresholds via [breakpointConfig](arkts-arkui-arkui-components-containerreader-containerreaderattribute-c.md#breakpointconfig) to define various wide and narrow layout sizes, enabling more refined layout control.

The ContainerReader component and the breakpointConfig API are added since API version 26.0.0.

Tap the button to change the width of the parent container, which returns different width breakpoint values, thereby adjusting the layout direction.
```

```TypeScript
### Example 3: Dynamically Adjusting the Number of Columns Using the Width Breakpoint

This example demonstrates how to dynamically adjust the number of columns based on the width breakpoint obtained from ContainerReader, enabling adaptive layouts across multiple devices with varying column counts for different breakpoints.

The ContainerReader component is added since API version 26.0.0.
```
