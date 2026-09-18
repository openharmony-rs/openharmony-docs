# chownSync

## Modules to Import

```TypeScript
```

## chownSync

```TypeScript
declare function chownSync(path: string, uid: number, gid: number): void
```

Changes the file owner based on its path. This API returns the result synchronously.

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Application sandbox path of the file. |
| uid | number | Yes | New UID. |
| gid | number | Yes | New GID. |
