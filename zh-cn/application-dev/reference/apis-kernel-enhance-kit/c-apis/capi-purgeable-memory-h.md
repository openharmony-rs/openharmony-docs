# purgeable_memory.h

## 概述

提供可丢弃内存的内存管理功能。<br>提供的功能包括创建、开始读取、结束读取、开始写入、结束写入、重建等。<br>使用时需要链接libpurgeable_memory_ndk.z.so。

**库：** libpurgeable_memory_ndk.z.so

**系统能力：** SystemCapability.Kernel.Memory

**起始版本：** 10

**相关模块：** [memory](capi-memory.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [PurgMem](capi-memory-purgmem.md) | OH_PurgeableMemory | 可清除的内存结构。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef bool (\*OH_PurgeableMemory_ModifyFunc)(void *, size_t, void *)](#oh_purgeablememory_modifyfunc) | OH_PurgeableMemory_ModifyFunc | 函数指针，它指向一个用于构建可丢弃内存对象内容的函数。 |
| [OH_PurgeableMemory *OH_PurgeableMemory_Create(size_t size, OH_PurgeableMemory_ModifyFunc func, void *funcPara)](#oh_purgeablememory_create) | - | create 一个可丢弃内存对象的指针。 |
| [bool OH_PurgeableMemory_Destroy(OH_PurgeableMemory *purgObj)](#oh_purgeablememory_destroy) | - | 销毁一个可丢弃内存对象 |
| [bool OH_PurgeableMemory_BeginRead(OH_PurgeableMemory *purgObj)](#oh_purgeablememory_beginread) | - | 开始读取可丢弃内存对象。 |
| [void OH_PurgeableMemory_EndRead(OH_PurgeableMemory *purgObj)](#oh_purgeablememory_endread) | - | 结束读取可丢弃内存对象。 |
| [bool OH_PurgeableMemory_BeginWrite(OH_PurgeableMemory *purgObj)](#oh_purgeablememory_beginwrite) | - | 开始写入可丢弃内存对象。 |
| [void OH_PurgeableMemory_EndWrite(OH_PurgeableMemory *purgObj)](#oh_purgeablememory_endwrite) | - | 结束写入可丢弃内存对象。 |
| [void *OH_PurgeableMemory_GetContent(OH_PurgeableMemory *purgObj)](#oh_purgeablememory_getcontent) | - | 获取可丢弃内存对象的内容指针。 |
| [size_t OH_PurgeableMemory_ContentSize(OH_PurgeableMemory *purgObj)](#oh_purgeablememory_contentsize) | - | 获取可丢弃内存对象的内容大小。 |
| [bool OH_PurgeableMemory_AppendModify(OH_PurgeableMemory *purgObj, OH_PurgeableMemory_ModifyFunc func, void *funcPara)](#oh_purgeablememory_appendmodify) | - | 向可丢弃内存对象追加修改。 |

## 函数说明

### OH_PurgeableMemory_ModifyFunc()

```c
typedef bool (*OH_PurgeableMemory_ModifyFunc)(void *, size_t, void *)
```

**描述**

函数指针，它指向一个用于构建可丢弃内存对象内容的函数。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| void \* | *: data ptr, points to start address of a PurgMem obj's content. |
| size_t | 内容的数据大小。 |
| void \* |  *: 其他私有参数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 构建内容结果，true 表示成功，false 表示失败。 |

### OH_PurgeableMemory_Create()

```c
OH_PurgeableMemory *OH_PurgeableMemory_Create(size_t size, OH_PurgeableMemory_ModifyFunc func, void *funcPara)
```

**描述**

create 一个可丢弃内存对象的指针。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| size_t size | 可丢弃内存对象内容的数据大小。 |
| [OH_PurgeableMemory_ModifyFunc](capi-purgeable-memory-h.md#oh_purgeablememory_modifyfunc) func | 函数指针，用于在可丢弃内存对象的内容被清除时恢复数据。 |
| void *funcPara | func使用的参数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_PurgeableMemory *](capi-memory-purgmem.md) | 一个可丢弃内存对象的指针。 |

### OH_PurgeableMemory_Destroy()

```c
bool OH_PurgeableMemory_Destroy(OH_PurgeableMemory *purgObj)
```

**描述**

销毁一个可丢弃内存对象

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PurgeableMemory](capi-memory-purgmem.md) *purgObj | 待销毁的可丢弃内存对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | true 表示成功，false 表示失败。如果 purgObj 为 NULL，则返回 true。如果返回 true，purgObj 将被设置为 NULL 以避免释放后使用（Use-After-Free）。 |

### OH_PurgeableMemory_BeginRead()

```c
bool OH_PurgeableMemory_BeginRead(OH_PurgeableMemory *purgObj)
```

**描述**

开始读取可丢弃内存对象。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PurgeableMemory](capi-memory-purgmem.md) *purgObj | 可丢弃内存对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 如果 purgObj 的内容存在，则返回 true；     如果内容已被清除（不存在），系统将尝试恢复其数据，如果内容已被清除且恢复失败，则返回 false，如果内容恢复成功，则返回 true；     当此函数返回 true 时，操作系统无法回收 purgObj 内容的内存，直到调用 PurgMemEndRead()。 |

### OH_PurgeableMemory_EndRead()

```c
void OH_PurgeableMemory_EndRead(OH_PurgeableMemory *purgObj)
```

**描述**

结束读取可丢弃内存对象。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PurgeableMemory](capi-memory-purgmem.md) *purgObj | 可丢弃内存对象。当此函数执行结束，操作系统可能会稍后回收可丢弃内存对象的内容的内存。 |

### OH_PurgeableMemory_BeginWrite()

```c
bool OH_PurgeableMemory_BeginWrite(OH_PurgeableMemory *purgObj)
```

**描述**

开始写入可丢弃内存对象。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PurgeableMemory](capi-memory-purgmem.md) *purgObj | 可丢弃内存对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 如果 purgObj 的内容存在，则返回 true；      如果内容已被清除（不存在），系统将尝试恢复其数据，如果内容已被清除且恢复失败，则返回 false，如果内容成功恢复，则返回 true；      当此函数返回 true 时，操作系统无法回收 purgObj 内容的内存，直到调用 PurgMemEndWrite()。 |

### OH_PurgeableMemory_EndWrite()

```c
void OH_PurgeableMemory_EndWrite(OH_PurgeableMemory *purgObj)
```

**描述**

结束写入可丢弃内存对象。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PurgeableMemory](capi-memory-purgmem.md) *purgObj | 可丢弃内存对象。当此函数执行结束时，操作系统可能会稍后回收可丢弃内存对象的内容的内存。 |

### OH_PurgeableMemory_GetContent()

```c
void *OH_PurgeableMemory_GetContent(OH_PurgeableMemory *purgObj)
```

**描述**

获取可丢弃内存对象的内容指针。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PurgeableMemory](capi-memory-purgmem.md) *purgObj | 可丢弃内存对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| void * | 返回可丢弃内存对象内容的起始地址。      如果 purgObj 为 NULL，则返回 NULL。      此函数应受 PurgMemBeginRead()/PurgMemEndRead() 或 PurgMemBeginWrite()/PurgMemEndWrite() 保护。 |

### OH_PurgeableMemory_ContentSize()

```c
size_t OH_PurgeableMemory_ContentSize(OH_PurgeableMemory *purgObj)
```

**描述**

获取可丢弃内存对象的内容大小。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PurgeableMemory](capi-memory-purgmem.md) *purgObj | 可丢弃内存对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| size_t | 返回 purgObj 的内容大小。      如果 purgObj 为 NULL，则返回 0。 |

### OH_PurgeableMemory_AppendModify()

```c
bool OH_PurgeableMemory_AppendModify(OH_PurgeableMemory *purgObj, OH_PurgeableMemory_ModifyFunc func, void *funcPara)
```

**描述**

向可丢弃内存对象追加修改。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PurgeableMemory](capi-memory-purgmem.md) *purgObj | 可丢弃内存对象。 |
| [OH_PurgeableMemory_ModifyFunc](capi-purgeable-memory-h.md#oh_purgeablememory_modifyfunc) func | 函数指针，用于修改可丢弃内存对象的内容。 |
| void *funcPara | func 使用的参数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 追加结果，true 表示成功，false 表示失败。 |


