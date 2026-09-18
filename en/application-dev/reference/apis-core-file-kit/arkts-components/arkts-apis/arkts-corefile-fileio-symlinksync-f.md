# symlinkSync

## Modules to Import

```TypeScript
```

## symlinkSync

```TypeScript
declare function symlinkSync(target: string, srcPath: string): void
```

Creates a symbolic link based on the file path. This API returns the result synchronously.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [symlinkSync](arkts-corefile-file-fs-symlinksync-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | string | Yes | Application sandbox path of the target file. |
| srcPath | string | Yes | Application sandbox path of the symbolic link. |
