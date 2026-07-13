# GallerySync（系统接口）

云图同步对象，用来支撑图库应用媒体资源端云同步流程。在使用前，需要先创建GallerySync实例。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

## constructor

```TypeScript
constructor()
```

端云同步流程的构造函数，用于获取GallerySync类的实例。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**示例：**

```TypeScript
let gallerySync = new cloudSync.GallerySync()

```

## off

```TypeScript
off(evt: 'progress', callback: (pg: SyncProgress) => void): void
```

云图同步对象移除'progress'类型中指定的callback回调。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| evt | 'progress' | 是 | 取消订阅的事件类型，取值为'progress'（同步过程事件）。 |
| callback | (pg: SyncProgress) =&gt; void | 是 | 回调函数。同步过程事件，入参为[SyncProgress](arkts-corefile-syncprogress-i.md)，返回值为void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are leftunspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error |

**示例：**

```TypeScript
let gallerySync = new cloudSync.GallerySync();

let callback = (pg: cloudSync.SyncProgress) => {
  console.info("gallery sync state: " + pg.state + "error type: " + pg.error);
}

gallerySync.on('progress', callback);

gallerySync.off('progress', callback);

```

## off

```TypeScript
off(evt: 'progress'): void
```

云图同步对象移除'progress'类型的所有回调。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| evt | 'progress' | 是 | 取消订阅的事件类型，取值为'progress'（同步过程事件）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are leftunspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error |

**示例：**

```TypeScript
let gallerySync = new cloudSync.GallerySync();

gallerySync.on('progress', (pg: cloudSync.SyncProgress) => {
    console.info("syncState: " + pg.state);
});

gallerySync.off('progress');

```

## on

```TypeScript
on(evt: 'progress', callback: (pg: SyncProgress) => void): void
```

云图同步对象添加同步过程事件监听。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| evt | 'progress' | 是 | 订阅的事件类型，取值为'progress'（同步过程事件）。 |
| callback | (pg: SyncProgress) =&gt; void | 是 | 回调函数。同步过程事件，入参为[SyncProgress](arkts-corefile-syncprogress-i.md)，返回值为void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are leftunspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error |

**示例：**

```TypeScript
let gallerySync = new cloudSync.GallerySync();

gallerySync.on('progress', (pg: cloudSync.SyncProgress) => {
  console.info("syncState: " + pg.state);
});

```

## start

```TypeScript
start(): Promise<void>
```

启动端云同步。使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:Incorrect parameter types. |
| 22400001 | Cloud status not ready. |
| 22400002 | Network unavailable. |
| 22400003 | Low battery level. |

**示例：**

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

## start

```TypeScript
start(callback: AsyncCallback<void>): void
```

异步方法启动端云同步。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。异步启动端云同步。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are leftunspecified;<br>2.Incorrect parameter types. |
| 22400001 | Cloud status not ready. |
| 22400002 | Network unavailable. |
| 22400003 | Low battery level. |

**示例：**

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

## stop

```TypeScript
stop(): Promise<void>
```

异步方法停止端云同步。使用Promise异步回调。

> **说明：**
>
> 调用stop接口，同步流程会停止。再次调用[start](arkts-corefile-gallerysync-c-sys.md#start-1)接口会继续同步。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:Incorrect parameter types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let gallerySync = new cloudSync.GallerySync();

gallerySync.stop().then(() => {
  console.info("stop sync successfully");
}).catch((err: BusinessError) => {
  console.error("stop sync failed with error message: " + err.message + ", error code: " + err.code);
});

```

## stop

```TypeScript
stop(callback: AsyncCallback<void>): void
```

异步方法停止端云同步。使用callback异步回调。

> **说明：**
>
> 调用stop接口，同步流程会停止。再次调用[start](arkts-corefile-gallerysync-c-sys.md#start-1)接口会继续同步。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。异步停止端云同步。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are leftunspecified;<br>2.Incorrect parameter types. |

**示例：**

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

