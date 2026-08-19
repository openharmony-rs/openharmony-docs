# MessageSequence

在RPC或IPC过程中，发送方可以使用MessageSequence提供的写方法，将待发送的数据以特定格式写入该对象。接收方可以使用MessageSequence提供的读方法从该对象中读取特定格式的数据。 数据格式包括：基础类型及数组、IPC对象、接口描述符和自定义序列化对象。读取顺序必须与写入顺序一致，否则会导致数据解析错误。

**起始版本：** 23

<!--Device-rpc-class MessageSequence--><!--Device-rpc-class MessageSequence-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## 导入模块

```TypeScript
import { rpc } from '@kit.IPCKit';
```

## closeFileDescriptor

```TypeScript
static closeFileDescriptor(fd: int): void
```

静态方法，关闭给定的文件描述符。 - 文件使用完毕后及时关闭，避免资源泄漏。 - 关闭前确保文件操作已完成。 - 不要关闭已关闭的文件描述符。 - 关闭后不能再读写文件。

**起始版本：** 23

<!--Device-MessageSequence-static closeFileDescriptor(fd: int): void--><!--Device-MessageSequence-static closeFileDescriptor(fd: int): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | int | 是 | 要关闭的文件描述符。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { fileIo } from '@kit.CoreFileKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let filePath = "path/to/file";
  let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
  rpc.MessageSequence.closeFileDescriptor(file.fd);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## containFileDescriptors

```TypeScript
containFileDescriptors(): boolean
```

检查此MessageSequence对象是否包含文件描述符。适用于文件传输场景中判断是否需要处理文件描述符，或在接收数据前检查数据类型以决定处理方式的场景。

**起始版本：** 23

<!--Device-MessageSequence-containFileDescriptors(): boolean--><!--Device-MessageSequence-containFileDescriptors(): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：包含文件描述符，false：不包含文件描述符。 |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { fileIo } from '@kit.CoreFileKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let sequence = rpc.MessageSequence.create();
  let filePath = "path/to/file";
  let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
  let containFD = sequence.containFileDescriptors();
  hilog.info(0x0000, 'testTag', 'sequence after write fd containFd result is ' + containFD);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## create

```TypeScript
static create(): MessageSequence
```

静态方法，创建MessageSequence对象。调用此方法后，系统会在内存中分配一块连续的缓冲区空间，用于存储待传输的序列化数据。该对象在IPC/RPC通信中用于封装请求和响应数据。 - 创建的MessageSequence对象必须在使用完毕后调用reclaim()释放资源，否则会导致内存泄漏。 - MessageSequence对象不能跨线程使用。 - 建议在需要IPC/RPC通信时按需创建，避免频繁创建和释放。

**起始版本：** 23

<!--Device-MessageSequence-static create(): MessageSequence--><!--Device-MessageSequence-static create(): MessageSequence-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MessageSequence](arkts-ipc-rpc-messagesequence-c.md) | 返回创建的MessageSequence对象。 |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  hilog.info(0x0000, 'testTag', 'data is ' + data);

  // 当MessageSequence对象不再使用，由业务主动调用reclaim方法去释放资源。
  data.reclaim();
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## dupFileDescriptor

```TypeScript
static dupFileDescriptor(fd: int): int
```

静态方法，复制给定的文件描述符。 - IPC传输前复制，避免原描述符被关闭。 - 多进程共享同一文件。 - 需要独立管理文件偏移量。 - 复制后两个描述符需要分别关闭。 - 不要复制无效的文件描述符。 - 复制后独立管理生命周期。

**起始版本：** 23

<!--Device-MessageSequence-static dupFileDescriptor(fd: int): int--><!--Device-MessageSequence-static dupFileDescriptor(fd: int): int-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | int | 是 | 表示已存在的文件描述符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回新的文件描述符。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900013](../errorcode-rpc.md#1900013-系统调用dup失败) | Failed to call dup. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { fileIo } from '@kit.CoreFileKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let filePath = "path/to/file";
  let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
  rpc.MessageSequence.dupFileDescriptor(file.fd);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## getCapacity

```TypeScript
getCapacity(): int
```

获取当前MessageSequence对象的容量大小。

**起始版本：** 23

<!--Device-MessageSequence-getCapacity(): int--><!--Device-MessageSequence-getCapacity(): int-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 获取的MessageSequence实例的容量大小。以字节为单位。 |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  let result = data.getCapacity();
  hilog.info(0x0000, 'testTag', 'capacity is ' + result);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## getRawDataCapacity

```TypeScript
getRawDataCapacity(): int
```

获取MessageSequence可以容纳的最大原始数据量。适用于大数据传输前检查容量是否满足需求，或在处理大批量数据时预先判断数据大小的场景。

**起始版本：** 23

<!--Device-MessageSequence-getRawDataCapacity(): int--><!--Device-MessageSequence-getRawDataCapacity(): int-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回MessageSequence可以容纳的最大原始数据量，即128MB。 |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let sequence = rpc.MessageSequence.create();
  let result = sequence.getRawDataCapacity();
  hilog.info(0x0000, 'testTag', 'sequence get RawDataCapacity result is ' + result);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## getReadPosition

```TypeScript
getReadPosition(): int
```

获取MessageSequence的读位置。

**起始版本：** 23

<!--Device-MessageSequence-getReadPosition(): int--><!--Device-MessageSequence-getReadPosition(): int-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回MessageSequence实例中的当前读取位置。 |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeString("hello world");
  let readPos = data.getReadPosition();
  hilog.info(0x0000, 'testTag', 'readPos is ' + readPos);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## getReadableBytes

```TypeScript
getReadableBytes(): int
```

获取MessageSequence的可读字节空间。

**起始版本：** 23

<!--Device-MessageSequence-getReadableBytes(): int--><!--Device-MessageSequence-getReadableBytes(): int-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 获取到的MessageSequence实例的可读字节空间。以字节为单位。 |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeString("hello world");
  let result = data.getReadableBytes();
  hilog.info(0x0000, 'testTag', 'RpcServer: getReadableBytes is ' + result);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## getSize

```TypeScript
getSize(): int
```

获取当前创建的MessageSequence对象的数据大小。 - 查看已写入数据的总大小。 - 判断缓冲区使用情况。 - 在数据传输前检查数据大小。

**起始版本：** 23

<!--Device-MessageSequence-getSize(): int--><!--Device-MessageSequence-getSize(): int-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 获取的MessageSequence实例的数据大小。以字节为单位。用于调整数据读取范围，建议设置为实际写入数据的大小。 |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  let size = data.getSize();
  hilog.info(0x0000, 'testTag', 'size is ' + size);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## getWritableBytes

```TypeScript
getWritableBytes(): int
```

获取MessageSequence的可写字节空间大小。

**起始版本：** 23

<!--Device-MessageSequence-getWritableBytes(): int--><!--Device-MessageSequence-getWritableBytes(): int-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 获取到的MessageSequence实例的可写字节空间。以字节为单位。 |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.setCapacity(100);
  let getWritableBytes = data.getWritableBytes();
  hilog.info(0x0000, 'testTag', 'RpcServer: getWritableBytes is ' + getWritableBytes);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## getWritePosition

```TypeScript
getWritePosition(): int
```

获取MessageSequence的写位置。

**起始版本：** 23

<!--Device-MessageSequence-getWritePosition(): int--><!--Device-MessageSequence-getWritePosition(): int-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回MessageSequence实例中的当前写入位置。 |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeInt(10);
  let bwPos = data.getWritePosition();
  hilog.info(0x0000, 'testTag', 'bwPos is ' + bwPos);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readArrayBuffer

```TypeScript
readArrayBuffer(typeCode: TypeCode): ArrayBuffer
```

从MessageSequence读取ArrayBuffer类型数据。 - 必须与[writeArrayBuffer](#writearraybuffer)配对使用。 - 读取typeCode必须与写入typeCode一致，顺序必须匹配。 - typeCode必须正确匹配，不匹配会导致数据异常或错误，建议根据业务类型选择合适的[TypeCode](arkts-ipc-rpc-typecode-e.md)。

**起始版本：** 23

<!--Device-MessageSequence-readArrayBuffer(typeCode: TypeCode): ArrayBuffer--><!--Device-MessageSequence-readArrayBuffer(typeCode: TypeCode): ArrayBuffer-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| typeCode | [TypeCode](arkts-ipc-rpc-typecode-e.md) | 是 | ArrayBuffer数据具体是以哪一种TypedArray来访问和操作(会根据业务传递的类型枚举值去决定底层的读取方式，需要业务正确传递枚举值， 读写枚举值不匹配会导致数据异常。) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArrayBuffer | 返回ArrayBuffer类型数据，用于存储从MessageSequence读取的二进制数据，可通过TypedArray进行访问和操作。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.The obtained value of typeCode is incorrect; |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
// TypeCode 类型枚举较多，示例代码以Int16Array为例
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  let buffer = new ArrayBuffer(10);
  let int16View = new Int16Array(buffer);
  for (let i = 0; i < int16View.length; i++) {
    int16View[i] = i * 2 + 1;
  }
  data.writeArrayBuffer(buffer, rpc.TypeCode.INT16_ARRAY);
  let result = data.readArrayBuffer(rpc.TypeCode.INT16_ARRAY);
  let readInt16View = new Int16Array(result);
  hilog.info(0x0000, 'testTag', 'read ArrayBuffer result is ' + readInt16View);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readAshmem

```TypeScript
readAshmem(): Ashmem
```

从MessageSequence读取匿名共享对象。使用前需先调用[mapReadWriteAshmem](arkts-ipc-rpc-ashmem-c.md#mapreadwriteashmem)方法进行内存映射。 - readAshmem()获取对象。 - [mapReadWriteAshmem](arkts-ipc-rpc-ashmem-c.md#mapreadwriteashmem)映射内存。 - [readDataFromAshmem](arkts-ipc-rpc-ashmem-c.md#readdatafromashmem)读取数据。 - unmapAshmem()取消映射。 - closeAshmem()关闭对象。 - 必须先映射才能读取数据。 - 数据读取后需要取消映射。 - 及时关闭避免内存泄漏。

**起始版本：** 23

<!--Device-MessageSequence-readAshmem(): Ashmem--><!--Device-MessageSequence-readAshmem(): Ashmem-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Ashmem](arkts-ipc-rpc-ashmem-c.md) | 返回匿名共享对象，用于跨进程共享内存数据。 读取数据前需先调用[mapReadWriteAshmem]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let sequence = rpc.MessageSequence.create();
  let ashmem = rpc.Ashmem.create("ashmem", 1024);
  // ashmem里写入数据
  let buffer = new ArrayBuffer(1024);
  let int32View = new Int32Array(buffer);
  for (let i = 0; i < int32View.length; i++) {
    int32View[i] = i * 2 + 1;
  }
  let size = buffer.byteLength;
  ashmem.mapReadWriteAshmem();
  ashmem.writeDataToAshmem(buffer, size, 0);
  // 将传递的数据大小写入messageSequence对象中
  sequence.writeInt(size);
  // 将ashmem对象写入messageSequence对象中
  sequence.writeAshmem(ashmem);

  // 读取传递的数据大小
  let dataSize = sequence.readInt();
  // 从messageSequence对象中读取ashmem对象
  let ashmem1 = sequence.readAshmem();
  // 从ashmem对象中读取数据
  ashmem1.mapReadWriteAshmem();
  let readResult = ashmem1.readDataFromAshmem(dataSize, 0);
  let readInt32View = new Int32Array(readResult);
  hilog.info(0x0000, 'testTag', 'read from Ashmem result is ' + readInt32View);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readBoolean

```TypeScript
readBoolean(): boolean
```

从MessageSequence实例中读取布尔值。

**起始版本：** 23

<!--Device-MessageSequence-readBoolean(): boolean--><!--Device-MessageSequence-readBoolean(): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回读取到的布尔值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeBoolean(false);
  let ret = data.readBoolean();
  hilog.info(0x0000, 'testTag', 'readBoolean is ' + ret);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readBooleanArray

```TypeScript
readBooleanArray(dataIn: boolean[]): void
```

从MessageSequence实例中读取布尔数组，并将其写入到创建的空数组中。

**起始版本：** 23

<!--Device-MessageSequence-readBooleanArray(dataIn: boolean[]): void--><!--Device-MessageSequence-readBooleanArray(dataIn: boolean[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataIn | boolean[] | 是 | 用于存储从MessageSequence读取的布尔数组，需预先创建空数组且长度应与写入时的数组长度一致。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match. |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeBooleanArray([false, true, false]);
  let array: Array<boolean> = new Array(3);
  data.readBooleanArray(array);
  hilog.info(0x0000, 'testTag', 'readBooleanArray is ' + array);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readBooleanArray

```TypeScript
readBooleanArray(): boolean[]
```

从MessageSequence实例中读取布尔数组。 - 返回新创建的数组，无需预先创建。 - 数组元素为布尔值。

**起始版本：** 23

<!--Device-MessageSequence-readBooleanArray(): boolean[]--><!--Device-MessageSequence-readBooleanArray(): boolean[]-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean[] | 返回布尔数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeBooleanArray([false, true, false]);
  let array = data.readBooleanArray();
  hilog.info(0x0000, 'testTag', 'readBooleanArray is ' + array);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readByte

```TypeScript
readByte(): int
```

从MessageSequence实例中读取字节值。 - 必须与[writeByte](#writebyte)配对使用。 - 一次写入对应一次读取。

**起始版本：** 23

<!--Device-MessageSequence-readByte(): int--><!--Device-MessageSequence-readByte(): int-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回字节值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeByte(2);
  let ret = data.readByte();
  hilog.info(0x0000, 'testTag', 'readByte is: ' +  ret);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readByteArray

```TypeScript
readByteArray(dataIn: int[]): void
```

从MessageSequence实例中读取字节数组，并将其写入到创建的空数组中。读取后dataIn数组会被填充读取的字节数据，读指针向后移动相应字节数。

**起始版本：** 23

<!--Device-MessageSequence-readByteArray(dataIn: int[]): void--><!--Device-MessageSequence-readByteArray(dataIn: int[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataIn | int[] | 是 | 用于存储从MessageSequence读取的字节数组，需预先创建空数组且长度应与写入时的数组长度一致。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match. |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  let ByteArrayVar = [1, 2, 3, 4, 5];
  data.writeByteArray(ByteArrayVar);
  let array: Array<number> = new Array(5);
  data.readByteArray(array);
  hilog.info(0x0000, 'testTag', 'readByteArray is  ' + array);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

ArkTS-Sta示例：

```TypeScript
import rpc from '@ohos.rpc';
import hilog from 'ohos.hilog';
import { BusinessError } from '@ohos.base';

try {
  let data = rpc.MessageSequence.create();
  let ByteArrayVar = [1, 2, 3, 4, 5];
  data.writeByteArray(ByteArrayVar);
  let array: Array<int> = new Array<int>(5);
  data.readByteArray(array);
  hilog.info(0x0000, 'testTag', 'readByteArray is  ' + array);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readByteArray

```TypeScript
readByteArray(): int[]
```

从MessageSequence实例中读取字节数组。读取后返回字节数组数据，读指针向后移动相应字节数。

**起始版本：** 23

<!--Device-MessageSequence-readByteArray(): int[]--><!--Device-MessageSequence-readByteArray(): int[]-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int[] | 返回字节数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  let ByteArrayVar = [1, 2, 3, 4, 5];
  data.writeByteArray(ByteArrayVar);
  let array = data.readByteArray();
  hilog.info(0x0000, 'testTag', 'readByteArray is  ' + array);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readChar

```TypeScript
readChar(): int
```

从MessageSequence实例中读取单个字符值。

**起始版本：** 23

<!--Device-MessageSequence-readChar(): int--><!--Device-MessageSequence-readChar(): int-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回单个字符值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeChar(97);
  let ret = data.readChar();
  hilog.info(0x0000, 'testTag', 'readChar is ' + ret);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readCharArray

```TypeScript
readCharArray(dataIn: int[]): void
```

从MessageSequence实例中读取单个字符数组，并将其写入到创建的空数组中。

**起始版本：** 23

<!--Device-MessageSequence-readCharArray(dataIn: int[]): void--><!--Device-MessageSequence-readCharArray(dataIn: int[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataIn | int[] | 是 | 用于存储从MessageSequence读取的单个字符数组，需预先创建空数组且长度应与写入时的数组长度一致。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match. |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeCharArray([97, 98, 88]);
  let array: Array<number> = new Array(3);
  data.readCharArray(array);
  hilog.info(0x0000, 'testTag', 'readCharArray is ' + array);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

ArkTS-Sta示例：

```TypeScript
import rpc from '@ohos.rpc';
import hilog from 'ohos.hilog';
import { BusinessError } from '@ohos.base';

try {
  let data = rpc.MessageSequence.create();
  data.writeCharArray([97, 98, 88]);
  let array: Array<int> = new Array<int>(3);
  data.readCharArray(array);
  hilog.info(0x0000, 'testTag', 'readCharArray is ' + array);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readCharArray

```TypeScript
readCharArray(): int[]
```

从MessageSequence实例中读取单个字符数组。 - 返回新创建的数组，无需预先创建。 - 数组元素为字符编码，取值范围[0, 65535]。

**起始版本：** 23

<!--Device-MessageSequence-readCharArray(): int[]--><!--Device-MessageSequence-readCharArray(): int[]-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int[] | 返回单个字符数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeCharArray([97, 98, 88]);
  let array = data.readCharArray();
  hilog.info(0x0000, 'testTag', 'readCharArray is ' + array);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readDouble

```TypeScript
readDouble(): double
```

从MessageSequence实例中读取双精度浮点值。 - 返回新创建的数组，无需预先创建。 - 数组元素为双精度浮点数。

**起始版本：** 23

<!--Device-MessageSequence-readDouble(): double--><!--Device-MessageSequence-readDouble(): double-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 返回双精度浮点值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeDouble(10.2);
  let ret = data.readDouble();
  hilog.info(0x0000, 'testTag', 'readDouble is ' +  ret);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readDoubleArray

```TypeScript
readDoubleArray(dataIn: double[]): void
```

从MessageSequence实例中读取双精度浮点数组，并将其写入到创建的空数组中。

**起始版本：** 23

<!--Device-MessageSequence-readDoubleArray(dataIn: double[]): void--><!--Device-MessageSequence-readDoubleArray(dataIn: double[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataIn | double[] | 是 | 用于存储从MessageSequence读取的双精度浮点数组，需预先创建空数组且长度应与写入时的数组长度一致。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match. |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeDoubleArray([11.1, 12.2, 13.3]);
  let array: Array<number> = new Array(3);
  data.readDoubleArray(array);
  hilog.info(0x0000, 'testTag', 'readDoubleArray is ' + array);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

ArkTS-Sta示例：

```TypeScript
import rpc from '@ohos.rpc';
import hilog from 'ohos.hilog';
import { BusinessError } from '@ohos.base';

try {
  let data = rpc.MessageSequence.create();
  data.writeDoubleArray([11.1, 12.2, 13.3]);
  let array: Array<double> = new Array<double>(3);
  data.readDoubleArray(array);
  hilog.info(0x0000, 'testTag', 'readDoubleArray is ' + array);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readDoubleArray

```TypeScript
readDoubleArray(): double[]
```

从MessageSequence实例中读取双精度浮点数组。由于系统内部对float类型的数据是按照double处理的，使用时对于数组所占的总字节数应按照double类型来计算。

**起始版本：** 23

<!--Device-MessageSequence-readDoubleArray(): double[]--><!--Device-MessageSequence-readDoubleArray(): double[]-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double[] | 返回双精度浮点数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeDoubleArray([11.1, 12.2, 13.3]);
  let array = data.readDoubleArray();
  hilog.info(0x0000, 'testTag', 'readDoubleArray is ' + array);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readException

```TypeScript
readException(): void
```

从MessageSequence中读取异常。适用于接收远端服务响应后检查异常状态的场景。 - 在IPC/RPC通信的客户端使用。 - 在调用sendMessageRequest收到响应后调用。 - 在每次IPC/RPC调用后优先调用此方法。 - 如有异常立即处理并终止后续数据读取，异常处理后建议调用reclaim()释放MessageSequence对象。 - 此方法与[writeNoException](#writenoexception)方法配对使用。 - 调用顺序：服务端处理请求 → [writeNoException](#writenoexception) → 客户端收到响应 → [readException](#readexception) - 如果服务端未调用 [writeNoException](#writenoexception)，调用此方法会失败。

**起始版本：** 23

<!--Device-MessageSequence-readException(): void--><!--Device-MessageSequence-readException(): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

在本文档的示例中，通过this.getUIContext().getHostContext()来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
// FA模型需要从@kit.AbilityKit导入featureAbility
// import { featureAbility } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { Want, common } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let proxy: rpc.IRemoteObject | undefined;
let connect: common.ConnectOptions = {
  onConnect: (elementName, remoteProxy) => {
    hilog.info(0x0000, 'testTag', 'js onConnect called');
    proxy = remoteProxy;
  },
  onDisconnect: (elementName) => {
    hilog.info(0x0000, 'testTag', 'onDisconnect');
  },
  onFailed: () => {
    hilog.info(0x0000, 'testTag', 'onFailed');
  }
};
let want: Want = {
  // 获取服务端包名和ability名称
  bundleName: "com.ohos.server",
  abilityName: "com.ohos.server.EntryAbility",
};

// FA模型使用此方法连接服务
// FA.connectAbility(want,connect);

// 建立连接后返回的Id需要保存下来，在解绑服务时需要作为参数传入
let context: common.UIAbilityContext = this.getUIContext().getHostContext(); // UIAbilityContext
// 建立连接后返回的Id需要保存下来，在解绑服务时需要作为参数传入
let connectionId = context.connectServiceExtensionAbility(want, connect);
```

上述onConnect回调函数中的proxy对象需要等ability异步连接成功后才会被赋值，然后才可调用proxy对象的sendMessageRequest接口方法发送消息

```TypeScript
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let option = new rpc.MessageOption();
  let data = rpc.MessageSequence.create();
  let reply = rpc.MessageSequence.create();
  data.writeNoException();
  data.writeInt(6);
  if (proxy != undefined) {
    proxy.sendMessageRequest(1, data, reply, option)
      .then((result: rpc.RequestResult) => {
        if (result.errCode === 0) {
          hilog.info(0x0000, 'testTag', 'sendMessageRequest got result');
          result.reply.readException();
          let num = result.reply.readInt();
          hilog.info(0x0000, 'testTag', 'reply num: ' + num);
        } else {
          hilog.error(0x0000, 'testTag', 'sendMessageRequest failed, errCode: ' + result.errCode);
        }
      }).catch((e: Error) => {
        hilog.error(0x0000, 'testTag', 'sendMessageRequest got exception: ' + JSON.stringify(e));
      }).finally (() => {
        hilog.info(0x0000, 'testTag', 'sendMessageRequest ends, reclaim parcel');
        data.reclaim();
        reply.reclaim();
      });
  }
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readFileDescriptor

```TypeScript
readFileDescriptor(): int
```

从MessageSequence中读取文件描述符。接收端读取到的是映射后的新文件描述符编号，与发送端写入的描述符编号不同，但指向同一个文件资源。读取后建议及时使用并关闭，防止资源泄漏。 如需长期使用，可调用dupFileDescriptor复制描述符。 - 必须与[writeFileDescriptor](#writefiledescriptor)配对使用。 - 不要依赖源端的fd编号。 - 读取后需要管理生命周期。 - 建议及时使用避免资源浪费。 - 使用完毕后及时关闭。

**起始版本：** 23

<!--Device-MessageSequence-readFileDescriptor(): int--><!--Device-MessageSequence-readFileDescriptor(): int-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回文件描述符。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { fileIo } from '@kit.CoreFileKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let sequence = rpc.MessageSequence.create();
  let filePath = "path/to/file";
  let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
  sequence.writeFileDescriptor(file.fd);
  let readFD = sequence.readFileDescriptor();
  hilog.info(0x0000, 'testTag', 'readFileDescriptor is ' + readFD);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readFloat

```TypeScript
readFloat(): double
```

从MessageSequence实例中读取浮点值。由于系统内部对float类型的数据是按照double处理的，读取的数据按double精度返回。

**起始版本：** 23

<!--Device-MessageSequence-readFloat(): double--><!--Device-MessageSequence-readFloat(): double-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 返回双精度浮点值。由于系统内部对float类型的数据是按照double处理的，读取的数据按double精度返回。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeFloat(1.2);
  let ret = data.readFloat();
  hilog.info(0x0000, 'testTag', 'readFloat is ' + ret);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readFloatArray

```TypeScript
readFloatArray(dataIn: double[]): void
```

从MessageSequence实例中读取双精度浮点数组，并将其写入到创建的空数组中。

**起始版本：** 23

<!--Device-MessageSequence-readFloatArray(dataIn: double[]): void--><!--Device-MessageSequence-readFloatArray(dataIn: double[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataIn | double[] | 是 | 用于存储从MessageSequence读取的双精度浮点数组，需预先创建空数组且长度应与写入时的数组长度一致。 由于系统内部对float类型的数据是按照double处理的，使用时对于数组所占的总字节数应按照double类型来计算。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match. |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeFloatArray([1.2, 1.3, 1.4]);
  let array: Array<number> = new Array(3);
  data.readFloatArray(array);
  hilog.info(0x0000, 'testTag', 'readFloatArray is ' + array);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

ArkTS-Sta示例：

```TypeScript
import rpc from '@ohos.rpc';
import hilog from 'ohos.hilog';
import { BusinessError } from '@ohos.base';

try {
  let data = rpc.MessageSequence.create();
  data.writeFloatArray([1.2, 1.3, 1.4]);
  let array: Array<double> = new Array<double>(3);
  data.readFloatArray(array);
  hilog.info(0x0000, 'testTag', 'readFloatArray is ' + array);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readFloatArray

```TypeScript
readFloatArray(): double[]
```

从MessageSequence实例中读取双精度浮点数组。由于系统内部对float类型的数据是按照double处理的，使用时对于数组所占的总字节数应按照double类型来计算。

**起始版本：** 23

<!--Device-MessageSequence-readFloatArray(): double[]--><!--Device-MessageSequence-readFloatArray(): double[]-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double[] | 返回双精度浮点数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeFloatArray([1.2, 1.3, 1.4]);
  let array = data.readFloatArray();
  hilog.info(0x0000, 'testTag', 'readFloatArray is ' + array);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readInt

```TypeScript
readInt(): int
```

从MessageSequence实例中读取整数值。 - 整数值占用4字节存储空间。 - 存储范围：[-2^31, 2^31-1]。

**起始版本：** 23

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MessageSequence-readInt(): int--><!--Device-MessageSequence-readInt(): int-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回整数值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
// 在原子化服务中，本示例仅用于说明readInt()接口的使用方法，示例中rpc.MessageSequence.create()暂不支持在原子化服务中调用。
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeInt(10);
  let ret = data.readInt();
  hilog.info(0x0000, 'testTag', 'readInt is ' + ret);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readIntArray

```TypeScript
readIntArray(dataIn: int[]): void
```

从MessageSequence实例中读取整数数组，并将其写入到创建的空数组中。 - 需预先创建空数组且长度应与写入时的数组长度一致。 - 数组元素取值范围:[-2^31, 2^31-1]。

**起始版本：** 23

<!--Device-MessageSequence-readIntArray(dataIn: int[]): void--><!--Device-MessageSequence-readIntArray(dataIn: int[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataIn | int[] | 是 | 用于存储从MessageSequence读取的整数数组，需预先创建空数组且长度应与写入时的数组长度一致。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match. |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeIntArray([100, 111, 112]);
  let array: Array<number> = new Array(3);
  data.readIntArray(array);
  hilog.info(0x0000, 'testTag', 'readIntArray is  ' + array);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

ArkTS-Sta示例：

```TypeScript
import rpc from '@ohos.rpc';
import hilog from 'ohos.hilog';
import { BusinessError } from '@ohos.base';

try {
  let data = rpc.MessageSequence.create();
  data.writeIntArray([100, 111, 112]);
  let array: Array<int> = new Array<int>(3);
  data.readIntArray(array);
  hilog.info(0x0000, 'testTag', 'readIntArray is  ' + array);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readIntArray

```TypeScript
readIntArray(): int[]
```

从MessageSequence实例中读取整数数组。

**起始版本：** 23

<!--Device-MessageSequence-readIntArray(): int[]--><!--Device-MessageSequence-readIntArray(): int[]-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int[] | 返回整数数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeIntArray([100, 111, 112]);
  let array = data.readIntArray();
  hilog.info(0x0000, 'testTag', 'readIntArray is ' + array);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readInterfaceToken

```TypeScript
readInterfaceToken(): string
```

从MessageSequence对象中读取接口描述符，接口描述符按写入MessageSequence的顺序读取，本地对象可使用该信息检验本次通信。 - 必须与[writeInterfaceToken](#writeinterfacetoken)配对使用。 - 读取前应确保缓冲区中有可读数据。 - 建议在收到IPC请求后立即读取校验。

**起始版本：** 23

<!--Device-MessageSequence-readInterfaceToken(): string--><!--Device-MessageSequence-readInterfaceToken(): string-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回读取到的接口描述符。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeInterfaceToken("aaa");
  let interfaceToken = data.readInterfaceToken();
  hilog.info(0x0000, 'testTag', 'RpcServer: interfaceToken is ' + interfaceToken);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readLong

```TypeScript
readLong(): long
```

从MessageSequence实例中读取长整数值。 - 取值范围：[-2^63, 2^63-1]。 - 长整数占用8字节存储空间。

**起始版本：** 23

<!--Device-MessageSequence-readLong(): long--><!--Device-MessageSequence-readLong(): long-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 返回长整数值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeLong(10000);
  let ret = data.readLong();
  hilog.info(0x0000, 'testTag', 'readLong is ' + ret);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readLongArray

```TypeScript
readLongArray(dataIn: long[]): void
```

从MessageSequence实例中读取长整数数组，并将其写入到创建的空数组中。

**起始版本：** 23

<!--Device-MessageSequence-readLongArray(dataIn: long[]): void--><!--Device-MessageSequence-readLongArray(dataIn: long[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataIn | long[] | 是 | 用于存储从MessageSequence读取的长整数数组，需预先创建空数组且长度应与写入时的数组长度一致。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match. |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeLongArray([1111, 1112, 1113]);
  let array: Array<number> = new Array(3);
  data.readLongArray(array);
  hilog.info(0x0000, 'testTag', 'readLongArray is ' + array);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

ArkTS-Sta示例：

```TypeScript
import rpc from '@ohos.rpc';
import hilog from 'ohos.hilog';
import { BusinessError } from '@ohos.base';

try {
  let data = rpc.MessageSequence.create();
  data.writeLongArray([1111, 1112, 1113]);
  let array: Array<long> = new Array<long>(3);
  data.readLongArray(array);
  hilog.info(0x0000, 'testTag', 'readLongArray is ' + array);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readLongArray

```TypeScript
readLongArray(): long[]
```

从MessageSequence实例中读取长整数数组。

**起始版本：** 23

<!--Device-MessageSequence-readLongArray(): long[]--><!--Device-MessageSequence-readLongArray(): long[]-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long[] | 返回长整数数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeLongArray([1111, 1112, 1113]);
  let array = data.readLongArray();
  hilog.info(0x0000, 'testTag', 'readLongArray is ' + array);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readParcelable

```TypeScript
readParcelable(dataIn: Parcelable): void
```

从MessageSequence实例中读取成员变量到指定的对象（dataIn）。 - dataIn参数必须为已实例化的Parcelable对象。 - unmarshalling方法必须按与marshalling相同的顺序读取。 - 反序列化顺序必须与序列化顺序一致。 - 建议在unmarshalling中处理异常情况。

**起始版本：** 23

<!--Device-MessageSequence-readParcelable(dataIn: Parcelable): void--><!--Device-MessageSequence-readParcelable(dataIn: Parcelable): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataIn | [Parcelable](arkts-ipc-rpc-parcelable-i.md) | 是 | 需要从MessageSequence读取成员变量的对象，使用前请先实例化可序列化对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900012](../errorcode-rpc.md#1900012-js回调方法执行失败) | Failed to call the JS callback function. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect. |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

class MyParcelable implements rpc.Parcelable {
  num: number = 0;
  str: string = '';
  constructor( num: number, str: string) {
    this.num = num;
    this.str = str;
  }
  marshalling(messageSequence: rpc.MessageSequence): boolean {
    messageSequence.writeInt(this.num);
    messageSequence.writeString(this.str);
    return true;
  }
  unmarshalling(messageSequence: rpc.MessageSequence): boolean {
    this.num = messageSequence.readInt();
    this.str = messageSequence.readString();
    return true;
  }
}

try {
  let parcelable = new MyParcelable(1, "aaa");
  let data = rpc.MessageSequence.create();
  data.writeParcelable(parcelable);
  let ret = new MyParcelable(0, "");
  data.readParcelable(ret);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readParcelableArray

```TypeScript
readParcelableArray(parcelableArray: Parcelable[]): void
```

从MessageSequence实例中读取可序列化对象数组。适用于接收批量传输的多个自定义数据结构对象的场景，如读取多条业务记录、批量配置信息、多个实体对象等。

**起始版本：** 23

<!--Device-MessageSequence-readParcelableArray(parcelableArray: Parcelable[]): void--><!--Device-MessageSequence-readParcelableArray(parcelableArray: Parcelable[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parcelableArray | [Parcelable](arkts-ipc-rpc-parcelable-i.md)[] | 是 | 要读取的可序列化对象数组，使用前请先实例化可序列化对象，且序列化与反序列化数组长度须一致。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900012](../errorcode-rpc.md#1900012-js回调方法执行失败) | Failed to call the JS callback function. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match; 4.The length of the array passed when reading is not equal to the length passed when writing to the array; 5.The element does not exist in the array. |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

class MyParcelable implements rpc.Parcelable {
  num: number = 0;
  str: string = '';
  constructor(num: number, str: string) {
    this.num = num;
    this.str = str;
  }
  marshalling(messageSequence: rpc.MessageSequence): boolean {
    messageSequence.writeInt(this.num);
    messageSequence.writeString(this.str);
    return true;
  }
  unmarshalling(messageSequence: rpc.MessageSequence): boolean {
    this.num = messageSequence.readInt();
    this.str = messageSequence.readString();
    return true;
  }
}

try {
  let parcelable = new MyParcelable(1, "aaa");
  let parcelable2 = new MyParcelable(2, "bbb");
  let parcelable3 = new MyParcelable(3, "ccc");
  let a = [parcelable, parcelable2, parcelable3];
  let data = rpc.MessageSequence.create();
  data.writeParcelableArray(a);
  let b = [new MyParcelable(0, ""), new MyParcelable(0, ""), new MyParcelable(0, "")];
  data.readParcelableArray(b);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'rpc write parcelable array fail, errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'rpc write parcelable array fail, errorMessage ' + e.message);
}
```

## readRawData

```TypeScript
readRawData(size: number): number[]
```

从MessageSequence读取原始数据。

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [readRawDataBuffer](#readrawdatabuffer)(size: int)

<!--Device-MessageSequence-readRawData(size: number): number[]--><!--Device-MessageSequence-readRawData(size: number): number[]-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | number | 是 | 要读取的原始数据的大小，以字节为单位。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number[] | 返回原始数据（以字节为单位）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let sequence = rpc.MessageSequence.create();
  let arr = [1, 2, 3, 4, 5];
  sequence.writeRawData(arr, arr.length);
  let size = arr.length;
  let result = sequence.readRawData(size);
  hilog.info(0x0000, 'testTag', 'sequence read raw data result is ' + result);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readRawDataBuffer

```TypeScript
readRawDataBuffer(size: int): ArrayBuffer
```

从MessageSequence读取原始数据。 - 需与写入时的数据大小匹配。 - 该接口是一次性接口,不允许在一次parcel通信中多次调用。 - 大数据量传输时注意系统资源占用。 - 必须与[writeRawDataBuffer](#writerawdatabuffer)配对使用。

**起始版本：** 23

<!--Device-MessageSequence-readRawDataBuffer(size: int): ArrayBuffer--><!--Device-MessageSequence-readRawDataBuffer(size: int): ArrayBuffer-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | int | 是 | 要读取的原始数据的大小，以字节为单位，需与写入时的数据大小匹配。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArrayBuffer | 返回原始数据（以字节为单位）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let buffer = new ArrayBuffer(64 * 1024);
  let int32View = new Int32Array(buffer);
  for (let i = 0; i < int32View.length; i++) {
    int32View[i] = i * 2 + 1;
  }
  let size = buffer.byteLength;
  let sequence = rpc.MessageSequence.create();
  sequence.writeRawDataBuffer(buffer, size);
  let result = sequence.readRawDataBuffer(size);
  let readInt32View = new Int32Array(result);
  hilog.info(0x0000, 'testTag', 'sequence read raw data result is ' + readInt32View);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readRemoteObject

```TypeScript
readRemoteObject(): IRemoteObject
```

从MessageSequence读取远程对象。此方法用于反序列化MessageSequence对象以生成IRemoteObject。远程对象按写入MessageSequence的顺序读取。调用此方法后，会从 MessageSequence缓冲区中读取已序列化的远程对象数据，并反序列化为IRemoteObject实例。读取操作会更新内部读指针位置。 - 读取前应确保缓冲区中有可读数据。 - 如果写入的是RemoteObject，读取得到的是RemoteProxy。 - 读取失败时会抛出异常，建议使用try-catch捕获。

**起始版本：** 23

<!--Device-MessageSequence-readRemoteObject(): IRemoteObject--><!--Device-MessageSequence-readRemoteObject(): IRemoteObject-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [IRemoteObject](arkts-ipc-rpc-iremoteobject-c.md) | 读取到的远程对象，用于IPC/RPC通信。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900008](../errorcode-rpc.md#1900008-非法的ipc对象) | The proxy or remote object is invalid. |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean | Promise<boolean> {
    // 根据业务实际逻辑，进行相应处理
    return true;
  }
}

try {
  let data = rpc.MessageSequence.create();
  let testRemoteObject = new TestRemoteObject("testObject");
  data.writeRemoteObject(testRemoteObject);
  let proxy = data.readRemoteObject();
  hilog.info(0x0000, 'testTag', 'readRemoteObject is ' + proxy);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readRemoteObjectArray

```TypeScript
readRemoteObjectArray(objects: IRemoteObject[]): void
```

从MessageSequence读取IRemoteObject对象数组，并将其写入到创建的空数组中。适用于接收批量传递的多个远程对象的场景，如批量获取服务代理、接收多个回调接口、多服务端点管理等。 - 需预先创建空数组且长度应与写入时的数组长度一致。 - 读取失败时会抛出异常，建议使用try-catch捕获。

**起始版本：** 23

<!--Device-MessageSequence-readRemoteObjectArray(objects: IRemoteObject[]): void--><!--Device-MessageSequence-readRemoteObjectArray(objects: IRemoteObject[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| objects | [IRemoteObject](arkts-ipc-rpc-iremoteobject-c.md)[] | 是 | 从MessageSequence读取的IRemoteObject对象数组，用于IPC/RPC通信，存储多个远程对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match; 4.The length of the array passed when reading is not equal to the length passed when writing to the array. |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean | Promise<boolean> {
    // 根据业务实际逻辑，进行相应处理
    return true;
  }
}

try {
  let a = [new TestRemoteObject("testObject1"), new TestRemoteObject("testObject2"), new TestRemoteObject("testObject3")];
  let data = rpc.MessageSequence.create();
  data.writeRemoteObjectArray(a);
  let b: Array<rpc.IRemoteObject> = new Array(3);
  data.readRemoteObjectArray(b);
  hilog.info(0x0000, 'testTag', 'readRemoteObjectArray is ' + b);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readRemoteObjectArray

```TypeScript
readRemoteObjectArray(): IRemoteObject[]
```

从MessageSequence读取IRemoteObject对象数组。

**起始版本：** 23

<!--Device-MessageSequence-readRemoteObjectArray(): IRemoteObject[]--><!--Device-MessageSequence-readRemoteObjectArray(): IRemoteObject[]-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [IRemoteObject](arkts-ipc-rpc-iremoteobject-c.md)[] | 返回IRemoteObject对象数组；当写入的是空数组时，返回的是nullptr。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean | Promise<boolean> {
    // 根据业务实际逻辑，进行相应处理
    return true;
  }
}

try {
  let a = [new TestRemoteObject("testObject1"), new TestRemoteObject("testObject2"), new TestRemoteObject("testObject3")];
  let data = rpc.MessageSequence.create();
  let b = data.readRemoteObjectArray();
  hilog.info(0x0000, 'testTag', 'readRemoteObjectArray is ' + b);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readShort

```TypeScript
readShort(): int
```

从MessageSequence实例中读取短整数值。 - 必须与[writeShort](#writeshort)配对使用。 - 注意写入时的取值范围[-2^15, 2^15-1]，超出此范围会导致数据截断。

**起始版本：** 23

<!--Device-MessageSequence-readShort(): int--><!--Device-MessageSequence-readShort(): int-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回短整数值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeShort(8);
  let ret = data.readShort();
  hilog.info(0x0000, 'testTag', 'readShort is ' + ret);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readShortArray

```TypeScript
readShortArray(dataIn: int[]): void
```

从MessageSequence实例中读取短整数数组，并将其写入到创建的空数组中。

**起始版本：** 23

<!--Device-MessageSequence-readShortArray(dataIn: int[]): void--><!--Device-MessageSequence-readShortArray(dataIn: int[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataIn | int[] | 是 | 用于存储从MessageSequence读取的短整数数组，需预先创建空数组且长度应与写入时的数组长度一致。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match. |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeShortArray([11, 12, 13]);
  let array: Array<number> = new Array(3);
  data.readShortArray(array);
  hilog.info(0x0000, 'testTag', 'readShortArray is  ' + array);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

ArkTS-Sta示例：

```TypeScript
import rpc from '@ohos.rpc';
import hilog from 'ohos.hilog';
import { BusinessError } from '@ohos.base';

try {
  let data = rpc.MessageSequence.create();
  data.writeShortArray([11, 12, 13]);
  let array: Array<int> = new Array<int>(3);
  data.readShortArray(array);
  hilog.info(0x0000, 'testTag', 'readShortArray is  ' + array);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readShortArray

```TypeScript
readShortArray(): int[]
```

从MessageSequence实例中读取短整数数组。

**起始版本：** 23

<!--Device-MessageSequence-readShortArray(): int[]--><!--Device-MessageSequence-readShortArray(): int[]-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int[] | 返回短整数数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeShortArray([11, 12, 13]);
  let array = data.readShortArray();
  hilog.info(0x0000, 'testTag', 'readShortArray is ' + array);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readString

```TypeScript
readString(): string
```

从MessageSequence实例中读取字符串值。 - 先读取长度，再读取内容。

**起始版本：** 23

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MessageSequence-readString(): string--><!--Device-MessageSequence-readString(): string-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回字符串值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
// 在原子化服务中，本示例仅用于说明readString()接口的使用方法，示例中rpc.MessageSequence.create()暂不支持在原子化服务中调用。
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeString('abc');
  let ret = data.readString();
  hilog.info(0x0000, 'testTag', 'readString is ' + ret);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readStringArray

```TypeScript
readStringArray(dataIn: string[]): void
```

从MessageSequence实例中读取字符串数组，并将其写入到创建的空数组中。 - 需预先创建空数组且长度应与写入时的数组长度一致。 - 读取后dataIn数组会被填充读取的字节数据。 - 读指针向后移动相应字节数。

**起始版本：** 23

<!--Device-MessageSequence-readStringArray(dataIn: string[]): void--><!--Device-MessageSequence-readStringArray(dataIn: string[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataIn | string[] | 是 | 要读取的字符串数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match. |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeStringArray(["abc", "def"]);
  let array: Array<string> = new Array(2);
  data.readStringArray(array);
  hilog.info(0x0000, 'testTag', 'readStringArray is ' + array);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## readStringArray

```TypeScript
readStringArray(): string[]
```

从MessageSequence实例中读取字符串数组。 - 返回新创建的数组，无需预先创建。 - 数组单个元素的长度范围0-40959字节。

**起始版本：** 23

<!--Device-MessageSequence-readStringArray(): string[]--><!--Device-MessageSequence-readStringArray(): string[]-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string[] | 返回字符串数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeStringArray(["abc", "def"]);
  let array = data.readStringArray();
  hilog.info(0x0000, 'testTag', 'readStringArray is ' + array);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## reclaim

```TypeScript
reclaim(): void
```

释放不再使用的MessageSequence对象。 - 必须与create()方法配对使用，调用create()创建MessageSequence对象后，必须在使用完毕后调用reclaim()释放资源。未及时调用reclaim()会导致内存资源泄漏。 - 调用后对象不能再被使用。 - 建议在finally块或任务结束时调用，确保资源释放。 - 不要在异步操作中跨线程释放。

**起始版本：** 23

<!--Device-MessageSequence-reclaim(): void--><!--Device-MessageSequence-reclaim(): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let reply = rpc.MessageSequence.create();
  reply.reclaim();
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## rewindRead

```TypeScript
rewindRead(pos: int): void
```

重新偏移读取位置到指定的位置。

**起始版本：** 23

<!--Device-MessageSequence-rewindRead(pos: int): void--><!--Device-MessageSequence-rewindRead(pos: int): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pos | int | 是 | 开始读取数据的目标位置，以字节为单位。用于重新定位MessageSequence的读指针，值应在 [0, [getSize](#getsize)]范围内。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900010](../errorcode-rpc.md#1900010-读取messagesequence数据失败) | Failed to read data from the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeInt(12);
  data.writeString("sequence");
  let number = data.readInt();
  hilog.info(0x0000, 'testTag', 'number is ' + number);
  data.rewindRead(0);
  let number2 = data.readInt();
  hilog.info(0x0000, 'testTag', 'rewindRead is ' + number2);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## rewindWrite

```TypeScript
rewindWrite(pos: int): void
```

重新偏移写位置到指定的位置。

**起始版本：** 23

<!--Device-MessageSequence-rewindWrite(pos: int): void--><!--Device-MessageSequence-rewindWrite(pos: int): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pos | int | 是 | 开始写入数据的目标位置，以字节为单位。用于重新定位MessageSequence的写指针，值应在 [0, [getSize](#getsize)]范围内。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeInt(4);
  data.rewindWrite(0);
  data.writeInt(5);
  let number = data.readInt();
  hilog.info(0x0000, 'testTag', 'rewindWrite is: ' + number);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## setCapacity

```TypeScript
setCapacity(size: int): void
```

设置MessageSequence对象的存储容量。

**起始版本：** 23

<!--Device-MessageSequence-setCapacity(size: int): void--><!--Device-MessageSequence-setCapacity(size: int): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | int | 是 | MessageSequence实例的存储容量。以字节为单位。用于限制可写入数据的最大字节数，建议根据实际数据量合理设置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |
| [1900011](../errorcode-rpc.md#1900011-内存分配失败) | Memory allocation failed. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.setCapacity(100);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## setSize

```TypeScript
setSize(size: int): void
```

设置MessageSequence对象中包含的数据大小。

**起始版本：** 23

<!--Device-MessageSequence-setSize(size: int): void--><!--Device-MessageSequence-setSize(size: int): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | int | 是 | MessageSequence实例的数据大小。以字节为单位。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeString('Hello World');
  data.setSize(16);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## writeArrayBuffer

```TypeScript
writeArrayBuffer(buf: ArrayBuffer, typeCode: TypeCode): void
```

将ArrayBuffer类型数据写入MessageSequence对象。 - 此方法与[readArrayBuffer](#readarraybuffer)方法配对使用。 - 写入的typeCode必须与读取的typeCode一致，否则会导致数据异常。 - 调用顺序：先调用writeArrayBuffer()写入数据 → 再调用[readArrayBuffer](#readarraybuffer)读取数据。 - typeCode参数决定了数据的写入和读取方式。 - 读写typeCode不匹配会导致数据解析错误。 - 必须根据实际数据类型选择正确的[TypeCode](arkts-ipc-rpc-typecode-e.md)枚举值。

**起始版本：** 23

<!--Device-MessageSequence-writeArrayBuffer(buf: ArrayBuffer, typeCode: TypeCode): void--><!--Device-MessageSequence-writeArrayBuffer(buf: ArrayBuffer, typeCode: TypeCode): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buf | ArrayBuffer | 是 | 要写入的ArrayBuffer数据，数据将根据typeCode指定的TypedArray类型进行格式化写入。 |
| typeCode | [TypeCode](arkts-ipc-rpc-typecode-e.md) | 是 | ArrayBuffer数据具体是以哪一种TypedArray来访问和操作(会根据业务传递的类型枚举值去决定底层的写入方式，需要业务正确传递枚举值。) |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match; 4.The obtained value of typeCode is incorrect; 5.Failed to obtain arrayBuffer information. |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |

**示例**

```TypeScript
// TypeCode 类型枚举较多，示例代码以Int16Array为例
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  let buffer = new ArrayBuffer(10);
  let int16View = new Int16Array(buffer);
  for (let i = 0; i < int16View.length; i++) {
    int16View[i] = i * 2 + 1;
  }
  data.writeArrayBuffer(buffer, rpc.TypeCode.INT16_ARRAY);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## writeAshmem

```TypeScript
writeAshmem(ashmem: Ashmem): void
```

将指定的匿名共享对象写入此MessageSequence。 - 创建Ashmem对象：Ashmem.create()。 - 映射内存并写入数据：[mapReadWriteAshmem](arkts-ipc-rpc-ashmem-c.md#mapreadwriteashmem) + [writeDataToAshmem](arkts-ipc-rpc-ashmem-c.md#writedatatoashmem)。 - 将Ashmem写入MessageSequence：writeAshmem()。 - 接收端读取Ashmem：[readAshmem](#readashmem)。 - 接收端映射内存并读取数据：mapReadWriteAshmem() + readDataFromAshmem()。 - 此方法与readAshmem()方法配对使用。 - 调用顺序：writeAshmem() → 传输MessageSequence → [readAshmem](#readashmem) → [mapReadWriteAshmem](arkts-ipc-rpc-ashmem-c.md#mapreadwriteashmem) → [readDataFromAshmem](arkts-ipc-rpc-ashmem-c.md#readdatafromashmem)。 - 使用前需先创建Ashmem对象并写入数据。

**起始版本：** 23

<!--Device-MessageSequence-writeAshmem(ashmem: Ashmem): void--><!--Device-MessageSequence-writeAshmem(ashmem: Ashmem): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ashmem | [Ashmem](arkts-ipc-rpc-ashmem-c.md) | 是 | 要写入MessageSequence的匿名共享对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter is not an instance of the Ashmem object. |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let sequence = rpc.MessageSequence.create();
  let ashmem = rpc.Ashmem.create("ashmem", 1024);
  // ashmem里写入数据
  let buffer = new ArrayBuffer(1024);
  let int32View = new Int32Array(buffer);
  for (let i = 0; i < int32View.length; i++) {
    int32View[i] = i * 2 + 1;
  }
  let size = buffer.byteLength;
  ashmem.mapReadWriteAshmem();
  ashmem.writeDataToAshmem(buffer, size, 0);
  // 将ashmem对象写入messageSequence对象中
  sequence.writeAshmem(ashmem);
  // 将传递的数据大小写入messageSequence对象中
  sequence.writeInt(size);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## writeBoolean

```TypeScript
writeBoolean(val: boolean): void
```

将布尔值写入MessageSequence实例。 - 必须与[readBoolean](#readboolean)配对使用。 - 一次写入对应一次读取。

**起始版本：** 23

<!--Device-MessageSequence-writeBoolean(val: boolean): void--><!--Device-MessageSequence-writeBoolean(val: boolean): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | boolean | 是 | 要写入的布尔值，true表示逻辑真，false表示逻辑假，写入后将占用1字节存储空间。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeBoolean(false);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## writeBooleanArray

```TypeScript
writeBooleanArray(booleanArray: boolean[]): void
```

将布尔数组写入MessageSequence实例。 - 必须与[readBooleanArray](#readbooleanarray)配对使用。 - 读取数组长度必须与写入数组长度一致。

**起始版本：** 23

<!--Device-MessageSequence-writeBooleanArray(booleanArray: boolean[]): void--><!--Device-MessageSequence-writeBooleanArray(booleanArray: boolean[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| booleanArray | boolean[] | 是 | 要写入的布尔数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match; 4.The element does not exist in the array. |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeBooleanArray([false, true, false]);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## writeByte

```TypeScript
writeByte(val: int): void
```

将字节值写入MessageSequence实例。调用此方法后，字节值会被以8位无符号整数形式存入缓冲区当前写指针位置，并自动更新写指针。该方法适用于传输小范围整数或标志位数据。 - 存储范围:[0, 255](无符号)或[-128, 127](有符号)。 - 数据对齐方式为字节对齐。 - 数值必须在字节范围内，超出范围可能导致数据截断。 - 读取时必须使用[readByte](#readbyte)方法配对读取。 - 不适合传输大范围数值，大范围数值建议使用[writeInt](#writeint)/ [writeLong](#writelong)等。

**起始版本：** 23

<!--Device-MessageSequence-writeByte(val: int): void--><!--Device-MessageSequence-writeByte(val: int): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | int | 是 | 要写入的字节值。取值范围[0, 255]。超出此范围时，数值会被自动截断为8位，可能导致数据精度丢失。建议传入前先检查数值范围。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeByte(2);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## writeByteArray

```TypeScript
writeByteArray(byteArray: int[]): void
```

将字节数组写入MessageSequence实例。 - 必须与[readByteArray](#readbytearray)配对使用。 - 读取数组长度必须与写入数组长度一致。

**起始版本：** 23

<!--Device-MessageSequence-writeByteArray(byteArray: int[]): void--><!--Device-MessageSequence-writeByteArray(byteArray: int[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| byteArray | int[] | 是 | 要写入的字节数组，用于批量传输字节序列数据。数组不能为空，每个元素取值范围[0, 255]。超出范围可能导致数据截断。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match; 4.The element does not exist in the array. 5.The type of the element in the array is incorrect. |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  let ByteArrayVar = [1, 2, 3, 4, 5];
  data.writeByteArray(ByteArrayVar);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## writeChar

```TypeScript
writeChar(val: int): void
```

将单个字符值写入MessageSequence实例。 - 必须与[readChar](#readchar)配对使用。 - 一次写入对应一次读取。

**起始版本：** 23

<!--Device-MessageSequence-writeChar(val: int): void--><!--Device-MessageSequence-writeChar(val: int): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | int | 是 | 要写入的单个字符值。取值范围：[0, 65535]，对应Unicode字符编码范围。超出此范围可能导致字符编码异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeChar(97);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## writeCharArray

```TypeScript
writeCharArray(charArray: int[]): void
```

将单个字符数组写入MessageSequence实例。 - 必须与[readCharArray](#readchararray)配对使用。 - 读取数组长度必须与写入数组长度一致。

**起始版本：** 23

<!--Device-MessageSequence-writeCharArray(charArray: int[]): void--><!--Device-MessageSequence-writeCharArray(charArray: int[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| charArray | int[] | 是 | 要写入的单个字符数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match; 4.The element does not exist in the array. |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeCharArray([97, 98, 88]);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## writeDouble

```TypeScript
writeDouble(val: double): void
```

将双精度浮点值写入MessageSequence实例。 - 必须与[readDouble](#readdouble)配对使用。 - 一次写入对应一次读取。

**起始版本：** 23

<!--Device-MessageSequence-writeDouble(val: double): void--><!--Device-MessageSequence-writeDouble(val: double): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | double | 是 | 要写入的双精度浮点值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeDouble(10.2);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## writeDoubleArray

```TypeScript
writeDoubleArray(doubleArray: double[]): void
```

将双精度浮点数组写入MessageSequence实例。 - 必须与[readDoubleArray](#readdoublearray)配对使用。 - 读取数组长度必须与写入数组长度一致。

**起始版本：** 23

<!--Device-MessageSequence-writeDoubleArray(doubleArray: double[]): void--><!--Device-MessageSequence-writeDoubleArray(doubleArray: double[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| doubleArray | double[] | 是 | 要写入的双精度浮点数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match; 4.The element does not exist in the array; 5.The type of the element in the array is incorrect. |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeDoubleArray([11.1, 12.2, 13.3]);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## writeFileDescriptor

```TypeScript
writeFileDescriptor(fd: int): void
```

写入文件描述符到MessageSequence。 调用此方法后，文件描述符会被封装并通过Binder机制跨进程传递。接收端可通过readFileDescriptor获取文件描述符并进行文件操作。 - 文件描述符通过Binder的FD传递机制跨进程传输。 - 接收端获得的是映射后的新文件描述符。 - 实际指向同一个文件资源。 - 支持普通文件、管道、socket等多种描述符。 - 文件描述符必须是有效的、已打开的描述符。 - 写入后原描述符仍然有效，需要业务自行管理。 - 建议使用dupFileDescriptor复制后再传递。 - 传递后接收端应及时使用，避免资源浪费。 - 读取后建议及时关闭，防止资源泄漏。

**起始版本：** 23

<!--Device-MessageSequence-writeFileDescriptor(fd: int): void--><!--Device-MessageSequence-writeFileDescriptor(fd: int): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | int | 是 | 文件描述符，通常通过文件操作接口（如fileIo.open）获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { fileIo } from '@kit.CoreFileKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let sequence = rpc.MessageSequence.create();
  let filePath = "path/to/file";
  let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
  sequence.writeFileDescriptor(file.fd);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## writeFloat

```TypeScript
writeFloat(val: double): void
```

将双精度浮点值写入MessageSequence实例。由于系统内部对float类型的数据是按照double处理的，实际写入的数据按双精度格式存储。

**起始版本：** 23

<!--Device-MessageSequence-writeFloat(val: double): void--><!--Device-MessageSequence-writeFloat(val: double): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | double | 是 | 要写入的双精度浮点值。适用于传输浮点数据(如坐标、比例、测量值等)。 必须与[readFloat](#readfloat)配对使用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeFloat(1.2);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## writeFloatArray

```TypeScript
writeFloatArray(floatArray: double[]): void
```

将双精度浮点数组写入MessageSequence实例。 - 必须与[readFloatArray](#readfloatarray)配对使用。 - 读取数组长度必须与写入数组长度一致。

**起始版本：** 23

<!--Device-MessageSequence-writeFloatArray(floatArray: double[]): void--><!--Device-MessageSequence-writeFloatArray(floatArray: double[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| floatArray | double[] | 是 | 要写入的双精度浮点数组。由于系统内部对float类型的数据是按照double处理的，使用时对于数组所占的总字节数应按照double类型来计算。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match; 4.The element does not exist in the array; 5.The type of the element in the array is incorrect. |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeFloatArray([1.2, 1.3, 1.4]);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## writeInt

```TypeScript
writeInt(val: int): void
```

将整数值写入MessageSequence实例。 调用此方法后，整数值会被以32位有符号整数形式存入缓冲区当前写指针位置，并自动更新写指针。该方法适用于传输标准整数数据。对于小范围数值建议使用 [writeByte](#writebyte)/[writeShort](#writeshort)提高效率；对于大范围数值建议 使用[writeLong](#writelong)。 - 必须与[readInt](#readint)配对使用。 - 一次写入对应一次读取 - 占用4字节(32位)存储空间。 - 采用系统默认字节序存储。 - 超出范围会导致数据截断或写入失败。

**起始版本：** 23

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MessageSequence-writeInt(val: int): void--><!--Device-MessageSequence-writeInt(val: int): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | int | 是 | 要写入的整数值。取值范围：[-2^31, 2^31-1]。适用于传输标准整数数据(如计数器、索引值、配置参数等)。超出此范围会导致数据截断或写入失败。 对于小范围数值(0-255或-128-127)建议使用writeByte提高效率，对于小范围整数(-32768-32767)建议使用writeShort，对于大整数建议使用writeLong。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |

**示例**

```TypeScript
// 在原子化服务中，本示例仅用于说明writeInt()接口的使用方法，示例中rpc.MessageSequence.create()暂不支持在原子化服务中调用。
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeInt(10);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## writeIntArray

```TypeScript
writeIntArray(intArray: int[]): void
```

将整数数组写入MessageSequence实例。 - 必须与[readIntArray](#readintarray)配对使用。 - 读取数组长度必须与写入数组长度一致。

**起始版本：** 23

<!--Device-MessageSequence-writeIntArray(intArray: int[]): void--><!--Device-MessageSequence-writeIntArray(intArray: int[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| intArray | int[] | 是 | 要写入的整数数组。数组元素的取值范围：[-2^31, 2^31-1]，超出此范围会导致数据截断或写入失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match; 4.The element does not exist in the array; 5.The type of the element in the array is incorrect. |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeIntArray([100, 111, 112]);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## writeInterfaceToken

```TypeScript
writeInterfaceToken(token: string): void
```

将接口描述符写入MessageSequence对象，远端对象可使用该信息校验本次通信。适用于需要验证通信双方接口一致性的场景，如跨进程服务调用、安全通信验证以及标识服务端提供的接口类型。建议使用唯一且有意义的描述符字符串（如" com.example.service"），避免使用敏感信息，长度应小于40960。调用此方法后，接口描述符字符串会被序列化并存入MessageSequence缓冲区。远端在接收到通信请求后，可读取该描述符来验证请求来源的合法 性。 - 必须与[readInterfaceToken](#readinterfacetoken)配对使用。 - 长度超过限制会抛出参数错误异常。

**起始版本：** 23

<!--Device-MessageSequence-writeInterfaceToken(token: string): void--><!--Device-MessageSequence-writeInterfaceToken(token: string): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| token | string | 是 | 字符串类型描述符，用于本次通信的接口身份校验。远端对象可使用该信息验证本次通信的合法性。其长度应小于40960。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.The string length is greater than or equal to 40960; 4.The number of bytes copied to the buffer is different from the length of the obtained string. |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeInterfaceToken("aaa");
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## writeLong

```TypeScript
writeLong(val: long): void
```

将长整数值写入MessageSequence实例。 - 必须与[readLong](#readlong)配对使用。 - 一次写入对应一次读取。

**起始版本：** 23

<!--Device-MessageSequence-writeLong(val: long): void--><!--Device-MessageSequence-writeLong(val: long): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | long | 是 | 要写入的长整数值。取值范围：[-2^63, 2^63-1]。超出此范围会导致数据截断或写入失败。 建议根据数值范围选择合适的类型(writeByte/writeShort/writeInt/writeLong)以提高传输效率。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeLong(10000);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## writeLongArray

```TypeScript
writeLongArray(longArray: long[]): void
```

将长整数数组写入MessageSequence实例。 - 必须与[readLongArray](#readlongarray)配对使用。 - 读取数组长度必须与写入数组长度一致。

**起始版本：** 23

<!--Device-MessageSequence-writeLongArray(longArray: long[]): void--><!--Device-MessageSequence-writeLongArray(longArray: long[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| longArray | long[] | 是 | 要写入的长整数数组，每个元素为64位整数。超出范围会导致数据截断。建议使用BigInt处理超大数值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match; 4.The element does not exist in the array; 5.The type of the element in the array is incorrect. |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeLongArray([1111, 1112, 1113]);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## writeNoException

```TypeScript
writeNoException(): void
```

向MessageSequence写入“指示未发生异常”的信息。通常在IPC/RPC通信的服务端实现以及onRemoteMessageRequest回调中调用。 - 此方法与[readException](#readexception)方法配对使用。 - 服务端在处理请求完成后，应调用writeNoException()写入未发生异常的信息。 - 客户端在收到响应后，应调用[readException](#readexception)读取异常信息。 - 如果服务端未调用writeNoException()，客户端调用[readException](#readexception)会读取失败。

**起始版本：** 23

<!--Device-MessageSequence-writeNoException(): void--><!--Device-MessageSequence-writeNoException(): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean | Promise<boolean> {
    if (code === 1) {
      hilog.info(0x0000, 'testTag', 'RpcServer: onRemoteMessageRequest called');
      try {
        reply.writeNoException();
      } catch (error) {
        let e: BusinessError = error as BusinessError;
        hilog.error(0x0000, 'testTag', 'rpc write no exception fail, errorCode ' + e.code);
        hilog.error(0x0000, 'testTag', 'rpc write no exception fail, errorMessage ' + e.message);
      }
      return true;
    } else {
      hilog.error(0x0000, 'testTag', 'RpcServer: unknown code: ' + code);
      return false;
    }
  }
}
```

## writeParcelable

```TypeScript
writeParcelable(val: Parcelable): void
```

将自定义序列化对象写入MessageSequence实例。调用此方法后，会调用Parcelable对象的marshalling方法，将对象的成员变量逐个序列化写入MessageSequence。该方法支持传输自定义数据结构对象 适用于传输复杂数据结构、业务对象、配置信息等场景。 - Parcelable接口定义了序列化和反序列化的标准方法。 - marshalling负责将对象状态写入MessageSequence。 - unmarshalling负责从MessageSequence恢复对象状态。 - 业务需自行实现具体的序列化逻辑。 - 必须传入实现了Parcelable接口的对象。 - marshalling方法必须正确实现所有成员变量的写入。 - 序列化顺序必须与反序列化顺序一致。 - 建议在marshalling中处理异常情况。 - 复杂对象可能占用较多缓冲区空间。

**起始版本：** 23

<!--Device-MessageSequence-writeParcelable(val: Parcelable): void--><!--Device-MessageSequence-writeParcelable(val: Parcelable): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | [Parcelable](arkts-ipc-rpc-parcelable-i.md) | 是 | 要写入的可序列对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

class MyParcelable implements rpc.Parcelable {
  num: number = 0;
  str: string = '';
  constructor( num: number, str: string) {
    this.num = num;
    this.str = str;
  }
  marshalling(messageSequence: rpc.MessageSequence): boolean {
    messageSequence.writeInt(this.num);
    messageSequence.writeString(this.str);
    return true;
  }
  unmarshalling(messageSequence: rpc.MessageSequence): boolean {
    this.num = messageSequence.readInt();
    this.str = messageSequence.readString();
    return true;
  }
}

try {
  let parcelable = new MyParcelable(1, "aaa");
  let data = rpc.MessageSequence.create();
  data.writeParcelable(parcelable);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## writeParcelableArray

```TypeScript
writeParcelableArray(parcelableArray: Parcelable[]): void
```

将可序列化对象数组写入MessageSequence实例。适用于批量传输多个自定义数据结构对象的场景，如传输多条业务记录、批量配置信息、多个实体对象等。 - 必须与[readParcelableArray](#readparcelablearray)配对使用。 - 读取数组长度必须与写入数组长度一致。

**起始版本：** 23

<!--Device-MessageSequence-writeParcelableArray(parcelableArray: Parcelable[]): void--><!--Device-MessageSequence-writeParcelableArray(parcelableArray: Parcelable[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parcelableArray | [Parcelable](arkts-ipc-rpc-parcelable-i.md)[] | 是 | 要写入的可序列化对象数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match; 4.The element does not exist in the array. |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

class MyParcelable implements rpc.Parcelable {
  num: number = 0;
  str: string = '';
  constructor(num: number, str: string) {
    this.num = num;
    this.str = str;
  }
  marshalling(messageSequence: rpc.MessageSequence): boolean {
    messageSequence.writeInt(this.num);
    messageSequence.writeString(this.str);
    return true;
  }
  unmarshalling(messageSequence: rpc.MessageSequence): boolean {
    this.num = messageSequence.readInt();
    this.str = messageSequence.readString();
    return true;
  }
}

try {
  let parcelable = new MyParcelable(1, "aaa");
  let parcelable2 = new MyParcelable(2, "bbb");
  let parcelable3 = new MyParcelable(3, "ccc");
  let a = [parcelable, parcelable2, parcelable3];
  let data = rpc.MessageSequence.create();
  data.writeParcelableArray(a);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'rpc write parcelable array fail, errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'rpc write parcelable array fail, errorMessage ' + e.message);
}
```

## writeRawData

```TypeScript
writeRawData(rawData: number[], size: number): void
```

将原始数据写入MessageSequence对象。 > **说明：** > > 该接口是一次性接口，不允许在一次parcel通信中多次调用该接口。 > > 该接口在传输数据时，当数据量较大时（超过32KB），会使用共享内存传输数据，此时需注意selinux配置。

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [writeRawDataBuffer](#writerawdatabuffer)(rawData: ArrayBuffer, size: int)

<!--Device-MessageSequence-writeRawData(rawData: number[], size: number): void--><!--Device-MessageSequence-writeRawData(rawData: number[], size: number): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rawData | number[] | 是 | 要写入的原始数据，大小不能超过128MB。 |
| size | number | 是 | 发送的原始数据大小，以字节为单位。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match; 4.The transferred size cannot be obtained; 5.The transferred size is less than or equal to 0; 6.The element does not exist in the array; 7.Failed to obtain typedArray information; 8.The array is not of type int32; 9.The length of typedarray is smaller than the size of the original data sent. |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let sequence = rpc.MessageSequence.create();
  let arr = [1, 2, 3, 4, 5];
  sequence.writeRawData(arr, arr.length);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## writeRawDataBuffer

```TypeScript
writeRawDataBuffer(rawData: ArrayBuffer, size: int): void
```

将原始数据写入MessageSequence对象。 > **说明：** > > 该接口是一次性接口，不允许在一次parcel通信中多次调用该接口。 > > 该接口在传输数据时，当数据量较大时（超过32KB），会使用共享内存传输数据，此时需注意selinux配置。

**起始版本：** 23

<!--Device-MessageSequence-writeRawDataBuffer(rawData: ArrayBuffer, size: int): void--><!--Device-MessageSequence-writeRawDataBuffer(rawData: ArrayBuffer, size: int): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rawData | ArrayBuffer | 是 | 要写入的原始数据，大小不能超过128MB。 |
| size | int | 是 | 发送的原始数据大小，以字节为单位。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.Failed to obtain arrayBuffer information; 4.The transferred size cannot be obtained; 5.The transferred size is less than or equal to 0; 6.The transferred size is greater than the byte length of ArrayBuffer. |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let buffer = new ArrayBuffer(64 * 1024);
  let int32View = new Int32Array(buffer);
  for (let i = 0; i < int32View.length; i++) {
    int32View[i] = i * 2 + 1;
  }
  let size = buffer.byteLength;
  let sequence = rpc.MessageSequence.create();
  sequence.writeRawDataBuffer(buffer, size);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## writeRemoteObject

```TypeScript
writeRemoteObject(obj: IRemoteObject): void
```

序列化远程对象并将其写入[MessageSequence](#messagesequence)对象。调用此方法后，IRemoteObject对象会被序列化为特定格式并存入MessageSequence的缓冲区 中，同时会更新内部写指针位置。该序列化对象可在接收端通过readRemoteObject方法反序列化读取。 - 只能写入有效的IRemoteObject对象，传入无效对象会抛出异常。 - 序列化后的对象占用固定大小的缓冲区空间。 - 写入的对象必须与对应的readRemoteObject方法配对使用。

**起始版本：** 23

<!--Device-MessageSequence-writeRemoteObject(obj: IRemoteObject): void--><!--Device-MessageSequence-writeRemoteObject(obj: IRemoteObject): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| obj | [IRemoteObject](arkts-ipc-rpc-iremoteobject-c.md) | 是 | 要序列化并写入MessageSequence的远程对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900008](../errorcode-rpc.md#1900008-非法的ipc对象) | The proxy or remote object is invalid. |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean | Promise<boolean> {
    // 根据业务实际逻辑，进行相应处理
    return true;
  }
}

try {
  let data = rpc.MessageSequence.create();
  let testRemoteObject = new TestRemoteObject("testObject");
  data.writeRemoteObject(testRemoteObject);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## writeRemoteObjectArray

```TypeScript
writeRemoteObjectArray(objectArray: IRemoteObject[]): void
```

将IRemoteObject对象数组写入MessageSequence。适用于需要传递多个远程对象的场景，如批量注册多个服务代理、传递多个回调接口、多服务端点管理等。 - 必须与[readRemoteObjectArray](#readremoteobjectarray)配对使用。 - 读取数组长度必须与写入数组长度一致。

**起始版本：** 23

<!--Device-MessageSequence-writeRemoteObjectArray(objectArray: IRemoteObject[]): void--><!--Device-MessageSequence-writeRemoteObjectArray(objectArray: IRemoteObject[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| objectArray | [IRemoteObject](arkts-ipc-rpc-iremoteobject-c.md)[] | 是 | 要写入MessageSequence的IRemoteObject对象数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match; 4.The element does not exist in the array; 5.The obtained remoteObject is null. |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean | Promise<boolean> {
    // 根据业务实际逻辑，进行相应处理
    return true;
  }
}

try {
  let a = [new TestRemoteObject("testObject1"), new TestRemoteObject("testObject2"), new TestRemoteObject("testObject3")];
  let data = rpc.MessageSequence.create();
  data.writeRemoteObjectArray(a);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## writeShort

```TypeScript
writeShort(val: int): void
```

将短整数值写入MessageSequence实例。 - 超出范围会导致数据截断。 - 必须与[readShort](#readshort)配对使用。 - 一次写入对应一次读取。

**起始版本：** 23

<!--Device-MessageSequence-writeShort(val: int): void--><!--Device-MessageSequence-writeShort(val: int): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | int | 是 | 要写入的短整数值。取值范围：[-2^15, 2^15-1]。适用于传输小范围整数数据(如端口号、标识ID等)。超出此范围会导致数据截断或写入失败。对于0-255范围建议使用 writeByte，对于标准整数建议使用writeInt，对于大整数建议使用writeLong。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeShort(8);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## writeShortArray

```TypeScript
writeShortArray(shortArray: int[]): void
```

将短整数数组写入MessageSequence实例。 - 必须与[readShortArray](#readshortarray)配对使用。 - 读取数组长度必须与写入数组长度一致。

**起始版本：** 23

<!--Device-MessageSequence-writeShortArray(shortArray: int[]): void--><!--Device-MessageSequence-writeShortArray(shortArray: int[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shortArray | int[] | 是 | 要写入的短整数数组。数组元素取值范围[-2^15, 2^15-1]。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match; 4.The element does not exist in the array; 5.The type of the element in the array is incorrect. |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeShortArray([11, 12, 13]);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## writeString

```TypeScript
writeString(val: string): void
```

将字符串值写入MessageSequence实例。调用此方法后，字符串会被序列化存入缓冲区。写入时会先存储字符串长度，再存储字节数据。 - 此方法与[readString](#readstring)方法配对使用。 - 先写入长度，再写入内容。 - 支持多语言字符集。 - 长度信息便于[readString](#readstring)确定读取边界。 - 注意区分字符数和字节数，中文字符占用更多字节。 - 长字符串会占用较多缓冲区空间。 - 空字符串也可以正常写入。

**起始版本：** 23

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MessageSequence-writeString(val: string): void--><!--Device-MessageSequence-writeString(val: string): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | string | 是 | 要写入的字符串值，其长度应小于40960。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.The string length is greater than or equal to 40960; 4.The number of bytes copied to the buffer is different from the length of the obtained string. |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |

**示例**

```TypeScript
// 在原子化服务中，本示例仅用于说明writeString()接口的使用方法，示例中rpc.MessageSequence.create()暂不支持在原子化服务中调用。
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeString('abc');
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## writeStringArray

```TypeScript
writeStringArray(stringArray: string[]): void
```

将字符串数组写入MessageSequence实例。 - 必须与[readStringArray](#readstringarray)配对使用。 - 读取数组长度必须与写入数组长度一致。

**起始版本：** 23

<!--Device-MessageSequence-writeStringArray(stringArray: string[]): void--><!--Device-MessageSequence-writeStringArray(stringArray: string[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| stringArray | string[] | 是 | 要写入的字符串数组，数组单个元素的长度应小于40960。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match; 4.The string length is greater than or equal to 40960; 5.The number of bytes copied to the buffer is different from the length of the obtained string. |
| [1900009](../errorcode-rpc.md#1900009-向messagesequence写入数据失败) | Failed to write data to the message sequence. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  data.writeStringArray(["abc", "def"]);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

