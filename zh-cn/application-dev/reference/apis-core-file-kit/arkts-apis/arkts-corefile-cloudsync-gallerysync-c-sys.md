# GallerySync（系统接口）

```TypeScript
class GallerySync
```

云图同步对象，用来支撑图库应用媒体资源端云同步流程。在使用前，需要先创建GallerySync实例。

**起始版本：** 10

<!--Device-cloudSync-class GallerySync--><!--Device-cloudSync-class GallerySync-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cloudSync } from '@kit.CoreFileKit';
```

## constructor

```TypeScript
constructor()
```

端云同步流程的构造函数，用于获取GallerySync类的实例。

**起始版本：** 10

<!--Device-GallerySync-constructor()--><!--Device-GallerySync-constructor()-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

<!--Del-->
**示例**

```TypeScript
let gallerySync = new cloudSync.GallerySync()
```

<!--DelEnd-->

## off

```TypeScript
off(evt: 'progress', callback: (pg: SyncProgress) => void): void
```

云图同步对象移除'progress'类型中指定的callback回调。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

<!--Device-GallerySync-off(evt: 'progress', callback: (pg: SyncProgress) => void): void--><!--Device-GallerySync-off(evt: 'progress', callback: (pg: SyncProgress) => void): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| evt | 'progress' | 是 | 取消订阅的事件类型，取值为'progress'（同步过程事件）。 |
| callback | (pg: SyncProgress) =&gt; void | 是 | 回调函数。同步过程事件，入参为[SyncProgress](arkts-corefile-cloudsync-syncprogress-i.md)，返回值为void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameter types. |
| 13600001 | IPC error |

<!--Del-->
**示例**

```TypeScript
let gallerySync = new cloudSync.GallerySync();

let callback = (pg: cloudSync.SyncProgress) => {
  console.info("gallery sync state: " + pg.state + "error type: " + pg.error);
}

gallerySync.on('progress', callback);

gallerySync.off('progress', callback);
```

<!--DelEnd-->

## off

```TypeScript
off(evt: 'progress'): void
```

云图同步对象移除'progress'类型的所有回调。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

<!--Device-GallerySync-off(evt: 'progress'): void--><!--Device-GallerySync-off(evt: 'progress'): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| evt | 'progress' | 是 | 取消订阅的事件类型，取值为'progress'（同步过程事件）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameter types. |
| 13600001 | IPC error |

<!--Del-->
**示例**

```TypeScript
let gallerySync = new cloudSync.GallerySync();

gallerySync.on('progress', (pg: cloudSync.SyncProgress) => {
    console.info("syncState: " + pg.state);
});

gallerySync.off('progress');
```

<!--DelEnd-->

## on

```TypeScript
on(evt: 'progress', callback: (pg: SyncProgress) => void): void
```

云图同步对象添加同步过程事件监听。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

<!--Device-GallerySync-on(evt: 'progress', callback: (pg: SyncProgress) => void): void--><!--Device-GallerySync-on(evt: 'progress', callback: (pg: SyncProgress) => void): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| evt | 'progress' | 是 | 订阅的事件类型，取值为'progress'（同步过程事件）。 |
| callback | (pg: SyncProgress) =&gt; void | 是 | 回调函数。同步过程事件，入参为[SyncProgress](arkts-corefile-cloudsync-syncprogress-i.md)，返回值为void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameter types. |
| 13600001 | IPC error |

<!--Del-->
**示例**

```TypeScript
let gallerySync = new cloudSync.GallerySync();

gallerySync.on('progress', (pg: cloudSync.SyncProgress) => {
  console.info("syncState: " + pg.state);
});
```

<!--DelEnd-->

## start

```TypeScript
start(): Promise<void>
```

启动端云同步。使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

<!--Device-GallerySync-start(): Promise<void>--><!--Device-GallerySync-start(): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | The input parameter is invalid.Possible causes:Incorrect parameter types. |
| 22400001 | Cloud status not ready. |
| 22400002 | Network unavailable. |
| 22400003 | Low battery level. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let gallerySync = new cloudSync.GallerySync();

gallerySync.on('progress', (pg: cloudSync.SyncProgress) => {
  console.info("syncState: " + pg.state);
});

gallerySync.start().then(() => {
  console.info("start sync successfully");
}).catch((err: BusinessError) => {
  console.error(`start sync failed with error message: ${err.message}, error code: ${err.code}`);
});
```

<!--DelEnd-->

## start

```TypeScript
start(callback: AsyncCallback<void>): void
```

异步方法启动端云同步。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

<!--Device-GallerySync-start(callback: AsyncCallback<void>): void--><!--Device-GallerySync-start(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。异步启动端云同步。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameter types. |
| 22400001 | Cloud status not ready. |
| 22400002 | Network unavailable. |
| 22400003 | Low battery level. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let gallerySync = new cloudSync.GallerySync();

gallerySync.start((err: BusinessError) => {
  if (err) {
    console.error(`start sync failed with error message: ${err.message}, error code: ${err.code}`);
  } else {
    console.info("start sync successfully");
  }
});
```

<!--DelEnd-->

## startWithType

```TypeScript
startWithType(type: SyncType): Promise<void>
```

启动端云同步。该接口使用promise返回结果。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GallerySync-startWithType(type: SyncType): Promise<void>--><!--Device-GallerySync-startWithType(type: SyncType): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [SyncType](arkts-corefile-cloudsync-synctype-e-sys.md) | 是 | 云同步的同步类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 不返回任何值的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| 22400001 | Cloud status not ready. |
| 22400002 | Network unavailable. |
| 22400003 | Low battery level. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let gallerySync = new cloudSync.GallerySync();

gallerySync.startWithType(cloudSync.SyncType.FORCE_THM).then(() => {
  console.info('start sync successfully.');
}).catch((err: BusinessError) => {
  console.error(`start sync failed, code: ${err.code}, message: ${err.message}`);
});
```

<!--DelEnd-->

## startWithType

```TypeScript
startWithType(callback: Callback<void>, type: SyncType): void
```

启动端云同步。该接口使用异步回调返回结果。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GallerySync-startWithType(callback: Callback<void>, type: SyncType): void--><!--Device-GallerySync-startWithType(callback: Callback<void>, type: SyncType): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 启动端云同步回调。 |
| type | [SyncType](arkts-corefile-cloudsync-synctype-e-sys.md) | 是 | 云同步的同步类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| 22400001 | Cloud status not ready. |
| 22400002 | Network unavailable. |
| 22400003 | Low battery level. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let gallerySync = new cloudSync.GallerySync();

try {
  gallerySync.startWithType(() => {
    console.info('start sync successfully.');
  }, cloudSync.SyncType.FORCE_THM);
} catch (err) {
  let error = err as BusinessError;
  console.error(`start sync failed, code: ${error.code}, message: ${error.message}`);
}
```

<!--DelEnd-->

## stop

```TypeScript
stop(): Promise<void>
```

异步方法停止端云同步。使用Promise异步回调。

> **说明：** 
> 
> 调用stop接口，同步流程会停止。再次调用[start](#start)接口会继续同步。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

<!--Device-GallerySync-stop(): Promise<void>--><!--Device-GallerySync-stop(): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | The input parameter is invalid.Possible causes:Incorrect parameter types. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let gallerySync = new cloudSync.GallerySync();

gallerySync.stop().then(() => {
  console.info("stop sync successfully");
}).catch((err: BusinessError) => {
  console.error("stop sync failed with error message: " + err.message + ", error code: " + err.code);
});
```

<!--DelEnd-->

## stop

```TypeScript
stop(callback: AsyncCallback<void>): void
```

异步方法停止端云同步。使用callback异步回调。

> **说明：** 
> 
> 调用stop接口，同步流程会停止。再次调用[start](#start)接口会继续同步。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

<!--Device-GallerySync-stop(callback: AsyncCallback<void>): void--><!--Device-GallerySync-stop(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。异步停止端云同步。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameter types. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let gallerySync = new cloudSync.GallerySync();

gallerySync.stop((err: BusinessError) => {
  if (err) {
    console.error(`stop sync failed with error message: ${err.message}, error code: ${err.code}`);
  } else {
    console.info("stop sync successfully");
  }
});
```

<!--DelEnd-->
