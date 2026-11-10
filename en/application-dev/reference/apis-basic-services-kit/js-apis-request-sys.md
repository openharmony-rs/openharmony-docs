# @ohos.request (Upload and Download) (System API)
<!--Kit: Basic Services Kit-->
<!--Subsystem: Request-->
<!--Owner: @huaxin05-->
<!--Designer: @hu-kai45-->
<!--Tester: @liuhaonan2-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=6da4b952e99935b5a05b98056dbd83ef48a0afaf translatedAt=2026-11-10T04:09:04.286Z pushedAt=2026-11-10T06:56:42.176Z nl=1 -->

The request component provides applications with basic capabilities for uploading and downloading files and background transfer agent, applicable to scenarios such as in-app file upload and download and background agent transfer, making it convenient for developers to complete file transfer tasks and support background task management.

> **NOTE**
>
> The initial APIs of this module are supported since API version 6. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This topic describes only system APIs provided by the module. For details about its public APIs, see [@ohos.request](js-apis-request.md).


## Modules to Import


```js
import { request } from '@kit.BasicServicesKit';
```


## Filter<sup>10+</sup>

Filter criteria. Used to filter tasks by application bundle name in upload and download task query scenarios.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name  | Type    | Read-Only| Optional| Description                           |
|------|--------|----|----|-------------------------------|
| bundle | string | No | Yes | Bundle name of the specified application, available only to system applications. Set this field to filter tasks by a specific application bundle name. If this field is not set, tasks are not filtered by bundle name (tasks of all applications are queried).<br>**System API**: This API is a system API. |


## TaskInfo<sup>10+</sup>

Data structure of the task information in query results. Provides normal query (through public APIs) and system query (through system APIs). The visibility of fields returned by the two query methods differs.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name  | Type    | Read-Only| Optional| Description                           |
|------|--------|----|----|-------------------------------|
| uid | string | Yes | Yes | UID of the application, used only for system queries.<br>**System API**: This API is a system API. |
| bundle | string | Yes | Yes | Bundle name of the application, used only for system queries.<br>**System API**: This API is a system API. |

## Notification<sup>15+</sup>

Describes the custom information of the notification bar.

**System capability**: SystemCapability.Request.FileTransferAgent

| Name  | Type    | Read-Only| Optional| Description                           |
|------|--------|----|----|-------------------------------|
| disable<sup>20+</sup> | boolean | No | Yes | Whether to disable the notification bar display. The value true means to disable the notification bar display, and false means the opposite.<br>The default value is false.<br>When this parameter is set to true (that is, the notification bar display is disabled), the ohos.permission.REQUEST_DISABLE_NOTIFICATION permission is required; if the permission is not requested, this setting does not take effect.<br>**System API**: This API is a system API. |

## request.agent.query<sup>10+</sup>

query(id: string, callback: AsyncCallback&lt;TaskInfo&gt;): void

Queries the detailed information of a task by task ID. This API uses an asynchronous callback to return the result. The uid and bundle fields in the returned TaskInfo are used only for system query. For details, see TaskInfo.

**Required permissions**: ohos.permission.DOWNLOAD_SESSION_MANAGER or ohos.permission.UPLOAD_SESSION_MANAGER

**System capability**: SystemCapability.Request.FileTransferAgent

**System API**: This is a system API.

**Parameters**

| Name| Type                                          | Mandatory| Description|
|----------------------------------------------| -------- | -------- | -------- |
| id | string | Yes | Unique ID of the task, returned when an upload or download task is created and used to query the detailed information of the corresponding task. |
| callback | AsyncCallback&lt;[TaskInfo](#taskinfo10)&gt; | Yes | Callback used to receive the detailed information of the task. Callback signature: (err: BusinessError, taskInfo: TaskInfo) => void, where err is the error object and is undefined when the operation succeeds; taskInfo is the detailed information of the task. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Upload and Download Error Codes](errorcode-request.md).

| Error Code| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 202 | permission verification failed, application which is not a system application uses system API. |
| 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. |
| 13400003 | Task service ability error. |
| 21900006 | Task removed or not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  // taskId is the ID of a created upload or download task. It can be obtained after creating a task through the request.agent.create API. 
  request.agent.query('123456', (err: BusinessError, taskInfo: request.agent.TaskInfo) => {
    if (err) {
      console.error(`Failed to query an upload task. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying an upload task. result: ${taskInfo.uid}`);
  });
  ```


## request.agent.query<sup>10+</sup>

query(id: string): Promise&lt;TaskInfo&gt;

Queries the detailed information of a task by task ID. This API uses a promise to return the result. The uid and bundle fields in the returned TaskInfo are used only for system query. For details, see TaskInfo.

**Required permissions**: ohos.permission.DOWNLOAD_SESSION_MANAGER or ohos.permission.UPLOAD_SESSION_MANAGER

**System capability**: SystemCapability.Request.FileTransferAgent

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| id | string | Yes | Unique ID of the task, returned when an upload or download task is created, used to query the detailed information of the corresponding task. |

**Return value**

| Type                                    | Description                     |
|----------------------------------------| ------------------------- |
| Promise&lt;[TaskInfo](#taskinfo10)&gt; | Promise Promise used to return task details.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Upload and Download Error Codes](errorcode-request.md).

| Error Code| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 202 | permission verification failed, application which is not a system application uses system API. |
| 401 | Parameter error. Possible causes: 1. Missing mandatory parameters. 2. Incorrect parameter type. |
| 13400003 | Task service ability error. |
| 21900006 | Task removed or not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  // taskId is the ID of a created upload/download task. It can be obtained after a task is created by calling request.agent.create. 
  request.agent.query('123456').then((taskInfo: request.agent.TaskInfo) => {
    console.info(`Succeeded in querying an upload task. result: ${taskInfo.uid}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to query an upload task. Code: ${err.code}, message: ${err.message}`);
  });
  ```
