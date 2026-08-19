# FileMapping

文件映射对象，在调用FileMapping的方法前，需要先通过[mmap()](arkts-corefile-file-fs-mmap-f.md)或方法[mmapSync()](arkts-corefile-file-fs-mmapsync-f.md)构建一个FileMapping实例。

**起始版本：** 26.0.0

<!--Device-unnamed-declare interface FileMapping--><!--Device-unnamed-declare interface FileMapping-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
import { fileIo } from '@kit.CoreFileKit'
import { ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, TaskSignal } from '@kit.CoreFileKit';
```

## capacity

```TypeScript
capacity(): number
```

获取文件映射区的容量。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-capacity(): number--><!--Device-FileMapping-capacity(): number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 文件映射区的容量，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900052 | Mmap buffer released |
| 13900050 | Internal resource error |

**示例**

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

翻转文件映射区，将写入准备状态切换为读取准备状态。调用后，limit被设置为当前position的值，position被重置为0。 推荐在一系列[write()](#write)操作完成后，调用此方法准备后续的[read()](#read)操作。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-flip(): void--><!--Device-FileMapping-flip(): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900052 | Mmap buffer released |
| 13900050 | Internal resource error |

**示例**

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

获取文件映射区可读写区域的上界。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-getLimit(): number--><!--Device-FileMapping-getLimit(): number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前可读写区域上界值，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900052 | Mmap buffer released |
| 13900050 | Internal resource error |

**示例**

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

获取文件映射区的当前位置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-getPosition(): number--><!--Device-FileMapping-getPosition(): number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 文件映射区的当前位置，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900052 | Mmap buffer released |
| 13900050 | Internal resource error |

**示例**

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

将整个文件映射区的数据同步到磁盘文件。使用Promise异步回调。 注意：如果文件不在本地设备上，调用此接口不保证所有更改都已持久化存储。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-msync(): Promise<void>--><!--Device-FileMapping-msync(): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900052 | Mmap buffer released |
| 13900055 | Mmap operation not supported |
| 13900050 | Internal resource error |
| 13900014 | Device or resource busy |
| 13900011 | Out of memory |

**示例**

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let filePath = pathDir + "/test.txt";
let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
let mapping = fileIo.mmapSync(file, fileIo.MappingMode.READ_WRITE, 0, 1024);

let buffer = new ArrayBuffer(11);
mapping.write(buffer);

mapping.msync().then(() => {
  console.info("Succeeded in msync.");
}).catch((error: Error) => {
  let err: BusinessError = error as BusinessError;
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

将文件映射区指定范围内的数据同步到磁盘文件。使用Promise异步回调。 注意：如果文件不在本地设备上，调用此接口不保证所有更改都已持久化存储。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-msync(position: number, length: number): Promise<void>--><!--Device-FileMapping-msync(position: number, length: number): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | number | 是 | 期望同步的起始位置，单位为Byte。 |
| length | number | 是 | 期望同步的数据长度，单位为Byte。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900052 | Mmap buffer released |
| 13900055 | Mmap operation not supported |
| 13900050 | Internal resource error |
| 13900014 | Device or resource busy |
| 13900011 | Out of memory |

**示例**

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let filePath = pathDir + "/test.txt";
let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
let mapping = fileIo.mmapSync(file, fileIo.MappingMode.READ_WRITE, 0, 1024);

let buffer = new ArrayBuffer(11);
mapping.write(50, buffer);

mapping.msync(50, buffer.byteLength).then(() => {
  console.info("Succeeded in msync.");
}).catch((error: Error) => {
  let err: BusinessError = error as BusinessError;
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

以同步方法将整个文件映射区的数据同步到磁盘文件。 注意：如果文件不在本地设备上，调用此接口不保证所有更改都已持久化存储。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-msyncSync(): void--><!--Device-FileMapping-msyncSync(): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900052 | Mmap buffer released |
| 13900055 | Mmap operation not supported |
| 13900050 | Internal resource error |
| 13900014 | Device or resource busy |
| 13900011 | Out of memory |

**示例**

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

以同步方法将文件映射区指定范围内的数据同步到磁盘文件。 注意：如果文件不在本地设备上，调用此接口不保证所有更改都已持久化存储。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-msyncSync(position: number, length: number): void--><!--Device-FileMapping-msyncSync(position: number, length: number): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | number | 是 | 期望同步的起始位置，单位为Byte。 |
| length | number | 是 | 期望同步的数据长度，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900052 | Mmap buffer released |
| 13900055 | Mmap operation not supported |
| 13900050 | Internal resource error |
| 13900014 | Device or resource busy |
| 13900011 | Out of memory |

**示例**

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

从当前位置读取数据，并将位置后移实际读取的字节数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-read(buffer: ArrayBuffer, length?: number): number--><!--Device-FileMapping-read(buffer: ArrayBuffer, length?: number): number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | ArrayBuffer | 是 | 用于保存读取到的文件数据的缓冲区。 |
| length | number | 否 | 期望读取数据的长度，单位为Byte。默认缓冲区长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回实际读取的数据长度，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900052 | Mmap buffer released |
| 13900054 | Mmap buffer is inaccessible |
| 13900050 | Internal resource error |
| 13900051 | Buffer read/write out of bounds |

**示例**

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

从指定位置读取数据，当前位置不会发生移动。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-read(position: number, buffer: ArrayBuffer, length?: number): number--><!--Device-FileMapping-read(position: number, buffer: ArrayBuffer, length?: number): number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | number | 是 | 期望读取的起始位置，单位为Byte。 |
| buffer | ArrayBuffer | 是 | 用于保存读取到的文件数据的缓冲区。 |
| length | number | 否 | 期望读取数据的长度，单位为Byte。默认缓冲区长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回实际读取的数据长度，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900052 | Mmap buffer released |
| 13900054 | Mmap buffer is inaccessible |
| 13900050 | Internal resource error |
| 13900051 | Buffer read/write out of bounds |

**示例**

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

获取从当前位置（position）到可读写区域的上界（limit）之间的剩余字节数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-remaining(): number--><!--Device-FileMapping-remaining(): number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 剩余可读或可写的字节数，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900052 | Mmap buffer released |
| 13900050 | Internal resource error |

**示例**

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

设置文件映射区可读写区域的上界。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-setLimit(limit: number): void--><!--Device-FileMapping-setLimit(limit: number): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| limit | number | 是 | 要设置的可读写区域上界值，单位为Byte。取值需大于等于0，且小于等于当前[capacity](#capacity)。 若所设值小于文件映射区的当前位置，则当前位置将自动调整至该值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900052 | Mmap buffer released |
| 13900050 | Internal resource error |

**示例**

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

设置文件映射区的当前位置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-setPosition(position: number): void--><!--Device-FileMapping-setPosition(position: number): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | number | 是 | 期望设置的目标位置，单位为Byte。必须为非负数且不大于当前可读写上界的limit，可通过[getLimit()](#getlimit)获得可读写上界的limit。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900052 | Mmap buffer released |
| 13900050 | Internal resource error |

**示例**

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

释放文件映射区。使用Promise异步回调。调用后，position、limit和capacity均被重置为0，FileMapping对象不可再进行任何操作。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-unmap(): Promise<void>--><!--Device-FileMapping-unmap(): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |

**示例**

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let filePath = pathDir + "/test.txt";
let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
let mapping = fileIo.mmapSync(file, fileIo.MappingMode.READ_WRITE, 0, 1024);

let buffer = new ArrayBuffer(11);
mapping.write(buffer);
mapping.unmap().then(() => {
  console.info("Succeeded in unmap.");
}).catch((error: Error) => {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to unmap. Code: ${err.code}, message: ${err.message}`);
}).finally(() => {
  fileIo.closeSync(file);
});
```

## unmapSync

```TypeScript
unmapSync(): void
```

以同步方法释放文件映射区。调用后，position、limit和capacity均被重置为0，FileMapping对象不可再进行任何操作。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-unmapSync(): void--><!--Device-FileMapping-unmapSync(): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |

**示例**

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

从当前位置写入数据，并将位置后移实际写入的字节数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-write(data: ArrayBuffer, length?: number): number--><!--Device-FileMapping-write(data: ArrayBuffer, length?: number): number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | ArrayBuffer | 是 | 待写入文件的缓冲区数据。 |
| length | number | 否 | 期望写入数据的长度，单位为Byte。默认缓冲区长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回实际写入的长度，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900052 | Mmap buffer released |
| 13900053 | Read-only mmap buffer |
| 13900054 | Mmap buffer is inaccessible |
| 13900050 | Internal resource error |
| 13900051 | Buffer read/write out of bounds |

**示例**

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

从指定位置写入数据，当前位置不会发生移动。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-write(position: number, data: ArrayBuffer, length?: number): number--><!--Device-FileMapping-write(position: number, data: ArrayBuffer, length?: number): number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | number | 是 | 期望写入的起始位置，单位为Byte。 |
| data | ArrayBuffer | 是 | 待写入文件的缓冲区数据。 |
| length | number | 否 | 期望写入数据的长度，单位为Byte。可选，默认缓冲区长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回实际写入的长度，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900052 | Mmap buffer released |
| 13900053 | Read-only mmap buffer |
| 13900054 | Mmap buffer is inaccessible |
| 13900050 | Internal resource error |
| 13900051 | Buffer read/write out of bounds |

**示例**

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

