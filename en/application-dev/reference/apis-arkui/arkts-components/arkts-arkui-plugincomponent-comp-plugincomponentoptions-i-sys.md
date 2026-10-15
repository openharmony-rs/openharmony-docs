# PluginComponentOptions (System API)

```TypeScript
declare interface PluginComponentOptions
```

Defines options for constructing a **PluginComponent**.

> **NOTE:** 
> 
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18.
> While historical version information is preserved for anonymous objects, there may be cases where the outer element
> 's

**Since:** 9

<!--Device-unnamed-declare interface PluginComponentOptions--><!--Device-unnamed-declare interface PluginComponentOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## data

```TypeScript
data: any
```

Data passed to the plugin component provider for use. The type is not limited (objects, strings, and so on are supported). The specific data format is defined through negotiation between the user and the provider.

**Type:** any

**Since:** 9

<!--Device-PluginComponentOptions-data: any--><!--Device-PluginComponentOptions-data: any-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## template

```TypeScript
template: PluginComponentTemplate
```

Template of the **PluginComponent**, which is bound to the component defined by the provider.

**Type:** [PluginComponentTemplate](arkts-arkui-plugincomponent-comp-plugincomponenttemplate-i-sys.md)

**Since:** 9

<!--Device-PluginComponentOptions-template: PluginComponentTemplate--><!--Device-PluginComponentOptions-template: PluginComponentTemplate-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
