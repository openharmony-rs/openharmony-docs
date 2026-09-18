# getAllLocalPluginInfoForSelf

## Modules to Import

```TypeScript
import { pluginBundleManager } from '@kit.AbilityKit';
```

## getAllLocalPluginInfoForSelf

```TypeScript
function getAllLocalPluginInfoForSelf(): Promise<Array<PluginBundleInfo>>
```

Obtains information about all local plugins installed on the current application.

**Since:** 26.0.0

**Required permissions:** ohos.permission.kernel.SUPPORT_LOCAL_PLUGIN

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[PluginBundleInfo](arkts-ability-pluginbundlemanager-pluginbundleinfo-t.md)&gt;&gt; | Promise used to return the list of PluginBundleInfos object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Calling interface without permission 'ohos.permission.kernel.SUPPORT_LOCAL_PLUGIN'. |
