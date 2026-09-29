# LoadingDialog

```TypeScript
export declare struct LoadingDialog
```

LoadingDialog({Controller: CustomDialogController, content?: ResourceStr, theme?: Theme | CustomTheme, themeColorMode?: ThemeColorMode})

Displays a loading dialog box to inform the user of the operation progress.

**Since:** 10

**Decorator:** @CustomDialog

<!--Device-unnamed-export declare struct LoadingDialog--><!--Device-unnamed-export declare struct LoadingDialog-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AlertDialog, ButtonOptions, ConfirmDialog, LoadingDialog, SelectDialog, TipsDialog, CustomContentDialog, PopoverDialog, PopoverOptions } from '@kit.ArkUI';
```

## content

```TypeScript
content?: ResourceStr
```

Content of the loading dialog box.

If this parameter is not set or is set to **undefined**, the content is not displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-LoadingDialog-content?: ResourceStr--><!--Device-LoadingDialog-content?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Controller

```TypeScript
Controller: CustomDialogController
```

Controller of the loading dialog box, used to control the show and hide of the dialog box.

**Note:** The **@Require** decorator is not used, and mandatory validation is not performed during construction.

**Type:** [CustomDialogController](arkts-arkui-customdialogcontroller-c.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-LoadingDialog-Controller: CustomDialogController--><!--Device-LoadingDialog-Controller: CustomDialogController-End-->

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

<!--Device-LoadingDialog-theme?: Theme | CustomTheme--><!--Device-LoadingDialog-theme?: Theme | CustomTheme-End-->

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

<!--Device-LoadingDialog-themeColorMode?: ThemeColorMode--><!--Device-LoadingDialog-themeColorMode?: ThemeColorMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
