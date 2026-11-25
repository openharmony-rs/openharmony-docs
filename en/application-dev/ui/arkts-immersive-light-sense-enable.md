# Enabling Immersive Lighting
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @H-xinwei-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=c1e3d900aa15d11707edd8e176650820d7bf9b3d translatedAt=2026-10-28T11:40:46.795Z pushedAt=2026-10-29T08:35:49.273Z nl=1 -->

Immersive lighting can be enabled at application or component level, which you can select as needed. After immersive lighting is enabled, it consumes a large amount of GPU resources. For specific adaptation guidance, see [Power Consumption Optimization for Immersive Lighting](arkts-immersive-light-sense-constraints.md). For other common issues after enablement, see [FAQs About Immersive Lighting](arkts-immersive-light-sense-faq.md).

> **NOTE**
>
> <!--RP1--><!--RP1End-->
> - After immersive lighting is enabled:
>   - The immersive lighting effect of the specified dialog components ([AlertDialog](../reference/apis-arkui/arkui-ts/ts-methods-alert-dialog-box.md), [ActionSheet](../reference/apis-arkui/arkui-ts/ts-methods-action-sheet.md), [CustomDialog](../reference/apis-arkui/arkui-ts/ts-methods-custom-dialog-box.md), [CalendarPickerDialog](../reference/apis-arkui/arkui-ts/ts-methods-calendarpicker-dialog.md), [DatePickerDialog](../reference/apis-arkui/arkui-ts/ts-methods-datepicker-dialog.md), [TimePickerDialog](../reference/apis-arkui/arkui-ts/ts-methods-timepicker-dialog.md), [TextPickerDialog](../reference/apis-arkui/arkui-ts/ts-methods-textpicker-dialog.md), [SelectionMenu](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-SelectionMenu.md), [AlphabetIndexer](../reference/apis-arkui/arkui-ts/ts-container-alphabet-indexer.md) popup, and the text menu triggered by long press or double tap after setting [copyOption](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#copyoption9) for [Text](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md)) can take effect on the entire page.
>   - The immersive lighting effect of the specified dialog APIs ([PromptAction](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md), [ArkUI_NativeDialog](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativedialog.md), [@ohos.promptAction (Dialog)](../reference/apis-arkui/js-apis-promptAction.md), [Popup Control](../reference/apis-arkui/arkui-ts/ts-universal-attributes-popup.md), [Tips Control](../reference/apis-arkui/arkui-ts/ts-universal-attributes-tips.md), [Menu Control](../reference/apis-arkui/arkui-ts/ts-universal-attributes-menu.md), [Sheet Transition](../reference/apis-arkui/arkui-ts/ts-universal-attributes-sheet-transition.md)) can take effect on the entire page.
>   - The immersive lighting effect of [Slider](../reference/apis-arkui/arkui-ts/ts-basic-components-slider.md), [Toggle](../reference/apis-arkui/arkui-ts/ts-basic-components-toggle.md), and [Select](../reference/apis-arkui/arkui-ts/ts-basic-components-select.md) can take effect on the entire page.
>   - Other components take effect only in the Navigation/NavDestination title bar or in the bottom TabBar of horizontal Tabs where barPosition is BarPosition.End. Setting the immersive lighting effect in other areas does not take effect.
> - For personalized configurations such as immersive system material color inversion, material colorization, interactive deformation and light sense interaction feedback, and shadow switch, see [Immersive System Material Visual Effects](arkts-immersive-light-sense-common-capability.md).

## Comparison of Immersive Light Sense Enablement Methods

The different enablement methods are compared as follows:

| Enablement Method | Supported Components | Description |
| --- | --- | --- |
| Application-Level Enabling | For the component list, see [MaterialState](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate). | Supports enablement in the following two ways:<br/> 1. Configure uniformly through [module.json5](../quick-start/module-configuration-file.md) to enable or globally disable immersive lighting in batches for components that support it. For details about how to enable it, see the content below the table.<br/>2. When this field is not configured in module.json5, the default mode is used. If a developer's application is upgraded from a version earlier than API version 26.0.0 to API version 26.0.0 or later, immersive lighting is enabled for components by default without any configuration, provided that immersive lighting has not been explicitly set. |
| Component-Level Enabling | For the component list and the setting method of each component, see [Component Adaptation to Immersive Light Sense](arkts-immersive-light-sense-component-adaptation.md) | Supports enablement in the following three ways:<br/> 1. Set through the universal attribute [systemMaterial](../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#systemmaterial).<br/>2. For dialog components, set through the systemMaterial field in the options parameter, for example, [ShowToastOptions](../reference/apis-arkui/js-apis-promptAction.md#showtoastoptions) of Toast and [CustomDialogControllerOptions](../reference/apis-arkui/arkui-ts/ts-methods-custom-dialog-box.md#customdialogcontrolleroptions) of custom dialogs.<br/>3. Set through component-specific APIs, for example, [menuSystemMaterial](../reference/apis-arkui/arkui-ts/ts-basic-components-select.md#menusystemmaterial) of the Select drop-down menu and [systemMaterial](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navigationtitleoptions11) of the Navigation title bar. |

Application-level enablement uniformly sets the immersive lighting switch of the application through the configuration file. In [module.json5](../quick-start/module-configuration-file.md), set the name field of the [metadata](../quick-start/module-configuration-file.md#metadata) parameter to "ohos.arkui.UIMaterial.state". When the value field is default or enable, immersive lighting is enabled; when the field is disable, it is disabled. This configuration takes effect only in modules of the entry type.

The following example shows how to configure the enable mode in [module.json5](../quick-start/module-configuration-file.md):

<!-- @[enable_module_config](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/arktsImmersiveLightSense/entry/src/main/module.json5) -->


``` JSON5
{
  "module": {
    "name": "entry",
    "type": "entry",
    // ...
    "metadata": [{
      "name": "ohos.arkui.UIMaterial.state",
      "value": "enable"
    }],
    // ...
  }
}
```


Developers can use [uiMaterial.getMaterialInfo()](../reference/apis-arkui/arkts-apis-uimaterial.md#uimaterialgetmaterialinfo) to obtain the current immersive system material configuration state [MaterialState](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate) of the application. [DEFAULT](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate), [ENABLE](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate), and [DISABLE](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate) in MaterialState correspond to the three values **default**, **enable**, and **disable** in the module.json5 configuration file, respectively.

> **NOTE**
>
> - Component-level enablement has a higher priority than application-level enablement. Developers can directly override the component effect enabled by the application-level switch through the component's immersive system material API, but not vice versa.

## Disabling Immersive Light Sense

You can disable immersive lighting in the following ways:

1. Component-level disabling: Set [uiMaterial.Material.empty](../reference/apis-arkui/arkts-apis-uimaterial.md#empty) at the component level. Both the application-level enablement and component-level enablement approaches can be disabled through this operation.

2. Application-level disabling: Set the application-level switch to disable, which globally disables immersive lighting. In this case, the immersive lighting effects enabled at both the application level and the component level do not take effect.

In addition, the immersive system materials of some components are controlled by multiple independent APIs. Take Select as an example: the immersive system material of its drop-down button is set through [systemMaterial](../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#systemmaterial), while the immersive system material of its drop-down menu is set through the independent [menuSystemMaterial](../reference/apis-arkui/arkui-ts/ts-basic-components-select.md#menusystemmaterial) API. The two are independent of each other and can be enabled or disabled separately.

> **NOTE**
>
> [uiMaterial.Material.empty](../reference/apis-arkui/arkts-apis-uimaterial.md#empty) and setting the systemMaterial attribute to undefined have different meanings: undefined means restoring to the component's default immersive lighting effect, while uiMaterial.Material.empty disables the immersive lighting effect. Therefore, to disable immersive lighting for a component that has it enabled by default, use uiMaterial.Material.empty.