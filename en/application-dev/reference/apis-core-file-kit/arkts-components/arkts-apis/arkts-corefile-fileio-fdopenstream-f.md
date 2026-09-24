# fdopenStream

## Modules to Import

```TypeScript
```

## fdopenStream

```TypeScript
declare function fdopenStream(fd: number, mode: string): Promise<Stream>
```

Opens a stream based on the file descriptor. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [fdopenStream](arkts-corefile-file-fs-fdopenstream-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fd | number | Yes | File descriptor of the target file. |
| mode | string | Yes | **r**: Open a file for reading. The file must exist.<br>- **r+**: Open a file for both reading and writing. The file must exist.<br>- **w**: Open a file for writing. If the file exists, clear its content. If the file does not exist, create a file.<br>- **w+**: Open a file for both reading and writing. If the file exists, clear its content. If the file does not exist, create a file.<br>- **a**: Open a file in append mode for writing at the end of the file. If the file does not exist, create a file. If the file exists, write data to the end of the file (the original content of the file is reserved).<br>- **a+**: Open a file in append mode for reading or updating at the end of the file. If the file does not exist, create a file. If the file exists, write data to the end of the file (the original content of the file is reserved). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Stream](arkts-corefile-fileio-stream-depr-i.md)&gt; | Promise that returns the file stream. |


<a id="fdopenstream-1"></a>

## fdopenStream

```TypeScript
declare function fdopenStream(fd: number, mode: string, callback: AsyncCallback<Stream>): void
```

Opens a stream based on the file descriptor. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [fdopenStream](arkts-corefile-file-fs-fdopenstream-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fd | number | Yes | File descriptor of the target file. |
| mode | string | Yes | **r**: Open a file for reading. The file must exist.<br>- **r+**: Open a file for both reading and writing. The file must exist.<br>- **w**: Open a file for writing. If the file exists, clear its content. If the file does not exist, create a file.<br>- **w+**: Open a file for both reading and writing. If the file exists, clear its content. If the file does not exist, create a file.<br>- **a**: Open a file in append mode for writing at the end of the file. If the file does not exist, create a file. If the file exists, write data to the end of the file (the original content of the file is reserved).<br>- **a+**: Open a file in append mode for reading or updating at the end of the file. If the file does not exist, create a file. If the file exists, write data to the end of the file (the original content of the file is reserved). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Stream](arkts-corefile-fileio-stream-depr-i.md)&gt; | Yes | Callback invoked when the stream is opened asynchronously. |
