# OnDownloadCompleteOptions

**Since:** 3

**Deprecated since:** 9

**Substitutes:** on

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

Called when API call has failed. Header information and HTTP status code returned when the upload task fails.

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
success?: (data: OnDownloadCompleteResponse) => void
```

Called when API call is successful.

**Since:** 3

**Deprecated since:** 9

**Substitutes:** on

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

**Substitutes:** tid

**System capability:** SystemCapability.MiscServices.Download
