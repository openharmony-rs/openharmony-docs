# ftruncateSync

## Modules to Import

```TypeScript
```

## ftruncateSync

```TypeScript
declare function ftruncateSync(fd: number, len?: number): void
```

Truncates a file based on the file descriptor. This API returns the result synchronously.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [truncateSync](arkts-corefile-file-fs-truncatesync-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fd | number | Yes | File descriptor of the file to truncate. |
| len | number | No | File length after truncation, in bytes. The default value is **0**. |
