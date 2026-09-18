# offDownloadSuccess

## Modules to Import

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';
```

## offDownloadSuccess

```TypeScript
function offDownloadSuccess(url: string, callback?: Callback<void>): void
```

Unsubscribes from the pre-download completion events. This API uses an asynchronous callback to return the result.

**Since:** 23

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | Callback URL to be registered, with a maximum of 8,192 bytes. |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;void&gt; | No | Callback to unregister. If this parameter is left blank, all completion callback functions of the URL are unregistered. |

**Examples**

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';

try {
  const successCallback = () => {
    console.info("Succeeded in getting callback from cacheDownload");
  };
  // Subscribe to the pre-download completion events. Callback is invoked when the download is complete.
  cacheDownload.onDownloadSuccess("https://www.example.com", successCallback);
  // Unsubscribe from the pre-download completion events.
  cacheDownload.offDownloadSuccess("https://www.example.com", successCallback);
  // Download the resource. If the download is successful, the resource will be cached to the specified file in the application memory or sandbox directory. 
  cacheDownload.download("https://www.example.com", {});
} catch (err) {
  console.error(`Failed to download the resource. err code: ${err.code}, err message: ${err.message}`);
}
```
