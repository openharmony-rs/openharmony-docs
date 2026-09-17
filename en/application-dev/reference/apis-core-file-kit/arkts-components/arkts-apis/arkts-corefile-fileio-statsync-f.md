# statSync

## Modules to Import

```TypeScript
```

## statSync

```TypeScript
declare function statSync(path: string): Stat
```

Obtains file information. This API returns the result synchronously.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [statSync](arkts-corefile-file-fs-statsync-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Application sandbox path of the file. |

**Return value:**

| Type | Description |
| --- | --- |
| [Stat](arkts-corefile-fileio-stat-depr-i.md) | File information obtained. |
