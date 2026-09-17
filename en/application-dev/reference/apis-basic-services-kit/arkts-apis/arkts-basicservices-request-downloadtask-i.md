# DownloadTask

Implements file downloads. Before using any APIs of this class, you must obtain a **DownloadTask** object, from a promise through [request.downloadFile](arkts-basicservices-request-downloadfile-f.md) or from a callback through [request.downloadFile](arkts-basicservices-request-downloadfile-f.md).

**Since:** 6

**System capability:** SystemCapability.MiscServices.Download

## Modules to Import

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

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

See [getTaskInfo](#gettaskinfo)

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

See [getTaskMimeType](#gettaskmimetype)

## off('progress')

```TypeScript
off(type: 'progress', callback?: (receivedSize: number, totalSize: number) => void): void
```

Unsubscribes from download progress events.

**Since:** 6

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

## off('complete' | 'pause' | 'remove')

```TypeScript
off(type: 'complete' | 'pause' | 'remove', callback?: () => void): void
```

Unsubscribes from download events.

**Since:** 7

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

## off('complete' | 'pause' | 'remove')

```TypeScript
off(type: 'complete' | 'pause' | 'remove', callback?: () => void): void
```

Unsubscribes from download events.

**Since:** 7

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

## off('complete' | 'pause' | 'remove')

```TypeScript
off(type: 'complete' | 'pause' | 'remove', callback?: () => void): void
```

Unsubscribes from download events.

**Since:** 7

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

## off('fail')

```TypeScript
off(type: 'fail', callback?: (err: number) => void): void
```

Unsubscribes from download failure events.

**Since:** 7

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

## on('complete' | 'pause' | 'remove')

```TypeScript
on(type: 'complete' | 'pause' | 'remove', callback: () => void): void
```

Subscribes to download events. This API uses an asynchronous callback to return the result.

**Since:** 7

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

## on('complete' | 'pause' | 'remove')

```TypeScript
on(type: 'complete' | 'pause' | 'remove', callback: () => void): void
```

Subscribes to download events. This API uses an asynchronous callback to return the result.

**Since:** 7

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

## on('complete' | 'pause' | 'remove')

```TypeScript
on(type: 'complete' | 'pause' | 'remove', callback: () => void): void
```

Subscribes to download events. This API uses an asynchronous callback to return the result.

**Since:** 7

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

## on('fail')

```TypeScript
on(type: 'fail', callback: (err: number) => void): void
```

Subscribes to download failure events. This API uses an asynchronous callback to return the result.

**Since:** 7

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

## pause

```TypeScript
pause(callback: AsyncCallback<void>): void
```

Pauses this download task. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [suspend](#suspend)(callback: AsyncCallback&lt;boolean&gt;)

**Required permissions:** ohos.permission.INTERNET

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
downloadTask.pause().then(() => {    
  console.info('Succeeded in pausing the download task.');
}).catch((err: BusinessError) => {
  console.error(`Failed to pause the download task. Code: ${err.code}, message: ${err.message}`);
});
```

```TypeScript
downloadTask.pause((err: BusinessError) => {
  if(err) {
    console.error(`Failed to pause the download task. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in pausing the download task.');
});
```

## pause

```TypeScript
pause(): Promise<void>
```

Pauses this download task. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [suspend](#suspend)()

**Required permissions:** ohos.permission.INTERNET

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

```TypeScript
downloadTask.pause((err: BusinessError) => {
  if(err) {
    console.error(`Failed to pause the download task. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in pausing the download task.');
});
```

## query

```TypeScript
query(callback: AsyncCallback<DownloadInfo>): void
```

Queries this download task. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getTaskInfo](#gettaskinfo)(callback: AsyncCallback&lt;DownloadInfo&gt;)

**Required permissions:** ohos.permission.INTERNET

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
downloadTask.query().then((downloadInfo) => {    
  console.info('Succeeded in querying the download task.')
}).catch((err: BusinessError) => {
  console.error(`Failed to query the download task. Code: ${err.code}, message: ${err.message}`)
});
```

```TypeScript
downloadTask.query((err: BusinessError, downloadInfo: request.DownloadInfo)=>{
  if(err) {
    console.error(`Failed to query the download mimeType. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in querying the download task.');
  }
});
```

## query

```TypeScript
query(): Promise<DownloadInfo>
```

Queries this download task. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getTaskInfo](#gettaskinfo)()

**Required permissions:** ohos.permission.INTERNET

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

See [query](#query)

## queryMimeType

```TypeScript
queryMimeType(callback: AsyncCallback<string>): void
```

Queries the MIME type of this download task. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getTaskMimeType](#gettaskmimetype)(callback: AsyncCallback&lt;string&gt;)

**Required permissions:** ohos.permission.INTERNET

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
downloadTask.queryMimeType().then((data: string) => {    
  console.info('Succeeded in querying the download MimeType.');
}).catch((err: BusinessError) => {
  console.error(`Failed to query the download MimeType. Code: ${err.code}, message: ${err.message}`)
});
```

```TypeScript
downloadTask.queryMimeType((err: BusinessError, data: string)=>{
  if(err) {
    console.error(`Failed to query the download mimeType. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in querying the download mimeType.');
  }
});
```

## queryMimeType

```TypeScript
queryMimeType(): Promise<string>
```

Queries the MIME type of this download task. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getTaskMimeType](#gettaskmimetype)()

**Required permissions:** ohos.permission.INTERNET

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

See [queryMimeType](#querymimetype)

## remove

```TypeScript
remove(callback: AsyncCallback<boolean>): void
```

Deletes the download task. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [delete](arkts-basicservices-request-uploadtask-i.md#delete)(callback: AsyncCallback&lt;boolean&gt;)

**Required permissions:** ohos.permission.INTERNET

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
downloadTask.remove().then((result) => {
  console.info('Succeeded in removing the download task.');
}).catch ((err: BusinessError) => {
  console.error(`Failed to remove the download task. Code: ${err.code}, message: ${err.message}`);
});
```

```TypeScript
downloadTask.remove((err, result)=>{
  if(err) {
    console.error(`Failed to remove the download task. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in removing the download task.');
});
```

## remove

```TypeScript
remove(): Promise<boolean>
```

Deletes the download task. This API uses a promise to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [delete](arkts-basicservices-request-uploadtask-i.md#delete)()

**Required permissions:** ohos.permission.INTERNET

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

```TypeScript
downloadTask.remove((err, result)=>{
  if(err) {
    console.error(`Failed to remove the download task. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in removing the download task.');
});
```

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

See [restore](#restore)

## resume

```TypeScript
resume(callback: AsyncCallback<void>): void
```

Restores the download task. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [restore](#restore)(callback: AsyncCallback&lt;boolean&gt;)

**Required permissions:** ohos.permission.INTERNET

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
downloadTask.resume().then(() => {
  console.info('Succeeded in resuming the download task.')
}).catch((err: BusinessError) => {
  console.error(`Failed to resume the download task. Code: ${err.code}, message: ${err.message}`);
});
```

```TypeScript
downloadTask.resume((err: BusinessError) => {
  if (err) {
    console.error(`Failed to resume the download task. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in resuming the download task.');
});
```

## resume

```TypeScript
resume(): Promise<void>
```

Restores the download task. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [restore](#restore)()

**Required permissions:** ohos.permission.INTERNET

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

```TypeScript
downloadTask.resume((err: BusinessError) => {
  if (err) {
    console.error(`Failed to resume the download task. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in resuming the download task.');
});
```

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

See [suspend](#suspend)
