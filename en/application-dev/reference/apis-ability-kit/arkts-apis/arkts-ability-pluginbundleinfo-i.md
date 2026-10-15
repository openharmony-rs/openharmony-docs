# PluginBundleInfo

```TypeScript
export interface PluginBundleInfo
```

Provides the plugin information, which is obtained by calling [pluginBundleManager.getAllLocalPluginInfoForSelf](arkts-ability-pluginbundlemanager-getalllocalplugininfoforself-f.md) to obtain all plugin information installed by the current app through self-distribution. The information includes the plugin name, icon, version number, and module information, and is used to manage installed plugins and perform compatibility checks and updates based on the version number and module information.

**Since:** 26.0.0

<!--Device-unnamed-export interface PluginBundleInfo--><!--Device-unnamed-export interface PluginBundleInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## icon

```TypeScript
readonly icon: string
```

Icon of the plugin. Corresponds to the **icon** field configured in [app.json5](../../../quick-start/app-configuration-file.md#tags-in-the-configuration-file).

**Type:** string

**Since:** 26.0.0

<!--Device-PluginBundleInfo-readonly icon: string--><!--Device-PluginBundleInfo-readonly icon: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## iconId

```TypeScript
readonly iconId: number
```

Resource ID of the plugin icon. It is automatically generated during compilation and building based on the icon configured for the plugin.

**Type:** number

**Since:** 26.0.0

<!--Device-PluginBundleInfo-readonly iconId: long--><!--Device-PluginBundleInfo-readonly iconId: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## label

```TypeScript
readonly label: string
```

Name of the plugin. Corresponds to the **label** field configured in [app.json5](../../../quick-start/app-configuration-file.md#tags-in-the-configuration-file).

**Type:** string

**Since:** 26.0.0

<!--Device-PluginBundleInfo-readonly label: string--><!--Device-PluginBundleInfo-readonly label: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## labelId

```TypeScript
readonly labelId: number
```

Resource ID of the plugin name. It is automatically generated during compilation and building based on the label configured for the plugin.

**Type:** number

**Since:** 26.0.0

<!--Device-PluginBundleInfo-readonly labelId: long--><!--Device-PluginBundleInfo-readonly labelId: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## pluginBundleName

```TypeScript
readonly pluginBundleName: string
```

Bundle name of the application that installs the plugin. Corresponds to the **bundleName** field configured in [app.json5](../../../quick-start/app-configuration-file.md#tags-in-the-configuration-file).

**Type:** string

**Since:** 26.0.0

<!--Device-PluginBundleInfo-readonly pluginBundleName: string--><!--Device-PluginBundleInfo-readonly pluginBundleName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## pluginModuleInfos

```TypeScript
readonly pluginModuleInfos: Array<PluginModuleInfo>
```

Module information of the plugin.

**Type:** Array&lt;[PluginModuleInfo](arkts-ability-pluginbundleinfo-pluginmoduleinfo-i.md)&gt;

**Since:** 26.0.0

<!--Device-PluginBundleInfo-readonly pluginModuleInfos: Array<PluginModuleInfo>--><!--Device-PluginBundleInfo-readonly pluginModuleInfos: Array<PluginModuleInfo>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## versionCode

```TypeScript
readonly versionCode: number
```

Version code of the plugin. Corresponds to the **versionCode** field configured in [app.json5](../../../quick-start/app-configuration-file.md#tags-in-the-configuration-file).

**Type:** number

**Since:** 26.0.0

<!--Device-PluginBundleInfo-readonly versionCode: long--><!--Device-PluginBundleInfo-readonly versionCode: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## versionName

```TypeScript
readonly versionName: string
```

Version name of the plugin. Corresponds to the **versionName** field configured in [app.json5](../../../quick-start/app-configuration-file.md#tags-in-the-configuration-file).

**Type:** string

**Since:** 26.0.0

<!--Device-PluginBundleInfo-readonly versionName: string--><!--Device-PluginBundleInfo-readonly versionName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
