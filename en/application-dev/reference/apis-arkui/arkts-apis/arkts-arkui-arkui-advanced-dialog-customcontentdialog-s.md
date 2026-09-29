# CustomContentDialog

```TypeScript
export declare struct CustomContentDialog
```

CustomContentDialog({controller: CustomDialogController, contentBuilder: () =&gt; void, primaryTitle?: ResourceStr, secondaryTitle?: ResourceStr, localizedContentAreaPadding?: LocalizedPadding, contentAreaPadding?: Padding, buttons?: ButtonOptions[], theme?: Theme | CustomTheme, themeColorMode?: ThemeColorMode})

Displays a dialog box that contains custom content and operation area.

> **NOTE:** 
> 
> When the height of the dialog box is insufficient, the area defined by **contentBuilder** will be compressed.
> Global scrolling will be enabled if the compressed area's height falls below 100 vp.
> 
> You must define scrolling of the content area in **CustomContentDialog**. In addition, the custom scrolling of the
> content area must be used in conjunction with the **nestedScroll** property, as in the
> **nestedScroll({ scrollForward: NestedScrollMode.PARALLEL, scrollBackward: NestedScrollMode.PARALLEL })** example.

**Since:** 12

**Decorator:** @CustomDialog

<!--Device-unnamed-export declare struct CustomContentDialog--><!--Device-unnamed-export declare struct CustomContentDialog-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AlertDialog, ButtonOptions, ConfirmDialog, LoadingDialog, SelectDialog, TipsDialog, CustomContentDialog, PopoverDialog, PopoverOptions } from '@kit.ArkUI';
```

## contentBuilder

```TypeScript
contentBuilder: () => void
```

Component builder function used to construct the content area of the dialog box.

**Since:** 12

**Decorator:** @BuilderParam

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CustomContentDialog-contentBuilder: () => void--><!--Device-CustomContentDialog-contentBuilder: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## buttons

```TypeScript
buttons?: ButtonOptions[]
```

Buttons in the operation area of the dialog box. A maximum of four buttons are allowed.

**Type:** [ButtonOptions](arkts-arkui-arkui-advanced-dialog-buttonoptions-c.md)[]

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CustomContentDialog-buttons?: ButtonOptions[]--><!--Device-CustomContentDialog-buttons?: ButtonOptions[]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## contentAreaPadding

```TypeScript
contentAreaPadding?: Padding
```

Padding of the content area of the dialog box. This attribute does not take effect when **localizedContentAreaPadding** is set.

**Type:** Padding

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CustomContentDialog-contentAreaPadding?: Padding--><!--Device-CustomContentDialog-contentAreaPadding?: Padding-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller: CustomDialogController
```

Dialog controller used to control the show and hide of the dialog box.

**Note:** Not decorated by **@Require**, and the parameter is not subject to mandatory validation during construction.

**Type:** [CustomDialogController](arkts-arkui-customdialogcontroller-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CustomContentDialog-controller: CustomDialogController--><!--Device-CustomContentDialog-controller: CustomDialogController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## localizedContentAreaPadding

```TypeScript
localizedContentAreaPadding?: LocalizedPadding
```

Padding of the content area of the dialog box, which supports adaptation based on language direction. When this attribute is set, **contentAreaPadding** does not take effect.

**Type:** [LocalizedPadding](arkts-arkui-localizedpadding-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CustomContentDialog-localizedContentAreaPadding?: LocalizedPadding--><!--Device-CustomContentDialog-localizedContentAreaPadding?: LocalizedPadding-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## primaryTitle

```TypeScript
primaryTitle?: ResourceStr
```

Primary title of the dialog box.

If this parameter is not set or is set to **undefined**, the primary title is not displayed.

**NOTE:** 

If the title exceeds two lines, it will be truncated with an ellipsis (...).

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CustomContentDialog-primaryTitle?: ResourceStr--><!--Device-CustomContentDialog-primaryTitle?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## secondaryTitle

```TypeScript
secondaryTitle?: ResourceStr
```

Secondary title of the dialog box.

If this parameter is not set or is set to **undefined**, the secondary title is not displayed.

**NOTE:** 

If the title exceeds two lines, it will be truncated with an ellipsis (...).

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CustomContentDialog-secondaryTitle?: ResourceStr--><!--Device-CustomContentDialog-secondaryTitle?: ResourceStr-End-->

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

<!--Device-CustomContentDialog-theme?: Theme | CustomTheme--><!--Device-CustomContentDialog-theme?: Theme | CustomTheme-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## themeColorMode

```TypeScript
themeColorMode?: ThemeColorMode
```

Light/dark mode of the custom dialog box.

Default value: **ThemeColorMode.SYSTEM**.

**Type:** [ThemeColorMode](../arkts-components/arkts-arkui-common-comp-themecolormode-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CustomContentDialog-themeColorMode?: ThemeColorMode--><!--Device-CustomContentDialog-themeColorMode?: ThemeColorMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
