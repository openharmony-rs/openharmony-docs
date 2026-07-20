# FileSync

云盘同步对象，用于支撑文件管理器应用完成云盘文件的端云同步流程。在使用前，需要先创建FileSync实例。

**起始版本：** 12

<!--Device-cloudSync-class FileSync--><!--Device-cloudSync-class FileSync-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## 导入模块

```TypeScript
import { cloudSync } from '@kit.CoreFileKit';
```

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

端云同步流程的构造函数，用于获取FileSync类的实例。

**起始版本：** 12

<!--Device-FileSync-constructor()--><!--Device-FileSync-constructor()-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:Incorrect parameter types. |

**示例：**

```TypeScript
let fileSync = new cloudSync.FileSync()

```

<a id="getlastsynctime"></a>
## getLastSyncTime

```TypeScript
getLastSyncTime(): Promise<number>
```

异步方法获取上次同步时间。使用Promise异步回调。

**起始版本：** 12

<!--Device-FileSync-getLastSyncTime(): Promise<long>--><!--Device-FileSync-getLastSyncTime(): Promise<long>-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回上次同步时间。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:Incorrect parameter types. |
| 13600001 | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileSync = new cloudSync.FileSync();

fileSync.getLastSyncTime().then((timeStamp: number) => {
  let date = new Date(timeStamp);
  console.info("get last sync time successfully: "+ date);
}).catch((err: BusinessError) => {
  console.error("get last sync time failed with error message: " + err.message + ", error code: " + err.code);
});


```

<a id="getlastsynctime-1"></a>
## getLastSyncTime

```TypeScript
getLastSyncTime(callback: AsyncCallback<number>): void
```

获取上次同步时间。使用callback异步回调。

**起始版本：** 12

<!--Device-FileSync-getLastSyncTime(callback: AsyncCallback<long>): void--><!--Device-FileSync-getLastSyncTime(callback: AsyncCallback<long>): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。异步获取上次同步时间。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileSync = new cloudSync.FileSync();

fileSync.getLastSyncTime((err: BusinessError, timeStamp: number) => {
  if (err) {
    console.error("get last sync time with error message: " + err.message + ", error code: " + err.code);
  } else {
    let date = new Date(timeStamp);
    console.info("get last sync time successfully: "+ date);
  }
});

```

<a id="off"></a>
## off

```TypeScript
off(event: 'progress', callback?: Callback<SyncProgress>): void
```

云盘同步对象移除'progress'类型的指定callback回调。

**起始版本：** 12

<!--Device-FileSync-off(event: 'progress', callback?: Callback<SyncProgress>): void--><!--Device-FileSync-off(event: 'progress', callback?: Callback<SyncProgress>): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'progress' | 是 | 取消订阅的事件类型，取值为'progress'（同步过程事件）。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;SyncProgress&gt; | 否 | 回调函数。同步过程事件， 默认值为null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| 13600001 | IPC error |

**示例：**

```TypeScript
let fileSync = new cloudSync.FileSync();

let callback = (pg: cloudSync.SyncProgress) => {
  console.info(`file sync state: ${pg.state}, error type: ${pg.error}`);
}

fileSync.on('progress', callback);

fileSync.off('progress', callback);

```

<a id="on"></a>
## on

```TypeScript
on(event: 'progress', callback: Callback<SyncProgress>): void
```

云盘同步对象添加同步过程事件监听。

**起始版本：** 12

<!--Device-FileSync-on(event: 'progress', callback: Callback<SyncProgress>): void--><!--Device-FileSync-on(event: 'progress', callback: Callback<SyncProgress>): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'progress' | 是 | 订阅的事件类型，取值为'progress'（同步过程事件）。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;SyncProgress&gt; | 是 | 回调函数。同步过程事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error |

**示例：**

```TypeScript
let fileSync = new cloudSync.FileSync();
let callback = (pg: cloudSync.SyncProgress) => {
  console.info(`file sync state: ${pg.state}, error type: ${pg.error}`);
}

fileSync.on('progress', callback);

```

<a id="start"></a>
## start

```TypeScript
start(): Promise<void>
```

异步方法启动云盘端云同步。使用Promise异步回调。

**起始版本：** 12

<!--Device-FileSync-start(): Promise<void>--><!--Device-FileSync-start(): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:Incorrect parameter types. |
| 13600001 | IPC error. |
| 22400001 | Cloud status not ready. |
| 22400002 | Network unavailable. |
| 22400003 | Low battery level. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileSync = new cloudSync.FileSync();

let callback = (pg: cloudSync.SyncProgress) => {
  console.info("file sync state: " + pg.state + "error type: " + pg.error);
}

fileSync.on('progress', callback);

fileSync.start().then(() => {
  console.info("start sync successfully");
}).catch((err: BusinessError) => {
  console.error("start sync failed with error message: " + err.message + ", error code: " + err.code);
});

```

<a id="start-1"></a>
## start

```TypeScript
start(callback: AsyncCallback<void>): void
```

异步方法启动云盘端云同步。使用callback异步回调。

**起始版本：** 12

<!--Device-FileSync-start(callback: AsyncCallback<void>): void--><!--Device-FileSync-start(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。异步启动端云同步。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| 13600001 | IPC error. |
| 22400001 | Cloud status not ready. |
| 22400002 | Network unavailable. |
| 22400003 | Low battery level. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileSync = new cloudSync.FileSync();

fileSync.start((err: BusinessError) => {
  if (err) {
    console.error("start sync failed with error message: " + err.message + ", error code: " + err.code);
  } else {
    console.info("start sync successfully");
  }
});

```

<a id="stop"></a>
## stop

```TypeScript
stop(): Promise<void>
```

异步方法停止云盘端云同步。使用Promise异步回调。

调用stop接口，同步流程会停止。再次调用[start](arkts-corefile-cloudsync-filesync-c.md#start-1)接口会继续同步。

**起始版本：** 12

<!--Device-FileSync-stop(): Promise<void>--><!--Device-FileSync-stop(): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:Incorrect parameter types. |
| 13600001 | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileSync = new cloudSync.FileSync();

fileSync.stop().then(() => {
  console.info("stop sync successfully");
}).catch((err: BusinessError) => {
  console.error("stop sync failed with error message: " + err.message + ", error code: " + err.code);
});

```

<a id="stop-1"></a>
## stop

```TypeScript
stop(callback: AsyncCallback<void>): void
```

异步方法停止云盘端云同步。使用callback异步回调。

调用stop接口，同步流程会停止。再次调用[start](arkts-corefile-cloudsync-filesync-c.md#start-1)接口会继续同步。

**起始版本：** 12

<!--Device-FileSync-stop(callback: AsyncCallback<void>): void--><!--Device-FileSync-stop(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。异步停止端云同步。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileSync = new cloudSync.FileSync();

fileSync.stop((err: BusinessError) => {
  if (err) {
    console.error("stop sync failed with error message: " + err.message + ", error code: " + err.code);
  } else {
    console.info("stop sync successfully");
  }
});

```

