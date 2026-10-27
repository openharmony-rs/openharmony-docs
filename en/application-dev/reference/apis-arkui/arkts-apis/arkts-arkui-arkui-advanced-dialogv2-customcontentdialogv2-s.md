# CustomContentDialogV2

```TypeScript
export declare struct CustomContentDialogV2
```

Displays a dialog box that contains custom content and operation area.

**Since:** 18

**Decorator:** @ComponentV2

<!--Device-unnamed-export declare struct CustomContentDialogV2--><!--Device-unnamed-export declare struct CustomContentDialogV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AlertDialogV2, AdvancedDialogV2Button, AdvancedDialogV2ButtonOptions, AdvancedDialogV2ButtonAction, AdvancedDialogV2OnCheckedChange, ConfirmDialogV2, LoadingDialogV2, SelectDialogV2, TipsDialogV2, CustomContentDialogV2, PopoverDialogV2, PopoverDialogV2OnVisibleChange, PopoverDialogV2Options } from '@kit.ArkUI';
```

## buttons

```TypeScript
buttons?: AdvancedDialogV2Button[]
```

Sets the CustomContentDialogV2 buttons.

**Type:** [AdvancedDialogV2Button](arkts-arkui-arkui-advanced-dialogv2-advanceddialogv2button-c.md)[]

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-CustomContentDialogV2-buttons?: AdvancedDialogV2Button[]--><!--Device-CustomContentDialogV2-buttons?: AdvancedDialogV2Button[]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## contentAreaPadding

```TypeScript
contentAreaPadding?: LocalizedPadding
```

Sets the CustomContentDialogV2 content area padding.

**Type:** [LocalizedPadding](arkts-arkui-localizedpadding-i.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-CustomContentDialogV2-contentAreaPadding?: LocalizedPadding--><!--Device-CustomContentDialogV2-contentAreaPadding?: LocalizedPadding-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## contentBuilder

```TypeScript
contentBuilder: CustomBuilder
```

Sets the CustomContentDialogV2 content.

**Type:** [CustomBuilder](../arkts-components/arkts-arkui-common-comp-custombuilder-t.md)

**Since:** 18

**Decorator:** @BuilderParam

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-CustomContentDialogV2-contentBuilder: CustomBuilder--><!--Device-CustomContentDialogV2-contentBuilder: CustomBuilder-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## primaryTitle

```TypeScript
primaryTitle?: ResourceStr
```

Sets the CustomContentDialogV2 title.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-CustomContentDialogV2-primaryTitle?: ResourceStr--><!--Device-CustomContentDialogV2-primaryTitle?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## secondaryTitle

```TypeScript
secondaryTitle?: ResourceStr
```

Sets the CustomContentDialogV2 secondary title.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-CustomContentDialogV2-secondaryTitle?: ResourceStr--><!--Device-CustomContentDialogV2-secondaryTitle?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
