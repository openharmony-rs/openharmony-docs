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

<!--Device-unnamed-export interface DownloadRequestOptions--><!--Device-unnamed-export interface DownloadRequestOptions-End-->

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

**Substitutes:** [on](arkts-basicservices-agent-task-i.md#on)

<!--Device-DownloadRequestOptions-complete?: () => void--><!--Device-DownloadRequestOptions-complete?: () => void-End-->

**System capability:** SystemCapability.MiscServices.Download

## fail

```TypeScript
fail?: (data: any, code: number) => void
```

Called when downloading fails.

**Since:** 3

**Deprecated since:** 9

**Substitutes:** [on](arkts-basicservices-agent-task-i.md#on)

<!--Device-DownloadRequestOptions-fail?: (data: any, code: number) => void--><!--Device-DownloadRequestOptions-fail?: (data: any, code: number) => void-End-->

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

**Substitutes:** [on](arkts-basicservices-agent-task-i.md#on)

<!--Device-DownloadRequestOptions-success?: (data: DownloadResponse) => void--><!--Device-DownloadRequestOptions-success?: (data: DownloadResponse) => void-End-->

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

**Substitutes:** [description](arkts-basicservices-agent-config-i.md#description)

<!--Device-DownloadRequestOptions-description?: string--><!--Device-DownloadRequestOptions-description?: string-End-->

**System capability:** SystemCapability.MiscServices.Download

## filename

```TypeScript
filename?: string
```

Name of the file to downloaded. The value is obtained from the current request or resource URL by default.

**Type:** string

**Since:** 3

**Deprecated since:** 9

**Substitutes:** [saveas](arkts-basicservices-agent-config-i.md#saveas)

<!--Device-DownloadRequestOptions-filename?: string--><!--Device-DownloadRequestOptions-filename?: string-End-->

**System capability:** SystemCapability.MiscServices.Download

## header

```TypeScript
header?: string
```

Request header.

**Type:** string

**Since:** 3

**Deprecated since:** 9

**Substitutes:** [headers](arkts-basicservices-agent-config-i.md#headers)

<!--Device-DownloadRequestOptions-header?: string--><!--Device-DownloadRequestOptions-header?: string-End-->

**System capability:** SystemCapability.MiscServices.Download

## url

```TypeScript
url: string
```

Resource URL.

**Type:** string

**Since:** 3

**Deprecated since:** 9

**Substitutes:** [url](arkts-basicservices-agent-config-i.md#url)

<!--Device-DownloadRequestOptions-url: string--><!--Device-DownloadRequestOptions-url: string-End-->

**System capability:** SystemCapability.MiscServices.Download
