# getBundleInstallerSync (System API)

## Modules to Import

```TypeScript
import { installer } from '@kit.AbilityKit';
```

## getBundleInstallerSync

```TypeScript
function getBundleInstallerSync(): BundleInstaller
```

Obtains and returns a BundleInstaller object. The API may return null when the call fails, so verify the return value before use.

**Since:** 10

<!--Device-installer-function getBundleInstallerSync(): BundleInstaller--><!--Device-installer-function getBundleInstallerSync(): BundleInstaller-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [BundleInstaller](arkts-ability-installer-bundleinstaller-i-sys.md) | BundleInstaller object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
