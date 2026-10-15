# OnDownloadCompleteOptions

```TypeScript
export interface OnDownloadCompleteOptions
```

**Since:** 3

**Deprecated since:** 9

**Substitutes:** [on](arkts-basicservices-agent-task-i.md#on)

<!--Device-unnamed-export interface OnDownloadCompleteOptions--><!--Device-unnamed-export interface OnDownloadCompleteOptions-End-->

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

<!--Device-OnDownloadCompleteOptions-complete?: () => void--><!--Device-OnDownloadCompleteOptions-complete?: () => void-End-->

**System capability:** SystemCapability.MiscServices.Download

## fail

```TypeScript
fail?: (data: any, code: number) => void
```

Called when API call has failed. Header information and HTTP status code returned when the upload task fails.

**Since:** 3

**Deprecated since:** 9

**Substitutes:** [on](arkts-basicservices-agent-task-i.md#on)

<!--Device-OnDownloadCompleteOptions-fail?: (data: any, code: number) => void--><!--Device-OnDownloadCompleteOptions-fail?: (data: any, code: number) => void-End-->

**System capability:** SystemCapability.MiscServices.Download

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | any | Yes |  |
| code | number | Yes |  |

## success

```TypeScript
success?: (data: OnDownloadCompleteResponse) => void
```

Called when API call is successful.

**Since:** 3

**Deprecated since:** 9

**Substitutes:** [on](arkts-basicservices-agent-task-i.md#on)

<!--Device-OnDownloadCompleteOptions-success?: (data: OnDownloadCompleteResponse) => void--><!--Device-OnDownloadCompleteOptions-success?: (data: OnDownloadCompleteResponse) => void-End-->

**System capability:** SystemCapability.MiscServices.Download

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [OnDownloadCompleteResponse](arkts-basicservices-system-request-ondownloadcompleteresponse-i.md) | Yes |  |

## token

```TypeScript
token: string
```

Result token returned by the download API.

**Type:** string

**Since:** 3

**Deprecated since:** 9

**Substitutes:** [tid](arkts-basicservices-agent-task-i.md#tid)

<!--Device-OnDownloadCompleteOptions-token: string--><!--Device-OnDownloadCompleteOptions-token: string-End-->

**System capability:** SystemCapability.MiscServices.Download
