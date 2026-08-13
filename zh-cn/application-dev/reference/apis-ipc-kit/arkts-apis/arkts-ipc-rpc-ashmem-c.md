# Ashmem

提供与匿名共享内存对象相关的方法，包括创建、关闭、映射和取消映射Ashmem、从Ashmem读取数据和写入数据、获取Ashmem大小、设置Ashmem保护。 共享内存只适用与本设备内跨进程通信。 - 大数据传输：传输大量数据(如图片、文件)时使用共享内存提升效率。 - 跨进程数据共享：多个进程需要共享访问同一块内存数据。 - 传输效率问题：大数据通过共享内存传输避免序列化开销，提升传输效率。 - 内存复用问题：多进程可共享访问同一内存，避免数据拷贝。 - 提升传输性能：共享内存机制大幅提升大数据传输效率。 - 减少内存占用：避免数据多次拷贝，节省内存资源。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-rpc-class Ashmem--><!--Device-rpc-class Ashmem-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## closeAshmem

```TypeScript
closeAshmem(): void
```

关闭这个Ashmem。 > **说明：** > > 关闭Ashmem对象前需要先解除地址映射。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Ashmem-closeAshmem(): void--><!--Device-Ashmem-closeAshmem(): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let ashmem = rpc.Ashmem.create("ashmem", 1024*1024);
  ashmem.closeAshmem();
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error is ' + error);
}
```

## create

```TypeScript
static create(name: string, size: int): Ashmem
```

静态方法，根据指定的名称和大小创建Ashmem对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Ashmem-static create(name: string, size: int): Ashmem--><!--Device-Ashmem-static create(name: string, size: int): Ashmem-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | Ashmem名称，用于查询Ashmem信息，其长度不能为0。 |
| size | int | 是 | Ashmem的大小，其大小应大于0，以字节为单位。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Ashmem](arkts-ipc-rpc-ashmem-c.md) | 返回创建的Ashmem对象；如果创建失败，返回null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.The Ashmem name passed is empty; 4.The Ashmem size passed is less than or equal to 0. |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let ashmem = rpc.Ashmem.create("ashmem", 1024*1024);
  hilog.info(0x0000, 'testTag', 'create ashmem: ' + ashmem);
  let size = ashmem.getAshmemSize();
  hilog.info(0x0000, 'testTag',  'size is ' + size);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## create

```TypeScript
static create(ashmem: Ashmem): Ashmem
```

静态方法，通过复制现有Ashmem对象的文件描述符(fd)来创建Ashmem对象。两个Ashmem对象指向同一个共享内存区域。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Ashmem-static create(ashmem: Ashmem): Ashmem--><!--Device-Ashmem-static create(ashmem: Ashmem): Ashmem-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ashmem | [Ashmem](arkts-ipc-rpc-ashmem-c.md) | 是 | 已存在的Ashmem对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Ashmem](arkts-ipc-rpc-ashmem-c.md) | 返回创建的Ashmem对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The passed parameter is not an Ashmem object; 3.The ashmem instance for obtaining packaging is empty. |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let ashmem = rpc.Ashmem.create("ashmem", 1024*1024);
  let ashmem2 = rpc.Ashmem.create(ashmem);
  let size = ashmem2.getAshmemSize();
  hilog.info(0x0000, 'testTag', 'size is ' + size);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## createAshmem

```TypeScript
static createAshmem(name: string, size: number): Ashmem
```

静态方法，根据指定的名称和大小创建Ashmem对象。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** create()

<!--Device-Ashmem-static createAshmem(name: string, size: number): Ashmem--><!--Device-Ashmem-static createAshmem(name: string, size: number): Ashmem-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 名称，用于查询Ashmem信息。 |
| size | number | 是 | Ashmem的大小，以字节为单位。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Ashmem](arkts-ipc-rpc-ashmem-c.md) | 返回创建的Ashmem对象；如果创建失败，返回null。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let ashmem = rpc.Ashmem.createAshmem("ashmem", 1024*1024);
  hilog.info(0x0000, 'testTag', 'create ashmem: ' + ashmem);
  let size = ashmem.getAshmemSize();
  hilog.info(0x0000, 'testTag',  'size is ' + size);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## createAshmemFromExisting

```TypeScript
static createAshmemFromExisting(ashmem: Ashmem): Ashmem
```

静态方法，通过复制现有Ashmem对象的文件描述符(fd)来创建Ashmem对象。两个Ashmem对象指向同一个共享内存区域。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** create()

<!--Device-Ashmem-static createAshmemFromExisting(ashmem: Ashmem): Ashmem--><!--Device-Ashmem-static createAshmemFromExisting(ashmem: Ashmem): Ashmem-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ashmem | [Ashmem](arkts-ipc-rpc-ashmem-c.md) | 是 | 已存在的Ashmem对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Ashmem](arkts-ipc-rpc-ashmem-c.md) | 返回创建的Ashmem对象。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let ashmem = rpc.Ashmem.create("ashmem", 1024*1024);
  let ashmem2 = rpc.Ashmem.createAshmemFromExisting(ashmem);
  let size = ashmem2.getAshmemSize();
  hilog.info(0x0000, 'testTag', 'size is ' + size);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error is ' + error);
}
```

## getAshmemSize

```TypeScript
getAshmemSize(): int
```

获取Ashmem对象的内存大小。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Ashmem-getAshmemSize(): int--><!--Device-Ashmem-getAshmemSize(): int-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回Ashmem对象的内存大小。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let ashmem = rpc.Ashmem.create("ashmem", 1024*1024);
  let size = ashmem.getAshmemSize();
  hilog.info(0x0000, 'testTag', ' size is ' + size);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error is ' + error);
}
```

## mapAshmem

```TypeScript
mapAshmem(mapType: number): boolean
```

在此进程的虚拟地址空间上创建共享文件映射，映射区域大小由此Ashmem对象指定。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [mapTypedAshmem](#mapTypedAshmem)(mapType: int)

<!--Device-Ashmem-mapAshmem(mapType: number): boolean--><!--Device-Ashmem-mapAshmem(mapType: number): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mapType | number | 是 | 指定映射的内存区域的保护等级。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：映射成功，false：映射失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let ashmem = rpc.Ashmem.create("ashmem", 1024*1024);
  let mapReadAndWrite = ashmem.mapAshmem(rpc.Ashmem.PROT_READ | rpc.Ashmem.PROT_WRITE);
  hilog.info(0x0000, 'testTag', 'map ashmem result is ' + mapReadAndWrite);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error is ' + error);
}
```

## mapReadAndWriteAshmem

```TypeScript
mapReadAndWriteAshmem(): boolean
```

在此进程虚拟地址空间上创建可读写的共享文件映射。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [mapReadWriteAshmem](#mapReadWriteAshmem)()

<!--Device-Ashmem-mapReadAndWriteAshmem(): boolean--><!--Device-Ashmem-mapReadAndWriteAshmem(): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：映射成功，false：映射失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let ashmem = rpc.Ashmem.create("ashmem", 1024*1024);
  let mapResult = ashmem.mapReadAndWriteAshmem();
  hilog.info(0x0000, 'testTag', 'map ashmem result is ' + mapResult);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error is ' + error);
}
```

## mapReadOnlyAshmem

```TypeScript
mapReadOnlyAshmem(): boolean
```

在此进程虚拟地址空间上创建只读的共享文件映射。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** mapReadonlyAshmem()

<!--Device-Ashmem-mapReadOnlyAshmem(): boolean--><!--Device-Ashmem-mapReadOnlyAshmem(): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：映射成功，false：映射失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let ashmem = rpc.Ashmem.create("ashmem", 1024*1024);
  let mapResult = ashmem.mapReadOnlyAshmem();
  hilog.info(0x0000, 'testTag', 'Ashmem mapReadOnlyAshmem result is ' + mapResult);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error is ' + error);
}
```

## mapReadWriteAshmem

```TypeScript
mapReadWriteAshmem(): void
```

在此进程虚拟地址空间上创建可读写的共享文件映射。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Ashmem-mapReadWriteAshmem(): void--><!--Device-Ashmem-mapReadWriteAshmem(): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900001](../errorcode-rpc.md#1900001-系统调用mmap失败) | Failed to call mmap. |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let ashmem = rpc.Ashmem.create("ashmem", 1024*1024);
  ashmem.mapReadWriteAshmem();
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## mapReadonlyAshmem

```TypeScript
mapReadonlyAshmem(): void
```

在此进程虚拟地址空间上创建只读的共享文件映射。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Ashmem-mapReadonlyAshmem(): void--><!--Device-Ashmem-mapReadonlyAshmem(): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900001](../errorcode-rpc.md#1900001-系统调用mmap失败) | Failed to call mmap. |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let ashmem = rpc.Ashmem.create("ashmem", 1024*1024);
  ashmem.mapReadonlyAshmem();
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## mapTypedAshmem

```TypeScript
mapTypedAshmem(mapType: int): void
```

在此进程的虚拟地址空间上创建共享文件映射，映射区域大小由此Ashmem对象指定。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Ashmem-mapTypedAshmem(mapType: int): void--><!--Device-Ashmem-mapTypedAshmem(mapType: int): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mapType | int | 是 | 指定映射的内存区域的保护等级。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.The passed mapType exceeds the maximum protection level. |
| [1900001](../errorcode-rpc.md#1900001-系统调用mmap失败) | Failed to call mmap. |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let ashmem = rpc.Ashmem.create("ashmem", 1024*1024);
  ashmem.mapTypedAshmem(rpc.Ashmem.PROT_READ | rpc.Ashmem.PROT_WRITE);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readAshmem

```TypeScript
readAshmem(size: number, offset: number): number[]
```

从此Ashmem对象关联的共享文件中读取数据。 > **说明：** > > 对Ashmem对象进行写操作时，需要先调用[mapReadWriteAshmem](#mapReadWriteAshmem)进行映射。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 11

**替代接口：** [readDataFromAshmem](#readDataFromAshmem)(size: int, offset: int)

<!--Device-Ashmem-readAshmem(size: number, offset: number): number[]--><!--Device-Ashmem-readAshmem(size: number, offset: number): number[]-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | number | 是 | 要读取的数据的大小，以字节为单位。 |
| offset | number | 是 | 要读取的数据在此Ashmem对象关联的内存区间的起始位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number[] | 返回读取的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900004](../errorcode-rpc.md#1900004-共享内存读数据失败) | Failed to read data from the shared memory. |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let ashmem = rpc.Ashmem.create("ashmem", 1024*1024);
  ashmem.mapReadWriteAshmem();
  let ByteArrayVar = [1, 2, 3, 4, 5];
  ashmem.writeAshmem(ByteArrayVar, 5, 0);
  let readResult = ashmem.readAshmem(5, 0);
  hilog.info(0x0000, 'testTag', 'read from Ashmem result is ' + readResult);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readDataFromAshmem

```TypeScript
readDataFromAshmem(size: int, offset: int): ArrayBuffer
```

从此Ashmem对象关联的共享文件中读取数据。 > **说明：** > > 对Ashmem对象进行写操作时，需要先调用[mapReadWriteAshmem](#mapReadWriteAshmem)进行映射。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Ashmem-readDataFromAshmem(size: int, offset: int): ArrayBuffer--><!--Device-Ashmem-readDataFromAshmem(size: int, offset: int): ArrayBuffer-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | int | 是 | 要读取的数据的大小，以字节为单位。 |
| offset | int | 是 | 要读取的数据在此Ashmem对象关联的内存区间的起始位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArrayBuffer | 返回读取的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900004](../errorcode-rpc.md#1900004-共享内存读数据失败) | Failed to read data from the shared memory. |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let buffer = new ArrayBuffer(1024);
  let int32View = new Int32Array(buffer);
  for (let i = 0; i < int32View.length; i++) {
    int32View[i] = i * 2 + 1;
  }
  let size = buffer.byteLength;
  let ashmem = rpc.Ashmem.create("ashmem", 1024*1024);
  ashmem.mapReadWriteAshmem();
  ashmem.writeDataToAshmem(buffer, size, 0);
  let readResult = ashmem.readDataFromAshmem(size, 0);
  let readInt32View = new Int32Array(readResult);
  hilog.info(0x0000, 'testTag', 'read from Ashmem result is ' + readInt32View);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readFromAshmem

```TypeScript
readFromAshmem(size: number, offset: number): number[]
```

从此Ashmem对象关联的共享文件中读取数据。 > **说明：** > > 对Ashmem对象进行写操作时，需要先调用[mapReadWriteAshmem](#mapReadWriteAshmem)进行映射。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [readDataFromAshmem](#readDataFromAshmem)(size: int, offset: int)

<!--Device-Ashmem-readFromAshmem(size: number, offset: number): number[]--><!--Device-Ashmem-readFromAshmem(size: number, offset: number): number[]-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | number | 是 | 要读取的数据的大小，以字节为单位。 |
| offset | number | 是 | 要读取的数据在此Ashmem对象关联的内存区间的起始位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number[] | 返回读取的数据。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let ashmem = rpc.Ashmem.create("ashmem", 1024*1024);
  let mapResult = ashmem.mapReadAndWriteAshmem();
  hilog.info(0x0000, 'testTag', 'RpcTest map ashmem result is ' + mapResult);
  let ByteArrayVar = [1, 2, 3, 4, 5];
  let writeResult = ashmem.writeToAshmem(ByteArrayVar, 5, 0);
  hilog.info(0x0000, 'testTag', 'write to Ashmem result is ' + writeResult);
  let readResult = ashmem.readFromAshmem(5, 0);
  hilog.info(0x0000, 'testTag', 'read to Ashmem result is ' + readResult);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error is ' + error);
}
```

## setProtection

```TypeScript
setProtection(protectionType: number): boolean
```

设置映射内存区域的保护等级。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [setProtectionType](#setProtectionType)(protectionType: int)

<!--Device-Ashmem-setProtection(protectionType: number): boolean--><!--Device-Ashmem-setProtection(protectionType: number): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| protectionType | number | 是 | 要设置的保护类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：设置成功，false：设置失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let ashmem = rpc.Ashmem.create("ashmem", 1024*1024);
  let result = ashmem.setProtection(rpc.Ashmem.PROT_READ);
  hilog.info(0x0000, 'testTag', 'Ashmem setProtection result is ' + result);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## setProtectionType

```TypeScript
setProtectionType(protectionType: int): void
```

设置映射内存区域的保护等级。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Ashmem-setProtectionType(protectionType: int): void--><!--Device-Ashmem-setProtectionType(protectionType: int): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| protectionType | int | 是 | 要设置的保护类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900002](../errorcode-rpc.md#1900002-系统调用ioctl失败) | Failed to call ioctl. |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let ashmem = rpc.Ashmem.create("ashmem", 1024*1024);
  ashmem.setProtectionType(rpc.Ashmem.PROT_READ);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'Rpc set protection type fail, errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'Rpc set protection type fail, errorMessage ' + e.message);
}
```

## unmapAshmem

```TypeScript
unmapAshmem(): void
```

删除该Ashmem对象的地址映射。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Ashmem-unmapAshmem(): void--><!--Device-Ashmem-unmapAshmem(): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let ashmem = rpc.Ashmem.create("ashmem", 1024*1024);
  ashmem.unmapAshmem();
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error is ' + error);
}
```

## writeAshmem

```TypeScript
writeAshmem(buf: number[], size: number, offset: number): void
```

将数据写入此Ashmem对象关联的共享文件。 > **说明：** > > 对Ashmem对象进行写操作时，需要先调用[mapReadWriteAshmem](#mapReadWriteAshmem)进行映射。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 11

**替代接口：** [writeDataToAshmem](#writeDataToAshmem)(buf: ArrayBuffer, size: int, offset: int)

<!--Device-Ashmem-writeAshmem(buf: number[], size: number, offset: number): void--><!--Device-Ashmem-writeAshmem(buf: number[], size: number, offset: number): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buf | number[] | 是 | 写入Ashmem对象的数据。 |
| size | number | 是 | 要写入的数据大小，以字节为单位。 |
| offset | number | 是 | 要写入的数据在此Ashmem对象关联的内存区间的起始位置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.The element does not exist in the array. |
| [1900003](../errorcode-rpc.md#1900003-共享内存写数据失败) | Failed to write data to the shared memory. |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let ashmem = rpc.Ashmem.create("ashmem", 1024*1024);
  ashmem.mapReadWriteAshmem();
  let ByteArrayVar = [1, 2, 3, 4, 5];
  ashmem.writeAshmem(ByteArrayVar, 5, 0);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'Rpc write to ashmem fail, errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'Rpc write to ashmem fail, errorMessage ' + e.message);
}
```

## writeDataToAshmem

```TypeScript
writeDataToAshmem(buf: ArrayBuffer, size: int, offset: int): void
```

将数据写入此Ashmem对象关联的共享文件。 > **说明：** > > 对Ashmem对象进行写操作时，需要先调用[mapReadWriteAshmem](#mapReadWriteAshmem)进行映射。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Ashmem-writeDataToAshmem(buf: ArrayBuffer, size: int, offset: int): void--><!--Device-Ashmem-writeDataToAshmem(buf: ArrayBuffer, size: int, offset: int): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buf | ArrayBuffer | 是 | 写入Ashmem对象的数据。 |
| size | int | 是 | 要写入的数据大小，以字节为单位。 |
| offset | int | 是 | 要写入的数据在此Ashmem对象关联的内存区间的起始位置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.Failed to obtain arrayBuffer information. |
| [1900003](../errorcode-rpc.md#1900003-共享内存写数据失败) | Failed to write data to the shared memory. |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let buffer = new ArrayBuffer(1024);
  let int32View = new Int32Array(buffer);
  for (let i = 0; i < int32View.length; i++) {
    int32View[i] = i * 2 + 1;
  }
  let size = buffer.byteLength;
  let ashmem = rpc.Ashmem.create("ashmem", 1024*1024);
  ashmem.mapReadWriteAshmem();
  ashmem.writeDataToAshmem(buffer, size, 0);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## writeToAshmem

```TypeScript
writeToAshmem(buf: number[], size: number, offset: number): boolean
```

将数据写入此Ashmem对象关联的共享文件。 > **说明：** > > 对Ashmem对象进行写操作时，需要先调用[mapReadWriteAshmem](#mapReadWriteAshmem)进行映射。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [writeDataToAshmem](#writeDataToAshmem)(buf: ArrayBuffer, size: int, offset: int)

<!--Device-Ashmem-writeToAshmem(buf: number[], size: number, offset: number): boolean--><!--Device-Ashmem-writeToAshmem(buf: number[], size: number, offset: number): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buf | number[] | 是 | 写入Ashmem对象的数据。 |
| size | number | 是 | 要写入的数据大小，以字节为单位。 |
| offset | number | 是 | 要写入的数据在此Ashmem对象关联的内存区间的起始位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：如果数据写入成功，false：在其他情况下，如数据写入越界或未获得写入权限。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let ashmem = rpc.Ashmem.create("ashmem", 1024*1024);
  let mapResult = ashmem.mapReadAndWriteAshmem();
  hilog.info(0x0000, 'testTag', 'RpcTest map ashmem result is ' + mapResult);
  let ByteArrayVar = [1, 2, 3, 4, 5];
  let writeResult = ashmem.writeToAshmem(ByteArrayVar, 5, 0);
  hilog.info(0x0000, 'testTag', 'write to Ashmem result is ' + writeResult);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error is ' + error);
}
```

## PROT_EXEC

```TypeScript
static readonly PROT_EXEC: number
```

映射内存保护类型，代表映射的内存可执行。

**类型：** number

**默认值：** 4

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

<!--Device-Ashmem-static readonly PROT_EXEC: number--><!--Device-Ashmem-static readonly PROT_EXEC: number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## PROT_NONE

```TypeScript
static readonly PROT_NONE: number
```

映射内存保护类型，代表映射的内存不可访问。

**类型：** number

**默认值：** 0

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

<!--Device-Ashmem-static readonly PROT_NONE: number--><!--Device-Ashmem-static readonly PROT_NONE: number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## PROT_READ

```TypeScript
static readonly PROT_READ: number
```

映射内存保护类型，代表映射的内存可读。

**类型：** number

**默认值：** 1

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

<!--Device-Ashmem-static readonly PROT_READ: number--><!--Device-Ashmem-static readonly PROT_READ: number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## PROT_WRITE

```TypeScript
static readonly PROT_WRITE: number
```

映射内存保护类型，代表映射的内存可写。

**类型：** number

**默认值：** 2

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

<!--Device-Ashmem-static readonly PROT_WRITE: number--><!--Device-Ashmem-static readonly PROT_WRITE: number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

