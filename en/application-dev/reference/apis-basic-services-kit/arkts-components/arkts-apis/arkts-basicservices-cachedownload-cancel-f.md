# cancel

## Modules to Import

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';
```

## cancel

```TypeScript
function cancel(url: string): void
```

Cancels an ongoing download task based on the URL. The saved memory cache and file cache are not affected.

- If there is no download task with the specified URL, this API does not take effect.  
- When this API is used for synchronous execution, the calling thread is not blocked.

**Since:** 18

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | URL of the target resource. HTTP and HTTPS are supported. The URL length cannot exceed 81 92 bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter error. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed. |

**Examples**

```TypeScript
import { cacheDownload, BusinessError } from '@kit.BasicServicesKit';

// Provide configuration options for the download task.
let options: cacheDownload.CacheDownloadOptions = {};

try {
  // Download the resource. If the download is successful, the resource will be cached to the specified file in the application memory or sandbox directory. 
  cacheDownload.download("https://www.example.com", options);
} catch (err) {
  console.error(`Failed to download the resource. err code: ${err.code}, err message: ${err.message}`);
}

// Other service logic is omitted here.

try {
  // Cancel the download task when it is not required. The cached data is not affected.
  cacheDownload.cancel("https://www.example.com");
} catch (err) {
  console.error(`Failed to cancel the task. err code: ${err.code}, err message: ${err.message}`);
}
```
