# @ohos.request.cacheDownload (Download and Cache)
<!--Kit: Basic Services Kit-->
<!--Subsystem: Request-->
<!--Owner: @huaxin05-->
<!--Designer: @hu-kai45-->
<!--Tester: @murphy1984-->
<!--Adviser: @zhang_yixin13-->

The **request** module provides applications with the basic capabilities of file upload and download and background transfer proxy.

- The child component **cacheDownload** provides the basic capability of caching application resources in advance.

- **cacheDownload** uses the HTTP protocol to download data and caches data resources to the application memory or specified files in the application sandbox directory.

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

**System capability**: SystemCapability.Request.FileTransferAgent

| Name| Value|Description|
| -------- | -------- |-------- |
| TLS | 'TLS' | TLS.|
| TLCP | 'TLCP' | TLCP.|

## ErrorCode<sup>23+</sup>

Enumerates the specific types of returned error code.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name| Value|Description|
| -------- | -------- |-------- |
| OTHERS | 0xFF | Other types of errors that are not classified.|
| DNS | 0x00 | DNS-related errors.|
| TCP | 0x10 | TCP-related errors.|
| SSL | 0x20 | SSL-related errors.|
| HTTP | 0x30 | HTTP-related errors.|

## CacheStrategy<sup>23+</sup>

Enumerates cache update strategies.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name| Value|Description|
| -------- | -------- |-------- |
| FORCE | 0 | Forcibly updates the cache, regardless of whether the cache already exists.|
| LAZY | 1 | Updates the cache only when the cache does not exist.|

## CacheDownloadOptions

Provides configuration options for download and cache, including HTTP options, transmission options, and task options.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name  | Type    | Read-Only| Optional| Description                           |
|------|--------|----|----|-------------------------------|
| headers | Record\<string, string\> | No | Yes| Request header used by a download task during HTTP transfer.|
| sslType<sup>21+</sup> | [SslType](#ssltype21) | No | Yes| Secure communication protocol, such as TSL or TLCP. TLS is used by default. Currently, TLS and TLCP do not support two-way authentication.|
| caPath<sup>21+</sup> | string | No | Yes| CA certificate path. Currently, only the .pem certificate is supported. The CA certificate preset by the system is used by default.|
| cacheStrategy<sup>23+</sup> | [CacheStrategy](#cachestrategy23) | No | Yes| Cache update strategies, including **FORCE** or **LAZY**. The **FORCE** policy is used by default.|

## ResourceInfo<sup>20+</sup>

Describes the pre-downloaded resource information.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name  | Type    | Read-Only| Optional| Description                           |
|------|--------|----|----|-------------------------------|
| size | number | Yes | No | Size of a pre-downloaded resource after decompression. If the value is a positive integer, the resource is successfully downloaded; if the value is **-1**, the resource fails to be downloaded.|

## NetworkInfo<sup>20+</sup>

Describes the pre-downloaded network information.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name        | Type      | Read-Only| Optional| Description               |
|------------|----------|----|----|-------------------|
| dnsServers | string[] | Yes | No | DNS servers used for downloading resources.|
| ip<sup>23+</sup> | string | Yes | Yes | IP address of the URL used for downloading resources. When the DNS resolution fails, the IP address is undefined.|

## PerformanceInfo<sup>20+</sup>

Describes the pre-downloaded performance information.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name              | Type    | Read-Only| Optional| Description                           |
|------------------|--------|----|----|-------------------------------|
| dnsTime          | number | Yes | No | Time taken from DNS startup to resolution completion, in milliseconds.  |
| connectTime      | number | Yes | No | Time taken from TCP startup to connection completion, in milliseconds.  |
| tlsTime          | number | Yes | No | Time taken from TLS startup to connection completion, in milliseconds.  |
| firstSendTime    | number | Yes | No | Time taken from startup to sending the first byte, in milliseconds.|
| firstReceiveTime | number | Yes | No | Time taken from startup to receiving the first byte, in milliseconds.  |
| totalTime        | number | Yes | No | Time taken from startup to request completion, in milliseconds.     |
| redirectTime     | number | Yes | No | Time taken from startup to redirection completion, in milliseconds.|

## DownloadInfo<sup>20+</sup>

Describes the pre-downloaded download information.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name         | Type                                   | Read-Only| Optional| Description       |
|-------------|---------------------------------------|----|----|-----------|
| resource    | [ResourceInfo](#resourceinfo20)       | Yes | No | Pre-downloaded resource information.|
| network     | [NetworkInfo](#networkinfo20)         | Yes | No | Pre-downloaded network information.|
| performance | [PerformanceInfo](#performanceinfo20) | Yes | No | Pre-downloaded performance information.|

## DownloadError<sup>23+</sup>

Describes the error information returned when a pre-download error occurs.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name         | Type                                   | Read-Only| Optional| Description       |
|-------------|---------------------------------------|----|----|-----------|
| errorCode    | [ErrorCode](#errorcode23)       | Yes | No | Specific error type returned by the pre-download error callback.|
| message     | string         | Yes | No | Description of a [universal error code](../../reference/errorcode-universal.md) or [HTTP error code](../../reference/apis-network-kit/errorcode-net-http.md).|

## cacheDownload.download

download(url: string, options: CacheDownloadOptions): void

Downloads a task from a specified URL. If the transfer is successful, the data is downloaded to the memory cache and file cache.

- After automatically decompressing during HTTP transmission, the size of the target resource cannot exceed 20971520 bytes (20 MB). Otherwise, the resource fails to store in the memory cache or file cache.

- When caching the downloaded data, if the data already exists in the destination URL, the new data will overwrite the old one.

- In addition, the system determines whether to store the target resource in a specified location based on each cache type's size limit in **cacheDownload**. By default, the LRU mode is used to replace the existing cached data.

- This API uses a synchronous method and does not block the calling thread.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

| Name    | Type                                                        | Mandatory| Description                            |
|---------|------------------------------------------------------------|----|--------------------------------|
| url     | string                                                     | Yes | URL of the target resource. Only the HTTP protocol is supported. The URL length cannot exceed 8192 bytes.|
| options | [CacheDownloadOptions](#cachedownloadoptions) | Yes | Cache download options for the target resource.                  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message                                                                                                                                     |
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
  };
  
  try {
    // Download the resource. If the download is successful, the resource will be cached to the specified file in the application memory or sandbox directory. 
    cacheDownload.download("https://www.example.com", options);
  } catch (err) {
    console.error(`Failed to download the resource. err code: ${err.code}, err message: ${err.message}`);
  }
  ```

## cacheDownload.cancel

cancel(url: string): void

Cancels an ongoing download task based on the URL. The saved memory cache and file cache are not affected.

- If there is no download task with the specified URL, this API does not take effect.

- When this API is used for synchronous execution, the calling thread is not blocked.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

| Name | Type    | Mandatory| Description                            |
|------|--------|----|--------------------------------|
| url  | string | Yes | URL of the target resource. Only the HTTP protocol is supported. The URL length cannot exceed 8192 bytes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message                                                                                                                                     |
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

## cacheDownload.setMemoryCacheSize

setMemoryCacheSize(bytes: number): void

Sets the upper limit of the memory cache size for the **cacheDownload** component.

- When this API is used to adjust the cache size, the LRU mode is used by default to clear redundant cached data in the memory.

- This API uses a synchronous method and does not block the calling thread.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

| Name  | Type    | Mandatory| Description                                     |
|-------|--------|----|-----------------------------------------|
| bytes | number | Yes | Upper limit of the cache, in bytes. The default value is **0**, and the maximum value cannot exceed **1073741824** (1 GB).|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message                                                                                                                                     |
|----------|-------------------------------------------------------------------------------------------------------------------------------------------|
| 401      | parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**:

  ```ts
  import { cacheDownload, BusinessError } from '@kit.BasicServicesKit';
  
  try {
    // Set the upper limit of the memory cache size. 
    cacheDownload.setMemoryCacheSize(10 * 1024 * 1024);
  } catch (err) {
    console.error(`Failed to set memory cache size. err code: ${err.code}, err message: ${err.message}`);
  }
  ```

## cacheDownload.setFileCacheSize

setFileCacheSize(bytes: number): void

Sets the upper limit of the file cache size for the **cacheDownload** component.

- When this API is used to adjust the cache size, the LRU mode is used by default to clear redundant cached data in the file.

- If **bytes** is set to **0**, all cached files will be deleted.

- This API returns the result synchronously, without blocking the calling thread.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
|-------|--------|----|------------------------------------------------------------|
| bytes | number | Yes | Upper limit of the cache, in bytes. The default value is **104857600** (100 MB), and the maximum value is **4294967296** (4 GB).|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message                                                                                                                                     |
|----------|-------------------------------------------------------------------------------------------------------------------------------------------|
| 401      | parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**:

  ```ts
  import { cacheDownload, BusinessError } from '@kit.BasicServicesKit';
  
  try {
    // Set the upper limit of the file cache size. 
    cacheDownload.setFileCacheSize(100 * 1024 * 1024);
  } catch (err) {
    console.error(`Failed to set file cache size. err code: ${err.code}, err message: ${err.message}`);
  }
  ```

> ​**NOTE**
>
> * Network cache files downloaded by the **cacheDownload** module are stored in the cache directory of the application sandbox.
> * An application can use this API to clear cache files.
> * Do not modify the cache directory and files directly to avoid function exceptions.

## cacheDownload.setDownloadInfoListSize<sup>20+</sup>

setDownloadInfoListSize(size: number): void

Sets the size of the download information list.

- The download information list is used to store pre-downloaded information.

- Each pre-download generates a piece of download information with a unique URL. Only the latest download information is saved for the same URL.

- If the list size is increased using this API, the original information in the list remains unchanged; if the list size is decreased, the LRU mode is used by default to clear excess cached data in the list.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

| Name | Type    | Mandatory| Description                                           |
|------|--------|----|-----------------------------------------------|
| size | number | Yes | Size of the download information list. The value ranges from 0 to 8192. The default value is **0**, indicating that no download information is stored.|

**Example**:

  ```ts
  import { cacheDownload, BusinessError } from '@kit.BasicServicesKit';
  
  try {
    // Set the size of the download information list. 
    cacheDownload.setDownloadInfoListSize(2048);
  } catch (err) {
    console.error(`Failed to set download information list size. err code: ${err.code}, err message: ${err.message}`);
  }
  ```

## cacheDownload.getDownloadInfo<sup>20+</sup>

getDownloadInfo(url: string): DownloadInfo | undefined

Obtains the download information based on the URL. The download information is stored in the download information list in memory and is cleared when the application exits.

- If the specified URL is found in the download information list, the latest [DownloadInfo](#downloadinfo20) corresponding to the URL is returned.

- If the specified URL cannot be found in the download information list, **undefined** is returned.

- If the download information has already cached in the URL, the new cached information will overwrite the old one.

- When the target information is stored in the memory, the existing cache data is replaced in the LRU mode.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

| Name| Type    | Mandatory| Description                  |
|-----|--------|----|----------------------|
| url | string | Yes | URL to be queried, with a maximum length of 8192 bytes.|

**Return value**

| Type                                          | Description                              |
|----------------------------------------------|----------------------------------|
| [DownloadInfo](#downloadinfo20) \| undefined | Returns the download information of the corresponding URL if the operation is successful; returns **undefined** if the specified URL does not exist.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message              |
|-------|--------------------|
| 201   | permission denied. |

  ```ts
  import { cacheDownload, BusinessError } from '@kit.BasicServicesKit';

  try {
    // Set the size of the download information list. 
    cacheDownload.setDownloadInfoListSize(2048);
  } catch (err) {
    console.error(`Failed to set download information list size. err code: ${err.code}, err message: ${err.message}`);
  }

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
    // Obtain the download information after the download task is complete.
    let downloadInfo = cacheDownload.getDownloadInfo("https://www.example.com");
    if (downloadInfo == undefined) {
      console.info(`CacheDownload get download info undefined.`);
    } else {
      console.info(`CacheDownload get download info : ${JSON.stringify(downloadInfo)}`);
    }
  } catch (err) {
    console.error(`Failed to get download info. err code: ${err.code}, err message: ${err.message}`);
  }
  ```

## cacheDownload.clearMemoryCache<sup>23+</sup>

clearMemoryCache(): void

Clears this memory cache.

**System capability**: SystemCapability.Request.FileTransferAgent

**Example**:

```ts
import { cacheDownload } from '@kit.BasicServicesKit';
  
cacheDownload.clearMemoryCache();
```

## cacheDownload.clearFileCache<sup>23+</sup>

clearFileCache(): void

Clears this file cache.

**System capability**: SystemCapability.Request.FileTransferAgent

**Example**:

```ts
import { cacheDownload } from '@kit.BasicServicesKit';
  
cacheDownload.clearFileCache();
```

## cacheDownload.onDownloadSuccess<sup>23+</sup>

onDownloadSuccess(url: string, callback: Callback&lt;void&gt;): void

Subscribes to the pre-download completion events. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

| Name| Type    | Mandatory| Description                  |
|-----|--------|----|----------------------|
| url | string | Yes | URL to be registered, with a maximum of 8192 bytes.|
| callback | Callback&lt;void&gt; | Yes| Callback used to return the result.|

**Example**:

  ```ts
  import { cacheDownload } from '@kit.BasicServicesKit';
  
  try {
    const successCallback = () => {
      console.log("Success callback from cacheDownload");
    };
    // Subscribe to the pre-download completion events. Callback is invoked when the download is complete.
    cacheDownload.onDownloadSuccess("https://www.example.com", successCallback)
    // Download the resource. If the download is successful, the resource will be cached to the specified file in the application memory or sandbox directory. 
    cacheDownload.download("https://www.example.com", {});
  } catch (err) {
    console.error(`Failed to download the resource. err code: ${err.code}, err message: ${err.message}`);
  }
  ```

## cacheDownload.onDownloadError<sup>23+</sup>

onDownloadError(url: string, callback: Callback&lt;DownloadError&gt;): void

Subscribes to the pre-download error events. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

| Name| Type    | Mandatory| Description                  |
|-----|--------|----|----------------------|
| url | string | Yes | URL to be registered, with a maximum of 8192 bytes.|
| callback | Callback&lt;[DownloadError](#downloaderror23)&gt; | Yes| Callback used to return the error information about the pre-download.|

**Example**:

  ```ts
  import { cacheDownload } from '@kit.BasicServicesKit';
  
  try {
    const errorCallback = (error: cacheDownload.DownloadError) => {
      console.log(`Error callback from cacheDownload.error code: ${error.errorCode}, error message: ${error.message}`);
    };
    // Subscribe to pre-download error events. When a download error occurs, the callback is invoked to return error information.
    cacheDownload.onDownloadError("https://www.example.com", errorCallback)
    // Download the resource. If the download is successful, the resource will be cached to the specified file in the application memory or sandbox directory. 
    cacheDownload.download("https://www.example.com", {});
  } catch (err) {
    console.error(`Failed to download the resource. err code: ${err.code}, err message: ${err.message}`);
  }
  ```

## cacheDownload.offDownloadSuccess<sup>23+</sup>

offDownloadSuccess(url: string, callback?: Callback&lt;void&gt;): void

Unsubscribes from the pre-download completion events. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name| Type    | Mandatory| Description                  |
|-----|--------|----|----------------------|
| url | string | Yes | URL to be unregistered, with a maximum of 8192 bytes.|
| callback | Callback&lt;void&gt; | No| Callback to unregister. If this parameter is left blank, all completion callback functions of the URL are unregistered.|

**Example**:

  ```ts
  import { cacheDownload } from '@kit.BasicServicesKit';
  
  try {
    const successCallback = () => {
      console.log("Success callback from cacheDownload");
    };
    // Subscribe to the pre-download completion events. Callback is invoked when the download is complete.
    cacheDownload.onDownloadSuccess("https://www.example.com", successCallback);
    // Unsubscribes from the pre-download completion events.
    cacheDownload.offDownloadSuccess("https://www.example.com", successCallback);
    // Download the resource. If the download is successful, the resource will be cached to the specified file in the application memory or sandbox directory. 
    cacheDownload.download("https://www.example.com", {});
  } catch (err) {
    console.error(`Failed to download the resource. err code: ${err.code}, err message: ${err.message}`);
  }
  ```

## cacheDownload.offDownloadError<sup>23+</sup>

offDownloadError(url: string, callback?: Callback&lt;DownloadError&gt;): void

Unsubscribes from the pre-download error events. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

| Name| Type    | Mandatory| Description                  |
|-----|--------|----|----------------------|
| url | string | Yes | URL to be unregistered, with a maximum of 8192 bytes.|
| callback | Callback&lt;[DownloadError](#downloaderror23)&gt; | No| Callback used to return the error information about the pre-download. If this parameter is left blank, all error callback functions of the URL are unregistered.|

**Example**:

  ```ts
  import { cacheDownload } from '@kit.BasicServicesKit';
  
  try {
    const errorCallback = (error: cacheDownload.DownloadError) => {
      console.log(`Error callback from cacheDownload.error code: ${error.errorCode}, error message: ${error.message}`);
    };
    // Subscribe to pre-download error events. When a download error occurs, the callback is invoked to return error information.
    cacheDownload.onDownloadError("https://www.example.com", errorCallback);
    // Unsubscribes from the pre-download error events.
    cacheDownload.offDownloadError("https://www.example.com", errorCallback);
    // Download the resource. If the download is successful, the resource will be cached to the specified file in the application memory or sandbox directory. 
    cacheDownload.download("https://www.example.com", {});
  } catch (err) {
    console.error(`Failed to download the resource. err code: ${err.code}, err message: ${err.message}`);
  }
  ```
