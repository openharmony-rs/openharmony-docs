# @ohos.request.cacheDownload (Download and Cache)
<!--Kit: Basic Services Kit-->
<!--Subsystem: Request-->
<!--Owner: @huaxin05-->
<!--Designer: @hu-kai45-->
<!--Tester: @liuhaonan2-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=d048b0bafe3e0e15f26e9ac5f8f709f206e6bb17 translatedAt=2026-11-10T04:10:39.092Z pushedAt=2026-11-10T06:56:22.274Z nl=1 -->

The **request** module provides applications with the basic capabilities of file upload and download and background transfer proxy.

- The child component **cacheDownload** provides the basic capability of caching application resources in advance.

- The **cacheDownload** component uses HTTP and HTTPS to download data and caches data resources to the application memory or specified files in the application sandbox directory.

- The cached data can be used by specific ArkUI components (such as **Image**) to improve resource loading efficiency. Check whether the ArkUI components support this function by referring to the ArkUI component topics.

> **NOTE**
>
> The initial APIs of this module are supported since API version 18. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```js
import { cacheDownload } from '@kit.BasicServicesKit';
```

## SslType<sup>21+</sup>

Enumerates secure communication protocols.

**System capability:** SystemCapability.Request.FileTransferAgent

| Name| Value|Description|
| -------- | -------- |-------- |
| TLS | 'TLS' | TLS.|
| TLCP | 'TLCP' | TLCP.|

## ErrorCode<sup>23+</sup>

Enumerates the specific types of returned error code.

**System capability:** SystemCapability.Request.FileTransferAgent

| Name| Value|Description|
| -------- | -------- |-------- |
| OTHERS | 0xFF | Other types of errors that are not classified.|
| DNS | 0x00 | DNS-related errors.|
| TCP | 0x10 | TCP-related errors.|
| SSL | 0x20 | SSL-related errors.|
| HTTP | 0x30 | HTTP-related errors.|

## CacheStrategy<sup>23+</sup>

Enumerates cache update strategies.

**System capability:** SystemCapability.Request.FileTransferAgent

| Name| Value|Description|
| -------- | -------- |-------- |
| FORCE | 0 | Forcibly updates the cache, regardless of whether the cache already exists.|
| LAZY | 1 | Updates the cache only when the cache does not exist.|

## TimeoutOptions

Enumerates the timeout configuration option of a task, including the timeout interval for checking network availability and the timeout interval for completing an HTTP request.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Request.FileTransferAgent

| Name  | Type    | Read-Only| Optional| Description                           |
|------|--------|----|----|-------------------------------|
| networkCheckTimeout | number | No | Yes | Timeout for checking network availability, in seconds. The default value is 20, the minimum value is 0 (a value of 0 means no network availability check is performed), and the maximum value is 20. An exception is thrown when the value is out of range.<br>Checking the network requires the permission **ohos.permission.GET_NETWORK_INFO**. Without the permission, the network check fails until timeout. |
| httpTotalTimeout | number | No | Yes | Timeout for completing an HTTP request, in seconds. The default value is 60, the minimum value is 1, and the maximum value is 4294967 |

## RetryOptions

Enumerates retry options of a task, which is used to set the maximum number of retries.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Request.FileTransferAgent

| Name  | Type    | Read-Only| Optional| Description                           |
|------|--------|----|----|-------------------------------|
| maxRetryCount | number | No  | Yes | Maximum number of retries when a task fails. The default value is 1, the minimum value is 0, and the maximum value is 10. An exception is thrown when the value is out of range. |

## CacheDownloadOptions

Provides configuration options for download and cache, including HTTP options, transmission options, and task options.

**System capability:** SystemCapability.Request.FileTransferAgent

| Name  | Type    | Read-Only| Optional| Description                           |
|------|--------|----|----|-------------------------------|
| headers | Record\<string, string\> | No | Yes| Request header used by a download task during HTTP transfer. The default value is empty.|
| sslType<sup>21+</sup> | [SslType](#ssltype21) | No | Yes| Secure communication protocol, such as TLS or TLCP. TLS is used by default. Currently, TLS and TLCP do not support two-way authentication.|
| caPath<sup>21+</sup> | string | No | Yes| CA certificate path. Currently, only the .pem certificate is supported. The CA certificate preset by the system is used by default.|
| cacheStrategy<sup>23+</sup> | [CacheStrategy](#cachestrategy23) | No | Yes| Cache update strategies, including **FORCE** or **LAZY**. The **FORCE** policy is used by default.|
| retry | [RetryOptions](#retryoptions) | No | Yes | Retry configuration of a task, used to customize the retry behavior for a single task. Set this option when the retry count needs to be specified separately for the task; if not set, it falls back to the global retry configuration (setGlobalRetryOptions), and then to the default value (maxRetryCount defaults to 1).<br>**Since Version:** 26.0.0<br>**Model Constraint:** This API can be used only in the stage model. |
| timeout | [TimeoutOptions](#timeoutoptions) | No | Yes | Timeout configuration of a task, used to customize the timeout behavior for a single task. Set this option when the network check timeout or HTTP request timeout needs to be specified separately for the task; if not set, it falls back to the global timeout configuration (setGlobalTimeoutOptions), and then to the default values (networkCheckTimeout defaults to 20 and httpTotalTimeout defaults to 60).<br>**Since Version:** 26.0.0<br>**Model Constraint:** This API can be used only in the stage model. |

## ResourceInfo<sup>20+</sup>

Describes the pre-downloaded resource information.

**System capability:** SystemCapability.Request.FileTransferAgent

| Name  | Type    | Read-Only| Optional| Description                           |
|------|--------|----|----|-------------------------------|
| size | number | Yes | No | Size of a pre-downloaded resource after decompression, in bytes. If the value is a positive integer, the resource is successfully downloaded; if the value is **-1**, the resource fails to be downloaded.|

## NetworkInfo<sup>20+</sup>

Describes the pre-downloaded network information.

**System capability:** SystemCapability.Request.FileTransferAgent

| Name        | Type      | Read-Only| Optional| Description               |
|------------|----------|----|----|-------------------|
| dnsServers | string[] | Yes | No | List of DNS servers used when downloading resources. |
| ip<sup>23+</sup> | string | Yes | Yes | IP address of the URL when downloading resources. When DNS resolution fails, the IP is undefined. |

## PerformanceInfo<sup>20+</sup>

Describes the pre-downloaded performance information.

**System capability:** SystemCapability.Request.FileTransferAgent

| Name              | Type    | Read-Only| Optional| Description                           |
|------------------|--------|----|----|-------------------------------|
| dnsTime          | number | Yes  | No  | Time required from startup to DNS resolution completion, in milliseconds (ms).   |
| connectTime      | number | Yes  | No  | Time required from startup to TCP connection completion, in milliseconds (ms).   |
| tlsTime          | number | Yes  | No  | Time required from startup to TLS connection completion, in milliseconds (ms).   |
| firstSendTime    | number | Yes | No | Time taken from startup to sending the first byte, in milliseconds.|
| firstReceiveTime | number | Yes | No | Time taken from startup to receiving the first byte, in milliseconds.  |
| totalTime        | number | Yes | No | Time taken from startup to request completion, in milliseconds.     |
| redirectTime     | number | Yes | No | Time taken from startup to redirection completion, in milliseconds.|

## DownloadInfo<sup>20+</sup>

Describes the pre-downloaded download information.

**System capability:** SystemCapability.Request.FileTransferAgent

| Name         | Type                                   | Read-Only| Optional| Description       |
|-------------|---------------------------------------|----|----|-----------|
| resource    | [ResourceInfo](#resourceinfo20)       | Yes | No | Pre-downloaded resource information.|
| network     | [NetworkInfo](#networkinfo20)         | Yes | No | Pre-downloaded network information.|
| performance | [PerformanceInfo](#performanceinfo20) | Yes | No | Pre-downloaded performance information.|

## DownloadError<sup>23+</sup>

Describes the error message returned when a pre-download error occurs.

**System capability:** SystemCapability.Request.FileTransferAgent

| Name         | Type                                   | Read-Only| Optional| Description       |
|-------------|---------------------------------------|----|----|-----------|
| errorCode    | [ErrorCode](#errorcode23)       | Yes | No | Specific error type returned by the pre-download error callback.|
| message     | string         | Yes | No | Error message. A [universal error code](../../reference/errorcode-universal.md) or [HTTP error code](../../reference/apis-network-kit/errorcode-net-http.md) is returned.|

## cacheDownload.download

download(url: string, options: CacheDownloadOptions): void

Downloads a task from a specified URL. If the transfer is successful, the data is downloaded to the memory cache and file cache.

- After automatically decompressing during HTTP transmission, the size of the target resource cannot exceed 20971520 bytes (20 MB). Otherwise, the resource fails to store in the memory cache or file cache.

- When downloading cached data, the cache refresh behavior is determined by **cacheStrategy**: when the FORCE (default) strategy is used, if cached content already exists under the URL, the new cached content overwrites the old cached content; when the LAZY strategy is used, the cache is updated only when no cache exists.

- In addition, the system determines whether to store the target resource in a specified location based on each cache type's size limit in **cacheDownload**. By default, the LRU mode is used to replace the existing cached data.

- This API returns the result synchronously, without blocking the calling thread.

**Required permissions:** ohos.permission.INTERNET

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters**

| Name    | Type                                                        | Mandatory| Description                            |
|---------|------------------------------------------------------------|----|--------------------------------|
| url     | string                                                     | Yes | URL of the target resource. HTTP and HTTPS are supported. The URL length cannot exceed 8192 bytes.|
| options | [CacheDownloadOptions](#cachedownloadoptions) | Yes | Cache download options for the target resource.                  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code   | Error Message                                                                                                                                     |
|----------|-------------------------------------------------------------------------------------------------------------------------------------------|
| 201      | permission denied.                                                                                                              |
| 401      | parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**:

  ```ts
  import { cacheDownload, BusinessError } from '@kit.BasicServicesKit';

  // Provide configuration options for the download task.
  let options: cacheDownload.CacheDownloadOptions = {
    headers: { 'Accept': 'application/json' },
    sslType: cacheDownload.SslType.TLS,
    caPath: '/path/to/ca.pem',
    cacheStrategy: cacheDownload.CacheStrategy.FORCE,
    retry: { maxRetryCount: 1 },
    timeout: {
      networkCheckTimeout: 20,
      httpTotalTimeout: 60,
    }
  };

  try {
    // Download the resource. If the download is successful, the resource will be cached to the specified file in the application memory or sandbox directory.
    cacheDownload.download("https://www.example.com", options);
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`Failed to download the resource. err code: ${err.code}, err message: ${err.message}`);
  }
  ```

## cacheDownload.cancel

cancel(url: string): void

Cancels an ongoing download task based on the URL. The saved memory cache and file cache are not affected.

- If there is no download task with the specified URL, this API does not take effect.

- When this API is used for synchronous execution, the calling thread is not blocked.

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters**

| Name | Type    | Mandatory| Description                            |
|------|--------|----|--------------------------------|
| url  | string | Yes | URL of the target resource. HTTP and HTTPS are supported. The URL length cannot exceed 8192 bytes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code   | Error Message                                                                                                                                     |
|----------|-------------------------------------------------------------------------------------------------------------------------------------------|
| 401      | parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**:

  ```ts
  import { cacheDownload, BusinessError } from '@kit.BasicServicesKit';

  // Provide configuration options for the download task.
  let options: cacheDownload.CacheDownloadOptions = {};
  
  try {
    // Download the resource. If the download is successful, the resource will be cached to the specified file in the application memory or sandbox directory.  
    cacheDownload.download("https://www.example.com", options);
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`Failed to download the resource. err code: ${err.code}, err message: ${err.message}`);
  }

  // Other service logic is omitted here.
  
  try {
    // Cancel the download task when it is not required. The cached data is not affected.
    cacheDownload.cancel("https://www.example.com");
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`Failed to cancel the task. err code: ${err.code}, err message: ${err.message}`);
  }
  ```

## cacheDownload.setMemoryCacheSize

setMemoryCacheSize(bytes: number): void

Sets the upper limit of the memory cache size for the **cacheDownload** component.

- When the cache size is adjusted using this API, the LRU (Least Recently Used) mode is used by default to clear excess cached memory cache content. When this API is used, if **bytes** is set to 0, all cached memory cache content is cleared.

- This API returns the result synchronously, without blocking the calling thread.

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters**

| Name  | Type    | Mandatory| Description                                     |
|-------|--------|----|-----------------------------------------|
| bytes | number | Yes | Cache storage limit set. The default value is 0B, the minimum value is 0, and the maximum value does not exceed 1073741824B (that is, 1GB). If bytes is set to 0, all cached memory cache content will be cleared. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code   | Error Message                                                                                                                                     |
|----------|-------------------------------------------------------------------------------------------------------------------------------------------|
| 401      | parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**:

  ```ts
  import { cacheDownload, BusinessError } from '@kit.BasicServicesKit';
  
  try {
    // Set the upper limit of the memory cache size.  
    cacheDownload.setMemoryCacheSize(10 * 1024 * 1024);
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`Failed to set memory cache size. err code: ${err.code}, err message: ${err.message}`);
  }
  ```

## cacheDownload.setFileCacheSize

setFileCacheSize(bytes: number): void

Sets the upper limit of the file cache size for the **cacheDownload** component.

- When this API is used to adjust the cache size, the LRU mode is used by default to clear redundant cached data in the file.

- If **bytes** is set to **0**, all cached files will be deleted.

- This API returns the result synchronously, without blocking the calling thread.

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
|-------|--------|----|------------------------------------------------------------|
| bytes | number | Yes | Cache storage limit set. Default value: 104857600B (100MB); minimum value: 0; maximum value: no more than 4294967296B (4GB). |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code   | Error Message                                                                                                                                     |
|----------|-------------------------------------------------------------------------------------------------------------------------------------------|
| 401      | parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**:

  ```ts
  import { cacheDownload, BusinessError } from '@kit.BasicServicesKit';
  
  try {
    // Set the upper limit of the file cache size.  
    cacheDownload.setFileCacheSize(100 * 1024 * 1024);
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`Failed to set file cache size. err code: ${err.code}, err message: ${err.message}`);
  }
  ```

> **NOTE**
​>
> * Network cache files downloaded by the **cacheDownload** module are stored in the cache directory of the application sandbox.
> * An application can use this API to clear cache files.
> * Do not modify the cache directory and files directly to avoid function exceptions.

## cacheDownload.setDownloadInfoListSize<sup>20+</sup>

setDownloadInfoListSize(size: number): void

Sets the size of the download information list.

- The download information list is used to store pre-downloaded information.

- Each pre-download generates a piece of download information with a unique URL. Only the latest download information is saved for the same URL.

- When the list size is adjusted using this API, if **size** is increased, the original information in the list remains unchanged; if **size** is decreased, the LRU (Least Recently Used) mode is used by default to clear excess cached information.

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters**

| Name | Type    | Mandatory| Description                                           |
|------|--------|----|-----------------------------------------------|
| size | number | Yes | Size of the download information list to set. Value range: [0, 8192]. The default value is 0, which means no download information is stored. An exception is thrown when the value is out of range. |

**Example**:

  ```ts
  import { cacheDownload, BusinessError } from '@kit.BasicServicesKit';
  
  try {
    // Set the size of the download information list.  
    cacheDownload.setDownloadInfoListSize(2048);
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`Failed to set download information list size. err code: ${err.code}, err message: ${err.message}`);
  }
  ```

## cacheDownload.getDownloadInfo<sup>20+</sup>

getDownloadInfo(url: string): DownloadInfo | undefined

Obtains the pre-downloaded download information based on the URL. The information is stored in the download information list in the memory and is cleared when the application exits. The pre-download information is stored in the list only after [setDownloadInfoListSize](#cachedownloadsetdownloadinfolistsize20) is called to set the list size (greater than 0). Otherwise, the default list size is 0, no download information is stored, and **getDownloadInfo** returns undefined.

- If the specified URL is found in the download information list, the latest [DownloadInfo](#downloadinfo20) corresponding to the URL is returned.

- If the specified URL cannot be found in the download information list, **undefined** is returned.

- If the download information has already cached in the URL, the new cached information will overwrite the old one.

- When the target information is stored in the memory, the existing cache data is replaced in the LRU mode.

**Required permission:** ohos.permission.GET_NETWORK_INFO

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters**

| Name| Type    | Mandatory| Description                  |
|-----|--------|----|----------------------|
| url | string | Yes | URL to query. Supports HTTP and HTTPS. The maximum length is 8192 bytes. An exception is thrown when the length limit is exceeded. |

**Return value**

| Type                                          | Description                              |
|----------------------------------------------|----------------------------------|
| [DownloadInfo](#downloadinfo20) \| undefined | Returns the download information of the corresponding URL if the operation is successful; returns **undefined** if the specified URL does not exist.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message              |
|-------|--------------------|
| 201   | permission denied. |

**Example**

  ```ts
  import { cacheDownload, BusinessError } from '@kit.BasicServicesKit';

  try {
    // Set the size of the download information list.  
    cacheDownload.setDownloadInfoListSize(2048);
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`Failed to set download information list size. err code: ${err.code}, err message: ${err.message}`);
  }

  // Provide configuration options for the download task.
  let options: cacheDownload.CacheDownloadOptions = {};
  
  try {
    // Download the resource. If the download is successful, the resource will be cached to the specified file in the application memory or sandbox directory.  
    cacheDownload.download("https://www.example.com", options);
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`Failed to download the resource. err code: ${err.code}, err message: ${err.message}`);
  }

  // Other service logic is omitted here.
  
  try {
    // Obtain the download information after the download task is complete.
    let downloadInfo = cacheDownload.getDownloadInfo("https://www.example.com");
    if (downloadInfo == undefined) {
      console.error(`CacheDownload get download info undefined.`);
    } else {
      console.info(`CacheDownload get download info : ${JSON.stringify(downloadInfo)}`);
    }
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`Failed to get download info. err code: ${err.code}, err message: ${err.message}`);
  }
  ```

## cacheDownload.clearMemoryCache<sup>23+</sup>

clearMemoryCache(): void

Clears this memory cache.

**System capability:** SystemCapability.Request.FileTransferAgent

**Example**:

```ts
import { cacheDownload } from '@kit.BasicServicesKit';
  
cacheDownload.clearMemoryCache();
```

## cacheDownload.clearFileCache<sup>23+</sup>

clearFileCache(): void

Clears this file cache.

**System capability:** SystemCapability.Request.FileTransferAgent

**Example**:

```ts
import { cacheDownload } from '@kit.BasicServicesKit';
  
cacheDownload.clearFileCache();
```

## cacheDownload.onDownloadSuccess<sup>23+</sup>

onDownloadSuccess(url: string, callback: Callback&lt;void&gt;): void

Subscribes to the pre-download completion event. This API uses an asynchronous callback. It is used together with the **offDownloadSuccess()** method. When the completion event no longer needs to be received, call **offDownloadSuccess()** to unsubscribe, so as to avoid unnecessary callback overhead.

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters**

| Name| Type    | Mandatory| Description                  |
|-----|--------|----|----------------------|
| url | string | Yes | URL of the callback to register. Both HTTP and HTTPS are supported. The maximum length of the URL string is 8192 bytes. An exception is thrown when the length limit is exceeded. |
| callback | Callback&lt;void&gt; | Yes | Callback invoked when the download succeeds. No callback parameter is provided. |

**Example**:

  ```ts
  import { cacheDownload, BusinessError } from '@kit.BasicServicesKit';
  
  try {
    const successCallback = () => {
      console.info("Succeeded in getting callback from cacheDownload");
    };
    // Subscribe to the pre-download completion events. Callback is invoked when the download is complete.
    cacheDownload.onDownloadSuccess("https://www.example.com", successCallback);
    // Download the resource. If the download is successful, the resource will be cached to the specified file in the application memory or sandbox directory.  
    cacheDownload.download("https://www.example.com", {});
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`Failed to download the resource. err code: ${err.code}, err message: ${err.message}`);
  }
  ```

## cacheDownload.onDownloadError<sup>23+</sup>

onDownloadError(url: string, callback: Callback&lt;DownloadError&gt;): void

Subscribes to the pre-download error event. This API uses an asynchronous callback. It is used together with the **offDownloadError()** method. When the error event no longer needs to be received, call **offDownloadError()** to unsubscribe, so as to avoid unnecessary callback overhead.

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters**

| Name| Type    | Mandatory| Description                  |
|-----|--------|----|----------------------|
| url | string | Yes | URL of the callback to register. Both HTTP and HTTPS are supported. The maximum length of the URL string is 8192 bytes. An exception is thrown when the length limit is exceeded. |
| callback | Callback&lt;[DownloadError](#downloaderror23)&gt; | Yes| Callback used to return the error information about the pre-download.|

**Example**:

  ```ts
  import { cacheDownload, BusinessError } from '@kit.BasicServicesKit';
  
  try {
    const errorCallback = (error: cacheDownload.DownloadError) => {
      console.error(`Error callback from cacheDownload. error code: ${error.errorCode}, error message: ${error.message}`);
    };
    // Subscribe to pre-download error events. When a download error occurs, the callback is invoked to return error information.
    cacheDownload.onDownloadError("https://www.example.com", errorCallback);
    // Download the resource. If the download is successful, the resource will be cached to the specified file in the application memory or sandbox directory.  
    cacheDownload.download("https://www.example.com", {});
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`Failed to download the resource. err code: ${err.code}, err message: ${err.message}`);
  }
  ```

## cacheDownload.offDownloadSuccess<sup>23+</sup>

offDownloadSuccess(url: string, callback?: Callback&lt;void&gt;): void

Unsubscribes from the pre-download completion event.

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters**

| Name| Type    | Mandatory| Description                  |
|-----|--------|----|----------------------|
| url | string | Yes | URL for which the callback is to be registered. Both HTTP and HTTPS are supported. The maximum length of the URL string is 8192 bytes. An exception is thrown when the length limit is exceeded. |
| callback | Callback&lt;void&gt; | No | Callback to unsubscribe. If this parameter is not specified, all completion callbacks under the URL are unsubscribed. |

**Example**:

  ```ts
  import { cacheDownload, BusinessError } from '@kit.BasicServicesKit';
  
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
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`Failed to download the resource. err code: ${err.code}, err message: ${err.message}`);
  }
  ```

## cacheDownload.offDownloadError<sup>23+</sup>

offDownloadError(url: string, callback?: Callback&lt;DownloadError&gt;): void

Unsubscribes from the pre-download error event.

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters**

| Name| Type    | Mandatory| Description                  |
|-----|--------|----|----------------------|
| url | string | Yes | URL of the callback to register. It supports HTTP and HTTPS. The maximum length of the URL string is 8192 bytes. An exception is thrown when the length limit is exceeded. |
| callback | Callback&lt;[DownloadError](#downloaderror23)&gt; | No | Callback for the error event to unsubscribe. If this parameter is not specified, all error callbacks under the URL are unsubscribed. |

**Example**:

  ```ts
  import { cacheDownload, BusinessError } from '@kit.BasicServicesKit';
  
  try {
    const errorCallback = (error: cacheDownload.DownloadError) => {
      console.error(`Error callback from cacheDownload. error code: ${error.errorCode}, error message: ${error.message}`);
    };
    // Subscribe to pre-download error events. When a download error occurs, the callback is invoked to return error information.
    cacheDownload.onDownloadError("https://www.example.com", errorCallback);
    // Unsubscribe from the pre-download error events.
    cacheDownload.offDownloadError("https://www.example.com", errorCallback);
    // Download the resource. If the download is successful, the resource will be cached to the specified file in the application memory or sandbox directory.  
    cacheDownload.download("https://www.example.com", {});
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`Failed to download the resource. err code: ${err.code}, err message: ${err.message}`);
  }
  ```

## cacheDownload.setGlobalRetryOptions

setGlobalRetryOptions(options?: RetryOptions): void

Sets the global retry options of a task. This configuration takes effect when no specific retry configuration is set for a task. The retry configuration priority is as follows: task settings > global settings > default settings.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters**

| Name| Type    | Mandatory| Description                  |
|-----|--------|----|----------------------|
| options | [RetryOptions](#retryoptions) | No  | Task retry configuration, used to customize the retry behavior of global tasks. Pass this parameter when you need to adjust policies such as the global retry count; if it is not passed, the current global retry configuration remains unchanged. |

**Example**:

  ```ts
  import { cacheDownload, BusinessError } from '@kit.BasicServicesKit';

  try {
    // Set the maximum number of retries for a task globally.
    cacheDownload.setGlobalRetryOptions({
      maxRetryCount: 1
    });
    cacheDownload.download("https://www.example.com", {});
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`Failed to download the resource. err code: ${err.code}, err message: ${err.message}`);
  }
  ```

## cacheDownload.setGlobalTimeoutOptions

setGlobalTimeoutOptions(options?: TimeoutOptions): void

Sets the global timeout options of a task. This configuration takes effect when no specific timeout configuration is set for a task. The timeout configuration priority is as follows: task settings > global settings > default settings.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters**

| Name| Type    | Mandatory| Description                  |
|-----|--------|----|----------------------|
| options | [TimeoutOptions](#timeoutoptions) | No | Task timeout configuration, used to customize the timeout behavior of global tasks. Pass this parameter when you need to adjust the global network check timeout or HTTP request timeout; if it is not passed, the current global timeout configuration remains unchanged. |

**Example**:

  ```ts
  import { cacheDownload, BusinessError } from '@kit.BasicServicesKit';
  
  try {
    // Set the global timeout options of a task.
    cacheDownload.setGlobalTimeoutOptions({
      networkCheckTimeout: 20,
      httpTotalTimeout: 60,
    });
    cacheDownload.download("https://www.example.com", {});
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`Failed to download the resource. err code: ${err.code}, err message: ${err.message}`);
  }
  ```
