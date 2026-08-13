# MessageParcel

在RPC过程中，发送方可以使用MessageParcel提供的写方法，将待发送的数据以特定格式写入该对象。接收方可以使用MessageParcel提供的读方法从该对象中读取特定格式的数据。数据格式包括：基础类型及数组、IPC对象、 接口描述符和自定义序列化对象。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [MessageSequence](arkts-ipc-rpc-messagesequence-c.md#MessageSequence)

<!--Device-rpc-class MessageParcel--><!--Device-rpc-class MessageParcel-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## closeFileDescriptor

```TypeScript
static closeFileDescriptor(fd: number): void
```

静态方法，关闭给定的文件描述符。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [closeFileDescriptor](arkts-ipc-rpc-messagesequence-c.md#closeFileDescriptor)(fd: int)

<!--Device-MessageParcel-static closeFileDescriptor(fd: number): void--><!--Device-MessageParcel-static closeFileDescriptor(fd: number): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 要关闭的文件描述符。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { fileIo } from '@kit.CoreFileKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let filePath = "path/to/file";
  let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
  rpc.MessageParcel.closeFileDescriptor(file.fd);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## containFileDescriptors

```TypeScript
containFileDescriptors(): boolean
```

检查此MessageParcel对象是否包含文件描述符。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [containFileDescriptors](arkts-ipc-rpc-messagesequence-c.md#containFileDescriptors)()

<!--Device-MessageParcel-containFileDescriptors(): boolean--><!--Device-MessageParcel-containFileDescriptors(): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：包含文件描述符，false：未包含文件描述符。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { fileIo } from '@kit.CoreFileKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let parcel = new rpc.MessageParcel();
  let filePath = "path/to/file";
  let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
  let writeResult = parcel.writeFileDescriptor(file.fd);
  hilog.info(0x0000, 'testTag', 'parcel writeFd result is ' + writeResult);
  let containFD = parcel.containFileDescriptors();
  hilog.info(0x0000, 'testTag', 'parcel after write fd containFd result is ' + containFD);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## create

```TypeScript
static create(): MessageParcel
```

静态方法，创建MessageParcel对象。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [create](arkts-ipc-rpc-messagesequence-c.md#create)()

<!--Device-MessageParcel-static create(): MessageParcel--><!--Device-MessageParcel-static create(): MessageParcel-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MessageParcel](arkts-ipc-rpc-messageparcel-c.md) | 返回创建的MessageParcel对象，用于在IPC过程中封装请求和响应数据。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  hilog.info(0x0000, 'testTag', 'data is ' + data);

  // 当MessageParcel对象不再使用，由业务主动调用reclaim方法去释放资源。
  data.reclaim();
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## dupFileDescriptor

```TypeScript
static dupFileDescriptor(fd: number): number
```

静态方法，复制给定的文件描述符。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [dupFileDescriptor](arkts-ipc-rpc-messagesequence-c.md#dupFileDescriptor)(fd: int)

<!--Device-MessageParcel-static dupFileDescriptor(fd: number): number--><!--Device-MessageParcel-static dupFileDescriptor(fd: number): number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 表示已存在的文件描述符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回新的文件描述符。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { fileIo } from '@kit.CoreFileKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let filePath = "path/to/file";
  let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
  rpc.MessageParcel.dupFileDescriptor(file.fd);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## getCapacity

```TypeScript
getCapacity(): number
```

获取当前MessageParcel的容量。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [getCapacity](arkts-ipc-rpc-messagesequence-c.md#getCapacity)()

<!--Device-MessageParcel-getCapacity(): number--><!--Device-MessageParcel-getCapacity(): number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 获取的MessageParcel的容量大小。以字节为单位。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.getCapacity();
  hilog.info(0x0000, 'testTag', 'capacity is ' + result);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## getRawDataCapacity

```TypeScript
getRawDataCapacity(): number
```

获取MessageParcel可以容纳的最大原始数据量。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [getRawDataCapacity](arkts-ipc-rpc-messagesequence-c.md#getRawDataCapacity)()

<!--Device-MessageParcel-getRawDataCapacity(): number--><!--Device-MessageParcel-getRawDataCapacity(): number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回MessageParcel可以容纳的最大原始数据量，即128MB。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let parcel = new rpc.MessageParcel();
  let result = parcel.getRawDataCapacity();
  hilog.info(0x0000, 'testTag', 'parcel get RawDataCapacity result is ' + result);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## getReadPosition

```TypeScript
getReadPosition(): number
```

获取MessageParcel的读位置。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [getReadPosition](arkts-ipc-rpc-messagesequence-c.md#getReadPosition)()

<!--Device-MessageParcel-getReadPosition(): number--><!--Device-MessageParcel-getReadPosition(): number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回MessageParcel实例中的当前读取位置。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let readPos = data.getReadPosition();
  hilog.info(0x0000, 'testTag', 'readPos is ' + readPos);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## getReadableBytes

```TypeScript
getReadableBytes(): number
```

获取MessageParcel的可读字节空间。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [getReadableBytes](arkts-ipc-rpc-messagesequence-c.md#getReadableBytes)()

<!--Device-MessageParcel-getReadableBytes(): number--><!--Device-MessageParcel-getReadableBytes(): number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 获取到的MessageParcel的可读字节空间。以字节为单位。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  data.writeInt(1);
  let result = data.getReadableBytes();
  hilog.info(0x0000, 'testTag', 'RpcServer: getReadableBytes is ' + result);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## getSize

```TypeScript
getSize(): number
```

获取当前MessageParcel的数据大小。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [getSize](arkts-ipc-rpc-messagesequence-c.md#getSize)()

<!--Device-MessageParcel-getSize(): number--><!--Device-MessageParcel-getSize(): number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 获取的MessageParcel的数据大小。以字节为单位。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  data.writeInt(1);
  let size = data.getSize();
  hilog.info(0x0000, 'testTag', 'size is ' + size);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## getWritableBytes

```TypeScript
getWritableBytes(): number
```

获取MessageParcel的可写字节空间。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [getWritableBytes](arkts-ipc-rpc-messagesequence-c.md#getWritableBytes)()

<!--Device-MessageParcel-getWritableBytes(): number--><!--Device-MessageParcel-getWritableBytes(): number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 获取到的MessageParcel的可写字节空间。以字节为单位。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  data.writeInt(1);
  let getWritableBytes = data.getWritableBytes();
  hilog.info(0x0000, 'testTag', 'RpcServer: getWritableBytes is ' + getWritableBytes);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## getWritePosition

```TypeScript
getWritePosition(): number
```

获取MessageParcel的写位置。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [getWritePosition](arkts-ipc-rpc-messagesequence-c.md#getWritePosition)()

<!--Device-MessageParcel-getWritePosition(): number--><!--Device-MessageParcel-getWritePosition(): number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回MessageParcel实例中的当前写入位置。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  data.writeInt(10);
  let bwPos = data.getWritePosition();
  hilog.info(0x0000, 'testTag', 'bwPos is ' + bwPos);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readAshmem

```TypeScript
readAshmem(): Ashmem
```

从MessageParcel读取匿名共享对象。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [readAshmem](arkts-ipc-rpc-messagesequence-c.md#readAshmem)()

<!--Device-MessageParcel-readAshmem(): Ashmem--><!--Device-MessageParcel-readAshmem(): Ashmem-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Ashmem](arkts-ipc-rpc-ashmem-c.md) | 返回匿名共享对象。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let parcel = new rpc.MessageParcel();
  let ashmem = rpc.Ashmem.createAshmem("ashmem", 1024);
  let isWriteSuccess = parcel.writeAshmem(ashmem);
  hilog.info(0x0000, 'testTag', 'write ashmem to result is ' + isWriteSuccess);
  let readAshmem = parcel.readAshmem();
  hilog.info(0x0000, 'testTag', 'read ashmem to result is ' + readAshmem);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readBoolean

```TypeScript
readBoolean(): boolean
```

从MessageParcel实例中读取布尔值。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [readBoolean](arkts-ipc-rpc-messagesequence-c.md#readBoolean)()

<!--Device-MessageParcel-readBoolean(): boolean--><!--Device-MessageParcel-readBoolean(): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回读取到的布尔值。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeBoolean(false);
  hilog.info(0x0000, 'testTag', 'writeBoolean is ' + result);
  let ret = data.readBoolean();
  hilog.info(0x0000, 'testTag', 'readBoolean is ' + ret);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readBooleanArray

```TypeScript
readBooleanArray(dataIn: boolean[]): void
```

从MessageParcel实例中读取布尔数组，并将其写入到创建的空数组中。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [readBooleanArray](arkts-ipc-rpc-messagesequence-c.md#readBooleanArray)(dataIn: boolean[])

<!--Device-MessageParcel-readBooleanArray(dataIn: boolean[]): void--><!--Device-MessageParcel-readBooleanArray(dataIn: boolean[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataIn | boolean[] | 是 | 要读取的布尔数组。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeBooleanArray([false, true, false]);
  hilog.info(0x0000, 'testTag', 'writeBooleanArray is ' + result);
  let array: Array<boolean> = new Array(3);
  data.readBooleanArray(array);
  hilog.info(0x0000, 'testTag', 'readBooleanArray is ' + array);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readBooleanArray

```TypeScript
readBooleanArray(): boolean[]
```

从MessageParcel实例中读取布尔数组。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [readBooleanArray](arkts-ipc-rpc-messagesequence-c.md#readBooleanArray)()

<!--Device-MessageParcel-readBooleanArray(): boolean[]--><!--Device-MessageParcel-readBooleanArray(): boolean[]-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean[] | 返回布尔数组。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeBooleanArray([false, true, false]);
  hilog.info(0x0000, 'testTag', 'writeBooleanArray is ' + result);
  let array = data.readBooleanArray();
  hilog.info(0x0000, 'testTag', 'readBooleanArray is ' + array);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readByte

```TypeScript
readByte(): number
```

从MessageParcel实例中读取字节值。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [readByte](arkts-ipc-rpc-messagesequence-c.md#readByte)()

<!--Device-MessageParcel-readByte(): number--><!--Device-MessageParcel-readByte(): number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回字节值。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeByte(2);
  hilog.info(0x0000, 'testTag', 'writeByte is ' + result);
  let ret = data.readByte();
  hilog.info(0x0000, 'testTag', 'readByte is ' + ret);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readByteArray

```TypeScript
readByteArray(dataIn: number[]): void
```

从MessageParcel实例中读取字节数组，并将其写入到创建的空数组中。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [readByteArray](arkts-ipc-rpc-messagesequence-c.md#readByteArray)(dataIn: int[])

<!--Device-MessageParcel-readByteArray(dataIn: number[]): void--><!--Device-MessageParcel-readByteArray(dataIn: number[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataIn | number[] | 是 | 要读取的字节数组。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let ByteArrayVar = [1, 2, 3, 4, 5];
  let result = data.writeByteArray(ByteArrayVar);
  let array: Array<number> = new Array(5);
  data.readByteArray(array);
  hilog.info(0x0000, 'testTag', 'readByteArray is ' + array);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readByteArray

```TypeScript
readByteArray(): number[]
```

从MessageParcel实例中读取字节数组。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [readByteArray](arkts-ipc-rpc-messagesequence-c.md#readByteArray)()

<!--Device-MessageParcel-readByteArray(): number[]--><!--Device-MessageParcel-readByteArray(): number[]-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number[] | 返回字节数组。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let ByteArrayVar = [1, 2, 3, 4, 5];
  let result = data.writeByteArray(ByteArrayVar);
  hilog.info(0x0000, 'testTag', 'writeByteArray is ' + result);
  let array = data.readByteArray();
  hilog.info(0x0000, 'testTag', 'readByteArray is ' + array);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readChar

```TypeScript
readChar(): number
```

从MessageParcel实例中读取单个字符值。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [readChar](arkts-ipc-rpc-messagesequence-c.md#readChar)()

<!--Device-MessageParcel-readChar(): number--><!--Device-MessageParcel-readChar(): number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回单个字符值。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeChar(97);
  hilog.info(0x0000, 'testTag', 'writeChar is ' + result);
  let ret = data.readChar();
  hilog.info(0x0000, 'testTag', 'readChar is ' + ret);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readCharArray

```TypeScript
readCharArray(dataIn: number[]): void
```

从MessageParcel实例中读取单个字符数组，并将其写入到创建的空数组中。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [readCharArray](arkts-ipc-rpc-messagesequence-c.md#readCharArray)(dataIn: int[])

<!--Device-MessageParcel-readCharArray(dataIn: number[]): void--><!--Device-MessageParcel-readCharArray(dataIn: number[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataIn | number[] | 是 | 要读取的单个字符数组。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeCharArray([97, 98, 99]);
  hilog.info(0x0000, 'testTag', 'writeCharArray is ' + result);
  let array: Array<number> = new Array(3);
  data.readCharArray(array);
  hilog.info(0x0000, 'testTag', 'writeCharArray is ' + result);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readCharArray

```TypeScript
readCharArray(): number[]
```

从MessageParcel实例中读取单个字符数组。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [readCharArray](arkts-ipc-rpc-messagesequence-c.md#readCharArray)()

<!--Device-MessageParcel-readCharArray(): number[]--><!--Device-MessageParcel-readCharArray(): number[]-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number[] | 返回单个字符数组。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeCharArray([97, 98, 99]);
  hilog.info(0x0000, 'testTag', 'writeCharArray is ' + result);
  let array = data.readCharArray();
  hilog.info(0x0000, 'testTag', 'readCharArray is ' + array);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readDouble

```TypeScript
readDouble(): number
```

从MessageParcel实例中读取双精度浮点值。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [readDouble](arkts-ipc-rpc-messagesequence-c.md#readDouble)()

<!--Device-MessageParcel-readDouble(): number--><!--Device-MessageParcel-readDouble(): number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回双精度浮点值。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeDouble(10.2);
  hilog.info(0x0000, 'testTag', 'writeDouble is ' + result);
  let ret = data.readDouble();
  hilog.info(0x0000, 'testTag', 'readDouble is ' + ret);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readDoubleArray

```TypeScript
readDoubleArray(dataIn: number[]): void
```

从MessageParcel实例中读取双精度浮点数组，并将其写入到创建的空数组中。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [readDoubleArray](arkts-ipc-rpc-messagesequence-c.md#readDoubleArray)(dataIn: double[])

<!--Device-MessageParcel-readDoubleArray(dataIn: number[]): void--><!--Device-MessageParcel-readDoubleArray(dataIn: number[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataIn | number[] | 是 | 要读取的双精度浮点数组。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeDoubleArray([11.1, 12.2, 13.3]);
  hilog.info(0x0000, 'testTag', 'writeDoubleArray is ' + result);
  let array: Array<number> = new Array(3);
  data.readDoubleArray(array);
  hilog.info(0x0000, 'testTag', 'readDoubleArray is ' + array);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readDoubleArray

```TypeScript
readDoubleArray(): number[]
```

从MessageParcel实例中读取双精度浮点数组。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [readDoubleArray](arkts-ipc-rpc-messagesequence-c.md#readDoubleArray)()

<!--Device-MessageParcel-readDoubleArray(): number[]--><!--Device-MessageParcel-readDoubleArray(): number[]-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number[] | 返回双精度浮点数组。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeDoubleArray([11.1, 12.2, 13.3]);
  hilog.info(0x0000, 'testTag', 'writeDoubleArray is ' + result);
  let array = data.readDoubleArray();
  hilog.info(0x0000, 'testTag', 'readDoubleArray is ' + array);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readException

```TypeScript
readException(): void
```

从MessageParcel中读取异常。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [readException](arkts-ipc-rpc-messagesequence-c.md#readException)()

<!--Device-MessageParcel-readException(): void--><!--Device-MessageParcel-readException(): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## 示例

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

上述onConnect回调函数中的proxy对象需要等ability异步连接成功后才会被赋值，然后才可调用proxy对象的sendRequest接口方法发送消息

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let option = new rpc.MessageOption();
  let data = rpc.MessageParcel.create();
  let reply = rpc.MessageParcel.create();
  data.writeNoException();
  data.writeString('hello');
  if (proxy != undefined) {
    let a = proxy.sendRequest(1, data, reply, option) as Object;
    let b = a as Promise<rpc.SendRequestResult>;
    b.then((result: rpc.SendRequestResult) => {
      if (result.errCode === 0) {
        hilog.info(0x0000, 'testTag', 'sendRequest got result');
        result.reply.readException();
        let msg = result.reply.readString();
        hilog.info(0x0000, 'testTag', 'reply msg: ' + msg);
      } else {
        hilog.error(0x0000, 'testTag', 'sendRequest failed, errCode: ' + result.errCode);
      }
    }).catch((e: Error) => {
      hilog.error(0x0000, 'testTag', 'sendRequest got exception: ' + JSON.stringify(e));
    }).finally (() => {
      hilog.info(0x0000, 'testTag', 'sendRequest ends, reclaim parcel');
      data.reclaim();
      reply.reclaim();
    });
  }
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readFileDescriptor

```TypeScript
readFileDescriptor(): number
```

从MessageParcel中读取文件描述符。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [readFileDescriptor](arkts-ipc-rpc-messagesequence-c.md#readFileDescriptor)()

<!--Device-MessageParcel-readFileDescriptor(): number--><!--Device-MessageParcel-readFileDescriptor(): number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回文件描述符。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { fileIo } from '@kit.CoreFileKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let parcel = new rpc.MessageParcel();
  let filePath = "path/to/file";
  let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
  parcel.writeFileDescriptor(file.fd);
  let readFD = parcel.readFileDescriptor();
  hilog.info(0x0000, 'testTag', 'parcel read fd is ' + readFD);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readFloat

```TypeScript
readFloat(): number
```

从MessageParcel实例中读取双精度浮点值。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [readFloat](arkts-ipc-rpc-messagesequence-c.md#readFloat)()

<!--Device-MessageParcel-readFloat(): number--><!--Device-MessageParcel-readFloat(): number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回双精度浮点值。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeFloat(1.2);
  hilog.info(0x0000, 'testTag', 'writeFloat is ' + result);
  let ret = data.readFloat();
  hilog.info(0x0000, 'testTag', 'readFloat is ' + ret);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readFloatArray

```TypeScript
readFloatArray(dataIn: number[]): void
```

从MessageParcel实例中读取双精度浮点数组，并将其写入到创建的空数组中。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [readFloatArray](arkts-ipc-rpc-messagesequence-c.md#readFloatArray)(dataIn: double[])

<!--Device-MessageParcel-readFloatArray(dataIn: number[]): void--><!--Device-MessageParcel-readFloatArray(dataIn: number[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataIn | number[] | 是 | 要读取的双精度浮点数组。由于系统内部对float类型的数据是按照double处理的，使用时对于数组所占的总字节数应按照double类型来计算。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeFloatArray([1.2, 1.3, 1.4]);
  hilog.info(0x0000, 'testTag', 'writeFloatArray is ' + result);
  let array: Array<number> = new Array(3);
  data.readFloatArray(array);
  hilog.info(0x0000, 'testTag', 'readFloatArray is ' + array);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readFloatArray

```TypeScript
readFloatArray(): number[]
```

从MessageParcel实例中读取双精度浮点数组。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [readFloatArray](arkts-ipc-rpc-messagesequence-c.md#readFloatArray)()

<!--Device-MessageParcel-readFloatArray(): number[]--><!--Device-MessageParcel-readFloatArray(): number[]-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number[] | 返回双精度浮点数组。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeFloatArray([1.2, 1.3, 1.4]);
  hilog.info(0x0000, 'testTag', 'writeFloatArray is ' + result);
  let array = data.readFloatArray();
  hilog.info(0x0000, 'testTag', 'readFloatArray is ' + array);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readInt

```TypeScript
readInt(): number
```

从MessageParcel实例中读取整数值。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [readInt](arkts-ipc-rpc-messagesequence-c.md#readInt)()

<!--Device-MessageParcel-readInt(): number--><!--Device-MessageParcel-readInt(): number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回整数值。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeInt(10);
  hilog.info(0x0000, 'testTag', 'writeInt is ' + result);
  let ret = data.readInt();
  hilog.info(0x0000, 'testTag', 'readInt is ' + ret);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readIntArray

```TypeScript
readIntArray(dataIn: number[]): void
```

从MessageParcel实例中读取整数数组，并将其写入到创建的空数组中。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [readIntArray](arkts-ipc-rpc-messagesequence-c.md#readIntArray)(dataIn: int[])

<!--Device-MessageParcel-readIntArray(dataIn: number[]): void--><!--Device-MessageParcel-readIntArray(dataIn: number[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataIn | number[] | 是 | 要读取的整数数组。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeIntArray([100, 111, 112]);
  hilog.info(0x0000, 'testTag', 'writeIntArray is ' + result);
  let array: Array<number> = new Array(3);
  data.readIntArray(array);
  hilog.info(0x0000, 'testTag', 'readIntArray is ' + array);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readIntArray

```TypeScript
readIntArray(): number[]
```

从MessageParcel实例中读取整数数组。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [readIntArray](arkts-ipc-rpc-messagesequence-c.md#readIntArray)()

<!--Device-MessageParcel-readIntArray(): number[]--><!--Device-MessageParcel-readIntArray(): number[]-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number[] | 返回整数数组。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeIntArray([100, 111, 112]);
  hilog.info(0x0000, 'testTag', 'writeIntArray is ' + result);
  let array = data.readIntArray();
  hilog.info(0x0000, 'testTag', 'readIntArray is ' + array);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readInterfaceToken

```TypeScript
readInterfaceToken(): string
```

从MessageParcel中读取接口描述符，接口描述符按写入MessageParcel的顺序读取，本地对象可使用该信息检验本次通信。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [readInterfaceToken](arkts-ipc-rpc-messagesequence-c.md#readInterfaceToken)()

<!--Device-MessageParcel-readInterfaceToken(): string--><!--Device-MessageParcel-readInterfaceToken(): string-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回读取到的接口描述符。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeInterfaceToken("aaa");
  let interfaceToken = data.readInterfaceToken();
  hilog.info(0x0000, 'testTag', 'RpcServer: interfaceToken is ' + interfaceToken);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readLong

```TypeScript
readLong(): number
```

从MessageParcel实例中读取长整数值。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [readLong](arkts-ipc-rpc-messagesequence-c.md#readLong)()

<!--Device-MessageParcel-readLong(): number--><!--Device-MessageParcel-readLong(): number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回长整数值。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeLong(10000);
  hilog.info(0x0000, 'testTag', 'writeLong is ' + result);
  let ret = data.readLong();
  hilog.info(0x0000, 'testTag', 'readLong is ' + ret);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readLongArray

```TypeScript
readLongArray(dataIn: number[]): void
```

从MessageParcel实例中读取长整数数组，并将其写入到创建的空数组中。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [readLongArray](arkts-ipc-rpc-messagesequence-c.md#readLongArray)(dataIn: long[])

<!--Device-MessageParcel-readLongArray(dataIn: number[]): void--><!--Device-MessageParcel-readLongArray(dataIn: number[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataIn | number[] | 是 | 要读取的长整数数组。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeLongArray([1111, 1112, 1113]);
  hilog.info(0x0000, 'testTag', 'writeLongArray is ' + result);
  let array: Array<number> = new Array(3);
  data.readLongArray(array);
  hilog.info(0x0000, 'testTag', 'readLongArray is ' + array);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readLongArray

```TypeScript
readLongArray(): number[]
```

从MessageParcel实例中读取长整数数组。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [readLongArray](arkts-ipc-rpc-messagesequence-c.md#readLongArray)()

<!--Device-MessageParcel-readLongArray(): number[]--><!--Device-MessageParcel-readLongArray(): number[]-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number[] | 返回长整数数组。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeLongArray([1111, 1112, 1113]);
  hilog.info(0x0000, 'testTag', 'writeLongArray is ' + result);
  let array = data.readLongArray();
  hilog.info(0x0000, 'testTag', 'readLongArray is ' + array);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readRawData

```TypeScript
readRawData(size: number): number[]
```

从MessageParcel读取原始数据。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [readRawDataBuffer](arkts-ipc-rpc-messagesequence-c.md#readRawDataBuffer)(size: int)

<!--Device-MessageParcel-readRawData(size: number): number[]--><!--Device-MessageParcel-readRawData(size: number): number[]-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | number | 是 | 要读取的原始数据的大小，以字节为单位。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number[] | 返回原始数据（以字节为单位）。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let parcel = new rpc.MessageParcel();
  let arr = [1, 2, 3, 4, 5];
  let isWriteSuccess = parcel.writeRawData(arr, arr.length);
  hilog.info(0x0000, 'testTag', 'parcel write raw data result is ' + isWriteSuccess);
  let result = parcel.readRawData(5);
  hilog.info(0x0000, 'testTag', 'parcel read raw data result is ' + result);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readRemoteObject

```TypeScript
readRemoteObject(): IRemoteObject
```

从MessageParcel读取远程对象。此方法用于反序列化MessageParcel对象以生成IRemoteObject。远程对象按写入MessageParcel的顺序读取。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [readRemoteObject](arkts-ipc-rpc-messagesequence-c.md#readRemoteObject)()

<!--Device-MessageParcel-readRemoteObject(): IRemoteObject--><!--Device-MessageParcel-readRemoteObject(): IRemoteObject-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [IRemoteObject](arkts-ipc-rpc-iremoteobject-c.md) | 读取到的远程对象，用于IPC/RPC通信。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteRequest(code: number, data: rpc.MessageParcel, reply: rpc.MessageParcel,
    option: rpc.MessageOption): boolean {
    // 根据业务实际逻辑，进行相应处理
    return true;
  }
}

try {
  let data = rpc.MessageParcel.create();
  let testRemoteObject = new TestRemoteObject("testObject");
  data.writeRemoteObject(testRemoteObject);
  let proxy = data.readRemoteObject();
  hilog.info(0x0000, 'testTag', 'readRemoteObject is ' + proxy);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readRemoteObjectArray

```TypeScript
readRemoteObjectArray(objects: IRemoteObject[]): void
```

从MessageParcel读取IRemoteObject对象数组，并将其写入到创建的空数组中。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [readRemoteObjectArray](arkts-ipc-rpc-messagesequence-c.md#readRemoteObjectArray)(objects: IRemoteObject[])

<!--Device-MessageParcel-readRemoteObjectArray(objects: IRemoteObject[]): void--><!--Device-MessageParcel-readRemoteObjectArray(objects: IRemoteObject[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| objects | [IRemoteObject](arkts-ipc-rpc-iremoteobject-c.md)[] | 是 | 从MessageParcel读取的IRemoteObject对象数组。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteRequest(code: number, data: rpc.MessageParcel, reply: rpc.MessageParcel,
    option: rpc.MessageOption): boolean {
    // 具体处理由业务决定
    return true;
  }
}

try {
  let a = [new TestRemoteObject("testObject1"), new TestRemoteObject("testObject2"),
    new TestRemoteObject("testObject3")];
  let data = rpc.MessageParcel.create();
  data.writeRemoteObjectArray(a);
  let b: Array<rpc.IRemoteObject> = new Array(3);
  data.readRemoteObjectArray(b);
  hilog.info(0x0000, 'testTag', 'readRemoteObjectArray is ' + b);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readRemoteObjectArray

```TypeScript
readRemoteObjectArray(): IRemoteObject[]
```

从MessageParcel读取IRemoteObject对象数组。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [readRemoteObjectArray](arkts-ipc-rpc-messagesequence-c.md#readRemoteObjectArray)(objects: IRemoteObject[])

<!--Device-MessageParcel-readRemoteObjectArray(): IRemoteObject[]--><!--Device-MessageParcel-readRemoteObjectArray(): IRemoteObject[]-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [IRemoteObject](arkts-ipc-rpc-iremoteobject-c.md)[] | 返回IRemoteObject对象数组。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteRequest(code: number, data: rpc.MessageParcel, reply: rpc.MessageParcel,
    option: rpc.MessageOption): boolean {
    // 具体处理由业务决定
    return true;
  }
}

try {
  let a = [new TestRemoteObject("testObject1"), new TestRemoteObject("testObject2"),
    new TestRemoteObject("testObject3")];
  let data = rpc.MessageParcel.create();
  let result = data.writeRemoteObjectArray(a);
  hilog.info(0x0000, 'testTag', 'readRemoteObjectArray is ' + result);
  let b = data.readRemoteObjectArray();
  hilog.info(0x0000, 'testTag', 'readRemoteObjectArray is ' + b);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readSequenceable

```TypeScript
readSequenceable(dataIn: Sequenceable): boolean
```

从MessageParcel实例中读取成员变量到指定的对象（dataIn）。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [readParcelable](arkts-ipc-rpc-messagesequence-c.md#readParcelable)(dataIn: Parcelable)

<!--Device-MessageParcel-readSequenceable(dataIn: Sequenceable): boolean--><!--Device-MessageParcel-readSequenceable(dataIn: Sequenceable): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataIn | [Sequenceable](arkts-ipc-rpc-sequenceable-i.md) | 是 | 需要从MessageParcel读取成员变量的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：反序列化成功，false：反序列化失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MySequenceable implements rpc.Sequenceable {
  num: number = 0;
  str: string = '';
  constructor(num: number, str: string) {
    this.num = num;
    this.str = str;
  }
  marshalling(messageParcel: rpc.MessageParcel): boolean {
    messageParcel.writeInt(this.num);
    messageParcel.writeString(this.str);
    return true;
  }
  unmarshalling(messageParcel: rpc.MessageParcel): boolean {
    this.num = messageParcel.readInt();
    this.str = messageParcel.readString();
    return true;
  }
}

try {
  let sequenceable = new MySequenceable(1, "aaa");
  let data = rpc.MessageParcel.create();
  let result = data.writeSequenceable(sequenceable);
  hilog.info(0x0000, 'testTag', 'writeSequenceable is ' + result);
  let ret = new MySequenceable(0, "");
  let result2 = data.readSequenceable(ret);
  hilog.info(0x0000, 'testTag', 'readSequenceable is ' + result2);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readSequenceableArray

```TypeScript
readSequenceableArray(sequenceableArray: Sequenceable[]): void
```

从MessageParcel实例中读取可序列化对象数组。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [readParcelableArray](arkts-ipc-rpc-messagesequence-c.md#readParcelableArray)(parcelableArray: Parcelable[])

<!--Device-MessageParcel-readSequenceableArray(sequenceableArray: Sequenceable[]): void--><!--Device-MessageParcel-readSequenceableArray(sequenceableArray: Sequenceable[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sequenceableArray | [Sequenceable](arkts-ipc-rpc-sequenceable-i.md)[] | 是 | 要读取的可序列化对象数组。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MySequenceable implements rpc.Sequenceable {
  num: number = 0;
  str: string = '';
  constructor(num: number, str: string) {
    this.num = num;
    this.str = str;
  }
  marshalling(messageParcel: rpc.MessageParcel): boolean {
    messageParcel.writeInt(this.num);
    messageParcel.writeString(this.str);
    return true;
  }
  unmarshalling(messageParcel: rpc.MessageParcel): boolean {
    this.num = messageParcel.readInt();
    this.str = messageParcel.readString();
    return true;
  }
}

try {
  let sequenceable = new MySequenceable(1, "aaa");
  let sequenceable2 = new MySequenceable(2, "bbb");
  let sequenceable3 = new MySequenceable(3, "ccc");
  let a = [sequenceable, sequenceable2, sequenceable3];
  let data = rpc.MessageParcel.create();
  let result = data.writeSequenceableArray(a);
  hilog.info(0x0000, 'testTag', 'writeSequenceableArray is ' + result);
  let b = [new MySequenceable(0, ""), new MySequenceable(0, ""), new MySequenceable(0, "")];
  data.readSequenceableArray(b);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readShort

```TypeScript
readShort(): number
```

从MessageParcel实例中读取短整数值。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [readShort](arkts-ipc-rpc-messagesequence-c.md#readShort)()

<!--Device-MessageParcel-readShort(): number--><!--Device-MessageParcel-readShort(): number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回短整数值。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeShort(8);
  hilog.info(0x0000, 'testTag', 'writeShort is ' + result);
  let ret = data.readShort();
  hilog.info(0x0000, 'testTag', 'readShort is ' + ret);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readShortArray

```TypeScript
readShortArray(dataIn: number[]): void
```

从MessageParcel实例中读取短整数数组，并将其写入到创建的空数组中。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [readShortArray](arkts-ipc-rpc-messagesequence-c.md#readShortArray)(dataIn: int[])

<!--Device-MessageParcel-readShortArray(dataIn: number[]): void--><!--Device-MessageParcel-readShortArray(dataIn: number[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataIn | number[] | 是 | 要读取的短整数数组。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeShortArray([11, 12, 13]);
  hilog.info(0x0000, 'testTag', 'writeShortArray is ' + result);
  let array: Array<number> = new Array(3);
  data.readShortArray(array);
  hilog.info(0x0000, 'testTag', 'readShortArray is ' + array);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readShortArray

```TypeScript
readShortArray(): number[]
```

从MessageParcel实例中读取短整数数组。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [readShortArray](arkts-ipc-rpc-messagesequence-c.md#readShortArray)()

<!--Device-MessageParcel-readShortArray(): number[]--><!--Device-MessageParcel-readShortArray(): number[]-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number[] | 返回短整数数组。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeShortArray([11, 12, 13]);
  hilog.info(0x0000, 'testTag', 'writeShortArray is ' + result);
  let array = data.readShortArray();
  hilog.info(0x0000, 'testTag', 'readShortArray is ' + array);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readString

```TypeScript
readString(): string
```

从MessageParcel实例中读取字符串值。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [readString](arkts-ipc-rpc-messagesequence-c.md#readString)()

<!--Device-MessageParcel-readString(): string--><!--Device-MessageParcel-readString(): string-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回字符串值。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeString('abc');
  hilog.info(0x0000, 'testTag', 'writeString is ' + result);
  let ret = data.readString();
  hilog.info(0x0000, 'testTag', 'readString is ' + ret);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readStringArray

```TypeScript
readStringArray(dataIn: string[]): void
```

从MessageParcel实例中读取字符串数组，并将其写入到创建的空数组中。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [readStringArray](arkts-ipc-rpc-messagesequence-c.md#readStringArray)(dataIn: string[])

<!--Device-MessageParcel-readStringArray(dataIn: string[]): void--><!--Device-MessageParcel-readStringArray(dataIn: string[]): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataIn | string[] | 是 | 要读取的字符串数组。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeStringArray(["abc", "def"]);
  hilog.info(0x0000, 'testTag', 'writeStringArray is ' + result);
  let array: Array<string> = new Array(2);
  data.readStringArray(array);
  hilog.info(0x0000, 'testTag', 'readStringArray is ' + array);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## readStringArray

```TypeScript
readStringArray(): string[]
```

从MessageParcel实例中读取字符串数组。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [readStringArray](arkts-ipc-rpc-messagesequence-c.md#readStringArray)()

<!--Device-MessageParcel-readStringArray(): string[]--><!--Device-MessageParcel-readStringArray(): string[]-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string[] | 返回字符串数组。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeStringArray(["abc", "def"]);
  hilog.info(0x0000, 'testTag', 'writeStringArray is ' + result);
  let array = data.readStringArray();
  hilog.info(0x0000, 'testTag', 'readStringArray is ' + array);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## reclaim

```TypeScript
reclaim(): void
```

释放不再使用的MessageParcel对象。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [reclaim](arkts-ipc-rpc-messagesequence-c.md#reclaim)()

<!--Device-MessageParcel-reclaim(): void--><!--Device-MessageParcel-reclaim(): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let reply = rpc.MessageParcel.create();
  reply.reclaim();
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## rewindRead

```TypeScript
rewindRead(pos: number): boolean
```

重新偏移读取位置到指定的位置。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [rewindRead](arkts-ipc-rpc-messagesequence-c.md#rewindRead)(pos: int)

<!--Device-MessageParcel-rewindRead(pos: number): boolean--><!--Device-MessageParcel-rewindRead(pos: number): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pos | number | 是 | 开始读取数据的目标位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：读取位置发生更改，false：读取位置未发生更改。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  data.writeInt(12);
  data.writeString("parcel");
  let number = data.readInt();
  hilog.info(0x0000, 'testTag', 'number is ' + number);
  data.rewindRead(0);
  let number2 = data.readInt();
  hilog.info(0x0000, 'testTag', 'rewindRead is ' + number2);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## rewindWrite

```TypeScript
rewindWrite(pos: number): boolean
```

重新偏移写位置到指定的位置。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [rewindWrite](arkts-ipc-rpc-messagesequence-c.md#rewindWrite)(pos: int)

<!--Device-MessageParcel-rewindWrite(pos: number): boolean--><!--Device-MessageParcel-rewindWrite(pos: number): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pos | number | 是 | 开始写入数据的目标位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：写入位置发生更改，false：写入位置未发生更改。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  data.writeInt(4);
  data.rewindWrite(0);
  data.writeInt(5);
  let number = data.readInt();
  hilog.info(0x0000, 'testTag', 'rewindWrite is ' + number);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## setCapacity

```TypeScript
setCapacity(size: number): boolean
```

设置MessageParcel实例的存储容量。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [setCapacity](arkts-ipc-rpc-messagesequence-c.md#setCapacity)(size: int)

<!--Device-MessageParcel-setCapacity(size: number): boolean--><!--Device-MessageParcel-setCapacity(size: number): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | number | 是 | MessageParcel实例的存储容量。以字节为单位。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：设置成功，false：设置失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.setCapacity(100);
  hilog.info(0x0000, 'testTag', 'setCapacity is ' + result);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## setSize

```TypeScript
setSize(size: number): boolean
```

设置MessageParcel实例中包含的数据大小。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [setSize](arkts-ipc-rpc-messagesequence-c.md#setSize)(size: int)

<!--Device-MessageParcel-setSize(size: number): boolean--><!--Device-MessageParcel-setSize(size: number): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | number | 是 | MessageParcel实例的数据大小。以字节为单位。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：设置成功，false：设置失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let setSize = data.setSize(16);
  hilog.info(0x0000, 'testTag', 'setSize is ' + setSize);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## writeAshmem

```TypeScript
writeAshmem(ashmem: Ashmem): boolean
```

将指定的匿名共享对象写入此MessageParcel。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [writeAshmem](arkts-ipc-rpc-messagesequence-c.md#writeAshmem)(ashmem: Ashmem)

<!--Device-MessageParcel-writeAshmem(ashmem: Ashmem): boolean--><!--Device-MessageParcel-writeAshmem(ashmem: Ashmem): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ashmem | [Ashmem](arkts-ipc-rpc-ashmem-c.md) | 是 | 要写入MessageParcel的匿名共享对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：写入成功，false：写入失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let parcel = new rpc.MessageParcel();
  let ashmem = rpc.Ashmem.createAshmem("ashmem", 1024);
  let isWriteSuccess = parcel.writeAshmem(ashmem);
  hilog.info(0x0000, 'testTag', 'write ashmem to result is ' + isWriteSuccess);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## writeBoolean

```TypeScript
writeBoolean(val: boolean): boolean
```

将布尔值写入MessageParcel实例。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [writeBoolean](arkts-ipc-rpc-messagesequence-c.md#writeBoolean)(val: boolean)

<!--Device-MessageParcel-writeBoolean(val: boolean): boolean--><!--Device-MessageParcel-writeBoolean(val: boolean): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | boolean | 是 | 要写入的布尔值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：写入成功，false：写入失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeBoolean(false);
  hilog.info(0x0000, 'testTag', 'writeBoolean is ' + result);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## writeBooleanArray

```TypeScript
writeBooleanArray(booleanArray: boolean[]): boolean
```

将布尔数组写入MessageParcel实例。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [writeBooleanArray](arkts-ipc-rpc-messagesequence-c.md#writeBooleanArray)(booleanArray: boolean[])

<!--Device-MessageParcel-writeBooleanArray(booleanArray: boolean[]): boolean--><!--Device-MessageParcel-writeBooleanArray(booleanArray: boolean[]): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| booleanArray | boolean[] | 是 | 要写入的布尔数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：写入成功，false：写入失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeBooleanArray([false, true, false]);
  hilog.info(0x0000, 'testTag', 'writeBooleanArray is ' + result);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## writeByte

```TypeScript
writeByte(val: number): boolean
```

将字节值写入MessageParcel实例。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [writeByte](arkts-ipc-rpc-messagesequence-c.md#writeByte)(val: int)

<!--Device-MessageParcel-writeByte(val: number): boolean--><!--Device-MessageParcel-writeByte(val: number): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | number | 是 | 要写入的字节值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：写入成功，false：写入失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeByte(2);
  hilog.info(0x0000, 'testTag', 'writeByte is ' + result);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## writeByteArray

```TypeScript
writeByteArray(byteArray: number[]): boolean
```

将字节数组写入MessageParcel实例。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [writeByteArray](arkts-ipc-rpc-messagesequence-c.md#writeByteArray)(byteArray: int[])

<!--Device-MessageParcel-writeByteArray(byteArray: number[]): boolean--><!--Device-MessageParcel-writeByteArray(byteArray: number[]): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| byteArray | number[] | 是 | 要写入的字节数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：写入成功，false：写入失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let ByteArrayVar = [1, 2, 3, 4, 5];
  let result = data.writeByteArray(ByteArrayVar);
  hilog.info(0x0000, 'testTag', 'writeByteArray is ' + result);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## writeChar

```TypeScript
writeChar(val: number): boolean
```

将单个字符值写入MessageParcel实例。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [writeChar](arkts-ipc-rpc-messagesequence-c.md#writeChar)(val: int)

<!--Device-MessageParcel-writeChar(val: number): boolean--><!--Device-MessageParcel-writeChar(val: number): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | number | 是 | 要写入的单个字符值。取值范围：[0, 65535]，对应Unicode字符编码范围。超出此范围可能导致字符编码异常。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：写入成功，false：写入失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeChar(97);
  hilog.info(0x0000, 'testTag', 'writeChar is ' + result);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## writeCharArray

```TypeScript
writeCharArray(charArray: number[]): boolean
```

将单个字符数组写入MessageParcel实例。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [writeCharArray](arkts-ipc-rpc-messagesequence-c.md#writeCharArray)(charArray: int[])

<!--Device-MessageParcel-writeCharArray(charArray: number[]): boolean--><!--Device-MessageParcel-writeCharArray(charArray: number[]): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| charArray | number[] | 是 | 要写入的单个字符数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：写入成功，false：写入失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeCharArray([97, 98, 88]);
  hilog.info(0x0000, 'testTag', 'writeCharArray is ' + result);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## writeDouble

```TypeScript
writeDouble(val: number): boolean
```

将双精度浮点值写入MessageParcel实例。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [writeDouble](arkts-ipc-rpc-messagesequence-c.md#writeDouble)(val: double)

<!--Device-MessageParcel-writeDouble(val: number): boolean--><!--Device-MessageParcel-writeDouble(val: number): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | number | 是 | 要写入的双精度浮点值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：写入成功，false：写入失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeDouble(10.2);
  hilog.info(0x0000, 'testTag', 'writeDouble is ' + result);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## writeDoubleArray

```TypeScript
writeDoubleArray(doubleArray: number[]): boolean
```

将双精度浮点数组写入MessageParcel实例。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [writeDoubleArray](arkts-ipc-rpc-messagesequence-c.md#writeDoubleArray)(doubleArray: double[])

<!--Device-MessageParcel-writeDoubleArray(doubleArray: number[]): boolean--><!--Device-MessageParcel-writeDoubleArray(doubleArray: number[]): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| doubleArray | number[] | 是 | 要写入的双精度浮点数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：写入成功，false：写入失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeDoubleArray([11.1, 12.2, 13.3]);
  hilog.info(0x0000, 'testTag', 'writeDoubleArray is ' + result);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## writeFileDescriptor

```TypeScript
writeFileDescriptor(fd: number): boolean
```

写入文件描述符到MessageParcel。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [writeFileDescriptor](arkts-ipc-rpc-messagesequence-c.md#writeFileDescriptor)(fd: int)

<!--Device-MessageParcel-writeFileDescriptor(fd: number): boolean--><!--Device-MessageParcel-writeFileDescriptor(fd: number): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 文件描述符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：操作成功，false：操作失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { fileIo } from '@kit.CoreFileKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let parcel = new rpc.MessageParcel();
  let filePath = "path/to/file";
  let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
  let writeResult = parcel.writeFileDescriptor(file.fd);
  hilog.info(0x0000, 'testTag', 'parcel writeFd result is ' + writeResult);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## writeFloat

```TypeScript
writeFloat(val: number): boolean
```

将双精度浮点值写入MessageParcel实例。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [writeFloat](arkts-ipc-rpc-messagesequence-c.md#writeFloat)(val: double)

<!--Device-MessageParcel-writeFloat(val: number): boolean--><!--Device-MessageParcel-writeFloat(val: number): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | number | 是 | 要写入的双精度浮点值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：写入成功，false：写入失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeFloat(1.2);
  hilog.info(0x0000, 'testTag', 'writeFloat is ' + result);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## writeFloatArray

```TypeScript
writeFloatArray(floatArray: number[]): boolean
```

将双精度浮点数组写入MessageParcel实例。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [writeFloatArray](arkts-ipc-rpc-messagesequence-c.md#writeFloatArray)(floatArray: double[])

<!--Device-MessageParcel-writeFloatArray(floatArray: number[]): boolean--><!--Device-MessageParcel-writeFloatArray(floatArray: number[]): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| floatArray | number[] | 是 | 要写入的双精度浮点数组。由于系统内部对float类型的数据是按照double处理的，使用时对于数组所占的总字节数应按照double类型来计算。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：写入成功，false：写入失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeFloatArray([1.2, 1.3, 1.4]);
  hilog.info(0x0000, 'testTag', 'writeFloatArray is ' + result);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## writeInt

```TypeScript
writeInt(val: number): boolean
```

将整数值写入MessageParcel实例。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [writeInt](arkts-ipc-rpc-messagesequence-c.md#writeInt)(val: int)

<!--Device-MessageParcel-writeInt(val: number): boolean--><!--Device-MessageParcel-writeInt(val: number): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | number | 是 | 要写入的整数值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：写入成功，false：写入失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeInt(10);
  hilog.info(0x0000, 'testTag', 'writeInt is ' + result);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## writeIntArray

```TypeScript
writeIntArray(intArray: number[]): boolean
```

将整数数组写入MessageParcel实例。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [writeIntArray](arkts-ipc-rpc-messagesequence-c.md#writeIntArray)(intArray: int[])

<!--Device-MessageParcel-writeIntArray(intArray: number[]): boolean--><!--Device-MessageParcel-writeIntArray(intArray: number[]): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| intArray | number[] | 是 | 要写入的整数数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：写入成功，false：写入失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeIntArray([100, 111, 112]);
  hilog.info(0x0000, 'testTag', 'writeIntArray is ' + result);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## writeInterfaceToken

```TypeScript
writeInterfaceToken(token: string): boolean
```

将接口描述符写入MessageParcel对象，远端对象可使用该信息校验本次通信。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [writeInterfaceToken](arkts-ipc-rpc-messagesequence-c.md#writeInterfaceToken)(token: string)

<!--Device-MessageParcel-writeInterfaceToken(token: string): boolean--><!--Device-MessageParcel-writeInterfaceToken(token: string): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| token | string | 是 | 字符串类型描述符，其长度应小于40960。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：操作成功，false：操作失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeInterfaceToken("aaa");
  hilog.info(0x0000, 'testTag', 'RpcServer: writeInterfaceToken is ' + result);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## writeLong

```TypeScript
writeLong(val: number): boolean
```

将长整数值写入MessageParcel实例。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [writeLong](arkts-ipc-rpc-messagesequence-c.md#writeLong)(val: long)

<!--Device-MessageParcel-writeLong(val: number): boolean--><!--Device-MessageParcel-writeLong(val: number): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | number | 是 | 要写入的长整数值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：写入成功，false：写入失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeLong(10000);
  hilog.info(0x0000, 'testTag', 'writeLong is ' + result);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## writeLongArray

```TypeScript
writeLongArray(longArray: number[]): boolean
```

将长整数数组写入MessageParcel实例。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [writeLongArray](arkts-ipc-rpc-messagesequence-c.md#writeLongArray)(longArray: long[])

<!--Device-MessageParcel-writeLongArray(longArray: number[]): boolean--><!--Device-MessageParcel-writeLongArray(longArray: number[]): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| longArray | number[] | 是 | 要写入的长整数数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：写入成功，false：写入失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeLongArray([1111, 1112, 1113]);
  hilog.info(0x0000, 'testTag', 'writeLongArray is ' + result);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## writeNoException

```TypeScript
writeNoException(): void
```

向MessageParcel写入“指示未发生异常”的信息。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [writeNoException](arkts-ipc-rpc-messagesequence-c.md#writeNoException)()

<!--Device-MessageParcel-writeNoException(): void--><!--Device-MessageParcel-writeNoException(): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MyDeathRecipient implements rpc.DeathRecipient {
  onRemoteDied() {
    hilog.info(0x0000, 'testTag', 'server died');
  }
}
class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }

  onRemoteRequest(code: number, data: rpc.MessageParcel, reply: rpc.MessageParcel, option: rpc.MessageOption): boolean {
    if (code === 1) {
      hilog.info(0x0000, 'testTag', 'RpcServer: onRemoteRequest called');
      reply.writeNoException();
      return true;
    } else {
      hilog.error(0x0000, 'testTag', 'RpcServer: unknown code: ' + code);
      return false;
    }
  }
}
```

## writeRawData

```TypeScript
writeRawData(rawData: number[], size: number): boolean
```

将原始数据写入MessageParcel对象。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [writeRawDataBuffer](arkts-ipc-rpc-messagesequence-c.md#writeRawDataBuffer)(rawData: ArrayBuffer, size: int)

<!--Device-MessageParcel-writeRawData(rawData: number[], size: number): boolean--><!--Device-MessageParcel-writeRawData(rawData: number[], size: number): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rawData | number[] | 是 | 要写入的原始数据，大小不能超过128MB。 |
| size | number | 是 | 发送的原始数据大小，以字节为单位。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：写入成功，false：写入失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let parcel = new rpc.MessageParcel();
  let arr = [1, 2, 3, 4, 5];
  let isWriteSuccess = parcel.writeRawData(arr, arr.length);
  hilog.info(0x0000, 'testTag', 'parcel write raw data result is ' + isWriteSuccess);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## writeRemoteObject

```TypeScript
writeRemoteObject(object: IRemoteObject): boolean
```

序列化远程对象并将其写入MessageParcel对象。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [writeRemoteObject](arkts-ipc-rpc-messagesequence-c.md#writeRemoteObject)(obj: IRemoteObject)

<!--Device-MessageParcel-writeRemoteObject(object: IRemoteObject): boolean--><!--Device-MessageParcel-writeRemoteObject(object: IRemoteObject): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| object | [IRemoteObject](arkts-ipc-rpc-iremoteobject-c.md) | 是 | 要序列化并写入MessageParcel的远程对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：操作成功，false：操作失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteRequest(code: number, data: rpc.MessageParcel, reply: rpc.MessageParcel, option: rpc.MessageOption): boolean {
    // 根据业务实际逻辑，进行相应处理
    return true;
  }
}

try {
  let data = rpc.MessageParcel.create();
  let testRemoteObject = new TestRemoteObject("testObject");
  data.writeRemoteObject(testRemoteObject);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## writeRemoteObjectArray

```TypeScript
writeRemoteObjectArray(objectArray: IRemoteObject[]): boolean
```

将IRemoteObject对象数组写入MessageParcel。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [writeRemoteObjectArray](arkts-ipc-rpc-messagesequence-c.md#writeRemoteObjectArray)(objectArray: IRemoteObject[])

<!--Device-MessageParcel-writeRemoteObjectArray(objectArray: IRemoteObject[]): boolean--><!--Device-MessageParcel-writeRemoteObjectArray(objectArray: IRemoteObject[]): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| objectArray | [IRemoteObject](arkts-ipc-rpc-iremoteobject-c.md)[] | 是 | 要写入MessageParcel的IRemoteObject对象数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：写入成功，false：写入失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteRequest(code: number, data: rpc.MessageParcel, reply: rpc.MessageParcel,
    option: rpc.MessageOption): boolean {
    // 具体处理由业务决定
    return true;
  }
}

try {
  let a = [new TestRemoteObject("testObject1"), new TestRemoteObject("testObject2"), new TestRemoteObject("testObject3")];
  let data = rpc.MessageParcel.create();
  let result = data.writeRemoteObjectArray(a);
  hilog.info(0x0000, 'testTag', 'writeRemoteObjectArray is ' + result);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## writeSequenceable

```TypeScript
writeSequenceable(val: Sequenceable): boolean
```

将自定义序列化对象写入MessageParcel实例。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [writeParcelable](arkts-ipc-rpc-messagesequence-c.md#writeParcelable)(val: Parcelable)

<!--Device-MessageParcel-writeSequenceable(val: Sequenceable): boolean--><!--Device-MessageParcel-writeSequenceable(val: Sequenceable): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | [Sequenceable](arkts-ipc-rpc-sequenceable-i.md) | 是 | 要写入的可序列对象。建议实现marshalling和unmarshalling方法时确保数据完整性，序列化与反序列化的数据结构应保持一致。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：写入成功，false：写入失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MySequenceable implements rpc.Sequenceable {
  num: number = 0;
  str: string = '';
  constructor(num: number, str: string) {
    this.num = num;
    this.str = str;
  }
  marshalling(messageParcel: rpc.MessageParcel): boolean {
    messageParcel.writeInt(this.num);
    messageParcel.writeString(this.str);
    return true;
  }
  unmarshalling(messageParcel: rpc.MessageParcel): boolean {
    this.num = messageParcel.readInt();
    this.str = messageParcel.readString();
    return true;
  }
}

try {
  let sequenceable = new MySequenceable(1, "aaa");
  let data = rpc.MessageParcel.create();
  let result = data.writeSequenceable(sequenceable);
  hilog.info(0x0000, 'testTag', 'writeSequenceable is ' + result);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## writeSequenceableArray

```TypeScript
writeSequenceableArray(sequenceableArray: Sequenceable[]): boolean
```

将可序列化对象数组写入MessageParcel实例。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [writeParcelableArray](arkts-ipc-rpc-messagesequence-c.md#writeParcelableArray)(parcelableArray: Parcelable[])

<!--Device-MessageParcel-writeSequenceableArray(sequenceableArray: Sequenceable[]): boolean--><!--Device-MessageParcel-writeSequenceableArray(sequenceableArray: Sequenceable[]): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sequenceableArray | [Sequenceable](arkts-ipc-rpc-sequenceable-i.md)[] | 是 | 要写入的可序列化对象数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：写入成功，false：写入失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MySequenceable implements rpc.Sequenceable {
  num: number = 0;
  str: string = '';
  constructor(num: number, str: string) {
    this.num = num;
    this.str = str;
  }
  marshalling(messageParcel: rpc.MessageParcel): boolean {
    messageParcel.writeInt(this.num);
    messageParcel.writeString(this.str);
    return true;
  }
  unmarshalling(messageParcel: rpc.MessageParcel): boolean {
    this.num = messageParcel.readInt();
    this.str = messageParcel.readString();
    return true;
  }
}

try {
  let sequenceable = new MySequenceable(1, "aaa");
  let sequenceable2 = new MySequenceable(2, "bbb");
  let sequenceable3 = new MySequenceable(3, "ccc");
  let a = [sequenceable, sequenceable2, sequenceable3];
  let data = rpc.MessageParcel.create();
  let result = data.writeSequenceableArray(a);
  hilog.info(0x0000, 'testTag', 'writeSequenceableArray is ' + result);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## writeShort

```TypeScript
writeShort(val: number): boolean
```

将短整数值写入MessageParcel实例。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [writeShort](arkts-ipc-rpc-messagesequence-c.md#writeShort)(val: int)

<!--Device-MessageParcel-writeShort(val: number): boolean--><!--Device-MessageParcel-writeShort(val: number): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | number | 是 | 要写入的短整数值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：写入成功，false：写入失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeShort(8);
  hilog.info(0x0000, 'testTag', 'writeShort is ' + result);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## writeShortArray

```TypeScript
writeShortArray(shortArray: number[]): boolean
```

将短整数数组写入MessageParcel实例。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [writeShortArray](arkts-ipc-rpc-messagesequence-c.md#writeShortArray)(shortArray: int[])

<!--Device-MessageParcel-writeShortArray(shortArray: number[]): boolean--><!--Device-MessageParcel-writeShortArray(shortArray: number[]): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shortArray | number[] | 是 | 要写入的短整数数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：写入成功，false：写入失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeShortArray([11, 12, 13]);
  hilog.info(0x0000, 'testTag', 'writeShortArray is ' + result);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## writeString

```TypeScript
writeString(val: string): boolean
```

将字符串值写入MessageParcel实例。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [writeString](arkts-ipc-rpc-messagesequence-c.md#writeString)(val: string)

<!--Device-MessageParcel-writeString(val: string): boolean--><!--Device-MessageParcel-writeString(val: string): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | string | 是 | 要写入的字符串值，其长度应小于40960。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：写入成功，false：写入失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeString('abc');
  hilog.info(0x0000, 'testTag', 'writeString is ' + result);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## writeStringArray

```TypeScript
writeStringArray(stringArray: string[]): boolean
```

将字符串数组写入MessageParcel实例。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [writeStringArray](arkts-ipc-rpc-messagesequence-c.md#writeStringArray)(stringArray: string[])

<!--Device-MessageParcel-writeStringArray(stringArray: string[]): boolean--><!--Device-MessageParcel-writeStringArray(stringArray: string[]): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| stringArray | string[] | 是 | 要写入的字符串数组，数组单个元素的长度应小于40960。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：写入成功，false：写入失败。 |

## 示例

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let result = data.writeStringArray(["abc", "def"]);
  hilog.info(0x0000, 'testTag', 'writeStringArray is ' + result);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

