# RequestFile

**Since:** 3

**Deprecated since:** 9

**Substitutes:** [File](arkts-basicservices-request-file-i.md)

**System capability:** SystemCapability.MiscServices.Upload

## Modules to Import

```TypeScript
import { Request, DownloadRequestOptions, DownloadResponse, OnDownloadCompleteOptions, OnDownloadCompleteResponse, RequestData, RequestFile, UploadRequestOptions, UploadResponse } from '@kit.BasicServicesKit';
```

## filename

```TypeScript
filename?: string
```

File name in the header when **multipart** is used.

**Type:** string

**Since:** 3

**Deprecated since:** 9

**Substitutes:** filename

**System capability:** SystemCapability.MiscServices.Upload

## name

```TypeScript
name?: string
```

Name of a form item when **multipart** is used. The default value is **file**.

**Type:** string

**Since:** 3

**Deprecated since:** 9

**Substitutes:** name

**System capability:** SystemCapability.MiscServices.Upload

## type

```TypeScript
type?: string
```

Type of the file content. By default, the type is obtained based on the extension of the file name or URI.

**Type:** string

**Since:** 3

**Deprecated since:** 9

**Substitutes:** contentType

**System capability:** SystemCapability.MiscServices.Upload

## uri

```TypeScript
uri: string
```

Local path for storing files.

**Type:** string

**Since:** 3

**Deprecated since:** 9

**Substitutes:** path

**System capability:** SystemCapability.MiscServices.Upload
