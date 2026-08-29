# AVDownloaderManager

离线下载任务管理接口，用于管理媒体资源的离线下载任务，包括创建、暂停、恢复、移除下载任务以及监听下载状态和进度变化事件。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Media.Core

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## addAVDownloadTask

```TypeScript
addAVDownloadTask(source: MediaSource): string
```

根据媒体源创建一个离线下载任务。默认情况下，下载任务仅在Wi-Fi环境下进行，如需在蜂窝网络环境下下载，请先设置allowsCellularAccess为true。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | [MediaSource](arkts-media-media-mediasource-i.md) | 是 | 媒体资源描述，至少包含资源URL。 值不能为null。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 成功添加的离线下载任务ID。 |

## allowsCellularAccess

```TypeScript
allowsCellularAccess(value: boolean): void
```

设置是否允许在蜂窝网络环境下进行下载。默认情况下仅在Wi-Fi环境下进行下载。如果设置不允许在蜂窝网络下载，但网络环境为蜂窝网络环境时，下载任务将暂停等待Wi-Fi环境可用后继续。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否允许在蜂窝网络环境下进行下载。true：允许在蜂窝网络环境下下载。- false：不允许在蜂窝网络环境下下载（默认）。 |

## getDownloadTasks

```TypeScript
getDownloadTasks(): Array<string>
```

获取离线下载管理器中的当前所有离线下载任务。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array &lt;string&gt; | 若任务管理器中存在任务，返回任务ID数组；否则返回空数组。 |

## getTaskCacheDirectory

```TypeScript
getTaskCacheDirectory(taskId: string): string
```

获取指定离线下载任务的缓存目录。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| taskId | string | 是 | 要查询缓存目录的离线下载任务ID。取值应为当前管理器中已存在的任务ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 离线下载任务的缓存目录在磁盘上的路径。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400108](../errorcode-media.md#5400108-参数超过取值范围) | If the specified ID is not in the manager, an error is returned. |

## getTaskProgress

```TypeScript
getTaskProgress(taskId: string): number
```

获取指定离线下载任务的下载进度。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| taskId | string | 是 | 要查询进度的离线下载任务ID。取值应为当前管理器中已存在的任务ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 下载进度比例值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400108](../errorcode-media.md#5400108-参数超过取值范围) | If the specified ID is not in the manager, an error is returned. |

## getTaskStatus

```TypeScript
getTaskStatus(taskId: string): AVDownloadTaskState
```

获取指定离线下载任务的状态。状态类型详见AVDownloadTaskState。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| taskId | string | 是 | 要查询状态的离线下载任务ID。取值应为当前管理器中已存在的任务ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AVDownloadTaskState](arkts-media-media-avdownloadtaskstate-t.md) | 指定任务的下载状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400108](../errorcode-media.md#5400108-参数超过取值范围) | If the specified ID is not in the manager, an error is returned. |

## offProgressChange

```TypeScript
offProgressChange(callback?: OnAVDownloadProgressChangeHandle): void
```

取消注册离线下载任务进度变化的事件监听函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnAVDownloadProgressChangeHandle](arkts-media-media-onavdownloadprogresschangehandle-t.md) | 否 | 进度变化事件的处理函数，必须是通过onProgressChange注册过的处理函数。 默认值：不指定此参数时，取消注册该事件的所有处理函数。 |

## offStatusChange

```TypeScript
offStatusChange(callback?: OnAVDownloadTaskStateHandle): void
```

取消注册离线下载任务状态变化的事件监听函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnAVDownloadTaskStateHandle](arkts-media-media-onavdownloadtaskstatehandle-t.md) | 否 | 状态变化事件的处理函数，必须是通过onStatusChange注册过的处理函数。 默认值：不指定此参数时，取消注册该事件的所有处理函数。 |

## onProgressChange

```TypeScript
onProgressChange(callback: OnAVDownloadProgressChangeHandle): void
```

注册离线下载任务进度变化的事件监听函数。当下载进度相比上次变化超过1%，且距上次触发时间超过500ms时，触发该事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnAVDownloadProgressChangeHandle](arkts-media-media-onavdownloadprogresschangehandle-t.md) | 是 | 进度变化事件的处理函数。由应用实现。 第一个参数为下载任务ID，第二个参数为下载进度值。 进度值取值范围为-1或[0.0, 1.0]。-1表示资源大小未知。 |

## onStatusChange

```TypeScript
onStatusChange(callback: OnAVDownloadTaskStateHandle): void
```

注册离线下载任务状态变化的事件监听函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnAVDownloadTaskStateHandle](arkts-media-media-onavdownloadtaskstatehandle-t.md) | 是 | 状态变化事件的处理函数。由应用实现。 第一个参数为状态变化的任务ID，第二个参数为任务的新状态。 |

## pauseDownloadTask

```TypeScript
pauseDownloadTask(taskId?: string): void
```

暂停指定离线下载任务，已下载的部分数据将保留，恢复后可从断点继续下载。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| taskId | string | 否 | 要暂停的离线下载任务ID。 默认值：不指定此参数时，暂停所有下载任务。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400108](../errorcode-media.md#5400108-参数超过取值范围) | If the specified ID is not in the offline download task manager. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |

## release

```TypeScript
release(): void
```

释放AVDownloaderManager对象使用的资源。调用此方法后，所有下载任务将被停止并移除，不可再通过该实例管理下载任务。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**示例**

```TypeScript
audioPlayer.release();
audioPlayer = undefined;
```

```TypeScript
audioRecorder.on('release', () => {    // 设置'release'事件回调。
  console.info('audio recorder release called');
});
audioRecorder.release();
audioRecorder = undefined;
```

## removeDownloadTask

```TypeScript
removeDownloadTask(taskId?: string): void
```

从离线下载管理器中移除离线下载任务，移除后该任务将停止下载并从管理器中删除。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| taskId | string | 否 | 要移除的离线下载任务ID。 默认值：不指定此参数时，移除所有离线下载任务。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400108](../errorcode-media.md#5400108-参数超过取值范围) | If the specified ID is not in the offline download task manager. |

## resumeDownloadTask

```TypeScript
resumeDownloadTask(taskId?: string): void
```

恢复指定离线下载任务，从上次暂停的断点处继续下载。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| taskId | string | 否 | 要恢复的离线下载任务ID，任务需处于已暂停状态。 默认值：不指定此参数时，恢复所有已暂停的离线下载任务。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400108](../errorcode-media.md#5400108-参数超过取值范围) | If the specified ID is not in the offline download task manager. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |

## setRequestTimeout

```TypeScript
setRequestTimeout(timeout: number): void
```

设置HTTP请求的网络超时时间。超时后下载任务将失败。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeout | number | 是 | 超时时间，单位为毫秒。 取值限定为整数。 如果值大于0，表示超时时间，取值范围(0, +∞)。 如果值小于等于0，表示无超时限制，建议根据业务场景设置合理的超时时间以避免任务长时间挂起。 |
