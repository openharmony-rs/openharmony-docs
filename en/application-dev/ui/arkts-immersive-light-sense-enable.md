# Enabling Immersive Light Sensing

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @H-xinwei-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=972f1649fdb6ebd99757019463fe43a902cdae45 translatedAt=2026-08-31T03:10:47.395Z pushedAt=2026-09-03T10:59:13.853Z -->

Immersive light sensing provides two enablement methods: app-level and component-level, which can be selected as needed. Once enabled, immersive light sensing requires significant GPU resources. For specific usage guidance, refer to [Immersive Light Sensing Power Consumption Optimization](arkts-immersive-light-sense-constraints.md). For other common issues after the function is enabled, refer to [Immersive Light Sensing FAQ](arkts-immersive-light-sense-faq.md).

## Comparison of Immersive Light Sense Enabling Methods

> **NOTE**
>
> - To enable immersive light sense, ensure that the [targetAPIVersion](../quick-start/app-configuration-file.md) of your app is not earlier than 26.0.0. For adaptation to earlier versions, see [Immersive Light Sense Compatibility Adaptation](arkts-immersive-light-sense-compatibility.md).
> - After immersive light sense is enabled, except for Slider, Toggle, and popup-type components, other components take effect only in the following subtrees: the title bar subtree of Navigation/NavDestination, or the bottom TabBar subtree of a horizontal Tabs where barPosition is BarPosition.End. Popup-type components include Popup, Tips, Menu, BindSheet, AlertDialog, CustomDialog, ActionSheet, CalendarPickerDialog, DatePickerDialog, TextPickerDialog, TimePickerDialog, Toast, Select drop-down menu, AlphabetIndexer bubble popup, and SelectionMenu text selection menu.

The following table compares the different enabling methods:

| Enabling Method | Supported Components | Description |
| --- | --- | --- |
| App-level | For the component list, see [MaterialState](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate). | Supports enabling in the following two ways:<br/> 1. Configure uniformly through [module.json5](../quick-start/module-configuration-file.md) to enable or globally disable immersive light sense in batches for components that support it. For details about how to enable it, see the content below the table.<br/>2. When this field is not configured in module.json5, the default mode applies. If your app is upgraded from an API version earlier than 26.0.0 to API version 26.0.0 or later, immersive light sense is enabled for components by default without any configuration when it is not explicitly set. |
| Component-level | Components that support setting the immersive system material | Supports enabling in the following three ways:<br/> 1. Set it through the universal attribute [systemMaterial](../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#systemmaterial).<br/>2. For popup-type components, set it through the systemMaterial field in the options parameter.<br/>3. Set it through component-specific APIs. The components that currently support this setting include the [menuSystemMaterial](../reference/apis-arkui/arkui-ts/ts-basic-components-select.md#menusystemmaterial) of the Select drop-down menu and the [systemMaterial](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navigationtitleoptions11) of the Navigation title bar. |

App-level enabling uniformly sets the immersive light sense switch of the app through the configuration file. In [module.json5](../quick-start/module-configuration-file.md), set the name field of the [metadata](../quick-start/module-configuration-file.md#metadata) parameter to "ohos.arkui.UIMaterial.state". Immersive light sense is enabled when the value field is default or enable, and disabled when the field is disable. This configuration takes effect only in modules of the entry type.

The following example shows how to configure the enable mode in [module.json5](../quick-start/module-configuration-file.md):

```json5
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

You can call [uiMaterial.getMaterialInfo()](../reference/apis-arkui/arkts-apis-uimaterial.md#uimaterialgetmaterialinfo) to obtain the current immersive system material configuration state [MaterialState](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate) of the app. [DEFAULT](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate), [ENABLE](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate), and [DISABLE](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate) in MaterialState correspond to the three value values default, enable, and disable in the module.json5 configuration file, respectively.

> **NOTE**
>
> - When the app-level switch is set to disable, immersive light sense is globally disabled, and neither app-level nor component-level enable settings take effect.
> - Component-level enabling has a higher priority than app-level enabling. You can directly override the component effect enabled by the app-level switch through the immersive system material API of a component, but not vice versa.

## Disabling Immersive Light Sensing

There are several ways to disable immersive light sensing:

1. Component-level disable: Set the component-level [uiMaterial.Material.empty](../reference/apis-arkui/arkts-apis-uimaterial.md#empty). Both app-level enablement and component-level enablement methods can be disabled through this operation.

2. App-level disable: Set the app-level switch to disable. This only applies to components enabled at the app level.























































In addition, the immersive system materials of some components are controlled by multiple independent APIs. Taking **Select** as an example, the immersive system material of its drop-down button is set via [systemMaterial](../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#systemmaterial), while the immersive system material of its drop-down menu is set via an independent [menuSystemMaterial](../reference/apis-arkui/arkui-ts/ts-basic-components-select.md#menusystemmaterial) API. These two are independent of each other and can be enabled or disabled separately.

> **NOTE**
>
> [uiMaterial.Material.empty](../reference/apis-arkui/arkts-apis-uimaterial.md#empty) has a different meaning from setting the **systemMaterial** property to **undefined**. **undefined** indicates restoring the component to its default immersive light sensing API effect. **uiMaterial.Material.empty** disables the immersive light sensing effect. Therefore, to disable a component that has immersive light sensing enabled by default, **uiMaterial.Material.empty** should be used.