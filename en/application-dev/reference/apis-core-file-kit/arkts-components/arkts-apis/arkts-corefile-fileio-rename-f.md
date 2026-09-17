# rename

## Modules to Import

```TypeScript
```

## rename

```TypeScript
declare function rename(oldPath: string, newPath: string): Promise<void>
```

Renames a file. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [rename](arkts-corefile-file-fs-rename-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| oldPath | string | Yes | Application sandbox path of the file to rename. |
| newPath | string | Yes | Application sandbox path of the file renamed. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |


## rename

```TypeScript
declare function rename(oldPath: string, newPath: string, callback: AsyncCallback<void>): void
```

Renames a file. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [rename](arkts-corefile-file-fs-rename-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| oldPath | string | Yes | Application sandbox path of the file to rename. |
| newPath | string | Yes | Application sandbox path of the file renamed. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback invoked when the file is asynchronously renamed. |
