# @ohos.request.cacheDownload(缓存下载)

request部件主要给应用提供上传下载文件、后台传输代理的基础能力。

- request的cacheDownload子组件主要给应用提供应用资源提前缓存的基础能力。  
- cacheDownload组件使用HTTP协议进行数据下载，并将数据资源缓存至应用内存或应用沙箱目录的指定文件中。  
- 这些缓存数据可以被特定的ArkUI组件（例如：Image组件）使用，从而提升资源加载效率。请查看ArkUI组件文档确定组件是否支持该功能。

**起始版本：** 18

**系统能力：** SystemCapability.Request.FileTransferAgent

## 导入模块

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [cancel](arkts-basicservices-cachedownload-cancel-f.md) | 根据url移除一个正在执行的缓存下载任务，已保存的内存缓存和文件缓存不会受到影响。 |
| [clearFileCache](arkts-basicservices-cachedownload-clearfilecache-f.md) | 清除保存下载内容的文件缓存。 |
| [clearMemoryCache](arkts-basicservices-cachedownload-clearmemorycache-f.md) | 清除缓存下载内容的内存缓存。 |
| [download](arkts-basicservices-cachedownload-download-f.md) | 启动一个缓存下载任务，若传输成功，则将数据下载到内存缓存和文件缓存中。 |
| [getDownloadInfo](arkts-basicservices-cachedownload-getdownloadinfo-f.md) | 基于url获取预下载的下载信息。信息存储在内存中的下载信息列表，当应用程序退出时清除。 |
| [offDownloadError](arkts-basicservices-cachedownload-offdownloaderror-f.md) | 取消订阅预下载的错误事件。使用callback异步回调。 |
| [offDownloadSuccess](arkts-basicservices-cachedownload-offdownloadsuccess-f.md) | 取消订阅预下载的完成事件。使用callback异步回调。 |
| [onDownloadError](arkts-basicservices-cachedownload-ondownloaderror-f.md) | 订阅预下载的错误事件。使用callback异步回调。 |
| [onDownloadSuccess](arkts-basicservices-cachedownload-ondownloadsuccess-f.md) | 订阅预下载的完成事件。使用callback异步回调。 |
| [setDownloadInfoListSize](arkts-basicservices-cachedownload-setdownloadinfolistsize-f.md) | 设置下载信息列表的大小。 |
| [setFileCacheSize](arkts-basicservices-cachedownload-setfilecachesize-f.md) | 设置缓存下载组件能够保存的文件缓存的上限。 |
| [setGlobalRetryOptions](arkts-basicservices-cachedownload-setglobalretryoptions-f.md) | Sets retry options for all tasks. Used when task-specific retry configuration is not configured. |
| [setGlobalTimeoutOptions](arkts-basicservices-cachedownload-setglobaltimeoutoptions-f.md) | Sets timeout configuration for all tasks. Used when task-specific timeout configuration is not configured. |
| [setMemoryCacheSize](arkts-basicservices-cachedownload-setmemorycachesize-f.md) | 设置缓存下载组件能够保存的内存缓存上限。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CacheDownloadOptions](arkts-basicservices-cachedownload-cachedownloadoptions-i.md) | 缓存下载的配置选项。包括HTTP选项、传输选项和任务选项。 |
| [DownloadError](arkts-basicservices-cachedownload-downloaderror-i.md) | 预下载错误回调的返回信息。 |
| [DownloadInfo](arkts-basicservices-cachedownload-downloadinfo-i.md) | 预下载的下载信息。 |
| [NetworkInfo](arkts-basicservices-cachedownload-networkinfo-i.md) | 预下载的网络信息。 |
| [PerformanceInfo](arkts-basicservices-cachedownload-performanceinfo-i.md) | 预下载的性能信息。 |
| [ResourceInfo](arkts-basicservices-cachedownload-resourceinfo-i.md) | 预下载的资源信息。 |
| [RetryOptions](arkts-basicservices-cachedownload-retryoptions-i.md) | Task retry configuration. |
| [TimeoutOptions](arkts-basicservices-cachedownload-timeoutoptions-i.md) | Task timeout configuration. |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CacheStrategy](arkts-basicservices-cachedownload-cachestrategy-e.md) | 表示缓存刷新策略的枚举。 |
| [ErrorCode](arkts-basicservices-cachedownload-errorcode-e.md) | 表示错误返回信息的特定类型枚举。 |
| [SslType](arkts-basicservices-cachedownload-ssltype-e.md) | 表示安全通信协议的枚举。 |
