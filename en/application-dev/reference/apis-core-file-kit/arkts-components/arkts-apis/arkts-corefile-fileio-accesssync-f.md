# accessSync

## Modules to Import

```TypeScript
```

## accessSync

```TypeScript
declare function accessSync(path: string, mode?: number): void
```

Checks whether this process can access a file. This API returns the result synchronously.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [accessSync](arkts-corefile-file-fs-accesssync-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Application sandbox path of the file. |
| mode | number | No | Options for accessing the file. You can specify multiple options, separated with a bitwise OR operator (&#124;). The default value is **0**.<br>The options are as follows:<br>- **0**: Check whether the file exists.<br>- **1**: Check whether the process has the execute permission on the file.<br>- **2**: Check whether the process has the write permission on the file.<br>- **4**: Check whether the process has the read permission on the file. |
