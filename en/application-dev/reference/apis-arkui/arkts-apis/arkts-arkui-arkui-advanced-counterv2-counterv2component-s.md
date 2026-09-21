# CounterV2Component

```TypeScript
declare struct CounterV2Component
```

The **CounterV2** component enables precise numeric value adjustment. It provides four types: list, compact, inline number, and inline date, which are applicable to scenarios such as shopping cart quantity adjustment and date selection.

This component is implemented based on [state management V2](../../../ui/state-management/arkts-state-management-overview.md#state-management-v2). Compared with [state management V1](../../../ui/state-management/arkts-state-management-overview.md#state-management-v1), state management V2 delivers enhanced capabilities for deep observation and management of data objects, and is no longer limited to the component level. With state management V2, you can more flexibly control the data and state of **CounterV2** through this component, achieving more efficient UI refresh.

> **NOTE:** 
> 
> - If [universal attributes](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md) and [universal events](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md) are set for **CounterV2**, the compilation toolchain generates an additional node \_\_Common\_\_ and attaches the universal attributes or universal events to \_\_Common\_\_, rather than directly applying them to **CounterV2** itself. This may cause the universal attributes or universal events you set to not take effect or behave unexpectedly. Therefore, setting universal attributes and universal events for **CounterV2** is not recommended.
> 
> - This component API can only be used in the stage model.

Universal attributes are not supported.

Universal events are not supported.

**Since:** 26.0.0

**Decorator:** @ComponentV2

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { CounterV2Component, CounterV2Options, CounterV2DateData, CounterV2Type } from '@kit.ArkUI';
```

## options

```TypeScript
options: CounterV2Options
```

Defines the type and style of the **CounterV2** component.

**Type:** [CounterV2Options](arkts-arkui-arkui-advanced-counterv2-counterv2options-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
