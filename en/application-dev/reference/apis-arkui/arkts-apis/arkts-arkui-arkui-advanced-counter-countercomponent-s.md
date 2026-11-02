# CounterComponent

```TypeScript
declare struct CounterComponent
```

Creates a **Counter** component instance.

**Since:** 11

**Decorator:** @Component

<!--Device-unnamed-declare struct CounterComponent--><!--Device-unnamed-declare struct CounterComponent-End-->

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

<!--Device-CounterComponent-options: CounterOptions--><!--Device-CounterComponent-options: CounterOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
