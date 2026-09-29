# ClearStorageOptions

```TypeScript
export interface ClearStorageOptions
```

@typedef ClearStorageOptions

**Since:** 3

**Deprecated since:** 6

<!--Device-unnamed-export interface ClearStorageOptions--><!--Device-unnamed-export interface ClearStorageOptions-End-->

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

<!--Device-ClearStorageOptions-complete?: () => void--><!--Device-ClearStorageOptions-complete?: () => void-End-->

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

Called when the stored content fails to be cleared.

**Since:** 3

**Deprecated since:** 6

**Model restriction:** This API can be used only in the FA model.

<!--Device-ClearStorageOptions-fail?: (data: string, code: number) => void--><!--Device-ClearStorageOptions-fail?: (data: string, code: number) => void-End-->

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes |  |
| code | number | Yes |  |

## success

```TypeScript
success?: () => void
```

Called when the stored content is cleared successfully.

**Since:** 3

**Deprecated since:** 6

**Model restriction:** This API can be used only in the FA model.

<!--Device-ClearStorageOptions-success?: () => void--><!--Device-ClearStorageOptions-success?: () => void-End-->

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core.Lite
