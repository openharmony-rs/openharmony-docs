# uninstallLocalPlugin

## Modules to Import

```TypeScript
import { pluginBundleManager } from '@kit.AbilityKit';
```

## uninstallLocalPlugin

```TypeScript
function uninstallLocalPlugin(pluginBundleName: string): Promise<void>
```

Uninstalls the specified plugin installed by the current app through self-distribution. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.kernel.SUPPORT_LOCAL_PLUGIN

**Model restriction:** This API can be used only in the stage model.

<!--Device-pluginBundleManager-function uninstallLocalPlugin(pluginBundleName: string): Promise<void>--><!--Device-pluginBundleManager-function uninstallLocalPlugin(pluginBundleName: string): Promise<void>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pluginBundleName | string | Yes | Bundle name of the plugin, indicating the application bundle name of the plugin to be uninstalled. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Calling interface without permission 'ohos.permission.kernel.SUPPORT_LOCAL_PLUGIN'. |
| [17700092](../errorcode-bundle.md#17700092-plugin-uninstall-failure-because-of-nonexistent-plugin-bundle-name) | Failed to uninstall the plugin because the specified plugin is not found. |
