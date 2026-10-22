# @ohos.bundle.pluginBundleManager(pluginBundleManager module)

This module provides the capability of managing self-distributed plugins for an app, including installing and uninstalling local plugins.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-declare namespace pluginBundleManager--><!--Device-unnamed-declare namespace pluginBundleManager-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## Modules to Import

```TypeScript
import { pluginBundleManager } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getAllLocalPluginInfoForSelf](arkts-ability-pluginbundlemanager-getalllocalplugininfoforself-f.md#getalllocalplugininfoforself-1) | Queries the information about all self-distributed plugins in the current app. This API uses a promise to return the result. |
| [installLocalPlugin](arkts-ability-pluginbundlemanager-installlocalplugin-f.md#installlocalplugin-1) | Installs a self-distributed plugin (that is, a plugin distributed and managed by the app through its own channels) for the current app. This API uses a promise to return the result. |
| [uninstallLocalPlugin](arkts-ability-pluginbundlemanager-uninstalllocalplugin-f.md#uninstalllocalplugin-1) | Uninstalls the specified plugin installed by the current app through self-distribution. This API uses a promise to return the result. |

### Types

| Name | Description |
| --- | --- |
| [PluginBundleInfo](arkts-ability-pluginbundlemanager-pluginbundleinfo-t.md) | Plugin information. |
| [PluginModuleInfo](arkts-ability-pluginbundlemanager-pluginmoduleinfo-t.md) | Module information of the plugin. |
