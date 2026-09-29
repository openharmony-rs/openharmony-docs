# FileCopyOption

```TypeScript
export interface FileCopyOption
```

Defines the options used in copy().

**Since:** 3

**Deprecated since:** 10

<!--Device-unnamed-export interface FileCopyOption--><!--Device-unnamed-export interface FileCopyOption-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO.Lite

## Modules to Import

```TypeScript
```

## complete

```TypeScript
complete?: () => void
```

Callback invoked when the API call is complete.

**Since:** 3

**Deprecated since:** 10

<!--Device-FileCopyOption-complete?: () => void--><!--Device-FileCopyOption-complete?: () => void-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

Callback invoked when the API call fails. **data** indicates the error information. **code** indicates the returned error code: **202**: invalid parameter **300**: I/O error **301**: file or directory not found

**Since:** 3

**Deprecated since:** 10

<!--Device-FileCopyOption-fail?: (data: string, code: number) => void--><!--Device-FileCopyOption-fail?: (data: string, code: number) => void-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes |  |
| code | number | Yes |  |

## success

```TypeScript
success?: (uri: string) => void
```

Callback invoked when the API call is successful. This API returns the URI of the destination location.

**Since:** 3

**Deprecated since:** 10

<!--Device-FileCopyOption-success?: (uri: string) => void--><!--Device-FileCopyOption-success?: (uri: string) => void-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes |  |

## dstUri

```TypeScript
dstUri: string
```

URI of the location to which the copy is to be saved. The directory of application resources and URI of the tmp type are not supported. Restricted by the underlying file system of lite wearables, the value must meet the following requirements:
1. The URI cannot contain the following special characters: \"*+,:;&lt;=&gt;?[]|\x7F.
2. The value can contain a maximum of 128 characters.

**Type:** string

**Since:** 3

**Deprecated since:** 10

<!--Device-FileCopyOption-dstUri: string--><!--Device-FileCopyOption-dstUri: string-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO.Lite

## srcUri

```TypeScript
srcUri: string
```

URI of the file to copy. Restricted by the underlying file system of lite wearables, the value must meet the following requirements:
1. The URI cannot contain the following special characters: \"*+,:;&lt;=&gt;?[]|\x7F.
2. The value can contain a maximum of 128 characters.

**Type:** string

**Since:** 3

**Deprecated since:** 10

<!--Device-FileCopyOption-srcUri: string--><!--Device-FileCopyOption-srcUri: string-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO.Lite
