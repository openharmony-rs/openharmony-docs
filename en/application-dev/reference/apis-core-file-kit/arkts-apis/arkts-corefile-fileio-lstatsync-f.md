# lstatSync

## Modules to Import

```TypeScript
```

## lstatSync

```TypeScript
declare function lstatSync(path: string): Stat
```

Obtains information about a symbolic link that is used to refer to a file or directory. This API returns the result synchronously.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [lstatSync](arkts-corefile-file-fs-lstatsync-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Application sandbox path of the target file. |

**Return value:**

| Type | Description |
| --- | --- |
| [Stat](arkts-corefile-fileio-stat-depr-i.md) | File information obtained. |
