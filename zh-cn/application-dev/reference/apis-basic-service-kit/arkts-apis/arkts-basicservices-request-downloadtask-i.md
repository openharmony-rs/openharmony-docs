# DownloadTask

下载任务，使用下列方法前，需要先获取DownloadTask对象，promise形式通过[request.downloadFile](arkts-basicservices-request-downloadfile-f.md#downloadfile-1)获取，callback形式通过[request.downloadFile](arkts-basicservices-request-downloadfile-f.md#downloadfile-1)获取。

**起始版本：** 6

<!--Device-request-interface DownloadTask--><!--Device-request-interface DownloadTask-End-->

**系统能力：** SystemCapability.MiscServices.Download

## 导入模块

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

<a id="delete"></a>
## delete

```TypeScript
delete(callback: AsyncCallback<boolean>): void
```

移除下载的任务，使用callback异步回调。

> **说明：**  
>  
> 由于不存在401报错场景，在api12中 `401 the parameters check fails` 这个错误码被移除。

**起始版本：** 9

**需要权限：** ohos.permission.INTERNET

<!--Device-DownloadTask-delete(callback: AsyncCallback<boolean>): void--><!--Device-DownloadTask-delete(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示移除下载任务成功；返回false表示移除下载任务失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permissions check fails. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // 需要手动将url替换为真实服务器的HTTP协议地址
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
  console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
}

```

<a id="delete-1"></a>
## delete

```TypeScript
delete(): Promise<boolean>
```

移除下载的任务，使用Promise异步回调。

> **说明：**  
>  
> 由于不存在401报错场景，在api12中 `401 the parameters check fails` 这个错误码被移除。

**起始版本：** 9

**需要权限：** ohos.permission.INTERNET

<!--Device-DownloadTask-delete(): Promise<boolean>--><!--Device-DownloadTask-delete(): Promise<boolean>-End-->

**系统能力：** SystemCapability.MiscServices.Download

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示移除下载任务成功；返回false表示移除下载任务失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permissions check fails. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // 需要手动将url替换为真实服务器的HTTP协议地址
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
  console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
}

```

<a id="gettaskinfo"></a>
## getTaskInfo

```TypeScript
getTaskInfo(callback: AsyncCallback<DownloadInfo>): void
```

查询下载的任务，使用callback异步回调。

> **说明：**  
>  
> 由于不存在401报错场景，在api12中 `401 the parameters check fails` 这个错误码被移除。

**起始版本：** 9

**需要权限：** ohos.permission.INTERNET

<!--Device-DownloadTask-getTaskInfo(callback: AsyncCallback<DownloadInfo>): void--><!--Device-DownloadTask-getTaskInfo(callback: AsyncCallback<DownloadInfo>): void-End-->

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;DownloadInfo&gt; | 是 | 回调函数。当查询下载任务操作成功，err为undefined，data为获取到的DownloadInfo对象；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permissions check fails. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // 需要手动将url替换为真实服务器的HTTP协议地址
  request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
    let downloadTask: request.DownloadTask = data;
    downloadTask.getTaskInfo((err: BusinessError, downloadInfo: request.DownloadInfo) => {
      if (err) {
        console.error(`Failed to query the download task. Code: ${err.code}, message: ${err.message}`);
      } else {
        console.info('Succeeded in querying the download task');
      }
    });
  }).catch((err: BusinessError) => {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  })
} catch (err) {
  console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
}

```

<a id="gettaskinfo-1"></a>
## getTaskInfo

```TypeScript
getTaskInfo(): Promise<DownloadInfo>
```

查询下载任务的信息，使用Promise异步回调。

> **说明：**  
>  
> 由于不存在401报错场景，在api12中 `401 the parameters check fails` 这个错误码被移除。

**起始版本：** 9

**需要权限：** ohos.permission.INTERNET

<!--Device-DownloadTask-getTaskInfo(): Promise<DownloadInfo>--><!--Device-DownloadTask-getTaskInfo(): Promise<DownloadInfo>-End-->

**系统能力：** SystemCapability.MiscServices.Download

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DownloadInfo&gt; | Promise对象，返回DownloadInfo对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permissions check fails. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // 需要手动将url替换为真实服务器的HTTP协议地址
  request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
    let downloadTask: request.DownloadTask = data;
    downloadTask.getTaskInfo().then((downloadInfo: request.DownloadInfo) => {
      console.info('Succeeded in querying the download task');
    }).catch((err: BusinessError) => {
      console.error(`Failed to query the download task. Code: ${err.code}, message: ${err.message}`);
    });
  }).catch((err: BusinessError) => {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  })
} catch (err) {
  console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
} 

```

<a id="gettaskmimetype"></a>
## getTaskMimeType

```TypeScript
getTaskMimeType(callback: AsyncCallback<string>): void
```

查询下载任务的 MimeType（HTTP中表示资源的媒体类型），使用callback异步回调。

> **说明：**  
>  
> 由于不存在401报错场景，在api12中 `401 the parameters check fails` 这个错误码被移除。

**起始版本：** 9

**需要权限：** ohos.permission.INTERNET

<!--Device-DownloadTask-getTaskMimeType(callback: AsyncCallback<string>): void--><!--Device-DownloadTask-getTaskMimeType(callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数。当查询下载任务MimeType成功，err为undefined，data为获取到的下载任务的MimeType的对象；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permissions check fails. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // 需要手动将url替换为真实服务器的HTTP协议地址
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
  console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
}

```

<a id="gettaskmimetype-1"></a>
## getTaskMimeType

```TypeScript
getTaskMimeType(): Promise<string>
```

查询下载的任务的MimeType(HTTP中表示资源的媒体类型)，使用Promise异步回调。

> **说明：**  
>  
> 由于不存在401报错场景，在api12中 `401 the parameters check fails` 这个错误码被移除。

**起始版本：** 9

**需要权限：** ohos.permission.INTERNET

<!--Device-DownloadTask-getTaskMimeType(): Promise<string>--><!--Device-DownloadTask-getTaskMimeType(): Promise<string>-End-->

**系统能力：** SystemCapability.MiscServices.Download

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象。返回下载任务的MimeType。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permissions check fails. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // 需要手动将url替换为真实服务器的HTTP协议地址
  request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
    let downloadTask: request.DownloadTask = data;
    downloadTask.getTaskMimeType().then((data: string) => {
      console.info('Succeeded in querying the download MimeType');
    }).catch((err: BusinessError) => {
      console.error(`Failed to query the download MimeType. Code: ${err.code}, message: ${err.message}`);
    });
  }).catch((err: BusinessError) => {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  })
} catch (err) {
  console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
}

```

<a id="off"></a>
## off('progress')

```TypeScript
off(type: 'progress', callback?: (receivedSize: number, totalSize: number) => void): void
```

取消订阅下载任务进度事件。

**起始版本：** 6

<!--Device-DownloadTask-off(type: 'progress', callback?: (receivedSize: long, totalSize: long) => void): void--><!--Device-DownloadTask-off(type: 'progress', callback?: (receivedSize: long, totalSize: long) => void): void-End-->

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'progress' | 是 | 取消订阅的事件类型。<br>- 取值为'progress'，表示下载的进度信息。 |
| callback | (receivedSize: number, totalSize: number) =&gt; void | 否 | 需要取消订阅的回调函数。若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameters check fails. Possible causes:<br> 1. Missing mandatory parameters.<br> 2. Incorrect parameter type.<br> 3. Parameter verification failed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // 需要手动将url替换为真实服务器的HTTP协议地址
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
    // 表示取消progressCallback1的订阅
    downloadTask.off('progress', progressCallback1);
    // 表示取消订阅下载任务进度事件的所有回调
    downloadTask.off('progress');
  }).catch((err: BusinessError) => {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  })
} catch (err) {
  console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
}

```

<a id="off-1"></a>
## off('complete' | 'pause' | 'remove')

```TypeScript
off(type: 'complete' | 'pause' | 'remove', callback?: () => void): void
```

取消订阅下载任务相关的事件。

**起始版本：** 7

<!--Device-DownloadTask-off(type: 'complete' | 'pause' | 'remove', callback?: () => void): void--><!--Device-DownloadTask-off(type: 'complete' | 'pause' | 'remove', callback?: () => void): void-End-->

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'complete' \| 'pause' \| 'remove' | 是 | 取消订阅的事件类型。<br/>- 取值为'complete'，表示下载任务完成。<br/>- 取值为'pause'，表示下载任务暂停。<br/>- 取值为'remove'，表示下载任务移除。 |
| callback | () =&gt; void | 否 | 需要取消订阅的回调函数。若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameters check fails. Possible causes:<br> 1. Missing mandatory parameters.<br> 2. Incorrect parameter type.<br> 3. Parameter verification failed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // 需要手动将url替换为真实服务器的HTTP协议地址
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
    // 表示取消completeCallback1的订阅
    downloadTask.off('complete', completeCallback1);
    // 表示取消订阅下载任务完成的所有回调
    downloadTask.off('complete');

    let pauseCallback1 = () => {
      console.info('Download delete pause notification.');
    };
    let pauseCallback2 = () => {
      console.info('Download delete pause notification.');
    };
    downloadTask.on('pause', pauseCallback1);
    downloadTask.on('pause', pauseCallback2);
    // 表示取消pauseCallback1的订阅
    downloadTask.off('pause', pauseCallback1);
    // 表示取消订阅下载任务暂停的所有回调
    downloadTask.off('pause');

    let removeCallback1 = () => {
      console.info('Download delete remove notification.');
    };
    let removeCallback2 = () => {
      console.info('Download delete remove notification.');
    };
    downloadTask.on('remove', removeCallback1);
    downloadTask.on('remove', removeCallback2);
    // 表示取消removeCallback1的订阅
    downloadTask.off('remove', removeCallback1);
    // 表示取消订阅下载任务移除的所有回调
    downloadTask.off('remove');
  }).catch((err: BusinessError) => {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  })
} catch (err) {
  console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
}  

```

<a id="off-2"></a>
## off('complete' | 'pause' | 'remove')

```TypeScript
off(type: 'complete' | 'pause' | 'remove', callback?: () => void): void
```

取消订阅下载任务相关的事件。

**起始版本：** 7

<!--Device-DownloadTask-off(type: 'complete' | 'pause' | 'remove', callback?: () => void): void--><!--Device-DownloadTask-off(type: 'complete' | 'pause' | 'remove', callback?: () => void): void-End-->

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'complete' \| 'pause' \| 'remove' | 是 | 取消订阅的事件类型。<br/>- 取值为'complete'，表示下载任务完成。<br/>- 取值为'pause'，表示下载任务暂停。<br/>- 取值为'remove'，表示下载任务移除。 |
| callback | () =&gt; void | 否 | 需要取消订阅的回调函数。若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameters check fails. Possible causes:<br> 1. Missing mandatory parameters.<br> 2. Incorrect parameter type.<br> 3. Parameter verification failed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // 需要手动将url替换为真实服务器的HTTP协议地址
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
    // 表示取消completeCallback1的订阅
    downloadTask.off('complete', completeCallback1);
    // 表示取消订阅下载任务完成的所有回调
    downloadTask.off('complete');

    let pauseCallback1 = () => {
      console.info('Download delete pause notification.');
    };
    let pauseCallback2 = () => {
      console.info('Download delete pause notification.');
    };
    downloadTask.on('pause', pauseCallback1);
    downloadTask.on('pause', pauseCallback2);
    // 表示取消pauseCallback1的订阅
    downloadTask.off('pause', pauseCallback1);
    // 表示取消订阅下载任务暂停的所有回调
    downloadTask.off('pause');

    let removeCallback1 = () => {
      console.info('Download delete remove notification.');
    };
    let removeCallback2 = () => {
      console.info('Download delete remove notification.');
    };
    downloadTask.on('remove', removeCallback1);
    downloadTask.on('remove', removeCallback2);
    // 表示取消removeCallback1的订阅
    downloadTask.off('remove', removeCallback1);
    // 表示取消订阅下载任务移除的所有回调
    downloadTask.off('remove');
  }).catch((err: BusinessError) => {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  })
} catch (err) {
  console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
}  

```

<a id="off-3"></a>
## off('complete' | 'pause' | 'remove')

```TypeScript
off(type: 'complete' | 'pause' | 'remove', callback?: () => void): void
```

取消订阅下载任务相关的事件。

**起始版本：** 7

<!--Device-DownloadTask-off(type: 'complete' | 'pause' | 'remove', callback?: () => void): void--><!--Device-DownloadTask-off(type: 'complete' | 'pause' | 'remove', callback?: () => void): void-End-->

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'complete' \| 'pause' \| 'remove' | 是 | 取消订阅的事件类型。<br/>- 取值为'complete'，表示下载任务完成。<br/>- 取值为'pause'，表示下载任务暂停。<br/>- 取值为'remove'，表示下载任务移除。 |
| callback | () =&gt; void | 否 | 需要取消订阅的回调函数。若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameters check fails. Possible causes:<br> 1. Missing mandatory parameters.<br> 2. Incorrect parameter type.<br> 3. Parameter verification failed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // 需要手动将url替换为真实服务器的HTTP协议地址
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
    // 表示取消completeCallback1的订阅
    downloadTask.off('complete', completeCallback1);
    // 表示取消订阅下载任务完成的所有回调
    downloadTask.off('complete');

    let pauseCallback1 = () => {
      console.info('Download delete pause notification.');
    };
    let pauseCallback2 = () => {
      console.info('Download delete pause notification.');
    };
    downloadTask.on('pause', pauseCallback1);
    downloadTask.on('pause', pauseCallback2);
    // 表示取消pauseCallback1的订阅
    downloadTask.off('pause', pauseCallback1);
    // 表示取消订阅下载任务暂停的所有回调
    downloadTask.off('pause');

    let removeCallback1 = () => {
      console.info('Download delete remove notification.');
    };
    let removeCallback2 = () => {
      console.info('Download delete remove notification.');
    };
    downloadTask.on('remove', removeCallback1);
    downloadTask.on('remove', removeCallback2);
    // 表示取消removeCallback1的订阅
    downloadTask.off('remove', removeCallback1);
    // 表示取消订阅下载任务移除的所有回调
    downloadTask.off('remove');
  }).catch((err: BusinessError) => {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  })
} catch (err) {
  console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
}  

```

<a id="off-4"></a>
## off('fail')

```TypeScript
off(type: 'fail', callback?: (err: number) => void): void
```

取消订阅下载任务失败事件。

**起始版本：** 7

<!--Device-DownloadTask-off(type: 'fail', callback?: (err: int) => void): void--><!--Device-DownloadTask-off(type: 'fail', callback?: (err: int) => void): void-End-->

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'fail' | 是 | 取消订阅的事件类型。<br>- 取值为'fail'，表示下载失败。 |
| callback | (err: number) =&gt; void | 否 | 需要取消订阅的回调函数。若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameters check fails. Possible causes:<br> 1. Missing mandatory parameters.<br> 2. Incorrect parameter type.<br> 3. Parameter verification failed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // 需要手动将url替换为真实服务器的HTTP协议地址
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
    // 表示取消failCallback1的订阅
    downloadTask.off('fail', failCallback1);
    // 表示取消订阅下载任务失败的所有回调
    downloadTask.off('fail');
  }).catch((err: BusinessError) => {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  })
} catch (err) {
  console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
}

```

<a id="on"></a>
## on('progress')

```TypeScript
on(type: 'progress', callback: (receivedSize: number, totalSize: number) => void): void
```

订阅下载任务进度事件，使用callback异步回调。

> **说明：**  
>  
> 应用处于后台时，为满足功耗性能要求，不支持调用此接口进行回调。

**起始版本：** 6

<!--Device-DownloadTask-on(type: 'progress', callback: (receivedSize: long, totalSize: long) => void): void--><!--Device-DownloadTask-on(type: 'progress', callback: (receivedSize: long, totalSize: long) => void): void-End-->

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'progress' | 是 | 订阅的事件类型。<br>- 取值为'progress'，表示下载的进度信息，当任务进度有进展时触发该事件。 |
| callback | (receivedSize: number, totalSize: number) =&gt; void | 是 | 下载任务进度的回调函数，返回已上传文件大小和上传文件大小总和，单位为字节（B）。在下载过程中，若服务器使用chunk方式传输导致无法从请求头中获取文件总大小时，totalSize为 -1。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameters check fails. Possible causes:<br> 1. Missing mandatory parameters.<br> 2. Incorrect parameter type.<br> 3. Parameter verification failed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // 需要手动将url替换为真实服务器的HTTP协议地址
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
  console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
}

```

<a id="on-1"></a>
## on('complete' | 'pause' | 'remove')

```TypeScript
on(type: 'complete' | 'pause' | 'remove', callback: () => void): void
```

订阅下载任务相关的事件，使用callback异步回调。

**起始版本：** 7

<!--Device-DownloadTask-on(type: 'complete' | 'pause' | 'remove', callback: () => void): void--><!--Device-DownloadTask-on(type: 'complete' | 'pause' | 'remove', callback: () => void): void-End-->

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'complete' \| 'pause' \| 'remove' | 是 | 订阅的事件类型。<br>- 取值为'complete'，表示下载任务完成，任务完成时触发该事件。<br/>- 取值为'pause'，表示下载任务暂停，任务暂停时触发该事件。<br/>- 取值为'remove'，表示下载任务移除，任务移除时触发该事件。 |
| callback | () =&gt; void | 是 | 下载任务相关的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameters check fails. Possible causes:<br> 1. Missing mandatory parameters.<br> 2. Incorrect parameter type.<br> 3. Parameter verification failed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // 需要手动将url替换为真实服务器的HTTP协议地址
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
  console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
}

```

<a id="on-2"></a>
## on('complete' | 'pause' | 'remove')

```TypeScript
on(type: 'complete' | 'pause' | 'remove', callback: () => void): void
```

订阅下载任务相关的事件，使用callback异步回调。

**起始版本：** 7

<!--Device-DownloadTask-on(type: 'complete' | 'pause' | 'remove', callback: () => void): void--><!--Device-DownloadTask-on(type: 'complete' | 'pause' | 'remove', callback: () => void): void-End-->

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'complete' \| 'pause' \| 'remove' | 是 | 订阅的事件类型。<br>- 取值为'complete'，表示下载任务完成，任务完成时触发该事件。<br/>- 取值为'pause'，表示下载任务暂停，任务暂停时触发该事件。<br/>- 取值为'remove'，表示下载任务移除，任务移除时触发该事件。 |
| callback | () =&gt; void | 是 | 下载任务相关的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameters check fails. Possible causes:<br> 1. Missing mandatory parameters.<br> 2. Incorrect parameter type.<br> 3. Parameter verification failed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // 需要手动将url替换为真实服务器的HTTP协议地址
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
  console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
}

```

<a id="on-3"></a>
## on('complete' | 'pause' | 'remove')

```TypeScript
on(type: 'complete' | 'pause' | 'remove', callback: () => void): void
```

订阅下载任务相关的事件，使用callback异步回调。

**起始版本：** 7

<!--Device-DownloadTask-on(type: 'complete' | 'pause' | 'remove', callback: () => void): void--><!--Device-DownloadTask-on(type: 'complete' | 'pause' | 'remove', callback: () => void): void-End-->

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'complete' \| 'pause' \| 'remove' | 是 | 订阅的事件类型。<br>- 取值为'complete'，表示下载任务完成，任务完成时触发该事件。<br/>- 取值为'pause'，表示下载任务暂停，任务暂停时触发该事件。<br/>- 取值为'remove'，表示下载任务移除，任务移除时触发该事件。 |
| callback | () =&gt; void | 是 | 下载任务相关的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameters check fails. Possible causes:<br> 1. Missing mandatory parameters.<br> 2. Incorrect parameter type.<br> 3. Parameter verification failed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // 需要手动将url替换为真实服务器的HTTP协议地址
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
  console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
}

```

<a id="on-4"></a>
## on('fail')

```TypeScript
on(type: 'fail', callback: (err: number) => void): void
```

订阅下载任务失败事件，使用callback异步回调。

**起始版本：** 7

<!--Device-DownloadTask-on(type: 'fail', callback: (err: int) => void): void--><!--Device-DownloadTask-on(type: 'fail', callback: (err: int) => void): void-End-->

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'fail' | 是 | 订阅的事件类型。<br>- 取值为'fail'，表示下载失败，任务失败时触发该事件。 |
| callback | (err: number) =&gt; void | 是 | 下载失败的回调函数。错误原因见[下载任务的错误码](docroot://reference/apis-basic-services-kit/js-apis-request.md#constants)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameters check fails. Possible causes:<br> 1. Missing mandatory parameters.<br> 2. Incorrect parameter type.<br> 3. Parameter verification failed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // 需要手动将url替换为真实服务器的HTTP协议地址
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
  console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
}

```

<a id="pause"></a>
## pause

```TypeScript
pause(callback: AsyncCallback<void>): void
```

暂停下载正在运行中的任务，使用callback异步回调。

> **说明：**  
>  
> 从API version 7开始支持，从API version 9开始废弃，建议使用  
> [suspend](arkts-basicservices-request-downloadtask-i.md#suspend-1)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [suspend(callback:](arkts-basicservices-request-downloadtask-i.md#suspend-1)

**需要权限：** ohos.permission.INTERNET

<!--Device-DownloadTask-pause(callback: AsyncCallback<void>): void--><!--Device-DownloadTask-pause(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当暂停下载任务成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permissions check fails. |

**示例：**

```TypeScript
downloadTask.pause((err: BusinessError) => {
  if (err) {
    console.error(`Failed to pause the download task. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in pausing the download task.');
});

```

<a id="pause-1"></a>
## pause

```TypeScript
pause(): Promise<void>
```

暂停下载正在运行中的任务，使用Promise异步回调。

> **说明：**  
>  
> 从API version 7开始支持，从API version 9开始废弃，建议使用[suspend](arkts-basicservices-request-downloadtask-i.md#suspend-1)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [suspend()](arkts-basicservices-request-downloadtask-i.md#suspend-1)

**需要权限：** ohos.permission.INTERNET

<!--Device-DownloadTask-pause(): Promise<void>--><!--Device-DownloadTask-pause(): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.Download

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permissions check fails. |

**示例：**

```TypeScript
downloadTask.pause().then(() => {    
  console.info('Succeeded in pausing the download task.');
}).catch((err: BusinessError) => {
  console.error(`Failed to pause the download task. Code: ${err.code}, message: ${err.message}`);
});

```

<a id="query"></a>
## query

```TypeScript
query(callback: AsyncCallback<DownloadInfo>): void
```

查询下载任务，返回下载任务的信息，使用callback异步回调。

> **说明：**  
>  
> 从API version 7开始支持，从API version 9开始废弃，建议使用  
> [getTaskInfo](arkts-basicservices-request-downloadtask-i.md#gettaskinfo-1)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getTaskInfo(callback:](arkts-basicservices-request-downloadtask-i.md#gettaskinfo-1)

**需要权限：** ohos.permission.INTERNET

<!--Device-DownloadTask-query(callback: AsyncCallback<DownloadInfo>): void--><!--Device-DownloadTask-query(callback: AsyncCallback<DownloadInfo>): void-End-->

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;DownloadInfo&gt; | 是 | 回调函数。当查询下载任务成功，err为undefined，data为获取到的DownloadInfo对象；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permissions check fails. |

**示例：**

```TypeScript
downloadTask.query((err: BusinessError, downloadInfo: request.DownloadInfo) => {
  if (err) {
    console.error(`Failed to query the download task. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in querying the download task.');
  }
});

```

<a id="query-1"></a>
## query

```TypeScript
query(): Promise<DownloadInfo>
```

查询下载任务，返回下载任务的信息，使用Promise异步回调。

> **说明：**  
>  
> 从API version 7开始支持，从API version 9开始废弃,建议使用[getTaskInfo](arkts-basicservices-request-downloadtask-i.md#gettaskinfo-1)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getTaskInfo()](arkts-basicservices-request-downloadtask-i.md#gettaskinfo-1)

**需要权限：** ohos.permission.INTERNET

<!--Device-DownloadTask-query(): Promise<DownloadInfo>--><!--Device-DownloadTask-query(): Promise<DownloadInfo>-End-->

**系统能力：** SystemCapability.MiscServices.Download

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DownloadInfo&gt; | Promise对象。返回DownloadInfo。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permissions check fails. |

**示例：**

```TypeScript
downloadTask.query().then((downloadInfo) => {    
  console.info('Succeeded in querying the download task.');
}).catch((err: BusinessError) => {
  console.error(`Failed to query the download task. Code: ${err.code}, message: ${err.message}`);
});

```

<a id="querymimetype"></a>
## queryMimeType

```TypeScript
queryMimeType(callback: AsyncCallback<string>): void
```

查询下载的任务的MimeType，使用callback异步回调。

> **说明：**  
>  
> 从API version 7开始支持，从API version 9开始废弃，建议使用  
> [getTaskMimeType](arkts-basicservices-request-downloadtask-i.md#gettaskmimetype-1)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getTaskMimeType(callback:](arkts-basicservices-request-downloadtask-i.md#gettaskmimetype-1)

**需要权限：** ohos.permission.INTERNET

<!--Device-DownloadTask-queryMimeType(callback: AsyncCallback<string>): void--><!--Device-DownloadTask-queryMimeType(callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数。当查询下载任务的MimeType成功，err为undefined，data为获取到的任务的MimeType对象；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permissions check fails. |

**示例：**

```TypeScript
downloadTask.queryMimeType((err: BusinessError, data: string) => {
  if (err) {
    console.error(`Failed to query the download mimeType. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in querying the download mimeType.');
  }
});

```

<a id="querymimetype-1"></a>
## queryMimeType

```TypeScript
queryMimeType(): Promise<string>
```

查询下载任务的MimeType，使用Promise异步回调。

> **说明：**  
>  
> 从API version 7开始支持，从API version 9开始废弃，建议使用[getTaskMimeType](arkts-basicservices-request-downloadtask-i.md#gettaskmimetype-1)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getTaskMimeType()](arkts-basicservices-request-downloadtask-i.md#gettaskmimetype-1)

**需要权限：** ohos.permission.INTERNET

<!--Device-DownloadTask-queryMimeType(): Promise<string>--><!--Device-DownloadTask-queryMimeType(): Promise<string>-End-->

**系统能力：** SystemCapability.MiscServices.Download

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象。返回下载任务的MimeType。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permissions check fails. |

**示例：**

```TypeScript
downloadTask.queryMimeType().then((data: string) => {    
  console.info('Succeeded in querying the download MimeType.');
}).catch((err: BusinessError) => {
  console.error(`Failed to query the download MimeType. Code: ${err.code}, message: ${err.message}`);
});

```

<a id="remove"></a>
## remove

```TypeScript
remove(callback: AsyncCallback<boolean>): void
```

移除下载的任务，使用callback异步回调。

> **说明：**  
>  
> 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [delete](arkts-basicservices-request-uploadtask-i.md#delete-1)替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [delete(callback:](arkts-basicservices-request-uploadtask-i.md#delete-1)

**需要权限：** ohos.permission.INTERNET

<!--Device-DownloadTask-remove(callback: AsyncCallback<boolean>): void--><!--Device-DownloadTask-remove(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示移除下载任务成功；返回false表示移除下载任务失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permissions check fails. |

**示例：**

```TypeScript
downloadTask.remove((err, result) => {
  if (err) {
    console.error(`Failed to remove the download task. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in removing the download task.');
});

```

<a id="remove-1"></a>
## remove

```TypeScript
remove(): Promise<boolean>
```

移除下载的任务，使用Promise异步回调。

> **说明：**  
>  
> 从API version 6开始支持，从API version 9开始废弃，建议使用[delete](arkts-basicservices-request-uploadtask-i.md#delete-1)替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [delete()](arkts-basicservices-request-uploadtask-i.md#delete-1)

**需要权限：** ohos.permission.INTERNET

<!--Device-DownloadTask-remove(): Promise<boolean>--><!--Device-DownloadTask-remove(): Promise<boolean>-End-->

**系统能力：** SystemCapability.MiscServices.Download

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示移除下载任务成功；返回false表示移除下载任务失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permissions check fails. |

**示例：**

```TypeScript
downloadTask.remove().then((result) => {
  console.info('Succeeded in removing the download task.');
}).catch ((err: BusinessError) => {
  console.error(`Failed to remove the download task. Code: ${err.code}, message: ${err.message}`);
});

```

<a id="restore"></a>
## restore

```TypeScript
restore(callback: AsyncCallback<boolean>): void
```

重新启动被暂停的下载任务，使用callback异步回调。

> **说明：**  
>  
> 由于不存在401报错场景，在api12中 `401 the parameters check fails` 这个错误码被移除。

**起始版本：** 9

**需要权限：** ohos.permission.INTERNET

<!--Device-DownloadTask-restore(callback: AsyncCallback<boolean>): void--><!--Device-DownloadTask-restore(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示重新启动已暂停的下载任务成功；返回false表示重新启动下载任务失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permissions check fails. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // 需要手动将url替换为真实服务器的HTTP协议地址
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
  console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
}

```

<a id="restore-1"></a>
## restore

```TypeScript
restore(): Promise<boolean>
```

重新启动被暂停的下载任务，使用Promise异步回调。

> **说明：**  
>  
> 由于不存在401报错场景，在api12中 `401 the parameters check fails` 这个错误码被移除。

**起始版本：** 9

**需要权限：** ohos.permission.INTERNET

<!--Device-DownloadTask-restore(): Promise<boolean>--><!--Device-DownloadTask-restore(): Promise<boolean>-End-->

**系统能力：** SystemCapability.MiscServices.Download

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示重新启动被暂停的下载任务成功；返回false表示重新启动被暂停的下载任务失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permissions check fails. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // 需要手动将url替换为真实服务器的HTTP协议地址
  request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
    let downloadTask: request.DownloadTask = data;
    downloadTask.restore().then((result: boolean) => {
      console.info('Succeeded in resuming the download task.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to resume the download task. Code: ${err.code}, message: ${err.message}`);
    });
  }).catch((err: BusinessError) => {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  })
} catch (err) {
  console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
}

```

<a id="resume"></a>
## resume

```TypeScript
resume(callback: AsyncCallback<void>): void
```

重新启动被暂停的下载任务，使用callback异步回调。

> **说明：**  
>  
> 从API version 7开始支持，从API version 9开始废弃，建议使用  
> [restore](arkts-basicservices-request-downloadtask-i.md#restore-1)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [restore(callback:](arkts-basicservices-request-downloadtask-i.md#restore-1)

**需要权限：** ohos.permission.INTERNET

<!--Device-DownloadTask-resume(callback: AsyncCallback<void>): void--><!--Device-DownloadTask-resume(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当重新启动已暂停的下载任务成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permissions check fails. |

**示例：**

```TypeScript
downloadTask.resume((err: BusinessError) => {
  if (err) {
    console.error(`Failed to resume the download task. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in resuming the download task.');
});

```

<a id="resume-1"></a>
## resume

```TypeScript
resume(): Promise<void>
```

重新启动被暂停的下载任务，使用Promise异步回调。

> **说明：**  
>  
> 从API version 7开始支持，从API version 9开始废弃，建议使用[restore](arkts-basicservices-request-downloadtask-i.md#restore-1)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [restore()](arkts-basicservices-request-downloadtask-i.md#restore-1)

**需要权限：** ohos.permission.INTERNET

<!--Device-DownloadTask-resume(): Promise<void>--><!--Device-DownloadTask-resume(): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.Download

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permissions check fails. |

**示例：**

```TypeScript
downloadTask.resume().then(() => {
  console.info('Succeeded in resuming the download task.');
}).catch((err: BusinessError) => {
  console.error(`Failed to resume the download task. Code: ${err.code}, message: ${err.message}`);
});

```

<a id="suspend"></a>
## suspend

```TypeScript
suspend(callback: AsyncCallback<boolean>): void
```

暂停下载正在运行中的任务，已暂停的任务可被[restore](arkts-basicservices-request-downloadtask-i.md#restore-1)恢复，使用callback异步回调。

> **说明：**  
>  
> 由于不存在401报错场景，在api12中 `401 the parameters check fails` 这个错误码被移除。

**起始版本：** 9

**需要权限：** ohos.permission.INTERNET

<!--Device-DownloadTask-suspend(callback: AsyncCallback<boolean>): void--><!--Device-DownloadTask-suspend(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示暂停下载任务成功；返回false表示暂停下载任务失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permissions check fails. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // 需要手动将url替换为真实服务器的HTTP协议地址
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
  console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
}

```

<a id="suspend-1"></a>
## suspend

```TypeScript
suspend(): Promise<boolean>
```

暂停下载正在运行中的任务，已暂停的任务可被[restore](arkts-basicservices-request-downloadtask-i.md#restore-1)恢复，使用Promise异步回调。

> **说明：**  
>  
> 由于不存在401报错场景，在api12中 `401 the parameters check fails` 这个错误码被移除。

**起始版本：** 9

**需要权限：** ohos.permission.INTERNET

<!--Device-DownloadTask-suspend(): Promise<boolean>--><!--Device-DownloadTask-suspend(): Promise<boolean>-End-->

**系统能力：** SystemCapability.MiscServices.Download

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示暂停下载正在运行中的任务成功；返回false表示暂停下载正在运行中的任务失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permissions check fails. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // 需要手动将url替换为真实服务器的HTTP协议地址
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
  console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
}

```

