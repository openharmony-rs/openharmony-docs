# FileMkdirOption

```TypeScript
export interface FileMkdirOption
```

Defines the options used in mkdir().

**Since:** 3

**Deprecated since:** 10

<!--Device-unnamed-export interface FileMkdirOption--><!--Device-unnamed-export interface FileMkdirOption-End-->

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

<!--Device-FileMkdirOption-complete?: () => void--><!--Device-FileMkdirOption-complete?: () => void-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

Callback invoked when the API call fails. **data** indicates the error information. **code** indicates the returned error code: **202**: invalid parameter **300**: I/O error

**Since:** 3

**Deprecated since:** 10

<!--Device-FileMkdirOption-fail?: (data: string, code: number) => void--><!--Device-FileMkdirOption-fail?: (data: string, code: number) => void-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes |  |
| code | number | Yes |  |

## success

```TypeScript
success?: () => void
```

Callback invoked when the API call is successful.

**Since:** 3

**Deprecated since:** 10

<!--Device-FileMkdirOption-success?: () => void--><!--Device-FileMkdirOption-success?: () => void-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO.Lite

## recursive

```TypeScript
recursive?: boolean
```

Whether to recursively create the upper-level directory of the specified directory. The default value is **false**. The value **true** means to create upper-level directory recursively; the value false means the opposite.

**Type:** boolean

**Since:** 3

**Deprecated since:** 10

<!--Device-FileMkdirOption-recursive?: boolean--><!--Device-FileMkdirOption-recursive?: boolean-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO.Lite

## uri

```TypeScript
uri: string
```

URI of the directory. Restricted by the underlying file system of lite wearables, the value must meet the following requirements:
1. The URI cannot contain the following special characters: \"*+,:;&lt;=&gt;?[]|\x7F.
2. The value can contain a maximum of 128 characters.

**Type:** string

**Since:** 3

**Deprecated since:** 10

<!--Device-FileMkdirOption-uri: string--><!--Device-FileMkdirOption-uri: string-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO.Lite
