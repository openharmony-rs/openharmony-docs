# copyFileSync

## Modules to Import

```TypeScript
```

## copyFileSync

```TypeScript
declare function copyFileSync(src: string | number, dest: string | number, mode?: number): void
```

Copies a file. This API returns the result synchronously.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [copyFileSync](arkts-corefile-file-fs-copyfilesync-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | string &#124; number | Yes | Path or file descriptor of the source file to copy. |
| dest | string &#124; number | Yes | Path or file descriptor of the destination file. |
| mode | number | No | Option for overwriting the destination file. The default value is **0**, which is the only value supported.<br>**0**: Overwrite the file with the same name completely and truncate the part that is not overwritten. |
