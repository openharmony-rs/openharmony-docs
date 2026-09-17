# copyFile

## Modules to Import

```TypeScript
```

## copyFile

```TypeScript
declare function copyFile(src: string | number, dest: string | number, mode?: number): Promise<void>
```

Copies a file. This API uses a promise to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [copyFile](arkts-corefile-file-fs-copyfile-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | string &#124; number | Yes | Path or file descriptor of the source file to copy. |
| dest | string &#124; number | Yes | Path or file descriptor of the destination file. |
| mode | number | No | Option for overwriting the destination file. The default value is **0**, which is the only value supported.<br>**0**: Overwrite the file with the same name completely and truncate the part that is not overwritten. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |


## copyFile

```TypeScript
declare function copyFile(src: string | number, dest: string | number, callback: AsyncCallback<void>): void
```

Copies a file. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [copyFile](arkts-corefile-file-fs-copyfile-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | string &#124; number | Yes | Path or file descriptor of the source file to copy. |
| dest | string &#124; number | Yes | Path or file descriptor of the destination file. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback invoked when the file is copied asynchronously. |


## copyFile

```TypeScript
declare function copyFile(
  src: string | number,
  dest: string | number,
  mode: number,
  callback: AsyncCallback<void>
): void
```

Copies a file. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [copyFile](arkts-corefile-file-fs-copyfile-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | string &#124; number | Yes | Path or file descriptor of the source file to copy. |
| dest | string &#124; number | Yes | Path or file descriptor of the destination file. |
| mode | number | Yes | Option for overwriting the destination file. The default value is **0**, which is the only value supported.<br>**0**: Overwrite the file with the same name completely and truncate the part that is not overwritten. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback invoked when the file is copied asynchronously. |
