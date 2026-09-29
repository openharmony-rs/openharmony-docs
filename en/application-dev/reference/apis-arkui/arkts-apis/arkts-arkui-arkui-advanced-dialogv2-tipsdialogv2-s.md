# TipsDialogV2

```TypeScript
export declare struct TipsDialogV2
```

The dialog box is a modal window that commands attention while retaining the current context. It is frequently used to draw the user's attention to vital information or prompt the user to complete a specific task. As all modal windows, this component requires the user to interact before exiting.

This component is implemented based on [state management V2](../../../ui/state-management/arkts-state-management-overview.md#state-management-v2). Compared with [state management V1](../../../ui/state-management/arkts-state-management-overview.md#state-management-v1), V2 offers a higher level of observation and management over data objects beyond the component level. You can now more easily manage dialog box data and states with greater flexibility, leading to faster UI updates.

> **NOTE:** 
> 
> - This component can be used only in the stage model.
> 
> - If the **DialogV2** component has [universal attributes](../arkts-components/arkts-arkui-common-comp.md) and [universal events](../arkts-components/arkts-arkui-common-comp.md) configured, the compiler toolchain automatically generates an additional \_\_Common\_\_ node and mounts the universal attributes and universal events on this node rather than the **DialogV2** component itself. As a result, the configured universal attributes and universal events may fail to take effect or behave as intended. For this reason, avoid using universal attributes and events with the **DialogV2** component.

@struct { TipsDialogV2 }

**Since:** 18

**Decorator:** @ComponentV2

<!--Device-unnamed-export declare struct TipsDialogV2--><!--Device-unnamed-export declare struct TipsDialogV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AlertDialogV2, AdvancedDialogV2Button, AdvancedDialogV2ButtonOptions, AdvancedDialogV2ButtonAction, AdvancedDialogV2OnCheckedChange, ConfirmDialogV2, LoadingDialogV2, SelectDialogV2, TipsDialogV2, CustomContentDialogV2, PopoverDialogV2, PopoverDialogV2OnVisibleChange, PopoverDialogV2Options } from '@kit.ArkUI';
```

## onCheckedChange

```TypeScript
onCheckedChange?: AdvancedDialogV2OnCheckedChange
```

Event triggered when the selected status of the check box changes.

By default, there is no event.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TipsDialogV2-onCheckedChange?: AdvancedDialogV2OnCheckedChange--><!--Device-TipsDialogV2-onCheckedChange?: AdvancedDialogV2OnCheckedChange-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## checked

```TypeScript
checked?: boolean
```

Whether to select the check box.

**true**: The check box is selected. **false**: The check box is not selected.

Default value: **false**.

**Type:** boolean

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TipsDialogV2-checked?: boolean--><!--Device-TipsDialogV2-checked?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## checkTips

```TypeScript
checkTips?: ResourceStr
```

Content of the check box.

It is not displayed by default.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TipsDialogV2-checkTips?: ResourceStr--><!--Device-TipsDialogV2-checkTips?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content?: ResourceStr
```

Content of the dialog box.

It is not displayed by default.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TipsDialogV2-content?: ResourceStr--><!--Device-TipsDialogV2-content?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## imageBorderColor

```TypeScript
imageBorderColor?: ColorMetrics
```

Stroke color of the image.

Default value: **Color.Black**.

**Type:** ColorMetrics

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TipsDialogV2-imageBorderColor?: ColorMetrics--><!--Device-TipsDialogV2-imageBorderColor?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## imageBorderWidth

```TypeScript
imageBorderWidth?: LengthMetrics
```

Stroke width of the image.

By default, there is no stroke effect.

**Type:** LengthMetrics

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TipsDialogV2-imageBorderWidth?: LengthMetrics--><!--Device-TipsDialogV2-imageBorderWidth?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## imageRes

```TypeScript
imageRes: ResourceStr | PixelMap
```

Image to be displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md) &#124; [PixelMap](../arkts-components/arkts-arkui-common-comp-pixelmap-t.md)

**Since:** 18

**Decorator:** @Require

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TipsDialogV2-imageRes: ResourceStr | PixelMap--><!--Device-TipsDialogV2-imageRes: ResourceStr | PixelMap-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## imageSize

```TypeScript
imageSize?: SizeOptions
```

Size of the image.

Default value: **64*64vp**.

**Type:** [SizeOptions](arkts-arkui-sizeoptions-i.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TipsDialogV2-imageSize?: SizeOptions--><!--Device-TipsDialogV2-imageSize?: SizeOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## primaryButton

```TypeScript
primaryButton?: AdvancedDialogV2Button
```

Left button of the dialog box.

It is not displayed by default.

**Type:** [AdvancedDialogV2Button](arkts-arkui-arkui-advanced-dialogv2-advanceddialogv2button-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TipsDialogV2-primaryButton?: AdvancedDialogV2Button--><!--Device-TipsDialogV2-primaryButton?: AdvancedDialogV2Button-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## secondaryButton

```TypeScript
secondaryButton?: AdvancedDialogV2Button
```

Right button of the dialog box.

It is not displayed by default.

**Type:** [AdvancedDialogV2Button](arkts-arkui-arkui-advanced-dialogv2-advanceddialogv2button-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TipsDialogV2-secondaryButton?: AdvancedDialogV2Button--><!--Device-TipsDialogV2-secondaryButton?: AdvancedDialogV2Button-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: ResourceStr
```

Title of the dialog box.

It is not displayed by default.

**NOTE:** 

If the title exceeds two lines, it will be truncated with an ellipsis (...).

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TipsDialogV2-title?: ResourceStr--><!--Device-TipsDialogV2-title?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
