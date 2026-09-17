# Request

**Since:** 3

**Deprecated since:** 9

**Substitutes:** [request](arkts-basicservices-request-n.md)

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

**Substitutes:** [downloadFile](arkts-basicservices-request-downloadfile-f.md)(context: BaseContext, config: DownloadConfig)

**System capability:** SystemCapability.MiscServices.Download

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [DownloadRequestOptions](arkts-basicservices-system-request-downloadrequestoptions-i.md) | Yes | Download configurations. |

## onDownloadComplete

```TypeScript
static onDownloadComplete(options: OnDownloadCompleteOptions): void
```

Listens for download task status. This API returns no value.

**Since:** 3

**Deprecated since:** 9

**Substitutes:** show(id: string)

**System capability:** SystemCapability.MiscServices.Download

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [OnDownloadCompleteOptions](arkts-basicservices-system-request-ondownloadcompleteoptions-i.md) | Yes | Configurations of the download task. |

## upload

```TypeScript
static upload(options: UploadRequestOptions): void
```

Uploads a file. This API returns no value.

**Since:** 3

**Deprecated since:** 9

**Substitutes:** [uploadFile](arkts-basicservices-request-uploadfile-f.md)(context: BaseContext, config: UploadConfig)

**System capability:** SystemCapability.MiscServices.Upload

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [UploadRequestOptions](arkts-basicservices-system-request-uploadrequestoptions-i.md) | Yes | Upload configurations. |
