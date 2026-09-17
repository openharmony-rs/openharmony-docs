# getStorageDataDir (System API)

## Modules to Import

```TypeScript
import { Environment } from '@kit.CoreFileKit';
```

## getStorageDataDir

```TypeScript
function getStorageDataDir(): Promise<string>
```

Obtains the root directory of the memory. This API uses a promise to return the result.

**Since:** 8

**System capability:** SystemCapability.FileManagement.File.Environment

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the root directory of the memory. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application |
| 13900020 | Invalid argument |
| 13900042 | Unknown error |


## getStorageDataDir

```TypeScript
function getStorageDataDir(callback: AsyncCallback<string>): void
```

Obtains the root directory of the memory. This API uses an asynchronous callback to return the result.

**Since:** 8

**System capability:** SystemCapability.FileManagement.File.Environment

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the root directory of the memory. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application |
| 13900020 | Invalid argument |
| 13900042 | Unknown error |
