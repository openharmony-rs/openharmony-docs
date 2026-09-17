# request(Upload and Download)

The **request** module provides applications with basic upload, download, and background transmission agent capabilities.

- Currently, the **request** module cannot be called in extensions.

**Since:** 6

**System capability:** 
- API version 10 and later: SystemCapability.Request.FileTransferAgent

## Modules to Import

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## Summary

### Namespaces

| Name | Description |
| --- | --- |
| [agent](arkts-basicservices-request-agent-n.md) | The request agent api. Supports "background" and "frontend" tasks as while. Though "background" and "frontend" here do not the same with process's concept. All tasks will be executed at request manager service and recorded. Background tasks is for concurrent transfer, such as caching videos for a later play. Frontend tasks is for instant transfer, such as submitting forms for a consumption bill. Background tasks use notification to tell user tasks' status information. Frontend tasks use callback to tell caller tasks' status information. Background has some automatically restore mechanism. Frontend tasks controlled by caller. Uses `multipart/form-data` in client request for upload. A `Content-Disposition: attachment; filename=&lt;filename&gt;` response from server leads to download. More details, please see the architecture documents of the request subsystem. Only front-end mode is supported in cross-platform scenarios. |

### Functions

| Name | Description |
| --- | --- |
| [download](arkts-basicservices-request-download-f.md) | Downloads a file. This API uses an asynchronous callback to return the result. |
| [downloadFile](arkts-basicservices-request-downloadfile-f.md) | Downloads a file. This API uses an asynchronous callback to return the result. HTTP is supported. You can use on('complete'&#124;'pause'&#124;'remove') to obtain the download task state, including task completion, pause, and removal. You can also use on('fail') to obtain the task download error information. |
| [download](arkts-basicservices-request-download-f.md) | Downloads a file. This API uses a promise to return the result. |
| [downloadFile](arkts-basicservices-request-downloadfile-f.md) | Downloads a file. This API uses a promise to return the result. HTTP is supported. You can use on('complete'&#124;'pause'&#124;'remove') to obtain the download task state, including task completion, pause, and removal. You can also use on('fail') to obtain the task download error information. |
| [upload](arkts-basicservices-request-upload-f.md) | Uploads a file. This API uses an asynchronous callback to return the result. |
| [uploadFile](arkts-basicservices-request-uploadfile-f.md) | Uploads a file. This API uses an asynchronous callback to return the result. HTTP is supported. You can use on('complete'&#124;'fail') to obtain the upload success or error information. |
| [upload](arkts-basicservices-request-upload-f.md) | Uploads a file. This API uses a promise to return the result. |
| [uploadFile](arkts-basicservices-request-uploadfile-f.md) | Uploads a file. This API uses a promise to return the result. HTTP is supported. You can use on('complete'&#124;'fail') to obtain the upload success or error information. |

### Interfaces

| Name | Description |
| --- | --- |
| [DownloadConfig](arkts-basicservices-request-downloadconfig-i.md) | Defines the download task configuration. |
| [DownloadInfo](arkts-basicservices-request-downloadinfo-i.md) | Defines the download task information, which is the callback parameter of the [getTaskInfo](arkts-basicservices-request-downloadtask-i.md#gettaskinfo) API. |
| [DownloadTask](arkts-basicservices-request-downloadtask-i.md) | Implements file downloads. Before using any APIs of this class, you must obtain a **DownloadTask** object, from a promise through [request.downloadFile](arkts-basicservices-request-downloadfile-f.md) or from a callback through [request.downloadFile](arkts-basicservices-request-downloadfile-f.md). |
| [File](arkts-basicservices-request-file-i.md) | Describes the list of files in [UploadConfig](arkts-basicservices-request-uploadconfig-i.md). |
| [RequestData](arkts-basicservices-request-requestdata-i.md) | Describes the form data in [UploadConfig](arkts-basicservices-request-uploadconfig-i.md). |
| [UploadConfig](arkts-basicservices-request-uploadconfig-i.md) | Describes the configuration of an upload task. |
| [TaskState](arkts-basicservices-request-taskstate-i.md) | Upload task information, which is the callback parameter of the on('complete' &#124; 'fail') and off('complete' &#124; 'fail') APIs. |
| [UploadTask](arkts-basicservices-request-uploadtask-i.md) | Implements file uploads. Before using any APIs of this class, you must obtain an **UploadTask** object, from a promise through [request.uploadFile](arkts-basicservices-request-uploadfile-f.md) or from a callback through [request.uploadFile](arkts-basicservices-request-uploadfile-f.md). |

### Constants

| Name | Description |
| --- | --- |
| [EXCEPTION_PERMISSION](arkts-basicservices-request-con.md#exception_permission) | (Universal error codes) Permission verification failed. |
| [EXCEPTION_PARAMCHECK](arkts-basicservices-request-con.md#exception_paramcheck) | (Universal error codes) Parameter check failed. |
| [EXCEPTION_UNSUPPORTED](arkts-basicservices-request-con.md#exception_unsupported) | (Universal error codes) The device does not support this API. |
| [EXCEPTION_FILEIO](arkts-basicservices-request-con.md#exception_fileio) | (Specific error codes) Abnormal file operation. |
| [EXCEPTION_FILEPATH](arkts-basicservices-request-con.md#exception_filepath) | (Specific error codes) Abnormal file path. |
| [EXCEPTION_SERVICE](arkts-basicservices-request-con.md#exception_service) | (Specific error codes) Abnormal service. |
| [EXCEPTION_OTHERS](arkts-basicservices-request-con.md#exception_others) | (Specific error codes) Other errors. |
| [NETWORK_MOBILE](arkts-basicservices-request-con.md#network_mobile) | (Network type) Bit flag download allowed on a mobile network. |
| [NETWORK_WIFI](arkts-basicservices-request-con.md#network_wifi) | (Network type) Bit flag download allowed on a WLAN. |
| [ERROR_CANNOT_RESUME](arkts-basicservices-request-con.md#error_cannot_resume) | (Download error codes) Failure to resume the download due to network errors. |
| [ERROR_DEVICE_NOT_FOUND](arkts-basicservices-request-con.md#error_device_not_found) | (Download error codes) Failure to find a storage device such as a memory card. |
| [ERROR_FILE_ALREADY_EXISTS](arkts-basicservices-request-con.md#error_file_already_exists) | (Download error codes) Failure to download the file because it already exists. |
| [ERROR_FILE_ERROR](arkts-basicservices-request-con.md#error_file_error) | (Download error codes) File operation failed. |
| [ERROR_HTTP_DATA_ERROR](arkts-basicservices-request-con.md#error_http_data_error) | (Download error codes) HTTP transmission failed. |
| [ERROR_INSUFFICIENT_SPACE](arkts-basicservices-request-con.md#error_insufficient_space) | (Download error codes) Insufficient storage space. |
| [ERROR_TOO_MANY_REDIRECTS](arkts-basicservices-request-con.md#error_too_many_redirects) | (Download error codes) Error caused by too many network redirections. |
| [ERROR_UNHANDLED_HTTP_CODE](arkts-basicservices-request-con.md#error_unhandled_http_code) | (Download error codes) Unidentified HTTP code. |
| [ERROR_UNKNOWN](arkts-basicservices-request-con.md#error_unknown) | (Download error codes) Unknown error. |
| [ERROR_OFFLINE](arkts-basicservices-request-con.md#error_offline) | (Download error codes) No network connection. |
| [ERROR_UNSUPPORTED_NETWORK_TYPE](arkts-basicservices-request-con.md#error_unsupported_network_type) | (Download error codes) Network type mismatch. |
| [PAUSED_QUEUED_FOR_WIFI](arkts-basicservices-request-con.md#paused_queued_for_wifi) | (Causes of download pause) Download paused and queuing for a WLAN connection because the file size exceeds the maximum value allowed for a mobile network session. |
| [PAUSED_WAITING_FOR_NETWORK](arkts-basicservices-request-con.md#paused_waiting_for_network) | (Causes of download pause) Download paused due to a network connection problem. |
| [PAUSED_WAITING_TO_RETRY](arkts-basicservices-request-con.md#paused_waiting_to_retry) | (Causes of download pause) Download paused due to network error and then retried. |
| [PAUSED_BY_USER](arkts-basicservices-request-con.md#paused_by_user) | (Causes of download pause) The user paused the session. |
| [PAUSED_UNKNOWN](arkts-basicservices-request-con.md#paused_unknown) | (Causes of download pause) Download paused due to unknown reasons. |
| [SESSION_SUCCESSFUL](arkts-basicservices-request-con.md#session_successful) | (Download task status codes) Successful download. |
| [SESSION_RUNNING](arkts-basicservices-request-con.md#session_running) | (Download task status codes) Download in progress. |
| [SESSION_PENDING](arkts-basicservices-request-con.md#session_pending) | (Download task status codes) Download pending. |
| [SESSION_PAUSED](arkts-basicservices-request-con.md#session_paused) | (Download task status codes) Download paused. |
| [SESSION_FAILED](arkts-basicservices-request-con.md#session_failed) | (Download task status codes) Download failure without retry. |
