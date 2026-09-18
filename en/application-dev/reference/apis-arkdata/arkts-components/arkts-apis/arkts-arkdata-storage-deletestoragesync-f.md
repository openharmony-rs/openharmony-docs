# deleteStorageSync

## Modules to Import

```TypeScript
```

## deleteStorageSync

```TypeScript
function deleteStorageSync(path: string): void
```

Deletes the singleton **Storage** instance of a file from the memory, and deletes the specified file, its backup file, and damaged files. After the specified files are deleted, the **Storage** instance cannot be used for data operations. Otherwise, data inconsistency will occur.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** deletePreferences

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Path of the target file. |
