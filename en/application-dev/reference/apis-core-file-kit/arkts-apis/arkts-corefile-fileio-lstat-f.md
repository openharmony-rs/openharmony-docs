# lstat

## Modules to Import

```TypeScript
```

## lstat

```TypeScript
declare function lstat(path: string): Promise<Stat>
```

Obtains information about a symbolic link that is used to refer to a file or directory. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [lstat](arkts-corefile-file-fs-lstat-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Application sandbox path of the target file. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Stat](arkts-corefile-fileio-stat-depr-i.md)&gt; | Promise that returns the symbolic link information obtained. For details, see **stat**. |


## lstat

```TypeScript
declare function lstat(path: string, callback: AsyncCallback<Stat>): void
```

Obtains information about a symbolic link that is used to refer to a file or directory. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [lstat](arkts-corefile-file-fs-lstat-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Application sandbox path of the target file. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Stat](arkts-corefile-fileio-stat-depr-i.md)&gt; | Yes | Callback used to return the symbolic link information obtained. |
