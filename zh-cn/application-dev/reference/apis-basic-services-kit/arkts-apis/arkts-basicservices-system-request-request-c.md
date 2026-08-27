# Request

**起始版本：** 3

**废弃版本：** 9

**替代接口：** [request](arkts-basicservices-request-n.md)

**系统能力：** SystemCapability.MiscServices.Download

## 导入模块

```TypeScript
import { Request, DownloadRequestOptions, DownloadResponse, OnDownloadCompleteOptions, OnDownloadCompleteResponse, RequestData, RequestFile, UploadRequestOptions, UploadResponse } from '@kit.BasicServicesKit';
```

## download

```TypeScript
static download(options: DownloadRequestOptions): void
```

下载文件，无返回值。

**起始版本：** 3

**废弃版本：** 9

**替代接口：** [downloadFile](arkts-basicservices-request-downloadfile-f.md)(context: BaseContext, config: DownloadConfig)

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DownloadRequestOptions](arkts-basicservices-system-request-downloadrequestoptions-i.md) | 是 | 下载的配置信息。 |

**示例**

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
} catch (err) {
  console.error('Failed to download, err:' + err);
}
```

## onDownloadComplete

```TypeScript
static onDownloadComplete(options: OnDownloadCompleteOptions): void
```

获取下载任务状态，无返回值。

**起始版本：** 3

**废弃版本：** 9

**替代接口：** show(id: string)

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [OnDownloadCompleteOptions](arkts-basicservices-system-request-ondownloadcompleteoptions-i.md) | 是 | 监听下载任务的配置信息。 |

**示例**

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

上传文件，无返回值。

**起始版本：** 3

**废弃版本：** 9

**替代接口：** [uploadFile](arkts-basicservices-request-uploadfile-f.md)(context: BaseContext, config: UploadConfig)

**系统能力：** SystemCapability.MiscServices.Upload

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [UploadRequestOptions](arkts-basicservices-system-request-uploadrequestoptions-i.md) | 是 | 上传的配置信息。 |

**示例**

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
