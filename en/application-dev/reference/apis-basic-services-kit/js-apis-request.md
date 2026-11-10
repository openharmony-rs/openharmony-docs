# @ohos.request (Upload and Download)
<!--Kit: Basic Services Kit-->
<!--Subsystem: Request-->
<!--Owner: @huaxin05-->
<!--Designer: @hu-kai45-->
<!--Tester: @liuhaonan2-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=993d7fa9ac4c0d7493b85f23ab2697e1d42331cb translatedAt=2026-11-10T04:14:41.073Z pushedAt=2026-11-10T07:03:29.376Z nl=1 -->

The request module provides applications with basic capabilities for uploading and downloading files and for background agent transfer. It supports the HTTP/HTTPS protocols and provides capabilities such as task progress monitoring, resumable transfer, background task management, and network type selection. It is applicable to scenarios such as in-app file upload and download and continuous background transfer.

- request does not support being called in an Extension.

> **NOTE**
>
> The initial APIs of this module are supported since API version 6. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import


```js
import { request } from '@kit.BasicServicesKit';
```

## Constants

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> **Network type**: Download supports custom network types, which can be configured to the following network types through networkType in [DownloadConfig](#downloadconfig).<br>
>
> **Download task error code**: The value of the error parameter of the callback of the download [on('fail')](#onfail7) event, and the value of the failedReason field of the return value of [getTaskInfo](#gettaskinfo9).<br>
>
> **Download task pause reason**: The value of the pausedReason field of the return value of the download-related [getTaskInfo](#gettaskinfo9).<br>
>
> **Download task status code**: The value of the status field of the return value of the download-related [getTaskInfo](#gettaskinfo9).

| Name | Type | Value | Description |
| -------- | -------- | -------- | -------- |
| EXCEPTION_PERMISSION<sup>9+</sup> | number |   201   | Common error code: permission verification failed. |
| EXCEPTION_PARAMCHECK<sup>9+</sup> | number |   401   | Common error code: parameter check failed. |
| EXCEPTION_UNSUPPORTED<sup>9+</sup> | number |   801   | Common error code: this API is not supported on the device. |
| EXCEPTION_FILEIO<sup>9+</sup> | number |   13400001   | Specific error code: file operation exception. For details, see the method about how to handle error 13400001. |
| EXCEPTION_FILEPATH<sup>9+</sup> | number |   13400002   | Specific error code: file path exception. |
| EXCEPTION_SERVICE<sup>9+</sup> | number |   13400003   | Specific error code: service exception. |
| EXCEPTION_OTHERS<sup>9+</sup> | number |   13499999   | Specific error code: other errors. |
| NETWORK_MOBILE | number | 0x00000001 | Network type: bit flag indicating that download is allowed when a cellular network is used. |
| NETWORK_WIFI | number | 0x00010000 | Network type: bit flag indicating that download is allowed when WLAN is used. |
| ERROR_CANNOT_RESUME<sup>7+</sup> | number |   0   | Download task error code: resuming the download failed due to a network issue. |
| ERROR_DEVICE_NOT_FOUND<sup>7+</sup> | number |   1   | Download task error code: a storage device such as an SD card cannot be found. |
| ERROR_FILE_ALREADY_EXISTS<sup>7+</sup> | number |   2   | Download task error code: the file to be downloaded already exists, and the download session cannot overwrite the existing file. |
| ERROR_FILE_ERROR<sup>7+</sup> | number |   3   | Download task error code: file operation failed. |
| ERROR_HTTP_DATA_ERROR<sup>7+</sup> | number |   4   | Download task error code: HTTP transfer failed. |
| ERROR_INSUFFICIENT_SPACE<sup>7+</sup> | number |   5   | Download task error code: insufficient storage space. |
| ERROR_TOO_MANY_REDIRECTS<sup>7+</sup> | number |   6   | Download task error code: error caused by too many network redirects. |
| ERROR_UNHANDLED_HTTP_CODE<sup>7+</sup> | number |   7   | Download task error code: unrecognized HTTP code. |
| ERROR_UNKNOWN<sup>7+</sup> | number |   8   | Download task error code: unknown error.<br>For example, in API version 12 and earlier, the system only supports serially attempting to connect to the IPs related to a domain name, and does not support connection time control for a single IP. If the first IP returned by DNS is blocked, ERROR_UNKNOWN may occur due to a handshake timeout. For details, see the method about how to handle the ERROR_UNKNOWN error. |
| ERROR_OFFLINE<sup>9+</sup> | number |   9   | Download task error code: the network is not connected. |
| ERROR_UNSUPPORTED_NETWORK_TYPE<sup>9+</sup> | number |   10   | Download task error code: the network type does not match. |
| PAUSED_QUEUED_FOR_WIFI<sup>7+</sup> | number |   0   | Download task pause reason: the file size exceeds the maximum value allowed for a cellular network session, so the download is paused and waits for a WLAN connection. |
| PAUSED_WAITING_FOR_NETWORK<sup>7+</sup> | number |   1   | Download task pause reason: the download is paused due to a network issue.<br>For example, the network is disconnected. |
| PAUSED_WAITING_TO_RETRY<sup>7+</sup> | number |   2   | Download task pause reason: the download session will be retried due to a network error. |
| PAUSED_BY_USER<sup>9+</sup> | number |   3   | Download task pause reason: the user paused the session. |
| PAUSED_UNKNOWN<sup>7+</sup> | number |   4   | Download task pause reason: the download is paused for an unknown reason. |
| SESSION_SUCCESSFUL<sup>7+</sup> | number |   0   | Download task status code: the download session is complete. |
| SESSION_RUNNING<sup>7+</sup> | number |   1   | Download task status code: the download session is in progress. |
| SESSION_PENDING<sup>7+</sup> | number |   2   | Download task status code: the download session is being scheduled. |
| SESSION_PAUSED<sup>7+</sup> | number |   3   | Download task status code: the download session is paused. |
| SESSION_FAILED<sup>7+</sup> | number |   4   | Download task status code: the download session has failed and will not be retried. |


## request.uploadFile<sup>9+</sup>

uploadFile(context: BaseContext, config: UploadConfig): Promise&lt;UploadTask&gt;

Creates and starts an upload task. This API uses a promise to return the result asynchronously and supports the HTTP protocol. You can use [on('complete' | 'fail')](#oncomplete--fail9) to obtain the success information or error information of the upload task.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Upload

> **NOTE**
>
> For details about how to obtain the **context** in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | context | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes | Context based on the application. |
  | config | [UploadConfig](#uploadconfig) | Yes | Upload configurations. |


**Return value**

  | Type | Description |
  | -------- | -------- |
  | Promise&lt;[UploadTask](#uploadtask)&gt; | Promise used to return the upload task **UploadTask** asynchronously. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | The permissions check fails. |
  | 401 | The parameters check fails. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |
  | 13400002 | File path not supported or invalid. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';
  
  // Obtain the context in the component to ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let uploadTask: request.UploadTask;
  let uploadConfig: request.UploadConfig = {
    url: 'http://www.example.com', // Manually replace the URL with the HTTP address of the real server.
    header: { 'Accept': '*/*' },
    method: 'POST',
    files: [{ filename: 'test', name: 'test', uri: 'internal://cache/test.jpg', type: 'image/jpeg' }], // It is recommended that type be set to the MIME type defined in the HTTP protocol.
    data: [{ name: 'name123', value: '123' }],
  };
  try {
    request.uploadFile(context, uploadConfig).then((data: request.UploadTask) => {
      uploadTask = data;
    }).catch((err: BusinessError) => {
      console.error(`Failed to request the upload. Code: ${err.code}, message: ${err.message}`);
    });
  } catch (err) {
    console.error(`Failed to request the upload. Code: ${err.code}, message: ${err.message}`);
  }
  ```


## request.uploadFile<sup>9+</sup>

uploadFile(context: BaseContext, config: UploadConfig, callback: AsyncCallback&lt;UploadTask&gt;): void

Creates and starts an upload task. This API uses an asynchronous callback to return the result and supports the HTTP protocol. You can obtain the success or error information of the upload task through [on('complete' | 'fail')](#oncomplete--fail9).

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Upload

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | context | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes | Context based on the application. |
  | config | [UploadConfig](#uploadconfig) | Yes | Upload configurations. |
  | callback | AsyncCallback&lt;[UploadTask](#uploadtask)&gt; | Yes | Callback function used to asynchronously return the UploadTask object. If the upload succeeds, **err** is **undefined** and **data** is the obtained UploadTask object; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | The permissions check fails. |
  | 401 | The parameters check fails. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |
  | 13400002 | File path not supported or invalid. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let uploadTask: request.UploadTask;
  let uploadConfig: request.UploadConfig = {
    url: 'http://www.example.com', // Manually replace the URL with the HTTP address of the real server.
    header: { 'Accept': '*/*' },
    method: 'POST',
    files: [{ filename: 'test', name: 'test', uri: 'internal://cache/test.jpg', type: 'image/jpeg' }], // It is recommended that type be set to a MIME type defined in the HTTP protocol.
    data: [{ name: 'name123', value: '123' }],
  };
  try {
    request.uploadFile(context, uploadConfig, (err: BusinessError, data: request.UploadTask) => {
      if (err) {
        console.error(`Failed to request the upload. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      uploadTask = data;
    });
  } catch (err) {
    console.error(`Failed to request the upload. Code: ${err.code}, message: ${err.message}`);
  }
  ```

## request.upload<sup>(deprecated)</sup>

upload(config: UploadConfig): Promise&lt;UploadTask&gt;

Creates and starts an upload task. This API uses a promise to return the result asynchronously.

**Model restriction**: This API can be used only in the FA model.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Upload

> **NOTE**
>
> This API has been supported since API version 6 and deprecated since API version 9. You are advised to use [request.uploadFile](#requestuploadfile9) instead.

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | config | [UploadConfig](#uploadconfig) | Yes | Upload configurations. |

**Return value**

  | Type | Description |
  | -------- | -------- |
  | Promise&lt;[UploadTask](#uploadtask)&gt; | Promise used to return the upload task object asynchronously. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | The permissions check fails. |

**Example**

  ```js
  let uploadTask: request.UploadTask;
  let uploadConfig: request.UploadConfig = {
    url: 'http://www.example.com', // Replace the URL with the actual HTTP address of the real server.
    header: { 'Accept': '*/*' },
    method: 'POST',
    files: [{ filename: 'test', name: 'test', uri: 'internal://cache/test.jpg', type: 'image/jpeg' }], // Set type to a MIME type that complies with the HTTP protocol.
    data: [{ name: 'name123', value: '123' }],
  };
  request.upload(uploadConfig).then((data: request.UploadTask) => {
    uploadTask = data;
  }).catch((err: BusinessError) => {
    console.error(`Failed to request the upload. Code: ${err.code}, message: ${err.message}`);
  });
  ```


## request.upload<sup>(deprecated)</sup>

upload(config: UploadConfig, callback: AsyncCallback&lt;UploadTask&gt;): void

Creates and starts an upload task. This API uses an asynchronous callback to return the result.

**Model restriction**: This API can be used only in the FA model.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Upload

> **NOTE**
>
> This API has been supported since API version 6 and deprecated since API version 9. You are advised to use [request.uploadFile](#requestuploadfile9) instead.

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | config | [UploadConfig](#uploadconfig) | Yes | Upload configurations. |
  | callback | AsyncCallback&lt;[UploadTask](#uploadtask)&gt; | Yes | Callback used to return the UploadTask object. If the upload succeeds, err is undefined and data is the obtained UploadTask object; otherwise, err is an error object. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | The permissions check fails. |

**Example**

  ```js
  let uploadTask: request.UploadTask;
  let uploadConfig: request.UploadConfig = {
    url: 'http://www.example.com', // Manually replace the URL with the HTTP address of the real server.
    header: { 'Accept': '*/*' },
    method: 'POST',
    files: [{ filename: 'test', name: 'test', uri: 'internal://cache/test.jpg', type: 'image/jpeg' }], // It is recommended that type be set to a MIME type defined in the HTTP protocol.
    data: [{ name: 'name123', value: '123' }],
  };
  request.upload(uploadConfig, (err: BusinessError, data: request.UploadTask) => {
    if (err) {
      console.error(`Failed to request the upload. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    uploadTask = data;
  });
  ```

## UploadTask

Upload task. Before using the following methods, you need to obtain an UploadTask object. In Promise form, obtain it through [request.uploadFile](#requestuploadfile9); in callback form, obtain it through [request.uploadFile](#requestuploadfile9-1).



### on('progress')

on(type: 'progress', callback: (uploadedSize: number, totalSize: number) =&gt; void): void

Subscribes to the upload task progress event. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.Upload

> **NOTE**
>
> When the application is running in the background, this API cannot be called for callbacks to meet the power consumption and performance requirements.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| type | string | Yes | Type of the event to subscribe to. The value is 'progress', which indicates the upload progress information. The event is triggered when the task progress changes. |
| callback | (uploadedSize: number, totalSize: number) => void | Yes | Callback invoked to return the upload task progress, including the size of the uploaded file and the total size of the file to upload, in bytes (B). |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | The parameters check fails. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed.<br> Applicable version: 12+ |

**Example**

<!--code_no_check-->
  ```ts
  let upProgressCallback = (uploadedSize: number, totalSize: number) => {
    console.info("upload totalSize:" + totalSize + "  uploadedSize:" + uploadedSize);
  };
  uploadTask.on('progress', upProgressCallback);
  ```


### on('headerReceive')<sup>7+</sup>

on(type: 'headerReceive', callback:  (header: object) =&gt; void): void

Subscribes to the HTTP response event of an upload task. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.Upload

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | type | string | Yes | Type of the event to subscribe to.<br>- The value is 'headerReceive', which is triggered when the HTTP request receives a response. |
  | callback | (header: object) => void | Yes | Callback invoked when the HTTP&nbsp;Response event occurs, returning the response content. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | The parameters check fails. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed.<br> Applicable version: 12+ |

**Example**

<!--code_no_check-->
  ```ts
  let headerCallback = (headers: object) => {
    console.info("upOnHeader headers:" + JSON.stringify(headers));
  };
  uploadTask.on('headerReceive', headerCallback);
  ```


### on('complete' | 'fail')<sup>9+</sup>

 on(type: 'complete' | 'fail', callback: Callback&lt;Array&lt;TaskState&gt;&gt;): void

Subscribes to the upload task completion or failure event. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.Upload

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | type | string | Yes | Type of the event to subscribe to. Supported events include:`'complete'`\|`'fail'`. <br>\- `'complete'`: indicates that the upload task is complete. This event is triggered when the task is complete. <br>\- `'fail'`: indicates that the upload task fails. This event is triggered when the task fails.|
  | callback | Callback&lt;Array&lt;[TaskState](#taskstate9)&gt;&gt; | Yes | Callback invoked to return the task state information when the upload task is complete or fails. |


**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | The parameters check fails. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed.<br> Applicable version: 12+ |

**Example**

<!--code_no_check-->
  ```ts
  let upCompleteCallback = (taskStates: Array<request.TaskState>) => {
    for (let i = 0; i < taskStates.length; i++) {
      console.info("upOnComplete taskState:" + JSON.stringify(taskStates[i]));
    }
  };
  uploadTask.on('complete', upCompleteCallback);

  let upFailCallback = (taskStates: Array<request.TaskState>) => {
    for (let i = 0; i < taskStates.length; i++) {
      console.info("upOnFail taskState:" + JSON.stringify(taskStates[i]));
    }
  };
  uploadTask.on('fail', upFailCallback);
  ```


### off('progress')

off(type:  'progress',  callback?: (uploadedSize: number, totalSize: number) =&gt;  void): void

Unsubscribes from the upload task progress event.

**System capability**: SystemCapability.MiscServices.Upload

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | type | string | Yes | Type of the event to unsubscribe from.<br>- The value is 'progress', indicating the upload progress information. |
  | callback | (uploadedSize: number, totalSize: number) => void | No | Callback for the upload progress event. If this parameter is not specified, all callbacks of the current type are unsubscribed from. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | The parameters check fails. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed.<br> Applicable version: 12+ |

**Example**

<!--code_no_check-->
  ```ts
  let upProgressCallback1 = (uploadedSize: number, totalSize: number) => {
    console.info('Upload delete progress notification.' + 'totalSize:' + totalSize + 'uploadedSize:' + uploadedSize);
  };
  let upProgressCallback2 = (uploadedSize: number, totalSize: number) => {
    console.info('Upload delete progress notification.' + 'totalSize:' + totalSize + 'uploadedSize:' + uploadedSize);
  };
  uploadTask.on('progress', upProgressCallback1);
  uploadTask.on('progress', upProgressCallback2);
  // Unsubscribe from upProgressCallback1.
  uploadTask.off('progress', upProgressCallback1);
  // Unsubscribe from all callbacks of the upload task progress event.
  uploadTask.off('progress');
  ```


### off('headerReceive')<sup>7+</sup>

off(type: 'headerReceive', callback?: (header: object) =&gt; void): void

Unsubscribes from the HTTP response event of an upload task.

**System capability**: SystemCapability.MiscServices.Upload

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | type | string | Yes | Type of the event to unsubscribe from.<br>- The value is 'headerReceive', which indicates that the HTTP request has received a response. |
  | callback | (header: object) => void | No | Callback for the event to unsubscribe from. If this parameter is not specified, all callbacks of the current type are unsubscribed from. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | The parameters check fails. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed.<br> Applicable version: 12+ |

**Example**

<!--code_no_check-->
  ```ts
  let headerCallback1 = (header: object) => {
    console.info(`Upload delete headerReceive notification. header: ${JSON.stringify(header)}`);
  };
  let headerCallback2 = (header: object) => {
    console.info(`Upload delete headerReceive notification. header: ${JSON.stringify(header)}`);
  };
  uploadTask.on('headerReceive', headerCallback1);
  uploadTask.on('headerReceive', headerCallback2);
  // Unsubscribe from headerCallback1.
  uploadTask.off('headerReceive', headerCallback1);
  // Unsubscribe from all callbacks of the upload task HTTP header event.
  uploadTask.off('headerReceive');
  ```

### off('complete' | 'fail')<sup>9+</sup>

 off(type: 'complete' | 'fail', callback?: Callback&lt;Array&lt;TaskState&gt;&gt;): void

Unsubscribes from the completion or failure event of an upload task.

**System capability**: SystemCapability.MiscServices.Upload

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | type | string | Yes | Type of the event to unsubscribe from.<br>- The value 'complete' indicates the completion of the upload task.<br>- The value 'fail' indicates the failure of the upload task.|
  | callback | Callback&lt;Array&lt;[TaskState](#taskstate9)&gt;&gt; | No | Callback for the event to unsubscribe from. If this parameter is not specified, all callbacks of the current type are unsubscribed from. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | The parameters check fails. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed.<br> Applicable version: 12+ |

**Example**

<!--code_no_check-->
  ```ts
  let upCompleteCallback1 = (taskStates: Array<request.TaskState>) => {
    console.info('Upload delete complete notification.');
    for (let i = 0; i < taskStates.length; i++) {
      console.info('taskState:' + JSON.stringify(taskStates[i]));
    }
  };
  let upCompleteCallback2 = (taskStates: Array<request.TaskState>) => {
    console.info('Upload delete complete notification.');
    for (let i = 0; i < taskStates.length; i++) {
      console.info('taskState:' + JSON.stringify(taskStates[i]));
    }
  };
  uploadTask.on('complete', upCompleteCallback1);
  uploadTask.on('complete', upCompleteCallback2);
  // Unsubscribe from upCompleteCallback1.
  uploadTask.off('complete', upCompleteCallback1);
  // Unsubscribe from all callbacks for the completion of the upload task.
  uploadTask.off('complete');

  let upFailCallback1 = (taskStates: Array<request.TaskState>) => {
    console.info('Upload delete fail notification.');
    for (let i = 0; i < taskStates.length; i++) {
      console.info('taskState:' + JSON.stringify(taskStates[i]));
    }
  };
  let upFailCallback2 = (taskStates: Array<request.TaskState>) => {
    console.info('Upload delete fail notification.');
    for (let i = 0; i < taskStates.length; i++) {
      console.info('taskState:' + JSON.stringify(taskStates[i]));
    }
  };
  uploadTask.on('fail', upFailCallback1);
  uploadTask.on('fail', upFailCallback2);
  // Unsubscribe from upFailCallback1.
  uploadTask.off('fail', upFailCallback1);
  // Unsubscribe from all callbacks for the failure of the upload task.
  uploadTask.off('fail');
  ```

### delete<sup>9+</sup>
delete(): Promise&lt;boolean&gt;

Removes the upload task. This API uses a promise to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Upload

> **NOTE**
>
> Since there is no scenario that returns error 401, the error code `401 the parameters check fails` is removed in API version 12.

**Return value**

  | Type | Description |
  | -------- | -------- |
  | Promise&lt;boolean&gt; | Promise object. The value **true** indicates that the upload task is removed successfully; the value **false** indicates that the upload task fails to be removed. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | The permissions check fails. |

**Example**

<!--code_no_check-->
  ```ts
  uploadTask.delete().then((result: boolean) => {
    console.info('Succeeded in deleting the upload task.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to delete the upload task. Code: ${err.code}, message: ${err.message}`);
  });
  ```


### delete<sup>9+</sup>

delete(callback: AsyncCallback&lt;boolean&gt;): void

Removes the upload task. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Upload

> **NOTE**
>
> Since there is no scenario that returns error 401, the error code `401 the parameters check fails` is removed in API version 12.

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** indicates that the upload task is removed successfully; the value **false** indicates that the upload task fails to be removed. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | The permissions check fails. |

**Example**

<!--code_no_check-->
  ```ts
  uploadTask.delete((err: BusinessError, result: boolean) => {
    if (err) {
      console.error(`Failed to delete the upload task. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in deleting the upload task.');
  });
  ```


### remove<sup>(deprecated)</sup>

remove(): Promise&lt;boolean&gt;

Removes the upload task. This API uses a promise to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Upload

> **NOTE**
>
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [delete](#delete9) instead.

**Return value**

  | Type | Description |
  | -------- | -------- |
  | Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the upload task is removed successfully; the value **false** indicates that the upload task fails to be removed. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | The permissions check fails. |

**Example**

  ```js
  uploadTask.remove().then((result: boolean) => {
    console.info('Succeeded in removing the upload task.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to remove the upload task. Code: ${err.code}, message: ${err.message}`);
  });
  ```


### remove<sup>(deprecated)</sup>

remove(callback: AsyncCallback&lt;boolean&gt;): void

Removes an upload task. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Upload

> **NOTE**
>
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [delete](#delete9-1) instead.

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;boolean&gt; | Yes | Callback invoked to return the result. The value **true** indicates that the upload task is removed successfully, and **false** indicates the opposite. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | The permissions check fails. |

**Example**

  ```js
  uploadTask.remove((err: BusinessError, result: boolean) => {
    if (err) {
      console.error(`Failed to remove the upload task. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    if (result) {
      console.info('Succeeded in removing the upload task.');
    }
  });
  ```

## UploadConfig
Upload configuration information.

**System capability**: SystemCapability.MiscServices.Upload

| Name   | Type     | Read-Only | Optional | Description                            |
|------|--------|----|----|-------------------------------|
| url | string | No | No | Resource URL. From API 6 to API 14, the maximum length is 2048 characters; from API 15 onward, the maximum length is 8192 characters. If the maximum length is exceeded, task creation fails. Supports the [HTTP interception](../../basic-services/request/app-file-upload-download.md#intercepting-http) feature. |
| header | Object | No | No | HTTP or HTTPS headers to be included in the upload request. |
| method | string | No | No | HTTP request method: POST or PUT. The default value is POST. Use POST to add a resource and PUT to modify a resource. |
| index<sup>11+</sup> | number | No | Yes | Path index of the task, usually used to specify the file path index in resumable transfer scenarios. The default value is 0. |
| begins<sup>11+</sup> | number | No | Yes | Starting position of the file to be read when the upload task starts, in bytes. It is usually used in resumable transfer scenarios. The default value is 0, and the value range is [0, file size], which is a closed interval, indicating that the transfer starts from the beginning. If the value is out of range, task creation fails. |
| ends<sup>11+</sup> | number | No | Yes | Ending position of the file to be read when the upload task ends, in bytes. It is usually used in resumable transfer scenarios. The default value is -1, and the value range is [-1, file size], which is a closed interval, indicating that the transfer ends at the end of the entire file. If the value is out of range, task creation fails. |
| files | Array&lt;[File](#file)&gt; | No | No | List of files to upload. The files are submitted in the HTTP multipart/form-data format. |
| data | Array&lt;[RequestData](#requestdata)&gt; | No | No | Form data in the request body. |

## TaskState<sup>9+</sup>
Task information of an upload task. It is the callback parameter of the [on('complete' | 'fail')](#oncomplete--fail9) and [off('complete' | 'fail')](#offcomplete--fail9) APIs.

**System capability**: SystemCapability.MiscServices.Upload

| Name   | Type     | Read-Only | Optional | Description                            |
|------|--------|----|----|-------------------------------|
| path | string | No | No | Path of the file.                                         |
| responseCode | number | No | No | Return code of the upload task. The value **0** indicates that the upload task is successful, and any other value indicates that the upload task is not completed successfully (including failure, pause, or stop). For details, see the return code table below and the upload task result description in the **message** parameter.<br>It is recommended to use [request.agent.create](#requestagentcreate10-1) to create an upload task and obtain standard error codes to handle exception branches. |
| message | string | No | No | Description of the upload task result.                           |

**Error code**
The return code values contained in **responseCode** are as follows.

| Return code | Description                               |
|-----|------------------------------------|
| 0   | Upload succeeded.                               |
| 5   | The task is actively paused or passively stopped.                         |
| 6   | The application to which the task belongs is switched to the background or terminated, causing the foreground task to stop. Check the application status.  |
| 7   | No network is available. Check whether the device is connected to the network.                  |
| 8   | The network type does not match. Check whether the current network type matches the network type required by the task.     |
| 10  | Failed to create the HTTP request. Check whether the parameters are correct or retry the task.          |
| 12  | Timeout. Check whether the parameters are correct, check whether the network condition allows, or retry the task.          |
| 13  | Connection failed. Check whether the parameters are correct, check whether the network condition allows, or retry the task.        |
| 14  | Request failed. Check whether the parameters are correct, check whether the network condition allows, or retry the task.        |
| 15  | Upload failed. Check whether the parameters are correct, check whether the network condition allows, or retry the task.        |
| 16  | Redirection failed. Check whether the parameters are correct, check whether the network condition allows, or retry the task.       |
| 17  | Protocol error. The server returns a 4XX or 5XX status code. Check whether the parameters are correct. |
| 20  | Other error. Check whether the parameters are correct, check whether the network condition allows, or retry the task.        |

## File
File list in [UploadConfig](#uploadconfig).

**System capability**: SystemCapability.MiscServices.Download

| Name | Type | Read-Only | Optional | Description |
|------|--------|----|----|-------------------------------|
| filename | string | No | No | Name of the file in the request header when **multipart** is used. |
| name | string | No | No | Name of a form item when **multipart** is used. The default value is **file**. |
| uri | string | No | No | Local storage path of the file.<br>Only "internal://cache/" is supported, that is, the cache path **context.cacheDir** corresponding to the caller (the passed-in context).<br>Example: internal://cache/path/to/file.txt |
| type | string | No | No | Type of the file content. By default, the type is obtained based on the extension of the file name or URI. |


## RequestData
Form data in [UploadConfig](#uploadconfig).

**System capability**: SystemCapability.MiscServices.Download

| Name | Type | Read-Only | Optional | Description |
|------|--------|----|----|-------------------------------|
| name | string | No | No | Name of the form element. |
| value | string | No | No | Value of the form element. |

## request.downloadFile<sup>9+</sup>

downloadFile(context: BaseContext, config: DownloadConfig): Promise&lt;DownloadTask&gt;

Creates and starts a download task. This API uses a promise to return the result asynchronously and supports the HTTP protocol. You can use [on('complete' | 'pause' | 'remove')](#oncomplete--pause--remove7) to obtain the status information of the task during download, including task completion, pause, or removal. You can use [on('fail')](#onfail7) to obtain the error information of the task during download.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | context | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes | Application context. |
  | config | [DownloadConfig](#downloadconfig) | Yes | Download configuration. |

**Return value**

  | Type | Description |
  | -------- | -------- |
  | Promise&lt;[DownloadTask](#downloadtask)&gt; | Promise used to return the download task **DownloadTask** object asynchronously. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | The permissions check fails. |
  | 401 | The parameters check fails. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |
  | 13400001 | Invalid file or file system error. |
  | 13400002 | File path not supported or invalid. |
  | 13400003 | Task service ability error. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component to ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Manually replace url with the HTTP address of the real server.
    request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
       let downloadTask: request.DownloadTask = data;
    }).catch((err: BusinessError) => {
      console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
    });
  } catch (err) {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  }
  ```


## request.downloadFile<sup>9+</sup>

downloadFile(context: BaseContext, config: DownloadConfig, callback: AsyncCallback&lt;DownloadTask&gt;): void

Creates and starts a download task. This API uses an asynchronous callback to return the result and supports the HTTP protocol. You can use [on('complete' | 'pause' | 'remove')](#oncomplete--pause--remove7) to obtain the status information of the task during download, including task completion, pause, or removal. You can use [on('fail')](#onfail7) to obtain the error information of the task during download.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | context | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes | Context based on the application program. |
  | config | [DownloadConfig](#downloadconfig) | Yes | Download configuration. |
  | callback | AsyncCallback&lt;[DownloadTask](#downloadtask)&gt; | Yes | Callback function. If the download task succeeds, **err** is **undefined** and **data** is the obtained **DownloadTask** object; otherwise, **data** is an error object. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | The permissions check fails. |
  | 401 | The parameters check fails. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |
  | 13400001 | Invalid file or file system error. |
  | 13400002 | File path not supported or invalid. |
  | 13400003 | Task service ability error. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Manually replace the URL with the HTTP protocol address of the real server.
    request.downloadFile(context, {
      url: 'https://xxxx/xxxxx.hap',
      filePath: 'xxx/xxxxx.hap'
    }, (err: BusinessError, data: request.DownloadTask) => {
      if (err) {
        console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
        return;
      }
    });
  } catch (err) {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  }
  ```

## request.download<sup>(deprecated)</sup>

download(config: DownloadConfig): Promise&lt;DownloadTask&gt;

Creates and starts a download task. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the FA model.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [request.downloadFile](#requestdownloadfile9) instead.

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | config | [DownloadConfig](#downloadconfig) | Yes | Download configuration. |

**Return value**

  | Type | Description |
  | -------- | -------- |
  | Promise&lt;[DownloadTask](#downloadtask)&gt; | Promise used to return the DownloadTask object. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | The permissions check fails. |

**Example**

  ```js
  let downloadTask: request.DownloadTask;
  // Manually replace the URL with the actual HTTP address of the server.
  request.download({ url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
    downloadTask = data;
  }).catch((err: BusinessError) => {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  })
  ```


## request.download<sup>(deprecated)</sup>

download(config: DownloadConfig, callback: AsyncCallback&lt;DownloadTask&gt;): void

Creates and starts a download task. This API uses an asynchronous callback to return the result.

**Model restriction**: This API can be used only in the FA model.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [request.downloadFile](#requestdownloadfile9-1) instead.

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | config | [DownloadConfig](#downloadconfig) | Yes | Download configuration. |
  | callback | AsyncCallback&lt;[DownloadTask](#downloadtask)&gt; | Yes | Callback function. If the download task succeeds, **err** is **undefined** and **data** is the obtained **DownloadTask** object; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 201 | The permissions check fails. |

**Example**

  ```js
  let downloadTask: request.DownloadTask;
  // Replace the URL with the actual HTTP address of the server.
  request.download({ url: 'https://xxxx/xxxxx.hap', 
  filePath: 'xxx/xxxxx.hap'}, (err: BusinessError, data: request.DownloadTask) => {
    if (err) {
      console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    downloadTask = data;
  });
  ```

## DownloadTask

A download task. Before using the following methods, you need to obtain a DownloadTask object first. In Promise form, obtain it through [request.downloadFile](#requestdownloadfile9); in callback form, obtain it through [request.downloadFile](#requestdownloadfile9-1).


### on('progress')

on(type: 'progress', callback: (receivedSize: number, totalSize: number) => void): void

Subscribes to the download task progress event. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> When the application is running in the background, calling this API to receive callbacks is not supported to meet the power consumption and performance requirements.

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | type | string | Yes | Type of the event to subscribe to.<br>- The value is 'progress', which indicates the download progress information. The event is triggered when the task progress changes. |
  | callback | (receivedSize: number, totalSize: number) => void | Yes | Callback invoked to return the download task progress, including the size of the downloaded file and the total size of the file to download, in bytes (B). During the download, if the server uses chunked transfer and the total file size cannot be obtained from the response header, totalSize is -1. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | The parameters check fails. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed.<br> Applicable version: 12+ |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Manually replace url with the HTTP protocol address of the real server.
    request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
      let downloadTask: request.DownloadTask = data;
      let progressCallback = (receivedSize: number, totalSize: number) => {
        console.info("download receivedSize:" + receivedSize + " totalSize:" + totalSize);
      };
      downloadTask.on('progress', progressCallback);
    }).catch((err: BusinessError) => {
      console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
    })
  } catch (err) {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  }
  ```


### off('progress')

off(type: 'progress', callback?: (receivedSize: number, totalSize: number) =&gt; void): void

Unsubscribes from the download task progress event.

**System capability**: SystemCapability.MiscServices.Download

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | type | string | Yes | Type of the event to unsubscribe from.<br>- The value is 'progress', which indicates the download progress information. |
  | callback | (receivedSize: number, totalSize: number) => void | No | Callback for the download progress event. If this parameter is not specified, all callbacks of the current type are unsubscribed from. |


**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | The parameters check fails. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed.<br> Applicable version: 12+ |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Manually replace the URL with the HTTP address of the real server.
    request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
      let downloadTask: request.DownloadTask = data;
      let progressCallback1 = (receivedSize: number, totalSize: number) => {
        console.info('Download delete progress notification.' + 'receivedSize:' + receivedSize + 'totalSize:' + totalSize);
      };
      let progressCallback2 = (receivedSize: number, totalSize: number) => {
        console.info('Download delete progress notification.' + 'receivedSize:' + receivedSize + 'totalSize:' + totalSize);
      };
      downloadTask.on('progress', progressCallback1);
      downloadTask.on('progress', progressCallback2);
      // Unsubscribe from progressCallback1.
      downloadTask.off('progress', progressCallback1);
      // Unsubscribe from all callbacks of the download task progress event.
      downloadTask.off('progress');
    }).catch((err: BusinessError) => {
      console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
    })
  } catch (err) {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  }
  ```


### on('complete' | 'pause' | 'remove')<sup>7+</sup>

on(type: 'complete' | 'pause' | 'remove', callback: () =&gt; void): void

Subscribes to the download task completion, pause, or removal event. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.Download

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | type | string | Yes | Type of the event to subscribe to.<br>- The value 'complete' indicates the download task completion event, which is triggered when the task is completed.<br>- The value 'pause' indicates the download task pause event, which is triggered when the task is paused.<br>- The value 'remove' indicates the download task removal event, which is triggered when the task is removed. |
  | callback | function | Yes | Callback for the download task event.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | The parameters check fails. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed.<br> Applicable version: 12+ |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Manually replace url with the HTTP address of the real server.
    request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
      let downloadTask: request.DownloadTask = data;
      let completeCallback = () => {
        console.info('Download task completed.');
      };
      downloadTask.on('complete', completeCallback);

      let pauseCallback = () => {
        console.info('Download task pause.');
      };
      downloadTask.on('pause', pauseCallback);

      let removeCallback = () => {
        console.info('Download task remove.');
      };
      downloadTask.on('remove', removeCallback);
    }).catch((err: BusinessError) => {
      console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
    })
  } catch (err) {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  }
  ```


### off('complete' | 'pause' | 'remove')<sup>7+</sup>

off(type: 'complete' | 'pause' | 'remove', callback?: () =&gt; void): void

Unsubscribes from the download task completion, pause, or removal event.

**System capability**: SystemCapability.MiscServices.Download

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | type | string | Yes | Type of the event to unsubscribe from.<br>- The value 'complete' indicates the download task completion event.<br>- The value 'pause' indicates the download task pause event.<br>- The value 'remove' indicates the download task removal event. |
  | callback | function | No | Callback to unsubscribe from. If this parameter is not specified, all callbacks of the current type are unsubscribed from. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | The parameters check fails. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed.<br> Supported since: 12+ |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Manually replace the URL with the HTTP address of the real server.
    request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
      let downloadTask: request.DownloadTask = data;
      let completeCallback1 = () => {
        console.info('Download delete complete notification.');
      };
      let completeCallback2 = () => {
        console.info('Download delete complete notification.');
      };
      downloadTask.on('complete', completeCallback1);
      downloadTask.on('complete', completeCallback2);
      // Unsubscribe from completeCallback1.
      downloadTask.off('complete', completeCallback1);
      // Unsubscribe from all callbacks of the download task completion event.
      downloadTask.off('complete');

      let pauseCallback1 = () => {
        console.info('Download delete pause notification.');
      };
      let pauseCallback2 = () => {
        console.info('Download delete pause notification.');
      };
      downloadTask.on('pause', pauseCallback1);
      downloadTask.on('pause', pauseCallback2);
      // Indicates unsubscribing from pauseCallback1.
      downloadTask.off('pause', pauseCallback1);
      // Indicates unsubscribing from all callbacks for the download task pause event.
      downloadTask.off('pause');

      let removeCallback1 = () => {
        console.info('Download delete remove notification.');
      };
      let removeCallback2 = () => {
        console.info('Download delete remove notification.');
      };
      downloadTask.on('remove', removeCallback1);
      downloadTask.on('remove', removeCallback2);
      // Indicates unsubscribing from removeCallback1.
      downloadTask.off('remove', removeCallback1);
      // Indicates unsubscribing from all callbacks for the download task removal event.
      downloadTask.off('remove');
    }).catch((err: BusinessError) => {
      console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
    })
  } catch (err) {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  }  
  ```


### on('fail')<sup>7+</sup>

on(type: 'fail', callback: (err: number) =&gt; void): void

Subscribes to the download task failure event. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.Download

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | type | string | Yes | Type of the event to subscribe to.<br>- The value is 'fail', which indicates a download failure. The event is triggered when the task fails. |
  | callback | (err: number) => void | Yes | Callback invoked when the download task fails. For details about the error causes, see the error codes of the download task in [constants](#constants). |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | The parameters check fails. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed.<br> Applicable version: 12+ |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Manually replace url with the HTTP address of the real server.
    request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
      let downloadTask: request.DownloadTask = data;
      let failCallback = (err: number) => {
        console.error(`Failed to download the task. Code: ${err}`);
      };
      downloadTask.on('fail', failCallback);
    }).catch((err: BusinessError) => {
      console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
    })
  } catch (err) {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  }
  ```


### off('fail')<sup>7+</sup>

off(type: 'fail', callback?: (err: number) =&gt; void): void

Unsubscribes from the download task failure event.

**System capability**: SystemCapability.MiscServices.Download

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | type | string | Yes | Type of the event to unsubscribe from.<br>- The value is 'fail', indicating a download failure. |
  | callback | (err: number) => void | No | Callback for the download task failure event. If this parameter is not specified, all callbacks of the current type are unsubscribed from. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | The parameters check fails. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed.<br> Applicable version: 12+ |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Manually replace url with the HTTP address of the real server.
    request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
      let downloadTask: request.DownloadTask = data;
      let failCallback1 = (err: number) => {
        console.error(`Failed to download the task. Code: ${err}`);
      };
      let failCallback2 = (err: number) => {
        console.error(`Failed to download the task. Code: ${err}`);
      };
      downloadTask.on('fail', failCallback1);
      downloadTask.on('fail', failCallback2);
      // Unsubscribe from failCallback1.
      downloadTask.off('fail', failCallback1);
      // Unsubscribe from all callbacks of the download task failure event.
      downloadTask.off('fail');
    }).catch((err: BusinessError) => {
      console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
    })
  } catch (err) {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  }
  ```

### delete<sup>9+</sup>

delete(): Promise&lt;boolean&gt;

Removes the download task. This API uses a promise to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download
  
> **NOTE**
>
> Since there is no scenario that returns error code 401, the error code `401 the parameters check fails` is removed in API version 12.

**Return value**

  | Type | Description |
  | -------- | -------- |
  | Promise&lt;boolean&gt; | Promise object. The value **true** indicates that the download task is removed successfully; the value **false** indicates that the download task fails to be removed. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | The permissions check fails. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Manually replace the URL with the HTTP address of the real server.
    request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
      data.delete().then((result: boolean) => {
        console.info('Succeeded in removing the download task.');
      }).catch((err: BusinessError) => {
        console.error(`Failed to remove the download task. Code: ${err.code}, message: ${err.message}`);
      });
    }).catch((err: BusinessError) => {
      console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
    })
  } catch (err) {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  }
  ```

### delete<sup>9+</sup>

delete(callback: AsyncCallback&lt;boolean&gt;): void

Removes the download task. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> Since there is no scenario that returns error code 401, the error code `401 the parameters check fails` is removed in API version 12.

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** indicates that the download task is removed successfully; the value **false** indicates that the download task fails to be removed. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | The permissions check fails. |


**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Manually replace url with the HTTP address of the real server.
    request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
      let downloadTask: request.DownloadTask = data;
      downloadTask.delete((err: BusinessError, result: boolean) => {
        if (err) {
          console.error(`Failed to remove the download task. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in removing the download task.');
      });
    }).catch((err: BusinessError) => {
      console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
    })
  } catch (err) {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  }
  ```

### getTaskInfo<sup>9+</sup>

getTaskInfo(): Promise&lt;DownloadInfo&gt;

Queries the information of a download task. This API uses a promise to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> Since there is no 401 error scenario, the error code `401 the parameters check fails` is removed in API version 12.

**Return value**

  | Type | Description |
  | -------- | -------- |
  | Promise&lt;[DownloadInfo](#downloadinfo7)&gt; | Promise object that returns a DownloadInfo object containing the download task information. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | The permissions check fails. |


**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Manually replace the URL with the HTTP address of the real server.
    request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
      let downloadTask: request.DownloadTask = data;
      downloadTask.getTaskInfo().then((downloadInfo: request.DownloadInfo) => {
        console.info('Succeeded in querying the download task');
      }).catch((err: BusinessError) => {
        console.error(`Failed to query the download task. Code: ${err.code}, message: ${err.message}`);
      });
    }).catch((err: BusinessError) => {
      console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
    })
  } catch (err) {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  } 
  ```

### getTaskInfo<sup>9+</sup>

getTaskInfo(callback: AsyncCallback&lt;DownloadInfo&gt;): void

Queries the information of a download task. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> Since there is no scenario that returns error code 401, the error code `401 the parameters check fails` is removed in API version 12.

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;[DownloadInfo](#downloadinfo7)&gt; | Yes | Callback function. If the operation of querying the download task succeeds, err is undefined and data is the obtained DownloadInfo object; otherwise, an error object is returned. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | The permissions check fails. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Manually replace url with the HTTP address of the real server.
    request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
      let downloadTask: request.DownloadTask = data;
      downloadTask.getTaskInfo((err: BusinessError, downloadInfo: request.DownloadInfo) => {
        if (err) {
          console.error(`Failed to query the download task. Code: ${err.code}, message: ${err.message}`);
        } else {
          console.info('Succeeded in querying the download task');
        }
      });
    }).catch((err: BusinessError) => {
      console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
    })
  } catch (err) {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  }
  ```

### getTaskMimeType<sup>9+</sup>

getTaskMimeType(): Promise&lt;string&gt;

Queries the MIME type of a download task (the media type of the resource in HTTP). This API uses a promise to return the result asynchronously.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> Since there is no 401 error scenario, the error code `401 the parameters check fails` has been removed in API version 12.

**Return value**

  | Type | Description |
  | -------- | -------- |
  | Promise&lt;string&gt; | Promise used to return the MIME type of the download task. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | The permissions check fails. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component, and ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Manually replace url with the HTTP address of the real server.
    request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
      let downloadTask: request.DownloadTask = data;
      downloadTask.getTaskMimeType().then((data: string) => {
        console.info('Succeeded in querying the download MimeType');
      }).catch((err: BusinessError) => {
        console.error(`Failed to query the download MimeType. Code: ${err.code}, message: ${err.message}`);
      });
    }).catch((err: BusinessError) => {
      console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
    })
  } catch (err) {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  }
  ```

### getTaskMimeType<sup>9+</sup>

getTaskMimeType(callback: AsyncCallback&lt;string&gt;): void

Queries the MIME type of a download task (the media type of a resource in HTTP). This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> Since there is no 401 error scenario, the error code `401 the parameters check fails` is removed in API version 12.

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;string&gt; | Yes | Callback used to return the result. If the MIME type of the download task is queried successfully, err is undefined and data is the obtained MIME type object of the download task; otherwise, data is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | The permissions check fails. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Manually replace url with the HTTP address of the real server.
    request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
      let downloadTask: request.DownloadTask = data;
      downloadTask.getTaskMimeType((err: BusinessError, data: string) => {
        if (err) {
          console.error(`Failed to query the download mimeType. Code: ${err.code}, message: ${err.message}`);
        } else {
          console.info('Succeeded in querying the download mimeType');
        }
      });
    }).catch((err: BusinessError) => {
      console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
    })
  } catch (err) {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  }
  ```

### suspend<sup>9+</sup>

suspend(): Promise&lt;boolean&gt;

Suspends a running download task. A suspended task can be resumed by [restore](#restore9). This API uses a promise to return the result asynchronously.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> Since there is no scenario that returns error code 401, the error code `401 the parameters check fails` is removed in API version 12.

**Return value**

  | Type | Description |
  | -------- | -------- |
  | Promise&lt;boolean&gt; | Promise object. The value **true** indicates that the running download task is suspended successfully; the value **false** indicates that the running download task fails to be suspended. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | The permissions check fails. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Manually replace url with the HTTP address of the real server.
    request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
      let downloadTask: request.DownloadTask = data;
      downloadTask.suspend().then((result: boolean) => {
        console.info('Succeeded in pausing the download task.');
      }).catch((err: BusinessError) => {
        console.error(`Failed to pause the download task. Code: ${err.code}, message: ${err.message}`);
      });
    }).catch((err: BusinessError) => {
      console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
    })
  } catch (err) {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  }
  ```

### suspend<sup>9+</sup>

suspend(callback: AsyncCallback&lt;boolean&gt;): void

Suspends a running download task. A suspended task can be resumed by [restore](#restore9). This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> Since there is no 401 error scenario, the error code `401 the parameters check fails` is removed in API version 12.

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** indicates that the download task is suspended successfully; the value **false** indicates that the download task fails to be suspended. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | The permissions check fails. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Manually replace url with the HTTP address of the real server.
    request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
      let downloadTask: request.DownloadTask = data;
      downloadTask.suspend((err: BusinessError, result: boolean) => {
        if (err) {
          console.error(`Failed to pause the download task. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in pausing the download task.');
      });
    }).catch((err: BusinessError) => {
      console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
    })
  } catch (err) {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  }
  ```

### restore<sup>9+</sup>

restore(): Promise&lt;boolean&gt;

Restarts a paused download task. This API uses a promise to return the result asynchronously.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> Since API version 12, the error code `401 the parameters check fails` has been removed because there is no scenario in which 401 is reported.

**Return value**

  | Type | Description |
  | -------- | -------- |
  | Promise&lt;boolean&gt; | Promise object. The value **true** indicates that the paused download task is restarted successfully; the value **false** indicates that the restart fails. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | The permissions check fails. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Manually replace the URL with the HTTP address of the real server.
    request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
      let downloadTask: request.DownloadTask = data;
      downloadTask.restore().then((result: boolean) => {
        console.info('Succeeded in resuming the download task.');
      }).catch((err: BusinessError) => {
        console.error(`Failed to resume the download task. Code: ${err.code}, message: ${err.message}`);
      });
    }).catch((err: BusinessError) => {
      console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
    })
  } catch (err) {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  }
  ```

### restore<sup>9+</sup>

restore(callback: AsyncCallback&lt;boolean&gt;): void

Restarts a paused download task. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> Since there is no scenario for error 401, the error code `401 the parameters check fails` is removed in API version 12.

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;boolean&gt; | Yes | Callback used to return the result. The value true indicates that the paused download task is restarted successfully, and false indicates the opposite. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | The permissions check fails. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Manually replace url with the HTTP address of the real server.
    request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
      let downloadTask: request.DownloadTask = data;
      downloadTask.restore((err: BusinessError, result: boolean) => {
        if (err) {
          console.error(`Failed to resume the download task. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in resuming the download task.');
      });
    }).catch((err: BusinessError) => {
      console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
    })
  } catch (err) {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  }
  ```

### remove<sup>(deprecated)</sup>

remove(): Promise&lt;boolean&gt;

Removes the download task. This API uses a promise to return the result asynchronously.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [delete](#delete9-2) instead.

**Return value**

  | Type | Description |
  | -------- | -------- |
  | Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means that the download task is removed successfully, and **false** means the opposite. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | The permissions check fails. |

**Example**

  ```js
  downloadTask.remove().then((result) => {
    console.info('Succeeded in removing the download task.');
  }).catch ((err: BusinessError) => {
    console.error(`Failed to remove the download task. Code: ${err.code}, message: ${err.message}`);
  });
  ```


### remove<sup>(deprecated)</sup>

remove(callback: AsyncCallback&lt;boolean&gt;): void

Removes the download task. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> Supported since API version 6. Deprecated since API version 9. Recommended to use [delete](#delete9-3) instead.

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;boolean&gt; | Yes | Callback function. The value **true** indicates that the download task is removed successfully; the value **false** indicates that the download task fails to be removed. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | The permissions check fails. |

**Example**

  ```js
  downloadTask.remove((err, result) => {
    if (err) {
      console.error(`Failed to remove the download task. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in removing the download task.');
  });
  ```


### query<sup>(deprecated)</sup>

query(): Promise&lt;DownloadInfo&gt;

Queries the download task and returns its information. This API uses a promise to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> Supported since API version 7 and deprecated since API version 9. Recommended to use [getTaskInfo](#gettaskinfo9) instead.

**Return value**

  | Type | Description |
  | -------- | -------- |
  | Promise&lt;[DownloadInfo](#downloadinfo7)&gt; | Promise object. Returns the DownloadInfo containing the download task information. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | The permissions check fails. |

**Example**

  ```js
  downloadTask.query().then((downloadInfo) => {    
    console.info('Succeeded in querying the download task.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to query the download task. Code: ${err.code}, message: ${err.message}`);
  });
  ```


### query<sup>(deprecated)</sup>

query(callback: AsyncCallback&lt;DownloadInfo&gt;): void

Queries a download task and returns the information about the download task. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [getTaskInfo](#gettaskinfo9-1) instead.

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;[DownloadInfo](#downloadinfo7)&gt; | Yes | Callback used to return the result. If the download task is queried successfully, **err** is **undefined** and **data** is the obtained **DownloadInfo** object. Otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | The permissions check fails. |

**Example**

  ```js
  downloadTask.query((err: BusinessError, downloadInfo: request.DownloadInfo) => {
    if (err) {
      console.error(`Failed to query the download task. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('Succeeded in querying the download task.');
    }
  });
  ```


### queryMimeType<sup>(deprecated)</sup>

queryMimeType(): Promise&lt;string&gt;

Queries the MIME type of the download task. This API uses a promise to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [getTaskMimeType](#gettaskmimetype9) instead.

**Return value**

  | Type | Description |
  | -------- | -------- |
  | Promise&lt;string&gt; | Promise used to return the MIME type of the download task. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | The permissions check fails. |

**Example**

  ```js
  downloadTask.queryMimeType().then((data: string) => {    
    console.info('Succeeded in querying the download MimeType.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to query the download MimeType. Code: ${err.code}, message: ${err.message}`);
  });
  ```


### queryMimeType<sup>(deprecated)</sup>

queryMimeType(callback: AsyncCallback&lt;string&gt;): void

Queries the MimeType of a download task. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> Supported since API version 7, deprecated since API version 9. Recommended to use [getTaskMimeType](#gettaskmimetype9-1) instead.

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;string&gt; | Yes | Callback function. If the MimeType of the download task is queried successfully, err is undefined and data is the obtained MimeType object of the task; otherwise, an error object is returned. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | The permissions check fails. |

**Example**

  ```js
  downloadTask.queryMimeType((err: BusinessError, data: string) => {
    if (err) {
      console.error(`Failed to query the download mimeType. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('Succeeded in querying the download mimeType.');
    }
  });
  ```


### pause<sup>(deprecated)</sup>

pause(): Promise&lt;void&gt;

Pauses a running download task. This API uses a Promise to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [suspend](#suspend9) instead.

**Return value**

  | Type | Description |
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | The permissions check fails. |

**Example**

  ```js
  downloadTask.pause().then(() => {    
    console.info('Succeeded in pausing the download task.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to pause the download task. Code: ${err.code}, message: ${err.message}`);
  });
  ```


### pause<sup>(deprecated)</sup>

pause(callback: AsyncCallback&lt;void&gt;): void

Pauses the running download task. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> Supported since API version 7. Deprecated since API version 9. Recommended to use [suspend](#suspend9-1) instead.

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | The permissions check fails. |

**Example**

  ```js
  downloadTask.pause((err: BusinessError) => {
    if (err) {
      console.error(`Failed to pause the download task. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in pausing the download task.');
  });
  ```


### resume<sup>(deprecated)</sup>

resume(): Promise&lt;void&gt;

Resumes the paused download task. This API uses a Promise to return the result asynchronously.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [restore](#restore9) instead.

**Return value**

  | Type | Description |
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | The permissions check fails. |

**Example**

  ```js
  downloadTask.resume().then(() => {
    console.info('Succeeded in resuming the download task.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to resume the download task. Code: ${err.code}, message: ${err.message}`);
  });
  ```


### resume<sup>(deprecated)</sup>

resume(callback: AsyncCallback&lt;void&gt;): void

Resumes a paused download task. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [restore](#restore9-1) instead.

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;void&gt; | Yes | Callback used to return the result. If the paused download task is resumed successfully, err is undefined; otherwise, err is an error object. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | The permissions check fails. |

**Example**

  ```js
  downloadTask.resume((err: BusinessError) => {
    if (err) {
      console.error(`Failed to resume the download task. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in resuming the download task.');
  });
  ```


## DownloadConfig
Download configuration information.

**System capability**: SystemCapability.MiscServices.Download

| Name | Type | Read-Only | Optional | Description |
|------|--------|----|----|-------------------------------|
| url | string | No | No | Resource address. From API 6 to API 14, the maximum length is 2048 characters; from API 15 onward, the maximum length is 8192 characters. If the maximum length is exceeded, task creation fails. Supports the [HTTP interception](../../basic-services/request/app-file-upload-download.md#intercepting-http) feature. |
| header | Object | No | Yes | HTTP or HTTPS headers to be included in the download request. The default value is empty. |
| enableMetered | boolean | No | Yes | Indicates whether to allow the download task configuration over a metered connection. The value true means allowed, and false means not allowed. The default value is false. When networkType is NETWORK_MOBILE \| NETWORK_WIFI, this parameter does not take effect.<br>**Note:**<br> Wi-Fi is a non-metered network, and mobile data is a metered network. |
| enableRoaming | boolean | No | Yes | Indicates whether to allow the download task configuration over a roaming network. The value true means allowed, and false means not allowed. The default value is false.<br>When networkType is NETWORK_MOBILE \| NETWORK_WIFI, this parameter does not take effect. |
| description | string | No | Yes | Description of the download session. The default value is an empty string. |
| filePath<sup>7+</sup> | string | No | Yes | Download path. The default value is the cache path corresponding to the caller (that is, the context passed in). The default file name is obtained from the part after the last "/" in the URL.<br>-&nbsp;In the FA model, use the [Context.getCacheDir](../apis-ability-kit/js-apis-inner-app-context.md#contextgetcachedir) method to obtain the application storage path.<br>-&nbsp;In the Stage model, use the AbilityContext class in [Context (base class of the Stage model context)](../apis-ability-kit/js-apis-inner-application-context.md) to obtain the file path. |
| networkType | number | No | Yes | Network types allowed for download. The allowed network types are determined by bitwise operations on the [network type constants](#constants). The following settings are supported:<br>- Only cellular network download is allowed. The parameter is NETWORK_MOBILE or 0x00000001.<br>- Only WLAN download is allowed. The parameter is NETWORK_WIFI or 0x00010000.<br>- Default value. Both cellular and WLAN download are allowed. The parameter is NETWORK_MOBILE \| NETWORK_WIFI or 0x00010001.<br>When the parameter is NETWORK_MOBILE \| NETWORK_WIFI, the enableMetered and enableRoaming parameters do not take effect. |
| title | string | No | Yes | Name of the download task. The default value is download. |
| background<sup>9+</sup> | boolean | No | Yes | Switch for background task notifications. When enabled, the download status can be displayed in notifications. The value true means enabled, and false means disabled. The default value is false. |


## DownloadInfo<sup>7+</sup>
Download task information, which is the callback parameter of the [getTaskInfo](#gettaskinfo9) API.

**System capability**: SystemCapability.MiscServices.Download

| Name   | Type     | Read-Only | Optional | Description                            |
|------|--------|----|----|-------------------------------|
| downloadId | number | No | No | Download task ID. |
| failedReason | number| No | No | Download failure reason, which can be any download task error code [constant](#constants). |
| fileName | string | No | No | Name of the downloaded file. |
| filePath | string | No | No | URI of the stored file. |
| pausedReason | number | No | No | Reason for pausing the session, which can be any download task pause reason [constant](#constants). |
| status | number | No | No | Download status code, which can be any download task status code [constant](#constants). |
| targetURI | string | No | No | URI of the downloaded file. |
| downloadTitle | string | No | No | Download task name. |
| downloadTotalBytes | number | No | No | Total size of the downloaded file, in bytes (B). |
| description | string | No | No | Description of the task to be downloaded. |
| downloadedBytes | number | No | No | Real-time download size, in bytes (B). |

## agent<sup>10+</sup>

request.agent provides task-based background upload and download agent capabilities. Developers create tasks and enqueue them through [request.agent.create](#requestagentcreate10), and manage the task lifecycle (start, pause, resume, stop, and remove) through the [Task](#requestagenttask10) object. Both foreground and background task modes are supported: a foreground task may fail or pause after the application switches to the background for a period of time, while a background task is not affected. Features such as resumable transfer, network condition control, automatic retry, and timeout control are supported. Compared with the basic [request.uploadFile](#requestuploadfile9)/[request.downloadFile](#requestdownloadfile9), request.agent provides more comprehensive task management and status query capabilities.

### Constants

**System capability**: SystemCapability.Request.FileTransferAgent


| Name | Type | Value | Description |
| -------- | -------- | -------- | -------- |
| VISIBILITY_COMPLETION<sup>21+</sup> | number |   1   | Display type of the [notification bar](#requestagentnotification15): displays the completion notification. |
| VISIBILITY_PROGRESS<sup>21+</sup>   | number |   2   | Display type of the [notification bar](#requestagentnotification15): displays the progress notification. |

## request.agent.Action<sup>10+</sup>

Enumerates the action options.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name | Value | Description |
| -------- | -------- | -------- |
| DOWNLOAD | 0 | Download task. |
| UPLOAD | 1 | Upload task. |


## request.agent.Mode<sup>10+</sup>
Defines the mode options.<br>
When an application's foreground task switches to the background for a period of time (depending on the system resource management policy), it may fail to run or be paused, whereas a background task is not affected by this operation.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name | Value | Description |
| -------- | -------- |-------- |
| BACKGROUND | 0 | Background task. |
| FOREGROUND | 1 | Foreground task. |

## request.agent.Network<sup>10+</sup>

Defines the network options.<br>
When the network does not meet the configured conditions, pending tasks wait for execution, and running tasks fail or pause.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name | Value | Description |
| -------- | -------- |-------- |
| ANY | 0 | No network type restriction. |
| WIFI | 1 | Wi-Fi network. |
| CELLULAR | 2 | Cellular data network. |

## request.agent.BroadcastEvent<sup>11+</sup>

Defines a custom system event. Users can obtain this event through the common event API.

The upload and download SA has the 'ohos.permission.SEND_TASK_COMPLETE_EVENT' permission. Users can configure the secondary configuration file pointed to by the event metadata to intercept other event senders.

The CommonEventData type is used to transfer common event related data. The content of its members differs from that described in [CommonEventData](js-apis-inner-commonEvent-commonEventData.md). CommonEventData.code indicates the task status, which is currently 0x40 COMPLETE or 0x41 FAILED; CommonEventData.data indicates the taskId of the task.

<!--Del-->
For details about the event configuration information and how to configure the secondary configuration file, see [Static Subscription to Common Events](../../basic-services/common-event/common-event-static-subscription-sys.md).<!--DelEnd-->

**System capability**: SystemCapability.Request.FileTransferAgent

| Name | Value | Description        |
| -------- | ------- |-----------|
| COMPLETE | ohos.request.event.COMPLETE | Indicates that the custom system event is complete. This event is triggered after the task ends. Based on the success or failure of the task, the event code returns 0x40 or 0x41. |

## request.agent.FileSpec<sup>10+</sup>
File information of a form item.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name   | Type     | Read-Only | Optional | Description                            |
|------|--------|----|----|-------------------------------|
| path | string | No | No | File path.<br>- Relative path, located under the caller's cache path.<br>For example: "./xxx/yyy/zzz.html", "xxx/yyy/zzz.html".<br>- internal protocol path, supporting "internal://" and its subpaths. "internal" corresponds to the path of the caller (that is, the passed-in context), and "internal://cache" corresponds to context.cacheDir.<br>For example: "internal://cache/path/to/file.txt".<br>- Application sandbox directory, only the base directory and its subdirectories are supported.<br>For example: "/data/storage/el1/base/path/to/file.txt".<br>- file protocol path, which must match the application bundle name, and only the base directory and its subdirectories are supported.<br>For example: "file://com.example.test/data/storage/el2/base/file.txt".<br>- User public file, supported only for upload tasks.<br>For example: "file://media/Photo/path/to/file.img". Only foreground tasks are supported.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| mimeType<sup>(deprecated)</sup> | string | No | Yes | MIME type of the file, obtained from the file name. The default value is the file name extension.<br>**Atomic service API**: This API can be used in atomic services since API version 11. <br> Supported since API version 10, and deprecated since API version 18. Recommended to use contentType instead. |
| contentType<sup>18+</sup> | string | No | Yes | Content type of the file. The default value is the file name extension. This option is written to the Content-Type field specified in the HTTP form. |
| filename | string | No | Yes | File name. The default value is obtained from the path.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| extras | object | No | Yes | Additional content of the file information. This parameter is not reflected in the HTTP request. The default value is empty.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |


## request.agent.FormItem<sup>10+</sup>
Form item information of a task.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name   | Type     | Read-Only | Optional | Description                            |
|------|--------|----|----|-------------------------------|
| name | string | No | No | Form parameter name. |
| value | string \| [FileSpec](#requestagentfilespec10) \| Array&lt;[FileSpec](#requestagentfilespec10)&gt; | No | No | Form parameter value. |


## request.agent.Config<sup>10+</sup>
Configuration information of an upload/download task.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name   | Type     | Read-Only | Optional | Description                            |
|------|--------|----|----|-------------------------------|
| action | [Action](#requestagentaction10) | No | No | Task operation option.<br>- UPLOAD indicates an upload task.<br>- DOWNLOAD indicates a download task.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| url | string | No | No | Resource address. From API 6 to API 14, the maximum length is 2048 characters; from API 15 onward, the maximum length is 8192 characters. If the maximum length is exceeded, task creation fails. Supports the [HTTP interception](../../basic-services/request/app-file-upload-download.md#intercepting-http) feature.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| title | string | No | Yes | Task title. The maximum length is 256 characters. The default value is lowercase upload or download, consistent with the action above. If the maximum length is exceeded, task creation fails.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| description | string | No | Yes | Detailed information about the task. The maximum length is 1024 characters. The default value is an empty string. If the maximum length is exceeded, task creation fails.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| mode | [Mode](#requestagentmode10) | No | Yes | Task mode. Supports setting foreground and background tasks. The default value is background task.<br>- FOREGROUND indicates a foreground task.<br>- BACKGROUND indicates a background task.<br>Since API version 20, when downloading to a user file, the mode must be request.agent.Mode.FOREGROUND; otherwise, the task cannot be created or executed properly.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| overwrite | boolean | No | Yes | Solution selection when the path already exists during download. The default value is false.<br>- true: overwrite the existing file.<br>- false: download fails.<br>Since API version 20, when downloading to a user file, this must be true.<br>When set to `true`, it is not recommended to create multiple tasks to download content to the same file simultaneously, as this may cause file content disorder.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| method | string | No | Yes | Standard HTTP method for upload or download, including GET, POST, and PUT, case-insensitive.<br>- For upload, PUT or POST is used, and the default value is PUT.<br>- For download, GET or POST is used, and the default value is GET.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| headers | object | No | Yes | Adds HTTP protocol headers to be included in the task.<br>- For an upload request, the default Content-Type is "multipart/form-data".<br>- For a download request, the default Content-Type is "application/json".<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| data | string \| Array&lt;[FormItem](#requestagentformitem10)&gt; | No | Yes | - For download, data is of the string type. Generally, the JSON format is used (an object will be converted to JSON text). The default value is empty.<br>- For upload, data is an array of form items Array&lt;[FormItem](#requestagentformitem10)&gt;. Since API version 15, a single task can upload up to 100 files. The default value is empty. If the file quantity limit is exceeded, task creation fails.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| saveas | string | No | Yes | Path for saving the downloaded file, including the following types:<br>- Relative path, located in the caller's cache path, for example, "./xxx/yyy/zzz.html" and "xxx/yyy/zzz.html".<br>- internal protocol path, supporting "internal://" and its subpaths. internal is the path corresponding to the caller (the passed-in context), and "internal://cache" corresponds to context.cacheDir. For example, "internal://cache/path/to/file.txt".<br>- Application sandbox directory, supporting only base and its subdirectories, for example, "/data/storage/el1/base/path/to/file.txt".<br>- file protocol path, supporting application files and user files. An application file must match the application bundle name and supports only base and its subdirectories, for example, "file://com.example.test/data/storage/el2/base/file.txt". A user file must be a user file URI created by the caller.<br>Since API version 20, except for [downloading network resource files to user files](../../basic-services/request/app-file-upload-download.md#downloading-network-resource-files-to-the-user-file), other cases can default to the cache path corresponding to the caller (that is, the passed-in context). The default file name is taken from the part after the last "/" in the URL.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| network | [Network](#requestagentnetwork10) | No | Yes | Network option. Currently supports the wireless network WIFI and the cellular data network CELLULAR. The default value is ANY (WIFI or CELLULAR).<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| metered | boolean | No | Yes | Whether to allow working in a metered network. The default value is false.<br>- true: yes <br>- false: no<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| roaming | boolean | No | Yes | Whether to allow working in a roaming network. The default value is true.<br>- true: yes <br>- false: no<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| retry | boolean | No | Yes | Whether to enable automatic retry for background tasks. This applies only to background tasks. The default value is true.<br>- true: yes <br>- false: no<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| redirect | boolean | No | Yes | Whether to allow redirection. The default value is true.<br>- true: yes <br>- false: no<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| proxy<sup>12+</sup> | string | No | Yes | Sets the proxy address. The maximum length is 512 characters. The default value is empty. If the maximum length is exceeded, task creation fails.<br>Proxy address format: "http://\<domain or address\>:\<port\>" |
| index | number | No | Yes | Path index of the task. Generally used for resumable transfer of the task. The default value is 0.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| begins | number | No | Yes | Start position of the file, in bytes (B). Generally used for resumable transfer. The default value is 0, and the value range is [0, file size], indicating that the transfer starts from the beginning. If the value is out of range, task creation fails.<br>- For download, requests the start position from which the server begins downloading the file (the "Range" option is set in the HTTP protocol).<br>- For upload, reads the start position of the file to be uploaded.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| ends | number | No | Yes | End position of the file, in bytes (B). Generally used for resumable transfer. The default value is -1, and the value range is [-1, file size], indicating that the transfer ends at the end of the entire file. If the value is out of range, task creation fails.<br>- For download, requests the end position from which the server begins downloading the file (the "Range" option is set in the HTTP protocol).<br>- For upload, reads the end position of the file to be uploaded.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| gauge | boolean | No | Yes | Progress notification policy for background tasks. This applies only to background tasks. <br>- false: sends only completion or failure notifications.<br>- true: sends progress, completion, and failure notifications.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| precise | boolean | No | Yes | - If set to true, the task fails when the file size cannot be obtained during upload/download.<br>- If set to false, the task continues when the file size is set to -1.<br>The default value is false.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| token | string | No | Yes | Task token. To query a task with a token, the token must be provided and queried through [request.agent.touch](#requestagenttouch10); otherwise, the specified task cannot be queried. The minimum length is 8 bytes and the maximum length is 2048 bytes. The default value is empty. If the value is out of range, task creation fails and an error code is returned.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| priority<sup>11+</sup> | number | No | Yes | Priority of the task. The priority of a foreground task is higher than that of a background task. When the task modes are the same, the smaller the number of this configuration item, the higher the priority. The default value is 0. |
| extras | object | No | Yes | Additional features of the configuration. The default value is empty.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| multipart<sup>15+</sup> | boolean | No | Yes | Whether to use a single request for upload. When uploading with a single request, multipart/form-data is always used.<br>- false: each file is transferred using one request. <br>- true: multiple files are uploaded using a single request. <br>The default value is false. |
| notification<sup>15+</sup> | [Notification](#requestagentnotification15) | No | Yes | Custom settings for the notification bar. The default value is `{}`.|
| minSpeed<sup>20+</sup> | [MinSpeed](#requestagentminspeed20) | No | Yes | Custom settings for the minimum speed limit. The minimum speed limit is disabled by default.|
| timeout<sup>20+</sup> | [Timeout](#requestagenttimeout20) | No | Yes | Custom settings for the timeout duration. The default connection timeout is 60 seconds, and the default total timeout is 604800 seconds (1 week). When the retry parameter is true, the [timeout](#requestagenttimeout20) event triggers an immediate retry, causing the [timeout](#requestagenttimeout20) to be masked by the retry action in external observation, but the internal [timeout](#requestagenttimeout20) condition has actually been triggered. To explicitly observe the [timeout](#requestagenttimeout20) event, disable the retry parameter. |

## request.agent.State<sup>10+</sup>

Enumerates the current states of a task.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name | Value | Description |
| -------- | -------- |-------- |
| INITIALIZED | 0x00 | The task created based on the configuration information ([Config](#requestagentconfig10)) has been initialized. |
| WAITING | 0x10 | The task is waiting for resources to run or retry, or the network status does not match. |
| RUNNING | 0x20 | The task is running. |
| RETRYING | 0x21 | The task has failed at least once and is being processed again. |
| PAUSED | 0x30 | The task is paused and will be resumed later. |
| STOPPED | 0x31 | The task is stopped. |
| COMPLETED | 0x40 | The task is completed. |
| FAILED | 0x41 | The task failed. |
| REMOVED | 0x50 | The task is removed. |


## request.agent.Progress<sup>10+</sup>
Defines the data structure of the task progress.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name   | Type     | Read-Only | Optional | Description                            |
|------|--------|----|----|-------------------------------|
| state | [State](#requestagentstate10) | Yes | No | Current state of the task.                                                            |
| index | number | Yes | No | Index of the file currently being processed in the task.                                                     |
| processed | number | Yes | No | Size of the processed data of the current file in the task, in bytes (B).                                               |
| sizes | Array&lt;number&gt; | Yes | No | Size of the current file in the task, in bytes (B). During download, if the server uses chunked transfer and the total file size cannot be obtained from the response header, the value of sizes is -1. |
| extras | object | Yes | Yes | Extra content for interaction, for example, the header and body of the response from the server. The default value is empty.                                     |


## request.agent.Faults<sup>10+</sup>

Defines the reasons for task failure.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> In API version 12 and earlier, only serial attempts to connect to the IP addresses related to a domain name are supported, and the connection time of a single IP address cannot be controlled. If the first IP address returned by DNS is blocked, a handshake timeout may occur, which in turn triggers a TIMEOUT error.<br>**Atomic service API**: This API can be used in atomic services since API version 11.

| Name | Value | Description                                                                             |
| -------- | -------- |--------------------------------------------------------------------------------|
| OTHERS | 0xFF | Indicates other faults.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                                                        |
| DISCONNECTED | 0x00 | Indicates that the network is disconnected.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                                                      |
| TIMEOUT | 0x10 | Indicates that the task times out.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                                                        |
| PROTOCOL | 0x20 | Indicates a protocol error, for example, an internal server error (500) or an unprocessable data range (416).<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                        |
| PARAM<sup>12+</sup> | 0x30 | Indicates a parameter error, for example, an invalid URL format.<br>**Atomic service API**: This API can be used in atomic services since API version 12.          |
| FSIO | 0x40 | Indicates a file system I/O error, for example, an error in opening, searching, reading, writing, or closing a file.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                                   |
| DNS<sup>12+</sup> | 0x50 | Indicates a DNS resolution error.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                  |
| TCP<sup>12+</sup> | 0x60 | Indicates a TCP connection error.<br>**Atomic service API**: This API can be used in atomic services since API version 12.              |
| SSL<sup>12+</sup> | 0x70 | Indicates an SSL connection error, for example, a certificate error or a certificate verification failure.<br>**Atomic service API**: This API can be used in atomic services since API version 12. |
| REDIRECT<sup>12+</sup> | 0x80 | Indicates a redirection error.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                    |
| LOW_SPEED<sup>20+</sup>  | 0x90 | Indicates that the task speed is too low.                    |

## request.agent.Filter<sup>10+</sup>
Filter criteria.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name   | Type     | Read-Only | Optional | Description                            |
|------|--------|----|----|-------------------------------|
| before | number | No | Yes | End Unix timestamp (in milliseconds). The default value is the time when the API is called. |
| after | number | No | Yes | Start Unix timestamp (in milliseconds). The default value is the time when the API is called minus 24 hours. |
| state | [State](#requestagentstate10) | No | Yes | State of the task. If not specified, all tasks are queried. |
| action | [Action](#requestagentaction10) | No | Yes | Task operation option.<br>- UPLOAD indicates an upload task.<br>- DOWNLOAD indicates a download task.<br>- If not specified, all tasks are queried. |
| mode | [Mode](#requestagentmode10) | No | Yes | Task mode.<br>- FOREGROUND indicates a foreground task.<br>- BACKGROUND indicates a background task.<br>- If not specified, all tasks are queried. |

## request.agent.TaskInfo<sup>10+</sup>

Defines the task information data structure for query results. It supports common queries (through APIs such as request.agent.show and request.agent.touch) and system queries (queries at the system application level). The visibility of fields differs between the two query modes.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name | Type | Read-Only | Optional | Description |
|------|--------|----|----|-------------------------------|
| saveas | string | Yes | Yes | Path for saving the downloaded file. The default value is empty.<br>Queried through [request.agent.show](#requestagentshow10-1) and [request.agent.touch](#requestagenttouch10-1). |
| url | string | Yes | Yes | URL of the task.<br>- Queried through [request.agent.show](#requestagentshow10-1) and [request.agent.touch](#requestagenttouch10-1). |
| data | string \| Array&lt;[FormItem](#requestagentformitem10)&gt; | Yes | Yes | Data content of the task.<br>- During download, data is of the string type, usually in JSON format.<br>- During upload, data is an array of form items Array\<FormItem\>.<br>- Queried through [request.agent.show](#requestagentshow10-1) and [request.agent.touch](#requestagenttouch10-1). |
| tid | string | Yes | No | Task ID. |
| title | string | Yes | No | Task title. |
| description | string | Yes | No | Task description. |
| action | [Action](#requestagentaction10) | Yes | No | Task action option.<br>- UPLOAD indicates an upload task.<br>- DOWNLOAD indicates a download task. |
| mode | [Mode](#requestagentmode10) | Yes | No | Task mode.<br>- FOREGROUND indicates a foreground task.<br>- BACKGROUND indicates a background task. |
| priority<sup>11+</sup> | number | Yes | No | Priority in the task configuration. The priority of a foreground task is higher than that of a background task. For tasks in the same mode, a smaller number indicates a higher priority. |
| mimeType | string | Yes | No | MimeType in the task configuration. |
| progress | [Progress](#requestagentprogress10) | Yes | No | Progress of the task. |
| gauge | boolean | Yes | No | Progress notification policy of a background task. It applies only to background tasks.<br>- false: sends only the completion or failure notification.<br>- true: sends the progress, completion, and failure notifications. |
| ctime | number | Yes | No | Unix timestamp (in milliseconds) when the task is created, generated by the system of the current device.<br>Note: When [request.agent.search](#requestagentsearch10-1) is used for querying, this value must fall within the [after, before] interval for the task ID to be queried normally. For details about before and after, see [Filter](#requestagentfilter10). |
| mtime | number | Yes | No | Unix timestamp (in milliseconds) when the task state changes, generated by the system of the current device. |
| retry | boolean | Yes | No | Retry switch of the task. It applies only to background tasks.<br>- true: yes <br>- false: no |
| tries | number | Yes | No | Number of attempts of the task. |
| faults | [Faults](#requestagentfaults10) | Yes | No | Failure reason of the task. |
| reason | string | Yes | No | Reason why the task is waiting, failed, stopped, or paused. |
| extras | object | Yes | Yes | Extra part of the task. The default value is empty.<br>Queried through [request.agent.show](#requestagentshow10-1) and [request.agent.touch](#requestagenttouch10-1). |

## request.agent.HttpResponse<sup>12+</sup>
Data structure of the task response header.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name | Type | Read-Only | Optional | Description |
|------|--------|----|----|-------------------------------|
| version | string | Yes | No | HTTP version. |
| statusCode | number | Yes | No | HTTP response status code. |
| reason | string | Yes | No | HTTP response reason. |
| headers | Map&lt;string, Array&lt;string&gt;&gt; | Yes | No | HTTP response header. |

## request.agent.Notification<sup>15+</sup>

Custom notification bar information.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name   | Type     | Read-Only | Optional | Description                            |
|------|--------|----|----|-------------------------------|
| title | string | No | Yes | Custom title of the notification bar. If this parameter is not set, the default display mode is used. The maximum length of title is 1024B. If the length exceeds the limit, the default display mode is used. |
| text | string | No | Yes | Custom body text of the notification bar. If this parameter is not set, the default display mode is used. The maximum length of text is 3072B. If the length exceeds the limit, the default display mode is used. |
| visibility<sup>21+</sup> | number | No | Yes | Sets the display mode of the task notification bar. The display mode is determined by the bitwise operation of the [VISIBILITY constants](#constants-1). The display modes of the task notification include the following:<br>- Only the completion notification is displayed. The parameter is VISIBILITY_COMPLETION or 1. The corresponding notification is displayed after the task is completed or fails.<br>- Only the progress notification is displayed. The parameter is VISIBILITY_PROGRESS or 2. The progress notification is displayed while the task is in progress. When the task download succeeds or fails, the progress notification exits directly and the completion notification is not displayed.<br>- Both the progress notification and the completion notification are displayed. The parameter is VISIBILITY_COMPLETION \| VISIBILITY_PROGRESS or 3. The progress notification is displayed while the task is in progress. When the task download succeeds or fails, the progress notification exits and the completion notification is displayed.<br>If this parameter is not set, the display mode is determined by the gauge field. If there is no gauge field, only the completion notification is displayed.|
| wantAgent<sup>22+</sup> | [WantAgent](../../reference/apis-ability-kit/js-apis-app-ability-wantAgent.md) | No | Yes | Notification parameter, used to implement the function of jumping after the task notification is tapped. The default value is empty.|


**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common, wantAgent, WantAgent } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let wantAgentInfo: wantAgent.WantAgentInfo = {
    wants: [
      {
        deviceId: '',
        bundleName: 'com.example.request',
        abilityName: 'EntryAbility',
        action: '',
        entities: [],
        uri: '',
        parameters: {}
      }
    ],
    actionType: wantAgent.OperationType.START_ABILITY,
    requestCode: 0,
    wantAgentFlags:[wantAgent.WantAgentFlags.CONSTANT_FLAG]
  };
  let config: request.agent.Config = {
    action: request.agent.Action.DOWNLOAD,
    url: 'http://127.0.0.1', // Manually replace the URL with the HTTP address of the real server.
    title: 'taskOnNotification',
    description: 'Sample code for event listening',
    mode: request.agent.Mode.BACKGROUND,
    overwrite: true,
    method: "GET",
    saveas: "./",
    network: request.agent.Network.ANY,
    gauge: true,
    notification: {
      visibility: request.agent.VISIBILITY_COMPLETION | request.agent.VISIBILITY_PROGRESS,
      wantAgent: await wantAgent.getWantAgent(wantAgentInfo),
    }
  };
  let createOnCallback = (progress: request.agent.Progress) => {
    console.info('download task progress.');
  };
  request.agent.create(context, config).then((task: request.agent.Task) => {
    task.on('progress', createOnCallback);
    console.info(`Succeeded in creating a download task. result: ${task.tid}`);
    task.start();
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a download task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

## request.agent.GroupConfig<sup>15+</sup>

Download task group configuration options.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name   | Type     | Read-Only | Optional | Description                            |
|------|--------|----|----|-------------------------------|
| gauge | boolean | No | Yes | Progress notification policy for background tasks, which applies only to background tasks. <br>- true: displays progress, success, and failure notifications. <br>- false: displays only success and failure notifications.<br>The default value is false. |
| notification<sup>15+</sup> | [Notification](#requestagentnotification15) | No | No  | Custom notification bar settings. The default value is `{}`                     |

## request.agent.WaitingReason<sup>20+</sup>

Enumerates the reasons why a task enters the waiting state.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name | Value | Description |
| -------- |------|--------------------------|
| TASK_QUEUE_FULL | 0x00 | The task enters the waiting state because the task queue is full. |
| NETWORK_NOT_MATCH | 0x01 | The task enters the waiting state because the required network conditions are not met. |
| APP_BACKGROUND | 0x02 | The task enters the waiting state because the application has been in the background for a long time. |
| USER_INACTIVATED | 0x03 | The task enters the waiting state because the user to which it belongs is inactive. |

## request.agent.MinSpeed<sup>20+</sup>

Minimum speed configuration of a task. If the task speed remains below the specified value for the specified duration, the task fails, and the failure reason is [LOW_SPEED](#requestagentfaults10).

**System capability**: SystemCapability.Request.FileTransferAgent

| Name | Type | Read-Only | Optional | Description |
|---------|----------|----|----|--------------------------------------------------------------|
| speed | number | No | No | Minimum speed of the task, in bytes per second (B/s), with a value range of [0, +∞). If the task speed remains below this value for the specified duration, the task fails. Setting this parameter to 0 disables the minimum speed limit. |
| duration | number | No | No | Duration allowed below the minimum speed, in seconds, with a value range of [0, +∞). If the task speed remains below the specified value for this duration, the task fails. Setting this parameter to 0 disables the minimum speed limit. |

## request.agent.Timeout<sup>20+</sup>

Timeout configuration of a task. The time during which a task is in the waiting state is not counted. An upload or download task may wait for the following reasons: [WaitingReason<sup>20+</sup>](#requestagentwaitingreason20).

**System capability**: SystemCapability.Request.FileTransferAgent

| Name      | Type     | Read-Only | Optional | Description                                      |
|---------|--------|----|----|-----------------------------------------|
| connectionTimeout   | number | No  | Yes  | Connection timeout of the task, in seconds. The connection timeout is the maximum time spent establishing a connection between the client and the server. If this parameter is not set, the default value 60 seconds is used. The minimum allowed value is 1 second, and the value range is [1, +∞). If the value is less than the minimum, parameter verification fails and an error code is returned. |
| totalTimeout   | number | No  | Yes  | Total timeout of the task, in seconds. The total timeout includes the entire time spent establishing the connection, sending the request, and receiving the response. If this parameter is not specified, the default value 604800 seconds (1 week) is used. The minimum allowed value is 1 second, and the maximum allowed value is 604800 seconds (1 week). If the value is out of range, parameter verification fails and an error code is returned. |


## request.agent.Task<sup>10+</sup>
Upload or download task. Before using the following methods, you need to obtain a Task object. In Promise mode, obtain it through [request.agent.create](#requestagentcreate10-1); in callback mode, obtain it through [request.agent.create](#requestagentcreate10).

### Properties
Includes the task ID and the task configuration information.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> The Task object and its mounted callback functions are released and automatically reclaimed by the system after the remove method is called.

| Name   | Type     | Read-Only | Optional | Description                            |
|------|--------|----|----|-------------------------------|
| tid | string | Yes | No | Task ID, automatically generated by the system and unique. |
| config | [Config](#requestagentconfig10) | No | No | Task configuration information. |

### on('progress')<sup>10+</sup>

on(event: 'progress', callback: (progress: Progress) =&gt; void): void

Subscribes to the task progress event. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | event | string | Yes | Type of the event to subscribe to.<br>- The value is 'progress', indicating the task progress. This event is triggered when the task progress changes. |
  | callback | (progress: [Progress](#requestagentprogress10)) => void | Yes | Callback invoked when the task progress changes. The callback parameter **progress** contains the current task status, file index, and size of processed data. For details, see [Progress](#requestagentprogress10). |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |
  | 21900005 | task mode error.<br> Supported since: 10-10 |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component to ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let attachments: Array<request.agent.FormItem> = [{
    name: "taskOnTest",
    value: {
      filename: "taskOnTest.avi",
      path: "./taskOnTest.avi",
    }
  }];
  let config: request.agent.Config = {
    action: request.agent.Action.UPLOAD,
    url: 'http://127.0.0.1', // Manually replace the URL with the HTTP address of the real server.
    title: 'taskOnTest',
    description: 'Sample code for event listening',
    mode: request.agent.Mode.FOREGROUND,
    overwrite: false,
    method: "PUT",
    data: attachments,
    saveas: "./",
    network: request.agent.Network.CELLULAR,
    metered: false,
    roaming: true,
    retry: true,
    redirect: true,
    index: 0,
    begins: 0,
    ends: -1,
    gauge: false,
    precise: false,
    token: "it is a secret"
  };
  let createOnCallback = (progress: request.agent.Progress) => {
    console.info('upload task progress.');
  };
  request.agent.create(context, config).then((task: request.agent.Task) => {
    task.on('progress', createOnCallback);
    console.info(`Succeeded in creating a upload task. result: ${task.tid}`);
    task.start();
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### on('completed')<sup>10+</sup>

on(event: 'completed', callback: (progress: Progress) =&gt; void): void

Subscribes to the task completion event. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | event | string | Yes | Type of the event to subscribe to.<br>- The value is 'completed', which indicates task completion. The event is triggered when the task is completed. |
  | callback | (progress: [Progress](#requestagentprogress10)) => void | Yes | Callback invoked when the task is completed. The callback parameter **progress** contains the progress information when the task is completed. For details, see [Progress](#requestagentprogress10). |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |
  | 21900005 | task mode error.<br> Applicable version: 10-10 |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let attachments: Array<request.agent.FormItem> = [{
    name: "taskOnTest",
    value: {
      filename: "taskOnTest.avi",
      path: "./taskOnTest.avi",
    }
  }];
  let config: request.agent.Config = {
    action: request.agent.Action.UPLOAD,
    url: 'http://127.0.0.1', // Manually replace the URL with the HTTP address of the real server.
    title: 'taskOnTest',
    description: 'Sample code for event listening',
    mode: request.agent.Mode.FOREGROUND,
    overwrite: false,
    method: "PUT",
    data: attachments,
    saveas: "./",
    network: request.agent.Network.CELLULAR,
    metered: false,
    roaming: true,
    retry: true,
    redirect: true,
    index: 0,
    begins: 0,
    ends: -1,
    gauge: false,
    precise: false,
    token: "it is a secret"
  };
  let createOnCallback = (progress: request.agent.Progress) => {
    console.info('upload task completed.');
  };
  request.agent.create(context, config).then((task: request.agent.Task) => {
    task.on('completed', createOnCallback);
    console.info(`Succeeded in creating a upload task. result: ${task.tid}`);
    task.start();
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### on('failed')<sup>10+</sup>

on(event: 'failed', callback: (progress: Progress) =&gt; void): void

Subscribes to the task failure event. This API uses an asynchronous callback. You can call [request.agent.show](#requestagentshow10-1) to view the failure cause.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | event | string | Yes | Type of the event to subscribe to.<br>- The value is 'failed', indicating a task failure. This event is triggered when the task fails. |
  | callback | (progress: [Progress](#requestagentprogress10)) => void | Yes | Callback invoked when the task fails. The callback parameter **progress** contains the progress information when the task fails. You can call [request.agent.show](#requestagentshow10-1) to view the failure cause. For details, see [Progress](#requestagentprogress10). |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |
  | 21900005 | Operation with wrong task mode.<br> Applicable version: 10-10 |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let attachments: Array<request.agent.FormItem> = [{
    name: "taskOnTest",
    value: {
      filename: "taskOnTest.avi",
      path: "./taskOnTest.avi",
    }
  }];
  let config: request.agent.Config = {
    action: request.agent.Action.UPLOAD,
    url: 'http://127.0.0.1', // Manually replace the URL with the HTTP address of the real server.
    title: 'taskOnTest',
    description: 'Sample code for event listening',
    mode: request.agent.Mode.FOREGROUND,
    overwrite: false,
    method: "PUT",
    data: attachments,
    saveas: "./",
    network: request.agent.Network.CELLULAR,
    metered: false,
    roaming: true,
    retry: true,
    redirect: true,
    index: 0,
    begins: 0,
    ends: -1,
    gauge: false,
    precise: false,
    token: "it is a secret"
  };
  let createOnCallback = (progress: request.agent.Progress) => {
    console.info('upload task failed.');
  };
  request.agent.create(context, config).then((task: request.agent.Task) => {
    task.on('failed', createOnCallback);
    console.info(`Succeeded in creating a upload task. result: ${task.tid}`);
    task.start();
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### on('pause')<sup>11+</sup>

on(event: 'pause', callback: (progress: Progress) =&gt; void): void

Subscribes to the task pause event. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | event | string | Yes | Type of the event to subscribe to.<br>- The value is 'pause', indicating that the task is paused. This event is triggered when the task is paused. |
  | callback | (progress: [Progress](#requestagentprogress10)) => void | Yes | Callback invoked when the task is paused. The callback parameter **progress** contains the progress information when the task is paused. For details, see [Progress](#requestagentprogress10). |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let attachments: Array<request.agent.FormItem> = [{
    name: "taskOnTest",
    value: {
      filename: "taskOnTest.avi",
      path: "./taskOnTest.avi",
    }
  }];
  let config: request.agent.Config = {
    action: request.agent.Action.UPLOAD,
    url: 'http://127.0.0.1', // Manually replace the URL with the HTTP address of the real server.
    title: 'taskOnTest',
    description: 'Sample code for event listening',
    mode: request.agent.Mode.FOREGROUND,
    overwrite: false,
    method: "POST",
    data: attachments,
    saveas: "./",
    network: request.agent.Network.CELLULAR,
    metered: false,
    roaming: true,
    retry: true,
    redirect: true,
    index: 0,
    begins: 0,
    ends: -1,
    gauge: false,
    precise: false,
    token: "it is a secret"
  };
  let createOnCallback = (progress: request.agent.Progress) => {
    console.info('upload task pause.');
  };
  request.agent.create(context, config).then(async (task: request.agent.Task) => {
    task.on('pause', createOnCallback);
    console.info(`Succeeded in creating a upload task. result: ${task.tid}`);
    task.start();
    // Wait for 1 second before performing the next step to prevent asynchronous disorder.
    await new Promise<void>((resolve) => {
      setTimeout(() => resolve(), 1000);
    })
    task.pause();
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### on('resume')<sup>11+</sup>

on(event: 'resume', callback: (progress: Progress) =&gt; void): void

Subscribes to the task resume event. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | event | string | Yes | Type of the event to subscribe to.<br>- The value is 'resume', which indicates the task resume event. This event is triggered when the task is resumed. |
  | callback | (progress: [Progress](#requestagentprogress10)) => void | Yes | Callback invoked when the task is resumed. The callback parameter **progress** contains the progress information when the task is resumed. For details, see [Progress](#requestagentprogress10). |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let attachments: Array<request.agent.FormItem> = [{
    name: "taskOnTest",
    value: {
      filename: "taskOnTest.avi",
      path: "./taskOnTest.avi",
    }
  }];
  let config: request.agent.Config = {
    action: request.agent.Action.UPLOAD,
    url: 'http://127.0.0.1', // Manually replace the URL with the HTTP address of the real server.
    title: 'taskOnTest',
    description: 'Sample code for event listening',
    mode: request.agent.Mode.FOREGROUND,
    overwrite: false,
    method: "PUT",
    data: attachments,
    saveas: "./",
    network: request.agent.Network.CELLULAR,
    metered: false,
    roaming: true,
    retry: true,
    redirect: true,
    index: 0,
    begins: 0,
    ends: -1,
    gauge: false,
    precise: false,
    token: "it is a secret"
  };
  let createOnCallback = (progress: request.agent.Progress) => {
    console.info('upload task resume.');
  };
  request.agent.create(context, config).then(async (task: request.agent.Task) => {
    task.on('resume', createOnCallback);
    console.info(`Succeeded in creating a upload task. result: ${task.tid}`);
    task.start();
    // Wait for 1 second before proceeding to the next step to prevent asynchronous disorder.
    await new Promise<void>((resolve) => {
      setTimeout(() => resolve(), 1000);
    })
    task.pause();
    // Wait for 1 second before proceeding to the next step to prevent asynchronous disorder.
    await new Promise<void>((resolve) => {
      setTimeout(() => resolve(), 1000);
    })
    task.resume();
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### on('remove')<sup>11+</sup>

on(event: 'remove', callback: (progress: Progress) =&gt; void): void

Subscribes to the task removal event. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | event | string | Yes | Event type to subscribe to.<br>- The value is 'remove', which indicates that the task is removed. This event is triggered when the task is removed. |
  | callback | (progress: [Progress](#requestagentprogress10)) => void | Yes | Callback invoked when the task is removed. The callback parameter **progress** carries the progress information when the task is removed. For details, see [Progress](#requestagentprogress10). |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let attachments: Array<request.agent.FormItem> = [{
    name: "taskOnTest",
    value: {
      filename: "taskOnTest.avi",
      path: "./taskOnTest.avi",
    }
  }];
  let config: request.agent.Config = {
    action: request.agent.Action.UPLOAD,
    url: 'http://127.0.0.1', // Manually replace the URL with the HTTP address of the real server.
    title: 'taskOnTest',
    description: 'Sample code for event listening',
    mode: request.agent.Mode.FOREGROUND,
    overwrite: false,
    method: "PUT",
    data: attachments,
    saveas: "./",
    network: request.agent.Network.CELLULAR,
    metered: false,
    roaming: true,
    retry: true,
    redirect: true,
    index: 0,
    begins: 0,
    ends: -1,
    gauge: false,
    precise: false,
    token: "it is a secret"
  };
  let createOnCallback = (progress: request.agent.Progress) => {
    console.info('upload task remove.');
  };
  request.agent.create(context, config).then(async (task: request.agent.Task) => {
    task.on('remove', createOnCallback);
    console.info(`Succeeded in creating a upload task. result: ${task.tid}`);
    task.start();
    // Wait for 1 second before performing the next step to prevent asynchronous disorder.
    await new Promise<void>((resolve) => {
      setTimeout(() => resolve(), 1000);
    })
    request.agent.remove(task.tid);
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### on('response')<sup>12+</sup>

on(event: 'response', callback: Callback&lt;HttpResponse&gt;): void

Subscribes to the task response header. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | event | string | Yes | Type of the event to subscribe to.<br>- The value is 'response', which indicates the task response. This event is triggered when a response is received for the request. |
  | callback | Callback&lt;[HttpResponse](#requestagenthttpresponse12)&gt; | Yes | Callback invoked when the related event occurs, returning the data structure of the task response header. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let attachments: Array<request.agent.FormItem> = [{
    name: "taskOnTest",
    value: {
      filename: "taskOnTest.avi",
      path: "./taskOnTest.avi",
    }
  }];
  let config: request.agent.Config = {
    action: request.agent.Action.UPLOAD,
    url: 'http://127.0.0.1', // Manually replace the URL with the HTTP address of the real server.
    title: 'taskOnTest',
    description: 'Sample code for event listening',
    mode: request.agent.Mode.FOREGROUND,
    overwrite: false,
    method: "PUT",
    data: attachments,
    saveas: "./",
    network: request.agent.Network.CELLULAR,
    metered: false,
    roaming: true,
    retry: true,
    redirect: true,
    index: 0,
    begins: 0,
    ends: -1,
    gauge: false,
    precise: false,
    token: "it is a secret"
  };
  let createOnCallback = (response: request.agent.HttpResponse) => {
    console.info('upload task response.');
  };
  request.agent.create(context, config).then((task: request.agent.Task) => {
    task.on('response', createOnCallback);
    console.info(`Succeeded in creating a upload task. result: ${task.tid}`);
    task.start();
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### on('faultOccur')<sup>20+</sup>

on(event: 'faultOccur', callback: Callback&lt;Faults&gt;): void

Subscribes to the task failure reason. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

| Name | Type                                  | Mandatory | Description                         |
| -------- |-------------------------------------| -------- |----------------------------|
| event | string                              | Yes | Type of the event to subscribe to.<br>- The value is 'faultOccur', indicating a task failure. |
| callback | Callback&lt;[Faults](#requestagentfaults10)&gt; | Yes | Callback invoked to return the task failure reason when the related event occurs. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';
  
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let attachments: Array<request.agent.FormItem> = [{
    name: "taskOnTest",
    value: {
      filename: "taskOnTest.avi",
      mimeType: "application/octet-stream",
      path: "./taskOnTest.avi",
    }
  }];
  let config: request.agent.Config = {
    action: request.agent.Action.UPLOAD,
    url: 'http://127.0.0.1', // Manually replace the URL with the HTTP address of the real server.
    title: 'taskOnTest',
    description: 'Sample code for event listening',
    mode: request.agent.Mode.FOREGROUND,
    overwrite: false,
    method: "PUT",
    data: attachments,
    saveas: "./",
    network: request.agent.Network.CELLULAR,
    metered: false,
    roaming: true,
    retry: true,
    redirect: true,
    index: 0,
    begins: 0,
    ends: -1,
    gauge: false,
    precise: false,
    token: "it is a secret"
  };
  let faultOnCallback = (faults: request.agent.Faults) => {
    console.info('upload task failed.');
  };
  request.agent.create(context, config).then((task: request.agent.Task) => {
    task.on('faultOccur', faultOnCallback);
    console.info(`Succeeded in creating a upload task. result: ${task.tid}`);
    task.start();
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### on('wait')<sup>20+</sup>

on(event: 'wait', callback: Callback&lt;WaitingReason&gt;): void

Subscribes to the task waiting reason. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the **context** object in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

| Name | Type                                                | Mandatory | Description                              |
| -------- |---------------------------------------------------| -------- |---------------------------------|
| event | string                                            | Yes | Type of the event to subscribe to.<br>- The value is 'wait', indicating that the task is waiting. |
| callback | Callback&lt;[WaitingReason](#requestagentwaitingreason20)&gt; | Yes | Callback invoked when the related event occurs, returning the reason why the task is waiting.      |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';
  
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let attachments: Array<request.agent.FormItem> = [{
    name: "taskOnTest",
    value: {
      filename: "taskOnTest.avi",
      mimeType: "application/octet-stream",
      path: "./taskOnTest.avi",
    }
  }];
  let config: request.agent.Config = {
    action: request.agent.Action.UPLOAD,
    url: 'http://127.0.0.1', // Manually replace the URL with the HTTP address of the real server.
    title: 'taskOnTest',
    description: 'Sample code for event listening',
    mode: request.agent.Mode.FOREGROUND,
    overwrite: false,
    method: "PUT",
    data: attachments,
    saveas: "./",
    network: request.agent.Network.CELLULAR,
    metered: false,
    roaming: true,
    retry: true,
    redirect: true,
    index: 0,
    begins: 0,
    ends: -1,
    gauge: false,
    precise: false,
    token: "it is a secret"
  };
  let waitOnCallback = (reason: request.agent.WaitingReason) => {
    console.info('upload task waiting.');
  };
  request.agent.create(context, config).then((task: request.agent.Task) => {
    task.on('wait', waitOnCallback);
    console.info(`Succeeded in creating a upload task. result: ${task.tid}`);
    task.start();
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### off('progress')<sup>10+</sup>

off(event: 'progress', callback?: (progress: Progress) =&gt; void): void

Unsubscribes from the task progress event.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the **context** in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | event | string | Yes | Type of the event to unsubscribe from.<br>- The value is 'progress', indicating the task progress. |
  | callback | (progress: [Progress](#requestagentprogress10)) => void | No | Callback for the task progress event. If this parameter is not specified, all progress callbacks are unsubscribed from. |


**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |
  | 21900005 | task mode error.<br> Applicable version: 10-10 |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component to ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let attachments: Array<request.agent.FormItem> = [{
    name: "taskOffTest",
    value: {
      filename: "taskOffTest.avi",
      path: "./taskOffTest.avi",
    }
  }];
  let config: request.agent.Config = {
    action: request.agent.Action.UPLOAD,
    url: 'http://127.0.0.1', // Manually replace the URL with the HTTP address of the real server.
    title: 'taskOffTest',
    description: 'Sample code for event listening',
    mode: request.agent.Mode.FOREGROUND,
    overwrite: false,
    method: "PUT",
    data: attachments,
    saveas: "./",
    network: request.agent.Network.CELLULAR,
    metered: false,
    roaming: true,
    retry: true,
    redirect: true,
    index: 0,
    begins: 0,
    ends: -1,
    gauge: false,
    precise: false,
    token: "it is a secret"
  };
  let createOffCallback1 = (progress: request.agent.Progress) => {
    console.info('upload task progress.');
  };
  let createOffCallback2 = (progress: request.agent.Progress) => {
    console.info('upload task progress.');
  };
  request.agent.create(context, config).then((task: request.agent.Task) => {
    task.on('progress', createOffCallback1);
    task.on('progress', createOffCallback2);
    // Unsubscribe from createOffCallback1.
    task.off('progress', createOffCallback1);
    // Unsubscribe from all callbacks for task progress.
    task.off('progress');
    console.info(`Succeeded in creating a upload task. result: ${task.tid}`);
    task.start();
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### off('completed')<sup>10+</sup>

off(event: 'completed', callback?: (progress: Progress) =&gt; void): void

Unsubscribes from the task completion event.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | event | string | Yes | Type of the event to unsubscribe from.<br>- The value is 'completed', indicating task completion. |
  | callback | (progress: [Progress](#requestagentprogress10)) => void | No | Callback for the task completion event. If this parameter is not specified, all completion callbacks are unsubscribed from. |


**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |
  | 21900005 | Operation with wrong task mode.<br> Supported since: 10-10 |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let attachments: Array<request.agent.FormItem> = [{
    name: "taskOffTest",
    value: {
      filename: "taskOffTest.avi",
      path: "./taskOffTest.avi",
    }
  }];
  let config: request.agent.Config = {
    action: request.agent.Action.UPLOAD,
    url: 'http://127.0.0.1', // Manually replace the URL with the HTTP address of the real server.
    title: 'taskOffTest',
    description: 'Sample code for event listening',
    mode: request.agent.Mode.FOREGROUND,
    overwrite: false,
    method: "PUT",
    data: attachments,
    saveas: "./",
    network: request.agent.Network.CELLULAR,
    metered: false,
    roaming: true,
    retry: true,
    redirect: true,
    index: 0,
    begins: 0,
    ends: -1,
    gauge: false,
    precise: false,
    token: "it is a secret"
  };
  let createOffCallback1 = (progress: request.agent.Progress) => {
    console.info('upload task completed.');
  };
  let createOffCallback2 = (progress: request.agent.Progress) => {
    console.info('upload task completed.');
  };
  request.agent.create(context, config).then((task: request.agent.Task) => {
    task.on('completed', createOffCallback1);
    task.on('completed', createOffCallback2);
    // Unsubscribe from createOffCallback1.
    task.off('completed', createOffCallback1);
    // Unsubscribe from all callbacks for task completion.
    task.off('completed');
    console.info(`Succeeded in creating a upload task. result: ${task.tid}`);
    task.start();
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### off('failed')<sup>10+</sup>

off(event: 'failed', callback?: (progress: Progress) =&gt; void): void

Unsubscribes from the task failure event.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | event | string | Yes | Type of the event to unsubscribe from.<br>- The value is 'failed', indicating a task failure. |
  | callback | (progress: [Progress](#requestagentprogress10)) => void | No | Callback for the task failure event. If this parameter is not specified, all failure callbacks are unsubscribed from. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |
  | 21900005 | Operation with wrong task mode.<br> Supported since: 10-10 |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let attachments: Array<request.agent.FormItem> = [{
    name: "taskOffTest",
    value: {
      filename: "taskOffTest.avi",
      path: "./taskOffTest.avi",
    }
  }];
  let config: request.agent.Config = {
    action: request.agent.Action.UPLOAD,
    url: 'http://127.0.0.1', // Manually replace the URL with the HTTP address of the real server.
    title: 'taskOffTest',
    description: 'Sample code for event listening',
    mode: request.agent.Mode.FOREGROUND,
    overwrite: false,
    method: "PUT",
    data: attachments,
    saveas: "./",
    network: request.agent.Network.CELLULAR,
    metered: false,
    roaming: true,
    retry: true,
    redirect: true,
    index: 0,
    begins: 0,
    ends: -1,
    gauge: false,
    precise: false,
    token: "it is a secret"
  };
  let createOffCallback1 = (progress: request.agent.Progress) => {
    console.info('upload task failed.');
  };
  let createOffCallback2 = (progress: request.agent.Progress) => {
    console.info('upload task failed.');
  };
  request.agent.create(context, config).then((task: request.agent.Task) => {
    task.on('failed', createOffCallback1);
    task.on('failed', createOffCallback2);
    // Unsubscribe from createOffCallback1.
    task.off('failed', createOffCallback1);
    // Unsubscribe from all callbacks for task failure.
    task.off('failed');
    console.info(`Succeeded in creating a upload task. result: ${task.tid}`);
    task.start();
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### off('pause')<sup>11+</sup>

off(event: 'pause', callback?: (progress: Progress) =&gt; void): void

Unsubscribes from the task pause event.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | event | string | Yes | Type of the event to unsubscribe from.<br>- The value is 'pause', indicating the task pause event. |
  | callback | (progress: [Progress](#requestagentprogress10)) => void | No | Callback for the pause event. If this parameter is not specified, all callbacks subscribed to the pause event are unsubscribed from. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let attachments: Array<request.agent.FormItem> = [{
    name: "taskOffTest",
    value: {
      filename: "taskOffTest.avi",
      path: "./taskOffTest.avi",
    }
  }];
  let config: request.agent.Config = {
    action: request.agent.Action.UPLOAD,
    url: 'http://127.0.0.1', // Manually replace the URL with the actual HTTP address of the server.
    title: 'taskOffTest',
    description: 'Sample code for event listening',
    mode: request.agent.Mode.FOREGROUND,
    overwrite: false,
    method: "PUT",
    data: attachments,
    saveas: "./",
    network: request.agent.Network.CELLULAR,
    metered: false,
    roaming: true,
    retry: true,
    redirect: true,
    index: 0,
    begins: 0,
    ends: -1,
    gauge: false,
    precise: false,
    token: "it is a secret"
  };
  let createOffCallback1 = (progress: request.agent.Progress) => {
    console.info('upload task pause.');
  };
  let createOffCallback2 = (progress: request.agent.Progress) => {
    console.info('upload task pause.');
  };
  request.agent.create(context, config).then((task: request.agent.Task) => {
    task.on('pause', createOffCallback1);
    task.on('pause', createOffCallback2);
    // Unsubscribe from createOffCallback1.
    task.off('pause', createOffCallback1);
    // Unsubscribe from all callbacks subscribed to the task pause event.
    task.off('pause');
    console.info(`Succeeded in creating a upload task. result: ${task.tid}`);
    task.start();
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### off('resume')<sup>11+</sup>

off(event: 'resume', callback?: (progress: Progress) =&gt; void): void

Unsubscribes from the task resume event.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | event | string | Yes | Type of the event to unsubscribe from.<br>- The value is 'resume', indicating task resume. |
  | callback | (progress: [Progress](#requestagentprogress10)) => void | No | Callback for the task resume event. If this parameter is not specified, all resume callbacks are unsubscribed from. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let attachments: Array<request.agent.FormItem> = [{
    name: "taskOffTest",
    value: {
      filename: "taskOffTest.avi",
      path: "./taskOffTest.avi",
    }
  }];
  let config: request.agent.Config = {
    action: request.agent.Action.UPLOAD,
    url: 'http://127.0.0.1', // Manually replace the URL with the HTTP address of the real server.
    title: 'taskOffTest',
    description: 'Sample code for event listening',
    mode: request.agent.Mode.FOREGROUND,
    overwrite: false,
    method: "PUT",
    data: attachments,
    saveas: "./",
    network: request.agent.Network.CELLULAR,
    metered: false,
    roaming: true,
    retry: true,
    redirect: true,
    index: 0,
    begins: 0,
    ends: -1,
    gauge: false,
    precise: false,
    token: "it is a secret"
  };
  let createOffCallback1 = (progress: request.agent.Progress) => {
    console.info('upload task resume.');
  };
  let createOffCallback2 = (progress: request.agent.Progress) => {
    console.info('upload task resume.');
  };
  request.agent.create(context, config).then((task: request.agent.Task) => {
    task.on('resume', createOffCallback1);
    task.on('resume', createOffCallback2);
    // Unsubscribe from createOffCallback1.
    task.off('resume', createOffCallback1);
    // Unsubscribe from all callbacks of the task resume event.
    task.off('resume');
    console.info(`Succeeded in creating a upload task. result: ${task.tid}`);
    task.start();
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### off('remove')<sup>11+</sup>

off(event: 'remove', callback?: (progress: Progress) =&gt; void): void

Unsubscribes from the task removal event.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | event | string | Yes | Type of the event to unsubscribe from.<br>- The value is 'remove', which indicates that the task is removed. |
  | callback | (progress: [Progress](#requestagentprogress10)) => void | No | Callback for the task removal event. It is invoked when the related event occurs. If this parameter is not specified, all callbacks for the removal event are unsubscribed from. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let attachments: Array<request.agent.FormItem> = [{
    name: "taskOffTest",
    value: {
      filename: "taskOffTest.avi",
      path: "./taskOffTest.avi",
    }
  }];
  let config: request.agent.Config = {
    action: request.agent.Action.UPLOAD,
    url: 'http://127.0.0.1', // Manually replace the URL with the HTTP address of the real server.
    title: 'taskOffTest',
    description: 'Sample code for event listening',
    mode: request.agent.Mode.FOREGROUND,
    overwrite: false,
    method: "PUT",
    data: attachments,
    saveas: "./",
    network: request.agent.Network.CELLULAR,
    metered: false,
    roaming: true,
    retry: true,
    redirect: true,
    index: 0,
    begins: 0,
    ends: -1,
    gauge: false,
    precise: false,
    token: "it is a secret"
  };
  let createOffCallback1 = (progress: request.agent.Progress) => {
    console.info('upload task remove.');
  };
  let createOffCallback2 = (progress: request.agent.Progress) => {
    console.info('upload task remove.');
  };
  request.agent.create(context, config).then((task: request.agent.Task) => {
    task.on('remove', createOffCallback1);
    task.on('remove', createOffCallback2);
    // Unsubscribe from createOffCallback1.
    task.off('remove', createOffCallback1);
    // Unsubscribe from all callbacks for the task removal event.
    task.off('remove');
    console.info(`Succeeded in creating a upload task. result: ${task.tid}`);
    task.start();
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### off('response')<sup>12+</sup>

off(event: 'response', callback?: Callback&lt;HttpResponse&gt;): void

Unsubscribes from the task response event.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | event | string | Yes | Type of the event to unsubscribe from.<br>- The value is 'response', indicating the task response. |
  | callback | Callback&lt;[HttpResponse](#requestagenthttpresponse12)&gt; | No | Callback for the task response event. If this parameter is not specified, all callbacks of the current type are unsubscribed from. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component to ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let attachments: Array<request.agent.FormItem> = [{
    name: "taskOffTest",
    value: {
      filename: "taskOffTest.avi",
      path: "./taskOffTest.avi",
    }
  }];
  let config: request.agent.Config = {
    action: request.agent.Action.UPLOAD,
    url: 'http://127.0.0.1', // Manually replace the URL with the HTTP address of the real server.
    title: 'taskOffTest',
    description: 'Sample code for event listening',
    mode: request.agent.Mode.FOREGROUND,
    overwrite: false,
    method: "PUT",
    data: attachments,
    saveas: "./",
    network: request.agent.Network.CELLULAR,
    metered: false,
    roaming: true,
    retry: true,
    redirect: true,
    index: 0,
    begins: 0,
    ends: -1,
    gauge: false,
    precise: false,
    token: "it is a secret"
  };
  let createOffCallback1 = (progress: request.agent.HttpResponse) => {
    console.info('upload task response.');
  };
  let createOffCallback2 = (progress: request.agent.HttpResponse) => {
    console.info('upload task response.');
  };
  request.agent.create(context, config).then((task: request.agent.Task) => {
    task.on('response', createOffCallback1);
    task.on('response', createOffCallback2);
    // Unsubscribe from createOffCallback1.
    task.off('response', createOffCallback1);
    // Unsubscribe from all callbacks of the task response.
    task.off('response');
    console.info(`Succeeded in creating a upload task. result: ${task.tid}`);
    task.start();
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### off('faultOccur')<sup>20+</sup>

off(event: 'faultOccur', callback?: Callback&lt;Faults&gt;): void

Unsubscribes from the event related to the task failure reason.


**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the **context** in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

| Name | Type                         | Mandatory | Description                                    |
| -------- |----------------------------| -------- |---------------------------------------|
| event | string                     | Yes | Type of the event to subscribe to.<br>- The value is 'faultOccur', which indicates a task failure.      |
| callback | Callback&lt;[Faults](#requestagentfaults10)&gt; | No | Callback for the event to unsubscribe from. If this parameter is not specified, all callbacks of the current type are unsubscribed from by default. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';
  
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let attachments: Array<request.agent.FormItem> = [{
    name: "taskOffTest",
    value: {
      filename: "taskOffTest.avi",
      mimeType: "application/octet-stream",
      path: "./taskOffTest.avi",
    }
  }];
  let config: request.agent.Config = {
    action: request.agent.Action.UPLOAD,
    url: 'http://127.0.0.1', // Manually replace the URL with the HTTP address of the real server.
    title: 'taskOffTest',
    description: 'Sample code for event listening',
    mode: request.agent.Mode.FOREGROUND,
    overwrite: false,
    method: "PUT",
    data: attachments,
    saveas: "./",
    network: request.agent.Network.CELLULAR,
    metered: false,
    roaming: true,
    retry: true,
    redirect: true,
    index: 0,
    begins: 0,
    ends: -1,
    gauge: false,
    precise: false,
    token: "it is a secret"
  };
  let faultOffCallback1 = (faults: request.agent.Faults) => {
    console.info('upload task failed.');
  };
  let faultOffCallback2 = (faults: request.agent.Faults) => {
    console.info('upload task failed.');
  };
  request.agent.create(context, config).then((task: request.agent.Task) => {
    task.on('faultOccur', faultOffCallback1);
    task.on('faultOccur', faultOffCallback2);
    // Unsubscribe from faultOffCallback1.
    task.off('faultOccur', faultOffCallback1);
    // Unsubscribe from all callbacks for the task failure reason.
    task.off('faultOccur');
    console.info(`Succeeded in creating a upload task. result: ${task.tid}`);
    task.start();
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### off('wait')<sup>20+</sup>

off(event: 'wait', callback?: Callback&lt;WaitingReason&gt;): void

Unsubscribes from the event related to the reason why a task is waiting.


**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the **context** object in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

| Name | Type                                | Mandatory | Description                                    |
| -------- |-----------------------------------| -------- |---------------------------------------|
| event | string                            | Yes | Type of the event to subscribe to.<br>- The value is 'wait', indicating that the task is waiting.       |
| callback | Callback&lt;[WaitingReason](#requestagentwaitingreason20)&gt; | No | Callback for the event to unsubscribe from. If this parameter is not specified, all callbacks of the current type are unsubscribed from by default. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';
  
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let attachments: Array<request.agent.FormItem> = [{
    name: "taskOffTest",
    value: {
      filename: "taskOffTest.avi",
      mimeType: "application/octet-stream",
      path: "./taskOffTest.avi",
    }
  }];
  let config: request.agent.Config = {
    action: request.agent.Action.UPLOAD,
    url: 'http://127.0.0.1', // Manually replace the URL with the HTTP address of the real server.
    title: 'taskOffTest',
    description: 'Sample code for event listening',
    mode: request.agent.Mode.FOREGROUND,
    overwrite: false,
    method: "PUT",
    data: attachments,
    saveas: "./",
    network: request.agent.Network.CELLULAR,
    metered: false,
    roaming: true,
    retry: true,
    redirect: true,
    index: 0,
    begins: 0,
    ends: -1,
    gauge: false,
    precise: false,
    token: "it is a secret"
  };
  let waitOffCallback1 = (reason: request.agent.WaitingReason) => {
    console.info('upload task waiting.');
  };
  let waitOffCallback2 = (reason: request.agent.WaitingReason) => {
    console.info('upload task waiting.');
  };
  request.agent.create(context, config).then((task: request.agent.Task) => {
    task.on('wait', waitOffCallback1);
    task.on('wait', waitOffCallback2);
    // Unsubscribe from waitOffCallback1.
    task.off('wait', waitOffCallback1);
    // Unsubscribe from all callbacks for the task waiting event.
    task.off('wait');
    console.info(`Succeeded in creating a upload task. result: ${task.tid}`);
    task.start();
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### start<sup>10+</sup>

start(callback: AsyncCallback&lt;void&gt;): void

Starts a task. This API uses an asynchronous callback.<br>
A task in any of the following states can be started:

1. A task just created by the request.agent.create API.
2. A download task that was created by the request.agent.create API and has failed or stopped.

**Required permissions**: ohos.permission.INTERNET

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;void&gt; | Yes | Callback used to return the result. If the task is started successfully, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | Permission denied. |
  | 13400003 | Task service ability error. |
  | 21900007 | Operation with wrong task state. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component to ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let config: request.agent.Config = {
    action: request.agent.Action.DOWNLOAD,
    url: 'http://127.0.0.1', // Manually replace the URL with the HTTP address of the real server.
    title: 'taskStartTest',
    description: 'Sample code for start the download task',
    mode: request.agent.Mode.BACKGROUND,
    overwrite: false,
    method: "GET",
    data: "",
    saveas: "./",
    network: request.agent.Network.CELLULAR,
    metered: false,
    roaming: true,
    retry: true,
    redirect: true,
    index: 0,
    begins: 0,
    ends: -1,
    gauge: false,
    precise: false,
    token: "it is a secret"
  };
  request.agent.create(context, config).then((task: request.agent.Task) => {
    task.start((err: BusinessError) => {
      if (err) {
        console.error(`Failed to start the download task, Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info(`Succeeded in starting a download task.`);
    });
    console.info(`Succeeded in creating a download task. result: ${task.tid}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a download task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### start<sup>10+</sup>

start(): Promise&lt;void&gt;

Starts a task. This API uses a promise to return the result asynchronously.<br>
Tasks in the following states can be started:

1. A task just created by the request.agent.create API.
2. A download task that was created by the request.agent.create API and has failed or stopped.

**Required permissions**: ohos.permission.INTERNET

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Return value** 

| Type                | Description                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | Permission denied. |
  | 13400003 | Task service ability error. |
  | 21900007 | Operation with wrong task state. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let config: request.agent.Config = {
    action: request.agent.Action.DOWNLOAD,
    url: 'http://127.0.0.1', // Manually replace the URL with the HTTP address of the real server.
    title: 'taskStartTest',
    description: 'Sample code for start the download task',
    mode: request.agent.Mode.BACKGROUND,
    overwrite: false,
    method: "GET",
    data: "",
    saveas: "./",
    network: request.agent.Network.CELLULAR,
    metered: false,
    roaming: true,
    retry: true,
    redirect: true,
    index: 0,
    begins: 0,
    ends: -1,
    gauge: false,
    precise: false,
    token: "it is a secret"
  };
  request.agent.create(context, config).then((task: request.agent.Task) => {
    task.start().then(() => {
      console.info(`Succeeded in starting a download task.`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to start the download task, Code: ${err.code}, message: ${err.message}`);
    });
    console.info(`Succeeded in creating a download task. result: ${task.tid}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a download task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### pause<sup>10+</sup>

pause(callback: AsyncCallback&lt;void&gt;): void

Pauses a task. This API can pause a task that is waiting, running, or retrying. A paused task can be resumed by [resume](#resume10). This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;void&gt; | Yes | Callback used to return the result. If the task is paused successfully, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md).

  | ID | Error Message |
  | -------- | -------- |
  | 13400003 | Task service ability error. |
  | 21900005 | Operation with wrong task mode.<br> Applicable version: 10-10 |
  | 21900007 | Operation with wrong task state. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let config: request.agent.Config = {
    action: request.agent.Action.DOWNLOAD,
    url: 'http://127.0.0.1', // Manually replace the URL with the HTTP address of the real server.
    title: 'taskPauseTest',
    description: 'Sample code for pause the download task',
    mode: request.agent.Mode.BACKGROUND,
    overwrite: false,
    method: "GET",
    data: "",
    saveas: "./",
    network: request.agent.Network.CELLULAR,
    metered: false,
    roaming: true,
    retry: true,
    redirect: true,
    index: 0,
    begins: 0,
    ends: -1,
    gauge: false,
    precise: false,
    token: "it is a secret"
  };
  request.agent.create(context, config).then(async (task: request.agent.Task) => {
    task.start();
    // Wait for 1 second before performing the next operation to prevent asynchronous disorder.
    await new Promise<void>((resolve) => {
      setTimeout(() => resolve(), 1000);
    })
    task.pause((err: BusinessError) => {
      if (err) {
        console.error(`Failed to pause the download task, Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info(`Succeeded in pausing a download task. `);
    });
    console.info(`Succeeded in creating a download task. result: ${task.tid}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a download task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### pause<sup>10+</sup>

pause(): Promise&lt;void&gt;

Pauses the task. This API can pause a task that is waiting, running, or retrying. A paused task can be resumed by [resume](#resume10). This API uses a promise to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

**Return value** 

| Type                | Description                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md).

  | ID | Error Message |
  | -------- | -------- |
  | 13400003 | Task service ability error. |
  | 21900005 | Operation with wrong task mode.<br> Applicable version: 10-10 |
  | 21900007 | Operation with wrong task state. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let config: request.agent.Config = {
    action: request.agent.Action.DOWNLOAD,
    url: 'http://127.0.0.1', // Manually replace the URL with the HTTP address of the real server.
    title: 'taskPauseTest',
    description: 'Sample code for pause the download task',
    mode: request.agent.Mode.BACKGROUND,
    overwrite: false,
    method: "GET",
    data: "",
    saveas: "./",
    network: request.agent.Network.CELLULAR,
    metered: false,
    roaming: true,
    retry: true,
    redirect: true,
    index: 0,
    begins: 0,
    ends: -1,
    gauge: false,
    precise: false,
    token: "it is a secret"
  };
  request.agent.create(context, config).then(async (task: request.agent.Task) => {
    task.start();
    // Wait for 1 second before performing the next step to prevent asynchronous disorder.
    await new Promise<void>((resolve) => {
      setTimeout(() => resolve(), 1000);
    })
    task.pause().then(() => {
      console.info(`Succeeded in pausing a download task. `);
    }).catch((err: BusinessError) => {
      console.error(`Failed to pause the download task, Code: ${err.code}, message: ${err.message}`);
    });
    console.info(`Succeeded in creating a download task. result: ${task.tid}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a download task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### resume<sup>10+</sup>

resume(callback: AsyncCallback&lt;void&gt;): void

Resumes a task. This API can be used to resume a paused task. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;void&gt; | Yes | Callback used to return the result. If the task is resumed successfully, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | Permission denied. |
  | 13400003 | Task service ability error. |
  | 21900005 | Operation with wrong task mode.<br> Applicable version: 10-10 |
  | 21900007 | Operation with wrong task state. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let config: request.agent.Config = {
    action: request.agent.Action.DOWNLOAD,
    url: 'http://127.0.0.1', // Manually replace the URL with the HTTP address of the real server.
    title: 'taskResumeTest',
    description: 'Sample code for resume the download task',
    mode: request.agent.Mode.BACKGROUND,
    overwrite: false,
    method: "GET",
    data: "",
    saveas: "./",
    network: request.agent.Network.CELLULAR,
    metered: false,
    roaming: true,
    retry: true,
    redirect: true,
    index: 0,
    begins: 0,
    ends: -1,
    gauge: false,
    precise: false,
    token: "it is a secret"
  };
  request.agent.create(context, config).then(async (task: request.agent.Task) => {
    task.start();
    // Wait for 1 second before proceeding to the next step to prevent asynchronous disorder.
    await new Promise<void>((resolve) => {
      setTimeout(() => resolve(), 1000);
    })
    task.pause();
    // Wait for 1 second before performing the next operation to prevent asynchronous disorder.
    await new Promise<void>((resolve) => {
      setTimeout(() => resolve(), 1000);
    })
    task.resume((err: BusinessError) => {
      if (err) {
        console.error(`Failed to resume the download task, Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info(`Succeeded in resuming a download task. `);
    });
    console.info(`Succeeded in creating a download task. result: ${task.tid}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a download task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### resume<sup>10+</sup>

resume(): Promise&lt;void&gt;

Resumes the task, that is, resumes a paused task. This API uses a promise to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.Request.FileTransferAgent

**Return value** 

| Type                | Description                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | Permission denied. |
  | 13400003 | Task service ability error. |
  | 21900005 | Operation with wrong task mode.<br> Supported since: 10-10 |
  | 21900007 | Operation with wrong task state. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let config: request.agent.Config = {
    action: request.agent.Action.DOWNLOAD,
    url: 'http://127.0.0.1', // Manually replace the URL with the HTTP address of the real server.
    title: 'taskResumeTest',
    description: 'Sample code for resume the download task',
    mode: request.agent.Mode.BACKGROUND,
    overwrite: false,
    method: "GET",
    data: "",
    saveas: "./",
    network: request.agent.Network.CELLULAR,
    metered: false,
    roaming: true,
    retry: true,
    redirect: true,
    index: 0,
    begins: 0,
    ends: -1,
    gauge: false,
    precise: false,
    token: "it is a secret"
  };
  request.agent.create(context, config).then(async (task: request.agent.Task) => {
    task.start();
    // Wait for 1 second before proceeding to the next step to avoid asynchronous disorder.
    await new Promise<void>((resolve) => {
      setTimeout(() => resolve(), 1000);
    })
    task.pause();
    // Wait for 1 second before proceeding to the next step to avoid asynchronous disorder.
    await new Promise<void>((resolve) => {
      setTimeout(() => resolve(), 1000);
    })
    task.resume().then(() => {
      console.info(`Succeeded in resuming a download task. `);
    }).catch((err: BusinessError) => {
      console.error(`Failed to resume the download task, Code: ${err.code}, message: ${err.message}`);
    });
    console.info(`Succeeded in creating a download task. result: ${task.tid}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a download task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### stop<sup>10+</sup>

stop(callback: AsyncCallback&lt;void&gt;): void

Stops a task. This API can stop a task that is running, waiting, or retrying. A stopped task can be resumed by [start](#start10). This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;void&gt; | Yes | Callback used to return the result. If the task is stopped successfully, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md).

  | ID | Error Message |
  | -------- | -------- |
  | 13400003 | Task service ability error. |
  | 21900007 | Operation with wrong task state. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let config: request.agent.Config = {
    action: request.agent.Action.DOWNLOAD,
    url: 'http://127.0.0.1', // Manually replace the URL with the HTTP address of the real server.
    title: 'taskStopTest',
    description: 'Sample code for stop the download task',
    mode: request.agent.Mode.BACKGROUND,
    overwrite: false,
    method: "GET",
    data: "",
    saveas: "./",
    network: request.agent.Network.CELLULAR,
    metered: false,
    roaming: true,
    retry: true,
    redirect: true,
    index: 0,
    begins: 0,
    ends: -1,
    gauge: false,
    precise: false,
    token: "it is a secret"
  };
  request.agent.create(context, config).then(async (task: request.agent.Task) => {
    task.start();
    // Wait for 1 second before performing the next step to prevent asynchronous disorder.
    await new Promise<void>((resolve) => {
      setTimeout(() => resolve(), 1000);
    })
    task.stop((err: BusinessError) => {
      if (err) {
        console.error(`Failed to stop the download task, Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info(`Succeeded in stopping a download task. `);
    });
    console.info(`Succeeded in creating a download task. result: ${task.tid}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a download task, Code: ${err.code}, message: ${err.message}`);
  });
  ```


### stop<sup>10+</sup>

stop(): Promise&lt;void&gt;

Stops a task. This API can stop a task that is running, waiting, or retrying. A stopped task can be resumed by [start](#start10). This API uses a promise to return the result asynchronously.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

**Return value** 

| Type               | Description                     |
| ------------------- | ------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md).

  | ID | Error Message |
  | -------- | -------- |
  | 13400003 | Task service ability error. |
  | 21900007 | Operation with wrong task state. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let config: request.agent.Config = {
    action: request.agent.Action.DOWNLOAD,
    url: 'http://127.0.0.1', // Manually replace the URL with the HTTP address of the real server.
    title: 'taskStopTest',
    description: 'Sample code for stop the download task',
    mode: request.agent.Mode.BACKGROUND,
    overwrite: false,
    method: "GET",
    data: "",
    saveas: "./",
    network: request.agent.Network.CELLULAR,
    metered: false,
    roaming: true,
    retry: true,
    redirect: true,
    index: 0,
    begins: 0,
    ends: -1,
    gauge: false,
    precise: false,
    token: "it is a secret"
  };
  request.agent.create(context, config).then(async (task: request.agent.Task) => {
    task.start();
    // Wait for 1 second before the next step to prevent asynchronous disorder.
    await new Promise<void>((resolve) => {
      setTimeout(() => resolve(), 1000);
    })
    task.stop().then(() => {
      console.info(`Succeeded in stopping a download task. `);
    }).catch((err: BusinessError) => {
      console.error(`Failed to stop the download task, Code: ${err.code}, message: ${err.message}`);
    });
    console.info(`Succeeded in creating a download task. result: ${task.tid}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a download task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### setMaxSpeed<sup>18+</sup>

setMaxSpeed(speed: number): Promise\<void\>

Sets the maximum number of bytes that a task can transfer per second. This API uses a promise to return the result asynchronously.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

| Name  | Type  | Mandatory | Description                                                                           |
|-------|-------|-----------|---------------------------------------------------------------------------------------|
| speed | number | Yes       | Maximum number of bytes that a task can transfer per second, in bytes per second (B/s). The minimum value is 16384 bytes per second, and the value range is [16384, +∞). The value must not be lower than the minimum speed set by [MinSpeed](#requestagentminspeed20). If a value smaller than the minimum is passed in, an error code is returned. |

**Return value**

| Type              | Description                         |
|-------------------|-------------------------------------|
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID    | Error Message                 |
|----------|------------------------------------------------------------------------------------------------------|
| 401      | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |
| 13400003 | Task service ability error.     |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component to ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let config: request.agent.Config = {
    action: request.agent.Action.DOWNLOAD,
    url: 'http://127.0.0.1', // Manually replace the URL with the HTTP address of the real server.
    saveas: "./",
  };
  request.agent.create(context, config).then((task: request.agent.Task) => {
    // Set the maximum task speed.
    task.setMaxSpeed(10 * 1024 * 1024).then(() => {
      console.info(`Succeeded in setting the max speed of the task. result: ${task.tid}`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to set the max speed of the task. Code: ${err.code}, message: ${err.message}`);
    });
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a download task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

## request.agent.create<sup>10+</sup>

create(context: BaseContext, config: Config, callback: AsyncCallback&lt;Task&gt;): void

Creates a task for upload or download and places it in the queue. HTTP and HTTPS are supported. This API uses an asynchronous callback. After the task is created, call [start](#start10) to start the task.


**Required permissions**: ohos.permission.INTERNET

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | context | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes | Context based on the application. |
  | config | [Config](#requestagentconfig10) | Yes | Configuration information of the upload/download task. |
  | callback | AsyncCallback&lt;[Task](#requestagenttask10)&gt; | Yes | Callback function. If the upload or download task is created successfully, **err** is **undefined** and **data** is the obtained **Task** object; otherwise, **data** is an error object. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | Permission denied. |
  | 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |
  | 13400001 | Invalid file or file system error. |
  | 13400003 | Task service ability error.    |
  | 21900004 | The application task queue is full. |
  | 21900005 | Operation with wrong task mode. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let attachments: Array<request.agent.FormItem> = [{
    name: "createTest",
    value: {
      filename: "createTest.avi",
      path: "./createTest.avi",
    }
  }];
  let config: request.agent.Config = {
    action: request.agent.Action.UPLOAD,
    url: 'http://127.0.0.1', // Manually replace the URL with the HTTP address of the real server.
    title: 'createTest',
    description: 'Sample code for create task',
    mode: request.agent.Mode.BACKGROUND,
    overwrite: false,
    method: "PUT",
    data: attachments,
    saveas: "./",
    network: request.agent.Network.CELLULAR,
    metered: false,
    roaming: true,
    retry: true,
    redirect: true,
    index: 0,
    begins: 0,
    ends: -1,
    gauge: false,
    precise: false,
    token: "it is a secret"
  };
  request.agent.create(context, config, async (err: BusinessError, task: request.agent.Task) => {
    if (err) {
      console.error(`Failed to create an upload task, Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in creating an upload task. result: ${task.config}`);
    await task.start();
    // The user needs to manually call remove to end the lifecycle of the task object.
    request.agent.remove(task.tid);
  });
  ```

## request.agent.create<sup>10+</sup>

create(context: BaseContext, config: Config): Promise&lt;Task&gt;

Creates a task for upload or download and places it in the queue. HTTP and HTTPS are supported. This API uses a promise to return the result asynchronously. After the task is created, call [start](#start10) to start the task.


**Required permissions**: ohos.permission.INTERNET

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | context | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes | Context based on the application. |
  | config | [Config](#requestagentconfig10) | Yes | Configuration information of the upload/download task. |

**Return value** 

| Type                | Description                      |
| ------------------- | ------------------------- |
| Promise&lt;[Task](#requestagenttask10)&gt; | Promise used to return the **Task** object. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 201 | Permission denied. |
  | 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |
  | 13400001 | Invalid file or file system error. |
  | 13400003 | Task service ability error. |
  | 21900004 | The application task queue is full. |
  | 21900005 | Operation with wrong task mode. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let attachments: Array<request.agent.FormItem> = [{
    name: "createTest",
    value: {
      filename: "createTest.avi",
      path: "./createTest.avi",
    }
  }];
  let config: request.agent.Config = {
    action: request.agent.Action.UPLOAD,
    url: 'http://127.0.0.1', // Manually replace the URL with the HTTP address of the real server.
    title: 'createTest',
    description: 'Sample code for create task',
    mode: request.agent.Mode.BACKGROUND,
    overwrite: false,
    method: "PUT",
    data: attachments,
    saveas: "./",
    network: request.agent.Network.CELLULAR,
    metered: false,
    roaming: true,
    retry: true,
    redirect: true,
    index: 0,
    begins: 0,
    ends: -1,
    gauge: false,
    precise: false,
    token: "it is a secret"
  };
  request.agent.create(context, config).then(async (task: request.agent.Task) => {
    console.info(`Succeeded in creating an upload task. result: ${task.config}`);
    await task.start();
    // The user needs to manually call remove to end the lifecycle of the task object.
    request.agent.remove(task.tid);
  }).catch((err: BusinessError) => {
    console.error(`Failed to create an upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

## request.agent.getTask<sup>11+</sup>

getTask(context: BaseContext, id: string, token?: string): Promise&lt;Task&gt;

Queries a task by task ID. This API uses a promise to return the result asynchronously.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | context | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes | Context based on the application program. |
  | id | string | Yes | Task ID. |
  | token | string | No | Task query token. If a token is set when the task is created, the corresponding token must be provided to query the task; otherwise, the specified task cannot be queried. The default value is empty (if not passed, only tasks without a token can be queried). |

**Return value** 

| Type                | Description                      |
| ------------------- | ------------------------- |
| Promise&lt;[Task](#requestagenttask10)&gt; | Promise object. Promise object used to return the task configuration information. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |
  | 13400003 | Task service ability error. |
  | 21900006 | Task removed or not found. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  request.agent.getTask(context, '123456').then((task: request.agent.Task) => {
    console.info(`Succeeded in querying a task. result: ${task.tid}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to query a task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

## request.agent.remove<sup>10+</sup>

remove(id: string, callback: AsyncCallback&lt;void&gt;): void

Removes the specified task that belongs to the caller. If the task is being processed, it is forcibly stopped. This API uses an asynchronous callback. After the call, the task object and its callback function are released.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | id | string | Yes | Task ID. |
  | callback | AsyncCallback&lt;void&gt; | Yes | Callback used to return the result. If the specified task is removed successfully, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. |
  | 13400003 | Task service ability error. |
  | 21900006 | Task removed or not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  request.agent.remove('123456', (err: BusinessError) => {
    if (err) {
      console.error(`Failed to remove a download task, Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in removing a download task.`);
  });
  ```


## request.agent.remove<sup>10+</sup>

remove(id: string): Promise&lt;void&gt;

Removes the specified task of the caller. If the task is being processed, it is forcibly stopped. This API uses a promise to return the result asynchronously. After the API is called, the task object and its callback function are released.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | id | string | Yes | Task ID. |

**Return value** 

| Type                | Description                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. |
  | 13400003 | Task service ability error. |
  | 21900006 | Task removed or not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  request.agent.remove('123456').then(() => {
    console.info(`Succeeded in removing a download task. `);
  }).catch((err: BusinessError) => {
    console.error(`Failed to remove a download task, Code: ${err.code}, message: ${err.message}`);
  });
  ```


## request.agent.show<sup>10+</sup>

show(id: string, callback: AsyncCallback&lt;TaskInfo&gt;): void

Queries the detailed information of a task by task ID. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | id | string | Yes | Task ID. |
  | callback | AsyncCallback&lt;[TaskInfo](#requestagenttaskinfo10)&gt; | Yes | Callback function. When the task query operation succeeds, err is undefined and data is the queried TaskInfo information; otherwise, an error object is returned. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. |
  | 13400003 | Task service ability error. |
  | 21900006 | Task removed or not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  request.agent.show('123456', (err: BusinessError, taskInfo: request.agent.TaskInfo) => {
    if (err) {
      console.error(`Failed to show a upload task, Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in showing a upload task.`);
  });
  ```


## request.agent.show<sup>10+</sup>

show(id: string): Promise&lt;TaskInfo&gt;

Queries the detailed information of a task based on the task ID. This API uses a promise to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | id | string | Yes | Task ID. |

**Return value** 

| Type                | Description                      |
| ------------------- | ------------------------- |
| Promise&lt;[TaskInfo](#requestagenttaskinfo10)&gt; | Promise used to return the detailed task information, which is a TaskInfo object. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. |
  | 13400003 | Task service ability error. |
  | 21900006 | Task removed or not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  request.agent.show('123456').then((taskInfo: request.agent.TaskInfo) => {
    console.info(`Succeeded in showing a upload task.`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to show a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```


## request.agent.touch<sup>10+</sup>

touch(id: string, token: string, callback: AsyncCallback&lt;TaskInfo&gt;): void

Queries the detailed information of a task based on the task ID and token. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | id | string | Yes | Task ID. |
  | token | string | Yes | Task query token. |
  | callback | AsyncCallback&lt;[TaskInfo](#requestagenttaskinfo10)&gt; | Yes | Callback used to return the result. If the task query operation is successful, **err** is **undefined** and **data** is the queried **TaskInfo** object. Otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |
  | 13400003 | Task service ability error. |
  | 21900006 | Task removed or not found.  |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  request.agent.touch('123456', "token", (err: BusinessError, taskInfo: request.agent.TaskInfo) => {
    if (err) {
      console.error(`Failed to touch a upload task, Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in touching a upload task.`);
  });
  ```


## request.agent.touch<sup>10+</sup>

touch(id: string, token: string): Promise&lt;TaskInfo&gt;

Queries the detailed information of a task based on the task ID and token. This API uses a promise to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | id | string | Yes | Task ID. |
  | token | string | Yes | Task query token. |

**Return value** 

| Type                | Description                      |
| ------------------- | ------------------------- |
| Promise&lt;[TaskInfo](#requestagenttaskinfo10)&gt; | Promise used to return the detailed task information TaskInfo. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |
  | 13400003 | Task service ability error. |
  | 21900006 | Task removed or not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  request.agent.touch('123456', "token").then((taskInfo: request.agent.TaskInfo) => {
    console.info(`Succeeded in touching a upload task. `);
  }).catch((err: BusinessError) => {
    console.error(`Failed to touch a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

## request.agent.search<sup>10+</sup>

search(callback: AsyncCallback&lt;Array&lt;string&gt;&gt;): void

Searches for task IDs based on the default [Filter](#requestagentfilter10) conditions, that is, queries the task IDs of all tasks from the call time to 24 hours ago. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | Yes | Callback function. If the task is found based on the filter conditions, err is undefined and data is the task IDs that meet the conditions; otherwise, an error object is returned. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | Parameter error. Possible causes: 1. Incorrect parameter type. 2. Parameter verification failed. |
  | 13400003 | Task service ability error. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  request.agent.search((err: BusinessError, data: Array<string>) => {
    if (err) {
      console.error(`Failed to search a upload task, Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in searching a upload task. `);
  });
  ```

## request.agent.search<sup>10+</sup>

search(filter: Filter, callback: AsyncCallback&lt;Array&lt;string&gt;&gt;): void

Searches for task IDs based on the [Filter](#requestagentfilter10) criteria. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | filter | [Filter](#requestagentfilter10) | Yes | Filter criteria. |
  | callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | Yes | Callback invoked to return the result. If the search succeeds, **err** is **undefined** and **data** is the array of task IDs that meet the criteria; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | Parameter error. Possible causes: 1. Incorrect parameter type. 2. Parameter verification failed. |
  | 13400003 | Task service ability error. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  let filter: request.agent.Filter = {
    action: request.agent.Action.UPLOAD,
    mode: request.agent.Mode.BACKGROUND
  };
  request.agent.search(filter, (err: BusinessError, data: Array<string>) => {
    if (err) {
      console.error(`Failed to search a upload task, Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in searching a upload task. `);
  });
  ```


## request.agent.search<sup>10+</sup>

search(filter?: Filter): Promise&lt;Array&lt;string&gt;&gt;

Searches for task IDs based on the filter conditions in [Filter](#requestagentfilter10). This API uses a promise to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | filter | [Filter](#requestagentfilter10) | No | Filter conditions. The default value is empty. |

**Return value** 

| Type                | Description                      |
| ------------------- | ------------------------- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the task IDs that meet the conditions. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID | Error Message |
  | -------- | -------- |
  | 401 | Parameter error. Possible causes: 1. Incorrect parameter type. 2. Parameter verification failed. |
  | 13400003 | Task service ability error. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  let filter: request.agent.Filter = {
    action: request.agent.Action.UPLOAD,
    mode: request.agent.Mode.BACKGROUND
  }
  request.agent.search(filter).then((data: Array<string>) => {
    console.info(`Succeeded in searching a upload task. `);
  }).catch((err: BusinessError) => {
    console.error(`Failed to search a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

## request.agent.createGroup<sup>15+</sup>

createGroup(config: GroupConfig): Promise\<string\>

Creates a group based on the grouping conditions in [GroupConfig](#requestagentgroupconfig15) and returns the group ID. This API is applicable to scenarios where notifications of multiple download tasks need to be displayed in a combined manner and task progress notifications need to be managed in a unified way. This API uses a promise to return the result asynchronously.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

| Name    | Type                                          | Mandatory | Description        |
|--------|---------------------------------------------|----|-----------|
| config | [GroupConfig<sup>15+</sup>](#requestagentgroupconfig15) | Yes  | Grouping options of the download task. |

**Return value**

| Type                | Description                               |
|-------------------|----------------------------------|
| Promise\<string\> | Promise object. Returns the ID of the created group. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID    | Error Message                                                                                           |
|----------|------------------------------------------------------------------------------------------------|
| 401      | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |
| 13400003 | Task service ability error.             |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  // Prepare the GroupConfig object for the grouping options.
  let config: request.agent.GroupConfig = {
      notification: {},
  };
  // Call createGroup to create a group.
  request.agent.createGroup(config).then((gid: string) => {
    console.info(`Succeeded in creating a download task group. `);
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a download group, Code: ${err.code}, message: ${err.message}`);
  });
  ```

## request.agent.attachGroup<sup>15+</sup>

attachGroup(gid: string, tids: string[]): Promise\<void\>

Binds multiple download task IDs to a specified group ID, so that multiple download tasks can be grouped together for unified management of notification display. This API uses a promise to return the result asynchronously.

If any task ID does not meet the adding conditions (for example, the task does not exist, the task status does not match, or the task mode does not match), none of the tasks in the list will be added to the group.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

| Name | Type | Mandatory | Description |
|------|----------|----|---------------------|
| gid  | string   | Yes  | Target group ID.             |
| tids | string[] | Yes  | List of task IDs to bind. |

**Return value**

| Type              | Description         |
|-----------------|------------|
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID    | Error Message                                                                                           |
|----------|------------------------------------------------------------------------------------------------|
| 401      | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |
| 13400003 | Task service ability error.               |
| 21900005 | Operation with wrong task mode.           |
| 21900006 | Task removed or not found.                |
| 21900007 | Operation with wrong task state.          |
| 21900008 | Group deleted or not found.               |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  // Prepare the group ID and the task ID list.
  let groupId: string = '123456789';
  let taskIds: string[] = ['1111', '2222', '3333', '4444'];
  // Call attachGroup to add the task ID list to the group.
  request.agent.attachGroup(groupId, taskIds).then(() => {
    console.info(`Succeeded in attaching tasks to the download task group.`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to attach tasks to the download group, Code: ${err.code}, message: ${err.message}`);
  });
  ```

## request.agent.deleteGroup<sup>15+</sup>

deleteGroup(gid: string): Promise\<void\>

Removes a specified group. After the group is removed, task IDs can no longer be added to it. This API uses a promise to return the result asynchronously.

When all tasks in the group are in the completed, failed, or removed state and the group is removed, the completion or failure notification of the group is displayed.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

| Name | Type | Mandatory | Description |
|------|----------|----|---------|
| gid | string | Yes | ID of the target group. It must be the same as the ID of the created task group, that is, the return value of the [request.agent.createGroup](#requestagentcreategroup15) API when the task group is created successfully. |

**Return value**

| Type | Description |
|-----------------|------------|
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID    | Error Message                                                                                           |
|----------|------------------------------------------------------------------------------------------------|
| 401      | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |
| 13400003 | Task service ability error.           |
| 21900008 | Group deleted or not found.           |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  // Prepare the group ID.
  let groupId: string = '123456789';
  
  // Call deleteGroup to remove the group.
  request.agent.deleteGroup(groupId).then(() => {
    console.info(`Succeeded in deleting the download task group.`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to delete the download group, Code: ${err.code}, message: ${err.message}`);
  });
  ```