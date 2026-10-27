# AlertDialogV2

```TypeScript
export declare struct AlertDialogV2
```

Displays an alert dialog box to prompt the user to confirm an action that is irreversible and may cause serious consequences, such as deletion, reset, editing cancellation, and stop.

**Since:** 18

**Decorator:** @ComponentV2

<!--Device-unnamed-export declare struct AlertDialogV2--><!--Device-unnamed-export declare struct AlertDialogV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AlertDialogV2, AdvancedDialogV2Button, AdvancedDialogV2ButtonOptions, AdvancedDialogV2ButtonAction, AdvancedDialogV2OnCheckedChange, ConfirmDialogV2, LoadingDialogV2, SelectDialogV2, TipsDialogV2, CustomContentDialogV2, PopoverDialogV2, PopoverDialogV2OnVisibleChange, PopoverDialogV2Options } from '@kit.ArkUI';
```

## content

```TypeScript
content: ResourceStr
```

Sets the AlertDialogV2 content.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Decorator:** @Require

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-AlertDialogV2-content: ResourceStr--><!--Device-AlertDialogV2-content: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## primaryButton

```TypeScript
primaryButton?: AdvancedDialogV2Button
```

Sets the AlertDialogV2 primary button.

**Type:** [AdvancedDialogV2Button](arkts-arkui-arkui-advanced-dialogv2-advanceddialogv2button-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-AlertDialogV2-primaryButton?: AdvancedDialogV2Button--><!--Device-AlertDialogV2-primaryButton?: AdvancedDialogV2Button-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## primaryTitle

```TypeScript
primaryTitle?: ResourceStr
```

Sets the AlertDialogV2 title.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-AlertDialogV2-primaryTitle?: ResourceStr--><!--Device-AlertDialogV2-primaryTitle?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## secondaryButton

```TypeScript
secondaryButton?: AdvancedDialogV2Button
```

Sets the AlertDialogV2 secondary button.

**Type:** [AdvancedDialogV2Button](arkts-arkui-arkui-advanced-dialogv2-advanceddialogv2button-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-AlertDialogV2-secondaryButton?: AdvancedDialogV2Button--><!--Device-AlertDialogV2-secondaryButton?: AdvancedDialogV2Button-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## secondaryTitle

```TypeScript
secondaryTitle?: ResourceStr
```

Sets the AlertDialogV2 secondary title.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-AlertDialogV2-secondaryTitle?: ResourceStr--><!--Device-AlertDialogV2-secondaryTitle?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
