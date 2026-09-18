# purgeable_memory.h

## Overview

Provides APIs for managing the purgeable memory. <br>For example, you can create a purgeable memory, start or end the memory reading/writing, and rebuild the memory. <br>Link to the **libpurgeable_memory_ndk.z.so** file when you use the API.

**Library**: libpurgeable_memory_ndk.z.so

**System capability**: SystemCapability.Kernel.Memory

**Since**: 10

**Related module**: [memory](capi-memory.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [PurgMem](capi-memory-purgmem.md) | OH_PurgeableMemory | Defines a purgeable memory struct. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef bool (\*OH_PurgeableMemory_ModifyFunc)(void *, size_t, void *)](#oh_purgeablememory_modifyfunc) | OH_PurgeableMemory_ModifyFunc | function pointer, it points to a function which is used to build content of a PurgMem obj.<br> * |
| [OH_PurgeableMemory *OH_PurgeableMemory_Create(size_t size, OH_PurgeableMemory_ModifyFunc func, void *funcPara)](#oh_purgeablememory_create) | - | create a PurgMem obj.<br> * |
| [bool OH_PurgeableMemory_Destroy(OH_PurgeableMemory *purgObj)](#oh_purgeablememory_destroy) | - | destroy a PurgMem obj.<br> * |
| [bool OH_PurgeableMemory_BeginRead(OH_PurgeableMemory *purgObj)](#oh_purgeablememory_beginread) | - | begin read a PurgMem obj.<br> * |
| [void OH_PurgeableMemory_EndRead(OH_PurgeableMemory *purgObj)](#oh_purgeablememory_endread) | - | end read a PurgMem obj.<br> * |
| [bool OH_PurgeableMemory_BeginWrite(OH_PurgeableMemory *purgObj)](#oh_purgeablememory_beginwrite) | - | begin write a PurgMem obj.<br> * |
| [void OH_PurgeableMemory_EndWrite(OH_PurgeableMemory *purgObj)](#oh_purgeablememory_endwrite) | - | end write a PurgMem obj.<br> * |
| [void *OH_PurgeableMemory_GetContent(OH_PurgeableMemory *purgObj)](#oh_purgeablememory_getcontent) | - | get content ptr of a PurgMem obj.<br> * |
| [size_t OH_PurgeableMemory_ContentSize(OH_PurgeableMemory *purgObj)](#oh_purgeablememory_contentsize) | - | get content size of a PurgMem obj.<br> * |
| [bool OH_PurgeableMemory_AppendModify(OH_PurgeableMemory *purgObj, OH_PurgeableMemory_ModifyFunc func, void *funcPara)](#oh_purgeablememory_appendmodify) | - | append a modify to a PurgMem obj.<br> * |

### Variable

| Name | Description |
| -- | -- |
| bool (*OH_PurgeableMemory_ModifyFunc)(void *, size_t, void *) | function pointer, it points to a function which is used to build content of a PurgMem obj.<br> *<br>**Since**: 10 |

## Function description

### OH_PurgeableMemory_ModifyFunc()

```c
typedef bool (*OH_PurgeableMemory_ModifyFunc)(void *, size_t, void *)
```

**Description**

function pointer, it points to a function which is used to build content of a PurgMem obj.<br> *

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| void \* | *: data ptr, points to start address of a PurgMem obj's content. |
| size_t | Data size of the content. |
| void \* | *: other private parameters. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | build content result, true means success, while false is fail. |

### OH_PurgeableMemory_Create()

```c
OH_PurgeableMemory *OH_PurgeableMemory_Create(size_t size, OH_PurgeableMemory_ModifyFunc func, void *funcPara)
```

**Description**

create a PurgMem obj.<br> *

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| size_t size | Data size of the content of a purgeable memory object. |
| [OH_PurgeableMemory_ModifyFunc](capi-purgeable-memory-h.md#oh_purgeablememory_modifyfunc) func | Function used to restore data when the content of a purgeable memory object is cleared. |
| void *funcPara | Pointer to the parameter used by func. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_PurgeableMemory *](capi-memory-purgmem.md) | a PurgMem obj. |

### OH_PurgeableMemory_Destroy()

```c
bool OH_PurgeableMemory_Destroy(OH_PurgeableMemory *purgObj)
```

**Description**

destroy a PurgMem obj.<br> *

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PurgeableMemory](capi-memory-purgmem.md) *purgObj | Pointer to the purgeable memory object to be destroyed. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | true is success, while false is fail. return true if purgObj is NULL.       <br>If return true, purgObj will be set to NULL to avoid Use-After-Free. |

### OH_PurgeableMemory_BeginRead()

```c
bool OH_PurgeableMemory_BeginRead(OH_PurgeableMemory *purgObj)
```

**Description**

begin read a PurgMem obj.<br> *

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PurgeableMemory](capi-memory-purgmem.md) *purgObj | Pointer to the purgeable memory object. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | return true if purgObj's content is present.      If content is purged(no present), system will recover its data,      return false if content is purged and recovered failed.      While return true if content recover success.      OS cannot reclaim the memory of purgObj's content when this      function return true, until PurgMemEndRead() is called. |

### OH_PurgeableMemory_EndRead()

```c
void OH_PurgeableMemory_EndRead(OH_PurgeableMemory *purgObj)
```

**Description**

end read a PurgMem obj.<br> *

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PurgeableMemory](capi-memory-purgmem.md) *purgObj | Pointer to the purgeable memory object. When this function ends, the OS may reclaim the memory of the content of the purgeable memory object later. |

### OH_PurgeableMemory_BeginWrite()

```c
bool OH_PurgeableMemory_BeginWrite(OH_PurgeableMemory *purgObj)
```

**Description**

begin write a PurgMem obj.<br> *

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PurgeableMemory](capi-memory-purgmem.md) *purgObj | Pointer to the purgeable memory object. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | return true if purgObj's content is present.      if content is purged(no present), system will recover its data,      return false if content is purged and recovered failed.      While return true if content is successfully recovered.      OS cannot reclaim the memory of purgObj's content when this      function return true, until PurgMemEndWrite() is called. |

### OH_PurgeableMemory_EndWrite()

```c
void OH_PurgeableMemory_EndWrite(OH_PurgeableMemory *purgObj)
```

**Description**

end write a PurgMem obj.<br> *

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PurgeableMemory](capi-memory-purgmem.md) *purgObj | Pointer to the purgeable memory object. When this function ends, the OS may reclaim the memory of the content of the purgeable memory object later. |

### OH_PurgeableMemory_GetContent()

```c
void *OH_PurgeableMemory_GetContent(OH_PurgeableMemory *purgObj)
```

**Description**

get content ptr of a PurgMem obj.<br> *

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PurgeableMemory](capi-memory-purgmem.md) *purgObj | Pointer to the purgeable memory object. |

**Returns**:

| Type | Description |
| -- | -- |
| void * | return start address of a PurgMem obj's content.      <br>Return NULL if purgObj is NULL.      <br>This function should be protect by PurgMemBeginRead()/PurgMemEndRead()      or PurgMemBeginWrite()/PurgMemEndWrite() |

### OH_PurgeableMemory_ContentSize()

```c
size_t OH_PurgeableMemory_ContentSize(OH_PurgeableMemory *purgObj)
```

**Description**

get content size of a PurgMem obj.<br> *

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PurgeableMemory](capi-memory-purgmem.md) *purgObj | Pointer to the purgeable memory object. |

**Returns**:

| Type | Description |
| -- | -- |
| size_t | return content size of purgObj.      Return 0 if purgObj is NULL. |

### OH_PurgeableMemory_AppendModify()

```c
bool OH_PurgeableMemory_AppendModify(OH_PurgeableMemory *purgObj, OH_PurgeableMemory_ModifyFunc func, void *funcPara)
```

**Description**

append a modify to a PurgMem obj.<br> *

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PurgeableMemory](capi-memory-purgmem.md) *purgObj | Pointer to the purgeable memory object. |
| [OH_PurgeableMemory_ModifyFunc](capi-purgeable-memory-h.md#oh_purgeablememory_modifyfunc) func | Function used to modify the content of a purgeable memory object. |
| void *funcPara | Pointer to the parameter used by func. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | append result, true is success, while false is fail. |


