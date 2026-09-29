# SelectDialog

```TypeScript
export declare struct SelectDialog
```

SelectDialog({controller: CustomDialogController, title: ResourceStr, content?: ResourceStr, selectedIndex?: number, confirm?: ButtonOptions, radioContent: Array&lt;SheetInfo&gt;, theme?: Theme | CustomTheme, themeColorMode?: ThemeColorMode})

Displays a dialog box from which the user can select options presented in a list or grid.

**Since:** 10

**Decorator:** @CustomDialog

<!--Device-unnamed-export declare struct SelectDialog--><!--Device-unnamed-export declare struct SelectDialog-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AlertDialog, ButtonOptions, ConfirmDialog, LoadingDialog, SelectDialog, TipsDialog, CustomContentDialog, PopoverDialog, PopoverOptions } from '@kit.ArkUI';
```

## confirm

```TypeScript
confirm?: ButtonOptions
```

Bottom button of the selection dialog box.

When not set by default or set to **undefined**, the bottom button is not displayed.

**Type:** [ButtonOptions](arkts-arkui-arkui-advanced-dialog-buttonoptions-c.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SelectDialog-confirm?: ButtonOptions--><!--Device-SelectDialog-confirm?: ButtonOptions-End-->

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

<!--Device-SelectDialog-content?: ResourceStr--><!--Device-SelectDialog-content?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller: CustomDialogController
```

Controller of the selection dialog box, used to control the show and hide of the dialog box.

**Note:** The **@Require** decorator is not used, and mandatory validation is not performed on the parameter during construction.

**Type:** [CustomDialogController](arkts-arkui-customdialogcontroller-c.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SelectDialog-controller: CustomDialogController--><!--Device-SelectDialog-controller: CustomDialogController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## radioContent

```TypeScript
radioContent: Array<SheetInfo>
```

List of subitems in the dialog box. You can set text and a select callback for each subitem.

**Type:** Array&lt;[SheetInfo](arkts-arkui-sheetinfo-i.md)&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SelectDialog-radioContent: Array<SheetInfo>--><!--Device-SelectDialog-radioContent: Array<SheetInfo>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedIndex

```TypeScript
selectedIndex?: number
```

Index of the selected option in the dialog box.

Value range: an integer no less than -1

The default value is **-1**, indicating that there is no selected option. Values less than -1 are treated as no selected option.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SelectDialog-selectedIndex?: number--><!--Device-SelectDialog-selectedIndex?: number-End-->

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

<!--Device-SelectDialog-theme?: Theme | CustomTheme--><!--Device-SelectDialog-theme?: Theme | CustomTheme-End-->

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

<!--Device-SelectDialog-themeColorMode?: ThemeColorMode--><!--Device-SelectDialog-themeColorMode?: ThemeColorMode-End-->

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

<!--Device-SelectDialog-title: ResourceStr--><!--Device-SelectDialog-title: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
