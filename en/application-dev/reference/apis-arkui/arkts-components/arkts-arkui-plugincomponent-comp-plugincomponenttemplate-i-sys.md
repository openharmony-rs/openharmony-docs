# PluginComponentTemplate (System API)

```TypeScript
interface PluginComponentTemplate
```

Defines the plugin component template information, which is used to bind to the component defined by the provider.

**Since:** 9

<!--Device-unnamed-interface PluginComponentTemplate--><!--Device-unnamed-interface PluginComponentTemplate-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## bundleName

```TypeScript
bundleName: string
```

bundleName of the provider application. This field does not need to be filled in when the template is provided through an absolute path, but must be filled in when the template is provided through an application package. For details, see [Attributes](#attributes).

**Type:** string

**Since:** 9

<!--Device-PluginComponentTemplate-bundleName: string--><!--Device-PluginComponentTemplate-bundleName: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## source

```TypeScript
source: string
```

Source of the component template. The value can be the absolute path of the template (not recommended), a relative path to the HAP package (in the "relative path&module name" format for multi-HAP scenarios), or the AbilityName in the FA model. For details, see [Attributes](#attributes).

**Type:** string

**Since:** 9

<!--Device-PluginComponentTemplate-source: string--><!--Device-PluginComponentTemplate-source: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
