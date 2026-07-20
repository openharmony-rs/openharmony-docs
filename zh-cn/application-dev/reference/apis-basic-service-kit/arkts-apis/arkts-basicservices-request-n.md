# request

request模块给应用提供上传下载文件、后台代理传输的基础功能。

- request暂不支持在Extension中调用。

**起始版本：** 6

<!--Device-unnamed-declare namespace request--><!--Device-unnamed-declare namespace request-End-->

**系统能力：** 
- API版本10+：SystemCapability.Request.FileTransferAgent

## 导入模块

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [agent](arkts-basicservices-request-agent-n.md) | The request agent api.Supports "background" and "frontend" tasks as while.Though "background" and "frontend" here do not the same with process's concept.All tasks will be executed at request manager service and recorded.Background tasks is for concurrent transfer, such as caching videos for a later play.Frontend tasks is for instant transfer, such as submitting forms for a consumption bill.Background tasks use notification to tell user tasks' status information.Frontend tasks use callback to tell caller tasks' status information.Background has some automatically restore mechanism.Frontend tasks controlled by caller.Uses `multipart/form-data` in client request for upload.A `Content-Disposition: attachment; filename=<filename>` response from server leads to download.More details, please see the architecture documents of the request subsystem.Only front-end mode is supported in cross-platform scenarios. |

### 函数

| 名称 | 说明 |
| --- | --- |
| [download](arkts-basicservices-request-download-f.md#download) | 创建并启动一个下载任务，使用callback异步回调。 |
| [downloadFile](arkts-basicservices-request-downloadfile-f.md#downloadfile) | 创建并启动一个下载任务，使用callback异步回调，支持HTTP协议。通过[on('complete'\|'pause'\|'remove')](request.DownloadTask.on(type: 'complete' \| 'pause' \| 'remove', callback: () => void))可获取任务下载时的状态信息，包括任务完成、暂停或移除。通过[on('fail')](request.DownloadTask.on(type: 'fail', callback: (err: int) => void))可获取任务下载时的错误信息。 |
| [download](arkts-basicservices-request-download-f.md#download-1) | 创建并启动一个下载任务，使用Promise异步回调。 |
| [downloadFile](arkts-basicservices-request-downloadfile-f.md#downloadfile-1) | 创建并启动一个下载任务，使用Promise异步回调，支持HTTP协议。通过[on('complete'\|'pause'\|'remove')](request.DownloadTask.on(type: 'complete' \| 'pause' \| 'remove', callback: () => void))可以获取任务下载时的状态信息，包括任务完成、暂停或移除。通过[on('fail')](request.DownloadTask.on(type: 'fail', callback: (err: int) => void))可以获取任务下载时的错误信息。 |
| [upload](arkts-basicservices-request-upload-f.md#upload) | 创建并启动一个上传任务，使用callback异步回调。 |
| [uploadFile](arkts-basicservices-request-uploadfile-f.md#uploadfile) | 创建并启动一个上传任务，使用callback异步回调，支持HTTP协议。通过[on('complete'\|'fail')](request.UploadTask.on(type: 'complete' \| 'fail', callback: Callback<Array<TaskState>>))可获取任务上传时的成功信息或错误信息。 |
| [upload](arkts-basicservices-request-upload-f.md#upload-1) | 创建并启动一个上传任务，使用Promise异步回调。 |
| [uploadFile](arkts-basicservices-request-uploadfile-f.md#uploadfile-1) | 创建并启动一个上传任务，使用Promise异步回调，支持HTTP协议。通过[on('complete'\|'fail')](request.UploadTask.on(type: 'complete' \| 'fail', callback: Callback<Array<TaskState>>))可获取任务上传时的成功信息或错误信息。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [DownloadConfig](arkts-basicservices-request-downloadconfig-i.md) | 下载任务的配置信息。 |
| [DownloadInfo](arkts-basicservices-request-downloadinfo-i.md) | 下载任务信息，[getTaskInfo](arkts-basicservices-request-downloadtask-i.md#gettaskinfo-1)接口的回调参数。 |
| [DownloadTask](arkts-basicservices-request-downloadtask-i.md) | 下载任务，使用下列方法前，需要先获取DownloadTask对象，promise形式通过[request.downloadFile](arkts-basicservices-request-downloadfile-f.md#downloadfile-1)获取，callback形式通过[request.downloadFile](arkts-basicservices-request-downloadfile-f.md#downloadfile-1)获取。 |
| [File](arkts-basicservices-request-file-i.md) | [UploadConfig](arkts-basicservices-request-uploadconfig-i.md)中的文件列表。 |
| [RequestData](arkts-basicservices-request-requestdata-i.md) | [UploadConfig](arkts-basicservices-request-uploadconfig-i.md)中的表单数据。 |
| [UploadConfig](arkts-basicservices-request-uploadconfig-i.md) | 上传任务的配置信息。 |
| [TaskState](arkts-basicservices-request-taskstate-i.md) | 上传任务的任务信息，是[on('complete' \| 'fail')](request.UploadTask.on(type: 'complete' \| 'fail', callback: Callback<Array<TaskState>>))和[off('complete' \| 'fail')](request.UploadTask.off(type: 'complete' \| 'fail', callback?: Callback<Array<TaskState>>))接口的回调参数。 |
| [UploadTask](arkts-basicservices-request-uploadtask-i.md) | 上传任务，使用下列方法前，需要先获取UploadTask对象，promise形式通过[request.uploadFile](arkts-basicservices-request-uploadfile-f.md#uploadfile-1)获取，callback形式通过[request.uploadFile](arkts-basicservices-request-uploadfile-f.md#uploadfile-1)获取。 |

### 常量

| 名称 | 说明 |
| --- | --- |
| [EXCEPTION_PERMISSION](arkts-basicservices-request-con.md#exception_permission) | 通用错误码：权限校验失败。 |
| [EXCEPTION_PARAMCHECK](arkts-basicservices-request-con.md#exception_paramcheck) | 通用错误码：参数检查失败。 |
| [EXCEPTION_UNSUPPORTED](arkts-basicservices-request-con.md#exception_unsupported) | 通用错误码：该设备不支持此API。 |
| [EXCEPTION_FILEIO](arkts-basicservices-request-con.md#exception_fileio) | 特有错误码：文件操作异常。 |
| [EXCEPTION_FILEPATH](arkts-basicservices-request-con.md#exception_filepath) | 特有错误码：文件路径异常。 |
| [EXCEPTION_SERVICE](arkts-basicservices-request-con.md#exception_service) | 特有错误码：服务异常。 |
| [EXCEPTION_OTHERS](arkts-basicservices-request-con.md#exception_others) | 特有错误码：其他错误。 |
| [NETWORK_MOBILE](arkts-basicservices-request-con.md#network_mobile) | 网络类型：使用蜂窝网络时允许下载的位标志。 |
| [NETWORK_WIFI](arkts-basicservices-request-con.md#network_wifi) | 网络类型：使用WLAN时允许下载的位标志。 |
| [ERROR_CANNOT_RESUME](arkts-basicservices-request-con.md#error_cannot_resume) | 下载任务错误码：网络原因导致恢复下载失败。 |
| [ERROR_DEVICE_NOT_FOUND](arkts-basicservices-request-con.md#error_device_not_found) | 下载任务错误码：找不到SD卡等存储设备。 |
| [ERROR_FILE_ALREADY_EXISTS](arkts-basicservices-request-con.md#error_file_already_exists) | 下载任务错误码：要下载的文件已存在，下载会话无法覆盖现有文件。 |
| [ERROR_FILE_ERROR](arkts-basicservices-request-con.md#error_file_error) | 下载任务错误码：文件操作失败。 |
| [ERROR_HTTP_DATA_ERROR](arkts-basicservices-request-con.md#error_http_data_error) | 下载任务错误码：HTTP传输失败。 |
| [ERROR_INSUFFICIENT_SPACE](arkts-basicservices-request-con.md#error_insufficient_space) | 下载任务错误码：存储空间不足。 |
| [ERROR_TOO_MANY_REDIRECTS](arkts-basicservices-request-con.md#error_too_many_redirects) | 下载任务错误码：网络重定向过多导致的错误。 |
| [ERROR_UNHANDLED_HTTP_CODE](arkts-basicservices-request-con.md#error_unhandled_http_code) | 下载任务错误码：无法识别的HTTP代码。 |
| [ERROR_UNKNOWN](arkts-basicservices-request-con.md#error_unknown) | 下载任务错误码：未知错误。  例如：API version 12及以下版本，系统仅支持串行地尝试连接域名相关IP，不支持单个IP的连接时间控制。若DNS返回的首个IP被阻塞，可能会由于握手超时导致ERROR_UNKNOWN错误。 |
| [ERROR_OFFLINE](arkts-basicservices-request-con.md#error_offline) | 下载任务错误码：网络未连接。 |
| [ERROR_UNSUPPORTED_NETWORK_TYPE](arkts-basicservices-request-con.md#error_unsupported_network_type) | 下载任务错误码：网络类型不匹配。 |
| [PAUSED_QUEUED_FOR_WIFI](arkts-basicservices-request-con.md#paused_queued_for_wifi) | 下载任务暂停原因：文件大小超过了使用蜂窝网络会话允许的最大值，下载被暂停并等待WLAN连接。 |
| [PAUSED_WAITING_FOR_NETWORK](arkts-basicservices-request-con.md#paused_waiting_for_network) | 下载任务暂停原因：网络问题导致下载暂停。  例如：网络断开。 |
| [PAUSED_WAITING_TO_RETRY](arkts-basicservices-request-con.md#paused_waiting_to_retry) | 下载任务暂停原因：网络错误导致下载会话将被重试。 |
| [PAUSED_BY_USER](arkts-basicservices-request-con.md#paused_by_user) | 下载任务暂停原因：用户暂停会话。 |
| [PAUSED_UNKNOWN](arkts-basicservices-request-con.md#paused_unknown) | 下载任务暂停原因：未知原因导致暂停下载。 |
| [SESSION_SUCCESSFUL](arkts-basicservices-request-con.md#session_successful) | 下载任务状态码：下载会话已完成。 |
| [SESSION_RUNNING](arkts-basicservices-request-con.md#session_running) | 下载任务状态码：下载会话正在进行中。 |
| [SESSION_PENDING](arkts-basicservices-request-con.md#session_pending) | 下载任务状态码：下载会话正在被调度中。 |
| [SESSION_PAUSED](arkts-basicservices-request-con.md#session_paused) | 下载任务状态码：下载会话已暂停。 |
| [SESSION_FAILED](arkts-basicservices-request-con.md#session_failed) | 下载任务状态码：下载会话已失败，将不会重试。 |

