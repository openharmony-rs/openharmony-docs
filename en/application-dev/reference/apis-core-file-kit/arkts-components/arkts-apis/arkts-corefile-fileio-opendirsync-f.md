# opendirSync

## Modules to Import

```TypeScript
```

## opendirSync

```TypeScript
declare function opendirSync(path: string): Dir
```

Opens a directory. This API returns the result synchronously.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [listFileSync](arkts-corefile-file-fs-listfilesync-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Application sandbox path of the directory to open. |

**Return value:**

| Type | Description |
| --- | --- |
| [Dir](arkts-corefile-fileio-dir-depr-i.md) | **Dir** object opened. |
