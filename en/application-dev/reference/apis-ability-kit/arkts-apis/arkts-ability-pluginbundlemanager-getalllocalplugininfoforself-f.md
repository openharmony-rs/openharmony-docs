# getAllLocalPluginInfoForSelf

## Modules to Import

```TypeScript
import { pluginBundleManager } from '@kit.AbilityKit';
```

## getAllLocalPluginInfoForSelf

```TypeScript
function getAllLocalPluginInfoForSelf(): Promise<Array<PluginBundleInfo>>
```

Queries the information about all self-distributed plugins in the current app. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.kernel.SUPPORT_LOCAL_PLUGIN

**Model restriction:** This API can be used only in the stage model.

<!--Device-pluginBundleManager-function getAllLocalPluginInfoForSelf(): Promise<Array<PluginBundleInfo>>--><!--Device-pluginBundleManager-function getAllLocalPluginInfoForSelf(): Promise<Array<PluginBundleInfo>>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[PluginBundleInfo](arkts-ability-pluginbundlemanager-pluginbundleinfo-t.md)&gt;&gt; | Promise used to return the list of all local plugin information installed for the current application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Calling interface without permission 'ohos.permission.kernel.SUPPORT_LOCAL_PLUGIN'. |
