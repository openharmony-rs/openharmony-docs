# Request

```TypeScript
export default class Request
```

**Since:** 3

**Deprecated since:** 9

**Substitutes:** [request](arkts-basicservices-request-n.md)

<!--Device-unnamed-export default class Request--><!--Device-unnamed-export default class Request-End-->

**System capability:** SystemCapability.MiscServices.Download

## Modules to Import

```TypeScript
import { Request, DownloadRequestOptions, DownloadResponse, OnDownloadCompleteOptions, OnDownloadCompleteResponse, RequestData, RequestFile, UploadRequestOptions, UploadResponse } from '@kit.BasicServicesKit';
```

## download

```TypeScript
static download(options: DownloadRequestOptions): void
```

Downloads a file. This API returns no value.

**Since:** 3

**Deprecated since:** 9

**Substitutes:** [downloadFile](arkts-basicservices-request-downloadfile-f.md#downloadfile-2)(context: BaseContext, config: DownloadConfig)

<!--Device-Request-static download(options: DownloadRequestOptions): void--><!--Device-Request-static download(options: DownloadRequestOptions): void-End-->

**System capability:** SystemCapability.MiscServices.Download

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [DownloadRequestOptions](arkts-basicservices-system-request-downloadrequestoptions-i.md) | Yes | Download configurations. |

**Examples**

```TypeScript
import  { Request, DownloadResponse, DownloadRequestOptions } from '@kit.BasicServicesKit';

let downloadRequestOptions: DownloadRequestOptions = {
  url: 'http://www.path.com',
  filename: 'requestSystemTest',
  header: "",
  description: 'this is requestSystem download response',
  success: (data: DownloadResponse) => {
    console.info('Succeeded in downloading, code:' + JSON.stringify(data));
  },
  fail: (data: string, code: number) => {
    console.info('Failed to download, data: ' + data + 'code: ' + code);
  },
  complete: () => {
    console.info('Download complete');
  }
}

try {
  Request.download(downloadRequestOptions);
  console.info('Start download');
} catch(err) {
  console.error('Failed to download, err:' + err);
}
```

## onDownloadComplete

```TypeScript
static onDownloadComplete(options: OnDownloadCompleteOptions): void
```

Listens for download task status. This API returns no value.

**Since:** 3

**Deprecated since:** 9

**Substitutes:** show(id: string)

<!--Device-Request-static onDownloadComplete(options: OnDownloadCompleteOptions): void--><!--Device-Request-static onDownloadComplete(options: OnDownloadCompleteOptions): void-End-->

**System capability:** SystemCapability.MiscServices.Download

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [OnDownloadCompleteOptions](arkts-basicservices-system-request-ondownloadcompleteoptions-i.md) | Yes | Configurations of the download task. |

**Examples**

```TypeScript
import  { Request, OnDownloadCompleteOptions, OnDownloadCompleteResponse } from '@kit.BasicServicesKit';

let onDownloadCompleteOptions: OnDownloadCompleteOptions = {
  token: 'token-index',
  success: (data: OnDownloadCompleteResponse) => {
    console.info('Succeeded in downloading, uri:' + JSON.stringify(data.uri));
  },
  fail: (data: string, code: number) => {
    console.info('Failed to download, data: ' + data + 'code: ' + code);
  },
  complete: () => {
    console.info('Download complete');
  }
}

Request.onDownloadComplete(onDownloadCompleteOptions);
```

## upload

```TypeScript
static upload(options: UploadRequestOptions): void
```

Uploads a file. This API returns no value.

**Since:** 3

**Deprecated since:** 9

**Substitutes:** [uploadFile](arkts-basicservices-request-uploadfile-f.md#uploadfile-2)(context: BaseContext, config: UploadConfig)

<!--Device-Request-static upload(options: UploadRequestOptions): void--><!--Device-Request-static upload(options: UploadRequestOptions): void-End-->

**System capability:** SystemCapability.MiscServices.Upload

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [UploadRequestOptions](arkts-basicservices-system-request-uploadrequestoptions-i.md) | Yes | Upload configurations. |

**Examples**

```TypeScript
import  { Request, UploadRequestOptions, UploadResponse } from '@kit.BasicServicesKit';

let uploadRequestOptions: UploadRequestOptions = {
  url: 'http://www.path.com',
  method: 'POST',
  files: [{
    filename: "test",
    name: "test",
    uri: "internal://cache/test.jpg",
    type: "jpg"
  }],
  data: [{
    name: "name123",
    value: "123"
  }],
  success: (data: UploadResponse) => {
    console.info('Succeeded in uploading, code:' + JSON.stringify(data.code));
  },
  fail: (data: string, code: number) => {
    console.info('Failed to upload, data: ' + data + 'code: ' + code);
  },
  complete: () => {
    console.info('Upload complete');
  }
}

try {
  Request.upload(uploadRequestOptions);
  console.info('Start Upload');
} catch (err) {
  console.error('Failed to upload, err:' + err);
}
```
