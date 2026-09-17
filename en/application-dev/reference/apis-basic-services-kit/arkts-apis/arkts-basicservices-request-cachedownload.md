# @ohos.request.cacheDownload(Download and Cache)

The **request** module provides applications with the basic capabilities of file upload and download and background transfer proxy.

- The child component **cacheDownload** provides the basic capability of caching application resources in advance.  
- **cacheDownload** uses the HTTP to download data and caches data resources to the application memory or specified  
files in the application sandbox directory.  
- The cached data can be used by specific ArkUI components (such as **Image**) to improve resource loading  
efficiency. Check whether the ArkUI components support this function by referring to the ArkUI component topics.

**Since:** 18

**System capability:** SystemCapability.Request.FileTransferAgent

## Modules to Import

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [cancel](arkts-basicservices-cachedownload-cancel-f.md) | Cancels an ongoing download task based on the URL. The saved memory cache and file cache are not affected. |
| [clearFileCache](arkts-basicservices-cachedownload-clearfilecache-f.md) | Clears this file cache. |
| [clearMemoryCache](arkts-basicservices-cachedownload-clearmemorycache-f.md) | Clears this memory cache. |
| [download](arkts-basicservices-cachedownload-download-f.md) | Downloads a task from a specified URL. If the transfer is successful, the data is downloaded to the memory cache and file cache. |
| [getDownloadInfo](arkts-basicservices-cachedownload-getdownloadinfo-f.md) | Obtains the download information based on the URL. The download information is stored in the download information list in memory and is cleared when the application exits. |
| [offDownloadError](arkts-basicservices-cachedownload-offdownloaderror-f.md) | Unsubscribes from the pre-download error events. This API uses an asynchronous callback to return the result. |
| [offDownloadSuccess](arkts-basicservices-cachedownload-offdownloadsuccess-f.md) | Unsubscribes from the pre-download completion events. This API uses an asynchronous callback to return the result. |
| [onDownloadError](arkts-basicservices-cachedownload-ondownloaderror-f.md) | Subscribes to the pre-download error events. This API uses an asynchronous callback to return the result. |
| [onDownloadSuccess](arkts-basicservices-cachedownload-ondownloadsuccess-f.md) | Subscribes to the pre-download completion events. This API uses an asynchronous callback to return the result. |
| [setDownloadInfoListSize](arkts-basicservices-cachedownload-setdownloadinfolistsize-f.md) | Sets the size of the download information list. |
| [setFileCacheSize](arkts-basicservices-cachedownload-setfilecachesize-f.md) | Sets the upper limit of the file cache size for the **cacheDownload** component. |
| [setGlobalRetryOptions](arkts-basicservices-cachedownload-setglobalretryoptions-f.md) | Sets retry options for all tasks. Used when task-specific retry configuration is not configured. |
| [setGlobalTimeoutOptions](arkts-basicservices-cachedownload-setglobaltimeoutoptions-f.md) | Sets timeout configuration for all tasks. Used when task-specific timeout configuration is not configured. |
| [setMemoryCacheSize](arkts-basicservices-cachedownload-setmemorycachesize-f.md) | Sets the upper limit of the memory cache size for the **cacheDownload** component. |

### Interfaces

| Name | Description |
| --- | --- |
| [CacheDownloadOptions](arkts-basicservices-cachedownload-cachedownloadoptions-i.md) | Provides configuration options for download and cache, including HTTP options, transmission options, and task options. |
| [DownloadError](arkts-basicservices-cachedownload-downloaderror-i.md) | Describes the error message returned when a pre-download error occurs. |
| [DownloadInfo](arkts-basicservices-cachedownload-downloadinfo-i.md) | Describes the pre-downloaded download information. |
| [NetworkInfo](arkts-basicservices-cachedownload-networkinfo-i.md) | Describes the pre-downloaded network information. |
| [PerformanceInfo](arkts-basicservices-cachedownload-performanceinfo-i.md) | Describes the pre-downloaded performance information. |
| [ResourceInfo](arkts-basicservices-cachedownload-resourceinfo-i.md) | Describes the pre-downloaded resource information. |
| [RetryOptions](arkts-basicservices-cachedownload-retryoptions-i.md) | Task retry configuration. |
| [TimeoutOptions](arkts-basicservices-cachedownload-timeoutoptions-i.md) | Task timeout configuration. |

### Enums

| Name | Description |
| --- | --- |
| [CacheStrategy](arkts-basicservices-cachedownload-cachestrategy-e.md) | Enumerates cache update strategies. |
| [ErrorCode](arkts-basicservices-cachedownload-errorcode-e.md) | Enumerates the specific types of returned error code. |
| [SslType](arkts-basicservices-cachedownload-ssltype-e.md) | Enumerates secure communication protocols. |
