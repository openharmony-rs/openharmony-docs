# @ohos.request.cacheDownload

request部件主要给应用提供上传下载文件、后台传输代理的基础能力。

- request的cacheDownload子组件主要给应用提供应用资源提前缓存的基础能力。
- cacheDownload组件使用HTTP协议进行数据下载，并将数据资源缓存至应用内存或应用沙箱目录的指定文件中。
- 这些缓存数据可以被特定的ArkUI组件（例如：Image组件）使用，从而提升资源加载效率。请查看ArkUI组件文档确定组件是否支持该功能。

**起始版本：** 18

**系统能力：** SystemCapability.Request.FileTransferAgent

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [cancel](arkts-basicservices-cachedownload-cancel-f.md#cancel-1) | 根据url移除一个正在执行的缓存下载任务，已保存的内存缓存和文件缓存不会受到影响。<br/><br/>- 当不存在对应url的任务时无其他效果。<br/>- 使用该方法同步执行时，不阻塞调用线程。<br/> |
| [clearFileCache](arkts-basicservices-cachedownload-clearfilecache-f.md#clearFileCache-1) | 清除保存下载内容的文件缓存。<br/> |
| [clearMemoryCache](arkts-basicservices-cachedownload-clearmemorycache-f.md#clearMemoryCache-1) | 清除缓存下载内容的内存缓存。<br/> |
| [download](arkts-basicservices-cachedownload-download-f.md#download-1) | 启动一个缓存下载任务，若传输成功，则将数据下载到内存缓存和文件缓存中。<br/><br/>- 目标资源经过HTTP传输自动解压后的大小不能超过20971520B（即20MB），否则不会保存到内存缓存或文件缓存中。<br/>- 在缓存下载数据时，如果在该url下已存在缓存内容，新的缓存内容会覆盖旧缓存内容。<br/>- 目标资源在存储到内存缓存或文件缓存中时，依照缓存下载组件的各类型缓存大小上限决定文件是否存储到指定位置，并默认使用“LRU”（最近最少使用）方式替换已有缓存内容。<br/>- 该方法为同步方法，不阻塞调用线程。<br/> |
| [getDownloadInfo](arkts-basicservices-cachedownload-getdownloadinfo-f.md#getDownloadInfo-1) | 基于url获取预下载的下载信息。信息存储在内存中的下载信息列表，当应用程序退出时清除。<br/><br/>- 如果下载信息列表中能够找到指定url，返回该url对应的最新[DownloadInfo](arkts-basicservices-cachedownload-downloadinfo-i.md#DownloadInfo)。<br/>- 如果下载信息列表中找不到指定url，返回undefined。<br/>- 在缓存下载信息时，如果在该url下已存在缓存信息，新的缓存内容会覆盖旧缓存。<br/>- 目标信息在存储到内存时，使用“LRU”（最近最少使用）方式替换已存在的缓存数据。<br/> |
| [offDownloadError](arkts-basicservices-cachedownload-offdownloaderror-f.md#offDownloadError-1) | 取消订阅预下载的错误事件。使用callback异步回调。<br/> |
| [offDownloadSuccess](arkts-basicservices-cachedownload-offdownloadsuccess-f.md#offDownloadSuccess-1) | 取消订阅预下载的完成事件。使用callback异步回调。<br/> |
| [onDownloadError](arkts-basicservices-cachedownload-ondownloaderror-f.md#onDownloadError-1) | 订阅预下载的错误事件。使用callback异步回调。<br/> |
| [onDownloadSuccess](arkts-basicservices-cachedownload-ondownloadsuccess-f.md#onDownloadSuccess-1) | 订阅预下载的完成事件。使用callback异步回调。<br/> |
| [setDownloadInfoListSize](arkts-basicservices-cachedownload-setdownloadinfolistsize-f.md#setDownloadInfoListSize-1) | 设置下载信息列表的大小。<br/><br/>- 下载信息列表用于存储预下载信息。<br/>- 下载信息和url一一对应，每次预下载都会生成一个下载信息，相同url下只会保存最新的下载信息。<br/>- 使用该接口调整列表大小时，size更新增大，列表中原有的信息不变，更新减小，默认使用“LRU”（最近最少使用）方式清除多余的已缓存信息。<br/> |
| [setFileCacheSize](arkts-basicservices-cachedownload-setfilecachesize-f.md#setFileCacheSize-1) | 设置缓存下载组件能够保存的文件缓存的上限。<br/><br/>- 使用该接口调整缓存大小时，默认使用“LRU”（最近最少使用）方式清除多余的已缓存的文件缓存内容。<br/>- 使用该接口时，若bytes设置为0，将会删除所有缓存文件。<br/>- 该方法为同步方法，不会阻塞调用线程。<br/> |
| [setGlobalRetryOptions](arkts-basicservices-cachedownload-setglobalretryoptions-f.md#setGlobalRetryOptions-1) | Sets retry options for all tasks.<br/>Used when task-specific retry configuration is not configured.<br/> |
| [setGlobalTimeoutOptions](arkts-basicservices-cachedownload-setglobaltimeoutoptions-f.md#setGlobalTimeoutOptions-1) | Sets timeout configuration for all tasks.<br/>Used when task-specific timeout configuration is not configured.<br/> |
| [setMemoryCacheSize](arkts-basicservices-cachedownload-setmemorycachesize-f.md#setMemoryCacheSize-1) | 设置缓存下载组件能够保存的内存缓存上限。<br/><br/>- 使用该接口调整缓存大小时，默认使用“LRU”（最近最少使用）方式清除多余的已缓存的内存缓存内容。<br/>- 该方法为同步方法，不阻塞调用线程。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CacheDownloadOptions](arkts-basicservices-cachedownload-cachedownloadoptions-i.md) | 缓存下载的配置选项。包括HTTP选项、传输选项和任务选项。<br/> |
| [DownloadError](arkts-basicservices-cachedownload-downloaderror-i.md) | 预下载错误回调的返回信息。<br/> |
| [DownloadInfo](arkts-basicservices-cachedownload-downloadinfo-i.md) | 预下载的下载信息。<br/> |
| [NetworkInfo](arkts-basicservices-cachedownload-networkinfo-i.md) | 预下载的网络信息。<br/> |
| [PerformanceInfo](arkts-basicservices-cachedownload-performanceinfo-i.md) | 预下载的性能信息。<br/> |
| [ResourceInfo](arkts-basicservices-cachedownload-resourceinfo-i.md) | 预下载的资源信息。<br/> |
| [RetryOptions](arkts-basicservices-cachedownload-retryoptions-i.md) | Task retry configuration.<br/> |
| [TimeoutOptions](arkts-basicservices-cachedownload-timeoutoptions-i.md) | Task timeout configuration.<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CacheStrategy](arkts-basicservices-cachedownload-cachestrategy-e.md) | 表示缓存刷新策略的枚举。<br/> |
| [ErrorCode](arkts-basicservices-cachedownload-errorcode-e.md) | 表示错误返回信息的特定类型枚举。<br/> |
| [SslType](arkts-basicservices-cachedownload-ssltype-e.md) | 表示安全通信协议的枚举。<br/> |

