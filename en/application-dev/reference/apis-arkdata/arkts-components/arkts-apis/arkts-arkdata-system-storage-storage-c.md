# Storage

```TypeScript
export default class Storage
```

**Since:** 3

**Deprecated since:** 6

<!--Device-unnamed-export default class Storage--><!--Device-unnamed-export default class Storage-End-->

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core.Lite

## Modules to Import

```TypeScript
```

## clear

```TypeScript
static clear(options?: ClearStorageOptions): void
```

Clears the stored content.

**Since:** 3

**Deprecated since:** 6

**Substitutes:** clear

**Model restriction:** This API can be used only in the FA model.

<!--Device-Storage-static clear(options?: ClearStorageOptions): void--><!--Device-Storage-static clear(options?: ClearStorageOptions): void-End-->

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ClearStorageOptions](arkts-arkdata-system-storage-clearstorageoptions-i.md) | No | Indicates the target options. |

## delete

```TypeScript
static delete(options: DeleteStorageOptions): void
```

Deletes the stored content.

**Since:** 3

**Deprecated since:** 6

**Substitutes:** delete

**Model restriction:** This API can be used only in the FA model.

<!--Device-Storage-static delete(options: DeleteStorageOptions): void--><!--Device-Storage-static delete(options: DeleteStorageOptions): void-End-->

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [DeleteStorageOptions](arkts-arkdata-system-storage-deletestorageoptions-i.md) | Yes | Indicates the target options. |

## get

```TypeScript
static get(options: GetStorageOptions): void
```

Reads the stored content.

**Since:** 3

**Deprecated since:** 6

**Substitutes:** get

**Model restriction:** This API can be used only in the FA model.

<!--Device-Storage-static get(options: GetStorageOptions): void--><!--Device-Storage-static get(options: GetStorageOptions): void-End-->

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [GetStorageOptions](arkts-arkdata-system-storage-getstorageoptions-i.md) | Yes | Indicates the target options. |

## set

```TypeScript
static set(options: SetStorageOptions): void
```

Modifies the stored content.

**Since:** 3

**Deprecated since:** 6

**Model restriction:** This API can be used only in the FA model.

<!--Device-Storage-static set(options: SetStorageOptions): void--><!--Device-Storage-static set(options: SetStorageOptions): void-End-->

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SetStorageOptions](arkts-arkdata-system-storage-setstorageoptions-i.md) | Yes | Indicates the target options. |
