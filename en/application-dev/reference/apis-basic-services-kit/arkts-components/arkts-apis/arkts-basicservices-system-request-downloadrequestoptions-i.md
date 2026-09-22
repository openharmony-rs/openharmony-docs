# DownloadRequestOptions

```TypeScript
export interface DownloadRequestOptions
```


> **NOTE:** 
> 
> This API has been supported since API version 3 and deprecated since API version 9. You are advised to use
> [UploadConfig](arkts-basicservices-agent-config-i.md) instead.

**Since:** 3

**Deprecated since:** 9

**Substitutes:** [UploadConfig](arkts-basicservices-request-uploadconfig-i.md)

**System capability:** SystemCapability.MiscServices.Download

## Modules to Import

```TypeScript
import { Request, DownloadRequestOptions, DownloadResponse, OnDownloadCompleteOptions, OnDownloadCompleteResponse, RequestData, RequestFile, UploadRequestOptions, UploadResponse } from '@kit.BasicServicesKit';
```

## complete

```TypeScript
complete?: () => void
```

Called when API call is complete.

**Since:** 3

**Deprecated since:** 9

**Substitutes:** on

**System capability:** SystemCapability.MiscServices.Download

## fail

```TypeScript
fail?: (data: any, code: number) => void
```

Called when downloading fails.

**Since:** 3

**Deprecated since:** 9

**Substitutes:** on

**System capability:** SystemCapability.MiscServices.Download

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | any | Yes |  |
| code | number | Yes |  |

## success

```TypeScript
success?: (data: DownloadResponse) => void
```

Called when the files are successfully downloaded.

**Since:** 3

**Deprecated since:** 9

**Substitutes:** on

**System capability:** SystemCapability.MiscServices.Download

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [DownloadResponse](arkts-basicservices-system-request-downloadresponse-i.md) | Yes |  |

## description

```TypeScript
description?: string
```

Download description. The default value is the file name.

**Type:** string

**Since:** 3

**Deprecated since:** 9

**Substitutes:** description

**System capability:** SystemCapability.MiscServices.Download

## filename

```TypeScript
filename?: string
```

Name of the file to downloaded. The value is obtained from the current request or resource URL by default.

**Type:** string

**Since:** 3

**Deprecated since:** 9

**Substitutes:** saveas

**System capability:** SystemCapability.MiscServices.Download

## header

```TypeScript
header?: string
```

Request header.

**Type:** string

**Since:** 3

**Deprecated since:** 9

**Substitutes:** headers

**System capability:** SystemCapability.MiscServices.Download

## url

```TypeScript
url: string
```

Resource URL.

**Type:** string

**Since:** 3

**Deprecated since:** 9

**Substitutes:** url

**System capability:** SystemCapability.MiscServices.Download
