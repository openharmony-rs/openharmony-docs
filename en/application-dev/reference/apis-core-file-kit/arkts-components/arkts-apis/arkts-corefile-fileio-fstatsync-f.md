# fstatSync

## Modules to Import

```TypeScript
```

## fstatSync

```TypeScript
declare function fstatSync(fd: number): Stat
```

Obtains file status based on the file descriptor. This API returns the result synchronously.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [statSync](arkts-corefile-file-fs-statsync-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fd | number | Yes | File descriptor of the file whose status is to be obtained. |

**Return value:**

| Type | Description |
| --- | --- |
| [Stat](arkts-corefile-fileio-stat-depr-i.md) | Detailed file status obtained. |
