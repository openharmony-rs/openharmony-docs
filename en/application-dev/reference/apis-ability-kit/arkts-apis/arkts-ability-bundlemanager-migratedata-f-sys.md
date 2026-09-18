# migrateData (System API)

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## migrateData

```TypeScript
function migrateData(sourcePaths: Array<string>, destinationPath: string): Promise<void>
```

Migrates files from the source path to the destination path. This API uses a promise to return the result.

**Since:** 18

**Required permissions:** ohos.permission.MIGRATE_DATA

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sourcePaths | Array&lt;string&gt; | Yes | Array of source paths. The value can be a single file path such as **\/example1/test.txt** or a directory path such as **\/example2/test**. |
| destinationPath | string | Yes | Destination path. Only one directory path is supported, for example, **\/example2/test**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [17700080](../errorcode-bundle.md#17700080-invalid-source-paths) | The source paths are invalid. |
| [17700081](../errorcode-bundle.md#17700081-invalid-destination-path) | The destination path is invalid. |
| [17700082](../errorcode-bundle.md#17700082-user-authentication-failed) | User authentication failed. |
| [17700083](../errorcode-bundle.md#17700083-user-authentication-times-out) | Waiting for user authentication timeout. |
| [17700084](../errorcode-bundle.md#17700084-no-read-permissions-for-source-paths) | There are inaccessible path in the source paths. |
| [17700085](../errorcode-bundle.md#17700085-no-write-permissions-for-the-destination-path) | The destination path cannot be accessed. |
| [17700086](../errorcode-bundle.md#17700086-system-error) | System error occurred during copy execution. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  // Change the values of source1, source2, and dest to the actual file or directory paths.
  let source1: string = "/data/app/el2/100/base/com.example.myapplication/";
  let source2: string = "/data/app/el2/101/base/com.example.myapplication/log.txt";
  let dest: string = "/data/local/tmp";
  let sourcePaths: Array<string> = [source1, source2];

  bundleManager.migrateData(sourcePaths, dest)
    .then(() => {
      hilog.info(0x0000, 'testTag', 'migrateData succeed');
    })
    .catch((err: BusinessError) => {
      hilog.error(0x0000, 'testTag', 'migrateData err: %{public}s', JSON.stringify(err));
    })
} catch (err) {
  hilog.error(0x0000, 'testTag', 'migrateData call err: %{public}s', JSON.stringify(err));
}
```
