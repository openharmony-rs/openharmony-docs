# ContainerReader properties/events

```TypeScript
export declare class ContainerReaderAttribute extends CommonMethod<ContainerReaderAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp-commonmethod-c.md), the following attributes are supported:

[Universal events](arkts-arkui-common-comp-commonmethod-c.md) are supported.

**Inheritance/Implementation:** ContainerReaderAttribute extends CommonMethod<ContainerReaderAttribute>

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ContainerReader, ContainerReaderAttribute, BreakpointOptions } from '@kit.ArkUI';
```

## breakpointConfig

```TypeScript
breakpointConfig(value?: BreakpointOptions)
```

Sets the breakpoint configuration options, defining the size thresholds that trigger different layout behaviors.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [BreakpointOptions](arkts-arkui-containerreader-comp-breakpointoptions-i.md) | No | Breakpoint configuration options, containing arrays of width and height breakpoint thresholds. |
