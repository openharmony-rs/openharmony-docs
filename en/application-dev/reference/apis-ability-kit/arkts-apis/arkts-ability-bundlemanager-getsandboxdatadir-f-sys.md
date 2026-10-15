# getSandboxDataDir (System API)

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getSandboxDataDir

```TypeScript
function getSandboxDataDir(bundleName: string, appIndex: number): string
```

Obtains the sandbox directory of an application based on the given bundle name and clone index.

**Since:** 20

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-bundleManager-function getSandboxDataDir(bundleName: string, appIndex: int): string--><!--Device-bundleManager-function getSandboxDataDir(bundleName: string, appIndex: int): string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the application. This API can be called only when the application or its clone is available for the current user. Otherwise, error code 17700001 is returned. |
| appIndex | number | Yes | Application index, used to identify different application instances. The value is an integer.<br>Value range:<br>- 0: main application <br> - [1, 5]: clone application<br>- [2000, 3000]: sandbox application (supported since API version 26.0.0) |

**Return value:**

| Type | Description |
| --- | --- |
| string | Sandbox directory of the application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName is not found. |
| [17700061](../errorcode-bundle.md#17700061-appindex-for-a-clone-is-invalid) | AppIndex not in valid range. |

<!--Del-->
**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = 'com.example.myapplication';
let appIndex = 1;

try {
  let dataDir = bundleManager.getSandboxDataDir(bundleName, appIndex);
  hilog.info(0x0000, 'testTag', 'getSandboxDataDir successfully. dataDir:%{public}s', dataDir);
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getSandboxDataDir failed. Cause: %{public}s', message);
}
```

<!--DelEnd-->
