# MessageSequence

```TypeScript
class MessageSequence
```

Provides APIs for reading and writing data in specific format. During RPC or IPC, the sender can use the **write()** method provided by **MessageSequence** to write data in specific format to a **MessageSequence** object. The receiver can use the **read()** method provided by **MessageSequence** to read data in specific format from a **MessageSequence** object. The data formats include basic data types and arrays, IPC objects, interface tokens, and custom sequenceable objects. The read sequence must be the same as the write sequence. Otherwise, data parsing errors occurs.

**Since:** 9

<!--Device-rpc-class MessageSequence--><!--Device-rpc-class MessageSequence-End-->

**System capability:** SystemCapability.Communication.IPC.Core

## Modules to Import

```TypeScript
import { rpc } from '@kit.IPCKit';
```

## closeFileDescriptor

```TypeScript
static closeFileDescriptor(fd: number): void
```

Closes a file descriptor. This API is a static method.

- After the file is no longer needed, close the file descriptor in a timely manner to avoid resource leaks.  
- Ensure that the file operations are complete before closing the file descriptor.  
- Do not close a file descriptor that has already been closed.  
- After the file descriptor is closed, the file cannot be read or written.

**Since:** 9

<!--Device-MessageSequence-static closeFileDescriptor(fd: int): void--><!--Device-MessageSequence-static closeFileDescriptor(fd: int): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fd | number | Yes | File descriptor to close. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |

**Examples**

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

Checks whether this **MessageSequence** object contains file descriptors. This method is applicable to scenarios where you need to determine whether to process file descriptors during file transfer or check the data type before receiving data to determine the processing method.

**Since:** 9

<!--Device-MessageSequence-containFileDescriptors(): boolean--><!--Device-MessageSequence-containFileDescriptors(): boolean-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the **MessageSequence** object contains file descriptors; returns **false** otherwise. |

**Examples**

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

Creates a **MessageSequence** object. This API is a static method. After this method is called, the system allocates a contiguous buffer in memory for storing the serialized data to be transmitted. This object is used to encapsulate request and response data in IPC/RPC communication.

- The created **MessageSequence** object must be released by calling **reclaim()** after use; otherwise,  
memory leaks may occur.  
- An **MessageSequence** object cannot be used across threads.  
- You are advised to create the object on demand when IPC/RPC communication is required, and to avoid  
frequent creation and release.

**Paired calling**: For the **MessageSequence** object created via **create()**, you must call **reclaim()** to release its resources after use. Otherwise, memory resource leaks occur.

**Since:** 9

<!--Device-MessageSequence-static create(): MessageSequence--><!--Device-MessageSequence-static create(): MessageSequence-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| [MessageSequence](arkts-ipc-rpc-messagesequence-c.md) | **MessageSequence** object created. |

**Examples**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Create a MessageSequence object to encapsulate request and response data in IPC/RPC communication.
  let data = rpc.MessageSequence.create();
  hilog.info(0x0000, 'testTag', 'data is ' + data);

  // When the MessageSequence object is no longer used, the service calls the reclaim method to release resources.
  data.reclaim();
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## dupFileDescriptor

```TypeScript
static dupFileDescriptor(fd: number): number
```

Duplicates a file descriptor. This API is a static method.

- The file descriptor should be duplicated before IPC transmission to prevent the original descriptor from being  
closed.  
- Multiple processes can share the same file.  
- The file offset needs to be managed independently.  
- After duplication, both the original and the duplicated descriptors must be closed separately.  
- An invalid file descriptor should not be duplicated.  
- The lifecycle of each descriptor must be managed independently after duplication.

**Since:** 9

<!--Device-MessageSequence-static dupFileDescriptor(fd: int): int--><!--Device-MessageSequence-static dupFileDescriptor(fd: int): int-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fd | number | Yes | File descriptor to duplicate. |

**Return value:**

| Type | Description |
| --- | --- |
| number | New file descriptor. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900013](../errorcode-rpc.md#1900013-failed-to-invoke-dup) | Failed to call dup. |

**Examples**

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
getCapacity(): number
```

Obtains the capacity of this **MessageSequence** object.

**Since:** 9

<!--Device-MessageSequence-getCapacity(): int--><!--Device-MessageSequence-getCapacity(): int-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Capacity of the obtained **MessageSequence** object, in bytes. |

**Examples**

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
getRawDataCapacity(): number
```

Obtains the maximum amount of raw data that can be held by this **MessageSequence** object. This method is applicable to scenarios where you need to check whether the capacity meets the requirements before large-data transmission, or to estimate the data size in advance before processing large batches of data.

**Since:** 9

<!--Device-MessageSequence-getRawDataCapacity(): int--><!--Device-MessageSequence-getRawDataCapacity(): int-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Maximum amount of raw data that **MessageSequence** can hold, that is, 128 MB. |

**Examples**

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

## getReadableBytes

```TypeScript
getReadableBytes(): number
```

Obtains the readable capacity of this **MessageSequence** object.

**Since:** 9

<!--Device-MessageSequence-getReadableBytes(): int--><!--Device-MessageSequence-getReadableBytes(): int-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Readable capacity of the **MessageSequence** instance, in bytes. |

**Examples**

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

## getReadPosition

```TypeScript
getReadPosition(): number
```

Obtains the read position of this **MessageSequence** object.

**Since:** 9

<!--Device-MessageSequence-getReadPosition(): int--><!--Device-MessageSequence-getReadPosition(): int-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Read position obtained. |

**Examples**

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

## getSize

```TypeScript
getSize(): number
```

Obtains the data size of this **MessageSequence** object.

- Check the total size of written data.  
- Check the buffer usage.  
- Check the data size before data transmission.

**Since:** 9

<!--Device-MessageSequence-getSize(): int--><!--Device-MessageSequence-getSize(): int-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Size of the **MessageSequence** instance obtained, in bytes. It is used to adjust the data read range. You are advised to set this parameter to the actual size of the written data. |

**Examples**

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
getWritableBytes(): number
```

Obtains the writable capacity (in bytes) of this **MessageSequence** object.

**Since:** 9

<!--Device-MessageSequence-getWritableBytes(): int--><!--Device-MessageSequence-getWritableBytes(): int-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Writable capacity of the **MessageSequence** instance, in bytes. |

**Examples**

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
getWritePosition(): number
```

Obtains the write position of this **MessageSequence** object.

**Since:** 9

<!--Device-MessageSequence-getWritePosition(): int--><!--Device-MessageSequence-getWritePosition(): int-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Write position obtained. |

**Examples**

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

Reads data of the ArrayBuffer type from this **MessageSequence**.

- This method and the [writeArrayBuffer](#writearraybuffer) method must be used in  
pairs.  
- The read **typeCode** must be consistent with the write **typeCode**, and the order must also match.  
- A mismatch in **typeCode** values may cause data exception or errors. It is advised to select an appropriate [TypeCode](arkts-ipc-rpc-typecode-e.md) value based on the service type.

**Since:** 12

<!--Device-MessageSequence-readArrayBuffer(typeCode: TypeCode): ArrayBuffer--><!--Device-MessageSequence-readArrayBuffer(typeCode: TypeCode): ArrayBuffer-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typeCode | [TypeCode](arkts-ipc-rpc-typecode-e.md) | Yes | TypedArray type of the ArrayBuffer data.<br>The underlying read mode is determined based on the enum value of **TypeCode** passed by the service. |

**Return value:**

| Type | Description |
| --- | --- |
| ArrayBuffer | ArrayBuffer data, which is used to store the binary data read from **MessageSequence**. The data can be accessed and operated using a TypedArray. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.The obtained value of typeCode is incorrect; |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

```TypeScript
// In this example, the value of TypeCode is Int16Array.
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

Reads the anonymous shared object from this **MessageSequence** object. Before using this method, call [mapReadWriteAshmem](arkts-ipc-rpc-ashmem-c.md#mapreadwriteashmem) to perform memory mapping.

- readAshmem(): obtains an object.  
- [mapReadWriteAshmem](arkts-ipc-rpc-ashmem-c.md#mapreadwriteashmem): performs memory mapping.  
- [readDataFromAshmem](arkts-ipc-rpc-ashmem-c.md#readdatafromashmem): reads data.  
- unmapAshmem(): cancels mapping.  
- closeAshmem(): closes an object.  
- Data can be read only after memory mapping.  
- Mapping needs to be canceled after data is read.  
- The object needs to be closed in a timely manner to avoid memory leaks.

**Since:** 9

<!--Device-MessageSequence-readAshmem(): Ashmem--><!--Device-MessageSequence-readAshmem(): Ashmem-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| [Ashmem](arkts-ipc-rpc-ashmem-c.md) | Anonymous shared object for memory data sharing across processes. Before reading data, call [mapReadWriteAshmem](arkts-ipc-rpc-ashmem-c.md#mapreadwriteashmem) to perform memory mapping. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let sequence = rpc.MessageSequence.create();
  let ashmem = rpc.Ashmem.create("ashmem", 1024);
  // Write data to ashmem.
  let buffer = new ArrayBuffer(1024);
  let int32View = new Int32Array(buffer);
  for (let i = 0; i < int32View.length; i++) {
    int32View[i] = i * 2 + 1;
  }
  let size = buffer.byteLength;
  ashmem.mapReadWriteAshmem();
  ashmem.writeDataToAshmem(buffer, size, 0);
  // Write the size of the transferred data to this MessageSequence object.
  sequence.writeInt(size);
  // Write the ashmem object to the messageSequence object.
  sequence.writeAshmem(ashmem);

  // Read the size of the transferred data.
  let dataSize = sequence.readInt();
  // Read the ashmem object from this MessageSequence object.
  let ashmem1 = sequence.readAshmem();
  // Read data from the ashmem object.
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

Reads the Boolean value from this **MessageSequence** object.

**Since:** 9

<!--Device-MessageSequence-readBoolean(): boolean--><!--Device-MessageSequence-readBoolean(): boolean-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Boolean value read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

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

Reads the Boolean array from this **MessageSequence** object and writes it to the created empty array.

**Since:** 9

<!--Device-MessageSequence-readBooleanArray(dataIn: boolean[]): void--><!--Device-MessageSequence-readBooleanArray(dataIn: boolean[]): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dataIn | boolean[] | Yes | Boolean array read from the message sequence. An empty array must be created in advance, and the length of the array must be the same as that of the array written. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match. |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

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

<a id="readbooleanarray-1"></a>

## readBooleanArray

```TypeScript
readBooleanArray(): boolean[]
```

Reads a boolean array from this MessageSequence instance.

- This API returns a newly created array. It is not necessary to pre-allocate the array.  
- The array elements are of the boolean type.

**Since:** 9

<!--Device-MessageSequence-readBooleanArray(): boolean[]--><!--Device-MessageSequence-readBooleanArray(): boolean[]-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean[] | Boolean array read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

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
readByte(): number
```

Reads the byte value from this **MessageSequence** object.

- This method and the [writeByte](#writebyte) method must be used in pairs.  
- One write corresponds to one read.

**Since:** 9

<!--Device-MessageSequence-readByte(): int--><!--Device-MessageSequence-readByte(): int-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Byte value read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

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
readByteArray(dataIn: number[]): void
```

Reads the byte array from this **MessageSequence** object and writes it to the created empty array. After reading, the **dataIn** array will be filled with the read byte data, and the read pointer advances by the corresponding number of bytes.

**Since:** 9

<!--Device-MessageSequence-readByteArray(dataIn: int[]): void--><!--Device-MessageSequence-readByteArray(dataIn: int[]): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dataIn | number[] | Yes | Stores the byte array read from **MessageSequence**. It must be pre-allocated as an empty array, and its length must match the length of the array that was written. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match. |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  let ByteArrayVar = [1, 2, 3, 4, 5];
  // Write the byte array to the MessageSequence Object
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

<a id="readbytearray-1"></a>

## readByteArray

```TypeScript
readByteArray(): number[]
```

Reads the byte array from this **MessageSequence** object. After the read operation, the byte array data is returned, the read pointer advances by the number of bytes read.

**Since:** 9

<!--Device-MessageSequence-readByteArray(): int[]--><!--Device-MessageSequence-readByteArray(): int[]-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| number[] | Byte array read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  let ByteArrayVar = [1, 2, 3, 4, 5];
  // Write the byte array to the MessageSequence Object
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
readChar(): number
```

Reads the character from this **MessageSequence** object.

**Since:** 9

<!--Device-MessageSequence-readChar(): int--><!--Device-MessageSequence-readChar(): int-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | **Char** value read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

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
readCharArray(dataIn: number[]): void
```

Reads the character array from this **MessageSequence** object and writes it to the created empty array.

**Since:** 9

<!--Device-MessageSequence-readCharArray(dataIn: int[]): void--><!--Device-MessageSequence-readCharArray(dataIn: int[]): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dataIn | number[] | Yes | Stores the character array read from **MessageSequence**. It must be pre-allocated as an empty array, and its length must match the length of the array that was written. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match. |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

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

<a id="readchararray-1"></a>

## readCharArray

```TypeScript
readCharArray(): number[]
```

Reads the character array from this **MessageSequence** object.

- This API returns a newly created array. It is not necessary to pre-allocate the array.  
- The array elements are character codes, with a value range of [0, 65535].

**Since:** 9

<!--Device-MessageSequence-readCharArray(): int[]--><!--Device-MessageSequence-readCharArray(): int[]-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| number[] | Character array read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

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
readDouble(): number
```

Reads the double value from this **MessageSequence** object.

- This API returns a newly created array. It is not necessary to pre-allocate the array.  
- The array elements are double-precision floating-point numbers.

**Since:** 9

<!--Device-MessageSequence-readDouble(): double--><!--Device-MessageSequence-readDouble(): double-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Double value read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

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
readDoubleArray(dataIn: number[]): void
```

Reads the double array from this **MessageSequence** object and writes it to the created empty array.

**Since:** 9

<!--Device-MessageSequence-readDoubleArray(dataIn: double[]): void--><!--Device-MessageSequence-readDoubleArray(dataIn: double[]): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dataIn | number[] | Yes | Stores the double-precision floating-point number array read from **MessageSequence**. It must be pre-allocated as an empty array, and its length must match the length of the array that was written. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match. |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

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

<a id="readdoublearray-1"></a>

## readDoubleArray

```TypeScript
readDoubleArray(): number[]
```

Reads the double array from this **MessageSequence** object. The system processes float data as that of the double type. Therefore, the total number of bytes occupied by a float array must be calculated as the double type.

**Since:** 9

<!--Device-MessageSequence-readDoubleArray(): double[]--><!--Device-MessageSequence-readDoubleArray(): double[]-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| number[] | Double array read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

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

Reads the exception information from this **MessageSequence** object. This method is applicable to scenarios where the exception status needs to be checked after a response from the remote service is received.

- This method is used on the client side in IPC/RPC communication.  
- This method is called after the response to a **sendMessageRequest** API call is received.  
- It is advised to call this method first after each IPC/RPC call.  
- If an exception is detected, handle it immediately and stop subsequent data reading. After exception handling,  
it is advised to call **reclaim()** to release the **MessageSequence** object.  
- This method must be used in pairs with the [writeNoException](#writenoexception)  
method.  
- Calling sequence: the server processes a request → call [writeNoException](#writenoexception) → the client receives the response → call [readException](#readexception). If the server does not call [writeNoException](#writenoexception), calling this method will fail.

**Since:** 9

<!--Device-MessageSequence-readException(): void--><!--Device-MessageSequence-readException(): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

> NOTE
> 
> In the sample code provided in this topic, this.getUIContext().getHostContext() is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```TypeScript
// If the FA model is used, import featureAbility from @kit.AbilityKit.
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
  // Obtain the package name and ability name on the server.
  bundleName: "com.ohos.server",
  abilityName: "com.ohos.server.EntryAbility",
};

// Use this method to connect to the ability for the FA model.
// FA.connectAbility(want,connect);

// Save the connection ID, which will be used for the subsequent service disconnection.
let context: common.UIAbilityContext = this.getUIContext().getHostContext(); // UIAbilityContext
// Save the connection ID, which will be used for the subsequent service disconnection.
let connectionId = context.connectServiceExtensionAbility(want, connect);
```

The proxy object in the onConnect callback can be assigned a value only after the ability is connected asynchronously. Then, sendMessageRequest() of the proxy object is called to send a message.

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
      }).finally(() => {
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
readFileDescriptor(): number
```

Reads the file descriptor from this **MessageSequence** object. The receiver reads the mapped new file descriptor ID, which is different from the descriptor ID written by the sender but points to the same file resource. After reading, it is advised to use and close the descriptor in a timely manner to prevent resource leaks. If the descriptor needs to be used for a long time, you can call **dupFileDescriptor** to duplicate the descriptor.

- This method and the [writeFileDescriptor](#writefiledescriptor) method must be used in  
pairs.  
- Do not rely on the fd ID of the source end.  
- After the read operation, the lifecycle of the file descriptor needs to be managed.  
- You are advised to use the descriptor promptly to avoid resource waste.  
- Close the file descriptor in a timely manner after use.

**Since:** 9

<!--Device-MessageSequence-readFileDescriptor(): int--><!--Device-MessageSequence-readFileDescriptor(): int-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | File descriptor read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

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
readFloat(): number
```

Reads a float value from this **MessageSequence** instance. Since the system internally processes float data as double, the read data is returned with double precision.

**Since:** 9

<!--Device-MessageSequence-readFloat(): double--><!--Device-MessageSequence-readFloat(): double-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Double value read. Since the system internally processes float data as double, the read data is returned with double precision. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

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
readFloatArray(dataIn: number[]): void
```

Reads the double array from this **MessageSequence** object and writes it to the created empty array.

**Since:** 9

<!--Device-MessageSequence-readFloatArray(dataIn: double[]): void--><!--Device-MessageSequence-readFloatArray(dataIn: double[]): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dataIn | number[] | Yes | Stores the double-precision floating-point number array read from **MessageSequence**. It must be pre-allocated as an empty array, and its length must match the length of the array that was written. The system processes float data as that of the double type. Therefore, the total number of bytes occupied by a float array must be calculated as the double type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match. |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

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

<a id="readfloatarray-1"></a>

## readFloatArray

```TypeScript
readFloatArray(): number[]
```

Reads the double array from this **MessageSequence** object. The system processes float data as that of the double type. Therefore, the total number of bytes occupied by a float array must be calculated as the double type.

**Since:** 9

<!--Device-MessageSequence-readFloatArray(): double[]--><!--Device-MessageSequence-readFloatArray(): double[]-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| number[] | Double array read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

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
readInt(): number
```

Reads the integer from this **MessageSequence** object.

- The integer occupies 4 bytes of storage space.  
- Storage range: –2^31 to 2^31 – 1.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-MessageSequence-readInt(): int--><!--Device-MessageSequence-readInt(): int-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Integer read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

```TypeScript
// In atomic services, this example is used only to describe how to use the readInt() API. However, rpc.MessageSequence.create() is currently not supported for use in atomic services.
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
readIntArray(dataIn: number[]): void
```

Reads the integer array from this **MessageSequence** object and writes it to the created empty array.

- An empty array must be created in advance, and its length must be the same as that of the array written.  
- The value range of array elements is [-2^31, 2^31-1].

**Since:** 9

<!--Device-MessageSequence-readIntArray(dataIn: int[]): void--><!--Device-MessageSequence-readIntArray(dataIn: int[]): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dataIn | number[] | Yes | Stores the integer array read from **MessageSequence**. It must be pre-allocated as an empty array, and its length must match the length of the array that was written. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match. |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

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

<a id="readintarray-1"></a>

## readIntArray

```TypeScript
readIntArray(): number[]
```

Reads the integer array from this **MessageSequence** object.

**Since:** 9

<!--Device-MessageSequence-readIntArray(): int[]--><!--Device-MessageSequence-readIntArray(): int[]-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| number[] | Integer array read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

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

Reads the interface token from this **MessageSequence** object. The interface token is read in the sequence in which it is written to the **MessageSequence** object. The local object can use it to verify the communication.

- This method and the [writeInterfaceToken](#writeinterfacetoken) method must be used in  
pairs.  
- Before reading, ensure that there is readable data available in the buffer.  
- It is advised to read and verify the interface token immediately after receiving an IPC request.

**Since:** 9

<!--Device-MessageSequence-readInterfaceToken(): string--><!--Device-MessageSequence-readInterfaceToken(): string-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Interface token obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

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
readLong(): number
```

Reads the long integer from this **MessageSequence** object.

- The value range is [-2^63, 2^63-1].  
- The long integer occupies 8 bytes of storage space.

**Since:** 9

<!--Device-MessageSequence-readLong(): long--><!--Device-MessageSequence-readLong(): long-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Long integer read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

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
readLongArray(dataIn: number[]): void
```

Reads a long array from this **MessageSequence** object and writes it to a created empty array.

**Since:** 9

<!--Device-MessageSequence-readLongArray(dataIn: long[]): void--><!--Device-MessageSequence-readLongArray(dataIn: long[]): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dataIn | number[] | Yes | Stores the long integer array read from **MessageSequence**. It must be pre-allocated as an empty array, and its length must match the length of the array that was written. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match. |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

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

<a id="readlongarray-1"></a>

## readLongArray

```TypeScript
readLongArray(): number[]
```

Reads a long array from this **MessageSequence** object.

**Since:** 9

<!--Device-MessageSequence-readLongArray(): long[]--><!--Device-MessageSequence-readLongArray(): long[]-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| number[] | Long array read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

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

Reads the **Parcelable** object from this **MessageSequence** object to the specified object (**dataIn**).

- The **dataIn** parameter must be an instantiated **Parcelable** object.  
- The **unmarshalling** method must read data in the same sequence as the **marshalling** method.  
- The deserialization order must be consistent with the serialization order.  
- It is advised to handle exceptions within the **unmarshalling** method.

**Since:** 9

<!--Device-MessageSequence-readParcelable(dataIn: Parcelable): void--><!--Device-MessageSequence-readParcelable(dataIn: Parcelable): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dataIn | [Parcelable](arkts-ipc-rpc-parcelable-i.md) | Yes | Object that reads member variables from the **MessageSequence** object. Instantiate the serializable object before using it. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect. |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |
| [1900012](../errorcode-rpc.md#1900012-js-callback-execution-failed) | Failed to call the JS callback function. |

**Examples**

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

Reads the **Parcelable** array from this **MessageSequence** object. This method is applicable to scenarios where multiple custom data structure objects that are transmitted in batches need to be received, such as reading multiple service records, batch configuration information, or multiple entity objects.

**Since:** 9

<!--Device-MessageSequence-readParcelableArray(parcelableArray: Parcelable[]): void--><!--Device-MessageSequence-readParcelableArray(parcelableArray: Parcelable[]): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| parcelableArray | [Parcelable](arkts-ipc-rpc-parcelable-i.md)[] | Yes | Array of **Parcelable** objects to read. Instantiate the objects before use. The lengths of the serialized and deserialized arrays must be consistent. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match; 4.The length of the array passed when reading is not equal to the length passed when writing to the array; 5.The element does not exist in the array. |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |
| [1900012](../errorcode-rpc.md#1900012-js-callback-execution-failed) | Failed to call the JS callback function. |

**Examples**

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

## readRawDataBuffer

```TypeScript
readRawDataBuffer(size: number): ArrayBuffer
```

Reads raw data from this **MessageSequence** object.

- The size must match the size of the data written.  
- This API must not be called multiple times within a single parcel communication.  
- When transmitting large data volumes, be mindful of system resource usage.  
- This method and the [writeRawDataBuffer](#writerawdatabuffer) method must be used in  
pairs.

**Since:** 11

<!--Device-MessageSequence-readRawDataBuffer(size: int): ArrayBuffer--><!--Device-MessageSequence-readRawDataBuffer(size: int): ArrayBuffer-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | number | Yes | Size of the original data to read, in bytes. The value must match the size of the data written. |

**Return value:**

| Type | Description |
| --- | --- |
| ArrayBuffer | Raw data obtained, in bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

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

Reads the remote object from **MessageSequence**. You can use this API to deserialize the **MessageSequence** object to generate an **IRemoteObject**. The remote object is read in the order in which it is written to this **MessageSequence** object. After this method is called, the serialized remote object data is read from the **MessageSequence** buffer and deserialized into an **IRemoteObject** instance. The read operation updates the internal read pointer position.

- Before reading, ensure that there is readable data available in the buffer.  
- If a **RemoteObject** was written, the read result will be a **RemoteProxy**.  
- If the read operation fails, an exception will be thrown. It is advised to use a try-catch block to catch it.

**Since:** 9

<!--Device-MessageSequence-readRemoteObject(): IRemoteObject--><!--Device-MessageSequence-readRemoteObject(): IRemoteObject-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| [IRemoteObject](arkts-ipc-rpc-iremoteobject-c.md) | Remote object read, which is used for IPC/RPC communication. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1900008](../errorcode-rpc.md#1900008-invalid-ipc-object) | The proxy or remote object is invalid. |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

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
    // Process services based on the actual service logic.
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

Reads the **IRemoteObject** array from this **MessageSequence** object and writes it to the created empty array. This method is applicable to scenarios where multiple remote objects that are passed in batches need to be passed, such as obtaining multiple service proxies in batches, receiving multiple callback APIs, and managing multiple service endpoints.

- An empty array must be created in advance, and its length must be the same as that of the array written.  
- If the read operation fails, an exception will be thrown. It is advised to use a try-catch block to catch it.

**Since:** 9

<!--Device-MessageSequence-readRemoteObjectArray(objects: IRemoteObject[]): void--><!--Device-MessageSequence-readRemoteObjectArray(objects: IRemoteObject[]): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| objects | [IRemoteObject](arkts-ipc-rpc-iremoteobject-c.md)[] | Yes | Array of **IRemoteObject** objects read from **MessageSequence**, which is used for IPC/RPC communication and stores multiple remote objects. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match; 4.The length of the array passed when reading is not equal to the length passed when writing to the array. |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

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
    // Process services based on the actual service logic.
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

<a id="readremoteobjectarray-1"></a>

## readRemoteObjectArray

```TypeScript
readRemoteObjectArray(): IRemoteObject[]
```

Reads the **IRemoteObject** array from this **MessageSequence** object.

**Since:** 9

<!--Device-MessageSequence-readRemoteObjectArray(): IRemoteObject[]--><!--Device-MessageSequence-readRemoteObjectArray(): IRemoteObject[]-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| [IRemoteObject](arkts-ipc-rpc-iremoteobject-c.md)[] | **IRemoteObject** object array. If an empty array is written, **nullptr** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

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
    // Process services based on the actual service logic.
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
readShort(): number
```

Reads the short integer from this **MessageSequence** object.

- This method and the [writeShort](#writeshort) method must be used in pairs.  
- Note that the value range for writing is [-2^15, 2^15 - 1]. Values outside this range will cause data  
truncation.

**Since:** 9

<!--Device-MessageSequence-readShort(): int--><!--Device-MessageSequence-readShort(): int-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Short integer read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

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
readShortArray(dataIn: number[]): void
```

Reads the short array from this **MessageSequence** object and writes it to the created empty array.

**Since:** 9

<!--Device-MessageSequence-readShortArray(dataIn: int[]): void--><!--Device-MessageSequence-readShortArray(dataIn: int[]): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dataIn | number[] | Yes | Stores the short integer array read from the MessageSequence. A pre-allocated empty array is required, and its length must match the length of the array that was written. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match. |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

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

<a id="readshortarray-1"></a>

## readShortArray

```TypeScript
readShortArray(): number[]
```

Reads the short array from this **MessageSequence** object.

**Since:** 9

<!--Device-MessageSequence-readShortArray(): int[]--><!--Device-MessageSequence-readShortArray(): int[]-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| number[] | Short array read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

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

Reads the string from this **MessageSequence** object.

- The length is read first, followed by the content.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-MessageSequence-readString(): string--><!--Device-MessageSequence-readString(): string-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | String read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

```TypeScript
// In atomic services, this example is used only to describe how to use the readString() API. However, rpc.MessageSequence.create() is currently not supported for use in atomic services.
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

Reads the string array from this **MessageSequence** object and writes it to the created empty array.

- An empty array must be created in advance, and its length must be the same as that of the array written.  
- After the read operation, the **dataIn** array will be filled with the read byte data.  
- The read pointer advances by the corresponding number of bytes.

**Since:** 9

<!--Device-MessageSequence-readStringArray(dataIn: string[]): void--><!--Device-MessageSequence-readStringArray(dataIn: string[]): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dataIn | string[] | Yes | String array to read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match. |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

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

<a id="readstringarray-1"></a>

## readStringArray

```TypeScript
readStringArray(): string[]
```

Reads the string array from this **MessageSequence** object.

- This API returns a newly created array. It is not necessary to pre-allocate the array.  
- The length of a single element in the array ranges from 0 to 40959 bytes.

**Since:** 9

<!--Device-MessageSequence-readStringArray(): string[]--><!--Device-MessageSequence-readStringArray(): string[]-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| string[] | String array read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

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

Reclaims the **MessageSequence** object that is no longer used.

- This method and the **create ()** method must be used in pairs. For the **MessageSequence** object created via  
**create()**, you must call **reclaim()** to release its resources after use. If **reclaim()** is not called in a timely manner, memory resources leaks occur.  
- After this method is called, the object cannot be used anymore.  
- It is advised to call this method in a finally block or at the end of a task to ensure resource release.  
- Do not release the object across threads in asynchronous operations.

**Since:** 9

<!--Device-MessageSequence-reclaim(): void--><!--Device-MessageSequence-reclaim(): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Examples**

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
rewindRead(pos: number): void
```

Moves the read pointer to the specified position.

**Since:** 9

<!--Device-MessageSequence-rewindRead(pos: int): void--><!--Device-MessageSequence-rewindRead(pos: int): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pos | number | Yes | Target position from which to start reading data, in bytes. It is used to reposition the read pointer of the **MessageSequence**. The value must be within the range of [0, [getSize](#getsize)]. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

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
rewindWrite(pos: number): void
```

Moves the write pointer to the specified position.

**Since:** 9

<!--Device-MessageSequence-rewindWrite(pos: int): void--><!--Device-MessageSequence-rewindWrite(pos: int): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pos | number | Yes | Target position from which to start writing data, in bytes. It is used to reposition the write pointer of the **MessageSequence**. The value must be within the range of [0, [getSize](#getsize)]. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |

**Examples**

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
setCapacity(size: number): void
```

Sets the storage capacity of this **MessageSequence** object.

**Since:** 9

<!--Device-MessageSequence-setCapacity(size: int): void--><!--Device-MessageSequence-setCapacity(size: int): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | number | Yes | Storage capacity of the **MessageSequence** object to set, in bytes. It is used to restrict the maximum number of bytes that can be written. You are advised to set this parameter based on the actual data volume. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |
| [1900011](../errorcode-rpc.md#1900011-memory-allocation-failed) | Memory allocation failed. |

**Examples**

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
setSize(size: number): void
```

Sets the size of the data contained in this **MessageSequence** object.

**Since:** 9

<!--Device-MessageSequence-setSize(size: int): void--><!--Device-MessageSequence-setSize(size: int): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | number | Yes | Data size to set, in bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |

**Examples**

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

Writes data of the ArrayBuffer type to this **MessageSequence** object.

- This method must be used in pairs with the [readArrayBuffer](#readarraybuffer) method.  
- **typeCode** written must be consistent with **typeCode** read. Otherwise, data exceptions may occur.  
- Calling sequence: call **writeArrayBuffer()** to write the data → call [readArrayBuffer](#readarraybuffer) to read the data  
- The **typeCode** parameter determines the data write and read methods.  
- A mismatch between the write and read **typeCode** values will cause data parsing errors.  
- You must select the correct [TypeCode](arkts-ipc-rpc-typecode-e.md) enumeration value based on the actual data type.

**Since:** 12

<!--Device-MessageSequence-writeArrayBuffer(buf: ArrayBuffer, typeCode: TypeCode): void--><!--Device-MessageSequence-writeArrayBuffer(buf: ArrayBuffer, typeCode: TypeCode): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buf | ArrayBuffer | Yes | ArrayBuffer data to be written. The data is formatted and written based on the TypedArray type specified by **typeCode**. |
| typeCode | [TypeCode](arkts-ipc-rpc-typecode-e.md) | Yes | TypedArray type of the ArrayBuffer data.<br>The underlying write mode is determined based on the enum value of **TypeCode** passed by the service. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match; 4.The obtained value of typeCode is incorrect; 5.Failed to obtain arrayBuffer information. |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |

**Examples**

```TypeScript
// In this example, the value of TypeCode is Int16Array.
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

Writes an anonymous shared object to this **MessageSequence** object.

- Create an **Ashmem** object: Ashmem.create()  
- Perform memory map and write data: [mapReadWriteAshmem](arkts-ipc-rpc-ashmem-c.md#mapreadwriteashmem) +[writeDataToAshmem](arkts-ipc-rpc-ashmem-c.md#writedatatoashmem)  
- Write **Ashmem** to **MessageSequence**: writeAshmem()  
- Read **Ashmem** by the receiving side: [readAshmem](#readashmem)  
- Perform memory mapping and read data by the receiving side: mapReadWriteAshmem() + readDataFromAshmem()  
- This method must be used in pairs with the **readAshmem()** method.  
- Call sequence: writeAshmem() → transmit **MessageSequence** →[readAshmem](#readashmem) → [mapReadWriteAshmem](arkts-ipc-rpc-ashmem-c.md#mapreadwriteashmem) → [readDataFromAshmem](arkts-ipc-rpc-ashmem-c.md#readdatafromashmem)  
- Before using this method, create an **Ashmem** object and write data to it.

**Since:** 9

<!--Device-MessageSequence-writeAshmem(ashmem: Ashmem): void--><!--Device-MessageSequence-writeAshmem(ashmem: Ashmem): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ashmem | [Ashmem](arkts-ipc-rpc-ashmem-c.md) | Yes | Anonymous shared object to write. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter is not an instance of the Ashmem object. |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |

**Examples**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let sequence = rpc.MessageSequence.create();
  let ashmem = rpc.Ashmem.create("ashmem", 1024);
  // Write data to ashmem.
  let buffer = new ArrayBuffer(1024);
  let int32View = new Int32Array(buffer);
  for (let i = 0; i < int32View.length; i++) {
    int32View[i] = i * 2 + 1;
  }
  let size = buffer.byteLength;
  ashmem.mapReadWriteAshmem();
  ashmem.writeDataToAshmem(buffer, size, 0);
  // Write the ashmem object to the messageSequence object.
  sequence.writeAshmem(ashmem);
  // Write the size of the transferred data to this MessageSequence object.
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

Writes a Boolean value to this **MessageSequence** object.

- This method and the [readBoolean](#readboolean) method must be used in pairs.  
- One write corresponds to one read.

**Since:** 9

<!--Device-MessageSequence-writeBoolean(val: boolean): void--><!--Device-MessageSequence-writeBoolean(val: boolean): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| val | boolean | Yes | Boolean value to write. The value **true** indicates logical true, and the value **false** indicates logical false. The value occupies 1 byte of storage space after being written. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |

**Examples**

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

Writes a Boolean array to this **MessageSequence** object.

- This method and the [readBooleanArray](#readbooleanarray) method  
must be used in pairs.  
- The length of the array to be read must match the length of the array that was written.

**Since:** 9

<!--Device-MessageSequence-writeBooleanArray(booleanArray: boolean[]): void--><!--Device-MessageSequence-writeBooleanArray(booleanArray: boolean[]): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| booleanArray | boolean[] | Yes | Boolean array to write. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match; 4.The element does not exist in the array. |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |

**Examples**

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
writeByte(val: number): void
```

Writes a byte value to this **MessageSequence** object. After this method is called, the byte value is stored as an 8-bit unsigned integer at the current write pointer position in the buffer, and the write pointer is automatically updated. This method is suitable for transmitting small-range integers or flag data.

- Storage range: 0 to 255 (unsigned) or -128 to 127 (signed).  
- Data alignment is byte-aligned.  
- The value must be within the byte range. Values outside this range may cause data truncation.  
- This method and the [readByte](#readbyte) method must be used in pairs.  
- This method is not suitable for transmitting large-range values. For large-range values, it is advised to use [writeInt](#writeint) or [writeLong](#writelong).

**Since:** 9

<!--Device-MessageSequence-writeByte(val: int): void--><!--Device-MessageSequence-writeByte(val: int): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| val | number | Yes | Byte value to write. The value range is [0, 255]. If the value exceeds this range, it will be automatically truncated to 8 bits, which may result in loss of data precision. It is advised to check the value range before passing it. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |

**Examples**

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
writeByteArray(byteArray: number[]): void
```

Writes a byte array to this **MessageSequence** object.

- This method and the [readByteArray](#readbytearray) method must be used  
in pairs.  
- The length of the array to be read must match the length of the array that was written.

**Since:** 9

<!--Device-MessageSequence-writeByteArray(byteArray: int[]): void--><!--Device-MessageSequence-writeByteArray(byteArray: int[]): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| byteArray | number[] | Yes | Byte array to be written, which is used to transfer byte sequence data in batches. The array cannot be empty, and each element must be within the range of [0, 255]. Values out of range may be truncated. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match; 4.The element does not exist in the array. 5.The type of the element in the array is incorrect. |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |

**Examples**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  let byteArrayVar = [1, 2, 3, 4, 5];
  // Write the byte array to the MessageSequence Object
  data.writeByteArray(ByteArrayVar);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## writeChar

```TypeScript
writeChar(val: number): void
```

Writes a character to this **MessageSequence** object.

- This method and the [readChar](#readchar) method must be used in pairs.  
- One write corresponds to one read.

**Since:** 9

<!--Device-MessageSequence-writeChar(val: int): void--><!--Device-MessageSequence-writeChar(val: int): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| val | number | Yes | **Char** value to write. The value range is [0, 65535], which corresponds to the Unicode character encoding range. Values outside this range may cause character encoding errors. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |

**Examples**

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
writeCharArray(charArray: number[]): void
```

Writes a character array to this **MessageSequence** object.

- This API must be used together with [readCharArray](#readchararray).  
- The length of the array to be read must match the length of the array that was written.

**Since:** 9

<!--Device-MessageSequence-writeCharArray(charArray: int[]): void--><!--Device-MessageSequence-writeCharArray(charArray: int[]): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| charArray | number[] | Yes | Character array to write. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match; 4.The element does not exist in the array. |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |

**Examples**

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
writeDouble(val: number): void
```

Writes a double value to this **MessageSequence** object.

- This method and the [readDouble](#readdouble) method must be used in pairs.  
- One write corresponds to one read.

**Since:** 9

<!--Device-MessageSequence-writeDouble(val: double): void--><!--Device-MessageSequence-writeDouble(val: double): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| val | number | Yes | Double value to write. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |

**Examples**

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
writeDoubleArray(doubleArray: number[]): void
```

Writes a double array to this **MessageSequence** object.

- This method and the [readDoubleArray](#readdoublearray) method must  
be used in pairs.  
- The length of the array to be read must match the length of the array that was written.

**Since:** 9

<!--Device-MessageSequence-writeDoubleArray(doubleArray: double[]): void--><!--Device-MessageSequence-writeDoubleArray(doubleArray: double[]): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| doubleArray | number[] | Yes | Double array to write. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match; 4.The element does not exist in the array; 5.The type of the element in the array is incorrect. |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |

**Examples**

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
writeFileDescriptor(fd: number): void
```

Writes a file descriptor to this **MessageSequence** object. After this method is called, the file descriptor is encapsulated and transmitted across processes through the Binder mechanism. The receiving side can obtain the file descriptor via **readFileDescriptor** and perform file operations accordingly.

- The file descriptor is transmitted across processes through Binder's FD passing mechanism.  
- The receiving side obtains a new mapped file descriptor.  
- Both descriptors actually point to the same file resource.  
- Various descriptor types, such as regular files, pipes, and sockets, are supported.  
- The file descriptor must be valid and already opened.  
- After the write operation, the original descriptor remains valid and must be managed by the service itself.  
- It is advised to duplicate the file descriptor using **dupFileDescriptor** before transmission.  
- After transmission, the receiving side should use the descriptor promptly to avoid resource waste.  
- After reading, it is advised to close the descriptor in a timely manner to prevent resource leaks.

**Since:** 9

<!--Device-MessageSequence-writeFileDescriptor(fd: int): void--><!--Device-MessageSequence-writeFileDescriptor(fd: int): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fd | number | Yes | File descriptor, which is usually obtained through a file operation API (such as **fileIo.open**). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |

**Examples**

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
writeFloat(val: number): void
```

Writes a double value to this **MessageSequence** object. Since the system internally processes float data as double, the data actually written is stored in double-precision format.

**Since:** 9

<!--Device-MessageSequence-writeFloat(val: double): void--><!--Device-MessageSequence-writeFloat(val: double): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| val | number | Yes | Double value to write. It is applicable to the transmission of floating-point data (such as coordinates, ratios, and measurement values). This method and the [readFloat](#readfloat) method must be used in pairs. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |

**Examples**

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
writeFloatArray(floatArray: number[]): void
```

Writes a double array to this **MessageSequence** object.

- This method and the [readFloatArray](#readfloatarray) method must be  
used in pairs.  
- The length of the array to be read must match the length of the array that was written.

**Since:** 9

<!--Device-MessageSequence-writeFloatArray(floatArray: double[]): void--><!--Device-MessageSequence-writeFloatArray(floatArray: double[]): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| floatArray | number[] | Yes | Double array to write. The system processes float data as that of the double type. Therefore, the total number of bytes occupied by a float array must be calculated as the double type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match; 4.The element does not exist in the array; 5.The type of the element in the array is incorrect. |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |

**Examples**

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
writeInt(val: number): void
```

Writes an integer to this **MessageSequence** object. After this method is called, the integer is stored as an 32-bit signed integer at the current write pointer position in the buffer, and the write pointer is automatically updated. This method is suitable for transmitting standard integer data. For small-range values, it is advised to use [writeByte](#writebyte) or [writeShort](#writeshort) to improve efficiency. For large-range values, it is advised to use [writeLong](#writelong).

- This API must be used in pairs with [readInt](#readint).  
- One write corresponds to one read.  
- 4 bytes (32 bits) of storage space are occupied.  
- The data is stored in the system default byte order.  
- Values outside this range will cause data truncation or write failure.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-MessageSequence-writeInt(val: int): void--><!--Device-MessageSequence-writeInt(val: int): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| val | number | Yes | Integer to write. The value range is [-2^31, 2^31-1]. This parameter is suitable for transmitting standard integer data (such as counters, index values, and configuration parameters). Values outside this range will cause data truncation or write failure. For small-range values (0-255 or -128-127), it is advised to use **writeByte** to improve efficiency. For small-range integers (-32768-32767), it is advised to use **writeShort**. For large integers, it is advised to use **writeLong**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |

**Examples**

```TypeScript
// In atomic services, this example is used only to describe how to use the writeInt() API. However, rpc.MessageSequence.create() is currently not supported for use in atomic services.
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
writeIntArray(intArray: number[]): void
```

Writes an integer array to this **MessageSequence** object.

- This API must be used together with [readIntArray](#readintarray).  
- The length of the array to be read must match the length of the array that was written.

**Since:** 9

<!--Device-MessageSequence-writeIntArray(intArray: int[]): void--><!--Device-MessageSequence-writeIntArray(intArray: int[]): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| intArray | number[] | Yes | Integer array to write. The value range of array elements is [-2^31, 2^31-1]. Values outside this range will cause data truncation or write failure. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match; 4.The element does not exist in the array; 5.The type of the element in the array is incorrect. |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |

**Examples**

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

Writes an interface token to this **MessageSequence** object. The remote object can use this interface token to verify the communication. This method is applicable to scenarios where the consistency of communication interfaces between both parties needs to be verified, such as cross-process service calls, secure communication verification, and identifying the interface type provided by the server. It is advised to use a unique and meaningful string as the interface token, such as **com.example.service**, and avoid including sensitive information. The length of the token should be less than 40960. After this method is called, the interface token string is serialized and stored in the **MessageSequence** buffer. Upon receiving a communication request, the remote side can read the interface token to verify the legitimacy of the request source.

- This method and the [readInterfaceToken](#readinterfacetoken) method must be used in  
pairs.  
- If the length limit is exceeded, a parameter error exception will be thrown.

**Since:** 9

<!--Device-MessageSequence-writeInterfaceToken(token: string): void--><!--Device-MessageSequence-writeInterfaceToken(token: string): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| token | string | Yes | Interface token of the string type. It is used to verify the interface identity for the current communication. The remote object can use this information to verify the validity of the communication. The value length must be less than 40960. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.The string length is greater than or equal to 40960; 4.The number of bytes copied to the buffer is different from the length of the obtained string. |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |

**Examples**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = rpc.MessageSequence.create();
  // Write the interface token to this MessageSequence object.
  data.writeInterfaceToken("aaa");
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## writeLong

```TypeScript
writeLong(val: number): void
```

Writes a long integer to this **MessageSequence** object.

- This method and the [readLong](#readlong) method must be used in pairs.  
- One write corresponds to one read.

**Since:** 9

<!--Device-MessageSequence-writeLong(val: long): void--><!--Device-MessageSequence-writeLong(val: long): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| val | number | Yes | Long integer to write. The value range is [-2^63, 2^63-1]. Values outside this range will cause data truncation or write failure. You are advised to select a proper method (writeByte/writeShort/writeInt/writeLong) based on the value range to improve transmission efficiency. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |

**Examples**

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
writeLongArray(longArray: number[]): void
```

Writes a long array to this **MessageSequence** object.

- This method and the [readLongArray](#readlongarray) method must be  
used in pairs.  
- The length of the array to be read must match the length of the array that was written.

**Since:** 9

<!--Device-MessageSequence-writeLongArray(longArray: long[]): void--><!--Device-MessageSequence-writeLongArray(longArray: long[]): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| longArray | number[] | Yes | Long integer array to write. Each element is a 64-bit integer. Values out of range will be truncated. You are advised to use **BigInt** to process ultra-large values. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match; 4.The element does not exist in the array; 5.The type of the element in the array is incorrect. |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |

**Examples**

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

Writes information to this **MessageSequence** object indicating that no exception occurred. This method is typically called in the server-side implementation of IPC/RPC communication and within the **onRemoteMessageRequest** callback.

- This method must be used in pairs with the [readException](#readexception) method.  
- After processing a request, the server should call **writeNoException()** to write information indicating that  
no exception occurred.  
- After receiving the response, the client should call [readException](#readexception)  
to retrieve exception information.  
- If the server does not call **writeNoException()**, the client's call to [readException](#readexception) will fail.

**Since:** 9

<!--Device-MessageSequence-writeNoException(): void--><!--Device-MessageSequence-writeNoException(): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |

**Examples**

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

Writes a **Parcelable** object to this **MessageSequence** object. After this method is called, the **marshalling** method of the **Parcelable** object is called to serialize the member variables of the object one by one and write them to **MessageSequence**. This method supports the transmission of custom data structure objects. It is applicable to scenarios such as transmitting complex data structures, service objects, and configuration information.

- The **Parcelable** API defines standard methods for serialization and deserialization.  
- The **marshalling** method is responsible for writing the object state to **MessageSequence**.  
- The **unmarshalling** method is responsible for restoring the object state from **MessageSequence**.  
- The service must implement the specific serialization logic itself.  
- Only objects that implement the **Parcelable** API can be passed.  
- The **marshalling** method must correctly implement the writing of all member variables.  
- The serialization order must be consistent with the deserialization order.  
- It is advised to handle exceptions within the **marshalling** method.  
- Complex objects may occupy a significant amount of buffer space.

**Since:** 9

<!--Device-MessageSequence-writeParcelable(val: Parcelable): void--><!--Device-MessageSequence-writeParcelable(val: Parcelable): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| val | [Parcelable](arkts-ipc-rpc-parcelable-i.md) | Yes | **Parcelable** object to write. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |

**Examples**

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

Writes the **Parcelable** array to this **MessageSequence** object. This method is applicable to scenarios where multiple custom data structure objects need to be transmitted in batch, such as transmitting multiple service records, batch configuration information, or multiple entity objects.

- This method and the [readParcelableArray](#readparcelablearray) method must be used in  
pairs.  
- The length of the array to be read must match the length of the array that was written.

**Since:** 9

<!--Device-MessageSequence-writeParcelableArray(parcelableArray: Parcelable[]): void--><!--Device-MessageSequence-writeParcelableArray(parcelableArray: Parcelable[]): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| parcelableArray | [Parcelable](arkts-ipc-rpc-parcelable-i.md)[] | Yes | **Parcelable** array to write. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match; 4.The element does not exist in the array. |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |

**Examples**

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

## writeRawDataBuffer

```TypeScript
writeRawDataBuffer(rawData: ArrayBuffer, size: number): void
```

Writes raw data to this **MessageSequence** object.

> **NOTE:** 
> 
> This API cannot be called for multiple times in one parcel communication.
> 
> When the data volume is large (greater than 32 KB), the shared memory is used to transmit data. In this case,
> pay attention to the SELinux configuration.

**Since:** 11

<!--Device-MessageSequence-writeRawDataBuffer(rawData: ArrayBuffer, size: int): void--><!--Device-MessageSequence-writeRawDataBuffer(rawData: ArrayBuffer, size: int): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rawData | ArrayBuffer | Yes | Raw data to write. The size cannot exceed 128 MB. |
| size | number | Yes | Size of the raw data, in bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.Failed to obtain arrayBuffer information; 4.The transferred size cannot be obtained; 5.The transferred size is less than or equal to 0; 6.The transferred size is greater than the byte length of ArrayBuffer. |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |

**Examples**

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

Serializes the remote object and writes it to the [MessageSequence](arkts-ipc-rpc-messagesequence-c.md) object. After this method is called, the **IRemoteObject** object is serialized into a specific format and stored in the buffer of **MessageSequence**. The internal write pointer position is updated accordingly. The serialized object can be deserialized and read on the receiving side via the **readRemoteObject** method.

- Only a valid **IRemoteObject** object can be written. Passing an invalid object will cause an exception to be  
thrown.  
- The serialized object occupies a fixed amount of buffer space.  
- This method and the **readRemoteObject** method must be used in pairs.

**Since:** 9

<!--Device-MessageSequence-writeRemoteObject(obj: IRemoteObject): void--><!--Device-MessageSequence-writeRemoteObject(obj: IRemoteObject): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| obj | [IRemoteObject](arkts-ipc-rpc-iremoteobject-c.md) | Yes | Remote object to serialize and write to the **MessageSequence** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900008](../errorcode-rpc.md#1900008-invalid-ipc-object) | The proxy or remote object is invalid. |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |

**Examples**

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
    // Process services based on the actual service logic.
    return true;
  }
}

try {
  let data = rpc.MessageSequence.create();
  let testRemoteObject = new TestRemoteObject("testObject");
  // Write the remote object to the MessageSequence object.
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

Writes an **IRemoteObject** array to this **MessageSequence** object. This method is applicable to scenarios where multiple remote objects need to be passed, such as registering multiple service proxies in batches, passing multiple callback APIs, and managing multiple service endpoints.

- This method and the [readRemoteObjectArray](#readremoteobjectarray) method must be used in pairs.  
- The length of the array to be read must match the length of the array that was written.

**Since:** 9

<!--Device-MessageSequence-writeRemoteObjectArray(objectArray: IRemoteObject[]): void--><!--Device-MessageSequence-writeRemoteObjectArray(objectArray: IRemoteObject[]): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| objectArray | [IRemoteObject](arkts-ipc-rpc-iremoteobject-c.md)[] | Yes | **IRemoteObject** array to write. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match; 4.The element does not exist in the array; 5.The obtained remoteObject is null. |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |

**Examples**

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
    // Process services based on the actual service logic.
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
writeShort(val: number): void
```

Writes a short integer to this **MessageSequence** object.

- Values out of range will be truncated.  
- This API must be used together with [readShort](#readshort).  
- One write corresponds to one read.

**Since:** 9

<!--Device-MessageSequence-writeShort(val: int): void--><!--Device-MessageSequence-writeShort(val: int): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| val | number | Yes | Short integer to write. The value range is [-2^15, 2^15-1]. This is suitable for transmitting small-range integer data (such as port numbers and IDs). Values outside this range will cause data truncation or write failure. For values in the 0–255 range, it is advised to use **writeByte**. For standard integers, use **writeInt**. For large integers, use **writeLong**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |

**Examples**

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
writeShortArray(shortArray: number[]): void
```

Writes a short array to this **MessageSequence** object.

- This method and the [readShortArray](#readshortarray) method must be  
used in pairs.  
- The length of the array to be read must match the length of the array that was written.

**Since:** 9

<!--Device-MessageSequence-writeShortArray(shortArray: int[]): void--><!--Device-MessageSequence-writeShortArray(shortArray: int[]): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shortArray | number[] | Yes | Short array to write. The value range of array elements is [-2^15, 2^15-1]. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match; 4.The element does not exist in the array; 5.The type of the element in the array is incorrect. |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |

**Examples**

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

Writes a string to this **MessageSequence** object. After this method is called, the string is serialized and stored to the buffer. During the write operation, the string length is stored first, followed by the byte data.

- This method must be used in pairs with the [readString](#readstring) method.  
- The length is written first, followed by the content.  
- Multilingual character sets are supported.  
- The length information helps [readString](#readstring) determine the read boundary.  
- Note the difference between the number of characters and the number of bytes. Chinese characters occupy more  
bytes.  
- Long strings consume more buffer space.  
- An empty string can also be written normally.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-MessageSequence-writeString(val: string): void--><!--Device-MessageSequence-writeString(val: string): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| val | string | Yes | String to write. The length of the string must be less than 40960. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.The string length is greater than or equal to 40960; 4.The number of bytes copied to the buffer is different from the length of the obtained string. |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |

**Examples**

```TypeScript
// In atomic services, this example is used only to describe how to use the writeString() API. However, rpc.MessageSequence.create() is currently not supported for use in atomic services.
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

Writes a string array to this **MessageSequence** object.

- This method and the [readStringArray](#readstringarray) method must  
be used in pairs.  
- The length of the array to be read must match the length of the array that was written.

**Since:** 9

<!--Device-MessageSequence-writeStringArray(stringArray: string[]): void--><!--Device-MessageSequence-writeStringArray(stringArray: string[]): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| stringArray | string[] | Yes | String array to write. Each string element must be less than 40960 in length. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match; 4.The string length is greater than or equal to 40960; 5.The number of bytes copied to the buffer is different from the length of the obtained string. |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |

**Examples**

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

## readRawData

```TypeScript
readRawData(size: number): number[]
```

Reads raw data from this **MessageSequence** object.

**Since:** 9

**Deprecated since:** 11

**Substitutes:** [readRawDataBuffer](#readrawdatabuffer)(size: number)

<!--Device-MessageSequence-readRawData(size: number): number[]--><!--Device-MessageSequence-readRawData(size: number): number[]-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | number | Yes | Size of the original data to read, in bytes. |

**Return value:**

| Type | Description |
| --- | --- |
| number[] | Raw data obtained, in bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900010](../errorcode-rpc.md#1900010-failed-to-read-data-from-messagesequence) | Failed to read data from the message sequence. |

**Examples**

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

## writeRawData

```TypeScript
writeRawData(rawData: number[], size: number): void
```

Writes raw data to this **MessageSequence** object.

> **NOTE:** 
> 
> This API cannot be called for multiple times in one parcel communication.
> 
> When the data volume is large (greater than 32 KB), the shared memory is used to transmit data. In this case,
> pay attention to the SELinux configuration.

**Since:** 9

**Deprecated since:** 11

**Substitutes:** [writeRawDataBuffer](#writerawdatabuffer)(rawData: ArrayBuffer, size: number)

<!--Device-MessageSequence-writeRawData(rawData: number[], size: number): void--><!--Device-MessageSequence-writeRawData(rawData: number[], size: number): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rawData | number[] | Yes | Raw data to write. The size cannot exceed 128 MB. |
| size | number | Yes | Size of the raw data, in bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The parameter is an empty array; 2.The number of parameters is incorrect; 3.The parameter type does not match; 4.The transferred size cannot be obtained; 5.The transferred size is less than or equal to 0; 6.The element does not exist in the array; 7.Failed to obtain typedArray information; 8.The array is not of type int32; 9.The length of typedarray is smaller than the size of the original data sent. |
| [1900009](../errorcode-rpc.md#1900009-failed-to-write-data-to-messagesequence) | Failed to write data to the message sequence. |

**Examples**

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
