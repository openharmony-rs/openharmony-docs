# LoadingDialogV2

```TypeScript
export declare struct LoadingDialogV2
```

The dialog box is a modal window that commands attention while retaining the current context. It is frequently used to draw the user's attention to vital information or prompt the user to complete a specific task. As all modal windows, this component requires the user to interact before exiting.

This component is implemented based on [state management V2](../../../ui/state-management/arkts-state-management-overview.md#state-management-v2). Compared with [state management V1](../../../ui/state-management/arkts-state-management-overview.md#state-management-v1), V2 offers a higher level of observation and management over data objects beyond the component level. You can now more easily manage dialog box data and states with greater flexibility, leading to faster UI updates.

> **NOTE:** 
> 
> - This component can be used only in the stage model.
> 
> - If the **DialogV2** component has [universal attributes](../arkts-components/arkts-arkui-common-comp.md) and [universal events](../arkts-components/arkts-arkui-common-comp.md) configured, the compiler toolchain automatically generates an additional \_\_Common\_\_ node and mounts the universal attributes and universal events on this node rather than the **DialogV2** component itself. As a result, the configured universal attributes and universal events may fail to take effect or behave as intended. For this reason, avoid using universal attributes and events with the **DialogV2** component.

@struct { LoadingDialogV2 }

**Since:** 18

**Decorator:** @ComponentV2

<!--Device-unnamed-export declare struct LoadingDialogV2--><!--Device-unnamed-export declare struct LoadingDialogV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AlertDialogV2, AdvancedDialogV2Button, AdvancedDialogV2ButtonOptions, AdvancedDialogV2ButtonAction, AdvancedDialogV2OnCheckedChange, ConfirmDialogV2, LoadingDialogV2, SelectDialogV2, TipsDialogV2, CustomContentDialogV2, PopoverDialogV2, PopoverDialogV2OnVisibleChange, PopoverDialogV2Options } from '@kit.ArkUI';
```

## content

```TypeScript
content?: ResourceStr
```

Sets the LoadingDialogV2 content.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-LoadingDialogV2-content?: ResourceStr--><!--Device-LoadingDialogV2-content?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
