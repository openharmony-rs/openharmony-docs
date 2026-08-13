# CloudFileCache

云盘文件缓存对象，用来支撑文件管理应用原文件下载流程。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-cloudSync-class CloudFileCache--><!--Device-cloudSync-class CloudFileCache-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## cleanFileCache

```TypeScript
cleanFileCache(uri: string): void
```

同步方法删除文件缓存。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CloudFileCache-cleanFileCache(uri: string): void--><!--Device-CloudFileCache-cleanFileCache(uri: string): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 待删除缓存文件的URI。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument. Possible causes: &lt;br&gt;1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 22400005 | Inner error. Possible causes: &lt;br&gt;1.Failed to access the database or execute the SQL statement. &lt;br&gt;2.System error, such as a null pointer, insufficient memory or a JS engine exception. |
| 13900002 | No such file or directory. |
| 14000002 | Invalid URI. |
| 13900012 | Permission denied by the file system |
| 13600001 | IPC error. Possible causes: &lt;br&gt;1.IPC failed or timed out. 2.Failed to load the service. |
| 13900010 | Try again. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileCache = new cloudSync.CloudFileCache();
let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);

try {
  fileCache.cleanFileCache(uri);
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`clean file cache failed with error message: ${error.message}, error code: ${error.code}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileCache = new cloudSync.CloudFileCache();
let path: string = "/data/storage/el2/cloud/1.txt";
let uri: string = fileUri.getUriFromPath(path);
try {
  fileCache.cleanFileCache(uri);
} catch (e) {
  const error = e as BusinessError;
  console.error(`clean file cache failed with error message: ${error.code}, message is ${error.message}`);
}
```

## cleanFileCache

```TypeScript
cleanFileCache(): Promise<void>
```

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CloudFileCache-cleanFileCache(): Promise<void>--><!--Device-CloudFileCache-cleanFileCache(): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Return Promise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900010 | Try again. |

## constructor

```TypeScript
constructor()
```

A constructor used to create a **CloudFileCache** instance. Data is not shared between multiple instances.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CloudFileCache-constructor()--><!--Device-CloudFileCache-constructor()-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The input parameter is invalid.Possible causes:Incorrect parameter types. |

## 示例

```TypeScript
let fileCache = new cloudSync.CloudFileCache();
```

## getCachedTotalSize

```TypeScript
getCachedTotalSize(): Promise<long>
```

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CloudFileCache-getCachedTotalSize(): Promise<long>--><!--Device-CloudFileCache-getCachedTotalSize(): Promise<long>-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;long&gt; | Return the total size of cached files. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900010 | Try again. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileCache = new cloudSync.CloudFileCache();
fileCache.getCachedTotalSize().then((totalDownloadSize: number) => {
  console.info("totalDownloadSize: " + totalDownloadSize);
}).catch((err: BusinessError) => {
  console.error("get totalDownloadSize failed with error message: " + err.message + ", error code: " + err.code);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileCache = new cloudSync.CloudFileCache();
fileCache.getCachedTotalSize().then<long>((totalDownloadSize: long): void => {
  console.info("totalDownloadSize: " + totalDownloadSize);
}).catch((err: BusinessError<void>): void => {
  console.error("get totalDownloadSize failed with error message: " + err.message + ", error code: " + err.code);
});
```

## offBatchDownload

```TypeScript
offBatchDownload(callback?: Callback<MultiDownloadProgress>): void
```

Unsubscribes from cloud file cache download progress event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CloudFileCache-offBatchDownload(callback?: Callback<MultiDownloadProgress>): void--><!--Device-CloudFileCache-offBatchDownload(callback?: Callback<MultiDownloadProgress>): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[MultiDownloadProgress](arkts-corefile-cloudsync-multidownloadprogress-c.md)&gt; | 否 | callback function with a `MultiDownloadProgress` argument. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument. Possible causes:Incorrect parameter types. |
| 22400005 | Inner error. Possible causes: &lt;br&gt;1.Failed to access the database or execute the SQL statement. &lt;br&gt;2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileCache = new cloudSync.CloudFileCache();
let callback = (pg: cloudSync.MultiDownloadProgress): void => {
  console.info("download state: " + pg.state);
}
try {
  fileCache.onBatchDownload(callback);
  fileCache.offBatchDownload(callback);
} catch (e) {
  let error = e as BusinessError;
  console.error(`Failed to unregister download callback, error code: ${error.code}, message: ${error.message}`);
}
```

## offProgress

```TypeScript
offProgress(callback?: Callback<DownloadProgress>): void
```

Unsubscribes from cloud file cache download progress event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CloudFileCache-offProgress(callback?: Callback<DownloadProgress>): void--><!--Device-CloudFileCache-offProgress(callback?: Callback<DownloadProgress>): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;DownloadProgress&gt; | 否 | callback function with a `DownloadProgress` argument. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The input parameter is invalid.Possible causes:Incorrect parameter types. |
| 13600001 | IPC error |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileCache = new cloudSync.CloudFileCache();
let callback = (pg: cloudSync.DownloadProgress): void => {
  console.info("download state: " + pg.state);
}
try {
  fileCache.onProgress(callback);
  fileCache.offProgress(callback);
} catch (error) {
  console.error(`Error code: ${error.code}, message: ${error.message}`);
}
```

## off_batchDownload

```TypeScript
off(event: 'batchDownload', callback?: Callback<MultiDownloadProgress>): void
```

云盘文件缓存对象移除由 [on](#on_progress)接口添加的云文 件批量缓存过程事件的监听。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

<!--Device-CloudFileCache-off(event: 'batchDownload', callback?: Callback<MultiDownloadProgress>): void--><!--Device-CloudFileCache-off(event: 'batchDownload', callback?: Callback<MultiDownloadProgress>): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'batchDownload' | 是 | 取消订阅的事件类型，取值为'batchDownload'，表示批量缓存过程事件。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[MultiDownloadProgress](arkts-corefile-cloudsync-multidownloadprogress-c.md)&gt; | 否 | 回调函数。云文件批量缓存过程事件。如果填写此参数，将取消指定的回调函数；否则，将取消当前订阅的相同事件类型的所有回 调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument. Possible causes: &lt;br&gt;1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 22400005 | Inner error. Possible causes: &lt;br&gt;1.Failed to access the database or execute the SQL statement. &lt;br&gt;2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileCache = new cloudSync.CloudFileCache();
let callback = (pg: cloudSync.MultiDownloadProgress) => {
  console.info("download state: " + pg.state);
}

try {
  fileCache.on('batchDownload', callback);
  fileCache.off('batchDownload', callback);
} catch (e) {
  let error = e as BusinessError;
  console.error(`Failed to unregister download callback, error code: ${error.code}, message: ${error.message}`);
}
```

## off_progress

```TypeScript
off(event: 'progress', callback?: Callback<DownloadProgress>): void
```

云盘文件缓存对象移除'progress'类型的指定callback回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-CloudFileCache-off(event: 'progress', callback?: Callback<DownloadProgress>): void--><!--Device-CloudFileCache-off(event: 'progress', callback?: Callback<DownloadProgress>): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'progress' | 是 | 取消订阅的事件类型，取值为'progress'（同步过程事件）。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;DownloadProgress&gt; | 否 | 回调函数。云文件下载过程事件。若填写，将视为取消指定的回调函数；否则为取消当前订阅的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified; &lt;br&gt;2.Incorrect parameter types. |
| 13600001 | IPC error |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileCache = new cloudSync.CloudFileCache();

let callback = (pg: cloudSync.DownloadProgress) => {
  console.info("download state: " + pg.state);
}

try {
  fileCache.on('progress', callback);
  fileCache.off('progress', callback);
} catch (e) {
  const error = e as BusinessError;
  console.error(`Error code: ${error.code}, message: ${error.message}`);
}
```

## onBatchDownload

```TypeScript
onBatchDownload(callback: Callback<MultiDownloadProgress>): void
```

Subscribes to a batch of cloud file cache download progress change event. This method uses a callback to get download progress changes.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CloudFileCache-onBatchDownload(callback: Callback<MultiDownloadProgress>): void--><!--Device-CloudFileCache-onBatchDownload(callback: Callback<MultiDownloadProgress>): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[MultiDownloadProgress](arkts-corefile-cloudsync-multidownloadprogress-c.md)&gt; | 是 | callback function with a `MultiDownloadProgress` argument. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument. Possible causes: &lt;br&gt;1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 22400005 | Inner error. Possible causes: &lt;br&gt;1.Failed to access the database or execute the SQL statement. &lt;br&gt;2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileCache = new cloudSync.CloudFileCache();
let callback = (data: cloudSync.MultiDownloadProgress): void => {
  console.info(`Batch download progress: downloadedSize: ${data.downloadedSize}, totalSize: ${data.totalSize}`);
  if (data.state == cloudSync.State.COMPLETED) {
    console.info('Batch download finished.');
  } else if (data.state == cloudSync.State.FAILED) {
    console.info(`Batch download stopped, error type: ${data.errType}.`);
  }
};
try {
  fileCache.onBatchDownload(callback);
} catch (e) {
  let error = e as BusinessError;
  console.error(`Failed to register download callback, error code: ${error.code}, message: ${error.message}`);
}
```

## onProgress

```TypeScript
onProgress(callback: Callback<DownloadProgress>): void
```

Subscribes to cloud file cache download progress change event. This method uses a callback to get download progress changes.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CloudFileCache-onProgress(callback: Callback<DownloadProgress>): void--><!--Device-CloudFileCache-onProgress(callback: Callback<DownloadProgress>): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;DownloadProgress&gt; | 是 | callback function with a `DownloadProgress` argument. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The input parameter is invalid.Possible causes: &lt;br&gt;1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 13600001 | IPC error |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileCache = new cloudSync.CloudFileCache();
let callback = (pg: cloudSync.DownloadProgress): void => {
  console.info("download state: " + pg.state);
};
try {
  fileCache.onProgress(callback);
} catch (error) {
  console.error(`Error code: ${error.code}, message: ${error.message}`);
}
```

## on_batchDownload

```TypeScript
on(event: 'batchDownload', callback: Callback<MultiDownloadProgress>): void
```

添加云文件批量缓存事件的监听。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

<!--Device-CloudFileCache-on(event: 'batchDownload', callback: Callback<MultiDownloadProgress>): void--><!--Device-CloudFileCache-on(event: 'batchDownload', callback: Callback<MultiDownloadProgress>): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'batchDownload' | 是 | 订阅的事件类型，取值为'batchDownload'，表示批量缓存过程事件。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[MultiDownloadProgress](arkts-corefile-cloudsync-multidownloadprogress-c.md)&gt; | 是 | 回调函数。云文件批量缓存过程事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument. Possible causes: &lt;br&gt;1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 22400005 | Inner error. Possible causes: &lt;br&gt;1.Failed to access the database or execute the SQL statement. &lt;br&gt;2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileCache = new cloudSync.CloudFileCache();
let callback = (data: cloudSync.MultiDownloadProgress) => {
  console.info(`Batch download progress: downloadedSize: ${data.downloadedSize}, totalSize: ${data.totalSize}`);
  if (data.state == cloudSync.State.COMPLETED) {
    console.info('Batch download finished.');
  } else if (data.state == cloudSync.State.FAILED) {
    console.info(`Batch download stopped, error type: ${data.errType}.`);
  }
};

try {
  fileCache.on('batchDownload', callback);
} catch (e) {
  let error = e as BusinessError;
  console.error(`Failed to register download callback, error code: ${error.code}, message: ${error.message}`);
}
```

## on_progress

```TypeScript
on(event: 'progress', callback: Callback<DownloadProgress>): void
```

添加云盘文件缓存过程事件监听。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-CloudFileCache-on(event: 'progress', callback: Callback<DownloadProgress>): void--><!--Device-CloudFileCache-on(event: 'progress', callback: Callback<DownloadProgress>): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'progress' | 是 | 订阅的事件类型，取值为'progress'（下载过程事件）。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;DownloadProgress&gt; | 是 | 回调函数。云文件下载过程事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified; &lt;br&gt;2.Incorrect parameter types. |
| 13600001 | IPC error |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileCache = new cloudSync.CloudFileCache();
let callback = (pg: cloudSync.DownloadProgress) => {
  console.info("download state: " + pg.state);
};

try {
  fileCache.on('progress', callback);
} catch (e) {
  const error = e as BusinessError;
  console.error(`Error code: ${error.code}, message: ${error.message}`);
}
```

## start

```TypeScript
start(uri: string): Promise<void>
```

异步方法启动云盘文件缓存。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CloudFileCache-start(uri: string): Promise<void>--><!--Device-CloudFileCache-start(uri: string): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 待下载文件uri。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified; &lt;br&gt;2.Incorrect parameter types. |
| 13900002 | No such file or directory. |
| 14000002 | Invalid uri. |
| 13900025 | No space left on device. |
| 13600001 | IPC error. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileCache = new cloudSync.CloudFileCache();
let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);

try {
  fileCache.on('progress', (pg: cloudSync.DownloadProgress) => {
    console.info("download state: " + pg.state);
  });
} catch (e) {
  const error = e as BusinessError;
  console.error(`Error code: ${error.code}, message: ${error.message}`);
}

fileCache.start(uri).then(() => {
  console.info("start download successfully");
}).catch((err: BusinessError) => {
  console.error("start download failed with error message: " + err.message + ", error code: " + err.code);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileCache = new cloudSync.CloudFileCache();
let path: string = "/data/storage/el2/cloud/1.txt";
let uri: string = fileUri.getUriFromPath(path);
try {
  fileCache.on('progress', (pg: cloudSync.DownloadProgress): void => {
    console.info("download state: " + pg.state);
  });
} catch (error) {
  console.error(`Error code: ${error.code}, message: ${error.message}`);
}
fileCache.start(uri).then<void>((): void => {
  console.info("start download successfully");
}).catch((err: BusinessError<void>): void => {
  console.error("start download failed with error message: " + err.message + ", error code: " + err.code);
});
```

## start

```TypeScript
start(uri: string, callback: AsyncCallback<void>): void
```

异步方法启动云盘文件缓存。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CloudFileCache-start(uri: string, callback: AsyncCallback<void>): void--><!--Device-CloudFileCache-start(uri: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 待下载文件uri。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。异步启动云文件下载。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified; &lt;br&gt;2.Incorrect parameter types. |
| 13900002 | No such file or directory. |
| 14000002 | Invalid uri. |
| 13900025 | No space left on device. |
| 13600001 | IPC error. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileCache = new cloudSync.CloudFileCache();
let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);

fileCache.start(uri, (err: BusinessError) => {
  if (err) {
    console.error("start download failed with error message: " + err.message + ", error code: " + err.code);
  } else {
    console.info("start download successfully");
  }
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileCache = new cloudSync.CloudFileCache();
let path: string = "/data/storage/el2/cloud/1.txt";
let uri: string = fileUri.getUriFromPath(path);
fileCache.start(uri, (err: BusinessError<void> | null): void => {
  if (err && err.code) {
    console.error("start download failed with error message: " + err.message + ", error code: " + err.code);
  } else {
    console.info("start download successfully");
  }
});
```

## startBatch

```TypeScript
startBatch(uris: Array<string>, fileType?: DownloadFileType): Promise<long>
```

启动云文件批量缓存。使用Promise异步回调。 不同的批量缓存任务可以通过接口返回的任务ID区分。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CloudFileCache-startBatch(uris: Array<string>, fileType?: DownloadFileType): Promise<long>--><!--Device-CloudFileCache-startBatch(uris: Array<string>, fileType?: DownloadFileType): Promise<long>-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uris | Array&lt;string&gt; | 是 | URI列表，一次调用最多支持传入400个URI，超过报错22400004。 |
| fileType | [DownloadFileType](arkts-corefile-cloudsync-downloadfiletype-e.md) | 否 | 文件类型，默认值为CONTENT类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;long&gt; | Promise对象，返回启动的云文件批量缓存任务的ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument. Possible causes: &lt;br&gt;1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 22400005 | Inner error. Possible causes: &lt;br&gt;1.Failed to access the database or execute the SQL statement. &lt;br&gt;2.System error, such as a null pointer, insufficient memory or a JS engine exception. |
| 22400004 | Exceed the maximum limit. |
| 14000002 | Invalid uri. |
| 13600001 | IPC error. Possible causes: &lt;br&gt;1.IPC failed or timed out. 2.Failed to load the service. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileCache = new cloudSync.CloudFileCache();
try {
  fileCache.on('batchDownload', (pg: cloudSync.MultiDownloadProgress) => {
    console.info(`batch download state: ${pg.state}`);
  });
} catch (e) {
  let error = e as BusinessError;
  console.error(`Failed to unregister download callback, error code: ${error.code}, message: ${error.message}`);
}

let uriList: Array<string> = [];
fileCache.startBatch(uriList, cloudSync.DownloadFileType.CONTENT).then((downloadId: number) => {
  console.info(`start batch download successfully, taskId: ${downloadId}`);
}).catch((err: BusinessError) => {
  console.error(`start download failed with error message: ${err.message}, error code: ${err.code}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileCache = new cloudSync.CloudFileCache();
try {
  fileCache.on('batchDownload', (pg: cloudSync.MultiDownloadProgress): void => {
    console.info(`batch download state: ${pg.state}`);
  });
} catch (e) {
  const error = e as BusinessError;
  console.error(`Failed to unregister download callback, error code: ${error.code}, message: ${error.message}`);
}
let uriList: Array<string> = [];
fileCache.startBatch(uriList, cloudSync.DownloadFileType.CONTENT).then<long>((downloadId: long): void => {
  console.info(`start batch download successfully, taskId: ${downloadId}`);
}).catch((err: BusinessError<void>): void => {
  console.error(`start download failed with error message: ${err.message}, error code: ${err.code}`);
});
```

## stop

```TypeScript
stop(uri: string, needClean?: boolean): Promise<void>
```

Stops downloading a file from the Drive Kit to the local device. This API uses a promise to return the result. When **stop()** is called, the current file download process terminates, and downloaded files are retained by default. You can call **start()** to resume the download.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CloudFileCache-stop(uri: string, needClean?: boolean): Promise<void>--><!--Device-CloudFileCache-stop(uri: string, needClean?: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 待下载文件uri。 |
| needClean | boolean | 否 | 是否删除已下载的文件。默认值为false表示不删除；true表示删除。&lt;br&gt;从API version12开始支持该参数。<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified; &lt;br&gt;2.Incorrect parameter types. |
| 13900002 | No such file or directory. |
| 14000002 | Invalid uri. |
| 13600001 | IPC error. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileCache = new cloudSync.CloudFileCache();
let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);

fileCache.stop(uri, true).then(() => {
  console.info("stop download successfully");
}).catch((err: BusinessError) => {
  console.error("stop download failed with error message: " + err.message + ", error code: " + err.code);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileCache = new cloudSync.CloudFileCache();
let path: string = "/data/storage/el2/cloud/1.txt";
let uri: string = fileUri.getUriFromPath(path);
fileCache.stop(uri, true).then<void>((): void => {
  console.info("stop download successfully");
}).catch((err: BusinessError<void>): void => {
  console.error("stop download failed with error message: " + err.message + ", error code: " + err.code);
});
```

## stop

```TypeScript
stop(uri: string, callback: AsyncCallback<void>): void
```

异步方法停止云盘文件缓存。使用callback异步回调。 调用stop接口，当前文件下载流程会终止，不删除缓存文件，再次调用start接口重新启动下载。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CloudFileCache-stop(uri: string, callback: AsyncCallback<void>): void--><!--Device-CloudFileCache-stop(uri: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 待下载文件uri。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。异步停止云文件下载。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified; &lt;br&gt;2.Incorrect parameter types. |
| 13900002 | No such file or directory. |
| 14000002 | Invalid uri. |
| 13600001 | IPC error. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileCache = new cloudSync.CloudFileCache();
let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);

fileCache.stop(uri, (err: BusinessError) => {
  if (err) {
    console.error("stop download failed with error message: " + err.message + ", error code: " + err.code);
  } else {
    console.info("stop download successfully");
  }
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileCache = new cloudSync.CloudFileCache();
let path: string = "/data/storage/el2/cloud/1.txt";
let uri: string = fileUri.getUriFromPath(path);
fileCache.stop(uri, (err: BusinessError<void> | null): void => {
  if (err && err.code) {
    console.error("stop download failed with error message: " + err.message + ", error code: " + err.code);
  } else {
    console.info("stop download successfully");
  }
});
```

## stopBatch

```TypeScript
stopBatch(downloadId: long, needClean?: boolean): Promise<void>
```

停止由[startBatch](#startBatch)启动的云文件批量缓存任务。使用Promise异步回调。 调用stopBatch接口会终止当前文件批量缓存流程，未下载完成的缓存文件是否删除由needClean参数决定。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CloudFileCache-stopBatch(downloadId: long, needClean?: boolean): Promise<void>--><!--Device-CloudFileCache-stopBatch(downloadId: long, needClean?: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| downloadId | long | 是 | 需要停止缓存的任务ID。 |
| needClean | boolean | 否 | 是否删除未完成缓存的文件。默认值为false表示不删除；true表示删除。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument. Possible causes: &lt;br&gt;1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 22400005 | Inner error. Possible causes: &lt;br&gt;1.Failed to access the database or execute the SQL statement. &lt;br&gt;2.System error, such as a null pointer, insufficient memory or a JS engine exception. |
| 13600001 | IPC error. Possible causes: &lt;br&gt;1.IPC failed or timed out. 2.Failed to load the service. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let taskId = -1;
let uriList: Array<string> = [];
let fileCache = new cloudSync.CloudFileCache();
fileCache.startBatch(uriList, cloudSync.DownloadFileType.CONTENT).then((downloadId: number) => {
  taskId = downloadId;
  console.info("start batch download successfully");
}).catch((err: BusinessError) => {
  console.error(`start batch download failed with error message: ${err.message}, error code: ${err.code}`);
});

let needStop = true;
if (needStop && taskId > 0) {
  fileCache.stopBatch(taskId, true).then(() => {
    console.info("stop batch download successfully");
  }).catch((err: BusinessError) => {
    console.error(`stop batch download failed with error message: ${err.message}, error code: ${err.code}`);
  });
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let taskId: long = -1;
let uriList: Array<string> = [];
let fileCache = new cloudSync.CloudFileCache();
fileCache.startBatch(uriList, cloudSync.DownloadFileType.CONTENT).then<long>((downloadId: long): void => {
  taskId = downloadId;
  console.info("start batch download successfully");
}).catch((err: BusinessError<void>): void => {
  console.error(`start batch download failed with error message: ${err.message}, error code: ${err.code}`);
});
let needStop: boolean = true;
if (needStop && taskId > 0) {
  fileCache.stopBatch(taskId, true).then<void>((): void => {
    console.info("stop batch download successfully");
  }).catch((err: BusinessError<void>): void => {
    console.error(`stop batch download failed with error message: ${err.message}, error code: ${err.code}`);
  });
}
```

