# FileMapping

```TypeScript
declare interface FileMapping
```

File mapping object. Before invoking the FileMapping method, you need to use the mmap() method (synchronous or asynchronous) to construct a FileMapping instance.

**Since:** 26.0.0

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

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| number | Size of the file mapping area, in bytes. |

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

Mode reversal. That is, the limit attribute is set to the current position, and then the current position is set to 0.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

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

Synchronizes the dirty page data in the entire file mapping area to the disk file and uses the promise asynchronous callback function. Note: If the file is not stored on the local device, calling this API does not ensure that all changes are stored persistently.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise object. No return value. |

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

<a id="msync-1"></a>

## msync

```TypeScript
msync(position: number, length: number): Promise<void>
```

Synchronizes the dirty page data in the specified range of the file mapping area to the disk file and uses the promise asynchronous callback function. Note: If the file is not stored on the local device, calling this API does not ensure that all changes are stored persistently.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| position | number | Yes | Start position to synchronize from, in bytes. |
| length | number | Yes | Length of the data to be synchronized, in bytes. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise object. No return value. |

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

Synchronizes the dirty page data of the entire file mapping area to the disk file by using the synchronization method. Note: If the file is not stored on the local device, calling this API does not ensure that all changes are stored persistently.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

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

<a id="msyncsync-1"></a>

## msyncSync

```TypeScript
msyncSync(position: number, length: number): void
```

Synchronize the dirty page data in the specified range of the file mapping area to the disk file by using the synchronization method. Note: If the file is not stored on the local device, calling this API does not ensure that all changes are stored persistently.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| position | number | Yes | Start position to synchronize from, in bytes. |
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

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buffer | ArrayBuffer | Yes | Buffer for storing the read file data. |
| length | number | No | Length of the data to be read, in bytes. This parameter is optional. The default value is the buffer length. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Length of the actually read data, in bytes. |

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

<a id="read-1"></a>

## read

```TypeScript
read(position: number, buffer: ArrayBuffer, length?: number): number
```

Reads data from the specified location without affecting the current location.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| position | number | Yes | Start position to read from. |
| buffer | ArrayBuffer | Yes | Buffer for storing the read file data. |
| length | number | No | Length of the data to be read, in bytes. This parameter is optional. The default value is the buffer length. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Length of the actually read data, in bytes. |

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

Obtains the number of remaining bytes between the current position (position) and the upper bound (limit) of the readable and writable area.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

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

Sets the upper bound of the readable and writable area of the file mapping area. The upper bound does not exceed the total capacity of the mapping area (0 &lt;= limit &lt;= capacity).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| limit | number | Yes | Upper bound of the readable and writable area to be set, in bytes. If the current position is greater than the new upper bound, the value is automatically adjusted to limit. |

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

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| position | number | Yes | Target location, in bytes. The value must be a non-negative number and cannot be greater than the current upper bound (limit). |

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

Releases the file mapping area and use the promise asynchronous callback function.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise object. No return value. |

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

Releases the file mapping area by using the synchronization method.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

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

Writes data from the current location and moves the location backward by the number of bytes actually written.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | ArrayBuffer | Yes | Buffer data to be written to the file. |
| length | number | No | Length of the data to be written, in bytes. This parameter is optional. The default value is the buffer length. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Length of the data written. |

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

<a id="write-1"></a>

## write

```TypeScript
write(position: number, data: ArrayBuffer, length?: number): number
```

Writes data from the specified location without affecting the current location.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| position | number | Yes | Start position of the expected write. |
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
