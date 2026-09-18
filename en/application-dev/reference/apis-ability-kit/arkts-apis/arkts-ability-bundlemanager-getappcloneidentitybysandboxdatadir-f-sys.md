# getAppCloneIdentityBySandboxDataDir (System API)

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getAppCloneIdentityBySandboxDataDir

```TypeScript
function getAppCloneIdentityBySandboxDataDir(sandboxDataDir: string): AppCloneIdentity
```

Obtains the identity information of an application, including the bundle name and clone index, based on the given sandbox directory name.

**Since:** 20

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sandboxDataDir | string | Yes | Name of the [sandbox directory of the application](../../../file-management/app-sandbox-directory.md).<br>**NOTE:** <br> The validity of this parameter is not verified. If the input **sandboxDataDir** does not match the directory name format for application clones or atomic services, **sandboxDataDir** is returned as **AppCloneIdentity.bundleName**, and **AppCloneIdentity.appIndex** is **0**.<br> 1. Directory name format for application clones: `+clone-{appIndex}+{bundleName}`, where **appIndex** and **bundleName** are variables corresponding to the clone index and bundle name, respectively. Example: `+clone-1+com.example.myapplication`.<br> 2. Directory name format for atomic services: `+auid-{uid}+{bundleName}`, where **uid** and **bundleName** are variables corresponding to the UID and bundle name, respectively. Example: `+auid-20000000+ com.example.myapplication`. |

**Return value:**

| Type | Description |
| --- | --- |
| [AppCloneIdentity](arkts-ability-bundlemanager-appcloneidentity-t.md) | Bundle name and clone index of the application. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// Main application.
let dataDir = 'com.example.myapplication';
try {
  let res = bundleManager.getAppCloneIdentityBySandboxDataDir(dataDir);
  hilog.info(0x0000, 'testTag', 'getAppCloneIdentityBySandboxDataDir successfully. res:%{public}s',
    JSON.stringify(res));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAppCloneIdentityBySandboxDataDir failed. Cause: %{public}s',
    message);
}

// Application clone.
let cloneDataDir = '+clone-1+com.example.myapplication';
try {
  let res = bundleManager.getAppCloneIdentityBySandboxDataDir(cloneDataDir);
  hilog.info(0x0000, 'testTag', 'getAppCloneIdentityBySandboxDataDir successfully. res:%{public}s',
    JSON.stringify(res));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAppCloneIdentityBySandboxDataDir failed. Cause: %{public}s',
    message);
}

// Atomic services
let atomicDataDir = '+auid-20000000+com.example.myapplication';
try {
  let res = bundleManager.getAppCloneIdentityBySandboxDataDir(atomicDataDir);
  hilog.info(0x0000, 'testTag', 'getAppCloneIdentityBySandboxDataDir successfully. res:%{public}s',
    JSON.stringify(res));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAppCloneIdentityBySandboxDataDir failed. Cause: %{public}s',
    message);
}
```
