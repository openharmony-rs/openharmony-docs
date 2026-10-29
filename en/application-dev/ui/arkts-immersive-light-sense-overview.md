# Immersive Light Sense Overview
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @H-xinwei-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=3a8b0fe553ae5d0b319caef2cc26c9db6a4714f0 translatedAt=2026-10-12T09:19:33.521Z pushedAt=2026-10-13T07:33:55.809Z -->

Starting from API version 26.0.0, ArkUI introduces Immersive Light Sense.

Immersive Light Sense is a set of experiences provided by ArkUI that spans from the "visual layer" to the "perception layer". It combines light-and-shadow materials with interactive animation effects to help applications establish a clear visual hierarchy and maintain a harmonious and consistent look across different devices. For example, when a user expands a menu, the deformation-based pop-up breaks the rigid regular boundary, and the Edge Light Flow outlines the panel contour, turning the menu pop-up operation into an immersive experience.

<!--Del-->   <!--DelEnd-->

Immersive Light Sense consists of two capabilities: [Immersive System Material](#immersive-system-material) and [Immersive Spatial Animation](#immersive-spatial-animation). The former gives components a light and translucent quality and establishes a clear visual hierarchy above the content, while the latter adds lively and natural dynamic expressions to the pop-up process of dialogs and menus.

Immersive Light Sense adaptively adjusts the degree of expression of the immersive system material and immersive spatial animation based on the device computing power and the Immersive Light Sense effect set by the user in the system. The computing power level is defined by the device and is fixed, and can be queried through the material level API ([uiMaterial.getGlobalMaterialLevel](../reference/apis-arkui/arkts-apis-uimaterial.md)<!--RP1--><!--RP1End-->. The Immersive System Material also automatically switches its effect with the system light/dark mode, ensuring that applications present the best effect in different usage environments.

## Key Technologies

### Immersive System Material

The immersive system material gives components a light and translucent quality: multiple layers of effects, including material filters, refraction, highlights, and shadows, are overlaid so that the underlying content naturally permeates through the material layer, delivering a premium visual presentation far beyond a solid-color background. You only need to [Enable Immersive Light Sense](arkts-immersive-light-sense-enable.md), and the visual effects of the component, such as its background, border, and shadow, are then uniformly managed by the immersive system material, which automatically adapts to the light/dark color mode and the device's computing power.

The immersive system material provides five styles, ranging from ultra-thin to ultra-thick<!--RP2--><!--RP2End-->. After Immersive Light Sense is enabled, the default styles of different components vary.

| Style | Description | Applicable Scenarios |
| --- | --- | --- |
| ULTRA_THIN | Ultra-thin style, with a highly transparent material layer. | Highly transparent backgrounds, such as floating toolbars. |
| THIN | Thin style, with a fairly transparent material layer. | Scenarios with strong transparency, such as search boxes. |
| REGULAR | Regular style, with a normal material layer thickness. | General scenarios. |
| THICK | Thick style, with a strong blur effect. | Scenarios with a strongly blurred background, such as menus. |
| ULTRA_THICK | Ultra-thick style, with a very strong blur effect. | Scenarios with a fully blurred background, such as dialogs. |

In addition, the immersive system material also supports personalized configurations such as automatic color inversion, material tinting, interactive deformation, point light sources, and shadow toggles. For details, please refer to [Immersive System Material Visual Effects](arkts-immersive-light-sense-common-capability.md).

### Immersive Spatial Animation
Immersive spatial animation condenses the behavior of light into three mutually complementary animation types, as shown in the following table. It adapts automatically based on the device's computing power and the immersive light sense effect you configure in the system, so no additional adaptation is required.

| Animation Type | Description | Supported Components |
| --- | --- | --- |
| Nonlinear Deformation | Achieves dynamic transformation of light and shadow forms, breaking regular boundaries to create soft and natural spatial transitions. | AlertDialog. For specific examples, please refer to [Example 9: Setting the Immersive Light Effect of the Dialog Box](../reference/apis-arkui/arkui-ts/ts-methods-alert-dialog-box.md).<br/>CustomDialog. For specific examples, please refer to [Example 14: Setting the System Material of a Dialog box](../reference/apis-arkui/arkui-ts/ts-methods-custom-dialog-box.md#example-14-setting-the-immersive-light-effect-of-a-dialog).<br/>ActionSheet. For specific examples, please refer to [Example 9: Setting the Immersive Light Effect of the Dialog Box](../reference/apis-arkui/arkui-ts/ts-methods-action-sheet.md#example-9-setting-the-immersive-light-effect-for-the-dialog-box).<br/>Menu Control. For specific examples, please refer to [Example 24: Setting the Immersive Light Effect of a Menu](../reference/apis-arkui/arkui-ts/ts-universal-attributes-menu.md). |
| Edge Light Flow | Light flow shapes visual focus and hierarchical order, guiding the user's line of sight along the direction of light flow. | AlertDialog. For specific examples, please refer to [Example 9: Setting the Immersive Light Effect of a Dialog](../reference/apis-arkui/arkui-ts/ts-methods-alert-dialog-box.md).<br/>CustomDialog. For specific examples, please refer to [Example 14: Setting the Immersive Light Effect of a Dialog](../reference/apis-arkui/arkui-ts/ts-methods-custom-dialog-box.md#example-14-setting-the-immersive-light-effect-of-a-dialog).<br/>ActionSheet. For specific examples, please refer to [Example 9: Setting the Immersive Light Effect of the Dialog Box](../reference/apis-arkui/arkui-ts/ts-methods-action-sheet.md#example-9-setting-the-immersive-light-effect-for-the-dialog-box).<br/>Menu Control. For specific examples, please refer to [Example 24: Setting the Immersive Light Effect of a Menu](../reference/apis-arkui/arkui-ts/ts-universal-attributes-menu.md). |
| Particle Animation | Particles carry concrete expression of information, conveying information changes through particle light points. | Slider. For specific examples, please refer to [Example 10: Setting the Immersive Light Effect for the Slider)](../reference/apis-arkui/arkui-ts/ts-basic-components-slider.md). |

## Constraints
For the effective scope of Immersive Light Sense, please refer to [Enable Immersive Light Sense](arkts-immersive-light-sense-enable.md).<br/>
After Immersive Light Sense is enabled,
- The Immersive Light Sense effect of the specified dialog components ([AlertDialog](../reference/apis-arkui/arkui-ts/ts-methods-alert-dialog-box.md), [ActionSheet](../reference/apis-arkui/arkui-ts/ts-methods-action-sheet.md), [CustomDialog](../reference/apis-arkui/arkui-ts/ts-methods-custom-dialog-box.md), [CalendarPickerDialog](../reference/apis-arkui/arkui-ts/ts-methods-calendarpicker-dialog.md), [DatePickerDialog](../reference/apis-arkui/arkui-ts/ts-methods-datepicker-dialog.md), [TimePickerDialog](../reference/apis-arkui/arkui-ts/ts-methods-timepicker-dialog.md), [TextPickerDialog](../reference/apis-arkui/arkui-ts/ts-methods-textpicker-dialog.md), [SelectionMenu](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-SelectionMenu.md), the [AlphabetIndexer](../reference/apis-arkui/arkui-ts/ts-container-alphabet-indexer.md) dialog, and the text menu triggered by long press or double tap after setting [copyOption](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#copyoption9) on [Text](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md)) can take effect on the full page.
- The Immersive Light Sense effect of the specified dialog APIs ([PromptAction](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md), [ArkUI_NativeDialog](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativedialog.md), [@ohos.promptAction (Dialog)](../reference/apis-arkui/js-apis-promptAction.md), [Popup Control](../reference/apis-arkui/arkui-ts/ts-universal-attributes-popup.md), [Tips Control](../reference/apis-arkui/arkui-ts/ts-universal-attributes-tips.md), [Menu Control](../reference/apis-arkui/arkui-ts/ts-universal-attributes-menu.md), and [Sheet Transition](../reference/apis-arkui/arkui-ts/ts-universal-attributes-sheet-transition.md)) can take effect on the full page.
- The Immersive Light Sense effect of [Slider](../reference/apis-arkui/arkui-ts/ts-basic-components-slider.md), [Toggle](../reference/apis-arkui/arkui-ts/ts-basic-components-toggle.md), and [Select](../reference/apis-arkui/arkui-ts/ts-basic-components-select.md) can take effect on the full page.
- Other components take effect only in the Navigation/NavDestination title bar or in the bottom TabBar of horizontal Tabs where `barPosition` is `BarPosition.End`. Setting the Immersive Light Sense effect in other areas does not take effect.

<!--RP3--><!--RP3End-->
