# @ohos.rpc (RPC)
<!--Kit: IPC Kit-->
<!--Subsystem: Communication-->
<!--Owner: @xdx19211@luodonghui0157-->
<!--Designer: @zhaopeng_gitee-->
<!--Tester: @maxiaorong-->
<!--Adviser: @zhang_yixin13-->

The **RPC** module implements communication between processes, including inter-process communication (IPC) on a single device and remote procedure call (RPC) between processes on difference devices. IPC is implemented based on the Binder driver, and RPC is based on the DSoftBus driver.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This module supports return of error codes since API version 9.

## Modules to Import

```ts
import { rpc } from '@kit.IPCKit';
```

## ErrorCode<sup>9+</sup>

The APIs of this module return exceptions since API version 9. The following table lists the error codes.

**System capability**: SystemCapability.Communication.IPC.Core

  | Name                                 | Value     | Description                                         |
  | ------------------------------------- | ------- | --------------------------------------------- |
  | CHECK_PARAM_ERROR                     | 401     | Parameter check failed.                               |
  | OS_MMAP_ERROR                         | 1900001 | Failed to call mmap.                       |
  | OS_IOCTL_ERROR                        | 1900002 | Failed to call **ioctl** with the shared memory file descriptor.|
  | WRITE_TO_ASHMEM_ERROR                 | 1900003 | Failed to write data to the shared memory.                       |
  | READ_FROM_ASHMEM_ERROR                | 1900004 | Failed to read data from the shared memory.                       |
  | ONLY_PROXY_OBJECT_PERMITTED_ERROR     | 1900005 | This operation is allowed only on the proxy object.                    |
  | ONLY_REMOTE_OBJECT_PERMITTED_ERROR    | 1900006 | This operation is allowed only on the remote object.                   |
  | COMMUNICATION_ERROR                   | 1900007 | Failed to communicate with the remote object over IPC.               |
  | PROXY_OR_REMOTE_OBJECT_INVALID_ERROR  | 1900008 | Invalid proxy or remote object.                 |
  | WRITE_DATA_TO_MESSAGE_SEQUENCE_ERROR  | 1900009 | Failed to write data to MessageSequence.                |
  | READ_DATA_FROM_MESSAGE_SEQUENCE_ERROR | 1900010 | Failed to read data from MessageSequence.                |
  | PARCEL_MEMORY_ALLOC_ERROR             | 1900011 | Failed to allocate memory during serialization.                   |
  | CALL_JS_METHOD_ERROR                  | 1900012 | Failed to invoke the JS callback.                         |
  | OS_DUP_ERROR                          | 1900013 | Failed to call dup.                        |

## TypeCode<sup>12+</sup>

Since API version 12, [writeArrayBuffer](#writearraybuffer12) and [readArrayBuffer](#readarraybuffer12) are added to pass ArrayBuffer data. The specific TypedArray type is determined by the **TypeCode** defined as follows:

**System capability**: SystemCapability.Communication.IPC.Core

  | Name                        | Value    | Description                                         |
  | ---------------------------- | ------ | --------------------------------------------  |
  | INT8_ARRAY                   | 0      | The TypedArray type is **INT8_ARRAY**.                 |
  | UINT8_ARRAY                  | 1      | The TypedArray type is **UINT8_ARRAY**.                |
  | INT16_ARRAY                  | 2      | The TypedArray type is **INT16_ARRAY**.                |
  | UINT16_ARRAY                 | 3      | The TypedArray type is **UINT16_ARRAY**.               |
  | INT32_ARRAY                  | 4      | The TypedArray type is **INT32_ARRAY**.                |
  | UINT32_ARRAY                 | 5      | The TypedArray type is **UINT32_ARRAY**.               |
  | FLOAT32_ARRAY                | 6      | The TypedArray type is **FLOAT32_ARRAY**.              |
  | FLOAT64_ARRAY                | 7      | The TypedArray type is **FLOAT64_ARRAY**.              |
  | BIGINT64_ARRAY               | 8      | The TypedArray type is **BIGINT64_ARRAY**.             |
  | BIGUINT64_ARRAY              | 9      | The TypedArray type is **BIGUINT64_ARRAY**.            |

## MessageSequence<sup>9+</sup>

Provides APIs for reading and writing data in specific format. During RPC or IPC, the sender can use the **write()** method provided by **MessageSequence** to write data in specific format to a **MessageSequence** object. The receiver can use the **read()** method provided by **MessageSequence** to read data in specific format from a **MessageSequence** object. The data formats include basic data types and arrays, IPC objects, interface tokens, and custom sequenceable objects.

### create<sup>9+</sup>

static create(): MessageSequence

Creates a **MessageSequence** object. This API is a static method.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

| Type           | Description                           |
| --------------- | ------------------------------- |
| [MessageSequence](#messagesequence9) | **MessageSequence** object created.|

**Example**

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
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

### reclaim<sup>9+</sup>

reclaim(): void

Reclaims the **MessageSequence** object that is no longer used.

**System capability**: SystemCapability.Communication.IPC.Core

**Example**

```ts
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

### writeRemoteObject<sup>9+</sup>

writeRemoteObject(obj: IRemoteObject): void

Serializes the remote object and writes it to the [MessageSequence](#messagesequence9) object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type                           | Mandatory| Description                                     |
  | ------ | ------------------------------- | ---- | ----------------------------------------- |
  | obj | [IRemoteObject](#iremoteobject) | Yes  | Remote object to serialize and write to the **MessageSequence** object.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match. |
  | 1900008  | The proxy or remote object is invalid. |
  | 1900009  | Failed to write data to the message sequence. |

**Example**

```ts
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
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

### readRemoteObject<sup>9+</sup>

readRemoteObject(): IRemoteObject

Reads the remote object from **MessageSequence**. You can use this API to deserialize the **MessageSequence** object to generate an **IRemoteObject**. The remote object is read in the order in which it is written to this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type                           | Description              |
  | ------------------------------- | ------------------ |
  | [IRemoteObject](#iremoteobject) | Remote object obtained.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 1900008  | The proxy or remote object is invalid. |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### writeInterfaceToken<sup>9+</sup>

writeInterfaceToken(token: string): void

Writes an interface token to this **MessageSequence** object. The remote object can use this interface token to verify the communication.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description              |
  | ------ | ------ | ---- | ------------------ |
  | token  | string | Yes  | Interface token to write. The length of the string must be less than 40960 bytes.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes:<br> 1.The number of parameters is incorrect;<br> 2.The parameter type does not match;<br> 3.The string length is greater than or equal to 40960 bytes;<br> 4.The number of bytes copied to the buffer is different from the length of the obtained string. |
  | 1900009  | Failed to write data to the message sequence. |

**Example**

```ts
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

### readInterfaceToken<sup>9+</sup>

readInterfaceToken(): string

Reads the interface token from this **MessageSequence** object. The interface token is read in the sequence in which it is written to the **MessageSequence** object. The local object can use it to verify the communication.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description                    |
  | ------ | ------------------------ |
  | string | Interface token obtained.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### getSize<sup>9+</sup>

getSize(): number

Obtains the data size of this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description                                           |
  | ------ | ----------------------------------------------- |
  | number | Size of the **MessageSequence** instance obtained, in bytes.|

**Example**

```ts
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

### getCapacity<sup>9+</sup>

getCapacity(): number

Obtains the capacity of this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description |
  | ------ | ----- |
  | number | Capacity of the obtained **MessageSequence** object, in bytes.|

**Example**

```ts
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

### setSize<sup>9+</sup>

setSize(size: number): void

Sets the size of the data contained in this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description  |
  | ------ | ------ | ---- | ------ |
  | size   | number | Yes  | Data size to set, in bytes.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match. |
  | 1900009  | Failed to write data to the message sequence. |

**Example**

```ts
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

### setCapacity<sup>9+</sup>

setCapacity(size: number): void

Sets the storage capacity of this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description                                         |
  | ------ | ------ | ---- | --------------------------------------------- |
  | size   | number | Yes  | Storage capacity of the **MessageSequence** object to set, in bytes.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match. |
  | 1900009  | Failed to write data to the message sequence. |
  | 1900011  | Memory allocation failed. |

**Example**

```ts
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

### getWritableBytes<sup>9+</sup>

getWritableBytes(): number

Obtains the writable capacity (in bytes) of this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description  |
  | ------ | ------ |
  | number | Writable capacity of the **MessageSequence** instance, in bytes.|

**Example**

```ts
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

### getReadableBytes<sup>9+</sup>

getReadableBytes(): number

Obtains the readable capacity of this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description   |
  | ------ | ------- |
  | number | Readable capacity of the **MessageSequence** instance, in bytes.|

**Example**

```ts
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

### getReadPosition<sup>9+</sup>

getReadPosition(): number

Obtains the read position of this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description  |
  | ------ | ------ |
  | number | Read position obtained.|

**Example**

```ts
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

### getWritePosition<sup>9+</sup>

getWritePosition(): number

Obtains the write position of this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description |
  | ------ | ----- |
  | number | Write position obtained.|

**Example**

```ts
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

### rewindRead<sup>9+</sup>

rewindRead(pos: number): void

Moves the read pointer to the specified position.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description   |
  | ------ | ------ | ---- | ------- |
  | pos    | number | Yes  | Position from which data is to read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match. |
  | 1900010 | Failed to read data from the message sequence. |

**Example**

```ts
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

### rewindWrite<sup>9+</sup>

rewindWrite(pos: number): void

Moves the write pointer to the specified position.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description |
  | ------ | ------ | ---- | ----- |
  | pos    | number | Yes  | Position from which data is to write.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match. |
  | 1900009  | Failed to write data to the message sequence. |

**Example**

```ts
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

### writeByte<sup>9+</sup>

writeByte(val: number): void

Writes a byte value to this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description |
  | ------ | ------ | ---- | ----- |
  | val    | number | Yes  | Byte value to write.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------  |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match. |
  | 1900009  | Failed to write data to the message sequence. |

**Example**

```ts
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

### readByte<sup>9+</sup>

readByte(): number

Reads the byte value from this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description |
  | ------ | ----- |
  | number | Byte value read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | ------- | --------  |
  | 1900010 | Failed to read data from the message sequence. |

**Example**

```ts
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

### writeShort<sup>9+</sup>

writeShort(val: number): void

Writes a short integer to this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description|
  | ------ | ------ | ---  | ---  |
  | val    | number | Yes  | Short integer to write.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match. |
  | 1900009  | Failed to write data to the message sequence. |

**Example**

```ts
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

### readShort<sup>9+</sup>

readShort(): number

Reads the short integer from this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description          |
  | ------ | -------------- |
  | number | Short integer read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### writeInt<sup>9+</sup>

writeInt(val: number): void

Writes an integer to this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description            |
  | ------ | ------ | ---- | ---------------- |
  | val    | number | Yes  | Integer to write.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match. |
  | 1900009  | Failed to write data to the message sequence. |

**Example**

```ts
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

### readInt<sup>9+</sup>

readInt(): number

Reads the integer from this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description        |
  | ------ | ------------ |
  | number | Integer read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### writeLong<sup>9+</sup>

writeLong(val: number): void

Writes a long integer to this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description            |
  | ------ | ------ | ---- | ---------------- |
  | val    | number | Yes  | Long integer to write.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match. |
  | 1900009  | Failed to write data to the message sequence. |

**Example**

```ts
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

### readLong<sup>9+</sup>

readLong(): number

Reads the long integer from this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description          |
  | ------ | -------------- |
  | number | Long integer read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### writeFloat<sup>9+</sup>

writeFloat(val: number): void

Writes a double value to this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description |
  | ------ | ------ | ---- | ----- |
  | val    | number | Yes  | Double value to write.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match. |
  | 1900009  | Failed to write data to the message sequence. |

**Example**

```ts
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

### readFloat<sup>9+</sup>

readFloat(): number

Reads the double value from this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description        |
  | ------ | ------------ |
  | number | Double value read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### writeDouble<sup>9+</sup>

writeDouble(val: number): void

Writes a double value to this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description                  |
  | ------ | ------ | ---- | ---------------------- |
  | val    | number | Yes  | Double value to write.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match. |
  | 1900009  | Failed to write data to the message sequence. |

**Example**

```ts
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

### readDouble<sup>9+</sup>

readDouble(): number

Reads the double value from this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description              |
  | ------ | ------------------ |
  | number | Double value read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### writeBoolean<sup>9+</sup>

writeBoolean(val: boolean): void

Writes a Boolean value to this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type   | Mandatory| Description            |
  | ------ | ------- | ---- | ---------------- |
  | val    | boolean | Yes  | Boolean value to write.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match. |
  | 1900009  | Failed to write data to the message sequence. |

**Example**

```ts
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

### readBoolean<sup>9+</sup>

readBoolean(): boolean

Reads the Boolean value from this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type   | Description                |
  | ------- | -------------------- |
  | boolean | Boolean value read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### writeChar<sup>9+</sup>

writeChar(val: number): void

Writes a character to this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description                |
  | ------ | ------ | ---- | -------------------- |
  | val    | number | Yes  | **Char** value to write.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match. |
  | 1900009  | Failed to write data to the message sequence. |

**Example**

```ts
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

### readChar<sup>9+</sup>

readChar(): number

Reads the character from this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description|
  | ------ | ---- |
  | number | **Char** value read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### writeString<sup>9+</sup>

writeString(val: string): void

Writes a string to this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description                                     |
  | ------ | ------ | ---- | ----------------------------------------- |
  | val    | string | Yes  | String to write. The length of the string must be less than 40960 bytes.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match; <br> 3.The string length is greater than or equal to 40960 bytes; <br> 4.The number of bytes copied to the buffer is different from the length of the obtained string. |
  | 1900009  | Failed to write data to the message sequence. |

**Example**

```ts
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

### readString<sup>9+</sup>

readString(): string

Reads the string from this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description          |
  | ------ | -------------- |
  | string | String read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### writeParcelable<sup>9+</sup>

writeParcelable(val: Parcelable): void

Writes a **Parcelable** object to this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | --------- | ---- | ------ |
| val    | [Parcelable](#parcelable9) | Yes  | **Parcelable** object to write.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match. |
  | 1900009  | Failed to write data to the message sequence. |

**Example**

```ts
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

### readParcelable<sup>9+</sup>

readParcelable(dataIn: Parcelable): void

Reads the **Parcelable** object from this **MessageSequence** object to the specified object (**dataIn**).

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

| Name| Type                      | Mandatory| Description                                     |
| ------ | -------------------------- | ---- | ----------------------------------------- |
| dataIn | [Parcelable](#parcelable9) | Yes  | **Parcelable** object to read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect. |
  | 1900010  | Failed to read data from the message sequence. |
  | 1900012  | Failed to call the JS callback function. |

**Example**

```ts
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

### writeByteArray<sup>9+</sup>

writeByteArray(byteArray: number[]): void

Writes a byte array to this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name   | Type    | Mandatory| Description              |
  | --------- | -------- | ---- | ------------------ |
  | byteArray | number[] | Yes  | Byte array to write.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The parameter is an empty array; <br> 2.The number of parameters is incorrect; <br> 3.The parameter type does not match; <br> 4.The element does not exist in the array. <br> 5.The type of the element in the array is incorrect. |
  | 1900009  | Failed to write data to the message sequence. |

**Example**

```ts
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

### readByteArray<sup>9+</sup>

readByteArray(dataIn: number[]): void

Reads the byte array from this **MessageSequence** object and writes it to the created empty array.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type    | Mandatory| Description              |
  | ------ | -------- | ---- | ------------------ |
  | dataIn | number[] | Yes  | Byte array to read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The parameter is an empty array; <br> 2.The number of parameters is incorrect; <br> 3.The parameter type does not match. |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### readByteArray<sup>9+</sup>

readByteArray(): number[]

Reads the byte array from this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type    | Description          |
  | -------- | -------------- |
  | number[] | Byte array read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### writeShortArray<sup>9+</sup>

writeShortArray(shortArray: number[]): void

Writes a short array to this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name    | Type    | Mandatory| Description                |
  | ---------- | -------- | ---- | -------------------- |
  | shortArray | number[] | Yes  | Short array to write.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The parameter is an empty array; <br> 2.The number of parameters is incorrect; <br> 3.The parameter type does not match; <br> 4.The element does not exist in the array; <br> 5.The type of the element in the array is incorrect. |
  | 1900009  | Failed to write data to the message sequence. |

**Example**

```ts
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

### readShortArray<sup>9+</sup>

readShortArray(dataIn: number[]): void

Reads the short array from this **MessageSequence** object and writes it to the created empty array.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type    | Mandatory| Description                |
  | ------ | -------- | ---- | -------------------- |
  | dataIn | number[] | Yes  | Short array to read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The parameter is an empty array; <br> 2.The number of parameters is incorrect; <br> 3.The parameter type does not match. |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### readShortArray<sup>9+</sup>

readShortArray(): number[]

Reads the short array from this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type    | Description            |
  | -------- | ---------------- |
  | number[] | Short array read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### writeIntArray<sup>9+</sup>

writeIntArray(intArray: number[]): void

Writes an integer array to this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name  | Type    | Mandatory| Description              |
  | -------- | -------- | ---- | ------------------ |
  | intArray | number[] | Yes  | Integer array to write.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The parameter is an empty array; <br> 2.The number of parameters is incorrect; <br> 3.The parameter type does not match; <br> 4.The element does not exist in the array; <br> 5.The type of the element in the array is incorrect. |
  | 1900009  | Failed to write data to the message sequence. |

**Example**

```ts
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

### readIntArray<sup>9+</sup>

readIntArray(dataIn: number[]): void

Reads the integer array from this **MessageSequence** object and writes it to the created empty array.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type    | Mandatory| Description              |
  | ------ | -------- | ---- | ------------------ |
  | dataIn | number[] | Yes  | Integer array to read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The parameter is an empty array; <br> 2.The number of parameters is incorrect; <br> 3.The parameter type does not match. |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### readIntArray<sup>9+</sup>

readIntArray(): number[]

Reads the integer array from this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type    | Description          |
  | -------- | -------------- |
  | number[] | Integer array read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### writeLongArray<sup>9+</sup>

writeLongArray(longArray: number[]): void

Writes a long array to this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name   | Type    | Mandatory| Description                |
  | --------- | -------- | ---- | -------------------- |
  | longArray | number[] | Yes  | Long array to write.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The parameter is an empty array; <br> 2.The number of parameters is incorrect; <br> 3.The parameter type does not match; <br> 4.The element does not exist in the array; <br> 5.The type of the element in the array is incorrect. |
  | 1900009  | Failed to write data to the message sequence. |

**Example**

```ts
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

### readLongArray<sup>9+</sup>

readLongArray(dataIn: number[]): void

Reads the long array from this **MessageSequence** object and writes it to the created empty array.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type    | Mandatory| Description                |
  | ------ | -------- | ---- | -------------------- |
  | dataIn | number[] | Yes  | Long array to read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The parameter is an empty array; <br> 2.The number of parameters is incorrect; <br> 3.The parameter type does not match. |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### readLongArray<sup>9+</sup>

readLongArray(): number[]

Reads the long integer array from this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type    | Description            |
  | -------- | ---------------- |
  | number[] | Long array read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### writeFloatArray<sup>9+</sup>

writeFloatArray(floatArray: number[]): void

Writes a double array to this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name    | Type    | Mandatory| Description                                                                                                                   |
  | ---------- | -------- | ---- | ----------------------------------------------------------------------------------------------------------------------- |
  | floatArray | number[] | Yes  | Double array to write. The system processes float data as that of the double type. Therefore, the total number of bytes occupied by a float array must be calculated as the double type.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The parameter is an empty array; <br> 2.The number of parameters is incorrect; <br> 3.The parameter type does not match; <br> 4.The element does not exist in the array; <br> 5.The type of the element in the array is incorrect. |
  | 1900009  | Failed to write data to the message sequence. |

**Example**

```ts
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

### readFloatArray<sup>9+</sup>

readFloatArray(dataIn: number[]): void

Reads the double array from this **MessageSequence** object and writes it to the created empty array.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type    | Mandatory| Description                                                                                                                   |
  | ------ | -------- | ---- | ----------------------------------------------------------------------------------------------------------------------- |
  | dataIn | number[] | Yes  | Double array to read. The system processes float data as that of the double type. Therefore, the total number of bytes occupied by a float array must be calculated as the double type.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The parameter is an empty array; <br> 2.The number of parameters is incorrect; <br> 3.The parameter type does not match. |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### readFloatArray<sup>9+</sup>

readFloatArray(): number[]

Reads the double array from this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type    | Description          |
  | -------- | -------------- |
  | number[] | Double array read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### writeDoubleArray<sup>9+</sup>

writeDoubleArray(doubleArray: number[]): void

Writes a double array to this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name     | Type    | Mandatory| Description                    |
  | ----------- | -------- | ---- | ------------------------ |
  | doubleArray | number[] | Yes  | Double array to write.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The parameter is an empty array; <br> 2.The number of parameters is incorrect; <br> 3.The parameter type does not match; <br> 4.The element does not exist in the array; <br> 5.The type of the element in the array is incorrect. |
  | 1900009  | Failed to write data to the message sequence. |

**Example**

```ts
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

### readDoubleArray<sup>9+</sup>

readDoubleArray(dataIn: number[]): void

Reads the double array from this **MessageSequence** object and writes it to the created empty array.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type    | Mandatory| Description                    |
  | ------ | -------- | ---- | ------------------------ |
  | dataIn | number[] | Yes  | Double array to read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The parameter is an empty array; <br> 2.The number of parameters is incorrect; <br> 3.The parameter type does not match. |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### readDoubleArray<sup>9+</sup>

readDoubleArray(): number[]

Reads the double array from this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type    | Description                |
  | -------- | -------------------- |
  | number[] | Double array read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### writeBooleanArray<sup>9+</sup>

writeBooleanArray(booleanArray: boolean[]): void

Writes a Boolean array to this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name      | Type     | Mandatory| Description              |
  | ------------ | --------- | ---- | ------------------ |
  | booleanArray | boolean[] | Yes  | Boolean array to write.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The parameter is an empty array; <br> 2.The number of parameters is incorrect; <br> 3.The parameter type does not match; <br> 4.The element does not exist in the array. |
  | 1900009  | Failed to write data to the message sequence. |

**Example**

```ts
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

### readBooleanArray<sup>9+</sup>

readBooleanArray(dataIn: boolean[]): void

Reads the Boolean array from this **MessageSequence** object and writes it to the created empty array.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type     | Mandatory| Description              |
  | ------ | --------- | ---- | ------------------ |
  | dataIn | boolean[] | Yes  | Boolean array to read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The parameter is an empty array; <br> 2.The number of parameters is incorrect; <br> 3.The parameter type does not match. |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### readBooleanArray<sup>9+</sup>

readBooleanArray(): boolean[]

Reads the Boolean array from this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type     | Description          |
  | --------- | -------------- |
  | boolean[] | Boolean array read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### writeCharArray<sup>9+</sup>

writeCharArray(charArray: number[]): void

Writes a character array to this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name   | Type    | Mandatory| Description                  |
  | --------- | -------- | ---- | ---------------------- |
  | charArray | number[] | Yes  | Character array to write.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The parameter is an empty array; <br> 2.The number of parameters is incorrect; <br> 3.The parameter type does not match; <br> 4.The element does not exist in the array. |
  | 1900009  | Failed to write data to the message sequence. |

**Example**

```ts
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

### readCharArray<sup>9+</sup>

readCharArray(dataIn: number[]): void

Reads the character array from this **MessageSequence** object and writes it to the created empty array.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type    | Mandatory| Description                  |
  | ------ | -------- | ---- | ---------------------- |
  | dataIn | number[] | Yes  | Character array to read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The parameter is an empty array; <br> 2.The number of parameters is incorrect; <br> 3.The parameter type does not match. |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### readCharArray<sup>9+</sup>

readCharArray(): number[]

Reads the character array from this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type    | Description              |
  | -------- | ------------------ |
  | number[] | Character array read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### writeStringArray<sup>9+</sup>

writeStringArray(stringArray: string[]): void

Writes a string array to this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name     | Type    | Mandatory| Description                                                   |
  | ----------- | -------- | ---- | ------------------------------------------------------- |
  | stringArray | string[] | Yes  | String array to write. The length of a single element in the array must be less than 40960 bytes.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The parameter is an empty array; <br> 2.The number of parameters is incorrect; <br> 3.The parameter type does not match; <br> 4.The string length is greater than or equal to 40960 bytes; <br> 5.The number of bytes copied to the buffer is different from the length of the obtained string. |
  | 1900009  | Failed to write data to the message sequence. |

**Example**

```ts
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

### readStringArray<sup>9+</sup>

readStringArray(dataIn: string[]): void

Reads the string array from this **MessageSequence** object and writes it to the created empty array.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type    | Mandatory| Description                |
  | ------ | -------- | ---- | -------------------- |
  | dataIn | string[] | Yes  | String array to read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The parameter is an empty array; <br> 2.The number of parameters is incorrect; <br> 3.The parameter type does not match. |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### readStringArray<sup>9+</sup>

readStringArray(): string[]

Reads the string array from this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type    | Description            |
  | -------- | ---------------- |
  | string[] | String array read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### writeNoException<sup>9+</sup>

writeNoException(): void

Writes information to this **MessageSequence** object indicating that no exception occurred.

**System capability**: SystemCapability.Communication.IPC.Core

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 1900009  | Failed to write data to the message sequence. |

**Example**

```ts
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

### readException<sup>9+</sup>

readException(): void

Reads the exception information from this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.getUIContext().getHostContext()** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

<!--code_no_check-->
```ts
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

The proxy object in the **onConnect** callback can be assigned a value only after the ability is connected asynchronously. Then, **sendMessageRequest()** of the proxy object is called to send a message.

```ts
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
        hilog.error(0x0000, 'testTag', 'sendMessageRequest got exception: ' + e);
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

### writeParcelableArray<sup>9+</sup>

writeParcelableArray(parcelableArray: Parcelable[]): void

Writes the **Parcelable** array to this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

| Name         | Type        | Mandatory| Description                      |
| --------------- | ------------ | ---- | -------------------------- |
| parcelableArray | [Parcelable](#parcelable9)[] | Yes  | **Parcelable** array to write.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The parameter is an empty array; <br> 2.The number of parameters is incorrect; <br> 3.The parameter type does not match; <br> 4.The element does not exist in the array. |
  | 1900009  | Failed to write data to the message sequence. |

**Example**

```ts
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

### readParcelableArray<sup>9+</sup>

readParcelableArray(parcelableArray: Parcelable[]): void

Reads the **Parcelable** array from this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

| Name         | Type        | Mandatory| Description                      |
| --------------- | ------------ | ---- | -------------------------- |
| parcelableArray | [Parcelable](#parcelable9)[] | Yes  | **Parcelable** array to read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The parameter is an empty array; <br> 2.The number of parameters is incorrect; <br> 3.The parameter type does not match; <br> 4.The length of the array passed when reading is not equal to the length passed when writing to the array; <br> 5.The element does not exist in the array. |
  | 1900010  | Failed to read data from the message sequence. |
  | 1900012  | Failed to call the JS callback function. |

**Example**

```ts
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

### writeRemoteObjectArray<sup>9+</sup>

writeRemoteObjectArray(objectArray: IRemoteObject[]): void

Writes an **IRemoteObject** array to this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

| Name     | Type           | Mandatory| Description                                          |
| ----------- | --------------- | ---- | ---------------------------------------------- |
| objectArray | [IRemoteObject](#iremoteobject)[] | Yes  | **IRemoteObject** array to write.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The parameter is an empty array; <br> 2.The number of parameters is incorrect; <br> 3.The parameter type does not match; <br> 4.The element does not exist in the array; <br> 5.The obtained remoteObject is null. |
  | 1900009  | Failed to write data to the message sequence. |

**Example**

```ts
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

### readRemoteObjectArray<sup>9+</sup>

readRemoteObjectArray(objects: IRemoteObject[]): void

Reads the **IRemoteObject** array from this **MessageSequence** object and writes it to the created empty array.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

| Name | Type           | Mandatory| Description                                          |
| ------- | --------------- | ---- | ---------------------------------------------- |
| objects | [IRemoteObject](#iremoteobject)[] | Yes  | **IRemoteObject** array to read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The parameter is an empty array; <br> 2.The number of parameters is incorrect; <br> 3.The parameter type does not match; <br> 4.The length of the array passed when reading is not equal to the length passed when writing to the array. |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### readRemoteObjectArray<sup>9+</sup>

readRemoteObjectArray(): IRemoteObject[]

Reads the **IRemoteObject** array from this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

| Type           | Description                       |
| --------------- | --------------------------- |
| [IRemoteObject](#iremoteobject)[] | The **IRemoteObject** array is returned. If an empty array is written, **null** is returned.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### closeFileDescriptor<sup>9+</sup>

static closeFileDescriptor(fd: number): void

Closes a file descriptor. This API is a static method.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description                |
  | ------ | ------ | ---- | -------------------- |
  | fd     | number | Yes  | File descriptor to close.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match. |

**Example**

```ts
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

### dupFileDescriptor<sup>9+</sup>

static dupFileDescriptor(fd: number): number

Duplicates a file descriptor. This API is a static method.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description                    |
  | ------ | ------ | ---- | ------------------------ |
  | fd     | number | Yes  | File descriptor to duplicate.|

**Return value**

  | Type  | Description                |
  | ------ | -------------------- |
  | number | New file descriptor.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match. |
  | 1900013  | Failed to call dup. |

**Example**

```ts
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

### containFileDescriptors<sup>9+</sup>

containFileDescriptors(): boolean

Checks whether this **MessageSequence** object contains file descriptors.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type   | Description                                                                |
  | ------- | -------------------------------------------------------------------- |
  | boolean | Returns **true** if the **MessageSequence** object contains file descriptors; returns **false** otherwise.|

**Example**

```ts
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

### writeFileDescriptor<sup>9+</sup>

writeFileDescriptor(fd: number): void

Writes a file descriptor to this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description        |
  | ------ | ------ | ---- | ------------ |
  | fd     | number | Yes  | File descriptor to write.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match. |
  | 1900009  | Failed to write data to the message sequence. |

**Example**

```ts
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

### readFileDescriptor<sup>9+</sup>

readFileDescriptor(): number

Reads the file descriptor from this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description            |
  | ------ | ---------------- |
  | number | File descriptor read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### writeAshmem<sup>9+</sup>

writeAshmem(ashmem: Ashmem): void

Writes an anonymous shared object to this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

| Name| Type  | Mandatory| Description                                 |
| ------ | ------ | ---- | ------------------------------------- |
| ashmem | [Ashmem](#ashmem8) | Yes  | Anonymous shared object to write.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | ------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter is not an instance of the Ashmem object. |
  | 1900009  | Failed to write data to the message sequence. |

**Example**

```ts
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

### readAshmem<sup>9+</sup>

readAshmem(): Ashmem

Reads the anonymous shared object from this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

| Type  | Description              |
| ------ | ------------------ |
| [Ashmem](#ashmem8) | Anonymous share object obtained.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### getRawDataCapacity<sup>9+</sup>

getRawDataCapacity(): number

Obtains the maximum amount of raw data that can be held by this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description                                                        |
  | ------ | ------------------------------------------------------------ |
  | number | Maximum amount of raw data that **MessageSequence** can hold, that is, 128 MB.|

**Example**

```ts
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

### writeRawData<sup>(deprecated)</sup>

writeRawData(rawData: number[], size: number): void

Writes raw data to this **MessageSequence** object.

> **NOTE**
>
> - This API is supported since API version 9 and deprecated since API version 11. Use [writeRawDataBuffer](#writerawdatabuffer11) instead.
>
> - This API cannot be called for multiple times in one parcel communication.
> - When the data volume is large (greater than 32 KB), the shared memory is used to transmit data. In this case, pay attention to the SELinux configuration.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name | Type    | Mandatory| Description                              |
  | ------- | -------- | ---- | ---------------------------------- |
  | rawData | number[] | Yes  | Raw data to write. The size cannot exceed 128 MB.|
  | size    | number   | Yes  | Size of the raw data, in bytes.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The parameter is an empty array; <br> 2.The number of parameters is incorrect; <br> 3.The parameter type does not match; <br> 4.The transferred size cannot be obtained; <br> 5.The transferred size is less than or equal to 0;<br> 6.The element does not exist in the array; <br> 7.Failed to obtain typedArray information; <br> 8.The array is not of type int32; <br> 9.The length of typedarray is smaller than the size of the original data sent. |
  | 1900009  | Failed to write data to the message sequence. |

**Example**

<!--deprecated_code_no_check-->
```ts
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

### writeRawDataBuffer<sup>11+</sup>

writeRawDataBuffer(rawData: ArrayBuffer, size: number): void

Writes raw data to this **MessageSequence** object.

> **NOTE**
>
> - This API cannot be called for multiple times in one parcel communication.
> - When the data volume is large (greater than 32 KB), the shared memory is used to transmit data. In this case, pay attention to the SELinux configuration.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name | Type       | Mandatory| Description                                |
  | ------- | ----------- | ---- | ------------------------------------ |
  | rawData | ArrayBuffer | Yes  | Raw data to write. The size cannot exceed 128 MB.|
  | size    | number      | Yes  | Size of the raw data, in bytes.   |

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match; <br> 3.Failed to obtain arrayBuffer information; <br> 4.The transferred size cannot be obtained; <br> 5.The transferred size is less than or equal to 0; <br> 6.The transferred size is greater than the byte length of ArrayBuffer. |
  | 1900009  | Failed to write data to the message sequence. |

**Example**

```ts
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

### readRawData<sup>(deprecated)</sup>

readRawData(size: number): number[]

Reads raw data from this **MessageSequence** object.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 11. Use [readRawDataBuffer](#readrawdatabuffer11) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description                    |
  | ------ | ------ | ---- | ------------------------ |
  | size   | number | Yes  | Size of the raw data to read.|

**Return value**

  | Type    | Description                          |
  | -------- | ------------------------------ |
  | number[] | Raw data obtained, in bytes.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match. |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readRawDataBuffer<sup>11+</sup>

readRawDataBuffer(size: number): ArrayBuffer

Reads raw data from this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description                    |
  | ------ | ------ | ---- | ------------------------ |
  | size   | number | Yes  | Size of the raw data to read.|

**Return value**

  | Type    | Description                          |
  | -------- | ------------------------------ |
  | ArrayBuffer | Raw data obtained, in bytes.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match. |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

### writeArrayBuffer<sup>12+</sup>

writeArrayBuffer(buf: ArrayBuffer, typeCode: TypeCode): void

Writes data of the ArrayBuffer type to this **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name   | Type                     | Mandatory| Description                       |
  | --------- | ------------------------- | ---- | --------------------------- |
  | buf       | ArrayBuffer               | Yes  | Data to write.  |
  | typeCode  | [TypeCode](#typecode12)   | Yes  | TypedArray type of the ArrayBuffer data.<br>The underlying write mode is determined based on the enum value of **TypeCode** passed by the service.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The parameter is an empty array; <br> 2.The number of parameters is incorrect; <br> 3.The parameter type does not match; <br> 4.The obtained value of typeCode is incorrect; <br> 5.Failed to obtain arrayBuffer information. |
  | 1900009  | Failed to write data to the message sequence. |

**Example**

```ts
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

### readArrayBuffer<sup>12+</sup>

readArrayBuffer(typeCode: TypeCode): ArrayBuffer

Reads data of the ArrayBuffer type from this **MessageSequence**.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name  | Type                    | Mandatory| Description                  |
  | -------- | ----------------------- | ---- | ------------------------|
  | typeCode | [TypeCode](#typecode12) | Yes  | TypedArray type of the ArrayBuffer data.<br>The underlying read mode is determined based on the enum value of **TypeCode** passed by the service. |

**Return value**

  | Type    | Description                                        |
  | -------- | -------------------------------------------- |
  | ArrayBuffer | Data of the ArrayBuffer type read, in bytes.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match; <br> 3.The obtained value of typeCode is incorrect; |
  | 1900010  | Failed to read data from the message sequence. |

**Example**

```ts
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

## MessageParcel<sup>(deprecated)</sup>

Provides APIs for reading and writing data in specific format. During RPC, the sender can use the **write()** method provided by **MessageParcel** to write data in specific format to a **MessageParcel** object. The receiver can use the **read()** method provided by **MessageParcel** to read data in specific format from a **MessageParcel** object. The data formats include basic data types and arrays, IPC objects, interface tokens, and custom sequenceable objects.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [MessageSequence](#messagesequence9) instead.

### create<sup>(deprecated)</sup>

static create(): MessageParcel

Creates a **MessageParcel** object. This method is a static method.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [create](#create9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type         | Description                         |
  | ------------- | ----------------------------- |
  | [MessageParcel](#messageparceldeprecated) | **MessageParcel** object created.|

**Example**

<!--deprecated_code_no_check-->
```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  hilog.info(0x0000, 'testTag', 'data is ' + data);

  // When the MessageParcel object is no longer used, the service calls the reclaim method to release resources.
  data.reclaim();
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

### reclaim<sup>(deprecated)</sup>

reclaim(): void

Reclaims the **MessageParcel** object that is no longer used.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [reclaim](#reclaim9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Example**

<!--deprecated_code_no_check-->
```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let reply = rpc.MessageParcel.create();
  reply.reclaim();
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

### writeRemoteObject<sup>(deprecated)</sup>

writeRemoteObject(object: IRemoteObject): boolean

Serializes a remote object and writes it to this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [writeRemoteObject](#writeremoteobject9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type                           | Mandatory| Description                                   |
  | ------ | ------------------------------- | ---- | --------------------------------------- |
  | object | [IRemoteObject](#iremoteobject) | Yes  | Remote object to serialize and write to the **MessageParcel** object.|

**Return value**

  | Type   | Description                                     |
  | ------- | ----------------------------------------- |
  | boolean | Returns **true** if the operation is successful; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteRequest(code: number, data: rpc.MessageParcel, reply: rpc.MessageParcel, option: rpc.MessageOption): boolean {
    // Process services based on the actual service logic.
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

### readRemoteObject<sup>(deprecated)</sup>

readRemoteObject(): IRemoteObject

Reads the remote object from this **MessageParcel** object. You can use this method to deserialize the **MessageParcel** object to generate an **IRemoteObject**. The remote objects are read in the order in which they are written to this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [readRemoteObject](#readremoteobject9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type                           | Description              |
  | ------------------------------- | ------------------ |
  | [IRemoteObject](#iremoteobject) | Remote object obtained.|

**Example**

<!--deprecated_code_no_check-->
```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteRequest(code: number, data: rpc.MessageParcel, reply: rpc.MessageParcel,
    option: rpc.MessageOption): boolean {
    // Process services based on the actual service logic.
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

### writeInterfaceToken<sup>(deprecated)</sup>

writeInterfaceToken(token: string): boolean

Writes an interface token to this **MessageParcel** object. The remote object can use this interface token to verify the communication.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [writeInterfaceToken](#writeinterfacetoken9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description              |
  | ------ | ------ | ---- | ------------------ |
  | token  | string | Yes  | Interface token to write. The length of the string must be less than 40960 bytes.|

**Return value**

  | Type   | Description                                     |
  | ------- | ----------------------------------------- |
  | boolean | Returns **true** if the operation is successful; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readInterfaceToken<sup>(deprecated)</sup>

readInterfaceToken(): string

Reads the interface token from this **MessageParcel** object. The interface token is read in the sequence in which it is written to the **MessageParcel** object. The local object can use it to verify the communication.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [readInterfaceToken](#readinterfacetoken9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description                    |
  | ------ | ------------------------ |
  | string | Interface token obtained.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### getSize<sup>(deprecated)</sup>

getSize(): number

Obtains the data size of this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [getSize](#getsize9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description                                         |
  | ------ | --------------------------------------------- |
  | number | Size of the **MessageParcel** object obtained, in bytes.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### getCapacity<sup>(deprecated)</sup>

getCapacity(): number

Obtains the capacity of this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [getCapacity](#getcapacity9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description                                         |
  | ------ | --------------------------------------------- |
  | number | **MessageParcel** capacity obtained, in bytes.|

**Example**

<!--deprecated_code_no_check-->
```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let data = rpc.MessageParcel.create();
  let data = rpc.MessageParcel.create();
  let result = data.getCapacity();
  hilog.info(0x0000, 'testTag', 'capacity is ' + result);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

### setSize<sup>(deprecated)</sup>

setSize(size: number): boolean

Sets the size of data contained in this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [setSize](#setsize9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description                                       |
  | ------ | ------ | ---- | ------------------------------------------- |
  | size   | number | Yes  | Data size to set, in bytes.|

**Return value**

  | Type   | Description                             |
  | ------- | --------------------------------- |
  | boolean | Returns **true** if the operation is successful; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### setCapacity<sup>(deprecated)</sup>

setCapacity(size: number): boolean

Sets the storage capacity of this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [setCapacity](#setcapacity9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description                                       |
  | ------ | ------ | ---- | ------------------------------------------- |
  | size   | number | Yes  | Storage capacity to set, in bytes.|

**Return value**

  | Type   | Description                             |
  | ------- | --------------------------------- |
  | boolean | Returns **true** if the operation is successful; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### getWritableBytes<sup>(deprecated)</sup>

getWritableBytes(): number

Obtains the writable capacity of this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [getWritableBytes](#getwritablebytes9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description                                               |
  | ------ | --------------------------------------------------- |
  | number | **MessageParcel** writable capacity obtained, in bytes.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### getReadableBytes<sup>(deprecated)</sup>

getReadableBytes(): number

Obtains the readable capacity of this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [getReadableBytes](#getreadablebytes9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description                                               |
  | ------ | --------------------------------------------------- |
  | number | **MessageParcel** object readable capacity, in bytes.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### getReadPosition<sup>(deprecated)</sup>

getReadPosition(): number

Obtains the read position of this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [getReadPosition](#getreadposition9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description                                   |
  | ------ | --------------------------------------- |
  | number | Current read position of the **MessageParcel** object.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### getWritePosition<sup>(deprecated)</sup>

getWritePosition(): number

Obtains the write position of this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [getWritePosition](#getwriteposition9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description                                   |
  | ------ | --------------------------------------- |
  | number | Current write position of the **MessageParcel** object.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### rewindRead<sup>(deprecated)</sup>

rewindRead(pos: number): boolean

Moves the read pointer to the specified position.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [rewindRead](#rewindread9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description                    |
  | ------ | ------ | ---- | ------------------------ |
  | pos    | number | Yes  | Position from which data is to read.|

**Return value**

  | Type   | Description                                             |
  | ------- | ------------------------------------------------- |
  | boolean | Returns **true** if the read position changes; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### rewindWrite<sup>(deprecated)</sup>

rewindWrite(pos: number): boolean

Moves the write pointer to the specified position.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [reWindWrite](#rewindwrite9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description                    |
  | ------ | ------ | ---- | ------------------------ |
  | pos    | number | Yes  | Position from which data is to write.|

**Return value**

  | Type   | Description                                         |
  | ------- | --------------------------------------------- |
  | boolean | Returns **true** if the write position changes; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### writeByte<sup>(deprecated)</sup>

writeByte(val: number): boolean

Writes a Byte value to this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [writeByte](#writebyte9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description            |
  | ------ | ------ | ---- | ---------------- |
  | val    | number | Yes  | Byte value to write.|

**Return value**

  | Type   | Description                         |
  | ------- | ----------------------------- |
  | boolean | Returns **true** if the data is written successfully; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readByte<sup>(deprecated)</sup>

readByte(): number

Reads the byte value from this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [readByte](#readbyte9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description        |
  | ------ | ------------ |
  | number | Byte value read.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### writeShort<sup>(deprecated)</sup>

writeShort(val: number): boolean

Writes a short int value to this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [writeShort](#writeshort9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description              |
  | ------ | ------ | ---- | ------------------ |
  | val    | number | Yes  | Short integer to write.|

**Return value**

  | Type   | Description                         |
  | ------- | ----------------------------- |
  | boolean | Returns **true** if the data is written successfully; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readShort<sup>(deprecated)</sup>

readShort(): number

Reads the short integer from this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [readShort](#readshort9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description          |
  | ------ | -------------- |
  | number | Short integer read.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### writeInt<sup>(deprecated)</sup>

writeInt(val: number): boolean

Writes an int value to this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [writeInt](#writeint9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description            |
  | ------ | ------ | ---- | ---------------- |
  | val    | number | Yes  | Integer to write.|

**Return value**

  | Type   | Description                         |
  | ------- | ----------------------------- |   
  | boolean | Returns **true** if the data is written successfully; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readInt<sup>(deprecated)</sup>

readInt(): number

Reads the integer from this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [readInt](#readint9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description        |
  | ------ | ------------ |
  | number | Integer read.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### writeLong<sup>(deprecated)</sup>

writeLong(val: number): boolean

Writes a long int value to this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [writeLong](#writelong9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description            |
  | ------ | ------ | ---- | ---------------- |
  | val    | number | Yes  | Long int value to write.|

**Return value**

  | Type   | Description                             |
  | ------- | --------------------------------- |
  | boolean | Returns **true** if the data is written successfully; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readLong<sup>(deprecated)</sup>

readLong(): number

Reads the long int value from this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [readLong](#readlong9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description          |
  | ------ | -------------- |
  | number | Long integer read.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### writeFloat<sup>(deprecated)</sup>

writeFloat(val: number): boolean

Writes a double value to this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [writeFloat](#writefloat9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description            |
  | ------ | ------ | ---- | ---------------- |
  | val    | number | Yes  | Double value to write.|

**Return value**

  | Type   | Description                             |
  | ------- | --------------------------------- |
  | boolean | Returns **true** if the data is written successfully; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readFloat<sup>(deprecated)</sup>

readFloat(): number

Reads the double value from this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [readFloat](#readfloat9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description        |
  | ------ | ------------ |
  | number | Double value read.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### writeDouble<sup>(deprecated)</sup>

writeDouble(val: number): boolean

Writes a double value to this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [writeDouble](#writedouble9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description                  |
  | ------ | ------ | ---- | ---------------------- |
  | val    | number | Yes  | Double value to write.|

**Return value**

  | Type   | Description                             |
  | ------- | --------------------------------- |
  | boolean | Returns **true** if the data is written successfully; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readDouble<sup>(deprecated)</sup>

readDouble(): number

Reads the double value from this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [readDouble](#readdouble9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description              |
  | ------ | ------------------ |
  | number | Double value read.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### writeBoolean<sup>(deprecated)</sup>

writeBoolean(val: boolean): boolean

Writes a Boolean value to this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [writeBoolean](#writeboolean9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type   | Mandatory| Description            |
  | ------ | ------- | ---- | ---------------- |
  | val    | boolean | Yes  | Boolean value to write.|

**Return value**

  | Type   | Description                             |
  | ------- | --------------------------------- |
  | boolean | Returns **true** if the data is written successfully; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readBoolean<sup>(deprecated)</sup>

readBoolean(): boolean

Reads the Boolean value from this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [readBoolean](#readboolean9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type   | Description                |
  | ------- | -------------------- |
  | boolean | Boolean value read.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### writeChar<sup>(deprecated)</sup>

writeChar(val: number): boolean

Writes a single character value to this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [writeChar](#writechar9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description                |
  | ------ | ------ | ---- | -------------------- |
  | val    | number | Yes  | **Char** value to write.|

**Return value**

  | Type   | Description                         |
  | ------- | ----------------------------- |
  | boolean | Returns **true** if the data is written successfully; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readChar<sup>(deprecated)</sup>

readChar(): number

Reads the single character value from this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [readChar](#readchar9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description            |
  | ------ | ---------------- |
  | number | **Char** value read.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### writeString<sup>(deprecated)</sup>

writeString(val: string): boolean

Writes a string to this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [writeString](#writestring9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description                                     |
  | ------ | ------ | ---- | ----------------------------------------- |
  | val    | string | Yes  | String to write. The length of the string must be less than 40960 bytes.|

**Return value**

  | Type   | Description                             |
  | ------- | --------------------------------- |
  | boolean | Returns **true** if the data is written successfully; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readString<sup>(deprecated)</sup>

readString(): string

Reads the string from this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [readString](#readstring9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description          |
  | ------ | -------------- |
  | string | String read.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### writeSequenceable<sup>(deprecated)</sup>

writeSequenceable(val: Sequenceable): boolean

Writes a **Sequenceable** object to this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [writeParcelable](#writeparcelable9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type                         | Mandatory| Description                |
  | ------ | ----------------------------- | ---- | -------------------- |
  | val    | [Sequenceable](#sequenceabledeprecated) | Yes  | **Sequenceable** object to write.|

**Return value**

  | Type   | Description                            |
  | ------- | -------------------------------- |
  | boolean | Returns **true** if the data is written successfully; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readSequenceable<sup>(deprecated)</sup>

readSequenceable(dataIn: Sequenceable): boolean

Reads member variables from this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [readParcelable](#readparcelable9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type                         | Mandatory   | Description                                          |
  | ------ | ----------------------------- | ------- | ---------------------------------------------- |
  | dataIn | [Sequenceable](#sequenceabledeprecated) | Yes  | Object that reads member variables from the **MessageParcel** object.|

**Return value**

  | Type   | Description                                    |
  | ------- | ---------------------------------------- |
  | boolean | Returns **true** if the operation is successful; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### writeByteArray<sup>(deprecated)</sup>

writeByteArray(byteArray: number[]): boolean

Writes a byte array to this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [writeByteArray](#writebytearray9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name   | Type    | Mandatory| Description              |
  | --------- | -------- | ---- | ------------------ |
  | byteArray | number[] | Yes  | Byte array to write.|

**Return value**

  | Type   | Description                            |
  | ------- | -------------------------------- |
  | boolean | Returns **true** if the data is written successfully; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readByteArray<sup>(deprecated)</sup>

readByteArray(dataIn: number[]): void

Reads the byte array from this **MessageParcel** object and writes it to the created empty array.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [readByteArray](#readbytearray9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type    | Mandatory| Description              |
  | ------ | -------- | ---- | ------------------ |
  | dataIn | number[] | Yes  | Byte array to read.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readByteArray<sup>(deprecated)</sup>

readByteArray(): number[]

Reads the byte array from this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [readByteArray](#readbytearray9-1) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type    | Description          |
  | -------- | -------------- |
  | number[] | Byte array read.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### writeShortArray<sup>(deprecated)</sup>

writeShortArray(shortArray: number[]): boolean

Writes a short array to this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [writeShortArray](#writeshortarray9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name    | Type    | Mandatory| Description                |
  | ---------- | -------- | ---- | -------------------- |
  | shortArray | number[] | Yes  | Short array to write.|

**Return value**

  | Type   | Description                            |
  | ------- | -------------------------------- |
  | boolean | Returns **true** if the data is written successfully; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readShortArray<sup>(deprecated)</sup>

readShortArray(dataIn: number[]): void

Reads the short array from this **MessageParcel** object and writes it to the created empty array.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [readShortArray](#readshortarray9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type    | Mandatory| Description                |
  | ------ | -------- | ---- | -------------------- |
  | dataIn | number[] | Yes  | Short array to read.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readShortArray<sup>(deprecated)</sup>

readShortArray(): number[]

Reads the short array from this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [readShortArray](#readshortarray9-1) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type    | Description            |
  | -------- | ---------------- |
  | number[] | Short array read.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### writeIntArray<sup>(deprecated)</sup>

writeIntArray(intArray: number[]): boolean

Writes an integer array to this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [writeIntArray](#writeintarray9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name  | Type    | Mandatory| Description              |
  | -------- | -------- | ---- | ------------------ |
  | intArray | number[] | Yes  | Integer array to write.|

**Return value**

  | Type   | Description                            |
  | ------- | -------------------------------- |
  | boolean | Returns **true** if the data is written successfully; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readIntArray<sup>(deprecated)</sup>

readIntArray(dataIn: number[]): void

Reads the integer array from this **MessageParcel** object and writes it to the created empty array.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [readIntArray](#readintarray9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type    | Mandatory| Description              |
  | ------ | -------- | ---- | ------------------ |
  | dataIn | number[] | Yes  | Integer array to read.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readIntArray<sup>(deprecated)</sup>

readIntArray(): number[]

Reads the integer array from this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [readIntArray](#readintarray9-1) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type    | Description          |
  | -------- | -------------- |
  | number[] | Integer array read.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### writeLongArray<sup>(deprecated)</sup>

writeLongArray(longArray: number[]): boolean

Writes a long array to this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [writeLongArray](#writelongarray9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name   | Type    | Mandatory| Description                |
  | --------- | -------- | ---- | -------------------- |
  | longArray | number[] | Yes  | Long array to write.|

**Return value**

  | Type   | Description                         |
  | ------- | ----------------------------- |
  | boolean | Returns **true** if the data is written successfully; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readLongArray<sup>(deprecated)</sup>

readLongArray(dataIn: number[]): void

Reads the long array from this **MessageParcel** object and writes it to the created empty array.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [readLongArray](#readlongarray9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type    | Mandatory| Description                |
  | ------ | -------- | ---- | -------------------- |
  | dataIn | number[] | Yes  | Long array to read.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readLongArray<sup>(deprecated)</sup>

readLongArray(): number[]

Reads the long array from this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [readLongArray](#readlongarray9-1) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

 | Type    | Description            |
 | -------- | ---------------- |
 | number[] | Long array read.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### writeFloatArray<sup>(deprecated)</sup>

writeFloatArray(floatArray: number[]): boolean

Writes a double array to this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [writeFloatArray](#writefloatarray9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type| Mandatory| Description |
  | ---------- | -------- | ---- | --- |
  | floatArray | number[] | Yes  | Double array to write. The system processes float data as that of the double type. Therefore, the total number of bytes occupied by a float array must be calculated as the double type.|

**Return value**

  | Type   | Description                            |
  | ------- | -------------------------------- |
  | boolean | Returns **true** if the data is written successfully; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readFloatArray<sup>(deprecated)</sup>

readFloatArray(dataIn: number[]): void

Reads the double array from this **MessageParcel** object and writes it to the created empty array.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [readFloatArray](#readfloatarray9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type    | Mandatory| Description  |
  | ------ | -------- | ---- | ------ |
  | dataIn | number[] | Yes  | Double array to read. The system processes float data as that of the double type. Therefore, the total number of bytes occupied by a float array must be calculated as the double type.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readFloatArray<sup>(deprecated)</sup>

readFloatArray(): number[]

Reads the double array from this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [readFloatArray](#readfloatarray9-1) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type    | Description          |
  | -------- | -------------- |
  | number[] | Double array read.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### writeDoubleArray<sup>(deprecated)</sup>

writeDoubleArray(doubleArray: number[]): boolean

Writes a double array to this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [writeDoubleArray](#writedoublearray9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name     | Type    | Mandatory| Description                    |
  | ----------- | -------- | ---- | ------------------------ |
  | doubleArray | number[] | Yes  | Double array to write.|

**Return value**

  | Type   | Description                            |
  | ------- | -------------------------------- |
  | boolean | Returns **true** if the data is written successfully; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readDoubleArray<sup>(deprecated)</sup>

readDoubleArray(dataIn: number[]): void

Reads the double array from this **MessageParcel** object and writes it to the created empty array.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [readDoubleArray](#readdoublearray9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type    | Mandatory| Description                    |
  | ------ | -------- | ---- | ------------------------ |
  | dataIn | number[] | Yes  | Double array to read.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readDoubleArray<sup>(deprecated)</sup>

readDoubleArray(): number[]

Reads the double array from this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [readDoubleArray](#readdoublearray9-1) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type    | Description                |
  | -------- | -------------------- |
  | number[] | Double array read.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### writeBooleanArray<sup>(deprecated)</sup>

writeBooleanArray(booleanArray: boolean[]): boolean

Writes a Boolean array to this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [writeBooleanArray](#writebooleanarray9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name      | Type     | Mandatory| Description              |
  | ------------ | --------- | ---- | ------------------ |
  | booleanArray | boolean[] | Yes  | Boolean array to write.|

**Return value**

  | Type   | Description                            |
  | ------- | -------------------------------- |
  | boolean | Returns **true** if the data is written successfully; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readBooleanArray<sup>(deprecated)</sup>

readBooleanArray(dataIn: boolean[]): void

Reads the Boolean array from this **MessageParcel** object and writes it to the created empty array.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [readBooleanArray](#readbooleanarray9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type     | Mandatory| Description              |
  | ------ | --------- | ---- | ------------------ |
  | dataIn | boolean[] | Yes  | Boolean array to read.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readBooleanArray<sup>(deprecated)</sup>

readBooleanArray(): boolean[]

Reads the Boolean array from this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [readBooleanArray](#readbooleanarray9-1) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type     | Description          |
  | --------- | -------------- |
  | boolean[] | Boolean array read.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### writeCharArray<sup>(deprecated)</sup>

writeCharArray(charArray: number[]): boolean

Writes a single character array to this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [writeCharArray](#writechararray9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name   | Type    | Mandatory| Description                  |
  | --------- | -------- | ---- | ---------------------- |
  | charArray | number[] | Yes  | Character array to write.|

**Return value**

  | Type   | Description                            |
  | ------- | -------------------------------- |
  | boolean | Returns **true** if the data is written successfully; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readCharArray<sup>(deprecated)</sup>

readCharArray(dataIn: number[]): void

Reads the character array from this **MessageParcel** object and writes it to the created empty array.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [readCharArray](#readchararray9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type    | Mandatory| Description                  |
  | ------ | -------- | ---- | ---------------------- |
  | dataIn | number[] | Yes  | Character array to read.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readCharArray<sup>(deprecated)</sup>

readCharArray(): number[]

Reads the single character array from this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [readCharArray](#readchararray9-1) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type    | Description              |
  | -------- | ------------------ |
  | number[] | Character array read.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### writeStringArray<sup>(deprecated)</sup>

writeStringArray(stringArray: string[]): boolean

Writes a string array to this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [writeStringArray](#writestringarray9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name     | Type    | Mandatory| Description            |
  | ----------- | -------- | ---- | ---------------- |
  | stringArray | string[] | Yes  | String array to write. The length of a single element in the array must be less than 40960 bytes.|

**Return value**

  | Type   | Description|
  | ------- | -------------------------------- |
  | boolean | Returns **true** if the data is written successfully; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readStringArray<sup>(deprecated)</sup>

readStringArray(dataIn: string[]): void

Reads the string array from this **MessageParcel** object and writes it to the created empty array.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [readStringArray](#readstringarray9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type    | Mandatory| Description                |
  | ------ | -------- | ---- | -------------------- |
  | dataIn | string[] | Yes  | String array to read.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readStringArray<sup>(deprecated)</sup>

readStringArray(): string[]

Reads the string array from this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [readStringArray](#readstringarray9-1) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type    | Description            |
  | -------- | ---------------- |
  | string[] | String array read.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### writeNoException<sup>(deprecated)</sup>

writeNoException(): void

Writes information to this **MessageParcel** object indicating that no exception occurred.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [writeNoException](#writenoexception9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readException<sup>(deprecated)</sup>

readException(): void

Reads the exception information from this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [readException](#readexception9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.getUIContext().getHostContext()** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

<!--code_no_check-->
```ts
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

  The proxy object in the **onConnect** callback can be assigned a value only after the ability is connected asynchronously. Then, **sendRequest()** of the proxy object is called to send a message.
<!--deprecated_code_no_check-->
```ts
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
      hilog.error(0x0000, 'testTag', 'sendRequest got exception: ' + e);
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

### writeSequenceableArray<sup>(deprecated)</sup>

writeSequenceableArray(sequenceableArray: Sequenceable[]): boolean

Writes a **Sequenceable** array to this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [writeParcelableArray](#writeparcelablearray9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

| Name           | Type                                     | Mandatory| Description                      |
| ----------------- | ----------------------------------------- | ---- | -------------------------- |
| sequenceableArray | [Sequenceable](#sequenceabledeprecated)[] | Yes  | **Sequenceable** array to write.|

**Return value**

  | Type   | Description                            |
  | ------- | -------------------------------- |
  | boolean | Returns **true** if the data is written successfully; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readSequenceableArray<sup>(deprecated)</sup>

readSequenceableArray(sequenceableArray: Sequenceable[]): void

Reads the **Sequenceable** array from this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [readParcelableArray](#readparcelablearray9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

| Name           | Type                                     | Mandatory| Description                      |
| ----------------- | ----------------------------------------- | ---- | -------------------------- |
| sequenceableArray | [Sequenceable](#sequenceabledeprecated)[] | Yes  | **Sequenceable** array to read.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### writeRemoteObjectArray<sup>(deprecated)</sup>

writeRemoteObjectArray(objectArray: IRemoteObject[]): boolean

Writes an **IRemoteObject** array to this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [writeRemoteObjectArray](#writeremoteobjectarray9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name     | Type           | Mandatory| Description |
  | ----------- | --------------- | ---- | ----- |
  | objectArray | [IRemoteObject](#iremoteobject)[] | Yes  | **IRemoteObject** array to write.|

**Return value**

  | Type   | Description                                                                                                                |
  | ------- | -------------------------------- |
  | boolean | Returns **true** if the data is written successfully; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteRequest(code: number, data: rpc.MessageParcel, reply: rpc.MessageParcel,
    option: rpc.MessageOption): boolean {
    // The specific processing is determined by the service.
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

### readRemoteObjectArray<sup>(deprecated)</sup>

readRemoteObjectArray(objects: IRemoteObject[]): void

Reads the **IRemoteObject** array from this **MessageParcel** object and writes it to the created empty array.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [readRemoteObjectArray](#readremoteobjectarray9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name | Type           | Mandatory| Description     |
  | ------- | --------------- | ---- | --------- |
  | objects | [IRemoteObject](#iremoteobject)[] | Yes  | **IRemoteObject** array to read.|

**Example**

<!--deprecated_code_no_check-->
```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteRequest(code: number, data: rpc.MessageParcel, reply: rpc.MessageParcel,
    option: rpc.MessageOption): boolean {
    // The specific processing is determined by the service.
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

### readRemoteObjectArray<sup>(deprecated)</sup>

readRemoteObjectArray(): IRemoteObject[]

Reads the **IRemoteObject** array from this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [readRemoteObjectArray](#readremoteobjectarray9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type           | Description                       |
  | --------------- | --------------------------- |
  | [IRemoteObject](#iremoteobject)[] | **IRemoteObject** object array obtained.|

**Example**

<!--deprecated_code_no_check-->
```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteRequest(code: number, data: rpc.MessageParcel, reply: rpc.MessageParcel,
    option: rpc.MessageOption): boolean {
    // The specific processing is determined by the service.
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

### closeFileDescriptor<sup>(deprecated)</sup>

static closeFileDescriptor(fd: number): void

Closes a file descriptor. This API is a static method.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [closeFileDescriptor](#closefiledescriptor9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description                |
  | ------ | ------ | ---- | -------------------- |
  | fd     | number | Yes  | File descriptor to close.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### dupFileDescriptor<sup>(deprecated)</sup>

static dupFileDescriptor(fd: number) :number

Duplicates a file descriptor. This API is a static method.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [dupFileDescriptor](#dupfiledescriptor9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description                    |
  | ------ | ------ | ---- | ------------------------ |
  | fd     | number | Yes  | File descriptor to duplicate.|

**Return value**

  | Type  | Description                |
  | ------ | -------------------- |
  | number | New file descriptor.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### containFileDescriptors<sup>(deprecated)</sup>

containFileDescriptors(): boolean

Checks whether this **MessageParcel** object contains file descriptors.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [containFileDescriptors](#containfiledescriptors9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type   | Description                                         |
  | ------- | --------------------------------------------- |
  | boolean |Returns **true** if the **MessageParcel** object contains file descriptors; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### writeFileDescriptor<sup>(deprecated)</sup>

writeFileDescriptor(fd: number): boolean

Writes a file descriptor to this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [writeFileDescriptor](#writefiledescriptor9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description        |
  | ------ | ------ | ---- | ------------ |
  | fd     | number | Yes  | File descriptor to write.|

**Return value**

  | Type   | Description                            |
  | ------- | -------------------------------- |
  | boolean | Returns **true** if the operation is successful; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readFileDescriptor<sup>(deprecated)</sup>

readFileDescriptor(): number

Reads the file descriptor from this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [readFileDescriptor](#readfiledescriptor9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description            |
  | ------ | ---------------- |
  | number | File descriptor read.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### writeAshmem<sup>(deprecated)</sup>

writeAshmem(ashmem: Ashmem): boolean

Writes an anonymous shared object to this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [writeAshmem](#writeashmem9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

| Name| Type  | Mandatory| Description                               |
| ------ | ------ | ---- | ----------------------------------- |
| ashmem | [Ashmem](#ashmem8) | Yes  | Anonymous shared object to write.|

**Return value**

  | Type   | Description                            |
  | ------- | -------------------------------- |
  | boolean | Returns **true** if the data is written successfully; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readAshmem<sup>(deprecated)</sup>

readAshmem(): Ashmem

Reads the anonymous shared object from this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [readAshmem](#readashmem9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

| Type  | Description              |
| ------ | ------------------ |
| [Ashmem](#ashmem8) | Anonymous share object obtained.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### getRawDataCapacity<sup>(deprecated)</sup>

getRawDataCapacity(): number

Obtains the maximum amount of raw data that can be held by this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [getRawDataCapacity](#getrawdatacapacity9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description                                                      |
  | ------ | ---------------------------------------------------------- |
  | number | Maximum amount of raw data that **MessageParcel** can hold, that is, 128 MB.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### writeRawData<sup>(deprecated)</sup>

writeRawData(rawData: number[], size: number): boolean

Writes raw data to this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [writeRawDataBuffer](#writerawdatabuffer11) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name | Type    | Mandatory| Description                              |
  | ------- | -------- | ---- | ---------------------------------- |
  | rawData | number[] | Yes  | Raw data to write. The size cannot exceed 128 MB.|
  | size    | number   | Yes  | Size of the raw data, in bytes.|

**Return value**

  | Type   | Description                            |
  | ------- | -------------------------------- |
  | boolean | Returns **true** if the data is written successfully; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readRawData<sup>(deprecated)</sup>

readRawData(size: number): number[]

Reads raw data from this **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [readRawDataBuffer](#readrawdatabuffer11) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description                    |
  | ------ | ------ | ---- | ------------------------ |
  | size   | number | Yes  | Size of the raw data to read.|

**Return value**

  | Type    | Description                          |
  | -------- | ------------------------------ |
  | number[] | Raw data obtained, in bytes.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

## Parcelable<sup>9+</sup>

Writes an object to a **MessageSequence** and reads it from the **MessageSequence** during IPC.

### marshalling<sup>9+</sup>

marshalling(dataOut: MessageSequence): boolean

Marshals this **Parcelable** object into a **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

| Name | Type           | Mandatory| Description                                       |
| ------- | --------------- | ---- | ------------------------------------------- |
| dataOut |[MessageSequence](#messagesequence9)| Yes  | **MessageSequence** object to which the **Parcelable** object is to be marshaled.|

**Return value**

  | Type   | Description                            |
  | ------- | -------------------------------- |
  | boolean | Returns **true** if the operation is successful; returns **false** otherwise.|

**Example**

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

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
    hilog.info(0x0000, 'testTag', 'readInt is ' + this.num + ' readString is ' + this.str);
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
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

### unmarshalling<sup>9+</sup>

unmarshalling(dataIn: MessageSequence): boolean

Unmarshals this **Parcelable** object from a **MessageSequence** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

| Name| Type           | Mandatory| Description                                           |
| ------ | --------------- | ---- | ----------------------------------------------- |
| dataIn | [MessageSequence](#messagesequence9) | Yes  | **MessageSequence** object from which the **Parcelable** object is to be unmarshaled.|

**Return value**

  | Type   | Description                                    |
  | ------- | ---------------------------------------- |
  | boolean | Returns **true** if the operation is successful; returns **false** otherwise.|

**Example**

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

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
    hilog.info(0x0000, 'testTag', 'readInt is ' + this.num + ' readString is ' + this.str);
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
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## Sequenceable<sup>(deprecated)</sup>

Writes objects of classes to a **MessageParcel** and reads them from the **MessageParcel** during IPC.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [Parcelable](#parcelable9) instead.

### marshalling<sup>(deprecated)</sup>

marshalling(dataOut: MessageParcel): boolean

Marshals the sequenceable object into a **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [marshalling](#marshalling9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name | Type                                     | Mandatory| Description                                     |
  | ------- | ----------------------------------------- | ---- | ----------------------------------------- |
  | dataOut | [MessageParcel](#messageparceldeprecated) | Yes  | **MessageParcel** object to which the sequenceable object is to be marshaled.|

**Return value**

  | Type   | Description                             |
  | ------- | --------------------------------  |
  | boolean | Returns **true** if the operation is successful; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### unmarshalling<sup>(deprecated)</sup>

unmarshalling(dataIn: MessageParcel): boolean

Unmarshals this sequenceable object from a **MessageParcel** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [unmarshalling](#unmarshalling9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type                                     | Mandatory| Description                                         |
  | ------ | ----------------------------------------- | ---- | --------------------------------------------- |
  | dataIn | [MessageParcel](#messageparceldeprecated) | Yes  | **MessageParcel** object in which the sequenceable object is to be unmarshaled.|

**Return value**

  | Type   | Description                                    |
  | ------- | ---------------------------------------- |
  | boolean | Returns **true** if the operation is successful; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

## IRemoteBroker

Represents the holder of a remote proxy object. It is used to obtain a proxy object.

### asObject

asObject(): IRemoteObject

Obtains a proxy or remote object. This API must be implemented by its derived classes.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type | Description |
  | ----- | ----- |
  | [IRemoteObject](#iremoteobject) | Returns the **RemoteObject** if it is the caller; returns the [IRemoteObject](#iremoteobject), the holder of this **RemoteProxy** object, if the caller is a [RemoteProxy](#remoteproxy) object.|

**Example**

```ts
import { rpc } from '@kit.IPCKit';

class TestAbility extends rpc.RemoteObject {
  asObject() {
    return this;
  }
}
let remoteObject = new TestAbility("testObject").asObject();
```

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.getUIContext().getHostContext()** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

<!--code_no_check-->
```ts
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
let want: Want  = {
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

The proxy object in the **onConnect** callback can be assigned a value only after the ability is connected asynchronously. Then, **asObject()** of the proxy object is called to obtain the proxy or remote object.

```ts
import { rpc } from '@kit.IPCKit';

class TestProxy {
  remote: rpc.IRemoteObject;
  constructor(remote: rpc.IRemoteObject) {
    this.remote = remote;
  }
  asObject() {
    return this.remote;
  }
}
if (proxy != undefined) {
  let iRemoteObject = new TestProxy(proxy).asObject();
}
```

## DeathRecipient

Subscribes to death notifications of a remote object. When the remote object is dead, the local end will receive a notification and **[onRemoteDied](#onremotedied)** will be called. A remote object is dead when the process holding the object is terminated or the device of the remote object is shut down or restarted. If the local and remote objects belong to different devices, the remote object is dead when the device holding the remote object is detached from the network. 

### onRemoteDied

onRemoteDied(): void

Called to perform subsequent operations when a death notification of the remote object is received.

**System capability**: SystemCapability.Communication.IPC.Core

**Example**

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MyDeathRecipient implements rpc.DeathRecipient {
  onRemoteDied() {
    hilog.info(0x0000, 'testTag', 'server died');
  }
}
```

## RequestResult<sup>9+</sup>

Defines the response to the request.

**System capability**: SystemCapability.Communication.IPC.Core

| Name   | Type           | Read-Only| Optional| Description                                 |
| ------- | --------------- | ---- | ---- |-------------------------------------- |
| errCode | number          | No  | No  | Error code.                             |
| code    | number          | No  | No  | Message code.                           |
| data    | [MessageSequence](#messagesequence9) | No  | No  | **MessageSequence** object sent to the remote process.|
| reply   | [MessageSequence](#messagesequence9) | No  | No  | **MessageSequence** object returned by the remote process.  |

## SendRequestResult<sup>(deprecated)</sup>

Defines the response to the request.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [RequestResult](#requestresult9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

  | Name   | Type         | Read-Only| Optional| Description                               |
  | ------- | ------------- | ---- | ---- | ----------------------------------- |
  | errCode | number        | No  | No  | Error code.                           |
  | code    | number        | No  | No  | Message code.                         |
  | data    | [MessageParcel](#messageparceldeprecated) | No  | No  | **MessageParcel** object sent to the remote process.|
  | reply   | [MessageParcel](#messageparceldeprecated) | No  | No  | **MessageParcel** object returned by the remote process.  |

## CallingInfo<sup>23+</sup>

Defines the IPC context, including the PID and UID, local and remote device IDs, and whether the API is invoked on the same device.

**System capability**: SystemCapability.Communication.IPC.Core

| Name   | Type           | Read-Only| Optional| Description                                 |
| ------- | --------------- | ---- | ---- |-------------------------------------- |
| callerPid | number          | Yes  | No  | PID of the caller.                             |
| callerUid    | number          | Yes  | No  | UID of the caller.                           |
| callerTokenId | number | Yes  | No  | Token ID of the caller.|
| remoteDeviceId   | string | Yes  | No  | Remote device ID. This parameter is valid only in RPC scenarios.  |
| localDeviceId   | string | Yes  | No  | Local device ID. This parameter is valid only in RPC scenarios.  |
| isLocalCalling   | boolean | Yes  | No  | Whether the peer end of the current communication is a process on the local device.  |

## IRemoteObject

Provides methods to query of obtain interface descriptors, add or delete death notifications, dump object status to specific files, and send messages.

### getLocalInterface<sup>9+</sup>

getLocalInterface(descriptor: string): IRemoteBroker

Obtains the string of the interface descriptor.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name    | Type  | Mandatory| Description                |
  | ---------- | ------ | ---- | -------------------- |
  | descriptor | string | Yes  | Interface descriptor.|

**Return value**

| Type         | Description                                         |
| ------------- | --------------------------------------------- |
| [IRemoteBroker](#iremotebroker) | **IRemoteBroker** object bound to the specified interface token.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match; <br> 3.The string length is greater than or equal to 40960 bytes; <br> 4.The number of bytes copied to the buffer is different from the length of the obtained string. |

### queryLocalInterface<sup>(deprecated)</sup>

queryLocalInterface(descriptor: string): IRemoteBroker

Obtains the string of the interface descriptor.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [getLocalInterface](#getlocalinterface9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name    | Type  | Mandatory| Description                |
  | ---------- | ------ | ---- | -------------------- |
  | descriptor | string | Yes  | Interface descriptor.|

**Return value**

| Type         | Description                                         |
| ------------- | --------------------------------------------- |
| [IRemoteBroker](#iremotebroker) | **IRemoteBroker** object bound to the specified interface token.|

### sendRequest<sup>(deprecated)</sup>

sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean

Sends a **MessageParcel** message to the remote process in synchronous or asynchronous mode. If asynchronous mode is set in **options**, a promise will be fulfilled immediately and the reply message does not contain any content. If synchronous mode is set in **options**, a promise will be fulfilled when the response to **sendRequest** is returned, and the reply message contains the returned information.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [sendMessageRequest](#sendmessagerequest9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name | Type                                     | Mandatory| Description                                                                                  |
  | ------- | ----------------------------------------- | ---- | -------------------------------------------------------------------------------------- |
  | code    | number                                    | Yes  | Message code (1-16777215) called by the request, which is determined by the communication parties. If the method is generated by an IDL tool, the message code is automatically generated by the IDL tool.|
  | data    | [MessageParcel](#messageparceldeprecated) | Yes  | **MessageParcel** object holding the data to send.                                             |
  | reply   | [MessageParcel](#messageparceldeprecated) | Yes  | **MessageParcel** object that receives the response.                                                     |
  | options | [MessageOption](#messageoption)           | Yes  | Request sending mode, which can be synchronous (default) or asynchronous.                                                  |

**Return value**

  | Type   | Description                            |
  | ------- | -------------------------------- |
  | boolean | Returns **true** if the message is sent successfully; returns **false** otherwise.|

### sendMessageRequest<sup>9+</sup>

sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption): Promise&lt;RequestResult&gt;

Sends a **MessageSequence** message to the remote process in synchronous or asynchronous mode. If asynchronous mode is set in **options**, a promise will be fulfilled immediately and the reply message is empty. The specific reply needs to be obtained from the callback on the service side. If synchronous mode is set in **options**, a promise will be fulfilled when the response to **sendMessageRequest** is returned, and the reply message contains the returned information.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name | Type                                | Mandatory| Description                                                                                  |
  | ------- | ------------------------------------ | ---- | -------------------------------------------------------------------------------------- |
  | code    | number                               | Yes  | Message code (1-16777215) called by the request, which is determined by the communication parties. If the method is generated by an IDL tool, the message code is automatically generated by the IDL tool.|
  | data    | [MessageSequence](#messagesequence9) | Yes  | **MessageSequence** object holding the data to send.                                           |
  | reply   | [MessageSequence](#messagesequence9) | Yes  | **MessageSequence** object that receives the response.                                                   |
  | options | [MessageOption](#messageoption)      | Yes  | Request sending mode, which can be synchronous (default) or asynchronous.                                                  |

**Return value**

  | Type                        | Description                                     |
  | ---------------------------- | ----------------------------------------- |
  | Promise&lt;[RequestResult](#requestresult9)&gt; | Promise used to return a **requestResult** instance.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match; <br> 3.Failed to obtain the passed object instance. |

### sendRequest<sup>(deprecated)</sup>

sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): Promise&lt;SendRequestResult&gt;

Sends a **MessageParcel** message to the remote process in synchronous or asynchronous mode. If asynchronous mode is set in **options**, a promise will be fulfilled immediately and the reply message is empty. The specific reply needs to be obtained from the callback on the service side. If synchronous mode is set in **options**, a promise will be fulfilled when the response to **sendRequest** is returned, and the reply message contains the returned information.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [sendMessageRequest](#sendmessagerequest9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name | Type                                     | Mandatory| Description                                                                                  |
  | ------- | ----------------------------------------  | ---- | -------------------------------------------------------------------------------------- |
  | code    | number                                    | Yes  | Message code (1-16777215) called by the request, which is determined by the communication parties. If the method is generated by an IDL tool, the message code is automatically generated by the IDL tool.|
  | data    | [MessageParcel](#messageparceldeprecated) | Yes  | **MessageParcel** object holding the data to send.                                             |
  | reply   | [MessageParcel](#messageparceldeprecated) | Yes  | **MessageParcel** object that receives the response.                                                     |
  | options | [MessageOption](#messageoption)           | Yes  | Request sending mode, which can be synchronous (default) or asynchronous.                                                  |

**Return value**

| Type                                                        | Description                                         |
| ------------------------------------------------------------ | --------------------------------------------- |
| Promise&lt;[SendRequestResult](#sendrequestresultdeprecated)&gt; | Promise used to return a **sendRequestResult** instance.|

### sendMessageRequest<sup>9+</sup>

sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption, callback: AsyncCallback&lt;RequestResult&gt;): void

Sends a **MessageSequence** message to the remote process in synchronous or asynchronous mode. If asynchronous mode is set in **options**, a callback will be called immediately, and the reply message is empty. The specific reply needs to be obtained from the callback on the service side. If synchronous mode is set in **options**, a callback will be invoked when the response to **sendRequest** is returned, and the reply message contains the returned information.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name  | Type                                | Mandatory| Description                                                                                  |
  | -------- | ------------------------------------ | ---- | -------------------------------------------------------------------------------------- |
  | code     | number                               | Yes  | Message code (1-16777215) called by the request, which is determined by the communication parties. If the method is generated by an IDL tool, the message code is automatically generated by the IDL tool.|
  | data     | [MessageSequence](#messagesequence9) | Yes  | **MessageSequence** object holding the data to send.                                           |
  | reply    | [MessageSequence](#messagesequence9) | Yes  | **MessageSequence** object that receives the response.                                                   |
  | options  | [MessageOption](#messageoption)      | Yes  | Request sending mode, which can be synchronous (default) or asynchronous.                                                  |
  | callback | AsyncCallback&lt;[RequestResult](#requestresult9)&gt;   | Yes  | Callback for receiving the sending result.                                                                  |

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match; <br> 3.Failed to obtain the passed object instance. |

### sendRequest<sup>(deprecated)</sup>

sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption, callback: AsyncCallback&lt;SendRequestResult&gt;): void

Sends a **MessageParcel** message to the remote process in synchronous or asynchronous mode. If asynchronous mode is set in **options**, a callback will be called immediately, and the reply message is empty. The specific reply needs to be obtained from the callback on the service side. If synchronous mode is set in **options**, a callback will be invoked when the response to **sendRequest** is returned, and the reply message contains the returned information.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [sendMessageRequest](#sendmessagerequest9-1) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| code     | number                                                       | Yes  | Message code (1-16777215) called by the request, which is determined by the communication parties. If the method is generated by an IDL tool, the message code is automatically generated by the IDL tool.|
| data     | [MessageParcel](#messageparceldeprecated)                    | Yes  | **MessageParcel** object holding the data to send.                   |
| reply    | [MessageParcel](#messageparceldeprecated)                    | Yes  | **MessageParcel** object that receives the response.                           |
| options  | [MessageOption](#messageoption)                              | Yes  | Request sending mode, which can be synchronous (default) or asynchronous.                        |
| callback | AsyncCallback&lt;[SendRequestResult](#sendrequestresultdeprecated)&gt; | Yes  | Callback for receiving the sending result.                                        |

### registerDeathRecipient<sup>9+</sup>

registerDeathRecipient(recipient: DeathRecipient, flags: number): void

Registers a callback for receiving death notifications of the remote object. This method is called if the remote object process matching the **RemoteProxy** object is killed.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name   | Type                             | Mandatory| Description          |
  | --------- | --------------------------------- | ---- | -------------- |
  | recipient | [DeathRecipient](#deathrecipient) | Yes  | Callback to register.|
  | flags     | number                            | Yes  | Flag of the death notification.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match; <br> 3.The callback used to receive remote object death notifications is empty. |
  | 1900005  | Operation allowed only for the proxy object. |
  | 1900008  | The proxy or remote object is invalid. |

### addDeathRecipient<sup>(deprecated)</sup>

addDeathRecipient(recipient: DeathRecipient, flags: number): boolean

Adds a callback for receiving death notifications of the remote object. This method is called if the remote object process matching the **RemoteProxy** object is killed.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [registerDeathRecipient](#registerdeathrecipient9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name   | Type                             | Mandatory| Description          |
  | --------- | --------------------------------- | ---- | -------------- |
  | recipient | [DeathRecipient](#deathrecipient) | Yes  | Callback to register.|
  | flags     | number                            | Yes  | Flag of the death notification.|

**Return value**

  | Type   | Description                                    |
  | ------- | ---------------------------------------- |
  | boolean | Returns **true** if the callback is added successfully; returns **false** otherwise.|

### unregisterDeathRecipient<sup>9+</sup>

unregisterDeathRecipient(recipient: DeathRecipient, flags: number): void

Unregisters from the callback used to receive death notifications of the remote object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name   | Type                             | Mandatory| Description          |
  | --------- | --------------------------------- | ---- | -------------- |
  | recipient | [DeathRecipient](#deathrecipient) | Yes  | Callback to unregister.|
  | flags     | number                            | Yes  | Flag of the death notification.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match; <br> 3.The callback used to receive remote object death notifications is empty. |
  | 1900005  | Operation allowed only for the proxy object. |
  | 1900008  | The proxy or remote object is invalid. |

### removeDeathRecipient<sup>(deprecated)</sup>

removeDeathRecipient(recipient: DeathRecipient, flags: number): boolean

Removes the callback used to receive death notifications of the remote object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [unregisterDeathRecipient](#unregisterdeathrecipient9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name   | Type                             | Mandatory| Description          |
  | --------- | --------------------------------- | ---- | -------------- |
  | recipient | [DeathRecipient](#deathrecipient) | Yes  | Callback to unregister.|
  | flags     | number                            | Yes  | Flag of the death notification.|

**Return value**

  | Type   | Description                                    |
  | ------- | -----------------------------------------|
  | boolean | Returns **true** if the callback is removed; returns **false** otherwise.|

### getDescriptor<sup>9+</sup>

getDescriptor(): string

Obtains the interface descriptor (which is a string) of this object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description            |
  | ------ | ---------------- |
  | string | Interface descriptor obtained.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 1900008  | The proxy or remote object is invalid. |

### getInterfaceDescriptor<sup>(deprecated)</sup>

getInterfaceDescriptor(): string

Obtains the interface descriptor (which is a string) of this object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [getDescriptor](#getdescriptor9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description            |
  | ------ | ---------------- |
  | string | Interface descriptor obtained.|

### isObjectDead

isObjectDead(): boolean

Checks whether this object is dead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type   | Description                              |
  | ------- | ---------------------------------- |
  | boolean | Returns **true** if the object is dead; returns **false** otherwise.|

## RemoteProxy

Provides APIs to implement **IRemoteObject**.

### Properties

**System capability**: SystemCapability.Communication.IPC.Core

  | Name                 | Type  | Read-Only | Optional| Description                                    |
  | --------------------- | -------| ------|------|------------------------------------------ |
  | PING_TRANSACTION      | number | Yes   | No  | Internal instruction code used to test whether the IPC service is normal.    |
  | DUMP_TRANSACTION      | number | Yes   | No  | Internal instruction code used to obtain IPC service status information.  |
  | INTERFACE_TRANSACTION | number | Yes   | No  | Internal instruction code used to obtain the remote interface token.         |
  | MIN_TRANSACTION_ID    | number | Yes   | No  | Minimum valid instruction code.                         |
  | MAX_TRANSACTION_ID    | number | Yes   | No  | Maximum valid instruction code.                         |

### sendRequest<sup>(deprecated)</sup>

sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean

Sends a **MessageParcel** message to the remote process in synchronous or asynchronous mode. If asynchronous mode is set in **options**, a promise will be fulfilled immediately and the reply message is empty. The specific reply needs to be obtained from the callback on the service side. If synchronous mode is set in **options**, a promise will be fulfilled when the response to **sendRequest** is returned, and the reply message contains the returned information.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 8. Use [sendMessageRequest](#sendmessagerequest9-2) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name | Type                                     | Mandatory| Description                                                                                  |
  | ------- | ----------------------------------------- | ---- | -------------------------------------------------------------------------------------- |
  | code    | number                                    | Yes  | Message code (1-16777215) called by the request, which is determined by the communication parties. If the method is generated by an IDL tool, the message code is automatically generated by the IDL tool.|
  | data    | [MessageParcel](#messageparceldeprecated) | Yes  | **MessageParcel** object holding the data to send.                                             |
  | reply   | [MessageParcel](#messageparceldeprecated) | Yes  | **MessageParcel** object that receives the response.                                                     |
  | options | [MessageOption](#messageoption)           | Yes  | Request sending mode, which can be synchronous (default) or asynchronous.                                                  |

**Return value**

  | Type   | Description                            |
  | ------- | ---------------------------------|
  | boolean | Returns **true** if the message is sent successfully; returns **false** otherwise.|

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.getUIContext().getHostContext()** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

<!--code_no_check-->
```ts
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

  The proxy object in the **onConnect** callback can be assigned a value only after the ability is connected asynchronously. Then, **sendRequest()** of the proxy object is called to send a message.

<!--deprecated_code_no_check-->
```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let option = new rpc.MessageOption();
  let data = rpc.MessageParcel.create();
  let reply = rpc.MessageParcel.create();
  data.writeInt(1);
  data.writeString("hello");
  if (proxy != undefined) {
    let ret: boolean = proxy.sendRequest(1, data, reply, option);
    if (ret) {
      hilog.info(0x0000, 'testTag', 'sendRequest got result');
      let msg = reply.readString();
      hilog.info(0x0000, 'testTag', 'reply msg: ' + msg);
    } else {
      hilog.error(0x0000, 'testTag', 'sendRequest failed');
    }
    hilog.info(0x0000, 'testTag', 'sendRequest ends, reclaim parcel');
    data.reclaim();
    reply.reclaim();
  }
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error: ' + error);
}
```

### sendMessageRequest<sup>9+</sup>

sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption): Promise&lt;RequestResult&gt;

Sends a **MessageSequence** message to the remote process in synchronous or asynchronous mode. If asynchronous mode is set in **options**, a promise will be fulfilled immediately and the reply message is empty. The specific reply needs to be obtained from the callback on the service side. If synchronous mode is set in **options**, a promise will be fulfilled when the response to **sendMessageRequest** is returned, and the reply message contains the returned information.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name | Type                                | Mandatory| Description                                                                                  |
  | ------- | ------------------------------------ | ---- | -------------------------------------------------------------------------------------- |
  | code    | number                               | Yes  | Message code (1-16777215) called by the request, which is determined by the communication parties. If the method is generated by an IDL tool, the message code is automatically generated by the IDL tool.|
  | data    | [MessageSequence](#messagesequence9) | Yes  | **MessageSequence** object holding the data to send.                                           |
  | reply   | [MessageSequence](#messagesequence9) | Yes  | **MessageSequence** object that receives the response.                                                   |
  | options | [MessageOption](#messageoption)      | Yes  | Request sending mode, which can be synchronous (default) or asynchronous.                                                  |

**Return value**

  | Type                        | Description                                     |
  | ---------------------------- | ----------------------------------------- |
  | Promise&lt;[RequestResult](#requestresult9)&gt; | Promise used to return a **requestResult** instance.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match; <br> 3.Failed to obtain the passed object instance. |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.getUIContext().getHostContext()** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

<!--code_no_check-->
```ts
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

The proxy object in the **onConnect** callback can be assigned a value only after the ability is connected asynchronously. Then, **sendMessageRequest()** of the proxy object is called to send a message.

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let option = new rpc.MessageOption();
  let data = rpc.MessageSequence.create();
  let reply = rpc.MessageSequence.create();
  data.writeInt(1);
  data.writeString("hello");
  if (proxy != undefined) {
    proxy.sendMessageRequest(1, data, reply, option)
    .then((result: rpc.RequestResult) => {
      if (result.errCode === 0) {
        hilog.info(0x0000, 'testTag', 'sendMessageRequest got result');
        let num = result.reply.readInt();
        let msg = result.reply.readString();
        hilog.info(0x0000, 'testTag', 'reply num: ' + num);
        hilog.info(0x0000, 'testTag', 'reply msg: ' + msg);
      } else {
        hilog.error(0x0000, 'testTag', 'sendMessageRequest failed, errCode: ' + result.errCode);
      }
    }).catch((e: Error) => {
      hilog.error(0x0000, 'testTag', 'sendMessageRequest failed, error: ' + e);
    }).finally (() => {
      hilog.info(0x0000, 'testTag', 'sendMessageRequest ends, reclaim parcel');
      data.reclaim();
      reply.reclaim();
    });
  }
} catch (error) {
  hilog.error(0x0000, 'testTag', 'sendMessageRequest failed, error: ' + error);
}
```

### sendRequest<sup>(deprecated)</sup>

sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): Promise&lt;SendRequestResult&gt;

Sends a **MessageParcel** message to the remote process in synchronous or asynchronous mode. If asynchronous mode is set in **options**, a promise will be fulfilled immediately and the reply message is empty. The specific reply needs to be obtained from the callback on the service side. If synchronous mode is set in **options**, a promise will be fulfilled when the response to **sendRequest** is returned, and the reply message contains the returned information.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [sendMessageRequest](#sendmessagerequest9-2) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name | Type                                     | Mandatory| Description                                                                                  |
  | ------- | ----------------------------------------- | ---- | -------------------------------------------------------------------------------------- |
  | code    | number                                    | Yes  | Message code (1-16777215) called by the request, which is determined by the communication parties. If the method is generated by an IDL tool, the message code is automatically generated by the IDL tool.|
  | data    | [MessageParcel](#messageparceldeprecated) | Yes  | **MessageParcel** object holding the data to send.                                             |
  | reply   | [MessageParcel](#messageparceldeprecated) | Yes  | **MessageParcel** object that receives the response.                                                     |
  | options | [MessageOption](#messageoption)           | Yes  | Request sending mode, which can be synchronous (default) or asynchronous.                                                  |

**Return value**

| Type                                                        | Description                                         |
| ------------------------------------------------------------ | --------------------------------------------- |
| Promise&lt;[SendRequestResult](#sendrequestresultdeprecated)&gt; | Promise used to return a **sendRequestResult** instance.|

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.getUIContext().getHostContext()** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

<!--code_no_check-->
```ts
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

  The proxy object in the **onConnect** callback can be assigned a value only after the ability is connected asynchronously. Then, **sendRequest()** of the proxy object is called to send a message.

<!--deprecated_code_no_check-->
```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let option = new rpc.MessageOption();
  let data = rpc.MessageParcel.create();
  let reply = rpc.MessageParcel.create();
  data.writeInt(1);
  data.writeString("hello");
  if (proxy != undefined) {
    let a = proxy.sendRequest(1, data, reply, option) as Object;
    let b = a as Promise<rpc.SendRequestResult>;
    b.then((result: rpc.SendRequestResult) => {
      if (result.errCode === 0) {
        hilog.info(0x0000, 'testTag', 'sendRequest got result');
        let num = result.reply.readInt();
        let msg = result.reply.readString();
        hilog.info(0x0000, 'testTag', 'reply num: ' + num);
        hilog.info(0x0000, 'testTag', 'reply msg: ' + msg);
      } else {
        hilog.error(0x0000, 'testTag', 'sendRequest failed, errCode: ' + result.errCode);
      }
    }).catch((e: Error) => {
      hilog.error(0x0000, 'testTag', 'sendRequest failed, error: ' + e);
    }).finally (() => {
      hilog.info(0x0000, 'testTag', 'sendRequest ends, reclaim parcel');
      data.reclaim();
      reply.reclaim();
    });
  }
} catch (error) {
  hilog.error(0x0000, 'testTag', 'sendRequest failed, error: ' + error);
}
```

### sendMessageRequest<sup>9+</sup>

sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption, callback: AsyncCallback&lt;RequestResult&gt;): void

Sends a **MessageSequence** message to the remote process in synchronous or asynchronous mode. If asynchronous mode is set in **options**, a callback will be called immediately, and the reply message is empty. The specific reply needs to be obtained from the callback on the service side. If synchronous mode is set in **options**, a callback will be invoked at certain time after the response to **RequestResult** is returned, and the reply contains the returned information.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name  | Type                                | Mandatory| Description                                                                                  |
  | -------- | ------------------------------------ | ---- | -------------------------------------------------------------------------------------- |
  | code     | number                               | Yes  | Message code (1-16777215) called by the request, which is determined by the communication parties. If the method is generated by an IDL tool, the message code is automatically generated by the IDL tool.|
  | data     | [MessageSequence](#messagesequence9) | Yes  | **MessageSequence** object holding the data to send.                                           |
  | reply    | [MessageSequence](#messagesequence9) | Yes  | **MessageSequence** object that receives the response.                                                   |
  | options  | [MessageOption](#messageoption)      | Yes  | Request sending mode, which can be synchronous (default) or asynchronous.                                                  |
  | callback | AsyncCallback&lt;[RequestResult](#requestresult9)&gt;   | Yes  | Callback for receiving the sending result.                                                                  |

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match; <br> 3.Failed to obtain the passed object instance. |

### sendRequest<sup>(deprecated)</sup>

sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption, callback: AsyncCallback&lt;SendRequestResult&gt;): void

Sends a **MessageParcel** message to the remote process in synchronous or asynchronous mode. If asynchronous mode is set in **options**, a callback will be called immediately, and the reply message is empty. The specific reply needs to be obtained from the callback on the service side. If synchronous mode is set in **options**, a callback will be invoked when the response to **sendRequest** is returned, and the reply message contains the returned information.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [sendMessageRequest](#sendmessagerequest9-3) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| code     | number                                                       | Yes  | Message code (1-16777215) called by the request, which is determined by the communication parties. If the method is generated by an IDL tool, the message code is automatically generated by the IDL tool.|
| data     | [MessageParcel](#messageparceldeprecated)                    | Yes  | **MessageParcel** object holding the data to send.                   |
| reply    | [MessageParcel](#messageparceldeprecated)                    | Yes  | **MessageParcel** object that receives the response.                           |
| options  | [MessageOption](#messageoption)                              | Yes  | Request sending mode, which can be synchronous (default) or asynchronous.                        |
| callback | AsyncCallback&lt;[SendRequestResult](#sendrequestresultdeprecated)&gt; | Yes  | Callback for receiving the sending result.                                        |

### getLocalInterface<sup>9+</sup>

getLocalInterface(interface: string): IRemoteBroker

Obtains the **LocalInterface** object of an interface token.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name   | Type  | Mandatory| Description                  |
  | --------- | ------ | ---- | ---------------------- |
  | interface | string | Yes  | Interface descriptor.|

**Return value**

| Type                           | Description                                      |
| ------------------------------- | ------------------------------------------ |
| [IRemoteBroker](#iremotebroker) | Returns **Null** by default, which indicates a proxy interface.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | check param failed |
  | 1900006  | Operation allowed only for the remote object. |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.getUIContext().getHostContext()** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

<!--code_no_check-->
```ts
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

  The proxy object in the **onConnect** callback can be assigned a value only after the ability is connected asynchronously. Then, **getLocalInterface()** of the proxy object is called to obtain the interface descriptor.

<!--deprecated_code_no_check-->
```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

if (proxy != undefined) {
  try {
    let broker: rpc.IRemoteBroker = proxy.getLocalInterface("testObject");
    hilog.info(0x0000, 'testTag', 'getLocalInterface is ' + broker);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    hilog.error(0x0000, 'testTag', 'rpc get local interface fail, errorCode ' + e.code);
    hilog.error(0x0000, 'testTag', 'rpc get local interface fail, errorMessage ' + e.message);
  }
}
```

### queryLocalInterface<sup>(deprecated)</sup>

queryLocalInterface(interface: string): IRemoteBroker

Obtains the **LocalInterface** object of an interface token.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [getLocalInterface](#getlocalinterface9-1) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name   | Type  | Mandatory| Description                  |
  | --------- | ------ | ---- | ---------------------- |
  | interface | string | Yes  | Interface descriptor.|

**Return value**

| Type                           | Description                                      |
| ------------------------------- | ------------------------------------------ |
| [IRemoteBroker](#iremotebroker) | Returns **Null** by default, which indicates a proxy interface.|

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.getUIContext().getHostContext()** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

<!--code_no_check-->
```ts
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

  The proxy object in the **onConnect** callback can be assigned a value only after the ability is connected asynchronously. Then, **queryLocalInterface()** of the proxy object is called to obtain the interface descriptor.

<!--deprecated_code_no_check-->
```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

if (proxy != undefined) {
  let broker: rpc.IRemoteBroker = proxy.queryLocalInterface("testObject");
  hilog.info(0x0000, 'testTag', 'queryLocalInterface is ' + broker);
}
```

### registerDeathRecipient<sup>9+</sup>

registerDeathRecipient(recipient: DeathRecipient, flags: number): void

Registers a callback for receiving death notifications of the remote object. This method is called if the remote object process matching the **RemoteProxy** object is killed.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name   | Type                             | Mandatory| Description          |
  | --------- | --------------------------------- | ---- | -------------- |
  | recipient | [DeathRecipient](#deathrecipient) | Yes  | Callback to register.|
  | flags     | number                            | Yes  | Flag of the death notification.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match; <br> 3.The callback used to receive remote object death notifications is empty. |
  | 1900008  | The proxy or remote object is invalid. |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.getUIContext().getHostContext()** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

<!--code_no_check-->
```ts
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

The proxy object in the **onConnect** callback can be assigned a value only after the ability is connected asynchronously. Then, **registerDeathRecipient()** of the proxy object is called to register a callback for receiving the death notification of the remote object.

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

class MyDeathRecipient implements rpc.DeathRecipient {
  onRemoteDied() {
    hilog.info(0x0000, 'testTag', 'server died');
  }
}
if (proxy != undefined) {
  try {
    let deathRecipient = new MyDeathRecipient();
    proxy.registerDeathRecipient(deathRecipient, 0);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    hilog.error(0x0000, 'testTag', 'proxy register deathRecipient fail, errorCode ' + e.code);
    hilog.error(0x0000, 'testTag', 'proxy register deathRecipient fail, errorMessage ' + e.message);
  }
}
```

### addDeathRecipient<sup>(deprecated)</sup>

addDeathRecipient(recipient: DeathRecipient, flags: number): boolean

Adds a callback for receiving the death notifications of the remote object, including the death notifications of the remote proxy.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [registerDeathRecipient](#registerdeathrecipient9-1) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name   | Type                             | Mandatory| Description                             |
  | --------- | --------------------------------- | ---- | --------------------------------- |
  | recipient | [DeathRecipient](#deathrecipient) | Yes  | Callback to add.         |
  | flags     | number                            | Yes  | Flag of the death notification. This parameter is reserved. It is set to **0**.|

**Return value**

  | Type   | Description                                    |
  | ------- | ---------------------------------------- |
  | boolean | Returns **true** if the callback is added successfully; returns **false** otherwise.|

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.getUIContext().getHostContext()** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

<!--code_no_check-->
```ts
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

  The proxy object in the **onConnect** callback can be assigned a value only after the ability is connected asynchronously. Then, **addDeathRecipient()** of the proxy object is called to add a callback for receiving the death notification of the remove object.

<!--deprecated_code_no_check-->
```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MyDeathRecipient implements rpc.DeathRecipient {
  onRemoteDied() {
    hilog.info(0x0000, 'testTag', 'server died');
  }
}
if (proxy != undefined) {
  let deathRecipient = new MyDeathRecipient();
  proxy.addDeathRecipient(deathRecipient, 0);
}
```

### unregisterDeathRecipient<sup>9+</sup>

unregisterDeathRecipient(recipient: DeathRecipient, flags: number): void

Unregisters from the callback used to receive death notifications of the remote object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name   | Type                             | Mandatory| Description          |
  | --------- | --------------------------------- | ---- | -------------- |
  | recipient | [DeathRecipient](#deathrecipient) | Yes  | Callback to unregister.|
  | flags     | number                            | Yes  | Flag of the death notification.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match; <br> 3.The callback used to receive remote object death notifications is empty. |
  | 1900008  | The proxy or remote object is invalid. |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.getUIContext().getHostContext()** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

<!--code_no_check-->
```ts
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

The proxy object in the **onConnect** callback can be assigned a value only after the ability is connected asynchronously. Then, **unregisterDeathRecipient()** of the proxy object is called to unregister the callback for receiving the death notification of the remote object.

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

class MyDeathRecipient implements rpc.DeathRecipient {
  onRemoteDied() {
    hilog.info(0x0000, 'testTag', 'server died');
  }
}
if (proxy != undefined) {
  try {
    let deathRecipient = new MyDeathRecipient();
    proxy.registerDeathRecipient(deathRecipient, 0);
    proxy.unregisterDeathRecipient(deathRecipient, 0);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    hilog.error(0x0000, 'testTag', 'proxy unregister deathRecipient fail, errorCode ' + e.code);
    hilog.error(0x0000, 'testTag', 'proxy unregister deathRecipient fail, errorMessage ' + e.message);
  }
}
```

### removeDeathRecipient<sup>(deprecated)</sup>

removeDeathRecipient(recipient: DeathRecipient, flags: number): boolean

Removes the callback used to receive death notifications of the remote object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [unregisterDeathRecipient](#unregisterdeathrecipient9-1) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name   | Type                             | Mandatory| Description                             |
  | --------- | --------------------------------- | ---- | --------------------------------- |
  | recipient | [DeathRecipient](#deathrecipient) | Yes  | Callback to remove.               |
  | flags     | number                            | Yes  | Flag of the death notification. This parameter is reserved. It is set to **0**.|

**Return value**

  | Type   | Description                                    |
  | ------- | ---------------------------------------- |
  | boolean | Returns **true** if the callback is removed; returns **false** otherwise.|

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.getUIContext().getHostContext()** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

<!--code_no_check-->
```ts
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

The proxy object in the **onConnect** callback can be assigned a value only after the ability is connected asynchronously. Then, **removeDeathRecipient()** of the proxy object is called to remove the callback used to receive the death notification of the remote object.

<!--deprecated_code_no_check-->
```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MyDeathRecipient implements rpc.DeathRecipient {
  onRemoteDied() {
    hilog.info(0x0000, 'testTag', 'server died');
  }
}
if (proxy != undefined) {
  let deathRecipient = new MyDeathRecipient();
  proxy.addDeathRecipient(deathRecipient, 0);
  proxy.removeDeathRecipient(deathRecipient, 0);
}
```

### getDescriptor<sup>9+</sup>

getDescriptor(): string

Obtains the interface descriptor (which is a string) of this object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description            |
  | ------ | ---------------- |
  | string | Interface descriptor obtained.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 1900007  | communication failed.              |
  | 1900008  | The proxy or remote object is invalid. |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.getUIContext().getHostContext()** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

<!--code_no_check-->
```ts
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

  The proxy object in the **onConnect** callback can be assigned a value only after the ability is connected asynchronously. Then, **getDescriptor()** of the proxy object is called to obtain the interface descriptor of the object.

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

if (proxy != undefined) {
  try {
    let descriptor: string = proxy.getDescriptor();
    hilog.info(0x0000, 'testTag', 'descriptor is ' + descriptor);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    hilog.error(0x0000, 'testTag', 'rpc get interface descriptor fail, errorCode ' + e.code);
    hilog.error(0x0000, 'testTag', 'rpc get interface descriptor fail, errorMessage ' + e.message);
  }
}
```

### getInterfaceDescriptor<sup>(deprecated)</sup>

getInterfaceDescriptor(): string

Obtains the interface descriptor of this proxy object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [getDescriptor](#getdescriptor9-1) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description              |
  | ------ | ------------------ |
  | string | Interface descriptor obtained.|

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.getUIContext().getHostContext()** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

<!--code_no_check-->
```ts
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

  The proxy object in the **onConnect** callback can be assigned a value only after the ability is connected asynchronously. Then, **getInterfaceDescriptor()** of the proxy object is called to obtain the interface descriptor of the current proxy object.

<!--deprecated_code_no_check-->
```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

if (proxy != undefined) {
  let descriptor: string = proxy.getInterfaceDescriptor();
  hilog.info(0x0000, 'testTag', 'descriptor is ' + descriptor);
}
```

### isObjectDead

isObjectDead(): boolean

Checks whether the **RemoteObject** is dead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type   | Description                                             |
  | ------- | ------------------------------------------------- |
  | boolean | Returns **true** if **RemoteObject** is dead; returns **false** otherwise.|

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.getUIContext().getHostContext()** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

<!--code_no_check-->
```ts
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

The proxy object in the **onConnect** callback can be assigned a value only after the ability is connected asynchronously. Then, **isObjectDead()** of the proxy object is called to check whether this object is dead.

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

if (proxy != undefined) {
  let isDead: boolean = proxy.isObjectDead();
  hilog.info(0x0000, 'testTag', 'isObjectDead is ' + isDead);
}
```

## MessageOption

Defines the options used to construct the **MessageOption** object.

### Properties

**System capability**: SystemCapability.Communication.IPC.Core

  | Name         | Type  | Read-Only | Optional | Description                                                                     |
  | ------------- | ------ | ----- | ----- | ------------------------------------------------------------------------ |
  | TF_SYNC       | number | Yes   | No   | Synchronous call.                                                           |
  | TF_ASYNC      | number | Yes   | No   | Asynchronous call.                                                           |
  | TF_ACCEPT_FDS | number | Yes   | No   | Indication to **sendMessageRequest<sup>9+</sup>** for passing the file descriptor.              |
  | TF_WAIT_TIME  | number | Yes   | No   | RPC wait time, in seconds. This parameter cannot be used in IPC. The default waiting time is 8 seconds. You are advised not to change the waiting time.|

### constructor<sup>9+</sup>

constructor(async?: boolean)

A constructor used to create a **MessageOption** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

| Name| Type   | Mandatory| Description                                                        |
| ------ | ------- | ---- | ------------------------------------------------------------ |
| async  | boolean | No  | Whether to execute the call asynchronously. The value **true** means to execute the call asynchronously; the value **false** means to execute the call synchronously. The default value is **synchronous**.|

**Example**

```ts
import { rpc } from '@kit.IPCKit';

class TestRemoteObject extends rpc.MessageOption {
  constructor(async: boolean) {
    super(async);
  }
}
```

### constructor

constructor(syncFlags?: number, waitTime?: number)

A constructor used to create a **MessageOption** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name   | Type  | Mandatory| Description                                         |
  | --------- | ------ | ---- | --------------------------------------------- |
  | syncFlags | number | No  | Call flag to set. The options are as follows: 0 (synchronous call) and 1 (asynchronous call). The default value is **synchronous**.       |
  | waitTime  | number | No  | Maximum wait time for an RPC call. The default value is **TF_WAIT_TIME**.|

**Example**

```ts
import { rpc } from '@kit.IPCKit';

class TestRemoteObject extends rpc.MessageOption {
  constructor(syncFlags?: number,waitTime?: number) {
    super(syncFlags,waitTime);
  }
}
```

### isAsync<sup>9+</sup>

isAsync(): boolean

Checks whether **SendMessageRequest** is called synchronously or asynchronously.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type   | Description                                    |
  | ------- | ---------------------------------------- |
  | boolean | Returns **true** if **SendMessageRequest** is called asynchronously; returns **false** if it is called synchronously.|

**Example**

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let option = new rpc.MessageOption();
  let result = option.isAsync();
} catch (error) {
  hilog.info(0x0000, 'testTag', 'error ' + error);
}
```

### setAsync<sup>9+</sup>

setAsync(isAsync: boolean): void

Sets whether **SendMessageRequest** is called synchronously or asynchronously.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

| Name| Type   | Mandatory| Description                                             |
| ------ | ------- | ---- | ------------------------------------------------- |
| isAsync | boolean | Yes  | Whether to execute the call asynchronously. The value **true** means to execute the call asynchronously; the value **false** means to execute the call synchronously.|

**Example**

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let option = new rpc.MessageOption();
  option.setAsync(true);
} catch (error) {
  hilog.info(0x0000, 'testTag', 'error ' + error);
}
```

### getFlags

getFlags(): number

Obtains the call flag, which can be synchronous or asynchronous.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description                                |
  | ------ | ------------------------------------ |
  | number | Call flag obtained. **0**: synchronous call flag; **1**: asynchronous call flag.|

**Example**

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let option = new rpc.MessageOption();
  hilog.info(0x0000, 'testTag', 'create object successfully');
  let flag = option.getFlags();
  hilog.info(0x0000, 'testTag', 'run getFlags success, flag is ' + flag);
  option.setFlags(rpc.MessageOption.TF_ASYNC);
  hilog.info(0x0000, 'testTag', 'run setFlags success');
  let flag2 = option.getFlags();
  hilog.info(0x0000, 'testTag', 'run getFlags success, flag2 is ' + flag2);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

### setFlags

setFlags(flags: number): void

Sets the call flag, which can be synchronous or asynchronous.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description                    |
  | ------ | ------ | ---- | ------------------------ |
  | flags  | number | Yes  | Call flag to set. **0**: synchronous call flag; **1**: asynchronous call flag.|

**Example**

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let option = new rpc.MessageOption();
  option.setFlags(rpc.MessageOption.TF_ASYNC);
  hilog.info(0x0000, 'testTag', 'run setFlags success');
  let flag = option.getFlags();
  hilog.info(0x0000, 'testTag', 'run getFlags success, flag is ' + flag);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

### getWaitTime

getWaitTime(): number

Obtains the maximum wait time for this RPC call.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description             |
  | ------ | ----------------- |
  | number | Maximum wait time obtained. The default value is **TF_WAIT_TIME**.|

**Example**

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let option = new rpc.MessageOption();
  let time = option.getWaitTime();
  hilog.info(0x0000, 'testTag', 'run getWaitTime success, time is ' + time);
  option.setWaitTime(16);
  let time2 = option.getWaitTime();
  hilog.info(0x0000, 'testTag', 'run getWaitTime success, time is ' + time2);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

### setWaitTime

setWaitTime(waitTime: number): void

Sets the maximum wait time for this RPC call.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name  | Type  | Mandatory| Description                 |
  | -------- | ------ | ---- | --------------------- |
  | waitTime | number | Yes  | Maximum wait time to set. The upper limit is 3000 seconds.|

**Example**

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let option = new rpc.MessageOption();
  option.setWaitTime(16);
  let time = option.getWaitTime();
  hilog.info(0x0000, 'testTag', 'run getWaitTime success, time is ' + time);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## IPCSkeleton

Obtains IPC context, including the UID and PID, local and remote device IDs, and whether the method is invoked on the same device.

### getContextObject

static getContextObject(): IRemoteObject

Obtains the system capability manager. This API is a static method.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type                           | Description                |
  | ------------------------------- | -------------------- |
  | [IRemoteObject](#iremoteobject) | System capability manager obtained.|

**Example**

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let samgr = rpc.IPCSkeleton.getContextObject();
  hilog.info(0x0000, 'testTag', 'RpcServer: getContextObject result: ' + samgr);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

### getCallingPid

static getCallingPid(): number

Obtains the PID of the caller. This API is a static method, which is invoked by the **RemoteObject** object in the **onRemoteRequest** method. If this method is not invoked in the IPC context (**onRemoteRequest**), the PID of the process will be returned.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description             |
  | ------ | ----------------- |
  | number | PID of the caller.|

**Example**

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class Stub extends rpc.RemoteObject {
  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean | Promise<boolean> {
    try {
      let callerPid = rpc.IPCSkeleton.getCallingPid();
      hilog.info(0x0000, 'testTag', 'RpcServer: getCallingPid result: ' + callerPid);
    } catch (error) {
      hilog.error(0x0000, 'testTag', 'error ' + error);
    }
    return true;
  }
}
```

### getCallingUid

static getCallingUid(): number

Obtains the UID of the caller. This API is a static method, which is invoked by the **RemoteObject** object in the **onRemoteRequest** method. If this method is not invoked in the IPC context (**onRemoteRequest**), the UID of the process will be returned.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description             |
  | ------ | ----------------- |
  | number | UID of the caller.|

**Example**

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class Stub extends rpc.RemoteObject {
  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean | Promise<boolean> {
    try {
      let callerUid = rpc.IPCSkeleton.getCallingUid();
      hilog.info(0x0000, 'testTag', 'RpcServer: getCallingUid result: ' + callerUid);
    } catch (error) {
      hilog.error(0x0000, 'testTag', 'error ' + error);
    }
    return true;
  }
}
```

### getCallingTokenId<sup>8+</sup>

static getCallingTokenId(): number

Obtains the caller's token ID, which is used to verify the caller identity.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

   | Type  | Description                 |
   | ------ | --------------------- |
   | number | Token ID of the caller obtained.|

**Example**

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class Stub extends rpc.RemoteObject {
  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean | Promise<boolean> {
    try {
      let callerTokenId = rpc.IPCSkeleton.getCallingTokenId();
      hilog.info(0x0000, 'testTag', 'RpcServer: getCallingTokenId result: ' + callerTokenId);
    } catch (error) {
      hilog.error(0x0000, 'testTag', 'error ' + error);
    }
    return true;
  }
}
```

### getCallingDeviceID

static getCallingDeviceID(): string

Obtains the ID of the device hosting the caller's process. This API is a static method.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description                        |
  | ------ | ---------------------------- |
  | string | Device ID obtained.|

**Example**

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class Stub extends rpc.RemoteObject {
  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean | Promise<boolean> {
    try {
      let callerDeviceID = rpc.IPCSkeleton.getCallingDeviceID();
      hilog.info(0x0000, 'testTag', 'RpcServer: callerDeviceID is ' + callerDeviceID);
    } catch (error) {
      hilog.error(0x0000, 'testTag', 'error ' + error);
    }
    return true;
  }
}
```

### getLocalDeviceID

static getLocalDeviceID(): string

Obtains the local device ID. This API is a static method.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description              |
  | ------ | ------------------ |
  | string | Local device ID obtained.|

**Example**

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class Stub extends rpc.RemoteObject {
  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean | Promise<boolean> {
    try {
      let localDeviceID = rpc.IPCSkeleton.getLocalDeviceID();
      hilog.info(0x0000, 'testTag', 'RpcServer: localDeviceID is ' + localDeviceID);
    } catch (error) {
      hilog.error(0x0000, 'testTag', 'error ' + error);
    }
    return true;
  }
}
```

### isLocalCalling

static isLocalCalling(): boolean

Checks whether the peer process is a process of the local device. This API is a static method.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type   | Description                                              |
  | ------- | -------------------------------------------------- |
  | boolean | Returns **true** if the local and peer processes are on the same device; returns **false** otherwise.|

**Example**

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class Stub extends rpc.RemoteObject {
  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean | Promise<boolean> {
    try {
      let isLocalCalling = rpc.IPCSkeleton.isLocalCalling();
      hilog.info(0x0000, 'testTag', 'RpcServer: isLocalCalling is ' + isLocalCalling);
    } catch (error) {
      hilog.error(0x0000, 'testTag', 'error ' + error);
    }
    return true;
  }
}
```

### flushCmdBuffer<sup>9+</sup>

static flushCmdBuffer(object: IRemoteObject): void

Flushes all suspended commands from the specified **RemoteProxy** to the corresponding **RemoteObject**. This API is a static method. You are advised to call this API before performing any sensitive operation.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type                           | Mandatory| Description               |
  | ------ | ------------------------------- | ---- | ------------------- |
  | object | [IRemoteObject](#iremoteobject) | Yes  | **RemoteProxy** specified. |

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match. |

**Example**

```ts
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
  let remoteObject = new TestRemoteObject("aaa");
  rpc.IPCSkeleton.flushCmdBuffer(remoteObject);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'proxy flushCmdBuffer fail, errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'proxy flushCmdBuffer fail, errorMessage ' + e.message);
}
```

### flushCommands<sup>(deprecated)</sup>

static flushCommands(object: IRemoteObject): number

Flushes all suspended commands from the specified **RemoteProxy** to the corresponding **RemoteObject**. This API is a static method. You are advised to call this API before performing any sensitive operation.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [flushCmdBuffer](#flushcmdbuffer9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type                           | Mandatory| Description               |
  | ------ | ------------------------------- | ---- | ------------------- |
  | object | [IRemoteObject](#iremoteobject) | Yes  | **RemoteProxy** specified. |

**Return value**

  | Type  | Description                                                                             |
  | ------ | --------------------------------------------------------------------------------- |
  | number | Returns **0** if the operation is successful; returns an error code if the input object is null or a **RemoteObject**, or if the operation fails.|

**Example**

<!--deprecated_code_no_check-->
```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

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
  let remoteObject = new TestRemoteObject("aaa");
  let ret = rpc.IPCSkeleton.flushCommands(remoteObject);
  hilog.info(0x0000, 'testTag', 'RpcServer: flushCommands result: ' + ret);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'proxy flushCmdBuffer fail, errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'proxy flushCmdBuffer fail, errorMessage ' + e.message);
}
```

### resetCallingIdentity

static resetCallingIdentity(): string

Resets the UID and PID of the remote user to those of the local user. This API is a static method and is used in scenarios such as identity authentication.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description                                |
  | ------ | ------------------------------------ |
  | string | String containing the UID and PID of the remote user.|

**Example**

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class Stub extends rpc.RemoteObject {
  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean | Promise<boolean> {
    try {
      let callingIdentity = rpc.IPCSkeleton.resetCallingIdentity();
      hilog.info(0x0000, 'testTag', 'RpcServer: callingIdentity is ' + callingIdentity);
    } catch (error) {
      hilog.error(0x0000, 'testTag', 'error ' + error);
    }
    return true;
  }
}
```

### restoreCallingIdentity<sup>9+</sup>

static restoreCallingIdentity(identity: string): void

Restores the UID and PID of the remote user. This API is a static method. It is usually called after **resetCallingIdentity**, and the UID and PID of the remote user returned by **resetCallingIdentity** are required.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name  | Type  | Mandatory| Description                                                              |
  | -------- | ------ | ---- | ------------------------------------------------------------------ |
  | identity | string | Yes  | A string containing the UID and PID of the remote user. The length of the string must be less than 40960 bytes. are returned by **resetCallingIdentity**.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match; <br> 3.The string length is greater than or equal to 40960 bytes; <br> 4.The number of bytes copied to the buffer is different from the length of the obtained string. |

**Example**

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class Stub extends rpc.RemoteObject {
  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean | Promise<boolean> {
    try {
      let callingIdentity = rpc.IPCSkeleton.resetCallingIdentity();
      hilog.info(0x0000, 'testTag', 'RpcServer: callingIdentity is ' + callingIdentity);
      rpc.IPCSkeleton.restoreCallingIdentity(callingIdentity);
    } catch (error) {
      hilog.error(0x0000, 'testTag', 'error ' + error);
    }
    return true;
  }
}
```

### setCallingIdentity<sup>(deprecated)</sup>

static setCallingIdentity(identity: string): boolean

Sets the UID and PID of the remote user. This API is a static method. It is usually called after **resetCallingIdentity**, and the UID and PID of the remote user returned by **resetCallingIdentity** are required.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [restoreCallingIdentity](#restorecallingidentity9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name  | Type  | Mandatory| Description                                                              |
  | -------- | ------ | ---- | ------------------------------------------------------------------ |
  | identity | string | Yes  | String containing the remote user's UID and PID, which are returned by **resetCallingIdentity**.|

**Return value**

  | Type   | Description                            |
  | ------- | ---------------------------------|
  | boolean | Returns **true** if the operation is successful; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class Stub extends rpc.RemoteObject {
  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean | Promise<boolean> {
    try {
      let callingIdentity = rpc.IPCSkeleton.resetCallingIdentity();
      hilog.info(0x0000, 'testTag', 'RpcServer: callingIdentity is ' + callingIdentity);
      let ret = rpc.IPCSkeleton.setCallingIdentity(callingIdentity);
      hilog.info(0x0000, 'testTag', 'RpcServer: setCallingIdentity is ' + ret);
    } catch (error) {
      hilog.error(0x0000, 'testTag', 'error ' + error);
    }
    return true;
  }
}
```

## RemoteObject

Provides methods to implement **RemoteObject**. The service provider must inherit from this class.

### constructor

constructor(descriptor: string)

A constructor used to create a **RemoteObject** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name    | Type  | Mandatory| Description        |
  | ---------- | ------ | ---- | ------------ |
  | descriptor | string | Yes  | Interface descriptor. The length of the string must be less than 40960 bytes.|

**Example**

```ts
import { rpc } from '@kit.IPCKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
}
```

### sendRequest<sup>(deprecated)</sup>

sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean

Sends a **MessageParcel** message to the remote process in synchronous or asynchronous mode. If asynchronous mode is set in **options**, a promise will be fulfilled immediately and the reply message is empty. The specific reply needs to be obtained from the callback on the service side. If synchronous mode is set in **options**, a promise will be fulfilled when the response to **sendRequest** is returned, and the reply message contains the returned information.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 8. Use [sendMessageRequest](#sendmessagerequest9-4) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name | Type                                     | Mandatory| Description                                                                                  |
  | ------- | ----------------------------------------- | ---- | -------------------------------------------------------------------------------------- |
  | code    | number                                    | Yes  | Message code (1-16777215) called by the request, which is determined by the communication parties. If the method is generated by an IDL tool, the message code is automatically generated by the IDL tool.|
  | data    | [MessageParcel](#messageparceldeprecated) | Yes  | **MessageParcel** object holding the data to send.                                             |
  | reply   | [MessageParcel](#messageparceldeprecated) | Yes  | **MessageParcel** object that receives the response.                                                     |
  | options | [MessageOption](#messageoption)           | Yes  | Request sending mode, which can be synchronous (default) or asynchronous.                                                  |

**Return value**

  | Type   | Description                            |
  | ------- | -------------------------------- |
  | boolean | Returns **true** if the message is sent successfully; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class testRemoteObject extends rpc.RemoteObject {
  onRemoteRequest(code: number, data: rpc.MessageParcel, reply: rpc.MessageParcel,
    option: rpc.MessageOption): boolean {
    // Process services based on the actual service logic.
    return true;
  }
}
try {
  let testRemoteObject = new TestRemoteObject("testObject");
  let option = new rpc.MessageOption();
  let data = rpc.MessageParcel.create();
  let reply = rpc.MessageParcel.create();
  data.writeInt(1);
  data.writeString("hello");
  let ret: boolean = testRemoteObject.sendRequest(1, data, reply, option);
  if (ret) {
    hilog.info(0x0000, 'testTag', 'sendRequest got result');
    let msg = reply.readString();
    hilog.info(0x0000, 'testTag', 'reply msg: ' + msg);
  } else {
    hilog.error(0x0000, 'testTag', 'sendRequest failed');
  }
  hilog.info(0x0000, 'testTag', 'sendRequest ends, reclaim parcel');
  data.reclaim();
  reply.reclaim();
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

### sendMessageRequest<sup>9+</sup>

sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption): Promise&lt;RequestResult&gt;

Sends a **MessageSequence** message to the remote process in synchronous or asynchronous mode. If asynchronous mode is set in **options**, a promise will be fulfilled immediately and the reply message is empty. The specific reply needs to be obtained from the callback on the service side. If synchronous mode is set in **options**, a promise will be fulfilled when the response to **sendMessageRequest** is returned, and the reply message contains the returned information.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name | Type                                | Mandatory| Description                                                                                  |
  | ------- | ------------------------------------ | ---- | -------------------------------------------------------------------------------------- |
  | code    | number                               | Yes  | Message code (1-16777215) called by the request, which is determined by the communication parties. If the method is generated by an IDL tool, the message code is automatically generated by the IDL tool.|
  | data    | [MessageSequence](#messagesequence9) | Yes  | **MessageSequence** object holding the data to send.                                           |
  | reply   | [MessageSequence](#messagesequence9) | Yes  | **MessageSequence** object that receives the response.                                                   |
  | options | [MessageOption](#messageoption)      | Yes  | Request sending mode, which can be synchronous (default) or asynchronous.                                                  |

**Return value**

| Type                                           | Description                                     |
| ----------------------------------------------- | ----------------------------------------- |
| Promise&lt;[RequestResult](#requestresult9)&gt; | Promise used to return a **RequestResult** instance.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match; <br> 3.Failed to obtain the passed object instance. |

**Example**

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

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
  let testRemoteObject = new TestRemoteObject("testObject");
  let option = new rpc.MessageOption();
  let data = rpc.MessageSequence.create();
  let reply = rpc.MessageSequence.create();
  data.writeInt(1);
  data.writeString("hello");
  testRemoteObject.sendMessageRequest(1, data, reply, option)
    .then((result: rpc.RequestResult) => {
      if (result.errCode === 0) {
        hilog.info(0x0000, 'testTag', 'sendMessageRequest got result');
        let num = result.reply.readInt();
        let msg = result.reply.readString();
        hilog.info(0x0000, 'testTag', 'reply num: ' + num);
        hilog.info(0x0000, 'testTag', 'reply msg: ' + msg);
      } else {
        hilog.error(0x0000, 'testTag', 'sendMessageRequest failed, errCode: ' + result.errCode);
      }
    }).catch((e: Error) => {
      hilog.error(0x0000, 'testTag', 'sendMessageRequest failed, error: ' + e);
    }).finally (() => {
      hilog.info(0x0000, 'testTag', 'sendMessageRequest ends, reclaim parcel');
      data.reclaim();
      reply.reclaim();
    });
} catch (error) {
  hilog.error(0x0000, 'testTag', 'sendMessageRequest failed, error: ' + error);
}
```

### sendRequest<sup>(deprecated)</sup>

sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): Promise&lt;SendRequestResult&gt;

Sends a **MessageParcel** message to the remote process in synchronous or asynchronous mode. If asynchronous mode is set in **options**, a promise will be fulfilled immediately and the reply message is empty. The specific reply needs to be obtained from the callback on the service side. If synchronous mode is set in **options**, a promise will be fulfilled when the response to **sendRequest** is returned, and the reply message contains the returned information.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [sendMessageRequest](#sendmessagerequest9-4) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name | Type                                     | Mandatory| Description                                                                                  |
  | ------- | ----------------------------------------- | ---- | -------------------------------------------------------------------------------------- |
  | code    | number                                    | Yes  | Message code (1-16777215) called by the request, which is determined by the communication parties. If the method is generated by an IDL tool, the message code is automatically generated by the IDL tool.|
  | data    | [MessageParcel](#messageparceldeprecated) | Yes  | **MessageParcel** object holding the data to send.                                             |
  | reply   | [MessageParcel](#messageparceldeprecated) | Yes  | **MessageParcel** object that receives the response.                                                     |
  | options | [MessageOption](#messageoption)           | Yes  | Request sending mode, which can be synchronous (default) or asynchronous.                                                  |

**Return value**

| Type                                                        | Description                                         |
| ------------------------------------------------------------ | --------------------------------------------- |
| Promise&lt;[SendRequestResult](#sendrequestresultdeprecated)&gt; | Promise used to return a **sendRequestResult** instance.|

**Example**

<!--deprecated_code_no_check-->
```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteRequest(code: number, data: rpc.MessageParcel, reply: rpc.MessageParcel, option: rpc.MessageOption): boolean {
    // Process services based on the actual service logic.
    return true;
  }
}
try {
  let testRemoteObject = new TestRemoteObject("testObject");
  let option = new rpc.MessageOption();
  let data = rpc.MessageParcel.create();
  let reply = rpc.MessageParcel.create();
  data.writeInt(1);
  data.writeString("hello");
  let a = testRemoteObject.sendRequest(1, data, reply, option) as Object;
  let b = a as Promise<rpc.SendRequestResult>;
  b.then((result: rpc.SendRequestResult) => {
    if (result.errCode === 0) {
      hilog.info(0x0000, 'testTag', 'sendRequest got result');
      let num = result.reply.readInt();
      let msg = result.reply.readString();
      hilog.info(0x0000, 'testTag', 'reply num: ' + num);
      hilog.info(0x0000, 'testTag', 'reply msg: ' + msg);
    } else {
      hilog.error(0x0000, 'testTag', 'sendRequest failed, errCode: ' + result.errCode);
    }
  }).catch((e: Error) => {
    hilog.error(0x0000, 'testTag', 'sendRequest failed, error: ' + e);
  }).finally (() => {
    hilog.info(0x0000, 'testTag', 'sendRequest ends, reclaim parcel');
    data.reclaim();
    reply.reclaim();
  });
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error: ' + error);
}
```

### sendMessageRequest<sup>9+</sup>

sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption, callback: AsyncCallback&lt;RequestResult&gt;): void

Sends a **MessageSequence** message to the remote process in synchronous or asynchronous mode. If asynchronous mode is set in **options**, a callback will be called immediately, and the reply message is empty. The specific reply needs to be obtained from the callback on the service side. If synchronous mode is set in **options**, a callback will be invoked when the response to **sendMessageRequest** is returned, and the reply message contains the returned information.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

| Name       | Type                                                 | Mandatory| Description                                                        |
| ------------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| code          | number                                                | Yes  | Message code (1-16777215) called by the request, which is determined by the communication parties. If the method is generated by an IDL tool, the message code is automatically generated by the IDL tool.|
| data          | [MessageSequence](#messagesequence9)                  | Yes  | **MessageSequence** object holding the data to send.                 |
| reply         | [MessageSequence](#messagesequence9)                  | Yes  | **MessageSequence** object that receives the response.                         |
| options       | [MessageOption](#messageoption)                       | Yes  | Request sending mode, which can be synchronous (default) or asynchronous.                        |
| callback      | AsyncCallback&lt;[RequestResult](#requestresult9)&gt; | Yes  | Callback for receiving the sending result.                                        |

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match; <br> 3.Failed to obtain the passed object instance. |

### sendRequest<sup>(deprecated)</sup> 

sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption, callback: AsyncCallback&lt;SendRequestResult&gt;): void

Sends a **MessageParcel** message to the remote process in synchronous or asynchronous mode. If asynchronous mode is set in **options**, a callback will be called immediately, and the reply message is empty. The specific reply needs to be obtained from the callback on the service side. If synchronous mode is set in **options**, a callback will be invoked when the response to **sendRequest** is returned, and the reply message contains the returned information.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [sendMessageRequest](#sendmessagerequest9-5) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

| Name       | Type                                                        | Mandatory| Description                                                        |
| ------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| code          | number                                                       | Yes  | Message code (1-16777215) called by the request, which is determined by the communication parties. If the method is generated by an IDL tool, the message code is automatically generated by the IDL tool.|
| data          | [MessageParcel](#messageparceldeprecated)                    | Yes  | **MessageParcel** object holding the data to send.                   |
| reply         | [MessageParcel](#messageparceldeprecated)                    | Yes  | **MessageParcel** object that receives the response.                           |
| options       | [MessageOption](#messageoption)                              | Yes  | Request sending mode, which can be synchronous (default) or asynchronous.                        |
| callback      | AsyncCallback&lt;[SendRequestResult](#sendrequestresultdeprecated)&gt; | Yes  | Callback for receiving the sending result.                                        |

### onRemoteMessageRequest<sup>23+</sup>

onRemoteMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption, callingInfo?: CallingInfo): boolean | Promise\<boolean>

Provides a response to **sendMessageRequest()**. The server processes the request and returns a response in this API. The IPC context can be obtained from the input parameter **callingInfo**.

> **NOTE**
>
> - You are advised to overload the **onRemoteMessageRequest** method with the **CallingInfo** parameter to implement synchronous and asynchronous message processing.
> - If both **onRemoteRequest()** and **onRemoteMessageRequest()** are overloaded, only **onRemoteMessageRequest()** takes effect.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type                                | Mandatory| Description                                     |
  | ------ | ------------------------------------ | ---- | ----------------------------------------- |
  | code   | number                               | Yes  | Service request code sent by the remote end.                   |
  | data   | [MessageSequence](#messagesequence9) | Yes  | **MessageSequence** object that holds the parameters called by the client.|
  | reply  | [MessageSequence](#messagesequence9) | Yes  | **MessageSequence** object to which the result is written.          |
  | options | [MessageOption](#messageoption)      | Yes  | Whether the operation is synchronous or asynchronous.                 |
  | callingInfo | [CallingInfo](#callinginfo23)      | Yes  | IPC context.                 |

**Return value**

  | Type             | Description                                                                                           |
  | ----------------- | ----------------------------------------------------------------------------------------------- |
  | boolean \| Promise\<boolean>  | - If the request is processed synchronously in **onRemoteMessageRequest**, a Boolean value is returned. The value **true** means that the operation is successful, and **false** means the opposite.<br>- If the request is processed asynchronously in **onRemoteMessageRequest**, a promise object is returned. The value **true** means that the operation is successful, and **false** means the opposite.|

**Example**: Overload **onRemoteMessageRequest** to process requests synchronously.

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }

  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption, callingInfo?: CallingInfo): boolean | Promise<boolean> {
    if (code === 1) {
      hilog.info(0x0000, 'testTag', 'RpcServer: sync onRemoteMessageRequest is called');
      let pid = callingInfo.callerPid;
      return true;
    } else {
      hilog.error(0x0000, 'testTag', 'RpcServer: unknown code: ' + code);
      return false;
    }
  }
}
```

  **Example**: Overload **onRemoteMessageRequest** to process requests asynchronously.

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }

  async onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption, callingInfo?: CallingInfo): Promise<boolean> {
    if (code === 1) {
      hilog.info(0x0000, 'testTag', 'RpcServer: async onRemoteMessageRequest is called');
      let pid = callingInfo.callerPid;
    } else {
      hilog.error(0x0000, 'testTag', 'RpcServer: unknown code: ' + code);
      return false;
    }
    await new Promise((resolve: (data: rpc.RequestResult) => void) => {
      setTimeout(resolve, 100);
    })
    return true;
  }
}
```

**Example**: Overload **onRemoteMessageRequest** and **onRemoteRequest** to process requests synchronously.

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }

  onRemoteRequest(code: number, data: rpc.MessageParcel, reply: rpc.MessageParcel, option: rpc.MessageOption): boolean {
     if (code === 1) {
        hilog.info(0x0000, 'testTag', 'RpcServer: sync onRemoteMessageRequest is called');
        return true;
     } else {
        hilog.error(0x0000, 'testTag', 'RpcServer: unknown code: ' + code);
        return false;
     }
  }
    // Only onRemoteMessageRequest is executed.
  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption, callingInfo?: CallingInfo): boolean | Promise<boolean> {
    if (code === 1) {
      hilog.info(0x0000, 'testTag', 'RpcServer: async onRemoteMessageRequest is called');
      let pid = callingInfo.callerPid;
    } else {
      hilog.error(0x0000, 'testTag', 'RpcServer: unknown code: ' + code);
      return false;
    }
    return true;
  }
}
```

  **Example**: Overload **onRemoteMessageRequest** and **onRemoteRequest** to process requests asynchronously.

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }

  onRemoteRequest(code: number, data: rpc.MessageParcel, reply: rpc.MessageParcel, option: rpc.MessageOption): boolean {
    if (code === 1) {
      hilog.info(0x0000, 'testTag', 'RpcServer: sync onRemoteRequest is called');
      return true;
    } else {
      hilog.error(0x0000, 'testTag', 'RpcServer: unknown code: ' + code);
      return false;
    }
  }
  // Only onRemoteMessageRequest is executed.
  async onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption, callingInfo?: CallingInfo): Promise<boolean> {
    if (code === 1) {
      hilog.info(0x0000, 'testTag', 'RpcServer: async onRemoteMessageRequest is called');
      let pid = callingInfo.callerPid;
    } else {
      hilog.error(0x0000, 'testTag', 'RpcServer: unknown code: ' + code);
      return false;
    }
    await new Promise((resolve: (data: rpc.RequestResult) => void) => {
      setTimeout(resolve, 100);
    })
    return true;
  }
}
```

### onRemoteMessageRequest<sup>9+</sup>

onRemoteMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption): boolean | Promise\<boolean>

> **NOTE**
>
> - You are advised to overload **onRemoteMessageRequest** preferentially, which implements synchronous and asynchronous message processing.
> - If both **onRemoteRequest()** and **onRemoteMessageRequest()** are overloaded, only **onRemoteMessageRequest()** takes effect.

Called to return a response to **sendMessageRequest()**. The server processes the request synchronously or asynchronously and returns the result in this API.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type                                | Mandatory| Description                                     |
  | ------ | ------------------------------------ | ---- | ----------------------------------------- |
  | code   | number                               | Yes  | Service request code sent by the remote end.                   |
  | data   | [MessageSequence](#messagesequence9) | Yes  | **MessageSequence** object that holds the parameters called by the client.|
  | reply  | [MessageSequence](#messagesequence9) | Yes  | **MessageSequence** object to which the result is written.          |
  | options | [MessageOption](#messageoption)      | Yes  | Whether the operation is synchronous or asynchronous.                 |

**Return value**

  | Type             | Description                                                                                           |
  | ----------------- | ----------------------------------------------------------------------------------------------- |
  | boolean \| Promise\<boolean>  | - If the request is processed synchronously in **onRemoteMessageRequest**, a Boolean value is returned. The value **true** means that the operation is successful, and **false** means the opposite.<br>- If the request is processed asynchronously in **onRemoteMessageRequest**, a promise object is returned. The value **true** means that the operation is successful, and **false** means the opposite.|

**Example**: Overload **onRemoteMessageRequest** to process requests synchronously.

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }

  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean | Promise<boolean> {
    if (code === 1) {
      hilog.info(0x0000, 'testTag', 'RpcServer: sync onRemoteMessageRequest is called');
      return true;
    } else {
      hilog.error(0x0000, 'testTag', 'RpcServer: unknown code: ' + code);
      return false;
    }
  }
}
```

  **Example**: Overload **onRemoteMessageRequest** to process requests asynchronously.

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }

  async onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): Promise<boolean> {
    if (code === 1) {
      hilog.info(0x0000, 'testTag', 'RpcServer: async onRemoteMessageRequest is called');
    } else {
      hilog.error(0x0000, 'testTag', 'RpcServer: unknown code: ' + code);
      return false;
    }
    await new Promise((resolve: (data: rpc.RequestResult) => void) => {
      setTimeout(resolve, 100);
    })
    return true;
  }
}
```

**Example**: Overload **onRemoteMessageRequest** and **onRemoteRequest** to process requests synchronously.

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }

  onRemoteRequest(code: number, data: rpc.MessageParcel, reply: rpc.MessageParcel, option: rpc.MessageOption): boolean {
     if (code === 1) {
        hilog.info(0x0000, 'testTag', 'RpcServer: sync onRemoteMessageRequest is called');
        return true;
     } else {
        hilog.error(0x0000, 'testTag', 'RpcServer: unknown code: ' + code);
        return false;
     }
  }
    // Only onRemoteMessageRequest is executed.
  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean | Promise<boolean> {
    if (code === 1) {
      hilog.info(0x0000, 'testTag', 'RpcServer: async onRemoteMessageRequest is called');
    } else {
      hilog.error(0x0000, 'testTag', 'RpcServer: unknown code: ' + code);
      return false;
    }
    return true;
  }
}
```

  **Example**: Overload **onRemoteMessageRequest** and **onRemoteRequest** to process requests asynchronously.

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }

  onRemoteRequest(code: number, data: rpc.MessageParcel, reply: rpc.MessageParcel, option: rpc.MessageOption): boolean {
    if (code === 1) {
      hilog.info(0x0000, 'testTag', 'RpcServer: sync onRemoteRequest is called');
      return true;
    } else {
      hilog.error(0x0000, 'testTag', 'RpcServer: unknown code: ' + code);
      return false;
    }
  }
  // Only onRemoteMessageRequest is executed.
  async onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): Promise<boolean> {
    if (code === 1) {
      hilog.info(0x0000, 'testTag', 'RpcServer: async onRemoteMessageRequest is called');
    } else {
      hilog.error(0x0000, 'testTag', 'RpcServer: unknown code: ' + code);
      return false;
    }
    await new Promise((resolve: (data: rpc.RequestResult) => void) => {
      setTimeout(resolve, 100);
    })
    return true;
  }
}
```

### onRemoteRequest<sup>(deprecated)</sup>

onRemoteRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean

Called to return a response to **sendRequest()**. The server processes the request and returns a response in this function.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [onRemoteMessageRequest](#onremotemessagerequest9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type                                     | Mandatory| Description                                   |
  | ------ | ----------------------------------------- | ---- | --------------------------------------- |
  | code   | number                                    | Yes  | Service request code sent by the remote end.                 |
  | data   | [MessageParcel](#messageparceldeprecated) | Yes  | **MessageParcel** object that holds the parameters called by the client.|
  | reply  | [MessageParcel](#messageparceldeprecated) | Yes  | **MessageParcel** object carrying the result.          |
  | options | [MessageOption](#messageoption)           | Yes  | Whether the operation is synchronous or asynchronous.               |

**Return value**

  | Type   | Description                            |
  | ------- | -------------------------------- |
  | boolean | Returns **true** if the operation is successful; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteRequest(code: number, data: rpc.MessageParcel, reply: rpc.MessageParcel, option: rpc.MessageOption): boolean {
    if (code === 1) {
      hilog.info(0x0000, 'testTag', 'RpcServer: onRemoteRequest called');
      return true;
    } else {
      hilog.error(0x0000, 'testTag', 'RpcServer: unknown code: ' + code);
      return false;
    }
  }
}
```

### getCallingUid

getCallingUid(): number

Obtains the UID of the remote process.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**
  | Type  | Description                   |
  | ------ | ----------------------- |
  | number | UID of the remote process obtained.|

**Example**

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

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
  let testRemoteObject = new TestRemoteObject("testObject");
  hilog.info(0x0000, 'testTag', 'RpcServer: getCallingUid: ' + testRemoteObject.getCallingUid());
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error: ' + error);
}
```

### getCallingPid

getCallingPid(): number

Obtains the PID of the remote process.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description                   |
  | ------ | ----------------------- |
  | number | PID of the remote process obtained.|

**Example**

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

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
  let testRemoteObject = new TestRemoteObject("testObject");
  hilog.info(0x0000, 'testTag', 'RpcServer: getCallingPid: ' + testRemoteObject.getCallingPid());
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error: ' + error);
}
```

### getLocalInterface<sup>9+</sup>

getLocalInterface(descriptor: string): IRemoteBroker

Obtains the string of the interface descriptor.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name    | Type  | Mandatory| Description                |
  | ---------- | ------ | ---- | -------------------- |
  | descriptor | string | Yes  | String of the interface descriptor. The length of the string must be less than 40960 bytes.|

**Return value**

  | Type         | Description                                         |
  | ------------- | --------------------------------------------- |
  | [IRemoteBroker](#iremotebroker) | **IRemoteBroker** object bound to the specified interface token.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match; <br> 3.The string length is greater than or equal to 40960 bytes; <br> 4.The number of bytes copied to the buffer is different from the length of the obtained string. |

**Example**

```ts
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
  let testRemoteObject = new TestRemoteObject("testObject");
  testRemoteObject.getLocalInterface("testObject");
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

### queryLocalInterface<sup>(deprecated)</sup>

queryLocalInterface(descriptor: string): IRemoteBroker

Checks whether the remote object corresponding to the specified interface token exists.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [getLocalInterface](#getlocalinterface9-2) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name    | Type  | Mandatory| Description                  |
  | ---------- | ------ | ---- | ---------------------- |
  | descriptor | string | Yes  | Interface descriptor.|

**Return value**

  | Type         | Description                                                              |
  | ------------- | ------------------------------------------------------------------ |
  | [IRemoteBroker](#iremotebroker) | Returns the remote object if a match is found; returns **Null** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

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
  let testRemoteObject = new TestRemoteObject("testObject");
  testRemoteObject.queryLocalInterface("testObject");
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error: ' + error);
}
```

### getDescriptor<sup>9+</sup>

getDescriptor(): string

Obtains the interface descriptor of this object. The interface descriptor is a string.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description            |
  | ------ | ---------------- |
  | string | Interface descriptor obtained.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 1900008  | The proxy or remote object is invalid. |

**Example**

```ts
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
  let testObject = new TestRemoteObject("ipcTest");
  let descriptor = testObject.getDescriptor();
  hilog.info(0x0000, 'testTag', 'RpcServer: descriptor is ' + descriptor);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

### getInterfaceDescriptor<sup>(deprecated)</sup>

getInterfaceDescriptor(): string

Obtains the interface descriptor.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [getDescriptor](#getdescriptor9-2) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description            |
  | ------ | ---------------- |
  | string | Interface descriptor obtained.|

**Example**

<!--deprecated_code_no_check-->
```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

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
  let testRemoteObject = new TestRemoteObject("testObject");
  let descriptor = testRemoteObject.getInterfaceDescriptor();
  hilog.info(0x0000, 'testTag', 'RpcServer: descriptor is: ' + descriptor);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

### modifyLocalInterface<sup>9+</sup>

modifyLocalInterface(localInterface: IRemoteBroker, descriptor: string): void

Binds an interface descriptor to an **IRemoteBroker** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

| Name        | Type                           | Mandatory| Description                                 |
| -------------- | ------------------------------- | ---- | ------------------------------------- |
| localInterface | [IRemoteBroker](#iremotebroker) | Yes  | **IRemoteBroker** object.  |
| descriptor     | string                          | Yes  | **IRemoteBroker** object bound to the interface descriptor. The length of the descriptor must be less than 40960 bytes.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match; <br> 3.The string length is greater than or equal to 40960 bytes; <br> 4.The number of bytes copied to the buffer is different from the length of the obtained string. |

**Example**

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

class MyDeathRecipient implements rpc.DeathRecipient {
  onRemoteDied() {
    hilog.info(0x0000, 'testTag', 'server died');
  }
}
class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
    try {
      this.modifyLocalInterface(this, descriptor);
    } catch (error) {
      let e: BusinessError = error as BusinessError;
      hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
      hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
    }
  }
  registerDeathRecipient(recipient: MyDeathRecipient, flags: number) {
    // Implement the method logic based on service requirements.
  }
  unregisterDeathRecipient(recipient: MyDeathRecipient, flags: number) {
    // Implement the method logic based on service requirements.
  }
}
let testRemoteObject = new TestRemoteObject("testObject");
```

### attachLocalInterface<sup>(deprecated)</sup>

attachLocalInterface(localInterface: IRemoteBroker, descriptor: string): void

Binds an interface descriptor to an **IRemoteBroker** object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [modifyLocalInterface](#modifylocalinterface9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

| Name        | Type                           | Mandatory| Description                                 |
| -------------- | ------------------------------- | ---- | ------------------------------------- |
| localInterface | [IRemoteBroker](#iremotebroker) | Yes  | **IRemoteBroker** object.  |
| descriptor     | string                          | Yes  | Interface descriptor.|

**Example**

<!--deprecated_code_no_check-->
```ts
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
    this.attachLocalInterface(this, descriptor);
  }
  addDeathRecipient(recipient: MyDeathRecipient, flags: number): boolean {
    // Implement the method logic based on service requirements.
    return true;
  }
  removeDeathRecipient(recipient: MyDeathRecipient, flags: number): boolean {
    // Implement the method logic based on service requirements.
    return true;
  }
}
let testRemoteObject = new TestRemoteObject("testObject");
```

## Ashmem<sup>8+</sup>

Provides methods related to anonymous shared memory objects, including creating, closing, mapping, and unmapping an **Ashmem** object, reading data from and writing data to an **Ashmem** object, obtaining the **Ashmem** size, and setting **Ashmem** protection.

The shared memory applies only to cross-process communication within the local device.

### Properties

**System capability**: SystemCapability.Communication.IPC.Core

  | Name      | Type  | Read-Only | Optional | Description                                    |
  | ---------- | ------ | ----- | ----- |----------------------------------------- |
  | PROT_EXEC  | number | Yes   | No   | Mapped memory protection type, indicating that the mapped memory is executable. |
  | PROT_NONE  | number | Yes   | No   | Mapped memory protection type, indicating that the mapped memory cannot be accessed.|
  | PROT_READ  | number | Yes   | No   | Mapped memory protection type, indicating that the mapped memory is readable.   |
  | PROT_WRITE | number | Yes   | No   | Mapped memory protection type, indicating that the mapped memory is readable.   |

### create<sup>9+</sup>

static create(name: string, size: number): Ashmem

Creates an **Ashmem** object with the specified name and size. This API is a static method.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description                        |
  | ------ | ------ | ---- | ---------------------------- |
  | name   | string | Yes  | Name of the **Ashmem** object to create. The length of the Ashmem name cannot be 0.  |
  | size   | number | Yes  | Size of the **Ashmem** object, in bytes. The value must be greater than 0.|

**Return value**

| Type              | Description                                          |
| ------------------ | ---------------------------------------------- |
| [Ashmem](#ashmem8) | Returns the **Ashmem** object if it is created successfully; returns null otherwise.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match; <br> 3.The Ashmem name passed is empty; <br> 4.The Ashmem size passed is less than or equal to 0. |

**Example**

```ts
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

### createAshmem<sup>(deprecated)</sup>

static createAshmem(name: string, size: number): Ashmem

Creates an **Ashmem** object with the specified name and size. This API is a static method.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [create](#create9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description                        |
  | ------ | ------ | ---- | ---------------------------- |
  | name   | string | Yes  | Name of the **Ashmem** object to create.  |
  | size   | number | Yes  | Size (in bytes) of the **Ashmem** object to create.|

**Return value**

| Type              | Description                                          |
| ------------------ | ---------------------------------------------- |
| [Ashmem](#ashmem8) | Returns the **Ashmem** object if it is created successfully; returns null otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### create<sup>9+</sup>

static create(ashmem: Ashmem): Ashmem

Creates an **Ashmem** object by copying the file descriptor of an existing **Ashmem** object. The two **Ashmem** objects point to the same shared memory region.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

| Name| Type              | Mandatory| Description                |
| ------ | ------------------ | ---- | -------------------- |
| ashmem | [Ashmem](#ashmem8) | Yes  | Existing **Ashmem** object.|

**Return value**

| Type              | Description                  |
| ------------------ | ---------------------- |
| [Ashmem](#ashmem8) | **Ashmem** object created.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The passed parameter is not an Ahmem object; <br> 3.The ashmem instance for obtaining packaging is empty. |

**Example**

```ts
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

### createAshmemFromExisting<sup>(deprecated)</sup>

static createAshmemFromExisting(ashmem: Ashmem): Ashmem

Creates an **Ashmem** object by copying the file descriptor of an existing **Ashmem** object. The two **Ashmem** objects point to the same shared memory region.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [create](#create9-1) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

| Name| Type              | Mandatory| Description                |
| ------ | ------------------ | ---- | -------------------- |
| ashmem | [Ashmem](#ashmem8) | Yes  | Existing **Ashmem** object.|

**Return value**

| Type              | Description                  |
| ------------------ | ---------------------- |
| [Ashmem](#ashmem8) | **Ashmem** object created.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### closeAshmem<sup>8+</sup>

closeAshmem(): void

Closes this **Ashmem** object.

> **NOTE**
>
> Before closing the **Ashmem** object, you need to remove the address mapping.

**System capability**: SystemCapability.Communication.IPC.Core

**Example**

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let ashmem = rpc.Ashmem.create("ashmem", 1024*1024);
  ashmem.closeAshmem();
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error is ' + error);
}
```

### unmapAshmem<sup>8+</sup>

unmapAshmem(): void

Deletes the mappings for the specified address range of this **Ashmem** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Example**

```ts
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let ashmem = rpc.Ashmem.create("ashmem", 1024*1024);
  ashmem.unmapAshmem();
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error is ' + error);
}
```

### getAshmemSize<sup>8+</sup>

getAshmemSize(): number

Obtains the memory size of this **Ashmem** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type  | Description                      |
  | ------ | -------------------------- |
  | number | **Ashmem** size obtained.|

**Example**

```ts
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

### mapTypedAshmem<sup>9+</sup>

mapTypedAshmem(mapType: number): void

Creates the shared file mapping on the virtual address space of this process. The size of the mapping region is specified by this **Ashmem** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name | Type  | Mandatory| Description                          |
  | ------- | ------ | ---- | ------------------------------ |
  | mapType | number | Yes  | Protection level of the memory region to which the shared file is mapped.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect;  <br> 2.The parameter type does not match; <br> 3.The passed mapType exceeds the maximum protection level. |
  | 1900001  | Failed to call mmap. |

**Example**

```ts
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

### mapAshmem<sup>(deprecated)</sup>

mapAshmem(mapType: number): boolean

Creates the shared file mapping on the virtual address space of this process. The size of the mapping region is specified by this **Ashmem** object.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [mapTypedAshmem](#maptypedashmem9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name | Type  | Mandatory| Description                          |
  | ------- | ------ | ---- | ------------------------------ |
  | mapType | number | Yes  | Protection level of the memory region to which the shared file is mapped.|

**Return value**

  | Type   | Description                            |
  | ------- | -------------------------------- |
  | boolean | Returns **true** if the mapping is created; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### mapReadWriteAshmem<sup>9+</sup>

mapReadWriteAshmem(): void

Maps the shared file to the readable and writable virtual address space of the process.

**System capability**: SystemCapability.Communication.IPC.Core

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 1900001  | Failed to call mmap. |

**Example**

```ts
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

### mapReadAndWriteAshmem<sup>(deprecated)</sup>

mapReadAndWriteAshmem(): boolean

Maps the shared file to the readable and writable virtual address space of the process.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [mapReadWriteAshmem](#mapreadwriteashmem9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type   | Description                            |
  | ------- | -------------------------------- |
  | boolean | Returns **true** if the mapping is created; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### mapReadonlyAshmem<sup>9+</sup>

mapReadonlyAshmem(): void

Maps the shared file to the read-only virtual address space of the process.

**System capability**: SystemCapability.Communication.IPC.Core

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 1900001  | Failed to call mmap. |

**Example**

```ts
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

### mapReadOnlyAshmem<sup>(deprecated)</sup>

mapReadOnlyAshmem(): boolean

Maps the shared file to the read-only virtual address space of the process.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [mapReadonlyAshmem](#mapreadonlyashmem9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Return value**

  | Type   | Description                            |
  | ------- | -------------------------------- |
  | boolean | Returns **true** if the mapping is created; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### setProtectionType<sup>9+</sup>

setProtectionType(protectionType: number): void

Sets the protection level of the memory region to which the shared file is mapped.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name        | Type  | Mandatory| Description              |
  | -------------- | ------ | ---- | ------------------ |
  | protectionType | number | Yes  | Protection type to set.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match. |
  | 1900002  | Failed to call ioctl. |

**Example**

```ts
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

### setProtection<sup>(deprecated)</sup>

setProtection(protectionType: number): boolean

Sets the protection level of the memory region to which the shared file is mapped.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [setProtectionType](#setprotectiontype9) instead.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name        | Type  | Mandatory| Description              |
  | -------------- | ------ | ---- | ------------------ |
  | protectionType | number | Yes  | Protection type to set.|

**Return value**

  | Type   | Description                            |
  | ------- | -------------------------------- |
  | boolean | Returns **true** if the operation is successful; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### writeDataToAshmem<sup>11+</sup>

writeDataToAshmem(buf: ArrayBuffer, size: number, offset: number): void

Writes data to the shared file associated with this **Ashmem** object.

> **NOTE**
>
> Before writing an **Ashmem** object, you need to call [mapReadWriteAshmem](#mapreadwriteashmem9) for mapping.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type    | Mandatory| Description                                              |
  | ------ | -------- | ---- | -------------------------------------------------- |
  | buf    | ArrayBuffer | Yes  | Data to write.                            |
  | size   | number   | Yes  | Size of the data to write.                                |
  | offset | number   | Yes  | Start position of the data to write in the memory region associated with this **Ashmem** object.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match; <br> 3.Failed to obtain arrayBuffer information. |
  | 1900003  | Failed to write data to the shared memory. |

**Example**

```ts
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

### writeAshmem<sup>(deprecated)</sup>

writeAshmem(buf: number[], size: number, offset: number): void

Writes data to the shared file associated with this **Ashmem** object.

> **NOTE**
>
> - This API is supported since API version 9 and deprecated since API version 11. Use [writeDataToAshmem](#writedatatoashmem11) instead.
>
> - Before writing an **Ashmem** object, you need to call [mapReadWriteAshmem](#mapreadwriteashmem9) for mapping.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type    | Mandatory| Description                                              |
  | ------ | -------- | ---- | -------------------------------------------------- |
  | buf    | number[] | Yes  | Data to write.                            |
  | size   | number   | Yes  | Size of the data to write.                                |
  | offset | number   | Yes  | Start position of the data to write in the memory region associated with this **Ashmem** object.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match; <br> 3.The element does not exist in the array. |
  | 1900003  | Failed to write data to the shared memory. |

**Example**

<!--deprecated_code_no_check-->
```ts
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

### writeToAshmem<sup>(deprecated)</sup>

writeToAshmem(buf: number[], size: number, offset: number): boolean

Writes data to the shared file associated with this **Ashmem** object.

> **NOTE**
>
> - This API is supported since API version 8 and deprecated since API version 9. Use [writeDataToAshmem](#writedatatoashmem11) instead.
>
> - Before writing an **Ashmem** object, you need to call [mapReadWriteAshmem](#mapreadwriteashmem9) for mapping.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type    | Mandatory| Description                                              |
  | ------ | -------- | ---- | -------------------------------------------------- |
  | buf    | number[] | Yes  | Data to write.                            |
  | size   | number   | Yes  | Size of the data to write.                                |
  | offset | number   | Yes  | Start position of the data to write in the memory region associated with this **Ashmem** object.|

**Return value**

  | Type   | Description                                                                         |
  | ------- | ----------------------------------------------------------------------------- |
  | boolean | Returns **true** if the data is written successfully; returns **false** otherwise.|

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readDataFromAshmem<sup>11+</sup>

readDataFromAshmem(size: number, offset: number): ArrayBuffer

Reads data from the shared file associated with this **Ashmem** object.

> **NOTE**
>
> Before writing an **Ashmem** object, you need to call [mapReadWriteAshmem](#mapreadwriteashmem9) for mapping.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description                                              |
  | ------ | ------ | ---- | -------------------------------------------------- |
  | size   | number | Yes  | Size of the data to read.                              |
  | offset | number | Yes  | Start position of the data to read in the memory region associated with this **Ashmem** object.|

**Return value**

  | Type    | Description            |
  | -------- | ---------------- |
  | ArrayBuffer | Data read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match. |
  | 1900004  | Failed to read data from the shared memory. |

**Example**

```ts
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

### readAshmem<sup>(deprecated)</sup>

readAshmem(size: number, offset: number): number[]

Reads data from the shared file associated with this **Ashmem** object.

> **NOTE**
>
> - This API is supported since API version 9 and deprecated since API version 11. Use [readDataFromAshmem](#readdatafromashmem11) instead.
>
> - Before writing an **Ashmem** object, you need to call [mapReadWriteAshmem](#mapreadwriteashmem9) for mapping.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description                                              |
  | ------ | ------ | ---- | -------------------------------------------------- |
  | size   | number | Yes  | Size of the data to read.                              |
  | offset | number | Yes  | Start position of the data to read in the memory region associated with this **Ashmem** object.|

**Return value**

  | Type    | Description            |
  | -------- | ---------------- |
  | number[] | Data read.|

**Error codes**

For details about the error codes, see [RPC Error Codes](errorcode-rpc.md).

  | ID| Error Message|
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: <br> 1.The number of parameters is incorrect; <br> 2.The parameter type does not match. |
  | 1900004  | Failed to read data from the shared memory. |

**Example**

<!--deprecated_code_no_check-->
```ts
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

### readFromAshmem<sup>(deprecated)</sup>

readFromAshmem(size: number, offset: number): number[]

Reads data from the shared file associated with this **Ashmem** object.

> **NOTE**
>
> - This API is supported since API version 8 and deprecated since API version 9. Use [readDataFromAshmem](#readdatafromashmem11) instead.
>
> - Before writing an **Ashmem** object, you need to call [mapReadWriteAshmem](#mapreadwriteashmem9) for mapping.

**System capability**: SystemCapability.Communication.IPC.Core

**Parameters**

  | Name| Type  | Mandatory| Description                                              |
  | ------ | ------ | ---- | -------------------------------------------------- |
  | size   | number | Yes  | Size of the data to read.                              |
  | offset | number | Yes  | Start position of the data to read in the memory region associated with this **Ashmem** object.|

**Return value**

  | Type    | Description            |
  | -------- | ---------------- |
  | number[] | Data read.|

**Example**

<!--deprecated_code_no_check-->
``` ts
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
