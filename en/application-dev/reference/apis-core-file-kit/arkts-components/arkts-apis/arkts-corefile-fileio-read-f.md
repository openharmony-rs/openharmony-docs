# read

## Modules to Import

```TypeScript
```

## read

```TypeScript
declare function read(
  fd: number,
  buffer: ArrayBuffer,
  options?: {
    offset?: number;
    length?: number;
    position?: number;
  }
): Promise<ReadOut>
```

Reads data from a file. This API uses a promise to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [read](arkts-corefile-file-fs-read-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fd | number | Yes | File descriptor of the file to read. |
| buffer | ArrayBuffer | Yes | Buffer used to store the file data read. |
| options | {     offset?: number;     length?: number;     position?: number;   } | No | The options are as follows:<br>- **offset** (number): position to store the data read in the buffer relative to the start address of the buffer, in bytes. This parameter is optional. The default value is **0**.<br>- **length** (number): length of the data to read. This parameter is optional. The default value is the buffer length minus the offset, in bytes.<br>- **position** (number): position of the data to read in the file. This parameter is optional. By default, data is read from the current position, in bytes.<br> Constraints: offset + length &lt;= Buffer size |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ReadOut](arkts-corefile-fileio-readout-depr-i.md)&gt; | Promise that returns the data read. |


## read

```TypeScript
declare function read(fd: number, buffer: ArrayBuffer, callback: AsyncCallback<ReadOut>): void
```

Reads data from a file. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [read](arkts-corefile-file-fs-read-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fd | number | Yes | File descriptor of the file to read. |
| buffer | ArrayBuffer | Yes | Buffer used to store the file data read. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ReadOut](arkts-corefile-fileio-readout-depr-i.md)&gt; | Yes | Callback invoked when the data is read asynchronously. |


## read

```TypeScript
declare function read(
  fd: number,
  buffer: ArrayBuffer,
  options: {
    offset?: number;
    length?: number;
    position?: number;
  },
  callback: AsyncCallback<ReadOut>
): void
```

Reads data from a file. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [read](arkts-corefile-file-fs-read-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fd | number | Yes | File descriptor of the file to read. |
| buffer | ArrayBuffer | Yes | Buffer used to store the file data read. |
| options | {     offset?: number;     length?: number;     position?: number;   } | Yes | The options are as follows:<br>- **offset** (number): byte offset from the start of the buffer where the read data is stored. This parameter is optional. The default value is **0**.<br>- **length** (number): length of the data to read, in bytes. This parameter is optional. The default value is the buffer length minus the offset.<br>- **position** (number): position in the file to read from, in bytes. This parameter is optional. By default, data is read from the current position.<br>Constraints: offset + length &lt;= Buffer size |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ReadOut](arkts-corefile-fileio-readout-depr-i.md)&gt; | Yes | Callback invoked when the data is read asynchronously. |
