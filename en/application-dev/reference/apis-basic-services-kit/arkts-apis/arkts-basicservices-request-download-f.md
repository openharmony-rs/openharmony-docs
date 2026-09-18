# download

## Modules to Import

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## download

```TypeScript
function download(config: DownloadConfig, callback: AsyncCallback<DownloadTask>): void
```

Downloads a file. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [downloadFile](arkts-basicservices-request-downloadfile-f.md)(context: BaseContext, config: DownloadConfig, callback: AsyncCallback&lt;DownloadTask&gt;)

**Required permissions:** ohos.permission.INTERNET

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.MiscServices.Download

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [DownloadConfig](arkts-basicservices-request-downloadconfig-i.md) | Yes | Download configuration. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[DownloadTask](arkts-basicservices-request-downloadtask-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the **DownloadTask** object obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The permissions check fails. |

**Examples**

```TypeScript
let downloadTask: request.DownloadTask;
// Replace the URL with the HTTP address of the real server.
request.download({ url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
  downloadTask = data;
}).catch((err: BusinessError) => {
  console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
})
```

```TypeScript
let downloadTask: request.DownloadTask;
// Replace the URL with the HTTP address of the real server.
request.download({ url: 'https://xxxx/xxxxx.hap', 
filePath: 'xxx/xxxxx.hap'}, (err: BusinessError, data: request.DownloadTask) => {
  if (err) {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  downloadTask = data;
});
```


## download

```TypeScript
function download(config: DownloadConfig): Promise<DownloadTask>
```

Downloads a file. This API uses a promise to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [downloadFile](arkts-basicservices-request-downloadfile-f.md)(context: BaseContext, config: DownloadConfig)

**Required permissions:** ohos.permission.INTERNET

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.MiscServices.Download

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [DownloadConfig](arkts-basicservices-request-downloadconfig-i.md) | Yes | Download configuration. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DownloadTask](arkts-basicservices-request-downloadtask-i.md)&gt; | Promise used to return the **DownloadTask** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The permissions check fails. |

**Examples**

See [download](#download)
