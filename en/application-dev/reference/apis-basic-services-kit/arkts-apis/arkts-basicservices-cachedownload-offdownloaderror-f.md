# offDownloadError

## Modules to Import

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';
```

## offDownloadError

```TypeScript
function offDownloadError(url: string, callback?: Callback<DownloadError>): void
```

Unsubscribes from the pre-download error events. This API uses an asynchronous callback to return the result.

**Since:** 23

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | URL to be unregistered, with a maximum of 8192 bytes. |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[DownloadError](arkts-basicservices-cachedownload-downloaderror-i.md)&gt; | No | Callback used to return the error information about the pre- download. If this parameter is left blank, all error callback functions of the URL are unregistered. |

**Examples**

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';

try {
  const errorCallback = (error: cacheDownload.DownloadError) => {
    console.info(`Error callback from cacheDownload.error code: ${error.errorCode}, error message: ${error.message}`);
  };
  // Subscribe to pre-download error events. When a download error occurs, the callback is invoked to return error information.
  cacheDownload.onDownloadError("https://www.example.com", errorCallback);
  // Unsubscribe from the pre-download error events.
  cacheDownload.offDownloadError("https://www.example.com", errorCallback);
  // Download the resource. If the download is successful, the resource will be cached to the specified file in the application memory or sandbox directory. 
  cacheDownload.download("https://www.example.com", {});
} catch (err) {
  console.error(`Failed to download the resource. err code: ${err.code}, err message: ${err.message}`);
}
```
