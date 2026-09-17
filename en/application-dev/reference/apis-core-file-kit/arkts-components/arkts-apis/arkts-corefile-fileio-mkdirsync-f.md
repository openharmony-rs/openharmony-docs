# mkdirSync

## Modules to Import

```TypeScript
```

## mkdirSync

```TypeScript
declare function mkdirSync(path: string, mode?: number): void
```

Creates a directory. This API returns the result synchronously.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [mkdirSync](arkts-corefile-file-fs-mkdirsync-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Application sandbox path of the directory. |
| mode | number | No | Permission on the directory to create. You can specify multiple permissions, separated using a bitwise OR operator (&#124;). The default value is **0o775**.<br>- **0o775**: The owner has the read, write, and execute permissions, and other users have the read and execute permissions.<br>- **0o700**: The owner has the read, write, and execute permissions.<br>- **0o400**: The owner has the read permission.<br>- **0o200**: The owner has the write permission.<br>- **0o100**: The owner has the execute permission.<br>- **0o070**: The user group has the read, write, and execute permissions.<br>- **0o040**: The user group has the read permission.<br>- **0o020**: The user group has the write permission.<br>- **0o010**: The user group has the execute permission.<br>- **0o007**: Other users have the read, write, and execute permissions.<br>- **0o004**: Other users have the read permission.<br>- **0o002**: Other users have the write permission.<br>- **0o001**: Other users have the execute permission. |
