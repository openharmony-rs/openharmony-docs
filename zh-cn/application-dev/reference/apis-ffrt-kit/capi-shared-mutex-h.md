# shared_mutex.h

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->

## 概述

声明读写锁（rwlock）的C接口。

**库：** libffrt.z.so

**系统能力：** SystemCapability.Resourceschedule.Ffrt.Core

**起始版本：** 18

**相关模块：** [FFRT](capi-ffrt.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [FFRT_C_API int ffrt_rwlock_init(ffrt_rwlock_t* rwlock, const ffrt_rwlockattr_t* attr)](#ffrt_rwlock_init) | 初始化rwlock。该rwlock不再使用时，必须通过[ffrt_rwlock_destroy](capi-shared-mutex-h.md#ffrt_rwlock_destroy)销毁。 |
| [FFRT_C_API int ffrt_rwlock_wrlock(ffrt_rwlock_t* rwlock)](#ffrt_rwlock_wrlock) | 加写锁。锁不可用时阻塞当前线程。成功时，调用线程持有排他写锁，直至通过[ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock)释放。写锁具有排他性，不允许与任何读锁同时持有。 |
| [FFRT_C_API int ffrt_rwlock_trywrlock(ffrt_rwlock_t* rwlock)](#ffrt_rwlock_trywrlock) | 尝试加写锁。不会阻塞当前线程。成功时，调用线程持有排他写锁，直至通过[ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock)释放。 |
| [FFRT_C_API int ffrt_rwlock_rdlock(ffrt_rwlock_t* rwlock)](#ffrt_rwlock_rdlock) | 加读锁。锁不可用时阻塞当前线程。成功时，调用线程持有读锁，直至通过[ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock)释放。多个读者可同时持有该锁，但不允许与写锁同时持有。 |
| [FFRT_C_API int ffrt_rwlock_tryrdlock(ffrt_rwlock_t* rwlock)](#ffrt_rwlock_tryrdlock) | 尝试加读锁。不会阻塞当前线程。成功时，调用线程持有读锁，直至通过[ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock)释放。 |
| [FFRT_C_API int ffrt_rwlock_unlock(ffrt_rwlock_t* rwlock)](#ffrt_rwlock_unlock) | 解锁rwlock。调用线程必须已持有该rwlock，且该锁之前由[ffrt_rwlock_rdlock](capi-shared-mutex-h.md#ffrt_rwlock_rdlock)、[ffrt_rwlock_tryrdlock](capi-shared-mutex-h.md#ffrt_rwlock_tryrdlock)、[ffrt_rwlock_wrlock](capi-shared-mutex-h.md#ffrt_rwlock_wrlock)或[ffrt_rwlock_trywrlock](capi-shared-mutex-h.md#ffrt_rwlock_trywrlock)获取。 |
| [FFRT_C_API int ffrt_rwlock_destroy(ffrt_rwlock_t* rwlock)](#ffrt_rwlock_destroy) | 销毁rwlock。该rwlock必须已通过[ffrt_rwlock_init](capi-shared-mutex-h.md#ffrt_rwlock_init)初始化，且在调用本接口时不得被任何线程以读锁或写锁持有。 |

## 函数说明

### ffrt_rwlock_init()

```c
FFRT_C_API int ffrt_rwlock_init(ffrt_rwlock_t* rwlock, const ffrt_rwlockattr_t* attr)
```

**描述**

初始化rwlock。该rwlock不再使用时，必须通过[ffrt_rwlock_destroy](capi-shared-mutex-h.md#ffrt_rwlock_destroy)销毁。

**起始版本：** 18

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_rwlock_t](capi-ffrt-ffrt-rwlock-t.md)* rwlock | 指向rwlock的指针。 |
| [const ffrt_rwlockattr_t](capi-ffrt-ffrt-rwlockattr-t.md)* attr | 指向rwlock属性的指针。当前仅支持默认模式，需设置为空指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FFRT_C_API int | rwlock初始化成功且attr为空指针时返回`ffrt_success`；<br>         否则返回`ffrt_error_inval`。 |

### ffrt_rwlock_wrlock()

```c
FFRT_C_API int ffrt_rwlock_wrlock(ffrt_rwlock_t* rwlock)
```

**描述**

加写锁。锁不可用时阻塞当前线程。成功时，调用线程持有排他写锁，直至通过[ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock)释放。写锁具有排他性，不允许与任何读锁同时持有。

**起始版本：** 18

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_rwlock_t](capi-ffrt-ffrt-rwlock-t.md)* rwlock | 指向rwlock的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FFRT_C_API int | rwlock加锁成功时返回`ffrt_success`；<br>         `rwlock`为空指针时返回`ffrt_error_inval`。 |

**参考：**

[ffrt_rwlock_rdlock](capi-shared-mutex-h.md#ffrt_rwlock_rdlock)
[ffrt_rwlock_trywrlock](capi-shared-mutex-h.md#ffrt_rwlock_trywrlock)


### ffrt_rwlock_trywrlock()

```c
FFRT_C_API int ffrt_rwlock_trywrlock(ffrt_rwlock_t* rwlock)
```

**描述**

尝试加写锁。不会阻塞当前线程。成功时，调用线程持有排他写锁，直至通过[ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock)释放。

**起始版本：** 18

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_rwlock_t](capi-ffrt-ffrt-rwlock-t.md)* rwlock | 指向rwlock的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FFRT_C_API int | rwlock加锁成功时返回`ffrt_success`；<br>         否则返回`ffrt_error_inval`或`ffrt_error_busy`。 |

**参考：**

[ffrt_rwlock_wrlock](capi-shared-mutex-h.md#ffrt_rwlock_wrlock)


### ffrt_rwlock_rdlock()

```c
FFRT_C_API int ffrt_rwlock_rdlock(ffrt_rwlock_t* rwlock)
```

**描述**

加读锁。锁不可用时阻塞当前线程。成功时，调用线程持有读锁，直至通过[ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock)释放。多个读者可同时持有该锁，但不允许与写锁同时持有。

**起始版本：** 18

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_rwlock_t](capi-ffrt-ffrt-rwlock-t.md)* rwlock | 指向rwlock的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FFRT_C_API int | rwlock加锁成功时返回`ffrt_success`；<br>         `rwlock`为空指针时返回`ffrt_error_inval`。 |

**参考：**

[ffrt_rwlock_wrlock](capi-shared-mutex-h.md#ffrt_rwlock_wrlock)
[ffrt_rwlock_tryrdlock](capi-shared-mutex-h.md#ffrt_rwlock_tryrdlock)


### ffrt_rwlock_tryrdlock()

```c
FFRT_C_API int ffrt_rwlock_tryrdlock(ffrt_rwlock_t* rwlock)
```

**描述**

尝试加读锁。不会阻塞当前线程。成功时，调用线程持有读锁，直至通过[ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock)释放。

**起始版本：** 18

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_rwlock_t](capi-ffrt-ffrt-rwlock-t.md)* rwlock | 指向rwlock的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FFRT_C_API int | rwlock加锁成功时返回`ffrt_success`；<br>         否则返回`ffrt_error_inval`或`ffrt_error_busy`。 |

**参考：**

[ffrt_rwlock_rdlock](capi-shared-mutex-h.md#ffrt_rwlock_rdlock)


### ffrt_rwlock_unlock()

```c
FFRT_C_API int ffrt_rwlock_unlock(ffrt_rwlock_t* rwlock)
```

**描述**

解锁rwlock。调用线程必须已持有该rwlock，且该锁之前由[ffrt_rwlock_rdlock](capi-shared-mutex-h.md#ffrt_rwlock_rdlock)、[ffrt_rwlock_tryrdlock](capi-shared-mutex-h.md#ffrt_rwlock_tryrdlock)、[ffrt_rwlock_wrlock](capi-shared-mutex-h.md#ffrt_rwlock_wrlock)或[ffrt_rwlock_trywrlock](capi-shared-mutex-h.md#ffrt_rwlock_trywrlock)获取。

**起始版本：** 18

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_rwlock_t](capi-ffrt-ffrt-rwlock-t.md)* rwlock | 指向rwlock的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FFRT_C_API int | rwlock解锁成功时返回`ffrt_success`；<br>         否则返回`ffrt_error_inval`。 |

### ffrt_rwlock_destroy()

```c
FFRT_C_API int ffrt_rwlock_destroy(ffrt_rwlock_t* rwlock)
```

**描述**

销毁rwlock。该rwlock必须已通过[ffrt_rwlock_init](capi-shared-mutex-h.md#ffrt_rwlock_init)初始化，且在调用本接口时不得被任何线程以读锁或写锁持有。

**起始版本：** 18

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_rwlock_t](capi-ffrt-ffrt-rwlock-t.md)* rwlock | 指向rwlock的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FFRT_C_API int | rwlock销毁成功时返回`ffrt_success`；<br>         否则返回`ffrt_error_inval`。 |


