# PopoverDialogV2

```TypeScript
export declare struct PopoverDialogV2
```

The dialog box is a modal window that commands attention while retaining the current context. It is frequently used to draw the user's attention to vital information or prompt the user to complete a specific task. As all modal windows, this component requires the user to interact before exiting.

This component is implemented based on [state management V2](../../../ui/state-management/arkts-state-management-overview.md#state-management-v2). Compared with [state management V1](../../../ui/state-management/arkts-state-management-overview.md#state-management-v1), V2 offers a higher level of observation and management over data objects beyond the component level. You can now more easily manage dialog box data and states with greater flexibility, leading to faster UI updates.

> **NOTE:** 
> 
> - This component can be used only in the stage model.
> 
> - If the **DialogV2** component has [universal attributes](../arkts-components/arkts-arkui-common-comp.md) and [universal events](../arkts-components/arkts-arkui-common-comp.md) configured, the compiler toolchain automatically generates an additional \_\_Common\_\_ node and mounts the universal attributes and universal events on this node rather than the **DialogV2** component itself. As a result, the configured universal attributes and universal events may fail to take effect or behave as intended. For this reason, avoid using universal attributes and events with the **DialogV2** component.

@struct { PopoverDialogV2 }

**Since:** 18

**Decorator:** @ComponentV2

<!--Device-unnamed-export declare struct PopoverDialogV2--><!--Device-unnamed-export declare struct PopoverDialogV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AlertDialogV2, AdvancedDialogV2Button, AdvancedDialogV2ButtonOptions, AdvancedDialogV2ButtonAction, AdvancedDialogV2OnCheckedChange, ConfirmDialogV2, LoadingDialogV2, SelectDialogV2, TipsDialogV2, CustomContentDialogV2, PopoverDialogV2, PopoverDialogV2OnVisibleChange, PopoverDialogV2Options } from '@kit.ArkUI';
```

## $visible

```TypeScript
$visible?: PopoverDialogV2OnVisibleChange
```

Sets the callback when visibility changed.

**Since:** 18

**Decorator:** @Event

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-PopoverDialogV2-$visible?: PopoverDialogV2OnVisibleChange--><!--Device-PopoverDialogV2-$visible?: PopoverDialogV2OnVisibleChange-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## popover

```TypeScript
popover: PopoverDialogV2Options
```

Sets the PopoverDialogV2 options.

**Type:** [PopoverDialogV2Options](arkts-arkui-arkui-advanced-dialogv2-popoverdialogv2options-i.md)

**Since:** 18

**Decorator:** @Require

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-PopoverDialogV2-popover: PopoverDialogV2Options--><!--Device-PopoverDialogV2-popover: PopoverDialogV2Options-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## targetBuilder

```TypeScript
targetBuilder: CustomBuilder
```

Sets the targetBuilder content.

**Type:** [CustomBuilder](../arkts-components/arkts-arkui-common-comp-custombuilder-t.md)

**Since:** 18

**Decorator:** @BuilderParam

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-PopoverDialogV2-targetBuilder: CustomBuilder--><!--Device-PopoverDialogV2-targetBuilder: CustomBuilder-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## visible

```TypeScript
visible: boolean
```

Sets the PopoverDialogV2 Visible Status.

**Type:** boolean

**Since:** 18

**Decorator:** @Require

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-PopoverDialogV2-visible: boolean--><!--Device-PopoverDialogV2-visible: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
