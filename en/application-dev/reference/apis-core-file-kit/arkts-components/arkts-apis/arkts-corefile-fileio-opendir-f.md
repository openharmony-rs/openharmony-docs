# opendir

## Modules to Import

```TypeScript
```

## opendir

```TypeScript
declare function opendir(path: string): Promise<Dir>
```

Opens a directory. This API uses a promise to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [listFile](arkts-corefile-file-fs-listfile-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Application sandbox path of the directory to open. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Dir](arkts-corefile-fileio-dir-depr-i.md)&gt; | Promise that returns the **Dir** object opened. |


## opendir

```TypeScript
declare function opendir(path: string, callback: AsyncCallback<Dir>): void
```

Opens a file directory. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [listFile](arkts-corefile-file-fs-listfile-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Application sandbox path of the directory to open. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Dir](arkts-corefile-fileio-dir-depr-i.md)&gt; | Yes | Callback invoked when the directory is opened asynchronously. |
