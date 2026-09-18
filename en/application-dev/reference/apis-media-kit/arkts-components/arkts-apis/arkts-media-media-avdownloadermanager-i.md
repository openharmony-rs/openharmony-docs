# AVDownloaderManager

Definition of the Offline Download Management Interface

**Since:** 26.0.0

**System capability:** SystemCapability.Multimedia.Media.Core

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## addAVDownloadTask

```TypeScript
addAVDownloadTask(source: MediaSource): string
```

Create a download task based on the media description.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| source | [MediaSource](arkts-media-media-mediasource-i.md) | Yes | Media description, including at least the resource URL.<br>Value constraint:The value cannot be null. |

**Return value:**

| Type | Description |
| --- | --- |
| string | ID of the offline download task that is successfully added. |

## allowsCellularAccess

```TypeScript
allowsCellularAccess(value: boolean): void
```

Set the network environment for the download. By default, the download is performed only in the Wi-Fi environment.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | If is set to true, the download can be performed in any network environment, Otherwise, the download is performed only in the free Wi-Fi network environment. |

## getDownloadTasks

```TypeScript
getDownloadTasks(): Array<string>
```

Obtains all offline download tasks in the Task Manager. Ended download tasks are automatically cleared.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | If a task exists in the task manager, the task ID array is returned. Otherwise null. |

## getTaskCacheDirectory

```TypeScript
getTaskCacheDirectory(taskId: string): string
```

Obtains the offline download cache directory of a specified task.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| taskId | string | Yes | ID of a task whose download cache directory is queried. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Return the accessible path of the offline download task on the disk. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400108](../errorcode-media.md#5400108-parameter-value-out-of-range) | If the specified ID is not in the manager, an error is returned. |

## getTaskProgress

```TypeScript
getTaskProgress(taskId: string): number
```

Obtains the progress of a specified offline download task.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| taskId | string | Yes | ID of the task for querying the progress. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the approximate ratio of the download progress of a specified task. Value range: [0.0-1.0] If the returned value range is -1, the resource size is unknown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400108](../errorcode-media.md#5400108-parameter-value-out-of-range) | If the specified ID is not in the manager, an error is returned. |

## getTaskStatus

```TypeScript
getTaskStatus(taskId: string): AVDownloadTaskState
```

Obtains the status of a specified offline download task. For details, see #AVDownloadTaskState.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| taskId | string | Yes | ID of a task whose status is queried. |

**Return value:**

| Type | Description |
| --- | --- |
| [AVDownloadTaskState](arkts-media-media-avdownloadtaskstate-t.md) | Returns the task status of a specified task. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400108](../errorcode-media.md#5400108-parameter-value-out-of-range) | If the specified ID is not in the manager, an error is returned. |

## offProgressChange

```TypeScript
offProgressChange(callback?: OnAVDownloadProgressChangeHandle): void
```

Deregisters a specified function's listening on task progress change events.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnAVDownloadProgressChangeHandle](arkts-media-media-onavdownloadprogresschangehandle-t.md) | No | Prototype of the function called by the event. The first parameter indicates the offline download task ID. The second parameter indicates the progress of an offline download task. The progress value ranges from 0.0 to 1.0, If the value is -1, the size of the resource is unknown.<br>Default value: If no parameter is set, all listening functions for the event are canceled. |

## offStatusChange

```TypeScript
offStatusChange(callback?: OnAVDownloadTaskStateHandle): void
```

Deregisters a specified function's listening on task status change events.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnAVDownloadTaskStateHandle](arkts-media-media-onavdownloadtaskstatehandle-t.md) | No | Prototype of the function invoked by the event. The first parameter indicates the ID of the offline download task. The second parameter indicates the latest status of the offline download task.<br>Default value: If no parameter is set, all listening functions for the event are canceled. |

## onProgressChange

```TypeScript
onProgressChange(callback: OnAVDownloadProgressChangeHandle): void
```

Registers a function to listen to the progress change value of an offline download task. The progress change of the offline download task exceeds 1% compared with that of the last time. The event is triggered after the interval exceeds 500 ms.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnAVDownloadProgressChangeHandle](arkts-media-media-onavdownloadprogresschangehandle-t.md) | Yes | Prototype of the function called by the event. The first parameter indicates the offline download task ID. The second parameter indicates the progress of an offline download task. The progress value ranges from 0.0 to 1.0, If the value is -1, the size of the resource is unknown. |

## onStatusChange

```TypeScript
onStatusChange(callback: OnAVDownloadTaskStateHandle): void
```

Registering a Function for Listening on Status Changes of Offline Download Tasks

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnAVDownloadTaskStateHandle](arkts-media-media-onavdownloadtaskstatehandle-t.md) | Yes | Prototype of the function invoked by the event. The first parameter indicates the ID of the task whose status changes. The second parameter indicates the new status of the task switchover. |

## pauseDownloadTask

```TypeScript
pauseDownloadTask(taskId?: string): void
```

Suspending the download of a specified task

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| taskId | string | No | ID of the task whose download needs to be suspended. Value constraint:If the task ID is not transferred, all download tasks are suspended.. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400108](../errorcode-media.md#5400108-parameter-value-out-of-range) | If the specified ID is not in the offline download task manager. |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. |

## release

```TypeScript
release(): void
```

Release resources used for AVDownloaderManager.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.Core

## removeDownloadTask

```TypeScript
removeDownloadTask(taskId?: string): void
```

Remove a download task from the offline download manager

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| taskId | string | No | Specifies the ID of an offline download task.<br>Default value: If this parameter is not specified, all offline download tasks are cleared.. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400108](../errorcode-media.md#5400108-parameter-value-out-of-range) | If the specified ID is not in the offline download task manager. |

## resumeDownloadTask

```TypeScript
resumeDownloadTask(taskId?: string): void
```

Resuming Offline Download of a Specified Task

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| taskId | string | No | Specifies the ID of an offline download task. Value constraint:If this parameter is not specified, all suspended offline download tasks are resumed.. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400108](../errorcode-media.md#5400108-parameter-value-out-of-range) | If the specified ID is not in the offline download task manager. |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. |

## setRequestTimeout

```TypeScript
setRequestTimeout(timeout: number): void
```

Sets the network timeout interval for HTTP requests. If the timeout interval is exceeded, the download fails.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| timeout | number | Yes | Timeout duration, in ms. If is not set, the default timeout duration is used. The value should be an integer.<br>**Description**&lt;/br&gt; &lt;ul&gt;&lt;li&gt;If the value is less than 0, there is no timeout duration.&lt;/li&gt;&lt;/ul&gt;. |
