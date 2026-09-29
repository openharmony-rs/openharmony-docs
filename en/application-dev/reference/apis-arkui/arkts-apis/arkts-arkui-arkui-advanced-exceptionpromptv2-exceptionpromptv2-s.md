# ExceptionPromptV2

```TypeScript
export declare struct ExceptionPromptV2
```

The **ExceptionPromptV2** component is used when an exception occurs and the exception content needs to be prompted.

This component is implemented based on [state management V2](../../../ui/state-management/arkts-state-management-overview.md#state-management-v2). Compared with [state management V1](../../../ui/state-management/arkts-state-management-overview.md#state-management-v1), state management V2 delivers enhanced capabilities for deep observation and management of data objects, and is no longer limited to the component level. With state management V2, you can more flexibly control the data and state of the exception prompt through this component, achieving more efficient UI refresh.

> **NOTE:** 
> 
> - This component can only be used in the stage model.
> 
> - If [universal attributes](../arkts-components/arkts-arkui-common-comp.md) and [universal events](../arkts-components/arkts-arkui-common-comp.md) are set for **ExceptionPromptV2**, the compilation toolchain will generate an additional node \_\_Common\_\_ and mount the universal attributes or universal events on \_\_Common\_\_, rather than directly applying them to **ExceptionPromptV2** itself. This may cause the set universal attributes or universal events to not take effect or behave unexpectedly. Therefore, it is not recommended to set universal attributes and universal events on **ExceptionPromptV2**.

**Since:** 26.0.0

**Decorator:** @ComponentV2

<!--Device-unnamed-export declare struct ExceptionPromptV2--><!--Device-unnamed-export declare struct ExceptionPromptV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { MarginTypeV2, PromptOptionsV2, PromptOptionsV2Config, ExceptionPromptV2 } from '@kit.ArkUI';
```

## onActionTextClick

```TypeScript
onActionTextClick?: OnActionTextClickCallback
```

Callback invoked when the right-side icon button is tapped. When not set, no operation is performed.

**Since:** 26.0.0

**Decorator:** @Event

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ExceptionPromptV2-onActionTextClick?: OnActionTextClickCallback--><!--Device-ExceptionPromptV2-onActionTextClick?: OnActionTextClickCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onTipClick

```TypeScript
onTipClick?: OnTipClickCallback
```

Callback invoked when the left-side tip text is tapped. When not set, no operation is performed.

**Since:** 26.0.0

**Decorator:** @Event

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ExceptionPromptV2-onTipClick?: OnTipClickCallback--><!--Device-ExceptionPromptV2-onTipClick?: OnTipClickCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options: PromptOptionsV2
```

Configuration information of the current exception prompt.

**Type:** [PromptOptionsV2](arkts-arkui-arkui-advanced-exceptionpromptv2-promptoptionsv2-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ExceptionPromptV2-options: PromptOptionsV2--><!--Device-ExceptionPromptV2-options: PromptOptionsV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
