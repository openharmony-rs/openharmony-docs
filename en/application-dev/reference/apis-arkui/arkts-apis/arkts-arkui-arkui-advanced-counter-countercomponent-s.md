# CounterComponent

```TypeScript
declare struct CounterComponent
```

The **Counter** component is used for precise numerical value adjustment. It supports four styles: list, compact, inline numeric, and inline date, and is suitable for scenarios such as shopping quantity adjustment, parameter setting, and date selection. It provides flexible style configuration and event callback capabilities.

> **NOTE:** 
> 
> - This component is supported since API version 11. Updates will be marked with a superscript to indicate their earliest API version.
> 
> - The APIs of this module can be used only in the stage model.
> 
> - If the **Counter** component has [universal attributes](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md) and [universal events](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md) set, the compilation toolchain generates an additional node \_\_Common\_\_ and attaches the universal attributes or events to \_\_Common\_\_ instead of directly applying them to the **Counter** component. This may cause the universal attributes or events to not take effect or behave unexpectedly. Therefore, setting universal attributes and events for the **Counter** component is not recommended.

**Since:** 11

**Decorator:** @Component

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { CounterComponent, CounterOptions, CounterType, DateData } from '@kit.ArkUI';
```

## options

```TypeScript
options: CounterOptions
```

Configuration options for the type and style of the **Counter** component, including type (Counter type), **direction** (layout direction), **numberOptions** (list and compact styles), **inlineOptions** (inline number style), and **dateOptions** (inline date style).

**Type:** [CounterOptions](arkts-arkui-arkui-advanced-counter-counteroptions-c.md)

**Since:** 11

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
