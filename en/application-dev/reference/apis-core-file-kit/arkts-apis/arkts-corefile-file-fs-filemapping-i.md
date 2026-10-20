# FileMapping

```TypeScript
declare interface FileMapping
```

Defines a file mapping object. Before calling the <b>FileMapping</b> method, construct a <b>FileMapping</b> instance using [mmap()](arkts-corefile-file-fs-mmap-f.md) or [mmapSync()](arkts-corefile-file-fs-mmapsync-f.md).

**Since:** 26.0.0

<!--Device-unnamed-declare interface FileMapping--><!--Device-unnamed-declare interface FileMapping-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## capacity

```TypeScript
capacity(): number
```

Obtains the capacity of the file mapping area.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FileMapping-capacity(): number--><!--Device-FileMapping-capacity(): number-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| number | Capacity of the file mapping area, in bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |
| 13900052 | Mmap buffer released |

**Examples**

```TypeScript
let filePath = pathDir + "/test.txt";
let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
let mapping = fileIo.mmapSync(file, fileIo.MappingMode.READ_WRITE, 0, 1024);
let cap = mapping.capacity();
console.info(`Succeeded in getting capacity, the capacity is: ${cap}`);
mapping.unmapSync();
fileIo.closeSync(file);
```

## flip

```TypeScript
flip(): void
```

Flips the file mapping area to switch from the write-ready state to the read-ready state. After this API is called, <b>limit</b> is set to the value of <b>position</b>, and <b>position</b> is reset to <b>0</b>. It is recommended that this API be called to prepare for subsequent [read()](#read) operations after the [write()](#write) operations are complete.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FileMapping-flip(): void--><!--Device-FileMapping-flip(): void-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |
| 13900052 | Mmap buffer released |

**Examples**

```TypeScript
let filePath = pathDir + "/test.txt";
let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
let mapping = fileIo.mmapSync(file, fileIo.MappingMode.READ_WRITE, 0, 1024);

let writeData = new ArrayBuffer(50);
mapping.write(writeData);
mapping.flip(); // limit=50, position=0
console.info("Succeeded in flip.");

let readBuffer = new ArrayBuffer(50);
mapping.read(readBuffer);

mapping.unmapSync();
fileIo.closeSync(file);
```

## getLimit

```TypeScript
getLimit(): number
```

Obtains the upper bound of the readable and writable area of the file mapping area.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FileMapping-getLimit(): number--><!--Device-FileMapping-getLimit(): number-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| number | Upper bound of the current readable and writable area, in bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |
| 13900052 | Mmap buffer released |

**Examples**

```TypeScript
let filePath = pathDir + "/test.txt";
let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
let mapping = fileIo.mmapSync(file, fileIo.MappingMode.READ_WRITE, 0, 1024);
let lim = mapping.getLimit();
console.info(`Succeeded in getting limit, the limit is: ${lim}`);
mapping.unmapSync();
fileIo.closeSync(file);
```

## getPosition

```TypeScript
getPosition(): number
```

Gets the current location of the file mapping area.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FileMapping-getPosition(): number--><!--Device-FileMapping-getPosition(): number-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| number | Current location of the file mapping area, in bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |
| 13900052 | Mmap buffer released |

**Examples**

```TypeScript
let filePath = pathDir + "/test.txt";
let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
let mapping = fileIo.mmapSync(file, fileIo.MappingMode.READ_WRITE, 0, 1024);
let pos = mapping.getPosition();
console.info(`Succeeded in getting position, the position is: ${pos}`);
mapping.unmapSync();
fileIo.closeSync(file);
```

## msync

```TypeScript
msync(): Promise<void>
```

Synchronizes data of the entire file mapping area to the disk file. This API uses a promise to return the result. Note: If the file is not stored on the local device, calling this API does not ensure that all changes are stored persistently.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FileMapping-msync(): Promise<void>--><!--Device-FileMapping-msync(): Promise<void>-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900011 | Out of memory |
| 13900014 | Device or resource busy |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |
| 13900052 | Mmap buffer released |
| 13900055 | Mmap operation not supported |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let filePath = pathDir + "/test.txt";
let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
let mapping = fileIo.mmapSync(file, fileIo.MappingMode.READ_WRITE, 0, 1024);

let buffer = new ArrayBuffer(11);
mapping.write(buffer);

mapping.msync().then(() => {
  console.info("Succeeded in msync.");
}).catch((err: BusinessError) => {
  console.error(`Failed to msync. Code: ${err.code}, message: ${err.message}`);
}).finally(() => {
  mapping.unmapSync();
  fileIo.closeSync(file);
});
```

## msync

```TypeScript
msync(position: number, length: number): Promise<void>
```

Synchronizes data in the specified range of the file mapping area to the disk file. This API uses a promise to return the result. Note: If the file is not stored on the local device, calling this API does not ensure that all changes are stored persistently.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FileMapping-msync(position: number, length: number): Promise<void>--><!--Device-FileMapping-msync(position: number, length: number): Promise<void>-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| position | number | Yes | Start position to synchronize, in bytes. |
| length | number | Yes | Length of the data to be synchronized, in bytes. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900011 | Out of memory |
| 13900014 | Device or resource busy |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |
| 13900052 | Mmap buffer released |
| 13900055 | Mmap operation not supported |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let filePath = pathDir + "/test.txt";
let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
let mapping = fileIo.mmapSync(file, fileIo.MappingMode.READ_WRITE, 0, 1024);

let buffer = new ArrayBuffer(11);
mapping.write(50, buffer);

mapping.msync(50, buffer.byteLength).then(() => {
  console.info("Succeeded in msync.");
}).catch((err: BusinessError) => {
  console.error(`Failed to msync. Code: ${err.code}, message: ${err.message}`);
}).finally(() => {
  mapping.unmapSync();
  fileIo.closeSync(file);
});
```

## msyncSync

```TypeScript
msyncSync(): void
```

Synchronizes data of the entire file mapping area to the disk file synchronously. Note: If the file is not stored on the local device, calling this API does not ensure that all changes are stored persistently.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FileMapping-msyncSync(): void--><!--Device-FileMapping-msyncSync(): void-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900011 | Out of memory |
| 13900014 | Device or resource busy |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |
| 13900052 | Mmap buffer released |
| 13900055 | Mmap operation not supported |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let filePath = pathDir + "/test.txt";
let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
let mapping = fileIo.mmapSync(file, fileIo.MappingMode.READ_WRITE, 0, 1024);

let buffer = new ArrayBuffer(11);
mapping.write(buffer);

mapping.msyncSync();
console.info("Succeeded in msync.");

mapping.unmapSync();
fileIo.closeSync(file);
```

## msyncSync

```TypeScript
msyncSync(position: number, length: number): void
```

Synchronizes data in the specified range of the file mapping area to the disk file synchronously. Note: If the file is not stored on the local device, calling this API does not ensure that all changes are stored persistently.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FileMapping-msyncSync(position: number, length: number): void--><!--Device-FileMapping-msyncSync(position: number, length: number): void-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| position | number | Yes | Start position to synchronize, in bytes. |
| length | number | Yes | Length of the data to be synchronized, in bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900011 | Out of memory |
| 13900014 | Device or resource busy |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |
| 13900052 | Mmap buffer released |
| 13900055 | Mmap operation not supported |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let filePath = pathDir + "/test.txt";
let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
let mapping = fileIo.mmapSync(file, fileIo.MappingMode.READ_WRITE, 0, 1024);

let buffer = new ArrayBuffer(11);
mapping.write(50, buffer);

mapping.msyncSync(50, buffer.byteLength);
console.info("Succeeded in msync.");

mapping.unmapSync();
fileIo.closeSync(file);
```

## read

```TypeScript
read(buffer: ArrayBuffer, length?: number): number
```

Reads data from the current position and moves the position backward by the number of bytes actually read.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FileMapping-read(buffer: ArrayBuffer, length?: number): number--><!--Device-FileMapping-read(buffer: ArrayBuffer, length?: number): number-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buffer | ArrayBuffer | Yes | Buffer for storing the read file data. |
| length | number | No | Length of the data to be read, in bytes. The default value is the buffer length. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Length of the data read, in bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |
| 13900051 | Buffer read/write out of bounds |
| 13900052 | Mmap buffer released |
| 13900054 | Mmap buffer is inaccessible |

**Examples**

```TypeScript
let filePath = pathDir + "/test.txt";
let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
let mapping = fileIo.mmapSync(file, fileIo.MappingMode.READ_WRITE, 0, 1024);

let buffer = new ArrayBuffer(100);
let bytesRead = mapping.read(buffer);
console.info(`Succeeded in reading data, size is: ${bytesRead}`);

mapping.unmapSync();
fileIo.closeSync(file);
```

## read

```TypeScript
read(position: number, buffer: ArrayBuffer, length?: number): number
```

Reads data from the specified position. The current position does not move.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FileMapping-read(position: number, buffer: ArrayBuffer, length?: number): number--><!--Device-FileMapping-read(position: number, buffer: ArrayBuffer, length?: number): number-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| position | number | Yes | Start position to read the data, in bytes. |
| buffer | ArrayBuffer | Yes | Buffer for storing the read file data. |
| length | number | No | Length of the data to be read, in bytes. The default value is the buffer length. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Length of the data read, in bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |
| 13900051 | Buffer read/write out of bounds |
| 13900052 | Mmap buffer released |
| 13900054 | Mmap buffer is inaccessible |

**Examples**

```TypeScript
let filePath = pathDir + "/test.txt";
let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
let mapping = fileIo.mmapSync(file, fileIo.MappingMode.READ_WRITE, 0, 1024);

let buffer = new ArrayBuffer(100);
let bytesRead = mapping.read(50, buffer, 50);
console.info(`Succeeded in reading data, size is: ${bytesRead}`);

mapping.unmapSync();
fileIo.closeSync(file);
```

## remaining

```TypeScript
remaining(): number
```

Obtains the number of remaining bytes between the current position (<b>position</b>) and the upper bound (<b>limit</b>) of the readable and writable area.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FileMapping-remaining(): number--><!--Device-FileMapping-remaining(): number-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of remaining readable or writable bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |
| 13900052 | Mmap buffer released |

**Examples**

```TypeScript
let filePath = pathDir + "/test.txt";
let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
let mapping = fileIo.mmapSync(file, fileIo.MappingMode.READ_WRITE, 0, 1024);

mapping.setPosition(100);
let remaining = mapping.remaining();
console.info(`Succeeded in getting remaining, the remaining is: ${remaining}`);

mapping.unmapSync();
fileIo.closeSync(file);
```

## setLimit

```TypeScript
setLimit(limit: number): void
```

Sets the upper bound of the readable and writable area of the file mapping area.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FileMapping-setLimit(limit: number): void--><!--Device-FileMapping-setLimit(limit: number): void-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| limit | number | Yes | Upper bound of the readable and writable area to be set, in bytes. The value is greater than or equal to 0 and less than or equal to the value of [capacity](#capacity). If the value of <b>limit</b> is smaller than that of <b>position</b> in the file mapping area, the value of <b>position</b> is automatically adjusted to that of <b>limit</b>. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |
| 13900052 | Mmap buffer released |

**Examples**

```TypeScript
let filePath = pathDir + "/test.txt";
let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
let mapping = fileIo.mmapSync(file, fileIo.MappingMode.READ_WRITE, 0, 1024);
mapping.setLimit(512);
console.info("Succeeded in setLimit.");
mapping.unmapSync();
fileIo.closeSync(file);
```

## setPosition

```TypeScript
setPosition(position: number): void
```

Sets the current location of the file mapping area.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FileMapping-setPosition(position: number): void--><!--Device-FileMapping-setPosition(position: number): void-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| position | number | Yes | Target position to set, in bytes. The value must be a non-negative number and cannot be greater than the upper bound (<b>limit</b>) of the readable and writable area. You can obtain the value of <b>limit</b> by calling [getLimit()](#getlimit). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |
| 13900052 | Mmap buffer released |

**Examples**

```TypeScript
let filePath = pathDir + "/test.txt";
let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
let mapping = fileIo.mmapSync(file, fileIo.MappingMode.READ_WRITE, 0, 1024);
mapping.setPosition(100);
console.info("Succeeded in setPosition.");
mapping.unmapSync();
fileIo.closeSync(file);
```

## unmap

```TypeScript
unmap(): Promise<void>
```

Releases the file mapping area. This API uses a promise to return the result. After this API is called, <b>position</b>, <b>limit</b>, and <b>capacity</b> are all reset to <b>0</b>, and no operation can be performed on the <b>FileMapping</b> object.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FileMapping-unmap(): Promise<void>--><!--Device-FileMapping-unmap(): Promise<void>-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let filePath = pathDir + "/test.txt";
let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
let mapping = fileIo.mmapSync(file, fileIo.MappingMode.READ_WRITE, 0, 1024);

let buffer = new ArrayBuffer(11);
mapping.write(buffer);
mapping.unmap().then(() => {
  console.info("Succeeded in unmap.");
}).catch((err: BusinessError) => {
  console.error(`Failed to unmap. Code: ${err.code}, message: ${err.message}`);
}).finally(() => {
  fileIo.closeSync(file);
});
```

## unmapSync

```TypeScript
unmapSync(): void
```

Releases the file mapping area synchronously. After this API is called, <b>position</b>, <b>limit</b>, and <b>capacity</b> are all reset to <b>0</b>, and no operation can be performed on the <b>FileMapping</b> object.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FileMapping-unmapSync(): void--><!--Device-FileMapping-unmapSync(): void-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let filePath = pathDir + "/test.txt";
let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
let mapping = fileIo.mmapSync(file, fileIo.MappingMode.READ_WRITE, 0, 1024);

mapping.unmapSync();
console.info("Succeeded in unmap.");
fileIo.closeSync(file);
```

## write

```TypeScript
write(data: ArrayBuffer, length?: number): number
```

Writes data from the current position and moves the position backward by the number of bytes actually written.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FileMapping-write(data: ArrayBuffer, length?: number): number--><!--Device-FileMapping-write(data: ArrayBuffer, length?: number): number-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | ArrayBuffer | Yes | Buffer data to be written to the file. |
| length | number | No | Length of the data to be written, in bytes. The default value is the buffer length. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Length of the data written, in bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |
| 13900051 | Buffer read/write out of bounds |
| 13900052 | Mmap buffer released |
| 13900053 | Read-only mmap buffer |
| 13900054 | Mmap buffer is inaccessible |

**Examples**

```TypeScript
let filePath = pathDir + "/test.txt";
let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
let mapping = fileIo.mmapSync(file, fileIo.MappingMode.READ_WRITE, 0, 1024);

let buffer = new ArrayBuffer(11);
let bytesWritten = mapping.write(buffer);
console.info(`Succeeded in writing data to file, size is: ${bytesWritten}`);

mapping.msyncSync();
mapping.unmapSync();
fileIo.closeSync(file);
```

## write

```TypeScript
write(position: number, data: ArrayBuffer, length?: number): number
```

Writes data to the specified position. The current position does not move.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FileMapping-write(position: number, data: ArrayBuffer, length?: number): number--><!--Device-FileMapping-write(position: number, data: ArrayBuffer, length?: number): number-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| position | number | Yes | Position to write data in the file, in bytes. |
| data | ArrayBuffer | Yes | Buffer data to be written to the file. |
| length | number | No | Length of the data to be written, in bytes. This parameter is optional. The default value is the buffer length. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Length of the data written, in bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |
| 13900051 | Buffer read/write out of bounds |
| 13900052 | Mmap buffer released |
| 13900053 | Read-only mmap buffer |
| 13900054 | Mmap buffer is inaccessible |

**Examples**

```TypeScript
let filePath = pathDir + "/test.txt";
let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
let mapping = fileIo.mmapSync(file, fileIo.MappingMode.READ_WRITE, 0, 1024);

let buffer = new ArrayBuffer(11);
let bytesWritten = mapping.write(50, buffer);
console.info(`Succeeded in writing data to file, size is: ${bytesWritten}`);

mapping.msyncSync();
mapping.unmapSync();
fileIo.closeSync(file);
```
