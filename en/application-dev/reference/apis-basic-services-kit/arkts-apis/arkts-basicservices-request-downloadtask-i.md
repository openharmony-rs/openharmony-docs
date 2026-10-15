# DownloadTask

```TypeScript
interface DownloadTask
```

Implements file downloads. Before using any APIs of this class, you must obtain a **DownloadTask** object, from a promise through [request.downloadFile](arkts-basicservices-request-downloadfile-f.md#downloadfile2) or from a callback through [request.downloadFile](arkts-basicservices-request-downloadfile-f.md#downloadfile1).

**Since:** 6

<!--Device-request-interface DownloadTask--><!--Device-request-interface DownloadTask-End-->

**System capability:** SystemCapability.MiscServices.Download

## Modules to Import

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

<a id="delete1"></a>

## delete

```TypeScript
delete(callback: AsyncCallback<boolean>): void
```

Deletes the download task. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> The scenarios for triggering error code **401 the parameters check fails** do not exist. Therefore, this error
> code is removed from API version 12.

**Since:** 9

**Required permissions:** ohos.permission.INTERNET

<!--Device-DownloadTask-delete(callback: AsyncCallback<boolean>): void--><!--Device-DownloadTask-delete(callback: AsyncCallback<boolean>): void-End-->

**System capability:** SystemCapability.MiscServices.Download

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** indicates that the operation is successful; **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The permissions check fails. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // Replace the URL with the HTTP address of the real server.
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

<a id="delete2"></a>

## delete

```TypeScript
delete(): Promise<boolean>
```

Deletes the download task. This API uses a promise to return the result.

> **NOTE:** 
> 
> The scenarios for triggering error code **401 the parameters check fails** do not exist. Therefore, this error
> code is removed from API version 12.

**Since:** 9

**Required permissions:** ohos.permission.INTERNET

<!--Device-DownloadTask-delete(): Promise<boolean>--><!--Device-DownloadTask-delete(): Promise<boolean>-End-->

**System capability:** SystemCapability.MiscServices.Download

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the operation is successful; **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The permissions check fails. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // Replace the URL with the HTTP address of the real server.
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

<a id="gettaskinfo1"></a>

## getTaskInfo

```TypeScript
getTaskInfo(callback: AsyncCallback<DownloadInfo>): void
```

Obtains the information about this download task. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> The scenarios for triggering error code **401 the parameters check fails** do not exist. Therefore, this error
> code is removed from API version 12.

**Since:** 9

**Required permissions:** ohos.permission.INTERNET

<!--Device-DownloadTask-getTaskInfo(callback: AsyncCallback<DownloadInfo>): void--><!--Device-DownloadTask-getTaskInfo(callback: AsyncCallback<DownloadInfo>): void-End-->

**System capability:** SystemCapability.MiscServices.Download

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[DownloadInfo](arkts-basicservices-request-downloadinfo-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the **DownloadInfo** object obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The permissions check fails. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // Replace the URL with the HTTP address of the real server.
  request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
    let downloadTask: request.DownloadTask = data;
    downloadTask.getTaskInfo((err: BusinessError, downloadInfo: request.DownloadInfo) => {
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

<a id="gettaskinfo2"></a>

## getTaskInfo

```TypeScript
getTaskInfo(): Promise<DownloadInfo>
```

Obtains the information about this download task. This API uses a promise to return the result.

> **NOTE:** 
> 
> The scenarios for triggering error code **401 the parameters check fails** do not exist. Therefore, this error
> code is removed from API version 12.

**Since:** 9

**Required permissions:** ohos.permission.INTERNET

<!--Device-DownloadTask-getTaskInfo(): Promise<DownloadInfo>--><!--Device-DownloadTask-getTaskInfo(): Promise<DownloadInfo>-End-->

**System capability:** SystemCapability.MiscServices.Download

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DownloadInfo](arkts-basicservices-request-downloadinfo-i.md)&gt; | Promise used to return a **DownloadInfo** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The permissions check fails. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // Replace the URL with the HTTP address of the real server.
  request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
    let downloadTask: request.DownloadTask = data;
    downloadTask.getTaskInfo().then((downloadInfo: request.DownloadInfo) => {
      console.info('Succeeded in querying the download task')
    }).catch((err: BusinessError) => {
      console.error(`Failed to query the download task. Code: ${err.code}, message: ${err.message}`)
    });
  }).catch((err: BusinessError) => {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  })
} catch (err) {
  console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
}
```

<a id="gettaskmimetype1"></a>

## getTaskMimeType

```TypeScript
getTaskMimeType(callback: AsyncCallback<string>): void
```

Obtains the MIME type (that is, media type of resources in HTTP) of a download task. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> The scenarios for triggering error code **401 the parameters check fails** do not exist. Therefore, this error
> code is removed from API version 12.

**Since:** 9

**Required permissions:** ohos.permission.INTERNET

<!--Device-DownloadTask-getTaskMimeType(callback: AsyncCallback<string>): void--><!--Device-DownloadTask-getTaskMimeType(callback: AsyncCallback<string>): void-End-->

**System capability:** SystemCapability.MiscServices.Download

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and data is the **MimeType** object obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The permissions check fails. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // Replace the URL with the HTTP address of the real server.
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

<a id="gettaskmimetype2"></a>

## getTaskMimeType

```TypeScript
getTaskMimeType(): Promise<string>
```

Obtains the MIME type (that is, media type of resources in HTTP) of a download task. This API uses a promise to return the result.

> **NOTE:** 
> 
> The scenarios for triggering error code **401 the parameters check fails** do not exist. Therefore, this error
> code is removed from API version 12.

**Since:** 9

**Required permissions:** ohos.permission.INTERNET

<!--Device-DownloadTask-getTaskMimeType(): Promise<string>--><!--Device-DownloadTask-getTaskMimeType(): Promise<string>-End-->

**System capability:** SystemCapability.MiscServices.Download

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the MIME type of a download task. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The permissions check fails. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // Replace the URL with the HTTP address of the real server.
  request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
    let downloadTask: request.DownloadTask = data;
    downloadTask.getTaskMimeType().then((data: string) => {
      console.info('Succeeded in querying the download MimeType');
    }).catch((err: BusinessError) => {
      console.error(`Failed to query the download MimeType. Code: ${err.code}, message: ${err.message}`)
    });
  }).catch((err: BusinessError) => {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  })
} catch (err) {
  console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
}
```

## off('progress')

```TypeScript
off(type: 'progress', callback?: (receivedSize: number, totalSize: number) => void): void
```

Unsubscribes from download progress events.

**Since:** 6

<!--Device-DownloadTask-off(type: 'progress', callback?: (receivedSize: long, totalSize: long) => void): void--><!--Device-DownloadTask-off(type: 'progress', callback?: (receivedSize: long, totalSize: long) => void): void-End-->

**System capability:** SystemCapability.MiscServices.Download

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'progress' | Yes | Event type.<br>- **'progress'**: download progress. |
| callback | (receivedSize: number, totalSize: number) =&gt; void | No | Callback to unregister. If this parameter is not specified, all callbacks of the current type will be unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameters check fails. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // Replace the URL with the HTTP address of the real server.
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
    // Unsubscribe from progressCallback1.
    downloadTask.off('progress', progressCallback1);
    // Unsubscribe from all callbacks of download progress events.
    downloadTask.off('progress');
  }).catch((err: BusinessError) => {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  })
} catch (err) {
  console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
}
```

## off('complete' | 'pause' | 'remove')

```TypeScript
off(type: 'complete' | 'pause' | 'remove', callback?: () => void): void
```

Unsubscribes from download events.

**Since:** 7

<!--Device-DownloadTask-off(type: 'complete' | 'pause' | 'remove', callback?: () => void): void--><!--Device-DownloadTask-off(type: 'complete' | 'pause' | 'remove', callback?: () => void): void-End-->

**System capability:** SystemCapability.MiscServices.Download

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'complete' &#124; 'pause' &#124; 'remove' | Yes | Event type.<br>- **'complete'**: download task completion.<br>- **'pause'**: download task pause.<br>- **'remove'**: download task removal. |
| callback | () =&gt; void | No | Callback to unregister. If this parameter is not specified, all callbacks of the current type will be unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameters check fails. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // Replace the URL with the HTTP address of the real server.
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
    // Unsubscribe from completeCallback1.
    downloadTask.off('complete', completeCallback1);
    // Unsubscribe from all callbacks of the download completion events.
    downloadTask.off('complete');

    let pauseCallback1 = () => {
      console.info('Download delete pause notification.');
    };
    let pauseCallback2 = () => {
      console.info('Download delete pause notification.');
    };
    downloadTask.on('pause', pauseCallback1);
    downloadTask.on('pause', pauseCallback2);
    // Unsubscribe from pauseCallback1.
    downloadTask.off('pause', pauseCallback1);
    // Unsubscribe from all callbacks of the download pause events.
    downloadTask.off('pause');

    let removeCallback1 = () => {
      console.info('Download delete remove notification.');
    };
    let removeCallback2 = () => {
      console.info('Download delete remove notification.');
    };
    downloadTask.on('remove', removeCallback1);
    downloadTask.on('remove', removeCallback2);
    // Unsubscribe from removeCallback1.
    downloadTask.off('remove', removeCallback1);
    // Unsubscribe from all callbacks of the download removal events.
    downloadTask.off('remove');
  }).catch((err: BusinessError) => {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  })
} catch (err) {
  console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
}
```

## off('fail')

```TypeScript
off(type: 'fail', callback?: (err: number) => void): void
```

Unsubscribes from download failure events.

**Since:** 7

<!--Device-DownloadTask-off(type: 'fail', callback?: (err: int) => void): void--><!--Device-DownloadTask-off(type: 'fail', callback?: (err: int) => void): void-End-->

**System capability:** SystemCapability.MiscServices.Download

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'fail' | Yes | Event type.<br>- **'fail'**: download task failure. |
| callback | (err: number) =&gt; void | No | Callback to unregister. If this parameter is not specified, all callbacks of the current type will be unregistered.For details about the error codes, see [Download Error Codes](../../../reference/apis-basic-services-kit/js-apis-request.md#constants). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameters check fails. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // Replace the URL with the HTTP address of the real server.
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
    // Unsubscribe from failCallback1.
    downloadTask.off('fail', failCallback1);
    // Unsubscribe from all callbacks of the download failure events.
    downloadTask.off('fail');
  }).catch((err: BusinessError) => {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  })
} catch (err) {
  console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
}
```

## on('progress')

```TypeScript
on(type: 'progress', callback: (receivedSize: number, totalSize: number) => void): void
```

Subscribes to download progress events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> To maintain a balance between power consumption and performance, this API cannot be called when the application
> is running in the background.

**Since:** 6

<!--Device-DownloadTask-on(type: 'progress', callback: (receivedSize: long, totalSize: long) => void): void--><!--Device-DownloadTask-on(type: 'progress', callback: (receivedSize: long, totalSize: long) => void): void-End-->

**System capability:** SystemCapability.MiscServices.Download

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'progress' | Yes | Event type.<br>- **'progress'**: download progress. |
| callback | (receivedSize: number, totalSize: number) =&gt; void | Yes | Callback used to return the size of the uploaded file and the total size of the file to upload, in bytes. If the server uses the chunk mode for data transmission and the total file size cannot be obtained from the request header, the value of **totalSize** is treated as **-1**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameters check fails. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // Replace the URL with the HTTP address of the real server.
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

## on('complete' | 'pause' | 'remove')

```TypeScript
on(type: 'complete' | 'pause' | 'remove', callback: () => void): void
```

Subscribes to download events. This API uses an asynchronous callback to return the result.

**Since:** 7

<!--Device-DownloadTask-on(type: 'complete' | 'pause' | 'remove', callback: () => void): void--><!--Device-DownloadTask-on(type: 'complete' | 'pause' | 'remove', callback: () => void): void-End-->

**System capability:** SystemCapability.MiscServices.Download

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'complete' &#124; 'pause' &#124; 'remove' | Yes | Event type.<br>- **'complete'**: download task completion.<br>- **'pause'**: download task pause.<br>- **'remove'**: download task removal. |
| callback | () =&gt; void | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameters check fails. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // Replace the URL with the HTTP address of the real server.
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

## on('fail')

```TypeScript
on(type: 'fail', callback: (err: number) => void): void
```

Subscribes to download failure events. This API uses an asynchronous callback to return the result.

**Since:** 7

<!--Device-DownloadTask-on(type: 'fail', callback: (err: int) => void): void--><!--Device-DownloadTask-on(type: 'fail', callback: (err: int) => void): void-End-->

**System capability:** SystemCapability.MiscServices.Download

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'fail' | Yes | Event type.<br>- **'fail'**: download task failure. |
| callback | (err: number) =&gt; void | Yes | Callback for the download task failure event.For details about the error codes, see [Download Error Codes](../../../reference/apis-basic-services-kit/js-apis-request.md#constants). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameters check fails. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // Replace the URL with the HTTP address of the real server.
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

<a id="restore1"></a>

## restore

```TypeScript
restore(callback: AsyncCallback<boolean>): void
```

Restores the download task. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> The scenarios for triggering error code **401 the parameters check fails** do not exist. Therefore, this error
> code is removed from API version 12.

**Since:** 9

**Required permissions:** ohos.permission.INTERNET

<!--Device-DownloadTask-restore(callback: AsyncCallback<boolean>): void--><!--Device-DownloadTask-restore(callback: AsyncCallback<boolean>): void-End-->

**System capability:** SystemCapability.MiscServices.Download

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** indicates that the operation is successful; **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The permissions check fails. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // Replace the URL with the HTTP address of the real server.
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

<a id="restore2"></a>

## restore

```TypeScript
restore(): Promise<boolean>
```

Restores the download task. This API uses a promise to return the result.

> **NOTE:** 
> 
> The scenarios for triggering error code **401 the parameters check fails** do not exist. Therefore, this error
> code is removed from API version 12.

**Since:** 9

**Required permissions:** ohos.permission.INTERNET

<!--Device-DownloadTask-restore(): Promise<boolean>--><!--Device-DownloadTask-restore(): Promise<boolean>-End-->

**System capability:** SystemCapability.MiscServices.Download

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the operation is successful; **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The permissions check fails. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // Replace the URL with the HTTP address of the real server.
  request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
    let downloadTask: request.DownloadTask = data;
    downloadTask.restore().then((result: boolean) => {
      console.info('Succeeded in resuming the download task.')
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

<a id="suspend1"></a>

## suspend

```TypeScript
suspend(callback: AsyncCallback<boolean>): void
```

Suspends this download task. You can use [restore](#restore) to restore the download. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> The scenarios for triggering error code **401 the parameters check fails** do not exist. Therefore, this error
> code is removed from API version 12.

**Since:** 9

**Required permissions:** ohos.permission.INTERNET

<!--Device-DownloadTask-suspend(callback: AsyncCallback<boolean>): void--><!--Device-DownloadTask-suspend(callback: AsyncCallback<boolean>): void-End-->

**System capability:** SystemCapability.MiscServices.Download

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** indicates that the operation is successful; **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The permissions check fails. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // Replace the URL with the HTTP address of the real server.
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

<a id="suspend2"></a>

## suspend

```TypeScript
suspend(): Promise<boolean>
```

Suspends this download task. You can use [restore](#restore) to restore the download. This API uses a promise to return the result.

> **NOTE:** 
> 
> The scenarios for triggering error code **401 the parameters check fails** do not exist. Therefore, this error
> code is removed from API version 12.

**Since:** 9

**Required permissions:** ohos.permission.INTERNET

<!--Device-DownloadTask-suspend(): Promise<boolean>--><!--Device-DownloadTask-suspend(): Promise<boolean>-End-->

**System capability:** SystemCapability.MiscServices.Download

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the operation is successful; **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The permissions check fails. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // Replace the URL with the HTTP address of the real server.
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

<a id="pause1"></a>

## pause

```TypeScript
pause(callback: AsyncCallback<void>): void
```

Pauses this download task. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [suspend](#suspend1)(callback: AsyncCallback&lt;boolean&gt;)

**Required permissions:** ohos.permission.INTERNET

<!--Device-DownloadTask-pause(callback: AsyncCallback<void>): void--><!--Device-DownloadTask-pause(callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.MiscServices.Download

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The permissions check fails. |

**Examples**

```TypeScript
downloadTask.pause((err: BusinessError) => {
  if(err) {
    console.error(`Failed to pause the download task. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in pausing the download task.');
});
```

<a id="pause2"></a>

## pause

```TypeScript
pause(): Promise<void>
```

Pauses this download task. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [suspend](#suspend)()

**Required permissions:** ohos.permission.INTERNET

<!--Device-DownloadTask-pause(): Promise<void>--><!--Device-DownloadTask-pause(): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.Download

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The permissions check fails. |

**Examples**

```TypeScript
downloadTask.pause().then(() => {    
  console.info('Succeeded in pausing the download task.');
}).catch((err: BusinessError) => {
  console.error(`Failed to pause the download task. Code: ${err.code}, message: ${err.message}`);
});
```

<a id="query1"></a>

## query

```TypeScript
query(callback: AsyncCallback<DownloadInfo>): void
```

Queries this download task. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getTaskInfo](#gettaskinfo1)(callback: AsyncCallback&lt;DownloadInfo&gt;)

**Required permissions:** ohos.permission.INTERNET

<!--Device-DownloadTask-query(callback: AsyncCallback<DownloadInfo>): void--><!--Device-DownloadTask-query(callback: AsyncCallback<DownloadInfo>): void-End-->

**System capability:** SystemCapability.MiscServices.Download

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[DownloadInfo](arkts-basicservices-request-downloadinfo-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the **DownloadInfo** object obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The permissions check fails. |

**Examples**

```TypeScript
downloadTask.query((err: BusinessError, downloadInfo: request.DownloadInfo)=>{
  if(err) {
    console.error(`Failed to query the download mimeType. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in querying the download task.');
  }
});
```

<a id="query2"></a>

## query

```TypeScript
query(): Promise<DownloadInfo>
```

Queries this download task. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getTaskInfo](#gettaskinfo)()

**Required permissions:** ohos.permission.INTERNET

<!--Device-DownloadTask-query(): Promise<DownloadInfo>--><!--Device-DownloadTask-query(): Promise<DownloadInfo>-End-->

**System capability:** SystemCapability.MiscServices.Download

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DownloadInfo](arkts-basicservices-request-downloadinfo-i.md)&gt; | Promise used to return the **DownloadInfo** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The permissions check fails. |

**Examples**

```TypeScript
downloadTask.query().then((downloadInfo) => {    
  console.info('Succeeded in querying the download task.')
}).catch((err: BusinessError) => {
  console.error(`Failed to query the download task. Code: ${err.code}, message: ${err.message}`)
});
```

<a id="querymimetype1"></a>

## queryMimeType

```TypeScript
queryMimeType(callback: AsyncCallback<string>): void
```

Queries the MIME type of this download task. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getTaskMimeType](#gettaskmimetype1)(callback: AsyncCallback&lt;string&gt;)

**Required permissions:** ohos.permission.INTERNET

<!--Device-DownloadTask-queryMimeType(callback: AsyncCallback<string>): void--><!--Device-DownloadTask-queryMimeType(callback: AsyncCallback<string>): void-End-->

**System capability:** SystemCapability.MiscServices.Download

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and data is the **MimeType** object obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The permissions check fails. |

**Examples**

```TypeScript
downloadTask.queryMimeType((err: BusinessError, data: string)=>{
  if(err) {
    console.error(`Failed to query the download mimeType. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in querying the download mimeType.');
  }
});
```

<a id="querymimetype2"></a>

## queryMimeType

```TypeScript
queryMimeType(): Promise<string>
```

Queries the MIME type of this download task. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getTaskMimeType](#gettaskmimetype)()

**Required permissions:** ohos.permission.INTERNET

<!--Device-DownloadTask-queryMimeType(): Promise<string>--><!--Device-DownloadTask-queryMimeType(): Promise<string>-End-->

**System capability:** SystemCapability.MiscServices.Download

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the MIME type of a download task. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The permissions check fails. |

**Examples**

```TypeScript
downloadTask.queryMimeType().then((data: string) => {    
  console.info('Succeeded in querying the download MimeType.');
}).catch((err: BusinessError) => {
  console.error(`Failed to query the download MimeType. Code: ${err.code}, message: ${err.message}`)
});
```

<a id="remove1"></a>

## remove

```TypeScript
remove(callback: AsyncCallback<boolean>): void
```

Deletes the download task. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [delete](arkts-basicservices-request-uploadtask-i.md#delete1)(callback: AsyncCallback&lt;boolean&gt;)

**Required permissions:** ohos.permission.INTERNET

<!--Device-DownloadTask-remove(callback: AsyncCallback<boolean>): void--><!--Device-DownloadTask-remove(callback: AsyncCallback<boolean>): void-End-->

**System capability:** SystemCapability.MiscServices.Download

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** indicates that the operation is successful; **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The permissions check fails. |

**Examples**

```TypeScript
downloadTask.remove((err, result)=>{
  if(err) {
    console.error(`Failed to remove the download task. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in removing the download task.');
});
```

<a id="remove2"></a>

## remove

```TypeScript
remove(): Promise<boolean>
```

Deletes the download task. This API uses a promise to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [delete](arkts-basicservices-request-uploadtask-i.md#delete)()

**Required permissions:** ohos.permission.INTERNET

<!--Device-DownloadTask-remove(): Promise<boolean>--><!--Device-DownloadTask-remove(): Promise<boolean>-End-->

**System capability:** SystemCapability.MiscServices.Download

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the operation is successful; **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The permissions check fails. |

**Examples**

```TypeScript
downloadTask.remove().then((result) => {
  console.info('Succeeded in removing the download task.');
}).catch ((err: BusinessError) => {
  console.error(`Failed to remove the download task. Code: ${err.code}, message: ${err.message}`);
});
```

<a id="resume1"></a>

## resume

```TypeScript
resume(callback: AsyncCallback<void>): void
```

Restores the download task. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [restore](#restore1)(callback: AsyncCallback&lt;boolean&gt;)

**Required permissions:** ohos.permission.INTERNET

<!--Device-DownloadTask-resume(callback: AsyncCallback<void>): void--><!--Device-DownloadTask-resume(callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.MiscServices.Download

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The permissions check fails. |

**Examples**

```TypeScript
downloadTask.resume((err: BusinessError) => {
  if (err) {
    console.error(`Failed to resume the download task. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in resuming the download task.');
});
```

<a id="resume2"></a>

## resume

```TypeScript
resume(): Promise<void>
```

Restores the download task. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [restore](#restore)()

**Required permissions:** ohos.permission.INTERNET

<!--Device-DownloadTask-resume(): Promise<void>--><!--Device-DownloadTask-resume(): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.Download

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The permissions check fails. |

**Examples**

```TypeScript
downloadTask.resume().then(() => {
  console.info('Succeeded in resuming the download task.')
}).catch((err: BusinessError) => {
  console.error(`Failed to resume the download task. Code: ${err.code}, message: ${err.message}`);
});
```
