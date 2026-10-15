# AVDownloaderManager

```TypeScript
interface AVDownloaderManager
```

This module provides APIs for managing offline download tasks of media resources, including creating, pausing, resuming, and removing download tasks, as well as listening for download status and progress change events. This module is applicable to scenarios where streaming media resources need to be cached offline in an app and played without network access. It helps users save traffic and improves media playback experience in poor network connection or offline scenarios. You can call [createAVDownloaderManager()](arkts-media-media-createavdownloadermanager-f.md) to create an instance.

**Since:** 26.0.0

<!--Device-media-interface AVDownloaderManager--><!--Device-media-interface AVDownloaderManager-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

## Modules to Import

```TypeScript
```

## addAVDownloadTask

```TypeScript
addAVDownloadTask(source: MediaSource): string
```

Creates an offline download task based on the media source. By default, download tasks are performed only over Wi-Fi. To perform download tasks on the cellular network, set **allowsCellularAccess** to **true**.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AVDownloaderManager-addAVDownloadTask(source: MediaSource): string--><!--Device-AVDownloaderManager-addAVDownloadTask(source: MediaSource): string-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| source | [MediaSource](arkts-media-media-mediasource-i.md) | Yes | Media resource, which must contain at least the resource URL.<br>The value cannot be null. |

**Return value:**

| Type | Description |
| --- | --- |
| string | ID of the offline download task that is successfully added. |

**Examples**

```TypeScript
async function test() {
  let downloaderManager: media.AVDownloaderManager = await media.createAVDownloaderManager();
  let headers: Record<string, string> = {'User-Agent' : 'MyApp/1.0'};
  let mediaSource: media.MediaSource = media.createMediaSourceWithUrl('http://example.com/video.mp4', headers);
  let taskId: string = downloaderManager.addAVDownloadTask(mediaSource);
  console.info(`Succeeded in adding download task, taskId: ${taskId}`);
}
```

## allowsCellularAccess

```TypeScript
allowsCellularAccess(value: boolean): void
```

Sets whether download is allowed on a cellular network. By default, download is allowed only over Wi-Fi. If download is not allowed on a cellular network but the current network is a cellular network, the download task will be paused and resumed when Wi-Fi is available.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AVDownloaderManager-allowsCellularAccess(value: boolean): void--><!--Device-AVDownloaderManager-allowsCellularAccess(value: boolean): void-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether download is allowed on a cellular network.<br>- **true**: allowed. <br>- **false**: not allowed (default). |

**Examples**

```TypeScript
async function test() {
  let downloaderManager: media.AVDownloaderManager = await media.createAVDownloaderManager();
  downloaderManager.allowsCellularAccess(true);
}
```

## getDownloadTasks

```TypeScript
getDownloadTasks(): Array<string>
```

Obtains all offline download tasks in the offline download manager.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AVDownloaderManager-getDownloadTasks(): Array<string>--><!--Device-AVDownloaderManager-getDownloadTasks(): Array<string>-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | If tasks exist in the task manager, an array of the task IDs is returned. Otherwise, an empty array is returned. |

**Examples**

```TypeScript
async function test() {
  let downloaderManager: media.AVDownloaderManager = await media.createAVDownloaderManager();
  let headers: Record<string, string> = {'User-Agent' : 'MyApp/1.0'};
  let mediaSource: media.MediaSource = media.createMediaSourceWithUrl('http://example.com/video.mp4', headers);
  let taskId: string = downloaderManager.addAVDownloadTask(mediaSource);
  let tasks: Array<string> = downloaderManager.getDownloadTasks();
  console.info(`Download tasks: ${tasks}`);
}
```

## getTaskCacheDirectory

```TypeScript
getTaskCacheDirectory(taskId: string): string
```

Obtains the cache directory of a specified offline download task.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AVDownloaderManager-getTaskCacheDirectory(taskId: string): string--><!--Device-AVDownloaderManager-getTaskCacheDirectory(taskId: string): string-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| taskId | string | Yes | ID of the offline download task whose cache directory is to be queried. The value must be the ID of an existing task in the current manager. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Path of the cache directory of the offline download task on the disk. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400108](../../apis-media-kit/errorcode-media.md#5400108-parameter-value-out-of-range) | If the specified ID is not in the manager, an error is returned. |

**Examples**

```TypeScript
async function test() {
  let downloaderManager: media.AVDownloaderManager = await media.createAVDownloaderManager();
  let headers: Record<string, string> = {'User-Agent' : 'MyApp/1.0'};
  let mediaSource: media.MediaSource = media.createMediaSourceWithUrl('http://example.com/video.mp4', headers);
  let taskId: string = downloaderManager.addAVDownloadTask(mediaSource);
  let cacheDir: string = downloaderManager.getTaskCacheDirectory(taskId);
  console.info(`Task cache directory: ${cacheDir}`);
}
```

## getTaskProgress

```TypeScript
getTaskProgress(taskId: string): number
```

Obtains the download progress of a specified offline download task.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AVDownloaderManager-getTaskProgress(taskId: string): double--><!--Device-AVDownloaderManager-getTaskProgress(taskId: string): double-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| taskId | string | Yes | ID of the offline download task whose progress is to be queried. The value must be the ID of an existing task in the current manager. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Download progress percentage.<br>- Value range: [0.0, 1.0] <br>- If the return value is **-1**, the resource size is unknown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400108](../../apis-media-kit/errorcode-media.md#5400108-parameter-value-out-of-range) | If the specified ID is not in the manager, an error is returned. |

**Examples**

```TypeScript
async function test() {
  let downloaderManager: media.AVDownloaderManager = await media.createAVDownloaderManager();
  let headers: Record<string, string> = {'User-Agent' : 'MyApp/1.0'};
  let mediaSource: media.MediaSource = media.createMediaSourceWithUrl('http://example.com/video.mp4', headers);
  let taskId: string = downloaderManager.addAVDownloadTask(mediaSource);
  let progress: number = downloaderManager.getTaskProgress(taskId);
  console.info(`Task progress: ${progress}`);
}
```

## getTaskStatus

```TypeScript
getTaskStatus(taskId: string): AVDownloadTaskState
```

Obtains the status of a specified offline download task. For details about the status types, see #AVDownloadTaskState.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AVDownloaderManager-getTaskStatus(taskId: string): AVDownloadTaskState--><!--Device-AVDownloaderManager-getTaskStatus(taskId: string): AVDownloadTaskState-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| taskId | string | Yes | ID of the offline download task whose status is to be queried. The value must be the ID of an existing task in the current manager. |

**Return value:**

| Type | Description |
| --- | --- |
| [AVDownloadTaskState](arkts-media-media-avdownloadtaskstate-t.md) | Download status of the specified task. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400108](../../apis-media-kit/errorcode-media.md#5400108-parameter-value-out-of-range) | If the specified ID is not in the manager, an error is returned. |

**Examples**

```TypeScript
async function test() {
  let downloaderManager: media.AVDownloaderManager = await media.createAVDownloaderManager();
  let headers: Record<string, string> = {'User-Agent' : 'MyApp/1.0'};
  let mediaSource: media.MediaSource = media.createMediaSourceWithUrl('http://example.com/video.mp4', headers);
  let taskId: string = downloaderManager.addAVDownloadTask(mediaSource);
  let status: media.AVDownloadTaskState = downloaderManager.getTaskStatus(taskId);
  console.info(`Task status: ${status}`);
}
```

## offProgressChange

```TypeScript
offProgressChange(callback?: OnAVDownloadProgressChangeHandle): void
```

Unregisters the listener for the progress change event of an offline download task.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AVDownloaderManager-offProgressChange(callback?: OnAVDownloadProgressChangeHandle): void--><!--Device-AVDownloaderManager-offProgressChange(callback?: OnAVDownloadProgressChangeHandle): void-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnAVDownloadProgressChangeHandle](arkts-media-media-onavdownloadprogresschangehandle-t.md) | No | Callback for progress changes, which must be registered using **onProgressChange**.<br>By default, if this parameter is not specified, all callbacks for the event are unregistered. |

**Examples**

```TypeScript
async function test() {
  let downloaderManager: media.AVDownloaderManager = await media.createAVDownloaderManager();
  downloaderManager.offProgressChange();
}
```

## offStatusChange

```TypeScript
offStatusChange(callback?: OnAVDownloadTaskStateHandle): void
```

Unregisters the listener for the status change event of an offline download task.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AVDownloaderManager-offStatusChange(callback?: OnAVDownloadTaskStateHandle): void--><!--Device-AVDownloaderManager-offStatusChange(callback?: OnAVDownloadTaskStateHandle): void-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnAVDownloadTaskStateHandle](arkts-media-media-onavdownloadtaskstatehandle-t.md) | No | Callback for status changes, which must be registered using **onStatusChange**.<br>By default, if this parameter is not specified, all callbacks for the event are unregistered. |

**Examples**

```TypeScript
async function test() {
  let downloaderManager: media.AVDownloaderManager = await media.createAVDownloaderManager();
  downloaderManager.offStatusChange();
}
```

## onProgressChange

```TypeScript
onProgressChange(callback: OnAVDownloadProgressChangeHandle): void
```

Registers a listener for the progress change event of an offline download task. This event is triggered when the download progress changes by more than 1% compared to the last time and the interval since the last triggering exceeds 500 ms.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AVDownloaderManager-onProgressChange(callback: OnAVDownloadProgressChangeHandle): void--><!--Device-AVDownloaderManager-onProgressChange(callback: OnAVDownloadProgressChangeHandle): void-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnAVDownloadProgressChangeHandle](arkts-media-media-onavdownloadprogresschangehandle-t.md) | Yes | Callback for progress changes, which is implemented by the app.<br>The first parameter indicates the download task ID, and the second parameter indicates the download progress. <br>The value can be **-1** or a number within the range of [0.0, 1.0]. The value **-1** indicates that the resource size is unknown. |

**Examples**

```TypeScript
async function test() {
  let downloaderManager: media.AVDownloaderManager = await media.createAVDownloaderManager();
  downloaderManager.onProgressChange((taskId: string, progress: number) => {
    console.info(`Task progress changed, taskId: ${taskId}, progress: ${progress}`);
  });
}
```

## onStatusChange

```TypeScript
onStatusChange(callback: OnAVDownloadTaskStateHandle): void
```

Registers a listener for the status change event of an offline download task.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AVDownloaderManager-onStatusChange(callback: OnAVDownloadTaskStateHandle): void--><!--Device-AVDownloaderManager-onStatusChange(callback: OnAVDownloadTaskStateHandle): void-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnAVDownloadTaskStateHandle](arkts-media-media-onavdownloadtaskstatehandle-t.md) | Yes | Callback for status changes, which is implemented by the app.<br>The first parameter indicates the ID of the task whose status changes, and the second parameter indicates the new status of the task |

**Examples**

```TypeScript
async function test() {
  let downloaderManager: media.AVDownloaderManager = await media.createAVDownloaderManager();
  downloaderManager.onStatusChange((taskId: string, state: media.AVDownloadTaskState) => {
    console.info(`Task status changed, taskId: ${taskId}, state: ${state}`);
  });
}
```

## pauseDownloadTask

```TypeScript
pauseDownloadTask(taskId?: string): void
```

Pauses a specified offline download task. The downloaded data will be retained. After the task is resumed, the download can continue from the breakpoint. The task must be in the downloading state. Otherwise, error code 5400102 will be returned. If no task ID is specified, all offline download tasks are paused. A paused task can be resumed using **resumeDownloadTask**.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AVDownloaderManager-pauseDownloadTask(taskId?: string): void--><!--Device-AVDownloaderManager-pauseDownloadTask(taskId?: string): void-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| taskId | string | No | ID of the offline download task to pause.<br>By default, if this parameter is not specified, all download tasks are paused. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400108](../../apis-media-kit/errorcode-media.md#5400108-parameter-value-out-of-range) | If the specified ID is not in the offline download task manager. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. |

**Examples**

```TypeScript
async function test() {
  let downloaderManager: media.AVDownloaderManager = await media.createAVDownloaderManager();
  let headers: Record<string, string> = {'User-Agent' : 'MyApp/1.0'};
  let mediaSource: media.MediaSource = media.createMediaSourceWithUrl('http://example.com/video.mp4', headers);
  let taskId: string = downloaderManager.addAVDownloadTask(mediaSource);
  downloaderManager.pauseDownloadTask(taskId);
}
```

## release

```TypeScript
release(): void
```

Releases the resources used by the **AVDownloaderManager** instance. After this method is called, all download tasks will be stopped and removed, and the instance cannot be used to manage download tasks anymore.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AVDownloaderManager-release(): void--><!--Device-AVDownloaderManager-release(): void-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

**Examples**

```TypeScript
async function test() {
  let downloaderManager: media.AVDownloaderManager = await media.createAVDownloaderManager();
  downloaderManager.release();
}
```

## removeDownloadTask

```TypeScript
removeDownloadTask(taskId?: string): void
```

Removes an offline download task from the offline download manager. After the task is removed, the download will stop and the task will be deleted from the manager.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AVDownloaderManager-removeDownloadTask(taskId?: string): void--><!--Device-AVDownloaderManager-removeDownloadTask(taskId?: string): void-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| taskId | string | No | ID of the offline download task to remove.<br>By default, if this parameter is not specified, all offline download tasks are removed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400108](../../apis-media-kit/errorcode-media.md#5400108-parameter-value-out-of-range) | If the specified ID is not in the offline download task manager. |

**Examples**

```TypeScript
async function test() {
  let downloaderManager: media.AVDownloaderManager = await media.createAVDownloaderManager();
  let headers: Record<string, string> = {'User-Agent' : 'MyApp/1.0'};
  let mediaSource: media.MediaSource = media.createMediaSourceWithUrl('http://example.com/video.mp4', headers);
  let taskId: string = downloaderManager.addAVDownloadTask(mediaSource);
  downloaderManager.removeDownloadTask(taskId);
}
```

## resumeDownloadTask

```TypeScript
resumeDownloadTask(taskId?: string): void
```

Resumes a specified offline download task from the breakpoint where the task was paused last time. The task must be in the paused state. Otherwise, error code 5400102 will be returned. If no task ID is specified, all paused offline download tasks are resumed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AVDownloaderManager-resumeDownloadTask(taskId?: string): void--><!--Device-AVDownloaderManager-resumeDownloadTask(taskId?: string): void-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| taskId | string | No | ID of the offline download task to resume. The task must be in the paused state.<br>By default, if this parameter is not specified, all paused offline download tasks are resumed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400108](../../apis-media-kit/errorcode-media.md#5400108-parameter-value-out-of-range) | If the specified ID is not in the offline download task manager. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. |

**Examples**

```TypeScript
async function test() {
  let downloaderManager: media.AVDownloaderManager = await media.createAVDownloaderManager();
  let headers: Record<string, string> = {'User-Agent' : 'MyApp/1.0'};
  let mediaSource: media.MediaSource = media.createMediaSourceWithUrl('http://example.com/video.mp4', headers);
  let taskId: string = downloaderManager.addAVDownloadTask(mediaSource);
  downloaderManager.pauseDownloadTask(taskId);
  downloaderManager.resumeDownloadTask(taskId);
}
```

## setRequestTimeout

```TypeScript
setRequestTimeout(timeout: number): void
```

Sets the network timeout interval for an HTTP request. If the timeout interval is reached, the download task will fail.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AVDownloaderManager-setRequestTimeout(timeout: int): void--><!--Device-AVDownloaderManager-setRequestTimeout(timeout: int): void-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| timeout | number | Yes | Timeout interval, in milliseconds.<br>The value must be an integer. <br>- If the value is greater than 0, it indicates the timeout interval. The value range is (0, +∞). <br>- If the value is less than or equal to 0, there is no timeout limit. You are advised to set a proper timeout interval based on the service scenario to prevent tasks from being suspended for a long time. <br>- If this parameter is not specified, the default timeout interval of 60,000 milliseconds is used. |

**Examples**

```TypeScript
async function test() {
  let downloaderManager: media.AVDownloaderManager = await media.createAVDownloaderManager();
  downloaderManager.setRequestTimeout(30000);
}
```
