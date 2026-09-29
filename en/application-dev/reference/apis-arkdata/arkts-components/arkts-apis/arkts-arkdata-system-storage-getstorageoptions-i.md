# GetStorageOptions

```TypeScript
export interface GetStorageOptions
```

@typedef GetStorageOptions

**Since:** 3

**Deprecated since:** 6

<!--Device-unnamed-export interface GetStorageOptions--><!--Device-unnamed-export interface GetStorageOptions-End-->

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core.Lite

## Modules to Import

```TypeScript
```

## complete

```TypeScript
complete?: () => void
```

Called when the execution is completed.

**Since:** 3

**Deprecated since:** 6

**Model restriction:** This API can be used only in the FA model.

<!--Device-GetStorageOptions-complete?: () => void--><!--Device-GetStorageOptions-complete?: () => void-End-->

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

Called when the stored content fails to be read.

**Since:** 3

**Deprecated since:** 6

**Model restriction:** This API can be used only in the FA model.

<!--Device-GetStorageOptions-fail?: (data: string, code: number) => void--><!--Device-GetStorageOptions-fail?: (data: string, code: number) => void-End-->

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes |  |
| code | number | Yes |  |

## success

```TypeScript
success?: (data: any) => void
```

Called when the stored content is read successfully.

**Since:** 3

**Deprecated since:** 6

**Model restriction:** This API can be used only in the FA model.

<!--Device-GetStorageOptions-success?: (data: any) => void--><!--Device-GetStorageOptions-success?: (data: any) => void-End-->

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | any | Yes |  |

## default

```TypeScript
default?: string
```

Default value returned when the key does not exist. If this parameter is not specified, an empty string is returned.

**Type:** string

**Since:** 3

**Deprecated since:** 6

**Model restriction:** This API can be used only in the FA model.

<!--Device-GetStorageOptions-default?: string--><!--Device-GetStorageOptions-default?: string-End-->

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core.Lite

## key

```TypeScript
key: string
```

Content index. the value contains a maximum of 32 characters and cannot contain special characters such as \/"*+,:;&lt;=&gt;?[]|\x7F.

**Type:** string

**Since:** 3

**Deprecated since:** 6

**Model restriction:** This API can be used only in the FA model.

<!--Device-GetStorageOptions-key: string--><!--Device-GetStorageOptions-key: string-End-->

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core.Lite
