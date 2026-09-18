# getDownloadInfo

## Modules to Import

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';
```

## getDownloadInfo

```TypeScript
function getDownloadInfo(url: string): DownloadInfo | undefined
```

Obtains the download information based on the URL. The download information is stored in the download information list in memory and is cleared when the application exits.

- If the specified URL is found in the download information list, the latest [DownloadInfo](arkts-basicservices-cachedownload-downloadinfo-i.md) corresponding to the URL is returned.  
- If the specified URL cannot be found in the download information list, **undefined** is returned.  
- If the download information has already cached in the URL, the new cached information will overwrite the old  
one.  
- When the target information is stored in the memory, the existing cache data is replaced in the LRU mode.

**Since:** 20

**Required permissions:** ohos.permission.GET_NETWORK_INFO

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | URL to be queried, with a maximum length of 8192 bytes. |

**Return value:**

| Type | Description |
| --- | --- |
| [DownloadInfo](arkts-basicservices-cachedownload-downloadinfo-i.md) &#124; undefined | Returns the download information of the corresponding URL if the operation is successful; returns **undefined** if the specified URL does not exist. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | permission denied. |
