# request

request模块给应用提供上传下载文件、后台代理传输的基础功能。

- request暂不支持在Extension中调用。

**起始版本：** 6

**系统能力：** SystemCapability.Request.FileTransferAgent

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [agent](arkts-basicservices-request-agent-n.md) | The request agent api.<br/>Supports "background" and "frontend" tasks as while.<br/>Though "background" and "frontend" here do not the same with process's concept.<br/>All tasks will be executed at request manager service and recorded.<br/>Background tasks is for concurrent transfer, such as caching videos for a later play.<br/>Frontend tasks is for instant transfer, such as submitting forms for a consumption bill.<br/>Background tasks use notification to tell user tasks' status information.<br/>Frontend tasks use callback to tell caller tasks' status information.<br/>Background has some automatically restore mechanism.<br/>Frontend tasks controlled by caller.<br/>Uses `multipart/form-data` in client request for upload.<br/>A `Content-Disposition: attachment; filename=&lt;filename&gt;` response from server leads to download.<br/>More details, please see the architecture documents of the request subsystem.<br/>Only front-end mode is supported in cross-platform scenarios.<br/> |

### 函数

| 名称 | 说明 |
| --- | --- |
| [download](arkts-basicservices-request-download-f.md#download-1) | 创建并启动一个下载任务，使用callback异步回调。<br/> |
| [downloadFile](arkts-basicservices-request-downloadfile-f.md#downloadFile-1) | 创建并启动一个下载任务，使用callback异步回调，支持HTTP协议。通过<br/>[on('complete'\|'pause'\|'remove')](request.DownloadTask.on(type: 'complete' \| 'pause' \| 'remove', callback: () =&gt; void))<br/>可获取任务下载时的状态信息，包括任务完成、暂停或移除。通过<br/>[on('fail')](request.DownloadTask.on(type: 'fail', callback: (err: int) =&gt; void))可获取任务下载时的错误信息。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../../application-models/uiability-usage.md#获取uiability的上下文信息)。<br/> |
| [download](arkts-basicservices-request-download-f.md#download-2) | 创建并启动一个下载任务，使用Promise异步回调。<br/> |
| [downloadFile](arkts-basicservices-request-downloadfile-f.md#downloadFile-2) | 创建并启动一个下载任务，使用Promise异步回调，支持HTTP协议。通过<br/>[on('complete'\|'pause'\|'remove')](request.DownloadTask.on(type: 'complete' \| 'pause' \| 'remove', callback: () =&gt; void))<br/>可以获取任务下载时的状态信息，包括任务完成、暂停或移除。通过<br/>[on('fail')](request.DownloadTask.on(type: 'fail', callback: (err: int) =&gt; void))可以获取任务下载时的错误信息。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../../application-models/uiability-usage.md#获取uiability的上下文信息)。<br/> |
| [upload](arkts-basicservices-request-upload-f.md#upload-1) | 创建并启动一个上传任务，使用callback异步回调。<br/> |
| [uploadFile](arkts-basicservices-request-uploadfile-f.md#uploadFile-1) | 创建并启动一个上传任务，使用callback异步回调，支持HTTP协议。通过<br/>[on('complete'\|'fail')](request.UploadTask.on(type: 'complete' \| 'fail', callback: Callback&lt;Array&lt;TaskState&gt;&gt;))<br/>可获取任务上传时的成功信息或错误信息。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../../application-models/uiability-usage.md#获取uiability的上下文信息)。<br/> |
| [upload](arkts-basicservices-request-upload-f.md#upload-2) | 创建并启动一个上传任务，使用Promise异步回调。<br/> |
| [uploadFile](arkts-basicservices-request-uploadfile-f.md#uploadFile-2) | 创建并启动一个上传任务，使用Promise异步回调，支持HTTP协议。通过<br/>[on('complete'\|'fail')](request.UploadTask.on(type: 'complete' \| 'fail', callback: Callback&lt;Array&lt;TaskState&gt;&gt;))<br/>可获取任务上传时的成功信息或错误信息。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../../application-models/uiability-usage.md#获取uiability的上下文信息)。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [DownloadConfig](arkts-basicservices-request-downloadconfig-i.md) | 下载任务的配置信息。<br/> |
| [DownloadInfo](arkts-basicservices-request-downloadinfo-i.md) | 下载任务信息，[getTaskInfo](arkts-basicservices-request-downloadtask-i.md#getTaskInfo-2)接口的回调参数。<br/> |
| [DownloadTask](arkts-basicservices-request-downloadtask-i.md) | 下载任务，使用下列方法前，需要先获取DownloadTask对象，promise形式通过<br/>[request.downloadFile](arkts-basicservices-request-downloadfile-f.md#downloadFile-2)获取，callback形式通过<br/>[request.downloadFile](request.downloadFile(context: BaseContext, config: DownloadConfig, callback: AsyncCallback&lt;DownloadTask&gt;))<br/>获取。<br/> |
| [File](arkts-basicservices-request-file-i.md) | [UploadConfig](arkts-basicservices-request-uploadconfig-i.md#UploadConfig)中的文件列表。<br/> |
| [RequestData](arkts-basicservices-request-requestdata-i.md) | [UploadConfig](arkts-basicservices-request-uploadconfig-i.md#UploadConfig)中的表单数据。<br/> |
| [UploadConfig](arkts-basicservices-request-uploadconfig-i.md) | 上传任务的配置信息。<br/> |
| [TaskState](arkts-basicservices-request-taskstate-i.md) | 上传任务的任务信息，是<br/>[on('complete' \| 'fail')](request.UploadTask.on(type: 'complete' \| 'fail', callback: Callback&lt;Array&lt;TaskState&gt;&gt;))<br/>和<br/>[off('complete' \| 'fail')](request.UploadTask.off(type: 'complete' \| 'fail', callback?: Callback&lt;Array&lt;TaskState&gt;&gt;))<br/>接口的回调参数。<br/> |
| [UploadTask](arkts-basicservices-request-uploadtask-i.md) | 上传任务，使用下列方法前，需要先获取UploadTask对象，promise形式通过<br/>[request.uploadFile](arkts-basicservices-request-uploadfile-f.md#uploadFile-2)获取，callback形式通过<br/>[request.uploadFile](request.uploadFile(context: BaseContext, config: UploadConfig, callback: AsyncCallback&lt;UploadTask&gt;))<br/>获取。<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |

### 常量

| 名称 | 说明 |
| --- | --- |
| [EXCEPTION_PERMISSION](arkts-basicservices-request-con.md#EXCEPTION_PERMISSION) | 通用错误码：权限校验失败。<br/> |
| [EXCEPTION_PARAMCHECK](arkts-basicservices-request-con.md#EXCEPTION_PARAMCHECK) | 通用错误码：参数检查失败。<br/> |
| [EXCEPTION_UNSUPPORTED](arkts-basicservices-request-con.md#EXCEPTION_UNSUPPORTED) | 通用错误码：该设备不支持此API。<br/> |
| [EXCEPTION_FILEIO](arkts-basicservices-request-con.md#EXCEPTION_FILEIO) | 特有错误码：文件操作异常。<br/> |
| [EXCEPTION_FILEPATH](arkts-basicservices-request-con.md#EXCEPTION_FILEPATH) | 特有错误码：文件路径异常。<br/> |
| [EXCEPTION_SERVICE](arkts-basicservices-request-con.md#EXCEPTION_SERVICE) | 特有错误码：服务异常。<br/> |
| [EXCEPTION_OTHERS](arkts-basicservices-request-con.md#EXCEPTION_OTHERS) | 特有错误码：其他错误。<br/> |
| [NETWORK_MOBILE](arkts-basicservices-request-con.md#NETWORK_MOBILE) | 网络类型：使用蜂窝网络时允许下载的位标志。<br/> |
| [NETWORK_WIFI](arkts-basicservices-request-con.md#NETWORK_WIFI) | 网络类型：使用WLAN时允许下载的位标志。<br/> |
| [ERROR_CANNOT_RESUME](arkts-basicservices-request-con.md#ERROR_CANNOT_RESUME) | 下载任务错误码：网络原因导致恢复下载失败。<br/> |
| [ERROR_DEVICE_NOT_FOUND](arkts-basicservices-request-con.md#ERROR_DEVICE_NOT_FOUND) | 下载任务错误码：找不到SD卡等存储设备。<br/> |
| [ERROR_FILE_ALREADY_EXISTS](arkts-basicservices-request-con.md#ERROR_FILE_ALREADY_EXISTS) | 下载任务错误码：要下载的文件已存在，下载会话无法覆盖现有文件。<br/> |
| [ERROR_FILE_ERROR](arkts-basicservices-request-con.md#ERROR_FILE_ERROR) | 下载任务错误码：文件操作失败。<br/> |
| [ERROR_HTTP_DATA_ERROR](arkts-basicservices-request-con.md#ERROR_HTTP_DATA_ERROR) | 下载任务错误码：HTTP传输失败。<br/> |
| [ERROR_INSUFFICIENT_SPACE](arkts-basicservices-request-con.md#ERROR_INSUFFICIENT_SPACE) | 下载任务错误码：存储空间不足。<br/> |
| [ERROR_TOO_MANY_REDIRECTS](arkts-basicservices-request-con.md#ERROR_TOO_MANY_REDIRECTS) | 下载任务错误码：网络重定向过多导致的错误。<br/> |
| [ERROR_UNHANDLED_HTTP_CODE](arkts-basicservices-request-con.md#ERROR_UNHANDLED_HTTP_CODE) | 下载任务错误码：无法识别的HTTP代码。<br/> |
| [ERROR_UNKNOWN](arkts-basicservices-request-con.md#ERROR_UNKNOWN) | 下载任务错误码：未知错误。<br/><br/>例如：API version 12及以下版本，系统仅支持串行地尝试连接域名相关IP，不支持单个IP的连接时间控制。若DNS返回的首个IP被阻塞，可能会由于握手超时导致ERROR_UNKNOWN错误。<br/> |
| [ERROR_OFFLINE](arkts-basicservices-request-con.md#ERROR_OFFLINE) | 下载任务错误码：网络未连接。<br/> |
| [ERROR_UNSUPPORTED_NETWORK_TYPE](arkts-basicservices-request-con.md#ERROR_UNSUPPORTED_NETWORK_TYPE) | 下载任务错误码：网络类型不匹配。<br/> |
| [PAUSED_QUEUED_FOR_WIFI](arkts-basicservices-request-con.md#PAUSED_QUEUED_FOR_WIFI) | 下载任务暂停原因：文件大小超过了使用蜂窝网络会话允许的最大值，下载被暂停并等待WLAN连接。<br/> |
| [PAUSED_WAITING_FOR_NETWORK](arkts-basicservices-request-con.md#PAUSED_WAITING_FOR_NETWORK) | 下载任务暂停原因：网络问题导致下载暂停。<br/><br/>例如：网络断开。<br/> |
| [PAUSED_WAITING_TO_RETRY](arkts-basicservices-request-con.md#PAUSED_WAITING_TO_RETRY) | 下载任务暂停原因：网络错误导致下载会话将被重试。<br/> |
| [PAUSED_BY_USER](arkts-basicservices-request-con.md#PAUSED_BY_USER) | 下载任务暂停原因：用户暂停会话。<br/> |
| [PAUSED_UNKNOWN](arkts-basicservices-request-con.md#PAUSED_UNKNOWN) | 下载任务暂停原因：未知原因导致暂停下载。<br/> |
| [SESSION_SUCCESSFUL](arkts-basicservices-request-con.md#SESSION_SUCCESSFUL) | 下载任务状态码：下载会话已完成。<br/> |
| [SESSION_RUNNING](arkts-basicservices-request-con.md#SESSION_RUNNING) | 下载任务状态码：下载会话正在进行中。<br/> |
| [SESSION_PENDING](arkts-basicservices-request-con.md#SESSION_PENDING) | 下载任务状态码：下载会话正在被调度中。<br/> |
| [SESSION_PAUSED](arkts-basicservices-request-con.md#SESSION_PAUSED) | 下载任务状态码：下载会话已暂停。<br/> |
| [SESSION_FAILED](arkts-basicservices-request-con.md#SESSION_FAILED) | 下载任务状态码：下载会话已失败，将不会重试。<br/> |

