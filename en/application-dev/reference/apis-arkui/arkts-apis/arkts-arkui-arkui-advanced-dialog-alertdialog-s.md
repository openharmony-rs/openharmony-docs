# AlertDialog

```TypeScript
export declare struct AlertDialog
```

AlertDialog({controller: CustomDialogController, primaryTitle?: ResourceStr, secondaryTitle?: ResourceStr, content: ResourceStr, primaryButton?: ButtonOptions, secondaryButton?: ButtonOptions, theme?: Theme | CustomTheme, themeColorMode?: ThemeColorMode})

Defines an alert dialog box used to warn the user when triggering an irreversible operation that will have serious consequences (such as deletion, reset, cancel editing, stop, etc.).

**Since:** 10

**Decorator:** @CustomDialog

<!--Device-unnamed-export declare struct AlertDialog--><!--Device-unnamed-export declare struct AlertDialog-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AlertDialog, ButtonOptions, ConfirmDialog, LoadingDialog, SelectDialog, TipsDialog, CustomContentDialog, PopoverDialog, PopoverOptions } from '@kit.ArkUI';
```

## content

```TypeScript
content: ResourceStr
```

Content of the alert dialog box.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AlertDialog-content: ResourceStr--><!--Device-AlertDialog-content: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller: CustomDialogController
```

Alert dialog box controller, used to control the show and hide of the dialog box.

**Note:** The **@Require** decorator is not used, and mandatory validation is not performed during construction.

**Type:** [CustomDialogController](arkts-arkui-customdialogcontroller-c.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AlertDialog-controller: CustomDialogController--><!--Device-AlertDialog-controller: CustomDialogController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## primaryButton

```TypeScript
primaryButton?: ButtonOptions
```

Left button of the alert dialog box.

This parameter is not set or set to **undefined** by default, indicating the left button of the alert dialog box is not displayed.

**Type:** [ButtonOptions](arkts-arkui-arkui-advanced-dialog-buttonoptions-c.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AlertDialog-primaryButton?: ButtonOptions--><!--Device-AlertDialog-primaryButton?: ButtonOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## primaryTitle

```TypeScript
primaryTitle?: ResourceStr
```

Primary title of the alert dialog box.

This parameter is not set or set to **undefined** by default, indicating the primary title of the alert dialog box is not displayed.

**Note:** If the title exceeds two lines, "..." is displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AlertDialog-primaryTitle?: ResourceStr--><!--Device-AlertDialog-primaryTitle?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## secondaryButton

```TypeScript
secondaryButton?: ButtonOptions
```

Right button of the alert dialog box.

This parameter is not set or set to **undefined** by default, indicating the right button of the alert dialog box is not displayed.

**Type:** [ButtonOptions](arkts-arkui-arkui-advanced-dialog-buttonoptions-c.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AlertDialog-secondaryButton?: ButtonOptions--><!--Device-AlertDialog-secondaryButton?: ButtonOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## secondaryTitle

```TypeScript
secondaryTitle?: ResourceStr
```

Secondary title of the alert dialog box.

This parameter is not set or set to **undefined** by default, indicating the secondary title of the alert dialog box is not displayed.

**Note:** If the title exceeds two lines, "..." is displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AlertDialog-secondaryTitle?: ResourceStr--><!--Device-AlertDialog-secondaryTitle?: ResourceStr-End-->

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

<!--Device-AlertDialog-theme?: Theme | CustomTheme--><!--Device-AlertDialog-theme?: Theme | CustomTheme-End-->

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

<!--Device-AlertDialog-themeColorMode?: ThemeColorMode--><!--Device-AlertDialog-themeColorMode?: ThemeColorMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
