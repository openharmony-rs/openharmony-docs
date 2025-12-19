# purgeable_memory.h

<!--Kit: Kernel Enhance Kit-->
<!--Subsystem: Kernel-->
<!--Owner: @sagittary-->
<!--Designer: @OH-wxy-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @fang-jinxu-->

## Overview

Provides APIs for managing the purgeable memory.<br>For example, you can create a purgeable memory, start or end the memory reading/writing, and rebuild the memory.<br>Link to the **libpurgeable_memory_ndk.z.so** file when you use the API.

**File to include**: <purgeable_memory/purgeable_memory.h>

**Library**: libpurgeable_memory_ndk.z.so

**System capability**: SystemCapability.Kernel.Memory

**Since**: 10

**Related module**: [memory](capi-memory.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [PurgMem](capi-memory-purgmem.md) | OH_PurgeableMemory | Defines a purgeable memory struct.|

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [typedef bool (\*OH_PurgeableMemory_ModifyFunc)(void *, size_t, void *)](#oh_purgeablememory_modifyfunc) | OH_PurgeableMemory_ModifyFunc | Pointer to a function used to construct the content of a purgeable memory object.|
| [OH_PurgeableMemory *OH_PurgeableMemory_Create(size_t size, OH_PurgeableMemory_ModifyFunc func, void *funcPara)](#oh_purgeablememory_create) | - | Creates a [PurgMem](capi-memory-purgmem.md) object.|
| [bool OH_PurgeableMemory_Destroy(OH_PurgeableMemory *purgObj)](#oh_purgeablememory_destroy) | - | Destroys a [PurgMem](capi-memory-purgmem.md) object.|
| [bool OH_PurgeableMemory_BeginRead(OH_PurgeableMemory *purgObj)](#oh_purgeablememory_beginread) | - | Starts reading a [PurgMem](capi-memory-purgmem.md) object.|
| [void OH_PurgeableMemory_EndRead(OH_PurgeableMemory *purgObj)](#oh_purgeablememory_endread) | - | Stops reading a [PurgMem](capi-memory-purgmem.md) object.|
| [bool OH_PurgeableMemory_BeginWrite(OH_PurgeableMemory *purgObj)](#oh_purgeablememory_beginwrite) | - | Starts writing a [PurgMem](capi-memory-purgmem.md) object.|
| [void OH_PurgeableMemory_EndWrite(OH_PurgeableMemory *purgObj)](#oh_purgeablememory_endwrite) | - | Stops writing a [PurgMem](capi-memory-purgmem.md) object.|
| [void *OH_PurgeableMemory_GetContent(OH_PurgeableMemory *purgObj)](#oh_purgeablememory_getcontent) | - | Obtains the content of a [PurgMem](capi-memory-purgmem.md) object.|
| [size_t OH_PurgeableMemory_ContentSize(OH_PurgeableMemory *purgObj)](#oh_purgeablememory_contentsize) | - | Obtains the content size of a [PurgMem](capi-memory-purgmem.md) object.|
| [bool OH_PurgeableMemory_AppendModify(OH_PurgeableMemory *purgObj, OH_PurgeableMemory_ModifyFunc func, void *funcPara)](#oh_purgeablememory_appendmodify) | - | Appends the modification to a [PurgMem](capi-memory-purgmem.md) object.|

## Function Description

### OH_PurgeableMemory_ModifyFunc()

```c
typedef bool (*OH_PurgeableMemory_ModifyFunc)(void *, size_t, void *)
```

**Description**

Pointer to a function used to construct the content of a purgeable memory object.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| void * | Pointer to the start address of the content of a purgeable memory object.|
| size_t | Data size of the content.|
| void * | Pointer to other private parameters.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Whether the content is successfully constructed. The value **true** indicates that the operation is successful, and **false** indicates the opposite.|

### OH_PurgeableMemory_Create()

```c
OH_PurgeableMemory *OH_PurgeableMemory_Create(size_t size, OH_PurgeableMemory_ModifyFunc func, void *funcPara)
```

**Description**

Creates a [PurgMem](capi-memory-purgmem.md) object.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| size_t size| Data size of the content of a purgeable memory object.|
| [OH_PurgeableMemory_ModifyFunc](capi-purgeable-memory-h.md#oh_purgeablememory_modifyfunc) func | Function used to restore data when the content of a purgeable memory object is cleared.|
| void *funcPara | Pointer to the parameter used by @func.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_PurgeableMemory *](capi-memory-purgmem.md) | Returns the purgeable memory object created.|

### OH_PurgeableMemory_Destroy()

```c
bool OH_PurgeableMemory_Destroy(OH_PurgeableMemory *purgObj)
```

**Description**

Destroys a [PurgMem](capi-memory-purgmem.md) object.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [OH_PurgeableMemory](capi-memory-purgmem.md) *purgObj | Pointer to the purgeable memory object to be destroyed.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Whether the destruction is successful. The value **true** indicates that the destruction is successful, and **false** indicates the opposite. Returns **true** if the purgeable memory object is **NULL**.<br> Returns **true** if the destruction is successful. The purgeable memory object is set to **NULL** to avoid Use-After-Free.|

### OH_PurgeableMemory_BeginRead()

```c
bool OH_PurgeableMemory_BeginRead(OH_PurgeableMemory *purgObj)
```

**Description**

Starts reading a [PurgMem](capi-memory-purgmem.md) object.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [OH_PurgeableMemory](capi-memory-purgmem.md) *purgObj | Pointer to the purgeable memory object.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Whether the reading is successful. Returns **true** if the content of the purgeable memory object exists.<br>          If the content is cleared (that is, the content does not exist), the system attempts to restore the data.<br>          Returns **false** if the restore fails.<br>          Returns **true** if the restore is successful.<br> When this function returns **true**, the system cannot reclaim the memory of the content of the purgeable memory object until [OH_PurgeableMemory_EndRead()](#oh_purgeablememory_endread) is called.|

### OH_PurgeableMemory_EndRead()

```c
void OH_PurgeableMemory_EndRead(OH_PurgeableMemory *purgObj)
```

**Description**

Stops reading a [PurgMem](capi-memory-purgmem.md) object.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [OH_PurgeableMemory](capi-memory-purgmem.md) *purgObj | Pointer to the purgeable memory object. When this function ends, the OS may reclaim the memory of the content of the purgeable memory object later.|

### OH_PurgeableMemory_BeginWrite()

```c
bool OH_PurgeableMemory_BeginWrite(OH_PurgeableMemory *purgObj)
```

**Description**

Starts writing a [PurgMem](capi-memory-purgmem.md) object.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [OH_PurgeableMemory](capi-memory-purgmem.md) *purgObj | Pointer to the purgeable memory object.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Whether the content of the purgeable memory object exists. Returns **true** if the content exists.<br>          If the content is cleared, the system restores its data.<br>          Returns **false** if the content is cleared and the restore fails.<br>          Returns **true** if the restore is successful.<br> When this function returns **true**, the OS cannot reclaim the memory of the content of the purgeable memory object until [OH_PurgeableMemory_EndWrite()](#oh_purgeablememory_endwrite) is called.|

### OH_PurgeableMemory_EndWrite()

```c
void OH_PurgeableMemory_EndWrite(OH_PurgeableMemory *purgObj)
```

**Description**

Stops writing a [PurgMem](capi-memory-purgmem.md) object.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [OH_PurgeableMemory](capi-memory-purgmem.md) *purgObj | Pointer to the purgeable memory object. When this function ends, the OS may reclaim the memory of the content of the purgeable memory object later.|

### OH_PurgeableMemory_GetContent()

```c
void *OH_PurgeableMemory_GetContent(OH_PurgeableMemory *purgObj)
```

**Description**

Obtains the content of a [PurgMem](capi-memory-purgmem.md) object.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [OH_PurgeableMemory](capi-memory-purgmem.md) *purgObj | Pointer to the purgeable memory object.|

**Returns**

| Type| Description|
| -- | -- |
| void * | Returns the start address of the content of the purgeable memory object.<br>          Returns **NULL** if the purgeable memory object is **NULL**.<br> This function should be protected by [OH_PurgeableMemory_BeginRead()](#oh_purgeablememory_beginread)/[OH_PurgeableMemory_EndRead()](#oh_purgeablememory_endread) or [OH_PurgeableMemory_BeginWrite()](#oh_purgeablememory_beginwrite)/[OH_PurgeableMemory_EndWrite()](#oh_purgeablememory_endwrite).|

### OH_PurgeableMemory_ContentSize()

```c
size_t OH_PurgeableMemory_ContentSize(OH_PurgeableMemory *purgObj)
```

**Description**

Obtains the content size of a [PurgMem](capi-memory-purgmem.md) object.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [OH_PurgeableMemory](capi-memory-purgmem.md) *purgObj | Pointer to the purgeable memory object.|

**Returns**

| Type| Description|
| -- | -- |
| size_t | Returns the content size of the purgeable memory object obtained.<br>          Returns **0** if the purgeable memory object is **NULL**.|

### OH_PurgeableMemory_AppendModify()

```c
bool OH_PurgeableMemory_AppendModify(OH_PurgeableMemory *purgObj, OH_PurgeableMemory_ModifyFunc func, void *funcPara)
```

**Description**

Appends the modification to a [PurgMem](capi-memory-purgmem.md) object.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [OH_PurgeableMemory](capi-memory-purgmem.md) *purgObj | Pointer to the purgeable memory object.|
| [OH_PurgeableMemory_ModifyFunc](#oh_purgeablememory_modifyfunc) func | Function used to modify the content of a purgeable memory object.|
| void *funcPara | Pointer to the parameter used by @func.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns the operation result. The value **true** indicates that the operation is successful, and **false** indicates the opposite.|
