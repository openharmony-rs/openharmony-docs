# tee_mem_mgmt_api.h

## Overview

Provides APIs for memory management.

**Library**: NA

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

## Summary

### Enum

| Name | Description |
| -- | -- |
| [MALLOC_HINT](#malloc_hint) | Defines the enumeration values for memory allocation hints. |

### Macro

| Name | Description |
| -- | -- |
| ZERO_SIZE_PTR       ((void *)16) | Represents a zero-size pointer.<br>**Since**: 20 |
| zero_or_null_ptr(x) ((unsigned long)(x) <= (unsigned long)ZERO_SIZE_PTR) | Checks if the pointer is either zero-size or NULL.<br>**Since**: 20 |
| TEE_MALLOC_FILL_ZERO 0x00000000 | Allocated memory filled with zeros.<br>**Since**: 20 |
| TEE_MALLOC_NO_FILL   0x00000001 | Allocated memory with no filling.<br>**Since**: 20 |
| TEE_MALLOC_NO_SHARE  0x00000002 | Allocated memory that is not shareable.<br>**Since**: 20 |
| TEE_MEMORY_ACCESS_READ      0x00000001 | Grants read access to memory.<br>**Since**: 20 |
| TEE_MEMORY_ACCESS_WRITE     0x00000002 | Grants write access to memory.<br>**Since**: 20 |
| TEE_MEMORY_ACCESS_ANY_OWNER 0x00000004 | Grants access to memory by any owner.<br>**Since**: 20 |

### Function

| Name | Description |
| -- | -- |
| [void TEE_MemFill(void *buffer, uint8_t x, size_t size)](#tee_memfill) | Fills <b>x</b> into the first <b>size</b> bytes of the buffer. |
| [void TEE_MemMove(void *dest, const void *src, size_t size)](#tee_memmove) | Copies bytes. |
| [void *TEE_Malloc(size_t size, uint32_t hint)](#tee_malloc) | Allocates space of the specified size for an object. |
| [void TEE_Free(void *buffer)](#tee_free) | Releases the memory allocated by <b>TEE_Malloc</b>.<br> If the buffer is a <b>NULL</b> pointer, <b>TEE_Free</b> does nothing. The buffer to be released must have been allocated by <b>TEE_Malloc</b> or <b>TEE_Realloc</b> and cannot be released repeatedly. Otherwise, unexpected result may be caused. |
| [void *TEE_Realloc(void *buffer, size_t new_size)](#tee_realloc) | Reallocates memory.<br> If <b>new_size</b> is greater than the old size, the content of the original memory does not change and the space in excess of the old size contains unspecified content. If the new size of the memory object requires movement of the object, the space for the previous instantiation of the object is deallocated. If the space cannot be allocated, the original object remains allocated and this function returns a <b>NULL</b> pointer. If the buffer is <b>NULL</b>, this function is equivalent to <b>TEE_Malloc</b>. |
| [int32_t TEE_MemCompare(const void *buffer1, const void *buffer2, size_t size)](#tee_memcompare) | Compares memory content from the beginning. |
| [TEE_Result TEE_CheckMemoryAccessRights(uint32_t accessFlags, const void *buffer, size_t size)](#tee_checkmemoryaccessrights) | Checks whether this TA has the requested permissions to access a buffer. |
| [void TEE_SetInstanceData(void *instanceData)](#tee_setinstancedata) | Sets the TA instance data pointer. |
| [void *TEE_GetInstanceData(void)](#tee_getinstancedata) | Obtains the instance data pointer set by the TA using <b>TEE_SetInstanceData</b>. |

## Enum type description

### MALLOC_HINT

```c
enum MALLOC_HINT
```

**Description**

Defines the enumeration values for memory allocation hints.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

| Enum item | Description |
| -- | -- |
| ZERO           = 0 | Uninitialized buffer. |
| NOT_ZERO       = 1 | Non-zero initialized buffer. |
| ALIGN_004      = 0x80000002 | 4-byte aligned buffer. |
| ALIGN_008      = 0x80000003 | 8-byte aligned buffer. |
| ALIGN_016      = 0x80000004 | 16-byte aligned buffer. |
| ALIGN_032      = 0x80000005 | 32-byte aligned buffer. |
| ALIGN_064      = 0x80000006 | 64-byte aligned buffer. |
| ALIGN_128      = 0x80000007 | 128-byte aligned buffer. |
| ALIGN_256      = 0x80000008 | 256-byte aligned buffer. |
| ALIGN_004_ZERO = 0x80000012 | 4-byte aligned buffer initialized to zero. |
| ALIGN_008_ZERO = 0x80000013 | 8-byte aligned buffer initialized to zero. |
| ALIGN_016_ZERO = 0x80000014 | 16-byte aligned buffer initialized to zero. |
| ALIGN_032_ZERO = 0x80000015 | 32-byte aligned buffer initialized to zero. |
| ALIGN_064_ZERO = 0x80000016 | 64-byte aligned buffer initialized to zero. |
| ALIGN_128_ZERO = 0x80000017 | 128-byte aligned buffer initialized to zero. |
| ALIGN_256_ZERO = 0x80000018 | 256-byte aligned buffer initialized to zero. |


## Function description

### TEE_MemFill()

```c
void TEE_MemFill(void *buffer, uint8_t x, size_t size)
```

**Description**

Fills <b>x</b> into the first <b>size</b> bytes of the buffer.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| void *buffer | Indicates the pointer to the buffer. |
| uint8_t x | Indicates the value to fill. |
| size_t size | Indicates the number of bytes to fill. |

### TEE_MemMove()

```c
void TEE_MemMove(void *dest, const void *src, size_t size)
```

**Description**

Copies bytes.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| void *dest | Indicates the pointer to the buffer that holds the bytes copied. |
| const void *src | Indicates the pointer to the buffer that holds the bytes to copy. |
| size_t size | Indicates the number of bytes to copy. |

### TEE_Malloc()

```c
void *TEE_Malloc(size_t size, uint32_t hint)
```

**Description**

Allocates space of the specified size for an object.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| size_t size | Indicates the size of the memory to be allocated. |
| uint32_t hint | Indicates a hint to the allocator. The value <b>0</b> indicates that the memory block returned is filled with "\0". |

**Returns**:

| Type | Description |
| -- | -- |
| void * | Returns a pointer to the newly allocated space if the operation is successful. |

### TEE_Free()

```c
void TEE_Free(void *buffer)
```

**Description**

Releases the memory allocated by <b>TEE_Malloc</b>.<br> If the buffer is a <b>NULL</b> pointer, <b>TEE_Free</b> does nothing. The buffer to be released must have been allocated by <b>TEE_Malloc</b> or <b>TEE_Realloc</b> and cannot be released repeatedly. Otherwise, unexpected result may be caused.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| void *buffer | Indicates the pointer to the memory to release. |

### TEE_Realloc()

```c
void *TEE_Realloc(void *buffer, size_t new_size)
```

**Description**

Reallocates memory.<br> If <b>new_size</b> is greater than the old size, the content of the original memory does not change and the space in excess of the old size contains unspecified content. If the new size of the memory object requires movement of the object, the space for the previous instantiation of the object is deallocated. If the space cannot be allocated, the original object remains allocated and this function returns a <b>NULL</b> pointer. If the buffer is <b>NULL</b>, this function is equivalent to <b>TEE_Malloc</b>.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| void *buffer | Indicates the pointer to the memory to reallocate. |
| size_t new_size | Indicates the new size required. |

**Returns**:

| Type | Description |
| -- | -- |
| void * | Returns a pointer to the allocated memory if the operation is successful. |

### TEE_MemCompare()

```c
int32_t TEE_MemCompare(const void *buffer1, const void *buffer2, size_t size)
```

**Description**

Compares memory content from the beginning.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const void *buffer1 | Indicates the pointer to the first buffer. |
| const void *buffer2 | Indicates the pointer to the second buffer. |
| size_t size | Indicates the number of the bytes to compare. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns <b>–1</b> if buffer1 < buffer2. |

### TEE_CheckMemoryAccessRights()

```c
TEE_Result TEE_CheckMemoryAccessRights(uint32_t accessFlags, const void *buffer, size_t size)
```

**Description**

Checks whether this TA has the requested permissions to access a buffer.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t accessFlags | Indicates the access permissions to check. |
| const void *buffer | Indicates the pointer to the target buffer. |
| size_t size | Indicates the size of the buffer to check. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the TA has the requested permissions. |

### TEE_SetInstanceData()

```c
void TEE_SetInstanceData(void *instanceData)
```

**Description**

Sets the TA instance data pointer.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| void *instanceData | Indicates the pointer to the global TA instance data. |

### TEE_GetInstanceData()

```c
void *TEE_GetInstanceData(void)
```

**Description**

Obtains the instance data pointer set by the TA using <b>TEE_SetInstanceData</b>.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Returns**:

| Type | Description |
| -- | -- |
| void * | Returns the pointer to the instance data set by <b>TEE_SetInstanceData</b> |


