# ContainerReaderAttribute

Defines the ContainerReader attribute functions. Provides methods for configuring container reading parameters and breakpoint analysis properties.

**Inheritance/Implementation:** ContainerReaderAttribute extends CommonMethod<ContainerReaderAttribute>

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ContainerReader, ContainerReaderAttribute, BreakpointOptions } from '@kit.ArkUI';
```

## breakpointConfig

```TypeScript
breakpointConfig(value?: BreakpointOptions): ContainerReaderAttribute
```

Sets the breakpoint configuration for container dimension analysis. Defines a set of threshold values that trigger different layout behaviors based on container size.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [BreakpointOptions](arkts-arkui-arkui-components-containerreader-breakpointoptions-i.md) | No | An array of breakpoint values in vp |

**Return value:**

| Type | Description |
| --- | --- |
| [ContainerReaderAttribute](arkts-arkui-arkui-components-containerreader-containerreaderattribute-c.md) |  |
