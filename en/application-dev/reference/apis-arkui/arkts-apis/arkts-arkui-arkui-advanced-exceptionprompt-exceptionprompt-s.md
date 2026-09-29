# ExceptionPrompt

```TypeScript
export declare struct ExceptionPrompt
```

The exception prompt component is used to show an error message when an error arises.

> **NOTE:** 
> 
> - This component can be used only in the stage model.
> 
> - If the **ExceptionPrompt** component has [universal attributes](../arkts-components/arkts-arkui-common-comp.md) and [universal events](../arkts-components/arkts-arkui-common-comp.md) configured, the compiler toolchain automatically generates an additional \_\_Common\_\_ node and mounts the universal attributes and universal events on this node rather than the **ExceptionPrompt** component itself. As a result, the configured universal attributes and universal events may fail to take effect or behave as intended. For this reason, avoid using universal attributes and events with the **ExceptionPrompt** component.

**Since:** 11

**Decorator:** @Component

<!--Device-unnamed-export declare struct ExceptionPrompt--><!--Device-unnamed-export declare struct ExceptionPrompt-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { MarginType, PromptOptions, ExceptionPrompt } from '@kit.ArkUI';
```

## build

```TypeScript
build(): void
```

The build function is a member function that must return an ArkTS component type (Element) to represent the component to be rendered as a user interface.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ExceptionPrompt-build(): void--><!--Device-ExceptionPrompt-build(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onActionTextClick

```TypeScript
onActionTextClick?: () => void
```

Callback invoked when the icon on the right is clicked. No operation is performed if this parameter is not specified.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ExceptionPrompt-onActionTextClick?: () => void--><!--Device-ExceptionPrompt-onActionTextClick?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onTipClick

```TypeScript
onTipClick?: () => void
```

Callback invoked when the tip text on the left is clicked. No operation is performed if this parameter is not specified.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ExceptionPrompt-onTipClick?: () => void--><!--Device-ExceptionPrompt-onTipClick?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options: PromptOptions
```

Exception prompt configuration.

**Type:** [PromptOptions](arkts-arkui-arkui-advanced-exceptionprompt-promptoptions-i.md)

**Since:** 11

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ExceptionPrompt-options: PromptOptions--><!--Device-ExceptionPrompt-options: PromptOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
