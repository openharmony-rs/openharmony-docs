# tee_sharemem_ops.h

## Overview

Provides  APIs for developers to apply for shared memory.

**Library**: NA

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [void *tee_alloc_sharemem_aux(const struct tee_uuid *uuid, uint32_t size)](#tee_alloc_sharemem_aux) | Alloc shared memory in TEE. |
| [void *tee_alloc_coherent_sharemem_aux(const struct tee_uuid *uuid, uint32_t size)](#tee_alloc_coherent_sharemem_aux) | Alloc continuous shared memory in TEE. |
| [uint32_t tee_free_sharemem(void *addr, uint32_t size)](#tee_free_sharemem) | Free the shared memory in TEE. |
| [int32_t copy_from_sharemem(uint32_t src_task, uint64_t src, uint32_t src_size, uintptr_t dst, uint32_t dst_size)](#copy_from_sharemem) | Copy shared memory from source task. |
| [int32_t copy_to_sharemem(uintptr_t src, uint32_t src_size, uint32_t dst_task, uint64_t dst, uint32_t dst_size)](#copy_to_sharemem) | Copy shared memory to destination task. |

## Function description

### tee_alloc_sharemem_aux()

```c
void *tee_alloc_sharemem_aux(const struct tee_uuid *uuid, uint32_t size)
```

**Description**

Alloc shared memory in TEE.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const struct tee_uuid *uuid | Indicates the UUID of TA. |
| uint32_t size | Indicates the size of the requested shared memory. |

**Returns**:

| Type | Description |
| -- | -- |
| void * | Returns a pointer to the newly allocated space if the operation is successful.          Returns a <b>NULL</b> pointer if the allocation fails. |

### tee_alloc_coherent_sharemem_aux()

```c
void *tee_alloc_coherent_sharemem_aux(const struct tee_uuid *uuid, uint32_t size)
```

**Description**

Alloc continuous shared memory in TEE.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const struct tee_uuid *uuid | Indicates the UUID of TA. |
| uint32_t size | Indicates the size of the requested shared memory. |

**Returns**:

| Type | Description |
| -- | -- |
| void * | Returns a pointer to the newly allocated space if the operation is successful.          Returns a <b>NULL</b> pointer if the allocation fails. |

### tee_free_sharemem()

```c
uint32_t tee_free_sharemem(void *addr, uint32_t size)
```

**Description**

Free the shared memory in TEE.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| void *addr | Indicates the shared memory address that will be freed. |
| uint32_t size | Indicates the size of the shared memory. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | Returns <b>0</b> if the operation is successful.          Returns others if the operation is failed. |

### copy_from_sharemem()

```c
int32_t copy_from_sharemem(uint32_t src_task, uint64_t src, uint32_t src_size, uintptr_t dst, uint32_t dst_size)
```

**Description**

Copy shared memory from source task.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t src_task | Indicates the pid of the source task. |
| uint64_t src | Indicates the address of the source buffer. |
| uint32_t src_size | Indicates the size of the source buffer. |
| uintptr_t dst | Indicates the address of the destination buffer. |
| uint32_t dst_size | Indicates the size of the destination buffer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns <b>0</b> if the operation is successful.          Returns <b>-1</b> if the operation is failed. |

### copy_to_sharemem()

```c
int32_t copy_to_sharemem(uintptr_t src, uint32_t src_size, uint32_t dst_task, uint64_t dst, uint32_t dst_size)
```

**Description**

Copy shared memory to destination task.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uintptr_t src | Indicates the address of the source buffer. |
| uint32_t src_size | Indicates the size of the source buffer. |
| uint32_t dst_task | Indicates the pid of the destination task. |
| uint64_t dst | Indicates the address of the destination buffer. |
| uint32_t dst_size | Indicates the size of the destination buffer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns <b>0</b> if the operation is successful.          Returns <b>-1</b> if the operation is failed. |


