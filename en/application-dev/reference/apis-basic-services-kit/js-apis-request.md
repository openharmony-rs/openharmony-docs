# @ohos.request (Upload and Download)
<!--Kit: Basic Services Kit-->
<!--Subsystem: Request-->
<!--Owner: @huaxin05-->
<!--Designer: @hu-kai45-->
<!--Tester: @murphy1984-->
<!--Adviser: @zhang_yixin13-->

The request module provides applications with basic upload, download, and background transmission agent capabilities.

- Currently, the **request** module cannot be called in extensions.

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
> **Network type**: custom network type specified by **networkType** in [DownloadConfig](#downloadconfig).<br>
>
> **Download error codes**: values of **err** in the [on('fail')](#onfail7) callback and the values of the **failedReason** field returned by [getTaskInfo](#gettaskinfo9).<br>
>
> **Causes of download pause**: values of **pausedReason** returned by [getTaskInfo](#gettaskinfo9).<br>
>
> **Download status code**: values of **status** returned by [getTaskInfo](#gettaskinfo9).

| Name| Type| Value| Description|
| -------- | -------- | -------- | -------- |
| EXCEPTION_PERMISSION<sup>9+</sup> | number |   201   | (Universal error codes) Permission verification failed.|
| EXCEPTION_PARAMCHECK<sup>9+</sup> | number |   401   | (Universal error codes) Parameter check failed.|
| EXCEPTION_UNSUPPORTED<sup>9+</sup> | number |   801   | (Universal error codes) The device does not support this API.|
| EXCEPTION_FILEIO<sup>9+</sup> | number |   13400001   | (Specific error codes) Abnormal file operation.|
| EXCEPTION_FILEPATH<sup>9+</sup> | number |   13400002   | (Specific error codes) Abnormal file path.|
| EXCEPTION_SERVICE<sup>9+</sup> | number |   13400003   | (Specific error codes) Abnormal service.|
| EXCEPTION_OTHERS<sup>9+</sup> | number |   13499999   | (Specific error codes) Other errors.|
| NETWORK_MOBILE<sup>6+</sup> | number | 0x00000001 | (Network type) Bit flag download allowed on a mobile network.|
| NETWORK_WIFI<sup>6+</sup> | number | 0x00010000 | (Network type) Bit flag download allowed on a WLAN.|
| ERROR_CANNOT_RESUME<sup>7+</sup> | number |   0   | (Download error codes) Failure to resume the download due to network errors.|
| ERROR_DEVICE_NOT_FOUND<sup>7+</sup> | number |   1   | (Download error codes) Failure to find a storage device such as a memory card.|
| ERROR_FILE_ALREADY_EXISTS<sup>7+</sup> | number |   2   | (Download error codes) Failure to download the file because it already exists.|
| ERROR_FILE_ERROR<sup>7+</sup> | number |   3   | (Download error codes) File operation failed.|
| ERROR_HTTP_DATA_ERROR<sup>7+</sup> | number |   4   | (Download error codes) HTTP transmission failed.|
| ERROR_INSUFFICIENT_SPACE<sup>7+</sup> | number |   5   | (Download error codes) Insufficient storage space.|
| ERROR_TOO_MANY_REDIRECTS<sup>7+</sup> | number |   6   | (Download error codes) Error caused by too many network redirections.|
| ERROR_UNHANDLED_HTTP_CODE<sup>7+</sup> | number |   7   | (Download error codes) Unidentified HTTP code.|
| ERROR_UNKNOWN<sup>7+</sup> | number |   8   | (Download error codes) Unknown error.<br>In API version 12 or earlier, only serial connection to the IP addresses associated with the specified domain name is supported, and the connection time for a single IP address is not controllable. If the first IP address returned by the DNS is blocked, a handshake timeout may occur, leading to an ERROR_UNKNOWN error.|
| ERROR_OFFLINE<sup>9+</sup> | number |   9   | (Download error codes) No network connection.|
| ERROR_UNSUPPORTED_NETWORK_TYPE<sup>9+</sup> | number |   10   | (Download error codes) Network type mismatch.|
| PAUSED_QUEUED_FOR_WIFI<sup>7+</sup> | number |   0   | (Causes of download pause) Download paused and queuing for a WLAN connection because the file size exceeds the maximum value allowed for a mobile network session.|
| PAUSED_WAITING_FOR_NETWORK<sup>7+</sup> | number |   1   | (Causes of download pause) Download paused due to a network connection problem.<br>Example: network disconnection|
| PAUSED_WAITING_TO_RETRY<sup>7+</sup> | number |   2   | (Causes of download pause) Download paused due to network error and then retried.|
| PAUSED_BY_USER<sup>9+</sup> | number |   3   | (Causes of download pause) The user paused the session.|
| PAUSED_UNKNOWN<sup>7+</sup> | number |   4   | (Causes of download pause) Download paused due to unknown reasons.|
| SESSION_SUCCESSFUL<sup>7+</sup> | number |   0   | (Download task status codes) Successful download.|
| SESSION_RUNNING<sup>7+</sup> | number |   1   | (Download task status codes) Download in progress.|
| SESSION_PENDING<sup>7+</sup> | number |   2   | (Download task status codes) Download pending.|
| SESSION_PAUSED<sup>7+</sup> | number |   3   | (Download task status codes) Download paused.|
| SESSION_FAILED<sup>7+</sup> | number |   4   | (Download task status codes) Download failure without retry.|
| VISIBILITY_COMPLETION<sup>21+</sup> | number |   1   | ([Notification](#notification15) visibility type) Completion notification displayed.|
| VISIBILITY_PROGRESS<sup>21+</sup>   | number |   2   | ([Notification](#notification15) visibility type) Notification progress displayed.|


## request.uploadFile<sup>9+</sup>

uploadFile(context: BaseContext, config: UploadConfig): Promise&lt;UploadTask&gt;

Uploads a file. This API uses a promise to return the result. HTTP is supported. You can use [on('complete'|'fail')](#oncomplete--fail9) to obtain the upload success or error information.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Upload

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| context | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes| Application-based context.|
| config | [UploadConfig](#uploadconfig6) | Yes| Upload configurations.|


**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;[UploadTask](#uploadtask)&gt; | Promise used to return the **UploadTask** object.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | The permissions check fails. |
| 401 | The parameters check fails. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |
| 13400002 | File path not supported or invalid. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';
  
  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let uploadTask: request.UploadTask;
  let uploadConfig: request.UploadConfig = {
    url: 'http://www.example.com', // Replace the URL with the HTTP address of the real server.
    header: { 'Accept': '*/*' },
    method: "POST",
    files: [{ filename: "test", name: "test", uri: "internal://cache/test.jpg", type: "image/jpeg" }], // Set type to the MIME type of the HTTP protocol.
    data: [{ name: "name123", value: "123" }],
  };
  try {
    request.uploadFile(context, uploadConfig).then((data: request.UploadTask) => {
      uploadTask = data;
    }).catch((err: BusinessError) => {
      console.error(`Failed to request the upload. Code: ${err.code}, message: ${err.message}`);
    });
  } catch (err) {
    console.error(`Failed to request the upload. err: ${JSON.stringify(err)}`);
  }
  ```


## request.uploadFile<sup>9+</sup>

uploadFile(context: BaseContext, config: UploadConfig, callback: AsyncCallback&lt;UploadTask&gt;): void

Uploads a file. This API uses an asynchronous callback to return the result. HTTP is supported. You can use [on('complete'|'fail')](#oncomplete--fail9) to obtain the upload success or error information.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Upload

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| context | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes| Application-based context.|
| config | [UploadConfig](#uploadconfig6) | Yes| Upload configurations.|
| callback | AsyncCallback&lt;[UploadTask](#uploadtask)&gt; | Yes| Callback used to return the **UploadTask** object. If the operation is successful, **err** is **undefined**, and **data** is the **UploadTask** object obtained. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | The permissions check fails. |
| 401 | The parameters check fails. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |
| 13400002 | File path not supported or invalid. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let uploadTask: request.UploadTask;
  let uploadConfig: request.UploadConfig = {
    url: 'http://www.example.com', // Replace the URL with the HTTP address of the real server.
    header: { 'Accept': '*/*' },
    method: "POST",
    files: [{ filename: "test", name: "test", uri: "internal://cache/test.jpg", type: "image/jpeg" }], // Set type to the MIME type of the HTTP protocol.
    data: [{ name: "name123", value: "123" }],
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
    console.error(`Failed to request the upload. err: ${JSON.stringify(err)}`);
  }
  ```

## request.upload<sup>(deprecated)</sup>

upload(config: UploadConfig): Promise&lt;UploadTask&gt;

Uploads files. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the FA model.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Upload

> **NOTE**
>
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [request.uploadFile](#requestuploadfile9) instead.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| config | [UploadConfig](#uploadconfig6) | Yes| Upload configurations.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;[UploadTask](#uploadtask)&gt; | Promise used to return the **UploadTask** object.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | The permissions check fails. |

**Example**

  ```js
  let uploadTask: request.UploadTask;
  let uploadConfig: request.UploadConfig = {
    url: 'http://www.example.com', // Replace the URL with the HTTP address of the real server.
    header: { 'Accept': '*/*' },
    method: "POST",
    files: [{ filename: "test", name: "test", uri: "internal://cache/test.jpg", type: "image/jpeg" }], // Set type to the MIME type of the HTTP protocol.
    data: [{ name: "name123", value: "123" }],
  };
  request.upload(uploadConfig).then((data: request.UploadTask) => {
    uploadTask = data;
  }).catch((err: BusinessError) => {
    console.error(`Failed to request the upload. Code: ${err.code}, message: ${err.message}`);
  })
  ```


## request.upload<sup>(deprecated)</sup>

upload(config: UploadConfig, callback: AsyncCallback&lt;UploadTask&gt;): void

Uploads files. This API uses an asynchronous callback to return the result.

**Model restriction**: This API can be used only in the FA model.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Upload

> **NOTE**
>
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [request.uploadFile](#requestuploadfile9) instead.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| config | [UploadConfig](#uploadconfig6) | Yes| Upload configurations.|
| callback | AsyncCallback&lt;[UploadTask](#uploadtask)&gt; | Yes| Callback used to return the **UploadTask** object. If the operation is successful, **err** is **undefined**, and **data** is the **UploadTask** object obtained. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | The permissions check fails. |

**Example**

  ```js
  let uploadTask: request.UploadTask;
  let uploadConfig: request.UploadConfig = {
    url: 'http://www.example.com', // Replace the URL with the HTTP address of the real server.
    header: { 'Accept': '*/*' },
    method: "POST",
    files: [{ filename: "test", name: "test", uri: "internal://cache/test.jpg", type: "image/jpeg" }], // Set type to the MIME type of the HTTP protocol.
    data: [{ name: "name123", value: "123" }],
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

Implements file uploads. Before using any APIs of this class, you must obtain an **UploadTask** object, from a promise through [request.uploadFile](#requestuploadfile9) or from a callback through [request.uploadFile](#requestuploadfile9-1).



### on('progress')

on(type: 'progress', callback: (uploadedSize: number, totalSize: number) =&gt; void): void

Subscribes to upload progress events. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.Upload

> **NOTE**
>
> To maintain a balance between power consumption and performance, this API cannot be called when the application is running in the background.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Event type. The value is fixed at **'progress'**, indicating upload progress.|
| callback | function | Yes| Callback used to return the size of the uploaded file and the total size of the file to upload.|

  Parameters of the callback function

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| uploadedSize | number | Yes| Size of the uploaded files, in bytes.|
| totalSize | number | Yes| Total size of the files to upload, in bytes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | The parameters check fails. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

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

Subscribes to HTTP response events for the upload task.This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.Upload

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Event type.<br>- **'headerReceive'**: The HTTP request receives a response.|
| callback | function | Yes| Callback used to return the response content.|

  Parameters of the callback function

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| header | object | Yes| HTTP response.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | The parameters check fails. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

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

Subscribes to upload completion or failure events. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.Upload

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Type of the event to subscribe to. The options are as follows:<br>\- **'complete'**: upload task completion.<br>\- **'fail'**: upload task failure.|
| callback | Callback&lt;Array&lt;[TaskState](#taskstate9)&gt;&gt; | Yes| Callback used to return the result.  |


**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | The parameters check fails. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

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

Unsubscribes from upload progress events.

**System capability**: SystemCapability.MiscServices.Upload

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Event type.<br>- **'progress'**: upload progress.|
| callback | function | No| Callback to unregister. If this parameter is not specified, all callbacks of the current type will be unregistered.|

Parameters of the callback function

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| uploadedSize | number | Yes| Size of the uploaded files, in bytes.|
| totalSize | number | Yes| Total size of the files to upload, in bytes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | The parameters check fails. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

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
  // Unsubscribe from all callbacks of upload progress events.
  uploadTask.off('progress');
  ```


### off('headerReceive')<sup>7+</sup>

off(type: 'headerReceive', callback?: (header: object) =&gt; void): void

Unsubscribes from HTTP response events for the upload task.

**System capability**: SystemCapability.MiscServices.Upload

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Event type.<br>- **'headerReceive'**: The HTTP request receives a response.|
| callback | function | No| Callback to unregister. If this parameter is not specified, all callbacks of the current type will be unregistered.|

  Parameters of the callback function

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| header | object | Yes| HTTP response.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | The parameters check fails. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

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
  // Unsubscribe from all callbacks of the HTTP header events for the upload task.
  uploadTask.off('headerReceive');
  ```

### off('complete' | 'fail')<sup>9+</sup>

 off(type: 'complete' | 'fail', callback?: Callback&lt;Array&lt;TaskState&gt;&gt;): void

Unsubscribes from upload completion or failure events.

**System capability**: SystemCapability.MiscServices.Upload

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Event type.<br>- **'complete'**: upload task completion.<br>- **'fail'**: upload task failure.|
| callback | Callback&lt;Array&lt;[TaskState](#taskstate9)&gt;&gt; | No| Callback to unregister. If this parameter is not specified, all callbacks of the current type will be unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | The parameters check fails. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

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
  // Unsubscribe from headerCallback1.
  uploadTask.off('complete', upCompleteCallback1);
  // Unsubscribe from all callbacks of the upload completion events.
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
  // Unsubscribe from headerCallback1.
  uploadTask.off('fail', upFailCallback1);
  // Unsubscribe from all callbacks of the upload failure events.
  uploadTask.off('fail');
  ```

### delete<sup>9+</sup>
delete(): Promise&lt;boolean&gt;

Deletes this upload task. This API uses a promise to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Upload

> **NOTE**
>
> The scenarios for triggering error code **401 the parameters check fails** do not exist. Therefore, this error code is removed from API version 12.

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the operation is successful; **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
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

Deletes an upload task. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Upload

> **NOTE**
>
> The scenarios for triggering error code **401 the parameters check fails** do not exist. Therefore, this error code is removed from API version 12.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;boolean&gt; | Yes| Callback used to return the result. The value **true** indicates that the operation is successful; **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
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

Removes this upload task. This API uses a promise to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Upload

> **NOTE**
>
> This API is deprecated since API version 9. You are advised to use [delete](#delete9) instead.

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the operation is successful; **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
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
> This API is deprecated since API version 9. You are advised to use [delete](#delete9-1) instead.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;boolean&gt; | Yes| Callback used to return the result. The value **true** indicates that the operation is successful; **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
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

## UploadConfig<sup>6+</sup>
Describes the configuration of an upload task.

**System capability**: SystemCapability.MiscServices.Upload

| Name  | Type    | Read-Only| Optional| Description                           |
|------|--------|----|----|-------------------------------|
| url | string | No| No| Resource URL. From API version 6 to 14, the value contains a maximum of 2048 characters; since API version 15, the value contains a maximum of 8192 characters. [Intercepting HTTP](../../basic-services/request/app-file-upload-download.md#intercepting-http) is supported.|
| header | Object | No| No| HTTP or HTTPS header added to an upload request.|
| method | string | No| No|  HTTP request method. The value can be **POST** or **PUT**. The default value is **POST**. Use **POST** to add resources and **PUT** to modify resources.|
| index<sup>11+</sup> | number | No| Yes| Path index of the task. The default value is **0**.|
| begins<sup>11+</sup> | number | No| Yes| Start point of the file read when the upload task begins. The default value is **0**. The value is a closed interval, indicating that the file is read from the beginning.|
| ends<sup>11+</sup> | number | No| Yes| End point of the file read when the upload task is complete. The default value is **-1**. The value is a closed interval, indicating that the file is read till the end.|
| files | Array&lt;[File](#file)&gt; | No| No| List of files to upload. The files are submitted in multipart/form-data format.|
| data | Array&lt;[RequestData](#requestdata)&gt; | No| No| Form data in the request body.|

## TaskState<sup>9+</sup>
Implements a **TaskState** object, which is the callback parameter of the [on('complete' | 'fail')](#oncomplete--fail9) and [off('complete' | 'fail')](#offcomplete--fail9) APIs.

**System capability**: SystemCapability.MiscServices.Upload

| Name  | Type    | Read-Only| Optional| Description                           |
|------|--------|----|----|-------------------------------|
| path | string | No| No| File path.                                        |
| responseCode | number | No| No| Return value of an upload task. The value **0** means that the task is successful, and other values means that the task fails. For details about the task result, see **message**.<br>You are advised to create an upload task by using [request.agent.create](#requestagentcreate10-1) and handle exceptions based on standard error codes.|
| message | string | No| No| Description of the upload task result.                          |

The following table describes the enum values of **responseCode**.

| Result Code| Description                              |
|-----|------------------------------------|
| 0   | uploaded success.                              |
| 5   | Task suspended or stopped proactively.                        |
| 6   | Foreground task stopped. The reason is that the application, to which the task belongs, is switched to the background or terminated. Check the application status. |
| 7   | No network connection. Check whether the device is connected to the network.                 |
| 8   | Network mismatch. Check whether the current network type matches the network type required by the task.    |
| 10  | Failed to create the HTTP request. Verify the parameters or try again.         |
| 12  | Request timeout. Verify the parameter configuration or the network connection, or try again.         |
| 13  | Connection failed. Verify the parameter configuration or the network connection, or try again.       |
| 14  | Request failed. Verify the parameter configuration or the network connection, or try again.       |
| 15  | Upload failed. Verify the parameter configuration or the network connection, or try again.       |
| 16  | Redirection failed. Verify the parameter configuration or the network connection, or try again.      |
| 17  | Protocol error. The server returns a 4XX or 5XX status code. Verify the parameter configuration and try again.|
| 20  | Other errors. Verify the parameter configuration or the network connection, or try again.       |

## File
Defines the list of files in [UploadConfig](#uploadconfig6).

**System capability**: SystemCapability.MiscServices.Download

| Name  | Type    | Read-Only| Optional| Description                           |
|------|--------|----|----|-------------------------------|
| filename | string | No| No| File name in the header when **multipart** is used.|
| name | string | No| No| Name of a form item when **multipart** is used. The default value is **file**.|
| uri | string | No| No| Local path for storing files.<br>Only **internal://cache/** is supported, that is, **context.cacheDir** of the caller (namely, cache directory of the input **context**).<br>Example: **internal://cache/path/to/file.txt**.|
| type | string | No| No| Type of the file content. By default, the type is obtained based on the extension of the file name or URI.|


## RequestData
Defines the form data in [UploadConfig](#uploadconfig6).

**System capability**: SystemCapability.MiscServices.Download

| Name  | Type    | Read-Only| Optional| Description                           |
|------|--------|----|----|-------------------------------|
| name | string | No| No| Name of a form element.|
| value | string | No| No| Value of a form element.|

## request.downloadFile<sup>9+</sup>

downloadFile(context: BaseContext, config: DownloadConfig): Promise&lt;DownloadTask&gt;

Downloads a file. This API uses a promise to return the result. HTTP is supported. You can use [on('complete'|'pause'|'remove')](#oncompletepauseremove7) to obtain the download task state, which can be completed, paused, or removed. You can also use [on('fail')](#onfail7) to obtain the task download error information.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| context | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes| Application-based context.|
| config | [DownloadConfig](#downloadconfig) | Yes| Download configuration.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;[DownloadTask](#downloadtask)&gt; | Promise used to return the **DownloadTask** object.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
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

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Replace the URL with the HTTP address of the real server.
    request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
       let downloadTask: request.DownloadTask = data;
    }).catch((err: BusinessError) => {
      console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
    })
  } catch (err) {
    console.error(`Failed to request the download. err: ${JSON.stringify(err)}`);
  }
  ```


## request.downloadFile<sup>9+</sup>

downloadFile(context: BaseContext, config: DownloadConfig, callback: AsyncCallback&lt;DownloadTask&gt;): void

Downloads a file. This API uses an asynchronous callback to return the result. HTTP is supported. You can use [on('complete'|'pause'|'remove')](#oncompletepauseremove7) to obtain the download task state, which can be completed, paused, or removed. You can also use [on('fail')](#onfail7) to obtain the task download error information.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| context | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes| Application-based context.|
| config | [DownloadConfig](#downloadconfig) | Yes| Download configuration.|
| callback | AsyncCallback&lt;[DownloadTask](#downloadtask)&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the **DownloadTask** object obtained. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
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

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Replace the URL with the HTTP address of the real server.
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
    console.error(`Failed to request the download. err: ${JSON.stringify(err)}`);
  }
  ```

## request.download<sup>(deprecated)</sup>

download(config: DownloadConfig): Promise&lt;DownloadTask&gt;

Download files. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the FA model.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [request.downloadFile](#requestdownloadfile9) instead.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| config | [DownloadConfig](#downloadconfig) | Yes| Download configuration.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;[DownloadTask](#downloadtask)&gt; | Promise used to return the **DownloadTask** object.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | The permissions check fails. |

**Example**

  ```js
  let downloadTask: request.DownloadTask;
  // Replace the URL with the HTTP address of the real server.
  request.download({ url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
    downloadTask = data;
  }).catch((err: BusinessError) => {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  })
  ```


## request.download<sup>(deprecated)</sup>

download(config: DownloadConfig, callback: AsyncCallback&lt;DownloadTask&gt;): void

Downloads files. This API uses an asynchronous callback to return the result.

**Model restriction**: This API can be used only in the FA model.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> This API is supported since API version 6 and is deprecated since API version 9. You are advised to use [request.downloadFile](#requestdownloadfile9-1) instead.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| config | [DownloadConfig](#downloadconfig) | Yes| Download configuration.|
| callback | AsyncCallback&lt;[DownloadTask](#downloadtask)&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the **DownloadTask** object obtained. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | The permissions check fails. |

**Example**

  ```js
  let downloadTask: request.DownloadTask;
  // Replace the URL with the HTTP address of the real server.
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

Implements file downloads. Before using any APIs of this class, you must obtain a **DownloadTask** object, from a promise through [request.downloadFile](#requestdownloadfile9) or from a callback through [request.downloadFile](#requestdownloadfile9-1).


### on('progress')

on(type: 'progress', callback: (receivedSize: number, totalSize: number) =&gt; void): void

Subscribes to download progress events. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> To maintain a balance between power consumption and performance, this API cannot be called when the application is running in the background.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Event type.<br>- **'progress'**: download progress.|
| callback | function | Yes| Callback used to return the size of the uploaded file and the total size of the file to upload.|

  Parameters of the callback function

| Name| Type| Mandatory| Description                                                                     |
| -------- | -------- | -------- |----------------------------------|
| receivedSize | number | Yes| Current download progress, in bytes.               |
| totalSize | number | Yes| Total size of the files to download, in bytes. If the server uses the chunk mode for data transmission and the total file size cannot be obtained from the request header, the value of **totalSize** is treated as **-1**.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | The parameters check fails. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Replace the URL with the HTTP address of the real server.
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
    console.error(`Failed to request the download. err: ${JSON.stringify(err)}`);
  }
  ```


### off('progress')

off(type: 'progress', callback?: (receivedSize: number, totalSize: number) =&gt; void): void

Unsubscribes from download progress events.

**System capability**: SystemCapability.MiscServices.Download

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Event type.<br>- **'progress'**: download progress.|
| callback | function | No| Callback to unregister. If this parameter is not specified, all callbacks of the current type will be unregistered.|

  Parameters of the callback function

| Name| Type| Mandatory| Description                                                                     |
| -------- | -------- | -------- |------------------------------------|
| receivedSize | number | Yes| Current download progress, in bytes.          |
| totalSize | number | Yes| Total size of the files to download, in bytes. If the server uses the chunk mode for data transmission and the total file size cannot be obtained from the request header, the value of **totalSize** is treated as **-1**.|


**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | The parameters check fails. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Replace the URL with the HTTP address of the real server.
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
      // Unsubscribe from all callbacks of download progress events.
      downloadTask.off('progress');
    }).catch((err: BusinessError) => {
      console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
    })
  } catch (err) {
    console.error(`Failed to request the download. err: ${JSON.stringify(err)}`);
  }
  ```


### on('complete'|'pause'|'remove')<sup>7+</sup>

on(type: 'complete'|'pause'|'remove', callback: () =&gt; void): void

Subscribes to download events. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.Download

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Event type.<br>- **'complete'**: download task completion.<br>- **'pause'**: download task pause.<br>- **'remove'**: download task removal.|
| callback | function | Yes| Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | The parameters check fails. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Replace the URL with the HTTP address of the real server.
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
    console.error(`Failed to request the download. err: ${JSON.stringify(err)}`);
  }
  ```


### off('complete'|'pause'|'remove')<sup>7+</sup>

off(type: 'complete'|'pause'|'remove', callback?: () =&gt; void): void

Unsubscribes from download events.

**System capability**: SystemCapability.MiscServices.Download

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Event type.<br>- **'complete'**: download task completion.<br>- **'pause'**: download task pause.<br>- **'remove'**: download task removal.|
| callback | function | No| Callback to unregister. If this parameter is not specified, all callbacks of the current type will be unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | The parameters check fails. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Replace the URL with the HTTP address of the real server.
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
      // Unsubscribe from all callbacks of the download completion events.
      downloadTask.off('complete');

      let pauseCallback1 = () => {
        console.info('Download delete pause notification.');
      };
      let pauseCallback2 = () => {
        console.info('Download delete pause notification.');
      };
      downloadTask.on('pause', pauseCallback1);
      downloadTask.on('pause', pauseCallback2);
      // Unsubscribe from pauseCallback1.
      downloadTask.off('pause', pauseCallback1);
      // Unsubscribe from all callbacks of the download pause events.
      downloadTask.off('pause');

      let removeCallback1 = () => {
        console.info('Download delete remove notification.');
      };
      let removeCallback2 = () => {
        console.info('Download delete remove notification.');
      };
      downloadTask.on('remove', removeCallback1);
      downloadTask.on('remove', removeCallback2);
      // Unsubscribe from removeCallback1.
      downloadTask.off('remove', removeCallback1);
      // Unsubscribe from all callbacks of the download removal events.
      downloadTask.off('remove');
    }).catch((err: BusinessError) => {
      console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
    })
  } catch (err) {
    console.error(`Failed to request the download. err: ${JSON.stringify(err)}`);
  }  
  ```


### on('fail')<sup>7+</sup>

on(type: 'fail', callback: (err: number) =&gt; void): void

Subscribes to download failure events. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.Download

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Event type.<br>- **'fail'**: download task failure.|
| callback | function | Yes| Callback for the download task failure event.|

  Parameters of the callback function

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| err | number | Yes| Error code of the download failure. For details about the error codes, see [Download Error Codes](#constants).|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | The parameters check fails. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Replace the URL with the HTTP address of the real server.
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
    console.error(`Failed to request the download. err: ${JSON.stringify(err)}`);
  }
  ```


### off('fail')<sup>7+</sup>

off(type: 'fail', callback?: (err: number) =&gt; void): void

Unsubscribes from download failure events.

**System capability**: SystemCapability.MiscServices.Download

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Event type.<br>- **'fail'**: download task failure.|
| callback | function | No| Callback to unregister. If this parameter is not specified, all callbacks of the current type will be unregistered.|

  Parameters of the callback function

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| err | number | Yes| Error code of the download failure. For details about the error codes, see [Download Error Codes](#constants).|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | The parameters check fails. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Replace the URL with the HTTP address of the real server.
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
      // Unsubscribe from all callbacks of the download failure events.
      downloadTask.off('fail');
    }).catch((err: BusinessError) => {
      console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
    })
  } catch (err) {
    console.error(`Failed to request the download. err: ${JSON.stringify(err)}`);
  }
  ```

### delete<sup>9+</sup>

delete(): Promise&lt;boolean&gt;

Deletes this download task. This API uses a promise to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> The scenarios for triggering error code **401 the parameters check fails** do not exist. Therefore, this error code is removed from API version 12.

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the operation is successful; **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | The permissions check fails. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Replace the URL with the HTTP address of the real server.
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
    console.error(`Failed to request the download. err: ${JSON.stringify(err)}`);
  }
  ```

### delete<sup>9+</sup>

delete(callback: AsyncCallback&lt;boolean&gt;): void

Deletes a download task. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> The scenarios for triggering error code **401 the parameters check fails** do not exist. Therefore, this error code is removed from API version 12.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;boolean&gt; | Yes| Callback used to return the result. The value **true** indicates that the operation is successful; **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | The permissions check fails. |


**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Replace the URL with the HTTP address of the real server.
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
    console.error(`Failed to request the download. err: ${JSON.stringify(err)}`);
  }
  ```

### getTaskInfo<sup>9+</sup>

getTaskInfo(): Promise&lt;DownloadInfo&gt;

Obtains the information about this download task. This API uses a promise to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> The scenarios for triggering error code **401 the parameters check fails** do not exist. Therefore, this error code is removed from API version 12.

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;[DownloadInfo](#downloadinfo7)&gt; |  Promise used to return a **DownloadInfo** object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | The permissions check fails. |


**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Replace the URL with the HTTP address of the real server.
    request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
      let downloadTask: request.DownloadTask = data;
      downloadTask.getTaskInfo().then((downloadInfo: request.DownloadInfo) => {
        console.info('Succeeded in querying the download task')
      }).catch((err: BusinessError) => {
        console.error(`Failed to query the download task. Code: ${err.code}, message: ${err.message}`)
      });
    }).catch((err: BusinessError) => {
      console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
    })
  } catch (err) {
    console.error(`Failed to request the download. err: ${JSON.stringify(err)}`);
  } 
  ```

### getTaskInfo<sup>9+</sup>

getTaskInfo(callback: AsyncCallback&lt;DownloadInfo&gt;): void

Obtains the information about this download task. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> The scenarios for triggering error code **401 the parameters check fails** do not exist. Therefore, this error code is removed from API version 12.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;[DownloadInfo](#downloadinfo7)&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the **DownloadInfo** object obtained. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | The permissions check fails. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Replace the URL with the HTTP address of the real server.
    request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
      let downloadTask: request.DownloadTask = data;
      downloadTask.getTaskInfo((err: BusinessError, downloadInfo: request.DownloadInfo) => {
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
    console.error(`Failed to request the download. err: ${JSON.stringify(err)}`);
  }
  ```

### getTaskMimeType<sup>9+</sup>

getTaskMimeType(): Promise&lt;string&gt;

Obtains the MIME type (that is, media type of resources in HTTP) of a download task. This API uses a promise to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> The scenarios for triggering error code **401 the parameters check fails** do not exist. Therefore, this error code is removed from API version 12.

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;string&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | The permissions check fails. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Replace the URL with the HTTP address of the real server.
    request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
      let downloadTask: request.DownloadTask = data;
      downloadTask.getTaskMimeType().then((data: string) => {
        console.info('Succeeded in querying the download MimeType');
      }).catch((err: BusinessError) => {
        console.error(`Failed to query the download MimeType. Code: ${err.code}, message: ${err.message}`)
      });
    }).catch((err: BusinessError) => {
      console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
    })
  } catch (err) {
    console.error(`Failed to request the download. err: ${JSON.stringify(err)}`);
  }
  ```

### getTaskMimeType<sup>9+</sup>

getTaskMimeType(callback: AsyncCallback&lt;string&gt;): void

Obtains the MIME type (that is, media type of resources in HTTP) of a download task. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> The scenarios for triggering error code **401 the parameters check fails** do not exist. Therefore, this error code is removed from API version 12.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;string&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined** and data is the **MimeType** object obtained. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | The permissions check fails. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Replace the URL with the HTTP address of the real server.
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
    console.error(`Failed to request the download. err: ${JSON.stringify(err)}`);
  }
  ```

### suspend<sup>9+</sup>

suspend(): Promise&lt;boolean&gt;

Suspends this download task. You can use [restore](#restore9) to restore the download. This API uses a promise to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> The scenarios for triggering error code **401 the parameters check fails** do not exist. Therefore, this error code is removed from API version 12.

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the operation is successful; **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | The permissions check fails. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Replace the URL with the HTTP address of the real server.
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
    console.error(`Failed to request the download. err: ${JSON.stringify(err)}`);
  }
  ```

### suspend<sup>9+</sup>

suspend(callback: AsyncCallback&lt;boolean&gt;): void

Suspends this download task. You can use [restore](#restore9) to restore the download. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> The scenarios for triggering error code **401 the parameters check fails** do not exist. Therefore, this error code is removed from API version 12.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;boolean&gt; | Yes| Callback used to return the result. The value **true** indicates that the operation is successful; **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | The permissions check fails. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Replace the URL with the HTTP address of the real server.
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
    console.error(`Failed to request the download. err: ${JSON.stringify(err)}`);
  }
  ```

### restore<sup>9+</sup>

restore(): Promise&lt;boolean&gt;

Restores this download task. This API uses a promise to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> The scenarios for triggering error code **401 the parameters check fails** do not exist. Therefore, this error code is removed from API version 12.

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the operation is successful; **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | The permissions check fails. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Replace the URL with the HTTP address of the real server.
    request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
      let downloadTask: request.DownloadTask = data;
      downloadTask.restore().then((result: boolean) => {
        console.info('Succeeded in resuming the download task.')
      }).catch((err: BusinessError) => {
        console.error(`Failed to resume the download task. Code: ${err.code}, message: ${err.message}`);
      });
    }).catch((err: BusinessError) => {
      console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
    })
  } catch (err) {
    console.error(`Failed to request the download. err: ${JSON.stringify(err)}`);
  }
  ```

### restore<sup>9+</sup>

restore(callback: AsyncCallback&lt;boolean&gt;): void

Restores a download task. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> The scenarios for triggering error code **401 the parameters check fails** do not exist. Therefore, this error code is removed from API version 12.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;boolean&gt; | Yes| Callback used to return the result. The value **true** indicates that the operation is successful; **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | The permissions check fails. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // Replace the URL with the HTTP address of the real server.
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
    console.error(`Failed to request the download. err: ${JSON.stringify(err)}`);
  }
  ```

### remove<sup>(deprecated)</sup>

remove(): Promise&lt;boolean&gt;

Removes this download task. This API uses a promise to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> This API is deprecated since API version 9. You are advised to use [delete](#delete9-2) instead.

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the operation is successful; **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
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

Removes a download task. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> This API is deprecated since API version 9. You are advised to use [delete](#delete9-3) instead.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;boolean&gt; | Yes| Callback used to return the result. The value **true** indicates that the operation is successful; **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | The permissions check fails. |

**Example**

  ```js
  downloadTask.remove((err, result)=>{
    if(err) {
      console.error(`Failed to remove the download task. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in removing the download task.');
  });
  ```


### query<sup>(deprecated)</sup>

query(): Promise&lt;DownloadInfo&gt;

Queries this download task. This API uses a promise to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> This API is supported since API version 7 and is deprecated since API version 9. You are advised to use [getTaskInfo](#gettaskinfo9) instead.

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;[DownloadInfo](#downloadinfo7)&gt; | Promise used to return the **DownloadInfo** object.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | The permissions check fails. |

**Example**

  ```js
  downloadTask.query().then((downloadInfo) => {    
    console.info('Succeeded in querying the download task.')
  }).catch((err: BusinessError) => {
    console.error(`Failed to query the download task. Code: ${err.code}, message: ${err.message}`)
  });
  ```


### query<sup>(deprecated)</sup>

query(callback: AsyncCallback&lt;DownloadInfo&gt;): void

Queries this download task. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> This API is supported since API version 7 and is deprecated since API version 9. You are advised to use [getTaskInfo](#gettaskinfo9-1) instead.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;[DownloadInfo](#downloadinfo7)&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the **DownloadInfo** object obtained. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | The permissions check fails. |

**Example**

  ```js
  downloadTask.query((err: BusinessError, downloadInfo: request.DownloadInfo)=>{
    if(err) {
      console.error(`Failed to query the download mimeType. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('Succeeded in querying the download task.');
    }
  });
  ```


### queryMimeType<sup>(deprecated)</sup>

queryMimeType(): Promise&lt;string&gt;

Queries the MIME type of this download task. This API uses a promise to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> This API is supported since API version 7 and is deprecated since API version 9. You are advised to use [getTaskMimeType](#gettaskmimetype9) instead.

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;string&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | The permissions check fails. |

**Example**

  ```js
  downloadTask.queryMimeType().then((data: string) => {    
    console.info('Succeeded in querying the download MimeType.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to query the download MimeType. Code: ${err.code}, message: ${err.message}`)
  });
  ```


### queryMimeType<sup>(deprecated)</sup>

queryMimeType(callback: AsyncCallback&lt;string&gt;): void

Queries the MIME type of this download task. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> This API is supported since API version 7 and is deprecated since API version 9. You are advised to use [getTaskMimeType](#gettaskmimetype9-1) instead.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;string&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined** and data is the **MimeType** object obtained. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | The permissions check fails. |

**Example**

  ```js
  downloadTask.queryMimeType((err: BusinessError, data: string)=>{
    if(err) {
      console.error(`Failed to query the download mimeType. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('Succeeded in querying the download mimeType.');
    }
  });
  ```


### pause<sup>(deprecated)</sup>

pause(): Promise&lt;void&gt;

Pauses this download task. This API uses a promise to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> This API is supported since API version 7 and is deprecated since API version 9. You are advised to use [suspend](#suspend9) instead.

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | The permissions check fails. |

**Example**

  ```js
  downloadTask.pause().then((result: boolean) => {    
    console.info('Succeeded in pausing the download task.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to pause the download task. Code: ${err.code}, message: ${err.message}`);
  });
  ```


### pause<sup>(deprecated)</sup>

pause(callback: AsyncCallback&lt;void&gt;): void

Pauses this download task. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> This API is supported since API version 7 and is deprecated since API version 9. You are advised to use [suspend](#suspend9-1) instead.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | The permissions check fails. |

**Example**

  ```js
  downloadTask.pause((err: BusinessError, result: boolean)=>{
    if(err) {
      console.error(`Failed to pause the download task. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in pausing the download task.');
  });
  ```


### resume<sup>(deprecated)</sup>

resume(): Promise&lt;void&gt;

Resumes this download task. This API uses a promise to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> This API is supported since API version 7 and is deprecated since API version 9. You are advised to use [restore](#restore9) instead.

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | The permissions check fails. |

**Example**

  ```js
  downloadTask.resume().then((result: boolean) => {
    console.info('Succeeded in resuming the download task.')
  }).catch((err: BusinessError) => {
    console.error(`Failed to resume the download task. Code: ${err.code}, message: ${err.message}`);
  });
  ```


### resume<sup>(deprecated)</sup>

resume(callback: AsyncCallback&lt;void&gt;): void

Resumes a download task. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> This API is supported since API version 7 and is deprecated since API version 9. You are advised to use [restore](#restore9-1) instead.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | The permissions check fails. |

**Example**

  ```js
  downloadTask.resume((err: BusinessError, result: boolean)=>{
    if (err) {
      console.error(`Failed to resume the download task. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in resuming the download task.');
  });
  ```


## DownloadConfig
Defines the download task configuration.

**System capability**: SystemCapability.MiscServices.Download

| Name  | Type    | Read-Only| Optional| Description                           |
|------|--------|----|----|-------------------------------|
| url | string | No| No| Resource URL. From API version 6 to 14, the value contains a maximum of 2048 characters; since API version 15, the value contains a maximum of 8192 characters. [Intercepting HTTP](../../basic-services/request/app-file-upload-download.md#intercepting-http) is supported.|
| header | Object | No| Yes| HTTPS flag header to be included in the download request.|
| enableMetered | boolean | No| Yes| Whether download is allowed on a metered connection. The value **true** means the download is allowed, and **false** means the opposite. The default value is **false**.<br>**Note:** In general cases, a mobile data connection is metered, while a Wi-Fi connection is not.|
| enableRoaming | boolean | No| Yes| Whether download is allowed on a roaming network. The value **true** means the download is allowed, and **false** means the opposite. The default value is **false**.|
| description | string | No| Yes| Description of the download session. The default value is an empty string.|
| filePath<sup>7+</sup> | string | No| Yes| Path where the downloaded file is stored. The default value is the cache directory of the caller (that is, the input **context**). The default file name is the part truncated from the last slash (/) in the URL.<br>- In the FA model, use [context](../apis-ability-kit/js-apis-inner-app-context.md#contextgetcachedir) to obtain the application storage path.<br>- In the stage model, use [AbilityContext](../apis-ability-kit/js-apis-inner-application-context.md) to obtain the application storage path.|
| networkType | number | No| Yes| Network type allowed for download. The default value can be **NETWORK_MOBILE** or **NETWORK_WIFI**.<br>- **NETWORK_MOBILE**: 0x00000001<br>- **NETWORK_WIFI**: 0x00010000|
| title | string | No| Yes| Download task name.|
| background<sup>9+</sup> | boolean | No| Yes| Whether to enable the background task notification. When this parameter is enabled, the download status is displayed in the notification panel. The value **true** means the parameter is enabled, and **false** means the opposite. The default value is **false**.|


## DownloadInfo<sup>7+</sup>
Defines the download task information, which is the callback parameter of the [getTaskInfo](#gettaskinfo9) API.

**System capability**: SystemCapability.MiscServices.Download

| Name  | Type    | Read-Only| Optional| Description                           |
|------|--------|----|----|-------------------------------|
| downloadId | number | No| No| Download task ID.|
| failedReason | number| No| No| Cause of the download failure. The value can be any constant in [Download Error Codes](#constants).|
| fileName | string | No| No| Name of the downloaded file.|
| filePath | string | No| No| URI of the saved file.|
| pausedReason | number | No| No| Cause of download pause. The value can be any constant in [Causes of Download Pause](#constants).|
| status | number | No| No| Download task status code. The value can be any constant in [Download Task Status Codes](#constants).|
| targetURI | string | No| No| URI of the downloaded file.|
| downloadTitle | string | No| No| Name of the download task.|
| downloadTotalBytes | number | No| No| Total size of the files to download, in bytes.|
| description | string | No| No| Description of the download task.|
| downloadedBytes | number | No| No| Real-time download size, in bytes.|

## Action<sup>10+</sup>  

Defines action options.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name| Value|Description|
| -------- | -------- |-------- |
| DOWNLOAD | 0 |Download.|
| UPLOAD | 1 |Upload.|


## Mode<sup>10+</sup>  
Defines mode options.<br>
After foreground tasks of an application are switched to the background for a period of time, background tasks are not affected but foreground tasks will fail or pause.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name| Value|Description|
| -------- | -------- |-------- |
| BACKGROUND | 0 |Background task.|
| FOREGROUND | 1 |Foreground task.|

## Network<sup>10+</sup>  

Defines network options.<br>
If the network does not meet the preset conditions, the tasks that have not been executed will await for execution, and the tasks that are being executed will fail or pause.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name| Value|Description|
| -------- | -------- |-------- |
| ANY | 0 |Network of any type.|
| WIFI | 1 |Wi-Fi network.|
| CELLULAR | 2 |Cellular data network.|

## BroadcastEvent<sup>11+</sup>

Defines a custom system event. You can use a common event API to obtain the event.
The upload and download SA has the ohos.permission.SEND_TASK_COMPLETE_EVENT permission. You can configure the level-2 configuration file to which the metadata of an event points to intercept other event senders.

Use the **CommonEventData** type to transmit data related to common events. The members in **CommonEventData** are different from those described in [CommonEventData](js-apis-inner-commonEvent-commonEventData.md). Specifically, **CommonEventData.code** indicates the task status, which is **0x40 COMPLETE** or **0x41 FAILED**, and **CommonEventData.data** indicates the task ID.

<!--Del-->
For details about how to obtain the event configuration and configure the level-2 configuration file, see [Subscribing to Common Events in Static Mode (for System Applications Only)](../../basic-services/common-event/common-event-static-subscription.md).<!--DelEnd-->

**System capability**: SystemCapability.Request.FileTransferAgent

| Name| Value| Description       |
| -------- | ------- |-----------|
| COMPLETE | ohos.request.event.COMPLETE | Task completion event. The returned event code can be **0x40** or **0x41**, depending on whether the task is successful or fails.|

## FileSpec<sup>10+</sup> 
Provides the file information of a table item.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name  | Type    | Read-Only| Optional| Description                           |
|------|--------|----|----|-------------------------------|
| path | string | No| No| File path.<br>- Relative path, which is in the cache directory of the caller.<br>Example: **./xxx/yyy/zzz.html** or **xxx/yyy/zzz.html**<br>- Internal protocol path, which can be **internal://** or its subdirectory. **internal** indicates the cache directory of the caller (that is, the input **context**), and **internal://cache** corresponds to **context.cacheDir**.<br>Example: **internal://cache/path/to/file.txt**<br>- Application sandbox directory. Only the **base** directory and its subdirectories are supported.<br>Example: **/data/storage/el1/base/path/to/file.txt**<br>- File protocol path, which must match the application bundle name. Only the **base** directory and its subdirectories are supported.<br>Example: **file://com.example.test/data/storage/el2/base/file.txt**<br>- Public files of users. Only upload tasks and foreground tasks are supported<br>Example: **file://media/Photo/path/to/file.img**  <br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| mimeType<sup>(deprecated)</sup> | string | No| Yes| MIME type of the file, which is obtained from the file name. The default value is the file name extension.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br> This API is deprecated since API version 18. You are advised to use **contentType** instead.|
| contentType<sup>18+</sup> | string | No| Yes| Content type of the file. The default value is the file name extension. This option is filled in the **Content-Type** field specified in the HTTP form.|
| filename | string | No| Yes| File name. The default value is obtained from the file path.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| extras | object | No| Yes| Additional information. This parameter is not included in HTTP requests.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|


## FormItem<sup>10+</sup> 
Describes the form item of a task.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name  | Type    | Read-Only| Optional| Description                           |
|------|--------|----|----|-------------------------------|
| name | string | No| No| Form parameter name.|
| value | string \| [FileSpec](#filespec10) \| Array&lt;[FileSpec](#filespec10)&gt; | No| No| Form parameter value.|


## Config<sup>10+</sup> 
Provides the configuration information of an upload or download task.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name  | Type    | Read-Only| Optional| Description                           |
|------|--------|----|----|-------------------------------|
| action | [Action](#action10) | No| No| Task action.<br>- **UPLOAD**: Upload tasks.<br>- **DOWNLOAD**: Download tasks.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| url | string | No| No| Resource URL. From API version 6 to 14, the value contains a maximum of 2048 characters; since API version 15, the value contains a maximum of 8192 characters. [Intercepting HTTP](../../basic-services/request/app-file-upload-download.md#intercepting-http) is supported.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| title | string | No| Yes| Task title. The value contains a maximum of 256 characters. The default value is **upload** or **download** in lowercase. Set the value to that of **action**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| description | string | No| Yes| Task description. The value contains a maximum of 1024 characters. The default value is a null string.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| mode | [Mode](#mode10) | No| Yes| Task mode. The default mode is background. Since API version 20, the task mode for downloading files to the user file folder must be set to **request.agent.Mode.FOREGROUND**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| overwrite | boolean | No| Yes| Whether to overwrite an existing file during the download. The default value is **false**.<br>- **true**: Overwrite the existing file.<br>- **false**: Do not overwrite the existing file. In this case, the download fails.<br>Since API version 20, the overwrite mode for downloading files to the user file folder must be set to **true**.<br>In this case, do not create multiple tasks to download content to the same file at a time. Otherwise, the file content will be disordered.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| method | string | No| Yes| Standard HTTP method for the task. The value can be **GET**, **POST**, or **PUT**, which is case-insensitive.<br>- For the upload task, use **PUT** or **POST**. The default value is **PUT**.<br>- For the download task, use **GET** or **POST**. The default value is **GET**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| headers | object | No| Yes| HTTP headers to be included in the task.<br>- For the upload task, the default **Content-Type** is **multipart/form-data**.<br>- For the download task, the default **Content-Type** is **application/json**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| data | string \| Array&lt;[FormItem](#formitem10)&gt; | No| Yes| - For the download task, the value is a string, typically in JSON format (an object will be converted to a JSON string); the default value is null.<br>- For the upload task, the value is Array&lt;[FormItem](#formitem10)&gt;. Since API version 15, a maximum of 100 files can be uploaded in a single task. This parameter is left empty by default.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| saveas | string | No| Yes| Path for storing downloaded files. The options are as follows:<br>- Relative path, which is in the cache directory of the caller, for example, **./xxx/yyy/zzz.html** or **xxx/yyy/zzz.html**.<br>- Internal protocol path, which can be **internal://** or its subdirectory. **internal** indicates the cache directory of the caller (that is, the input **context**), and **internal://cache** corresponds to **context.cacheDir**, for example, **internal://cache/path/to/file.txt**.<br>- Application sandbox path. Only the **base** directory and its subdirectories are supported, for example, **/data/storage/el1/base/path/to/file.txt**.<br>- File protocol path, which can be the path of an application file or a user file. For the application file, the application bundle name must be matched and only the **base** directory and its subdirectories are supported, for example, **file://com.example.test/data/storage/el2/base/file.txt**. For the user file, its path must be the user file URI created by the caller.<br>Since API version 20, the default file path can be the cache path of the caller (that is, the passed context), except for [downloading network resource files to the user file](../../basic-services/request/app-file-upload-download.md#downloading-network-resource-files-to-the-user-file). The default file name is the part truncated from the last slash (/) in the URL.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| network | [Network](#network10) | No| Yes| Network used for the task. The default value is **ANY** (Wi-Fi or cellular).<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| metered | boolean | No| Yes| Whether the task is allowed on a metered network.<br>- **true**: The task is allowed on a metered network.<br>- **false** (default): The task is not allowed on a metered network.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| roaming | boolean | No| Yes| Whether the task is allowed on a roaming network.<br>- **true** (default): The task is allowed on a roaming network.<br>- **false**: The task is not allowed on a roaming network.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| retry | boolean | No| Yes| Whether automatic retry is enabled for the task. This parameter is only applicable to background tasks.<br>- **true** (default): The automatic retry is enabled.<br>- **false**: The automatic retry is disabled.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| redirect | boolean | No| Yes| Whether redirection is allowed.<br>- **true** (default): The redirection is allowed.<br>- **false**: The redirection is not allowed.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| proxy<sup>12+</sup> | string | No| Yes| Proxy address. The value contains a maximum of 512 characters.<br>It is in the format of http://\<domain or address\>:\<port\>. By default, this parameter is left blank.|
| index | number | No| Yes| Path index of the task. It is usually used for resumable transfers. The default value is **0**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| begins | number | No| Yes| File start point of the task. It is usually used for resumable transfers. The default value is **0**. The value is a closed interval.<br>- For the download task, the value is obtained by sending an HTTP range request to read the start position when the server starts to download files.<br>- For the upload task, the value is obtained at the beginning of the upload.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| ends | number | No| Yes| File end point of the task. It is usually used for resumable transfers. The default value is **-1**. The value is a closed interval.<br>- For the download task, the value is obtained by sending an HTTP range request to read the end position when the server starts to download files.<br>- For the upload task, the value is obtained at the end of the upload.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| gauge | boolean | No| Yes| Whether to send progress notifications. This parameter applies only to background tasks. The default value is **false**.<br>- **false**: Progress notifications are not sent. This means that a notification is sent only to indicate the result of the total task.<br>- **true**: Progress notifications are sent to indicate the result of each file.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| precise | boolean | No| Yes| - If this parameter is set to **true**, the task fails when the file size cannot be obtained.<br>- If this parameter is set to **false**, the task continues when the file size is set to **-1**.<br>The default value is **false**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| token | string | No| Yes| Task token. To query a task with a token, you need to provide the token and use [request.agent.touch](#requestagenttouch10). Otherwise, the specified task cannot be queried. The value contains 8 to 2048 bytes. This parameter is left empty by default.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| priority<sup>11+</sup> | number | No| Yes| Priority of the task. The priority of a foreground task is higher than that of a background task. For tasks in the same mode, a smaller value indicates a higher priority.<br>Default value: **0**|
| extras | object | No| Yes| Additional information of the task. This parameter is left empty by default.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| multipart<sup>15+</sup> | boolean | No| Yes| Whether to use a single request to upload multiple files. If yes, **multipart/form-data** must be used.<br>- **false**: A single request is used to upload one file.<br>- **true**: A single request is used to upload multiple files.<br>The default value is **false**.|
| notification<sup>15+</sup> | [Notification](#notification15) | No| Yes| Custom settings for the notification bar. The default value is **{}**.|
| minSpeed<sup>20+</sup> | [MinSpeed](#minspeed20) | No| Yes| Minimum speed, which is disabled by default.|
| timeout<sup>20+</sup> | [Timeout](#timeout20) | No| Yes| Custom timeout interval. The default connection timeout interval is 60 seconds, and the default total timeout interval is 604800 seconds (one week). If retry is set to **true**, the [timeout](#timeout20) event triggers immediate retry, which will obscure the timeout event itself. As a result, the internal [timeout](#timeout20) condition has been triggered but the [timeout](#timeout20) event is not observable. Set **retry** to **false** to explicitly observe the [timeout](#timeout20) event.|

## State<sup>10+</sup>  

Defines the current task status.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name| Value|Description|
| -------- | -------- |-------- |
| INITIALIZED | 0x00 |The task is initialized based on the configuration specified in [Config](#config10).|
| WAITING | 0x10 |The task lacks resources for running or the resources for retries, or does not match the network status.|
| RUNNING | 0x20 |The task is being executed.|
| RETRYING | 0x21 |The task has failed at least once and is being executed again.|
| PAUSED | 0x30 |The task is suspended and will be resumed later.|
| STOPPED | 0x31 |The task is stopped.|
| COMPLETED | 0x40 |The task is complete.|
| FAILED | 0x41 |The task fails.|
| REMOVED | 0x50 |The task is removed.|


## Progress<sup>10+</sup> 
Describes the data structure of the task progress.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name  | Type    | Read-Only| Optional| Description                           |
|------|--------|----|----|-------------------------------|
| state | [State](#state10) | Yes| No| Current task status.                                                           |
| index | number | Yes| No| Index of the file that is being processed in the task.                                                    |
| processed | number | Yes| No| Size of processed data in the current file in the task, in bytes.                                              |
| sizes | Array&lt;number&gt; | Yes| No| Size of a file in a task, in bytes. If the server uses the chunk mode for data transmission and the total file size cannot be obtained from the request header, the value of **sizes** is treated as **-1**.|
| extras | object | Yes| Yes| Extra information of the task, for example, the header and body of the response from the server.                                    |


## Faults<sup>10+</sup>  

Defines the cause of a task failure.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> In API version 12 or earlier, only serial connection to the IP addresses associated with the specified domain name is supported, and the connection time for a single IP address is not controllable. If the first IP address returned by the DNS is blocked, a handshake timeout may occur, leading to a **TIMEOUT** error.

| Name| Value| Description                                                                            |
| -------- | -------- |--------------------------------------------------------------------------------|
| OTHERS | 0xFF | Other fault.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                                                       |
| DISCONNECTED | 0x00 | Network disconnection.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                                                     |
| TIMEOUT | 0x10 | Timeout.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                                                       |
| PROTOCOL | 0x20 | Protocol error, for example, an internal server error (500) or a data range that cannot be processed (416).<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                       |
| PARAM<sup>12+</sup> | 0x30 | Parameter error, for example, incorrect URL format.<br>**Atomic service API**: This API can be used in atomic services since API version 12.         |
| FSIO | 0x40 | File system I/O error, for example, an error that occurs during the open, search, read, write, or close operation.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                                  |
| DNS<sup>12+</sup> | 0x50 | DNS resolution error.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                 |
| TCP<sup>12+</sup> | 0x60 | TCP connection error.<br>**Atomic service API**: This API can be used in atomic services since API version 12.             |
| SSL<sup>12+</sup> | 0x70 | SSL connection error, for example, a certificate error or certificate verification failure.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| REDIRECT<sup>12+</sup> | 0x80 | Redirection error.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                   |
| LOW_SPEED<sup>20+</sup>  | 0x90 | Low speed.                   |

## Filter<sup>10+</sup>
Defines the filter criteria.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name  | Type    | Read-Only| Optional| Description                           |
|------|--------|----|----|-------------------------------|
| before | number | No| Yes| Unix timestamp of the end time, in milliseconds. The default value is the invoking time.|
| after | number | No| Yes| Unix timestamp of the start time, in milliseconds. The default value is the invoking time minus 24 hours.|
| state | [State](#state10) | No| Yes| Task state. If this parameter is not set, all tasks are queried.|
| action | [Action](#action10) | No| Yes| Task action.<br>- **UPLOAD**: Upload tasks.<br>- **DOWNLOAD**: Download tasks.<br>- If this parameter is not set, all tasks are queried.|
| mode | [Mode](#mode10) | No| Yes| Task mode.<br>- **FOREGROUND**: foreground task.<br>- **BACKGROUND**: background task.<br>- If this parameter is not set, all tasks are queried.|

## TaskInfo<sup>10+</sup> 
Defines the data structure of the task information for query. The fields available vary depending on the query type.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name  | Type    | Read-Only| Optional| Description                           |
|------|--------|----|----|-------------------------------|
| saveas | string | Yes| Yes| Path for storing downloaded files.|
| url | string | Yes| Yes| Task URL.<br>- Use [request.agent.show](#requestagentshow10-1) and [request.agent.touch](#requestagenttouch10-1) to query the value.|
| data | string \| Array&lt;[FormItem](#formitem10)&gt; | Yes| Yes| Task value.<br>- Use [request.agent.show](#requestagentshow10-1) and [request.agent.touch](#requestagenttouch10-1) to query the value.|
| tid | string | Yes| No| Task ID.|
| title | string | Yes| No| Task title.|
| description | string | Yes| No| Task description.|
| action | [Action](#action10) | Yes| No| Task action.<br>- **UPLOAD**: Upload tasks.<br>- **DOWNLOAD**: Download tasks.|
| mode | [Mode](#mode10) | Yes| No| Task mode.<br>- **FOREGROUND**: foreground task.<br>- **BACKGROUND**: background task.|
| priority<sup>11+</sup> | number | Yes| No| Task priority. The priority of a foreground task is higher than that of a background task. For tasks in the same mode, a smaller value indicates a higher priority.|
| mimeType | string | Yes| No| MIME type in the task configuration.|
| progress | [Progress](#progress10) | Yes| No| Task progress.|
| gauge | boolean | Yes| No| Whether to send progress notifications. This parameter applies only to background tasks.<br>- **false**: Progress notifications are not sent. This means that a notification is sent only to indicate the result of the total task.<br>- **true**: Progress notifications are sent to indicate the result of each file.|
| ctime | number | Yes| No| Unix timestamp when the task is created, in milliseconds. The value is generated by the system of the current device.<br>**NOTE**<br>When [request.agent.search](#requestagentsearch10-1) is used for query, this value must be within the range of [after,before] for the task ID to be obtained. For details about **before** and **after**, see [Filter](#filter10).|
| mtime | number | Yes| No| Unix timestamp when the task state changes, in milliseconds. The value is generated by the system of the current device.|
| retry | boolean | Yes| No| Whether automatic retry is enabled for the task. This parameter applies only to background tasks.<br>- **true**: The automatic retry is enabled.<br>- **false**: The automatic retry is disabled.|
| tries | number | Yes| No| Number of retries of the task.|
| faults | [Faults](#faults10) | Yes| No| Failure cause of the task.|
| reason | string | Yes| No| Reason why the task is waiting, failed, stopped, or paused.|
| extras | object | Yes| Yes| Extra information of the task.|

## HttpResponse<sup>12+</sup> 
Describes the data structure of the task response header.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name  | Type    | Read-Only| Optional| Description                           |
|------|--------|----|----|-------------------------------|
| version | string | Yes| No| HTTP version.|
| statusCode | number | Yes| No| HTTP response status code.|
| reason | string | Yes| No| HTTP response cause.|
| headers | Map&lt;string, Array&lt;string&gt;&gt; | Yes| No| HTTP response header.|

## Notification<sup>15+</sup>

Describes the custom information of the notification bar.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name  | Type    | Read-Only| Optional| Description                           |
|------|--------|----|----|-------------------------------|
| title   | string | No| Yes| Custom title, with a maximum of 1024 bytes. The default title is used if this parameter is not set.  |
| text    | string | No| Yes| Custom body text, with a maximum of 3072 bytes. The default text is used if this parameter is not set.   |
| visibility<sup>21+</sup> | number | No| Yes| Task visibility mode for the notification bar, which is determined by bitwise operations on agent [constants](#constants). If this parameter is not set, the **gauge** field is used for determination. If there is no **gauge** field, only the completion notification is displayed.|


**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let config: request.agent.Config = {
    action: request.agent.Action.DOWNLOAD,
    url: 'http://127.0.0.1', // Replace the URL with the HTTP address of the real server.
    title: 'taskOnNotification',
    description: 'Sample code for event listening',
    mode: request.agent.Mode.BACKGROUND,
    overwrite: true,
    method: "PUT",
    saveas: "./",
    network: request.agent.Network.ANY,
    gauge: true,
    notification: {
      visibility: request.agent.VISIBILITY_COMPLETION | request.agent.VISIBILITY_PROGRESS
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

## GroupConfig<sup>15+</sup>

Describes group configuration options for download tasks.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name  | Type    | Read-Only| Optional| Description                           |
|------|--------|----|----|-------------------------------|
| gauge        | boolean                                       | No| Yes | Whether to send progress notifications. This parameter applies only to background tasks.<br>- **true**: The progress, success, and failure notifications are displayed.<br>- **false**: Only success and failure notifications are displayed.<br>The default value is **false**.|
| notification<sup>15+</sup> | [Notification](#notification15) | No| No | Custom settings for the notification bar. The default value is **{}**.                    |

## WaitingReason<sup>20+</sup>

Enumerates the reasons why a task is waiting.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name| Value   | Description                      |
| -------- |------|--------------------------|
| TASK_QUEUE_FULL | 0x00 | The task queue is full.     |
| NETWORK_NOT_MATCH | 0x01 | The required network conditions are not met.  |
| APP_BACKGROUND | 0x02 | The application has been running in the background for a long time.  |
| USER_INACTIVATED | 0x03 | The user is inactive.|

## MinSpeed<sup>20+</sup>

Defines the minimum speed of a task. If the task speed is lower than the preset value for a specified period of time, the task fails. The failure cause is [LOW_SPEED](#faults10).

**System capability**: SystemCapability.Request.FileTransferAgent

| Name     | Type  | Read-Only| Optional| Description                                                          |
|---------|----------|----|----|--------------------------------------------------------------|
| speed   | number   | No | No | Minimum speed of a task, in byte/s. If the task speed is lower than this value for a specified period of time, the task fails. If the value is set to **0**, there is no minimum speed limit.|
| duration    | number   | No | No | Duration during which the task speed can be lower than the minimum speed, in seconds. If the task speed is lower than the preset value for a specified period of time, the task fails. If the value is set to **0**, there is no minimum speed limit. |

## Timeout<sup>20+</sup>

Defines the timeout configuration of a task. The task waiting duration is not counted. For details about the waiting reasons, see [WaitingReason<sup>20+</sup>](#waitingreason20).

**System capability**: SystemCapability.Request.FileTransferAgent

| Name     | Type    | Read-Only| Optional| Description                                     |
|---------|--------|----|----|-----------------------------------------|
| connectionTimeout   | number | No | Yes | Task connection timeout interval, in seconds. The connection timeout interval indicates the maximum time required for establishing a connection between the client and server. If this parameter is not set, the default value **60** is used. The minimum value is **1**.|
| totalTimeout    | number | No | Yes |Total timeout interval of a task, in seconds. The total timeout interval includes the time required for establishing a connection, sending a request, and receiving a response. If this parameter is not set, the default value **604800** is used. The minimum value is 1, and the maximum value is **604800** (that is, one week). |


## Task<sup>10+</sup> 
Implements an upload or download task. Before using this API, you must obtain a **Task** object, from a promise through [request.agent.create](#requestagentcreate10-1) or from a callback through [request.agent.create](#requestagentcreate10).

### Properties
Task properties include the task ID and task configuration.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> The **Task** object and its mounting callback function are released and automatically reclaimed by the system after the **remove** method is called.

| Name  | Type    | Read-Only| Optional| Description                           |
|------|--------|----|----|-------------------------------|
| tid | string | Yes| No| Task ID, which is unique and automatically generated by the system.|
| config | [Config](#config10) | No| No| Task configuration.|

### on('progress')<sup>10+</sup>

on(event: 'progress', callback: (progress: [Progress](#progress10)) =&gt; void): void

Subscribes to task progress changes. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| event | string | Yes| Event type.<br>- **'progress'**: task progress.|
| callback | function | Yes| Callback used to return the data structure of the task progress.|

Parameters of the callback function

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| progress | [Progress](#progress10) | Yes| Task progress.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
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
    url: 'http://127.0.0.1', // Replace the URL with the HTTP address of the real server.
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

on(event: 'completed', callback: (progress: [Progress](#progress10)) =&gt; void): void

Subscribes to task completion events. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| event | string | Yes| Event type.<br>- **'completed'**: task completion.|
| callback | function | Yes| Callback used to return the data structure of the task progress.|

Parameters of the callback function

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| progress | [Progress](#progress10) | Yes| Task progress.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
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
    url: 'http://127.0.0.1', // Replace the URL with the HTTP address of the real server.
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

on(event: 'failed', callback: (progress: [Progress](#progress10)) =&gt; void): void

Subscribes to task failure events. This API uses an asynchronous callback to return the result. You can call [request.agent.show](#requestagentshow10-1) to view the error cause.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| event | string | Yes| Event type.<br>- **'fail'**: task failure.|
| callback | function | Yes| Callback used to return the data structure of the task progress.|

Parameters of the callback function

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| progress | [Progress](#progress10) | Yes| Task progress.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
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
    url: 'http://127.0.0.1', // Replace the URL with the HTTP address of the real server.
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

on(event: 'pause', callback: (progress: [Progress](#progress10)) =&gt; void): void

Subscribes to task pause events. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| event | string | Yes| Event type.<br>- **'pause'**: task pause.|
| callback | function | Yes| Callback used to return the data structure of the task progress.|

Parameters of the callback function

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| progress | [Progress](#progress10) | Yes| Task progress.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
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
    url: 'http://127.0.0.1', // Replace the URL with the HTTP address of the real server.
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
    // Wait for 1 second before executing the next step to prevent asynchronous out-of-order.
    await new Promise<void>((resolve) => {
      setTimeout(() => resolve(),1000)
    })
    task.pause();
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### on('resume')<sup>11+</sup>

on(event: 'resume', callback: (progress: [Progress](#progress10)) =&gt; void): void

Subscribes to task resume events. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| event | string | Yes| Event type.<br>- **'resume'**: task resume.|
| callback | function | Yes| Callback used to return the data structure of the task progress.|

Parameters of the callback function

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| progress | [Progress](#progress10) | Yes| Task progress.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
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
    url: 'http://127.0.0.1', // Replace the URL with the HTTP address of the real server.
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
    // Wait for 1 second before executing the next step to prevent asynchronous out-of-order.
    await new Promise<void>((resolve) => {
      setTimeout(() => resolve(),1000)
    })
    task.pause();
    // Wait for 1 second before executing the next step to prevent asynchronous out-of-order.
    await new Promise<void>((resolve) => {
      setTimeout(() => resolve(),1000)
    })
    task.resume();
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### on('remove')<sup>11+</sup>

on(event: 'remove', callback: (progress: [Progress](#progress10)) =&gt; void): void

Subscribes to task removal events. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| event | string | Yes| Event type.<br>- **'remove'**: task removal.|
| callback | function | Yes| Callback used to return the data structure of the task progress.|

Parameters of the callback function

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| progress | [Progress](#progress10) | Yes| Task progress.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
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
    url: 'http://127.0.0.1', // Replace the URL with the HTTP address of the real server.
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
    // Wait for 1 second before executing the next step to prevent asynchronous out-of-order.
    await new Promise<void>((resolve) => {
      setTimeout(() => resolve(),1000)
    })
    request.agent.remove(task.tid);
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### on('response')<sup>12+</sup>

on(event: 'response', callback: Callback&lt;HttpResponse&gt;): void

Subscribes to task response headers. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| event | string | Yes| Event type.<br>- **'response'**: task response.|
| callback | Callback&lt;[HttpResponse](#httpresponse12)&gt; | Yes| Callback used to return the data structure of the task response header.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
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
    url: 'http://127.0.0.1', // Replace the URL with the HTTP address of the real server.
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

Subscribes to task failure events. This API uses a callback to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

| Name| Type                                 | Mandatory| Description                        |
| -------- |-------------------------------------| -------- |----------------------------|
| event | string                              | Yes| Event type.<br>- **'faultOccur'**: task failure.|
| callback | Callback&lt;[Faults](#faults10)&gt; | Yes| Callback used to return the failure cause of the task.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
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
    url: 'http://127.0.0.1', // Replace the URL with the HTTP address of the real server.
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

Subscribes to task wait events. This API uses a callback to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

| Name| Type                                               | Mandatory| Description                             |
| -------- |---------------------------------------------------| -------- |---------------------------------|
| event | string                                            | Yes| Event type.<br>- 'wait': The task is waiting.|
| callback | Callback&lt;[WaitingReason](#waitingreason20)&gt; | Yes| Callback used to return the waiting reason of the task.     |

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
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
    url: 'http://127.0.0.1', // Replace the URL with the HTTP address of the real server.
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

off(event: 'progress', callback?: (progress: [Progress](#progress10)) =&gt; void): void

Unsubscribes from task progress events.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| event | string | Yes| Event type.<br>- **'progress'**: task progress.|
| callback | function | No| Callback used to return the data structure of the task progress.|

Parameters of the callback function

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| progress | [Progress](#progress10) | Yes| Task progress.|


**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
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
    url: 'http://127.0.0.1', // Replace the URL with the HTTP address of the real server.
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
    // Unsubscribe from all callbacks of task progress changes.
    task.off('progress');
    console.info(`Succeeded in creating a upload task. result: ${task.tid}`);
    task.start();
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### off('completed')<sup>10+</sup>

off(event: 'completed', callback?: (progress: [Progress](#progress10)) =&gt; void): void

Unsubscribes from task completion events.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| event | string | Yes| Event type.<br>- **'completed'**: task completion.|
| callback | function | No| Callback used to return the data structure of the task progress.|

Parameters of the callback function

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| progress | [Progress](#progress10) | Yes| Task progress.|


**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
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
    url: 'http://127.0.0.1', // Replace the URL with the HTTP address of the real server.
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
    // Unsubscribe from all callbacks of the task completion events.
    task.off('completed');
    console.info(`Succeeded in creating a upload task. result: ${task.tid}`);
    task.start();
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### off('failed')<sup>10+</sup>

off(event: 'failed', callback?: (progress: [Progress](#progress10)) =&gt; void): void

Unsubscribes from task failure events.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| event | string | Yes| Event type.<br>- **'failed'**: task failure.|
| callback | function | No| Callback used to return the data structure of the task progress.|

Parameters of the callback function

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| progress | [Progress](#progress10) | Yes| Task progress.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
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
    url: 'http://127.0.0.1', // Replace the URL with the HTTP address of the real server.
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
    // Unsubscribe from all callbacks of the task failure events.
    task.off('failed');
    console.info(`Succeeded in creating a upload task. result: ${task.tid}`);
    task.start();
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### off('pause')<sup>11+</sup>

off(event: 'pause', callback?: (progress: [Progress](#progress10)) =&gt; void): void

Unsubscribes from the foreground task pause event.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| event | string | Yes| Event type.<br>- **'pause'**: task pause.|
| callback | function | No| Callback used to return the data structure of the task progress.|

Parameters of the callback function

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| progress | [Progress](#progress10) | Yes| Task progress.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
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
    url: 'http://127.0.0.1', // Replace the URL with the HTTP address of the real server.
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
    // Unsubscribe from all callbacks of the foreground task pause event.
    task.off('pause');
    console.info(`Succeeded in creating a upload task. result: ${task.tid}`);
    task.start();
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### off('resume')<sup>11+</sup>

off(event: 'resume', callback?: (progress: [Progress](#progress10)) =&gt; void): void

Unsubscribes from foreground task resume events.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| event | string | Yes| Event type.<br>- **'resume'**: task resume.|
| callback | function | No| Callback used to return the data structure of the task progress.|

Parameters of the callback function

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| progress | [Progress](#progress10) | Yes| Task progress.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
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
    url: 'http://127.0.0.1', // Replace the URL with the HTTP address of the real server.
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
    // Unsubscribe from all callbacks of the foreground task resume event.
    task.off('resume');
    console.info(`Succeeded in creating a upload task. result: ${task.tid}`);
    task.start();
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### off('remove')<sup>11+</sup>

off(event: 'remove', callback?: (progress: [Progress](#progress10)) =&gt; void): void

Unsubscribes from the task removal event.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| event | string | Yes| Event type.<br>- **'remove'**: task removal.|
| callback | function | No| Callback used to return the data structure of the task progress.|

Parameters of the callback function

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| progress | [Progress](#progress10) | Yes| Task progress.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
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
    url: 'http://127.0.0.1', // Replace the URL with the HTTP address of the real server.
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
    // Unsubscribe from all callbacks of the task removal event.
    task.off('remove');
    console.info(`Succeeded in creating a upload task. result: ${task.tid}`);
    task.start();
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### off('response')<sup>12+</sup>

off(event: 'response', callback?: Callback&lt;HttpResponse&gt;): void

Unsubscribes from task response headers.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| event | string | Yes| Event type.<br>- **response**: task response.|
| callback | Callback&lt;[HttpResponse](#httpresponse12)&gt; | No| Callback to unregister. If this parameter is not specified, all callbacks of the current type will be unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
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
    url: 'http://127.0.0.1', // Replace the URL with the HTTP address of the real server.
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
    // Unsubscribe from all callbacks of the task response event.
    task.off('response');
    console.info(`Succeeded in creating a upload task. result: ${task.tid}`);
    task.start();
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### off('faultOccur')<sup>20+</sup>

off(event: 'faultOccur', callback?: Callback&lt;Faults&gt;): void

Unsubscribes from task failure events.


**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

| Name| Type                        | Mandatory| Description                                   |
| -------- |----------------------------| -------- |---------------------------------------|
| event | string                     | Yes| Event type.<br>- **'faultOccur'**: task failure.     |
| callback | Callback&lt;[Faults](#faults10)&gt; | No| Callback to unregister. If this parameter is not specified, all callbacks of the current type will be unregistered.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
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
    url: 'http://127.0.0.1', // Replace the URL with the HTTP address of the real server.
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
    // Unsubscribe from all callbacks of the task failure event.
    task.off('faultOccur');
    console.info(`Succeeded in creating a upload task. result: ${task.tid}`);
    task.start();
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### off('wait')<sup>20+</sup>

off(event: 'wait', callback?: Callback&lt;WaitingReason&gt;): void

Unsubscribes from task wait events.


**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

| Name| Type                               | Mandatory| Description                                   |
| -------- |-----------------------------------| -------- |---------------------------------------|
| event | string                            | Yes| Event type.<br>- 'wait': The task is waiting.      |
| callback | Callback&lt;[WaitingReason](#waitingreason20)&gt; | No| Callback to unregister. If this parameter is not specified, all callbacks of the current type will be unregistered.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
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
    url: 'http://127.0.0.1', // Replace the URL with the HTTP address of the real server.
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
    // Unsubscribe from all callbacks of the task wait event.
    task.off('wait');
    console.info(`Succeeded in creating a upload task. result: ${task.tid}`);
    task.start();
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

### start<sup>10+</sup>

start(callback: AsyncCallback&lt;void&gt;): void

Starts a task. This API uses an asynchronous callback to return the result.<br>
Tasks in the following states can be started:
1. Task created by **request.agent.create**.
2. Download tasks that are created by **request.agent.create** but have failed or paused.

**Required permissions**: ohos.permission.INTERNET

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 13400003 | Task service ability error. |
| 21900007 | Operation with wrong task state. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let config: request.agent.Config = {
    action: request.agent.Action.DOWNLOAD,
    url: 'http://127.0.0.1', // Replace the URL with the HTTP address of the real server.
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

Starts a task. This API uses a promise to return the result.<br>
Tasks in the following states can be started:
1. Task created by **request.agent.create**.
2. Download tasks that are created by **request.agent.create** but have failed or paused.

**Required permissions**: ohos.permission.INTERNET

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 13400003 | Task service ability error. |
| 21900007 | Operation with wrong task state. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let config: request.agent.Config = {
    action: request.agent.Action.DOWNLOAD,
    url: 'http://127.0.0.1', // Replace the URL with the HTTP address of the real server.
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

Pauses a task that is waiting, running, or retrying. A paused task can be resumed by [resume](#resume10). This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md).

| ID| Error Message|
| -------- | -------- |
| 13400003 | Task service ability error. |
| 21900007 | Operation with wrong task state. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let config: request.agent.Config = {
    action: request.agent.Action.DOWNLOAD,
    url: 'http://127.0.0.1', // Replace the URL with the HTTP address of the real server.
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
    // Wait for 1 second before executing the next step to prevent asynchronous out-of-order.
    await new Promise<void>((resolve) => {
      setTimeout(() => resolve(),1000)
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

Pauses a task that is waiting, running, or retrying. A paused task can be resumed by [resume](#resume10). This API uses a promise to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md).

| ID| Error Message|
| -------- | -------- |
| 13400003 | Task service ability error. |
| 21900007 | Operation with wrong task state. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let config: request.agent.Config = {
    action: request.agent.Action.DOWNLOAD,
    url: 'http://127.0.0.1', // Replace the URL with the HTTP address of the real server.
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
    // Wait for 1 second before executing the next step to prevent asynchronous out-of-order.
    await new Promise<void>((resolve) => {
      setTimeout(() => resolve(),1000)
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

Resumes a paused task. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 13400003 | Task service ability error. |
| 21900007 | Operation with wrong task state. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let config: request.agent.Config = {
    action: request.agent.Action.DOWNLOAD,
    url: 'http://127.0.0.1', // Replace the URL with the HTTP address of the real server.
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
    // Wait for 1 second before executing the next step to prevent asynchronous out-of-order.
    await new Promise<void>((resolve) => {
      setTimeout(() => resolve(),1000)
    })
    task.pause();
    // Wait for 1 second before executing the next step to prevent asynchronous out-of-order.
    await new Promise<void>((resolve) => {
      setTimeout(() => resolve(),1000)
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

Resumes a paused task. This API uses a promise to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.Request.FileTransferAgent

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 13400003 | Task service ability error. |
| 21900007 | Operation with wrong task state. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let config: request.agent.Config = {
    action: request.agent.Action.DOWNLOAD,
    url: 'http://127.0.0.1', // Replace the URL with the HTTP address of the real server.
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
    // Wait for 1 second before executing the next step to prevent asynchronous out-of-order.
    await new Promise<void>((resolve) => {
      setTimeout(() => resolve(),1000)
    })
    task.pause();
    // Wait for 1 second before executing the next step to prevent asynchronous out-of-order.
    await new Promise<void>((resolve) => {
      setTimeout(() => resolve(),1000)
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

Stops a task that is running, waiting, or retrying. A paused task can be resumed by [start](#start10). This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md).

| ID| Error Message|
| -------- | -------- |
| 13400003 | Task service ability error. |
| 21900007 | Operation with wrong task state. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let config: request.agent.Config = {
    action: request.agent.Action.DOWNLOAD,
    url: 'http://127.0.0.1', // Replace the URL with the HTTP address of the real server.
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
    // Wait for 1 second before executing the next step to prevent asynchronous out-of-order.
    await new Promise<void>((resolve) => {
      setTimeout(() => resolve(),1000)
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

Stops a task that is running, waiting, or retrying. A paused task can be resumed by [start](#start10). This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md).

| ID| Error Message|
| -------- | -------- |
| 13400003 | Task service ability error. |
| 21900007 | Operation with wrong task state. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let config: request.agent.Config = {
    action: request.agent.Action.DOWNLOAD,
    url: 'http://127.0.0.1', // Replace the URL with the HTTP address of the real server.
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
    // Wait for 1 second before executing the next step to prevent asynchronous out-of-order.
    await new Promise<void>((resolve) => {
      setTimeout(() => resolve(),1000)
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

Sets the maximum number of bytes that can be transmitted by a task per second. This API uses a promise to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

| Name  | Type    | Mandatory| Description                                                                          |
|-------|--------|----|------------------------------------------------------------------------------|
| speed | number | Yes | Maximum number of bytes that can be transmitted by a task per second, with a minimum of 16384 bytes. The value cannot be less than the minimum speed value specified by [MinSpeed](#minspeed20).|

**Return value**

| Type             | Description                        |
|-----------------|----------------------------|
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message                |
|----------|------------------------------------------------------------------------------------------------------|
| 401      | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |
| 13400003 | Task service ability error.     |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let config: request.agent.Config = {
    action: request.agent.Action.DOWNLOAD,
    url: 'http://127.0.0.1', // Replace the URL with the HTTP address of the real server.
    saveas: "./",
  };
  request.agent.create(context, config).then((task: request.agent.Task) => {
    // Set the maximum transmission speed.
    task.setMaxSpeed(10 * 1024 * 1024).then(() => {
      console.info(`Succeeded in setting the max speed of the task. result: ${task.tid}`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to set the max speed of the task. result: ${task.tid}`);
    });
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a download task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

## request.agent.create<sup>10+</sup>

create(context: BaseContext, config: Config, callback: AsyncCallback&lt;Task&gt;): void

Creates an upload or download task and adds it to the queue. This API uses an asynchronous callback to return the result. HTTP/HTTPS is supported.


**Required permissions**: ohos.permission.INTERNET

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| context | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes| Application-based context.|
| config | [Config](#config10) | Yes| Task configuration.|
| callback | AsyncCallback&lt;[Task](#task10)&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the **Task** object obtained. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
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

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
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
    url: 'http://127.0.0.1', // Replace the URL with the HTTP address of the real server.
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
      console.error(`Failed to create a download task, Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in creating a download task. result: ${task.config}`);
    await task.start();
    // You need to manually call remove() to end the lifecycle of the task object.
    request.agent.remove(task.tid);
  });
  ```

## request.agent.create<sup>10+</sup>

create(context: BaseContext, config: Config): Promise&lt;Task&gt;

Creates an upload or download task and adds it to the queue. This API uses a promise to return the result. HTTP/HTTPS is supported.


**Required permissions**: ohos.permission.INTERNET

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

> **NOTE**
>
> For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| context | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes| Application-based context.|
| config | [Config](#config10) | Yes| Task configuration.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;[Task](#task10)&gt; | Promise used to return the created task.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
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

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
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
    url: 'http://127.0.0.1', // Replace the URL with the HTTP address of the real server.
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
    console.info(`Succeeded in creating a download task. result: ${task.config}`);
    await task.start();
    // You need to manually call remove() to end the lifecycle of the task object.
    request.agent.remove(task.tid);
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a download task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

## request.agent.getTask<sup>11+</sup>

getTask(context: BaseContext, id: string, token?: string): Promise&lt;Task&gt;

Obtains task information based on the task ID. This API uses a promise to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| context | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes| Application-based context.|
| id | string | Yes| Task ID.|
| token | string | No| Token for task query.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;[Task](#task10)&gt; | Promise used to return the task information.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |
| 13400003 | Task service ability error. |
| 21900006 | Task removed or not found. |

**Example**
  <!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  request.agent.getTask(context, "123456").then((task: request.agent.Task) => {
    console.info(`Succeeded in querying a task. result: ${task.tid}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to query a task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

## request.agent.remove<sup>10+</sup>

remove(id: string, callback: AsyncCallback&lt;void&gt;): void

Removes a specified task of the invoker. If the task is being executed, the task is forced to stop. This API uses an asynchronous callback to return the result. After this API is called, the **task** object and its callback function are released.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| id | string | Yes| Task ID.|
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. |
| 13400003 | Task service ability error. |
| 21900006 | Task removed or not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  request.agent.remove("123456", (err: BusinessError) => {
    if (err) {
      console.error(`Failed to remove a download task, Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in removing a download task.`);
  });
  ```


## request.agent.remove<sup>10+</sup>

remove(id: string): Promise&lt;void&gt;

Removes a specified task of the invoker. If the task is being executed, the task is forced to stop. This API uses a promise to return the result. After this API is called, the **task** object and its callback function are released.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| id | string | Yes| Task ID.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. |
| 13400003 | Task service ability error. |
| 21900006 | Task removed or not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  request.agent.remove("123456").then(() => {
    console.info(`Succeeded in removing a download task. `);
  }).catch((err: BusinessError) => {
    console.error(`Failed to remove a download task, Code: ${err.code}, message: ${err.message}`);
  });
  ```


## request.agent.show<sup>10+</sup>

show(id: string, callback: AsyncCallback&lt;TaskInfo&gt;): void

Queries a task details based on the task ID. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| id | string | Yes| Task ID.|
| callback | AsyncCallback&lt;[TaskInfo](#taskinfo10)&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the **TaskInfo** object obtained. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. |
| 13400003 | Task service ability error. |
| 21900006 | Task removed or not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  request.agent.show("123456", (err: BusinessError, taskInfo: request.agent.TaskInfo) => {
    if (err) {
      console.error(`Failed to show a upload task, Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in showing a upload task.`);
  });
  ```


## request.agent.show<sup>10+</sup>

show(id: string): Promise&lt;TaskInfo&gt;

Queries a task details based on the task ID. This API uses a promise to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| id | string | Yes| Task ID.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;[TaskInfo](#taskinfo10)&gt; | Promise used to return the **TaskInfo** object.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. |
| 13400003 | Task service ability error. |
| 21900006 | Task removed or not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  request.agent.show("123456").then((taskInfo: request.agent.TaskInfo) => {
    console.info(`Succeeded in showing a upload task.`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to show a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```


## request.agent.touch<sup>10+</sup>

touch(id: string, token: string, callback: AsyncCallback&lt;TaskInfo&gt;): void

Queries the task details based on the task ID and token. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| id | string | Yes| Task ID.|
| token | string | Yes| Token for task query.|
| callback | AsyncCallback&lt;[TaskInfo](#taskinfo10)&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the **TaskInfo** object obtained. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |
| 13400003 | Task service ability error. |
| 21900006 | Task removed or not found.  |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  request.agent.touch("123456", "token", (err: BusinessError, taskInfo: request.agent.TaskInfo) => {
    if (err) {
      console.error(`Failed to touch a upload task, Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in touching a upload task.`);
  });
  ```


## request.agent.touch<sup>10+</sup>

touch(id: string, token: string): Promise&lt;TaskInfo&gt;

Queries the task details based on the task ID and token. This API uses a promise to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| id | string | Yes| Task ID.|
| token | string | Yes| Token for task query.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;[TaskInfo](#taskinfo10)&gt; | Promise used to return the **TaskInfo** object.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |
| 13400003 | Task service ability error. |
| 21900006 | Task removed or not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  request.agent.touch("123456", "token").then((taskInfo: request.agent.TaskInfo) => {
    console.info(`Succeeded in touching a upload task. `);
  }).catch((err: BusinessError) => {
    console.error(`Failed to touch a upload task, Code: ${err.code}, message: ${err.message}`);
  });
  ```

## request.agent.search<sup>10+</sup>

search(callback: AsyncCallback&lt;Array&lt;string&gt;&gt;): void

Searches for task IDs based on [Filter](#filter10). The IDs of all tasks from the invoking time to 24 hours ago are searched. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the task ID. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
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

Searches for task IDs based on [Filter](#filter10). This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| filter | [Filter](#filter10) | Yes| Filter criteria.|
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the task ID. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
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

Searches for task IDs based on [Filter](#filter10). This API uses a promise to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| filter | [Filter](#filter10) | No| Filter criteria.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the task IDs that meet the filter criteria.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
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

Creates a group based on [GroupConfig](#groupconfig15). This API uses a promise to return the group ID. This API uses a promise to return the result.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

| Name   | Type                                         | Mandatory| Description       |
|--------|---------------------------------------------|----|-----------|
| config | [GroupConfig<sup>15+</sup>](#groupconfig15) | Yes | Group options for a download task.|

**Return value**

| Type               | Description                              |
|-------------------|----------------------------------|
| Promise\<string\> | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message                                                                                          |
|----------|------------------------------------------------------------------------------------------------|
| 401      | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |
| 13400003 | Task service ability error.             |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  // Prepare the GroupConfig object.
  let config: request.agent.GroupConfig = {
      notification: {},
  };
  // Call the createGroup API to create a group.
  request.agent.createGroup(config).then((gid: string) => {
    console.info(`Succeeded in creating a download task group. `);
  }).catch((err: BusinessError) => {
    console.error(`Failed to create a download group, Code: ${err.code}, message: ${err.message}`);
  });
  ```

## request.agent.attachGroup<sup>15+</sup>

attachGroup(gid: string, tids: string[]): Promise\<void\>

Attaches multiple download task IDs to a specified group ID. This API uses a promise to return the result.

If any task ID does not meet the attachment conditions, all tasks in the list will not be added to the group.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

| Name | Type      | Mandatory| Description                 |
|------|----------|----|---------------------|
| gid  | string   | Yes | Target group ID.            |
| tids | string[] | Yes | List of task IDs to attach.|

**Return value**

| Type             | Description        |
|-----------------|------------|
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message                                                                                          |
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

  // Prepare the group ID and task ID list.
  let groupId: string = "123456789";
  let taskIds: string[] = ["1111", "2222", "3333", "4444"];
  // Call the attachGroup API to add a task ID list to the group.
  request.agent.attachGroup(groupId, taskIds).then(() => {
    console.info(`Succeeded in attaching tasks to the download task group.`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to attach tasks to the download group, Code: ${err.code}, message: ${err.message}`);
  });
  ```

## request.agent.deleteGroup<sup>15+</sup>

deleteGroup(gid: string): Promise\<void\>

Deletes a specified group. No task ID can be added to the group. This API uses a promise to return the result.

When all tasks in a group are succeeded, failed, or removed and the group is deleted, the completion and failure notifications of this group are displayed.

**System capability**: SystemCapability.Request.FileTransferAgent

**Parameters**

| Name | Type      | Mandatory| Description     |
|------|----------|----|---------|
| gid  | string   | Yes | Target group ID.|

**Return value**

| Type             | Description        |
|-----------------|------------|
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Upload and Download Error Codes](errorcode-request.md) and [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message                                                                                          |
|----------|------------------------------------------------------------------------------------------------|
| 401      | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. 3. Parameter verification failed. |
| 13400003 | Task service ability error.           |
| 21900008 | Group deleted or not found.           |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  // Prepare the group ID.
  let groupId: string = "123456789";
  
  // Call the deleteGroup API to delete a group.
  request.agent.deleteGroup(groupId).then(() => {
    console.info(`Succeeded in deleting the download task group.`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to delete the download group, Code: ${err.code}, message: ${err.message}`);
  });
  ```

