# installLocalPlugin

## Modules to Import

```TypeScript
import { pluginBundleManager } from '@kit.AbilityKit';
```

## installLocalPlugin

```TypeScript
function installLocalPlugin(pluginFilePaths: Array<string>): Promise<void>
```

Install the plugin for self application.

**Since:** 26.0.0

**Required permissions:** ohos.permission.kernel.SUPPORT_LOCAL_PLUGIN

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pluginFilePaths | Array&lt;string&gt; | Yes | Indicates the file paths of plugin. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Calling interface without permission 'ohos.permission.kernel.SUPPORT_LOCAL_PLUGIN'. |
| [17700010](../errorcode-bundle.md#17700010-bundle-installation-failure-due-to-file-parsing-failure) | Failed to install the plugin because the plugin fails to be parsed. |
| [17700011](../errorcode-bundle.md#17700011-bundle-installation-failure-due-to-signature-verification-failure) | Failed to install the plugin because the plugin signature fails to be verified. |
| [17700012](../errorcode-bundle.md#17700012-bundle-installation-failure-due-to-invalid-file-path-or-too-large-file) | Failed to install the plugin because the HSP path is invalid or the HSP is too large. |
| [17700015](../errorcode-bundle.md#17700015-bundle-installation-failure-due-to-different-configuration-information-of-multiple-haps) | Failed to install the plugin because they have different configuration information. |
| [17700016](../errorcode-bundle.md#17700016-bundle-installation-failure-due-to-insufficient-system-disk-space) | Failed to install the plugin because of insufficient system disk space. |
| [17700017](../errorcode-bundle.md#17700017-bundle-installation-failure-because-the-version-to-install-is-too-earlier) | Failed to install the plugin since the version of the plugin to install is too early. |
| [17700048](../errorcode-bundle.md#17700048-code-signature-verification-failure) | Failed to install the plugin because the code signature verification failed. |
| [17700052](../errorcode-bundle.md#17700052-installing-a-debug-self-distributed-plugin-or-debug-application-is-not-allowed-in-non-developer-mode) | Failed to install the plugin because debug bundle cannot be installed under non-developer mode. |
| [17700073](../errorcode-bundle.md#17700073-installation-failure-caused-by-an-application-with-the-same-bundle-name-but-different-signature-information) | Failed to install the plugin because a plugin with the same<br>bundle name but different signature information exists on the device. |
| [17700087](../errorcode-bundle.md#17700087-unsupported-plugin-installation) | Failed to install the plugin because the current device does not support plugins. |
| [17700091](../errorcode-bundle.md#17700091-plugin-installation-failure-because-of-the-same-plugin-name-and-host-bundle-name) | Failed to install the plugin because the plugin name is the same as the host bundle name. |
