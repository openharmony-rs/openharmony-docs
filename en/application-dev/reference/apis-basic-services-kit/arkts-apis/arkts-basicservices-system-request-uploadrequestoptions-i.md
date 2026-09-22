# UploadRequestOptions

```TypeScript
export interface UploadRequestOptions
```


> **NOTE:** 
> 
> This API has been supported since API version 3 and deprecated since API version 9. You are advised to use
> [UploadConfig](arkts-basicservices-agent-config-i.md) instead.

**Since:** 3

**Deprecated since:** 9

**Substitutes:** [UploadConfig](arkts-basicservices-request-uploadconfig-i.md)

**System capability:** SystemCapability.MiscServices.Upload

## Modules to Import

```TypeScript
import { Request, DownloadRequestOptions, DownloadResponse, OnDownloadCompleteOptions, OnDownloadCompleteResponse, RequestData, RequestFile, UploadRequestOptions, UploadResponse } from '@kit.BasicServicesKit';
```

## complete

```TypeScript
complete?: () => void
```

Called when the execution is completed.

**Since:** 3

**Deprecated since:** 9

**Substitutes:** on

**System capability:** SystemCapability.MiscServices.Upload

## fail

```TypeScript
fail?: (data: any, code: number) => void
```

Called when uploading fails.

**Since:** 3

**Deprecated since:** 9

**Substitutes:** on

**System capability:** SystemCapability.MiscServices.Upload

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | any | Yes |  |
| code | number | Yes |  |

## success

```TypeScript
success?: (data: UploadResponse) => void
```

Called when the files are uploaded successfully.

**Since:** 3

**Deprecated since:** 9

**Substitutes:** on

**System capability:** SystemCapability.MiscServices.Upload

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [UploadResponse](arkts-basicservices-system-request-uploadresponse-i.md) | Yes |  |

## data

```TypeScript
data?: Array<RequestData>
```

Form data in the request body.

**Type:** Array&lt;[RequestData](arkts-basicservices-system-request-requestdata-i.md)&gt;

**Since:** 3

**Deprecated since:** 9

**Substitutes:** data

**System capability:** SystemCapability.MiscServices.Upload

## files

```TypeScript
files: Array<RequestFile>
```

List of files to upload, which is submitted through multipart/form-data.

**Type:** Array&lt;[RequestFile](arkts-basicservices-system-request-requestfile-i.md)&gt;

**Since:** 3

**Deprecated since:** 9

**Substitutes:** data

**System capability:** SystemCapability.MiscServices.Upload

## header

```TypeScript
header?: Object
```

Request header.

**Type:** Object

**Since:** 3

**Deprecated since:** 9

**Substitutes:** headers

**System capability:** SystemCapability.MiscServices.Upload

## method

```TypeScript
method?: string
```

Request methods available: POST and PUT. The default value is POST.

**Type:** string

**Since:** 3

**Deprecated since:** 9

**Substitutes:** method

**System capability:** SystemCapability.MiscServices.Upload

## url

```TypeScript
url: string
```

Resource URL.

**Type:** string

**Since:** 3

**Deprecated since:** 9

**Substitutes:** url

**System capability:** SystemCapability.MiscServices.Upload
