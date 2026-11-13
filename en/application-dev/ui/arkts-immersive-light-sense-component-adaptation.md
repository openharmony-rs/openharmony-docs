# Adapting Components to Immersive Lighting
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @H-xinwei-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=fdf5215fffd09f20c5f300fc25df95a870931fdd translatedAt=2026-10-28T11:39:45.161Z pushedAt=2026-10-29T08:42:29.431Z nl=1 -->

This document categorizes components into four major scenarios: navigation components, popup components, button and selection components, and other components. It systematically describes how each component enables immersive lighting through the app-level switch and component-level configuration, covering the visual effects, setting methods, and adaptation points of immersive lighting, to help developers quickly complete component adaptation for immersive lighting.

## Navigation Components

Navigation components include the Navigation title bar, bottom tab, and index bar. They are auxiliary elements for page navigation and content positioning, usually fixed at the top or bottom of a page. Immersive lighting gives navigation components a translucent floating quality, allowing the navigation bar to present a light layered effect above scrolling content. The underlying content naturally shows through the material layer, establishing a visual hierarchy between the navigation area and the content. Navigation components typically use a thinner material style (ULTRA_THIN or THIN) to keep the background translucent while avoiding excessive occlusion of content.
  
### Navigation Title Bar

The Navigation title bar supports enabling immersive lighting through application-level enablement and component-level enablement.

Application-level enablement: When the app-level switch is in [ENABLE](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate) mode, immersive lighting is enabled by default for the Navigation title bar, and the immersive system material style defaults to ULTRA_THIN. In non-ENABLE mode, immersive lighting does not take effect.
 
Component-level enablement: The Navigation title bar supports setting the immersive lighting effect through the systemMaterial field in [NavigationTitleOptions](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navigationtitleoptions11).
 
- It is recommended to limit immersive lighting to prominent local areas such as the top title bar, and control the usage area and number of layers. For details, see [Power Consumption Optimization for Immersive Lighting](arkts-immersive-light-sense-constraints.md).
- The scope where immersive lighting takes effect on the title bar is: the back key and non-custom Menu.
- When systemMaterial is undefined, if the [MaterialState](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate) switch is configured as DEFAULT, the title bar has no material effect; if it is configured as ENABLE, the title bar takes effect with the system default immersive material effect.
- When setting immersive lighting, it is recommended to use [barStyle](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navigationtitleoptions11) as STACK so that the Navigation content area extends to the title bar area, achieving the best immersive lighting experience.
 
For the effect of enabling immersive lighting on the component, see [Example 20: Setting systemMaterial to Enable the Material Effect for the Title Bar](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#example-20-setting-systemmaterial-to-enable-the-material-effect-for-the-title-bar).
 
### Bottom Tab (Tabs)

The bottom tab supports enabling immersive lighting through application-level enablement and component-level enablement.

Application-level enablement: When the app-level switch is in [ENABLE](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate) mode, the bottom tab does not enable immersive lighting by default. When the [barFloatingStyle](../reference/apis-arkui/arkui-ts/ts-container-tabs.md#barfloatingstyle) attribute is set and the floating style of the bottom tab takes effect, the bottom tab enables immersive lighting by default, and the immersive system material style defaults to THIN.
 
Component-level enablement: The bottom tab supports setting the immersive lighting effect of the TabBar backplane through the systemMaterial field of [FloatingTabBarStyle](../reference/apis-arkui/arkui-ts/ts-container-tabs.md#floatingtabbarstyle) in the [barFloatingStyle](../reference/apis-arkui/arkui-ts/ts-container-tabs.md#barfloatingstyle) attribute.
 
- The floating style takes effect only when [barOverlap](../reference/apis-arkui/arkui-ts/ts-container-tabs.md#baroverlap10) is true, [vertical](../reference/apis-arkui/arkui-ts/ts-container-tabs.md#vertical) is false, and [barPosition](../reference/apis-arkui/arkui-ts/ts-container-tabs.md#barposition9) is BarPosition.End. All three conditions must be met simultaneously; otherwise, the systemMaterial setting does not take effect.
- After the floating material is set, it is not recommended to set the background color or background blur for the TabBar through [barBackgroundColor](../reference/apis-arkui/arkui-ts/ts-container-tabs.md#barbackgroundcolor10) or [barBackgroundBlurStyle](../reference/apis-arkui/arkui-ts/ts-container-tabs.md#barbackgroundblurstyle11), to avoid obscuring the material effect.
- TabContent does not support setting immersive lighting.
 
For the effect of enabling immersive lighting for the component, see [Example 24 Setting the TabBar Floating Style](../reference/apis-arkui/arkui-ts/ts-container-tabs.md#example-24-setting-the-tabbar-floating-style).

### AlphabetIndexer

The AlphabetIndexer prompt popup supports enabling immersive lighting through application-level enablement and component-level enablement.

Application-level enablement: When the app-level switch is in [ENABLE](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate) mode, immersive lighting is enabled by default for the AlphabetIndexer prompt popup, and the immersive system material style defaults to THICK.
 
Component-level enablement: When neither the [popupBackground](../reference/apis-arkui/arkui-ts/ts-container-alphabet-indexer.md#popupbackground) nor the [popupBackgroundBlurStyle](../reference/apis-arkui/arkui-ts/ts-container-alphabet-indexer.md#popupbackgroundblurstyle12) parameter of AlphabetIndexer is actively set (or the parameter value is passed as undefined), immersive lighting is enabled by default for the prompt popup, and the default material style is THICK.
 
- On high-computing-power and medium-computing-power devices, the immersive lighting THICK style is displayed by default. On low-computing-power devices, the immersive lighting effect is not displayed, and a white background is shown instead.
- The popupBackground and popupBackgroundBlurStyle attributes are mutually exclusive with the immersive lighting capability. After popupBackground or popupBackgroundBlurStyle is actively set, no immersive lighting effect is generated.

For the effect of enabling immersive lighting for the component, see [Example 4: Setting the Immersive Lighting Effect of the Dialog](../reference/apis-arkui/arkui-ts/ts-container-alphabet-indexer.md).

## Popup Components

Popup components include Toast, Popup, Tips, Menu, and Dialog (including AlertDialog, CustomDialog, and various PickerDialog types). These components are floating-layer elements that establish a visual hierarchy above the content. The immersive system material gives the popup background a light and translucent texture, allowing the underlying content to naturally show through the material layer. Combined with multi-layer effects such as refraction, highlights, and shadows, it establishes a clear visual hierarchy for the popup above the content. The immersive spatial motion adds dynamic expressions such as deformation and flowing light to the popup and menu emergence process, making the emergence process lively and natural. Popup components typically use thicker material styles (THICK or ULTRA_THICK) to achieve a stronger background blur effect, ensuring clear visual separation between the popup content and the background content. After immersive lighting is enabled, custom style attributes such as the actively set background color and background blur do not take effect.

### Toast

Toast supports enabling immersive lighting through application-level and component-level enablement.

Application-level enablement: When the app-level switch is in [ENABLE](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate) mode, immersive lighting is enabled by default for Toast, and the immersive system material style defaults to THICK.

Component-level enablement: Toast supports setting the immersive lighting effect through the systemMaterial field in [ShowToastOptions](../reference/apis-arkui/js-apis-promptAction.md#showtoastoptions). If custom style attributes such as the background color and background blur are not actively set and the systemMaterial field is not set, the immersive system material style ImmersiveStyle of the popup defaults to ImmersiveStyle.THICK.

For the effect of enabling immersive lighting for the component, see [showToast](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#showtoast).

### Popup and Tips

Popup and Tips support enabling immersive lighting through component-level enablement.

Application-level enablement: When the app-level switch is in [ENABLE](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate) mode, the popup does not enable immersive lighting by default.

Component-level enablement: The popup supports setting the immersive lighting effect through the systemMaterial field in [PopupOptions](../reference/apis-arkui/arkui-ts/ts-universal-attributes-popup.md#popupoptions); the floating tip is set through the systemMaterial field in [TipsOptions](../reference/apis-arkui/arkui-ts/ts-universal-attributes-tips.md#tipsoptions).

For the effect of enabling immersive lighting on the component, see [Example 9: Setting the System Material Effect of a Popup](../reference/apis-arkui/arkui-ts/ts-universal-attributes-popup.md#example-9-setting-the-system-material-effect-of-a-popup) and [Example 3: Setting the Immersive Light-Sensing Visual Effect of a Floating Bubble](../reference/apis-arkui/arkui-ts/ts-universal-attributes-tips.md#example-3-setting-the-immersive-light-sensing-visual-effect-of-a-floating-bubble).

### Menu

The menu supports enabling immersive lighting through application-level enablement and component-level enablement.

Application-level enablement: When the app-level switch is in [ENABLE](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate) mode, immersive lighting is enabled by default for the menu, and the immersive system material style takes the default value THICK.

Component-level enablement: The menu supports setting the immersive lighting effect through the systemMaterial field in [ContextMenuOptions](../reference/apis-arkui/arkui-ts/ts-universal-attributes-menu.md#contextmenuoptions10).

For the effect of enabling immersive lighting for the component, see [Example 24: Setting the System Material of a Menu](../reference/apis-arkui/arkui-ts/ts-universal-attributes-menu.md#example-24-setting-the-system-material-of-a-menu).

### Dialog

The dialog box supports enabling immersive lighting through application-level and component-level enablement.

Application-level enablement: When the app-level switch is in [ENABLE](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate) mode, immersive lighting is enabled by default for the dialog box, and the immersive system material style defaults to ULTRA_THICK.

Component-level enablement: The dialog box supports setting the immersive lighting effect through the systemMaterial field in the dialog box options parameter, such as [CustomDialogControllerOptions](../reference/apis-arkui/arkui-ts/ts-methods-custom-dialog-box.md#customdialogcontrolleroptions), [AlertDialogParam](../reference/apis-arkui/arkui-ts/ts-methods-alert-dialog-box.md#alertdialogparam), and [ActionSheetOptions](../reference/apis-arkui/arkui-ts/ts-methods-action-sheet.md#actionsheetoptions). If no custom style attributes such as background color or background blur are set and the systemMaterial field is not set, the immersive system material style ImmersiveStyle of the dialog box defaults to ImmersiveStyle.ULTRA_THICK.

- Enabling the immersive lighting effect on a large-area dialog box brings more animation rendering overhead, so it is not recommended. For details, see the size recommendations in [Controlling Dialog Size](arkts-immersive-light-sense-constraints.md#controlling-dialog-size).
- The popup opened by the [CalendarPicker](../reference/apis-arkui/arkui-ts/ts-basic-components-calendarpicker.md) component currently does not support enabling the immersive lighting effect. The immersive lighting effect set through universal attributes is reflected on the CalendarPicker component itself.
- The immersive lighting effect of the [CalendarPickerDialog](../reference/apis-arkui/arkui-ts/ts-methods-calendarpicker-dialog.md), [DatePickerDialog](../reference/apis-arkui/arkui-ts/ts-methods-datepicker-dialog.md), [TextPickerDialog](../reference/apis-arkui/arkui-ts/ts-methods-textpicker-dialog.md), and [TimePickerDialog](../reference/apis-arkui/arkui-ts/ts-methods-timepicker-dialog.md) components is the same as that of CustomDialog.

For the effect of enabling immersive lighting on the component, see [Example 9: Setting the System Material of the Dialog Box](../reference/apis-arkui/arkui-ts/ts-methods-alert-dialog-box.md#example-9-setting-the-system-material-of-the-dialog-box), [Example 14: Setting the System Material of a Dialog box](../reference/apis-arkui/arkui-ts/ts-methods-custom-dialog-box.md#example-14-setting-the-system-material-of-a-dialog-box), and [Example 9: Setting the System Material of the Dialog Box](../reference/apis-arkui/arkui-ts/ts-methods-action-sheet.md#example-9-setting-the-system-material-of-the-dialog-box).

### Half-modal (bindSheet)

The bindSheet half-modal transition supports enabling immersive lighting only through component-level enablement.

Application-level enablement: When the app-level switch is in [ENABLE](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate) mode, the bindSheet half-modal transition does not enable immersive lighting by default.

Component-level enablement: bindSheet supports setting the immersive lighting effect through the systemMaterial field in [SheetOptions](../reference/apis-arkui/arkui-ts/ts-universal-attributes-sheet-transition.md#sheetoptions). The default value of systemMaterial is undefined, which means there is no default immersive lighting effect; it takes effect only after being explicitly set. After systemMaterial is set, the affected attributes such as background color [backgroundColor](../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundcolor), border color [borderColor](../reference/apis-arkui/arkui-ts/ts-universal-attributes-border.md#bordercolor), border width [borderWidth](../reference/apis-arkui/arkui-ts/ts-universal-attributes-border.md#borderwidth), and shadow [shadow](../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#shadow) no longer take effect, and it is not recommended to use them together with the preceding attributes.

For the effect of enabling immersive lighting for the component, see [Example 10: Setting the System Material for a Half-Modal](../reference/apis-arkui/arkui-ts/ts-universal-attributes-sheet-transition.md#example-10-setting-the-system-material-for-a-half-modal).

## Button and Selection Components

Button and selection components include Button, Select, Toggle, Slider, ChipGroup/ChipGroupV2, and SegmentButton/SegmentButtonV2. They are interactive elements embedded in the content flow through which users make selections and perform operations. Immersive lighting provides selection components with delicate interactive feedback and a transparent visual texture: immersive system material typically uses a thinner material style (ULTRA_THIN or THIN). While keeping the component background transparent, it uses the interactive deformation (interactive) and light sensing interaction feedback (lightEffect) in [ImmersiveOptions](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions) to provide lively visual feedback for operations such as pressing and touching, replacing the component's default pressed state and hover state effects.

### Button

The button supports enabling immersive lighting through component-level enablement.

Application-level enablement: When the app-level switch is in [ENABLE](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate) mode, the button does not enable immersive lighting by default.

Component-level enablement: The button supports setting the immersive lighting effect for the [Button](../reference/apis-arkui/arkui-ts/ts-basic-components-button.md) component through the [systemMaterial](../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#systemmaterial) attribute.

- The immersive lighting effect of this component takes effect only in the Navigation/NavDestination title bar or in the bottom TabBar of horizontal Tabs where `barPosition` is `BarPosition.End`. Setting the immersive lighting effect in other areas does not take effect.
- When the material style is THIN or ULTRA_THIN, [fontColor](../reference/apis-arkui/arkui-ts/ts-basic-components-button.md#fontcolor) uses the system-predefined reversible color resource and can automatically reverse color along with the material.
- When immersive lighting enables the light sensing interaction feedback effect ([lightEffect](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions)), the default pressed-state and hover-state visual feedback of the button is no longer displayed and is replaced by the light sensing interaction feedback effect of the material.
- When immersive lighting is configured but color-related attributes such as [buttonStyle](../reference/apis-arkui/arkui-ts/ts-basic-components-button.md#buttonstyle11) and [backgroundColor](../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundcolor) are not set, and the material color is not set, the material style of the Button theme color takes effect by default.

For the effect of enabling immersive lighting for the component, see [Example 9: Setting the Immersive Light Effect for a Button](../reference/apis-arkui/arkui-ts/ts-basic-components-button.md#example-9-setting-the-immersive-light-effect-for-a-button).

### Dropdown Button (Select)

The dropdown button supports enabling immersive lighting through application-level enablement and component-level enablement.

Application-level enablement: When the app-level switch is in [ENABLE](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate) mode, the dropdown button and the dropdown menu enable immersive lighting by default. The immersive system material style of the dropdown button defaults to ULTRA_THIN, and interactive deformation ([interactive](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions)) and light sensing interaction feedback ([lightEffect](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions)) are enabled by default. The immersive system material style of the dropdown menu defaults to THICK.

Component-level enablement: The dropdown button supports setting the immersive lighting effect through the [systemMaterial](../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#systemmaterial) attribute. The dropdown menu sets the immersive lighting effect through the independent [menuSystemMaterial](../reference/apis-arkui/arkui-ts/ts-basic-components-select.md#menusystemmaterial) API.

- The immersive lighting of the dropdown button and the dropdown menu are independent of each other and can be enabled or disabled separately. To disable immersive lighting separately, set [uiMaterial.Material.empty](../reference/apis-arkui/arkts-apis-uimaterial.md#empty) instead of setting systemMaterial to undefined.
- When the immersive lighting of the dropdown button enables the light sensing interaction feedback effect ([lightEffect](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions)), the default pressed-state and hover-state visual feedback of the dropdown button is no longer displayed and is replaced by the light sensing interaction feedback effect of the material.

For the effect of enabling immersive lighting for the component, see [Example 11: Setting the Immersive Light Effect for the Select Component and Drop-Down Menu](../reference/apis-arkui/arkui-ts/ts-basic-components-select.md#example-11-setting-the-immersive-light-effect-for-the-select-component-and-drop-down-menu).

### Toggle

Toggle supports enabling immersive lighting through application-level enablement and component-level enablement.

Application-level enablement: When the app-level switch is in [ENABLE](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate) mode, Toggle has immersive lighting enabled by default.

Component-level enablement: Toggle supports setting the immersive lighting effect through the [systemMaterial](../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#systemmaterial) attribute.

- The immersive lighting effect varies with different [ToggleType](../reference/apis-arkui/arkui-ts/ts-basic-components-toggle.md#toggletype) values:
  - ToggleType.Checkbox: This type is not yet adapted to the immersive lighting effect, so no immersive lighting effect is produced after setting.
  - ToggleType.Switch: The material parameters passed in serve only as a switch marker for enabling immersive lighting and do not affect the actual visual effect. The component's internal preset visual parameters are used, mainly affecting the slider size, slider style, shadow, and so on. The material effect varies with the device's computing power tier.
  - ToggleType.Button: The effect is the same as that of setting immersive lighting on the [Button](../reference/apis-arkui/arkui-ts/ts-basic-components-button.md) component, mainly affecting visual attributes such as background color, border, and shadow.

For the effect of enabling immersive lighting on the component, see [Example 4: Implementing the Immersive Light Effect for the Toggle Component](../reference/apis-arkui/arkui-ts/ts-basic-components-toggle.md#example-4-implementing-the-immersive-light-effect-for-the-toggle-component).

### Slider

The slider supports enabling immersive lighting through application-level enablement and component-level enablement.

Application-level enablement: When the app-level switch is in [ENABLE](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate) mode, immersive lighting is enabled by default for the slider.

Component-level enablement: The slider supports setting the immersive lighting effect through the [systemMaterial](../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#systemmaterial) attribute.

- The material parameter passed in serves only as a switch marker for enabling immersive lighting and does not affect the actual visual effect. The component uses its internal preset visual parameters, which mainly affect the slider size, slider style, and shadow. When undefined is passed in, immersive lighting does not take effect, and the original Slider style is restored.
- The interactive feedback effect of immersive lighting takes effect only when the slider block shape is [SliderBlockType](../reference/apis-arkui/arkui-ts/ts-basic-components-slider.md#sliderblocktype10).DEFAULT and [SliderStyle](../reference/apis-arkui/arkui-ts/ts-basic-components-slider.md#sliderstyle) is not NONE.

For the effect of enabling immersive lighting for the component, see [Example 10: Setting the Immersive Light Effect for the Slider](../reference/apis-arkui/arkui-ts/ts-basic-components-slider.md#example-10-setting-the-immersive-light-effect-for-the-slider).

### Sub Tab (ChipGroup/ChipGroupV2)

The sub tab supports enabling immersive lighting through application-level enablement and component-level enablement.

Application-level enablement: When the app-level switch is in [ENABLE](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate) mode, immersive lighting is enabled by default for the sub tab, and the immersive system material style defaults to ULTRA_THIN.
 
Component-level enablement: The sub tab supports setting the immersive lighting effect through the backgroundSystemMaterial, selectedBackgroundSystemMaterial (selected state), and iconBackgroundSystemMaterial (icon) fields of [ChipGroup](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-ChipGroup.md) and [ChipGroupV2](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-ChipGroupV2.md).

- The immersive lighting effect of this component takes effect only in the Navigation/NavDestination title bar or in the bottom TabBar of horizontal Tabs where `barPosition` is `BarPosition.End`. Setting the immersive lighting effect in other areas does not take effect.
- When the text and icon colors need to be automatically inverted along with the material, use the system-predefined invertible color resources (such as `$r('sys.color.font_primary')`). Hard-coded color values do not trigger automatic color inversion. For details, see [Setting Color Inversion for Immersive System Material](arkts-immersive-light-sense-common-capability.md#setting-color-inversion-for-immersive-system-material).
 
For the effect of enabling immersive lighting for the component, see [Example 6: Setting System Material Style](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-ChipGroup.md#example-6-setting-system-material-style) and [Example 7: Setting the System Material Style for the Selected State of a Component](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-ChipGroup.md#example-7-setting-the-system-material-style-for-the-selected-state-of-a-component).
 
### Segmented Button (SegmentButton/SegmentButtonV2)

The segmented button supports enabling immersive lighting through application-level enablement and component-level enablement.

Application-level enablement: When the app-level switch is in [ENABLE](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate) mode, immersive lighting is enabled by default for the segmented button, and the immersive system material style defaults to THIN.
 
Component-level enablement: [SegmentButton](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-SegmentButton.md) supports setting the immersive lighting effect through the `backgroundSystemMaterial` field in `SegmentButtonOptions`; [SegmentButtonV2](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-SegmentButtonV2.md) sets it through the `backgroundSystemMaterial` field in the `options` parameter of each type of segmented button.
 
- The immersive lighting effect of this component takes effect only in the Navigation/NavDestination title bar or in the bottom TabBar of horizontal Tabs where `barPosition` is `BarPosition.End`. Setting the immersive lighting effect in other areas does not take effect.
- The capsule-type multi-select segmented button of SegmentButton (where `type` of [SegmentButtonOptions](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-SegmentButton.md#segmentbuttonoptions) is "capsule" and `multiply` of [SegmentButtonOptions](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-SegmentButton.md#segmentbuttonoptions) is true) does not support `backgroundSystemMaterial`, and the setting does not take effect. MultiCapsuleSegmentButtonV2 does not support immersive lighting.
- After immersive lighting is enabled for the segmented button, the selected item background supports following finger dragging; otherwise, it does not support following finger dragging.
- When automatic color inversion is set, that is, when `colorInvert` is true, if `fontColor` and `selectedFontColor` in SegmentButton, or `itemFontColor`, `itemSelectedFontColor`, `itemIconFillColor`, and `itemSelectedIconFillColor` in SegmentButtonV2, use system resources that support color inversion, the colors are automatically adapted to the inverted color of the material background color.
 
For the effect of enabling immersive lighting for the component, see [Example 8: Setting the Background Material](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-SegmentButton.md#example-8-setting-the-background-material) and [Example 6: Setting the Background Material](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-SegmentButtonV2.md#example-6-setting-the-background-material).

## Other Components

Other components all support the universal attribute [systemMaterial](../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#systemmaterial) to set the immersive system material, and the effect follows the effective rules of the universal attribute, for example, [layout containers](arkts-layout-development-overview.md) and [scroll containers](arkts-list-grid-development-overview.md). The effective area is the Navigation/NavDestination title bar, or the bottom TabBar whose barPosition is BarPosition.End in a horizontal Tabs. For common issues after enablement, see [Immersive Lighting FAQs](arkts-immersive-light-sense-faq.md).