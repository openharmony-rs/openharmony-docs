# getStorageSync

## Modules to Import

```TypeScript
```

## getStorageSync

```TypeScript
function getStorageSync(path: string): Storage
```

Reads the specified file and loads its data to the **Storage** instance for data operations.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** getPreferences

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Path of the target file. |

**Return value:**

| Type | Description |
| --- | --- |
| [Storage](arkts-arkdata-storage-storage-i.md) | **Storage** instance used for data storage operations. |
