# ConfirmDialog

```TypeScript
export declare struct ConfirmDialog
```

ConfirmDialog({controller: CustomDialogController, title: ResourceStr, content?: ResourceStr, checkTips?: ResourceStr, isChecked?: boolean, onCheckedChange?: Callback\&lt;boolean&gt;, primaryButton?: ButtonOptions, secondaryButton?: ButtonOptions, theme?: Theme | CustomTheme, themeColorMode?: ThemeColorMode})

Defines a confirmation dialog box used to provide error feedback or prompt information when an operation is not correctly executed (for example, a network error or low battery level) or when an incorrect operation is performed (for example, fingerprint enrollment).

**Since:** 10

**Decorator:** @CustomDialog

<!--Device-unnamed-export declare struct ConfirmDialog--><!--Device-unnamed-export declare struct ConfirmDialog-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AlertDialog, ButtonOptions, ConfirmDialog, LoadingDialog, SelectDialog, TipsDialog, CustomContentDialog, PopoverDialog, PopoverOptions } from '@kit.ArkUI';
```

## checkTips

```TypeScript
checkTips?: ResourceStr
```

Tip content of the checkbox.

When not set by default or set to **undefined**, the tip content of the checkbox is not displayed.

**Note:** When the tip content is not set, the checkbox is also displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ConfirmDialog-checkTips?: ResourceStr--><!--Device-ConfirmDialog-checkTips?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content?: ResourceStr
```

Content of the dialog box.

If this parameter is not set or is set to **undefined**, the content is not displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ConfirmDialog-content?: ResourceStr--><!--Device-ConfirmDialog-content?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller: CustomDialogController
```

Confirmation dialog box controller, used to control the show and hide of the dialog box.

**Note:** When **@Require** is not used, mandatory validation is not performed on the parameter during construction.

**Type:** [CustomDialogController](arkts-arkui-customdialogcontroller-c.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ConfirmDialog-controller: CustomDialogController--><!--Device-ConfirmDialog-controller: CustomDialogController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isChecked

```TypeScript
isChecked?: boolean
```

Whether the checkbox is selected. The value **true** means selected, and **false** means unselected.

Default value: **false**

**Type:** boolean

**Since:** 10

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ConfirmDialog-isChecked?: boolean--><!--Device-ConfirmDialog-isChecked?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onCheckedChange

```TypeScript
onCheckedChange?: Callback<boolean>
```

Callback invoked when the checked state of the checkbox changes. The callback parameter is of the boolean type. The value **true** indicates that the checkbox is checked, and **false** indicates that the checkbox is not checked.

**Type:** Callback&lt;boolean&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ConfirmDialog-onCheckedChange?: Callback<boolean>--><!--Device-ConfirmDialog-onCheckedChange?: Callback<boolean>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## primaryButton

```TypeScript
primaryButton?: ButtonOptions
```

Left button of the dialog box.

If this parameter is not set or is set to **undefined**, the left button is not displayed.

**Type:** [ButtonOptions](arkts-arkui-arkui-advanced-dialog-buttonoptions-c.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ConfirmDialog-primaryButton?: ButtonOptions--><!--Device-ConfirmDialog-primaryButton?: ButtonOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## secondaryButton

```TypeScript
secondaryButton?: ButtonOptions
```

Right button of the dialog box.

If this parameter is not set or is set to **undefined**, the right button is not displayed.

**Type:** [ButtonOptions](arkts-arkui-arkui-advanced-dialog-buttonoptions-c.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ConfirmDialog-secondaryButton?: ButtonOptions--><!--Device-ConfirmDialog-secondaryButton?: ButtonOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## theme

```TypeScript
theme?: Theme | CustomTheme
```

Theme information, which can be a custom theme or a **Theme** instance obtained from **onWillApplyTheme**.

**Type:** [Theme](arkts-arkui-arkui-theme-theme-i.md) &#124; [CustomTheme](arkts-arkui-arkui-theme-customtheme-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ConfirmDialog-theme?: Theme | CustomTheme--><!--Device-ConfirmDialog-theme?: Theme | CustomTheme-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## themeColorMode

```TypeScript
themeColorMode?: ThemeColorMode
```

Theme color mode of the dialog box.

Default value: **ThemeColorMode.SYSTEM**

**Type:** [ThemeColorMode](../arkts-components/arkts-arkui-common-comp-themecolormode-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ConfirmDialog-themeColorMode?: ThemeColorMode--><!--Device-ConfirmDialog-themeColorMode?: ThemeColorMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title: ResourceStr
```

Title of the dialog box.

**NOTE:** 

If the title exceeds two lines, it will be truncated with an ellipsis (...).

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ConfirmDialog-title: ResourceStr--><!--Device-ConfirmDialog-title: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
