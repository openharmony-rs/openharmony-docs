# TipsDialog

```TypeScript
export declare struct TipsDialog
```

TipsDialog({controller: CustomDialogController, imageRes: ResourceStr | PixelMap, imageSize?: SizeOptions, title?: ResourceStr, content?: ResourceStr, checkTips?: ResourceStr, isChecked?: boolean, checkAction?: (isChecked: boolean) =&gt; void, onCheckedChange?: Callback\&lt;boolean&gt;, primaryButton?: ButtonOptions, secondaryButton?: ButtonOptions, theme?: Theme | CustomTheme, themeColorMode?: ThemeColorMode})

Defines a tip dialog box used to remind users to pay attention to specific matters or perform confirmation operations.

**Since:** 10

**Decorator:** @CustomDialog

<!--Device-unnamed-export declare struct TipsDialog--><!--Device-unnamed-export declare struct TipsDialog-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AlertDialog, ButtonOptions, ConfirmDialog, LoadingDialog, SelectDialog, TipsDialog, CustomContentDialog, PopoverDialog, PopoverOptions } from '@kit.ArkUI';
```

## checkAction

```TypeScript
checkAction?: (isChecked: boolean) => void
```

State change event of the checkbox. When **isChecked** is **true**, the checkbox is selected; when **isChecked** is **false**, the checkbox is unselected.

**Note:** It is recommended to use onCheckedChange&lt;sup&gt;12+&lt;/sup&gt;.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TipsDialog-checkAction?: (isChecked: boolean) => void--><!--Device-TipsDialog-checkAction?: (isChecked: boolean) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isChecked | boolean | Yes |  |

## checkTips

```TypeScript
checkTips?: ResourceStr
```

Content of the check box.

If this parameter is not set or is set to **undefined**, the check box content is not displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TipsDialog-checkTips?: ResourceStr--><!--Device-TipsDialog-checkTips?: ResourceStr-End-->

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

<!--Device-TipsDialog-content?: ResourceStr--><!--Device-TipsDialog-content?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller: CustomDialogController
```

Tip pop-up dialog box controller, used to control the show and hide of the dialog box.

**Note:** The **@Require** decorator is not used, and parameters are not mandatorily validated during construction.

**Type:** [CustomDialogController](arkts-arkui-customdialogcontroller-c.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TipsDialog-controller: CustomDialogController--><!--Device-TipsDialog-controller: CustomDialogController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## imageRes

```TypeScript
imageRes: ResourceStr | PixelMap
```

Image displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md) &#124; [PixelMap](../arkts-components/arkts-arkui-common-comp-pixelmap-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TipsDialog-imageRes: ResourceStr | PixelMap--><!--Device-TipsDialog-imageRes: ResourceStr | PixelMap-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## imageSize

```TypeScript
imageSize?: SizeOptions
```

Image size.

Default value: **64*64vp**

**Type:** [SizeOptions](arkts-arkui-sizeoptions-i.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TipsDialog-imageSize?: SizeOptions--><!--Device-TipsDialog-imageSize?: SizeOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isChecked

```TypeScript
isChecked?: boolean
```

When **isChecked** is **true**, the checkbox is selected; when **isChecked** is **false**, the checkbox is unselected.

Default value: **false**

**Type:** boolean

**Since:** 10

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TipsDialog-isChecked?: boolean--><!--Device-TipsDialog-isChecked?: boolean-End-->

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

<!--Device-TipsDialog-onCheckedChange?: Callback<boolean>--><!--Device-TipsDialog-onCheckedChange?: Callback<boolean>-End-->

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

<!--Device-TipsDialog-primaryButton?: ButtonOptions--><!--Device-TipsDialog-primaryButton?: ButtonOptions-End-->

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

<!--Device-TipsDialog-secondaryButton?: ButtonOptions--><!--Device-TipsDialog-secondaryButton?: ButtonOptions-End-->

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

<!--Device-TipsDialog-theme?: Theme | CustomTheme--><!--Device-TipsDialog-theme?: Theme | CustomTheme-End-->

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

<!--Device-TipsDialog-themeColorMode?: ThemeColorMode--><!--Device-TipsDialog-themeColorMode?: ThemeColorMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: ResourceStr
```

Title of the dialog box.

If this parameter is not set or is set to **undefined**, the title is not displayed.

**NOTE:** 

If the title exceeds two lines, it will be truncated with an ellipsis (...).

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TipsDialog-title?: ResourceStr--><!--Device-TipsDialog-title?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
