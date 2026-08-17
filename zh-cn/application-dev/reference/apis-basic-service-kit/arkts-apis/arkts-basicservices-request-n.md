# request

request模块给应用提供上传下载文件、后台代理传输的基础功能。 - request暂不支持在Extension中调用。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace request--><!--Device-unnamed-declare namespace request-End-->

**系统能力：** 
- API版本10+：SystemCapability.Request.FileTransferAgent

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [agent](arkts-basicservices-request-agent-n.md) | The request agent api. Supports "background" and "frontend" tasks as while. Though "background" and "frontend" here do not the same with process's concept. All tasks will be executed at request manager service and recorded. Background tasks is for concurrent transfer, such as caching videos for a later play. Frontend tasks is for instant transfer, such as submitting forms for a consumption bill. Background tasks use notification to tell user tasks' status information. Frontend tasks use callback to tell caller tasks' status information. Background has some automatically restore mechanism. Frontend tasks controlled by caller. Uses `multipart/form-data` in client request for upload. A `Content-Disposition: attachment; filename=&lt;filename&gt;` response from server leads to download. More details, please see the architecture documents of the request subsystem. Only front-end mode is supported in cross-platform scenarios. |

### 函数

| 名称 | 说明 |
| --- | --- |
| [download](arkts-basicservices-request-download-f.md#download) | 创建并启动一个下载任务，使用callback异步回调。 |
| [downloadFile](arkts-basicservices-request-downloadfile-f.md#downloadfile) | 创建并启动一个下载任务，使用callback异步回调，支持HTTP协议。通过 on('complete'\|'pause'\|'remove') 可获取任务下载时的状态信息，包括任务完成、暂停或移除。通过 on('fail')可获取任务下载时的错误信息。 |
| [download](arkts-basicservices-request-download-f.md#download) | 创建并启动一个下载任务，使用Promise异步回调。 |
| [downloadFile](arkts-basicservices-request-downloadfile-f.md#downloadfile) | 创建并启动一个下载任务，使用Promise异步回调，支持HTTP协议。通过 on('complete'\|'pause'\|'remove') 可以获取任务下载时的状态信息，包括任务完成、暂停或移除。通过 on('fail')可以获取任务下载时的错误信息。 |
| [upload](arkts-basicservices-request-upload-f.md#upload) | 创建并启动一个上传任务，使用callback异步回调。 |
| [uploadFile](arkts-basicservices-request-uploadfile-f.md#uploadfile) | 创建并启动一个上传任务，使用callback异步回调，支持HTTP协议。通过 [on('complete'\|'fail')](arkts-basicservices-request-uploadtask-i.md#onprogress) 可获取任务上传时的成功信息或错误信息。 |
| [upload](arkts-basicservices-request-upload-f.md#upload) | 创建并启动一个上传任务，使用Promise异步回调。 |
| [uploadFile](arkts-basicservices-request-uploadfile-f.md#uploadfile) | 创建并启动一个上传任务，使用Promise异步回调，支持HTTP协议。通过 [on('complete'\|'fail')](arkts-basicservices-request-uploadtask-i.md#onprogress) 可获取任务上传时的成功信息或错误信息。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [DownloadConfig](arkts-basicservices-request-downloadconfig-i.md) | 下载任务的配置信息。 |
| [DownloadInfo](arkts-basicservices-request-downloadinfo-i.md) | 下载任务信息，[getTaskInfo](arkts-basicservices-request-downloadtask-i.md#gettaskinfo)接口的回调参数。 |
| [DownloadTask](arkts-basicservices-request-downloadtask-i.md) | 下载任务，使用下列方法前，需要先获取DownloadTask对象，promise形式通过 [request.downloadFile](arkts-basicservices-request-downloadfile-f.md#downloadfile)获取，callback形式通过 [request.downloadFile](arkts-basicservices-request-downloadfile-f.md#downloadfile) 获取。 |
| [File](arkts-basicservices-request-file-i.md) | [UploadConfig](arkts-basicservices-request-uploadconfig-i.md#uploadconfig)中的文件列表。 |
| [RequestData](arkts-basicservices-request-requestdata-i.md) | [UploadConfig](arkts-basicservices-request-uploadconfig-i.md#uploadconfig)中的表单数据。 |
| [UploadConfig](arkts-basicservices-request-uploadconfig-i.md) | 上传任务的配置信息。 |
| [TaskState](arkts-basicservices-request-taskstate-i.md) | 上传任务的任务信息，是 [on('complete' \| 'fail')](arkts-basicservices-request-uploadtask-i.md#onprogress) 和 [off('complete' \| 'fail')](arkts-basicservices-request-uploadtask-i.md#offprogress) 接口的回调参数。 |
| [UploadTask](arkts-basicservices-request-uploadtask-i.md) | 上传任务，使用下列方法前，需要先获取UploadTask对象，promise形式通过 [request.uploadFile](arkts-basicservices-request-uploadfile-f.md#uploadfile)获取，callback形式通过 [request.uploadFile](arkts-basicservices-request-uploadfile-f.md#uploadfile) 获取。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [DownloadProgressCallback](arkts-basicservices-request-downloadprogresscallback-t.md) | The callback function for the download progress event. |
| [DownloadCompleteCallback](arkts-basicservices-request-downloadcompletecallback-t.md) | The callback function for the download complete event. |
| [DownloadPauseCallback](arkts-basicservices-request-downloadpausecallback-t.md) | The callback function for the download pause event. |
| [DownloadRemoveCallback](arkts-basicservices-request-downloadremovecallback-t.md) | The callback function for the download remove event. |
| [DownloadFailCallback](arkts-basicservices-request-downloadfailcallback-t.md) | The callback function for the download fail event. <br>The value should be an integer. |
| [UploadProgressCallback](arkts-basicservices-request-uploadprogresscallback-t.md) | The callback function for the download progress event. |
| [UploadHeaderReceiveCallback](arkts-basicservices-request-uploadheaderreceivecallback-t.md) | The callback function for the HTTP Response Header event. |

### 常量

| 名称 | 说明 |
| --- | --- |
| [EXCEPTION_PERMISSION](arkts-basicservices-request-con.md#exceptionpermission) | 通用错误码：权限校验失败。 |
| [EXCEPTION_PARAMCHECK](arkts-basicservices-request-con.md#exceptionparamcheck) | 通用错误码：参数检查失败。 |
| [EXCEPTION_UNSUPPORTED](arkts-basicservices-request-con.md#exceptionunsupported) | 通用错误码：该设备不支持此API。 |
| [EXCEPTION_FILEIO](arkts-basicservices-request-con.md#exceptionfileio) | 特有错误码：文件操作异常。 |
| [EXCEPTION_FILEPATH](arkts-basicservices-request-con.md#exceptionfilepath) | 特有错误码：文件路径异常。 |
| [EXCEPTION_SERVICE](arkts-basicservices-request-con.md#exceptionservice) | 特有错误码：服务异常。 |
| [EXCEPTION_OTHERS](arkts-basicservices-request-con.md#exceptionothers) | 特有错误码：其他错误。 |
| [NETWORK_MOBILE](arkts-basicservices-request-con.md#networkmobile) | 网络类型：使用蜂窝网络时允许下载的位标志。 |
| [NETWORK_WIFI](arkts-basicservices-request-con.md#networkwifi) | 网络类型：使用WLAN时允许下载的位标志。 |
| [ERROR_CANNOT_RESUME](arkts-basicservices-request-con.md#errorcannotresume) | 下载任务错误码：网络原因导致恢复下载失败。 |
| [ERROR_DEVICE_NOT_FOUND](arkts-basicservices-request-con.md#errordevicenotfound) | 下载任务错误码：找不到SD卡等存储设备。 |
| [ERROR_FILE_ALREADY_EXISTS](arkts-basicservices-request-con.md#errorfilealreadyexists) | 下载任务错误码：要下载的文件已存在，下载会话无法覆盖现有文件。 |
| [ERROR_FILE_ERROR](arkts-basicservices-request-con.md#errorfileerror) | 下载任务错误码：文件操作失败。 |
| [ERROR_HTTP_DATA_ERROR](arkts-basicservices-request-con.md#errorhttpdataerror) | 下载任务错误码：HTTP传输失败。 |
| [ERROR_INSUFFICIENT_SPACE](arkts-basicservices-request-con.md#errorinsufficientspace) | 下载任务错误码：存储空间不足。 |
| [ERROR_TOO_MANY_REDIRECTS](arkts-basicservices-request-con.md#errortoomanyredirects) | 下载任务错误码：网络重定向过多导致的错误。 |
| [ERROR_UNHANDLED_HTTP_CODE](arkts-basicservices-request-con.md#errorunhandledhttpcode) | 下载任务错误码：无法识别的HTTP代码。 |
| [ERROR_UNKNOWN](arkts-basicservices-request-con.md#errorunknown) | 下载任务错误码：未知错误。 例如：API version 12及以下版本，系统仅支持串行地尝试连接域名相关IP，不支持单个IP的连接时间控制。若DNS返回的首个IP被阻塞，可能会由于握手超时导致ERROR_UNKNOWN错误。 |
| [ERROR_OFFLINE](arkts-basicservices-request-con.md#erroroffline) | 下载任务错误码：网络未连接。 |
| [ERROR_UNSUPPORTED_NETWORK_TYPE](arkts-basicservices-request-con.md#errorunsupportednetworktype) | 下载任务错误码：网络类型不匹配。 |
| [PAUSED_QUEUED_FOR_WIFI](arkts-basicservices-request-con.md#pausedqueuedforwifi) | 下载任务暂停原因：文件大小超过了使用蜂窝网络会话允许的最大值，下载被暂停并等待WLAN连接。 |
| [PAUSED_WAITING_FOR_NETWORK](arkts-basicservices-request-con.md#pausedwaitingfornetwork) | 下载任务暂停原因：网络问题导致下载暂停。 例如：网络断开。 |
| [PAUSED_WAITING_TO_RETRY](arkts-basicservices-request-con.md#pausedwaitingtoretry) | 下载任务暂停原因：网络错误导致下载会话将被重试。 |
| [PAUSED_BY_USER](arkts-basicservices-request-con.md#pausedbyuser) | 下载任务暂停原因：用户暂停会话。 |
| [PAUSED_UNKNOWN](arkts-basicservices-request-con.md#pausedunknown) | 下载任务暂停原因：未知原因导致暂停下载。 |
| [SESSION_SUCCESSFUL](arkts-basicservices-request-con.md#sessionsuccessful) | 下载任务状态码：下载会话已完成。 |
| [SESSION_RUNNING](arkts-basicservices-request-con.md#sessionrunning) | 下载任务状态码：下载会话正在进行中。 |
| [SESSION_PENDING](arkts-basicservices-request-con.md#sessionpending) | 下载任务状态码：下载会话正在被调度中。 |
| [SESSION_PAUSED](arkts-basicservices-request-con.md#sessionpaused) | 下载任务状态码：下载会话已暂停。 |
| [SESSION_FAILED](arkts-basicservices-request-con.md#sessionfailed) | 下载任务状态码：下载会话已失败，将不会重试。 |

