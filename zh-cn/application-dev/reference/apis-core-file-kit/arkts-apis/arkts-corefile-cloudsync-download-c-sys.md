# Download（系统接口）

云文件下载对象，用来支撑图库应用原图文件下载流程。在使用前，需要先创建Download实例。

**起始版本：** 10

<!--Device-cloudSync-class Download--><!--Device-cloudSync-class Download-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cloudSync } from '@kit.CoreFileKit';
```

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

云文件下载流程的构造函数，用于获取Download类的实例。

**起始版本：** 10

<!--Device-Download-constructor()--><!--Device-Download-constructor()-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**示例：**

```TypeScript
let download = new cloudSync.Download()

```

<a id="off"></a>
## off

```TypeScript
off(evt: 'progress', callback: (pg: DownloadProgress) => void): void
```

云图下载对象移除'progress'类型中指定的callback回调。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

<!--Device-Download-off(evt: 'progress', callback: (pg: DownloadProgress) => void): void--><!--Device-Download-off(evt: 'progress', callback: (pg: DownloadProgress) => void): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| evt | 'progress' | 是 | 取消订阅的事件类型，取值为'progress'（同步过程事件）。 |
| callback | (pg: DownloadProgress) =&gt; void | 是 | 回调函数。云文件下载过程事件，入参为[DownloadProgress](arkts-corefile-cloudsync-downloadprogress-i.md)，返回值为void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error |

**示例：**

```TypeScript
let download = new cloudSync.Download();

let callback = (pg: cloudSync.DownloadProgress) => {
  console.info("download state: " + pg.state);
}

download.on('progress', callback);

download.off('progress', callback);

```

<a id="off-1"></a>
## off

```TypeScript
off(evt: 'progress'): void
```

云图下载对象移除'progress'类型的所有回调。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

<!--Device-Download-off(evt: 'progress'): void--><!--Device-Download-off(evt: 'progress'): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| evt | 'progress' | 是 | 取消订阅的事件类型，取值为'progress'（下载过程事件）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error |

**示例：**

```TypeScript
let download = new cloudSync.Download();

download.on('progress', (pg: cloudSync.DownloadProgress) => {
    console.info("download state: " + pg.state);
});

download.off('progress');

```

<a id="on"></a>
## on

```TypeScript
on(evt: 'progress', callback: (pg: DownloadProgress) => void): void
```

添加云文件下载过程事件监听。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

<!--Device-Download-on(evt: 'progress', callback: (pg: DownloadProgress) => void): void--><!--Device-Download-on(evt: 'progress', callback: (pg: DownloadProgress) => void): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| evt | 'progress' | 是 | 订阅的事件类型，取值为'progress'（下载过程事件）。 |
| callback | (pg: DownloadProgress) =&gt; void | 是 | 回调函数。云文件下载过程事件，入参为[DownloadProgress](arkts-corefile-cloudsync-downloadprogress-i.md)，返回值为void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error |

**示例：**

```TypeScript
let download = new cloudSync.Download();

download.on('progress', (pg: cloudSync.DownloadProgress) => {
  console.info("download state: " + pg.state);
});

```

<a id="start"></a>
## start

```TypeScript
start(uri: string): Promise<void>
```

异步方法启动云文件下载。使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

<!--Device-Download-start(uri: string): Promise<void>--><!--Device-Download-start(uri: string): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

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
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13900002 | No such file or directory. |
| 13900025 | No space left on device. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let download = new cloudSync.Download();
let uri: string = "file:///media/Photo/1";

download.on('progress', (pg: cloudSync.DownloadProgress) => {
  console.info("download state: " + pg.state);
});

download.start(uri).then(() => {
  console.info("start download successfully");
}).catch((err: BusinessError) => {
  console.error(`start download failed with error message: ${err.message}, error code: ${err.code}`);
});

```

<a id="start-1"></a>
## start

```TypeScript
start(uri: string, callback: AsyncCallback<void>): void
```

异步方法启动云文件下载。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

<!--Device-Download-start(uri: string, callback: AsyncCallback<void>): void--><!--Device-Download-start(uri: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 待下载文件uri。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。异步启动云文件下载。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13900002 | No such file or directory. |
| 13900025 | No space left on device. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let download = new cloudSync.Download();
let uri: string = "file:///media/Photo/1";

download.start(uri, (err: BusinessError) => {
  if (err) {
    console.error(`start download failed with error message: ${err.message}, error code: ${err.code}`);
  } else {
    console.info("start download successfully");
  }
});

```

<a id="stop"></a>
## stop

```TypeScript
stop(uri: string): Promise<void>
```

异步方法停止云文件下载。使用Promise异步回调。

> **说明：**  
>  
> 调用stop接口，当前文件下载流程会终止，缓存文件会被删除，再次调用start接口会重新开始下载。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

<!--Device-Download-stop(uri: string): Promise<void>--><!--Device-Download-stop(uri: string): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

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
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let download = new cloudSync.Download();
let uri: string = "file:///media/Photo/1";

download.stop(uri).then(() => {
  console.info("stop download successfully");
}).catch((err: BusinessError) => {
  console.error(`stop download failed with error message: ${err.message}, error code: ${err.code}`);
});

```

<a id="stop-1"></a>
## stop

```TypeScript
stop(uri: string, callback: AsyncCallback<void>): void
```

异步方法停止云文件下载。使用callback异步回调。

> **说明：**  
>  
> 调用stop接口，当前文件下载流程会终止，缓存文件会被删除，再次调用start接口会重新开始下载。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

<!--Device-Download-stop(uri: string, callback: AsyncCallback<void>): void--><!--Device-Download-stop(uri: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 待下载文件uri。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。异步停止云文件下载。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let download = new cloudSync.Download();
let uri: string = "file:///media/Photo/1";

download.stop(uri, (err: BusinessError) => {
  if (err) {
    console.error(`stop download failed with error message: ${err.message}, error code: ${err.code}`);
  } else {
    console.info("stop download successfully");
  }
});

```

