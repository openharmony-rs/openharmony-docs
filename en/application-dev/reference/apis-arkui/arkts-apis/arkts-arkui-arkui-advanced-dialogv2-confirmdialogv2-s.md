# ConfirmDialogV2

```TypeScript
export declare struct ConfirmDialogV2
```

Displays an error dialog box that informs the user of an operational error (for example, a network error or low battery level) or an incorrect operation (for example, fingerprint enrollment).

**Since:** 18

**Decorator:** @ComponentV2

<!--Device-unnamed-export declare struct ConfirmDialogV2--><!--Device-unnamed-export declare struct ConfirmDialogV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AlertDialogV2, AdvancedDialogV2Button, AdvancedDialogV2ButtonOptions, AdvancedDialogV2ButtonAction, AdvancedDialogV2OnCheckedChange, ConfirmDialogV2, LoadingDialogV2, SelectDialogV2, TipsDialogV2, CustomContentDialogV2, PopoverDialogV2, PopoverDialogV2OnVisibleChange, PopoverDialogV2Options } from '@kit.ArkUI';
```

## onCheckedChange

```TypeScript
onCheckedChange?: AdvancedDialogV2OnCheckedChange
```

Sets the ConfirmDialogV2 CheckBox Callback.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ConfirmDialogV2-onCheckedChange?: AdvancedDialogV2OnCheckedChange--><!--Device-ConfirmDialogV2-onCheckedChange?: AdvancedDialogV2OnCheckedChange-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## checked

```TypeScript
checked?: boolean
```

Sets the ConfirmDialogV2 checkbox state.

**Type:** boolean

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ConfirmDialogV2-checked?: boolean--><!--Device-ConfirmDialogV2-checked?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## checkTips

```TypeScript
checkTips?: ResourceStr
```

Sets the ConfirmDialogV2 checkbox tips.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ConfirmDialogV2-checkTips?: ResourceStr--><!--Device-ConfirmDialogV2-checkTips?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content?: ResourceStr
```

Sets the ConfirmDialogV2 content.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ConfirmDialogV2-content?: ResourceStr--><!--Device-ConfirmDialogV2-content?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## primaryButton

```TypeScript
primaryButton?: AdvancedDialogV2Button
```

Sets the ConfirmDialogV2 primary button.

**Type:** [AdvancedDialogV2Button](arkts-arkui-arkui-advanced-dialogv2-advanceddialogv2button-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ConfirmDialogV2-primaryButton?: AdvancedDialogV2Button--><!--Device-ConfirmDialogV2-primaryButton?: AdvancedDialogV2Button-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## secondaryButton

```TypeScript
secondaryButton?: AdvancedDialogV2Button
```

Sets the ConfirmDialogV2 secondary button.

**Type:** [AdvancedDialogV2Button](arkts-arkui-arkui-advanced-dialogv2-advanceddialogv2button-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ConfirmDialogV2-secondaryButton?: AdvancedDialogV2Button--><!--Device-ConfirmDialogV2-secondaryButton?: AdvancedDialogV2Button-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title: ResourceStr
```

Sets the ConfirmDialogV2 title.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Decorator:** @Require

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ConfirmDialogV2-title: ResourceStr--><!--Device-ConfirmDialogV2-title: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
