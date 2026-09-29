# Ashmem

```TypeScript
class Ashmem
```

Provides methods related to anonymous shared memory objects, including creating, closing, mapping, and unmapping an **Ashmem** object, reading data from and writing data to an **Ashmem** object, obtaining the **Ashmem** size, and setting **Ashmem** protection.

The shared memory applies only to cross-process communication within the local device.

- Large data transmission: When transmitting large amounts of data (such as images or files), shared memory can be  
used to improve efficiency.  
- Cross-process data sharing: Multiple processes need to share access to the same block of memory data.  
- Transmission efficiency: Transmitting large data via shared memory avoids serialization overhead and improves  
transmission efficiency.  
- Memory reuse: Multiple processes can share access to the same memory, avoiding data duplication.  
- Improved transmission performance: The shared memory mechanism significantly improves the efficiency of large  
data transmission.  
- Reduced memory usage: Avoiding multiple data copies helps save memory resources.

**Since:** 8

<!--Device-rpc-class Ashmem--><!--Device-rpc-class Ashmem-End-->

**System capability:** SystemCapability.Communication.IPC.Core

## Modules to Import

```TypeScript
import { rpc } from '@kit.IPCKit';
```

## closeAshmem

```TypeScript
closeAshmem(): void
```

Closes this **Ashmem** object.

> **NOTE:** 
> 
> Before closing the **Ashmem** object, you need to remove the address mapping.

**Since:** 8

<!--Device-Ashmem-closeAshmem(): void--><!--Device-Ashmem-closeAshmem(): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Examples**

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
static create(name: string, size: number): Ashmem
```

Creates an **Ashmem** object with the specified name and size. This API is a static method.

**Since:** 9

<!--Device-Ashmem-static create(name: string, size: int): Ashmem--><!--Device-Ashmem-static create(name: string, size: int): Ashmem-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the **Ashmem** object to create. The length of the Ashmem name cannot be 0. |
| size | number | Yes | Size of the **Ashmem** object, in bytes. The value must be greater than 0. |

**Return value:**

| Type | Description |
| --- | --- |
| [Ashmem](arkts-ipc-rpc-ashmem-c.md) | Returns the **Ashmem** object if it is created successfully; returns null otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.The Ashmem name passed is empty; 4.The Ashmem size passed is less than or equal to 0. |

**Examples**

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

<a id="create-1"></a>

## create

```TypeScript
static create(ashmem: Ashmem): Ashmem
```

Creates an **Ashmem** object by copying the file descriptor of an existing **Ashmem** object. The two **Ashmem** objects point to the same shared memory region.

**Since:** 9

<!--Device-Ashmem-static create(ashmem: Ashmem): Ashmem--><!--Device-Ashmem-static create(ashmem: Ashmem): Ashmem-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ashmem | [Ashmem](arkts-ipc-rpc-ashmem-c.md) | Yes | Existing **Ashmem** object. |

**Return value:**

| Type | Description |
| --- | --- |
| [Ashmem](arkts-ipc-rpc-ashmem-c.md) | **Ashmem** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The passed parameter is not an Ashmem object; 3.The ashmem instance for obtaining packaging is empty. |

**Examples**

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

## getAshmemSize

```TypeScript
getAshmemSize(): number
```

Obtains the memory size of this **Ashmem** object.

**Since:** 8

<!--Device-Ashmem-getAshmemSize(): int--><!--Device-Ashmem-getAshmemSize(): int-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | **Ashmem** size obtained. |

**Examples**

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

## mapReadonlyAshmem

```TypeScript
mapReadonlyAshmem(): void
```

Maps the shared file to the read-only virtual address space of the process.

**Since:** 9

<!--Device-Ashmem-mapReadonlyAshmem(): void--><!--Device-Ashmem-mapReadonlyAshmem(): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1900001](../errorcode-rpc.md#1900001-failed-to-call-mmap) | Failed to call mmap. |

**Examples**

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

## mapReadWriteAshmem

```TypeScript
mapReadWriteAshmem(): void
```

Maps the shared file to the readable and writable virtual address space of the process.

**Since:** 9

<!--Device-Ashmem-mapReadWriteAshmem(): void--><!--Device-Ashmem-mapReadWriteAshmem(): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1900001](../errorcode-rpc.md#1900001-failed-to-call-mmap) | Failed to call mmap. |

**Examples**

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

## mapTypedAshmem

```TypeScript
mapTypedAshmem(mapType: number): void
```

Creates the shared file mapping on the virtual address space of this process. The size of the mapping region is specified by this **Ashmem** object.

**Since:** 9

<!--Device-Ashmem-mapTypedAshmem(mapType: int): void--><!--Device-Ashmem-mapTypedAshmem(mapType: int): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mapType | number | Yes | Protection level of the memory region to which the shared file is mapped. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.The passed mapType exceeds the maximum protection level. |
| [1900001](../errorcode-rpc.md#1900001-failed-to-call-mmap) | Failed to call mmap. |

**Examples**

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

## readDataFromAshmem

```TypeScript
readDataFromAshmem(size: number, offset: number): ArrayBuffer
```

Reads data from the shared file associated with this **Ashmem** object.

> **NOTE:** 
> 
> Before writing an **Ashmem** object, you need to call
> [mapReadWriteAshmem](#mapreadwriteashmem) for mapping.

**Since:** 11

<!--Device-Ashmem-readDataFromAshmem(size: int, offset: int): ArrayBuffer--><!--Device-Ashmem-readDataFromAshmem(size: int, offset: int): ArrayBuffer-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | number | Yes | Size of the data to read, in bytes. |
| offset | number | Yes | Start position of the data to read in the memory region associated with this **Ashmem** object. |

**Return value:**

| Type | Description |
| --- | --- |
| ArrayBuffer | Data read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900004](../errorcode-rpc.md#1900004-failed-to-read-data-from-the-shared-memory) | Failed to read data from the shared memory. |

**Examples**

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

## setProtectionType

```TypeScript
setProtectionType(protectionType: number): void
```

Sets the protection level of the memory region to which the shared file is mapped.

**Since:** 9

<!--Device-Ashmem-setProtectionType(protectionType: int): void--><!--Device-Ashmem-setProtectionType(protectionType: int): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| protectionType | number | Yes | Protection type to set. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900002](../errorcode-rpc.md#1900002-failed-to-call-ioctl) | Failed to call ioctl. |

**Examples**

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

Deletes the mappings for the specified address range of this **Ashmem** object.

**Since:** 8

<!--Device-Ashmem-unmapAshmem(): void--><!--Device-Ashmem-unmapAshmem(): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Examples**

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

## writeDataToAshmem

```TypeScript
writeDataToAshmem(buf: ArrayBuffer, size: number, offset: number): void
```

Writes data to the shared file associated with this **Ashmem** object.

> **NOTE:** 
> 
> Before writing an **Ashmem** object, you need to call
> [mapReadWriteAshmem](#mapreadwriteashmem) for mapping.

**Since:** 11

<!--Device-Ashmem-writeDataToAshmem(buf: ArrayBuffer, size: int, offset: int): void--><!--Device-Ashmem-writeDataToAshmem(buf: ArrayBuffer, size: int, offset: int): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buf | ArrayBuffer | Yes | Data to write. |
| size | number | Yes | Size of the data to write, in bytes. |
| offset | number | Yes | Start position of the data to write in the memory region associated with this **Ashmem** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.Failed to obtain arrayBuffer information. |
| [1900003](../errorcode-rpc.md#1900003-failed-to-write-data-to-the-shared-memory) | Failed to write data to the shared memory. |

**Examples**

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

## createAshmem

```TypeScript
static createAshmem(name: string, size: number): Ashmem
```

Creates an **Ashmem** object with the specified name and size. This API is a static method.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** create()

<!--Device-Ashmem-static createAshmem(name: string, size: number): Ashmem--><!--Device-Ashmem-static createAshmem(name: string, size: number): Ashmem-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the **Ashmem** object to create. |
| size | number | Yes | Size (in bytes) of the **Ashmem** object to create. |

**Return value:**

| Type | Description |
| --- | --- |
| [Ashmem](arkts-ipc-rpc-ashmem-c.md) | Returns the **Ashmem** object if it is created successfully; returns null otherwise. |

**Examples**

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

Creates an **Ashmem** object by copying the file descriptor of an existing **Ashmem** object. The two **Ashmem** objects point to the same shared memory region.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** create()

<!--Device-Ashmem-static createAshmemFromExisting(ashmem: Ashmem): Ashmem--><!--Device-Ashmem-static createAshmemFromExisting(ashmem: Ashmem): Ashmem-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ashmem | [Ashmem](arkts-ipc-rpc-ashmem-c.md) | Yes | Existing **Ashmem** object. |

**Return value:**

| Type | Description |
| --- | --- |
| [Ashmem](arkts-ipc-rpc-ashmem-c.md) | **Ashmem** object created. |

**Examples**

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

## mapAshmem

```TypeScript
mapAshmem(mapType: number): boolean
```

Creates the shared file mapping on the virtual address space of this process. The size of the mapping region is specified by this **Ashmem** object.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [mapTypedAshmem](#maptypedashmem)(mapType: number)

<!--Device-Ashmem-mapAshmem(mapType: number): boolean--><!--Device-Ashmem-mapAshmem(mapType: number): boolean-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mapType | number | Yes | Protection level of the memory region to which the shared file is mapped. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the mapping is created; returns **false** otherwise. |

**Examples**

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

Maps the shared file to the readable and writable virtual address space of the process.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [mapReadWriteAshmem](#mapreadwriteashmem)()

<!--Device-Ashmem-mapReadAndWriteAshmem(): boolean--><!--Device-Ashmem-mapReadAndWriteAshmem(): boolean-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the mapping is created; returns **false** otherwise. |

**Examples**

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

Maps the shared file to the read-only virtual address space of the process.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [mapReadonlyAshmem](#mapreadonlyashmem)()

<!--Device-Ashmem-mapReadOnlyAshmem(): boolean--><!--Device-Ashmem-mapReadOnlyAshmem(): boolean-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the mapping is created; returns **false** otherwise. |

**Examples**

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

## readAshmem

```TypeScript
readAshmem(size: number, offset: number): number[]
```

Reads data from the shared file associated with this **Ashmem** object.

> **NOTE:** 
> 
> - Before writing an **Ashmem** object, you need to call [mapReadWriteAshmem](#mapreadwriteashmem) for mapping.

**Since:** 9

**Deprecated since:** 11

**Substitutes:** [readDataFromAshmem](#readdatafromashmem)(size: number, offset: number)

<!--Device-Ashmem-readAshmem(size: number, offset: number): number[]--><!--Device-Ashmem-readAshmem(size: number, offset: number): number[]-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | number | Yes | Size of the data to read. |
| offset | number | Yes | Start position of the data to read in the memory region associated with this **Ashmem** object. |

**Return value:**

| Type | Description |
| --- | --- |
| number[] | Data read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match. |
| [1900004](../errorcode-rpc.md#1900004-failed-to-read-data-from-the-shared-memory) | Failed to read data from the shared memory. |

**Examples**

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

## readFromAshmem

```TypeScript
readFromAshmem(size: number, offset: number): number[]
```

Reads data from the shared file associated with this **Ashmem** object.

> **NOTE:** 
> 
> - Before writing an **Ashmem** object, you need to call [mapReadWriteAshmem](#mapreadwriteashmem) for mapping.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [readDataFromAshmem](#readdatafromashmem)(size: number, offset: number)

<!--Device-Ashmem-readFromAshmem(size: number, offset: number): number[]--><!--Device-Ashmem-readFromAshmem(size: number, offset: number): number[]-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | number | Yes | Size of the data to read. |
| offset | number | Yes | Start position of the data to read in the memory region associated with this **Ashmem** object. |

**Return value:**

| Type | Description |
| --- | --- |
| number[] | Data read. |

**Examples**

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

Sets the protection level of the memory region to which the shared file is mapped.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [setProtectionType](#setprotectiontype)(protectionType: number)

<!--Device-Ashmem-setProtection(protectionType: number): boolean--><!--Device-Ashmem-setProtection(protectionType: number): boolean-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| protectionType | number | Yes | Protection type to set. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise. |

**Examples**

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

## writeAshmem

```TypeScript
writeAshmem(buf: number[], size: number, offset: number): void
```

Writes data to the shared file associated with this **Ashmem** object.

> **NOTE:** 
> 
> - Before writing an **Ashmem** object, you need to call [mapReadWriteAshmem](#mapreadwriteashmem) for mapping.

**Since:** 9

**Deprecated since:** 11

**Substitutes:** [writeDataToAshmem](#writedatatoashmem)(buf: ArrayBuffer, size: number, offset: number)

<!--Device-Ashmem-writeAshmem(buf: number[], size: number, offset: number): void--><!--Device-Ashmem-writeAshmem(buf: number[], size: number, offset: number): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buf | number[] | Yes | Data to write. |
| size | number | Yes | Size of the data to write, in bytes. |
| offset | number | Yes | Start position of the data to write in the memory region associated with this **Ashmem** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.The element does not exist in the array. |
| [1900003](../errorcode-rpc.md#1900003-failed-to-write-data-to-the-shared-memory) | Failed to write data to the shared memory. |

**Examples**

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

## writeToAshmem

```TypeScript
writeToAshmem(buf: number[], size: number, offset: number): boolean
```

Writes data to the shared file associated with this **Ashmem** object.

> **NOTE:** 
> 
> - Before writing an **Ashmem** object, you need to call [mapReadWriteAshmem](#mapreadwriteashmem) for mapping.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [writeDataToAshmem](#writedatatoashmem)(buf: ArrayBuffer, size: number, offset: number)

<!--Device-Ashmem-writeToAshmem(buf: number[], size: number, offset: number): boolean--><!--Device-Ashmem-writeToAshmem(buf: number[], size: number, offset: number): boolean-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buf | number[] | Yes | Data to write. |
| size | number | Yes | Size of the data to write, in bytes. |
| offset | number | Yes | Start position of the data to write in the memory region associated with this **Ashmem** object. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the data is written successfully; returns **false** otherwise. |

**Examples**

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

Mapped memory protection type, indicating that the mapped memory is executable.

**Type:** number

**Default:** 4

**Since:** 8

<!--Device-Ashmem-static readonly PROT_EXEC: number--><!--Device-Ashmem-static readonly PROT_EXEC: number-End-->

**System capability:** SystemCapability.Communication.IPC.Core

## PROT_NONE

```TypeScript
static readonly PROT_NONE: number
```

Mapped memory protection type, indicating that the mapped memory cannot be accessed.

**Type:** number

**Default:** 0

**Since:** 8

<!--Device-Ashmem-static readonly PROT_NONE: number--><!--Device-Ashmem-static readonly PROT_NONE: number-End-->

**System capability:** SystemCapability.Communication.IPC.Core

## PROT_READ

```TypeScript
static readonly PROT_READ: number
```

Mapped memory protection type, indicating that the mapped memory is readable.

**Type:** number

**Default:** 1

**Since:** 8

<!--Device-Ashmem-static readonly PROT_READ: number--><!--Device-Ashmem-static readonly PROT_READ: number-End-->

**System capability:** SystemCapability.Communication.IPC.Core

## PROT_WRITE

```TypeScript
static readonly PROT_WRITE: number
```

Mapped memory protection type, indicating that the mapped memory is writable.

**Type:** number

**Default:** 2

**Since:** 8

<!--Device-Ashmem-static readonly PROT_WRITE: number--><!--Device-Ashmem-static readonly PROT_WRITE: number-End-->

**System capability:** SystemCapability.Communication.IPC.Core
