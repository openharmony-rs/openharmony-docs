# setDownloadInfoListSize

## Modules to Import

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';
```

## setDownloadInfoListSize

```TypeScript
function setDownloadInfoListSize(size: number): void
```

Sets the size of the download information list.

- The download information list is used to store pre-downloaded information.  
- Each pre-download generates a piece of download information with a unique URL. Only the latest download  
information is saved for the same URL.  
- If the list size is increased using this API, the original information in the list remains unchanged; if the  
list size is decreased, the LRU mode is used by default to clear excess cached data in the list.

**Since:** 20

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | number | Yes | Size of the download information list. The value ranges from 0 to 8192. The default value is **0**, indicating that no download information is stored. |

**Examples**

```TypeScript
import { cacheDownload, BusinessError } from '@kit.BasicServicesKit';

try {
  // Set the size of the download information list. 
  cacheDownload.setDownloadInfoListSize(2048);
} catch (err) {
  console.error(`Failed to set download information list size. err code: ${err.code}, err message: ${err.message}`);
}
```
