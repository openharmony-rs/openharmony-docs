# PluginModuleInfo

```TypeScript
export interface PluginModuleInfo
```

Provides the module information of a plugin, which describes the name and function description of the plugin module.

**Since:** 26.0.0

<!--Device-unnamed-export interface PluginModuleInfo--><!--Device-unnamed-export interface PluginModuleInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## description

```TypeScript
readonly description: string
```

Description of the plugin module. It corresponds to the **description** field configured in the [module.json5 configuration file](../../../quick-start/module-configuration-file.md#tags-in-the-configuration-file).

**Type:** string

**Since:** 26.0.0

<!--Device-PluginModuleInfo-readonly description: string--><!--Device-PluginModuleInfo-readonly description: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## descriptionId

```TypeScript
readonly descriptionId: number
```

Resource ID of the plugin module description. It is a resource ID automatically generated during compilation and building based on the **description** configured in the plugin configuration.

**Type:** number

**Since:** 26.0.0

<!--Device-PluginModuleInfo-readonly descriptionId: long--><!--Device-PluginModuleInfo-readonly descriptionId: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## moduleName

```TypeScript
readonly moduleName: string
```

Name of the plugin module. It corresponds to the **name** field configured in the [module.json5 configuration file](../../../quick-start/module-configuration-file.md#tags-in-the-configuration-file).

**Type:** string

**Since:** 26.0.0

<!--Device-PluginModuleInfo-readonly moduleName: string--><!--Device-PluginModuleInfo-readonly moduleName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
