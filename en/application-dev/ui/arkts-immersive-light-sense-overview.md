# Immersive Light Sense Overview
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @H-xinwei-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=972f1649fdb6ebd99757019463fe43a902cdae45 translatedAt=2026-08-31T03:12:29.580Z pushedAt=2026-09-03T10:04:50.486Z -->


Starting from API version 26.0.0, ArkUI introduces Immersive Light Sense.

Immersive Light Sense is a set of experiences provided by ArkUI that spans from the "visual layer" to the "perception layer". It combines light-and-shadow materials with interactive animation effects to help applications establish a clear visual hierarchy and maintain a harmonious and consistent look across different devices. For example, when a user expands a menu, the deformation-based pop-up breaks the rigid regular boundary, and the Edge Light Flow outlines the panel contour, turning the menu pop-up operation into an immersive experience.

Immersive Light Sense consists of two capabilities:

- **Immersive system material**: Gives components a light and translucent texture, allowing content to naturally permeate through the system material layer. Combined with multi-layer effects such as refraction, highlights, and shadows, it enables floating elements such as dialogs, menus, and toolbars to establish a clear visual hierarchy above the content. The system provides five material styles ranging from ultra-thin to ultra-thick, covering different light-transmission requirements from floating toolbars to dialogs.
- **Immersive spatial animation**: Adds dynamic expressions such as deformation and light flow to the pop-up process of dialogs and menus, making every pop-up lively and natural.

Immersive Light Sense adaptively adjusts the degree of expression of the immersive system material and immersive spatial animation based on the device computing power and the Immersive Light Sense effect set by the user in the system. The computing power level is defined by the device and is fixed, and can be queried through the material level API ([uiMaterial.getGlobalMaterialLevel](../reference/apis-arkui/arkts-apis-uimaterial.md)<!--RP1--><!--RP1End-->. The Immersive System Material also automatically switches its effect with the system light/dark mode, ensuring that applications present the best effect in different usage environments.

<!--Del-->   <!--DelEnd-->

## Key Technologies

### Immersive System Material

The immersive system material gives components a light and translucent quality: multiple layers of effects, including material filters, refraction, highlights, and shadows, are overlaid so that the underlying content naturally permeates through the material layer, delivering a premium visual presentation far beyond that of a solid-color background. You only need to enable Immersive Light Sense, and the visual effects of a component, such as its background, border, and shadow, are then uniformly managed by the immersive system material, which automatically adapts to the light/dark mode and device computing power.

The immersive system material provides five styles, ranging from ultra-thin to ultra-thick<!--RP2--><!--RP2End-->. After Immersive Light Sense is enabled, the default styles of different components vary.

| Style | Description | Applicable Scenarios |
| --- | --- | --- |
| ULTRA_THIN | Ultra-thin style, with a highly transparent material layer. | Highly transparent backgrounds, such as floating toolbars. |
| THIN | Thin style, with a fairly transparent material layer. | Scenarios with strong transparency, such as search boxes. |
| REGULAR | Regular style, with a normal material layer thickness. | General scenarios. |
| THICK | Thick style, with a strong blur effect. | Scenarios with a strongly blurred background, such as menus. |
| ULTRA_THICK | Ultra-thick style, with a very strong blur effect. | Scenarios with a fully blurred background, such as dialogs. |

In addition, the immersive system material supports personalized configurations such as material tinting, automatic color inversion, shadow toggling, interactive deformation, and point light sources.

### Immersive Spatial Animation
Immersive spatial animation condenses the behavior of light into three mutually complementary animation types, as shown in the following table. It adapts automatically based on the device's computing power and the immersive light sense effect you configure in the system, so no additional adaptation is required.

| Animation Type | Description | Supported Components |
| --- | --- | --- |
| Nonlinear Deformation<br/>Edge Light Flow | Nonlinear Deformation: Achieves dynamic transformation of light and shadow forms, breaking regular boundaries to create soft and natural spatial transitions.<br/>Edge Light Flow: The flowing light shapes visual focus and hierarchical order, guiding the user's gaze along the direction of the light flow. | AlertDialog: See [Example 9 (Immersive Light Sense Effect of the Settings Dialog)](../reference/apis-arkui/arkui-ts/ts-methods-alert-dialog-box.md#example-9-setting-the-system-material-of-the-dialog-box)<br/>CustomDialog<br/>ActionSheet<br/>Menu control: See [Example 24: Setting the System Material of a Menu](../reference/apis-arkui/arkui-ts/ts-universal-attributes-menu.md#example-24-setting-the-system-material-of-a-menu) |
| Particle Animation | Particles carry the concrete expression of information, conveying information changes through particle light points. | Slider |

<!--RP3--><!--RP3End-->
