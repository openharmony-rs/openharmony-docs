# mutex.h

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->

## 概述

声明互斥锁（mutex）的C接口，用于在并发任务间提供互斥访问，保护共享资源免受竞争条件影响。

**库：** libffrt.z.so

**系统能力：** SystemCapability.Resourceschedule.Ffrt.Core

**起始版本：** 10

**相关模块：** [FFRT](capi-ffrt.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [FFRT_C_API int ffrt_mutexattr_init(ffrt_mutexattr_t* attr)](#ffrt_mutexattr_init) | 初始化mutex属性。初始化成功后，mutex属性被设置为默认值。该mutex属性不再使用时，必须通过[ffrt_mutexattr_destroy](capi-mutex-h.md#ffrt_mutexattr_destroy)销毁。 |
| [FFRT_C_API int ffrt_mutexattr_settype(ffrt_mutexattr_t* attr, int type)](#ffrt_mutexattr_settype) | 设置mutex属性的类型。类型可以是`ffrt_mutex_normal`（普通互斥锁）或`ffrt_mutex_recursive`（递归互斥锁，允许同一任务多次获取该锁）。 |
| [FFRT_C_API int ffrt_mutexattr_gettype(ffrt_mutexattr_t* attr, int* type)](#ffrt_mutexattr_gettype) | 获取mutex属性的类型。调用成功后，类型值通过出参`type`返回。 |
| [FFRT_C_API int ffrt_mutexattr_destroy(ffrt_mutexattr_t* attr)](#ffrt_mutexattr_destroy) | 销毁mutex属性。该mutex属性必须已通过[ffrt_mutexattr_init](capi-mutex-h.md#ffrt_mutexattr_init)初始化。 |
| [FFRT_C_API int ffrt_mutex_init(ffrt_mutex_t* mutex, const ffrt_mutexattr_t* attr)](#ffrt_mutex_init) | 初始化mutex。该mutex不再使用时，必须通过[ffrt_mutex_destroy](capi-mutex-h.md#ffrt_mutex_destroy)销毁。通过`attr`传入已配置的mutex属性，或传入空指针使用默认值。 |
| [FFRT_C_API int ffrt_mutex_lock(ffrt_mutex_t* mutex)](#ffrt_mutex_lock) | 加锁mutex。若mutex已被其他线程持有，则阻塞当前线程直到mutex可用。成功时，调用线程持有该mutex，直至通过[ffrt_mutex_unlock](capi-mutex-h.md#ffrt_mutex_unlock)释放。 |
| [FFRT_C_API int ffrt_mutex_unlock(ffrt_mutex_t* mutex)](#ffrt_mutex_unlock) | 解锁mutex。调用线程必须已持有该mutex，且该锁之前由[ffrt_mutex_lock](capi-mutex-h.md#ffrt_mutex_lock)或[ffrt_mutex_trylock](capi-mutex-h.md#ffrt_mutex_trylock)获取。 |
| [FFRT_C_API int ffrt_mutex_trylock(ffrt_mutex_t* mutex)](#ffrt_mutex_trylock) | 尝试加锁mutex。该接口为非阻塞操作：若mutex已被其他线程持有，则立即返回错误码。成功时，调用线程持有该mutex，直至通过[ffrt_mutex_unlock](capi-mutex-h.md#ffrt_mutex_unlock)释放。 |
| [FFRT_C_API int ffrt_mutex_destroy(ffrt_mutex_t* mutex)](#ffrt_mutex_destroy) | 销毁mutex。调用成功后，mutex占用的资源被释放，该mutex对象不可再使用。该mutex必须已通过[ffrt_mutex_init](capi-mutex-h.md#ffrt_mutex_init)初始化，且在调用本接口时不得被任何线程持有。 |

## 函数说明

### ffrt_mutexattr_init()

```c
FFRT_C_API int ffrt_mutexattr_init(ffrt_mutexattr_t* attr)
```

**描述**

初始化mutex属性。初始化成功后，mutex属性被设置为默认值。该mutex属性不再使用时，必须通过[ffrt_mutexattr_destroy](capi-mutex-h.md#ffrt_mutexattr_destroy)销毁。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_mutexattr_t](capi-ffrt-ffrt-mutexattr-t.md)* attr | 指向mutex属性的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FFRT_C_API int | mutex属性初始化成功时返回`ffrt_success`；<br>         否则返回`ffrt_error_inval`。 |

### ffrt_mutexattr_settype()

```c
FFRT_C_API int ffrt_mutexattr_settype(ffrt_mutexattr_t* attr, int type)
```

**描述**

设置mutex属性的类型。类型可以是`ffrt_mutex_normal`（普通互斥锁）或`ffrt_mutex_recursive`（递归互斥锁，允许同一任务多次获取该锁）。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_mutexattr_t](capi-ffrt-ffrt-mutexattr-t.md)* attr | 指向mutex属性的指针。 |
| int type | mutex类型，取值为`ffrt_mutex_normal`、`ffrt_mutex_recursive`或`ffrt_mutex_default`（等价于`ffrt_mutex_normal`）。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FFRT_C_API int | mutex属性类型设置成功时返回`ffrt_success`；<br>         当attr为空指针，或mutex属性类型既不是`ffrt_mutex_normal`也不是`ffrt_mutex_recursive`时<br>         返回`ffrt_error_inval`。 |

**参考：**

[ffrt_mutex_type](capi-type-def-h.md#ffrt_mutex_type)


### ffrt_mutexattr_gettype()

```c
FFRT_C_API int ffrt_mutexattr_gettype(ffrt_mutexattr_t* attr, int* type)
```

**描述**

获取mutex属性的类型。调用成功后，类型值通过出参`type`返回。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_mutexattr_t](capi-ffrt-ffrt-mutexattr-t.md)* attr | 指向mutex属性的指针。 |
| int* type | 指向mutex类型的指针，用于接收获取的类型值（`ffrt_mutex_normal`或`ffrt_mutex_recursive`）。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FFRT_C_API int | mutex属性类型获取成功时返回`ffrt_success`；<br>         attr或type为空指针时返回`ffrt_error_inval`。 |

### ffrt_mutexattr_destroy()

```c
FFRT_C_API int ffrt_mutexattr_destroy(ffrt_mutexattr_t* attr)
```

**描述**

销毁mutex属性。该mutex属性必须已通过[ffrt_mutexattr_init](capi-mutex-h.md#ffrt_mutexattr_init)初始化。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_mutexattr_t](capi-ffrt-ffrt-mutexattr-t.md)* attr | 指向mutex属性的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FFRT_C_API int | mutex属性销毁成功时返回`ffrt_success`；<br>         否则返回`ffrt_error_inval`。 |

### ffrt_mutex_init()

```c
FFRT_C_API int ffrt_mutex_init(ffrt_mutex_t* mutex, const ffrt_mutexattr_t* attr)
```

**描述**

初始化mutex。该mutex不再使用时，必须通过[ffrt_mutex_destroy](capi-mutex-h.md#ffrt_mutex_destroy)销毁。通过`attr`传入已配置的mutex属性，或传入空指针使用默认值。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_mutex_t](capi-ffrt-ffrt-mutex-t.md)* mutex | 指向mutex的指针。 |
| [const ffrt_mutexattr_t](capi-ffrt-ffrt-mutexattr-t.md)* attr | 指向mutex属性的指针，或传入空指针使用默认值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FFRT_C_API int | mutex初始化成功时返回`ffrt_success`；<br>         `mutex`为空，或`attr`非空但未指定合法的mutex类型时返回`ffrt_error_inval`。 |

### ffrt_mutex_lock()

```c
FFRT_C_API int ffrt_mutex_lock(ffrt_mutex_t* mutex)
```

**描述**

加锁mutex。若mutex已被其他线程持有，则阻塞当前线程直到mutex可用。成功时，调用线程持有该mutex，直至通过[ffrt_mutex_unlock](capi-mutex-h.md#ffrt_mutex_unlock)释放。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_mutex_t](capi-ffrt-ffrt-mutex-t.md)* mutex | 指向mutex的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FFRT_C_API int | mutex加锁成功时返回`ffrt_success`；<br>         否则返回`ffrt_error_inval`。 |

**参考：**

[ffrt_mutex_trylock](capi-mutex-h.md#ffrt_mutex_trylock)


### ffrt_mutex_unlock()

```c
FFRT_C_API int ffrt_mutex_unlock(ffrt_mutex_t* mutex)
```

**描述**

解锁mutex。调用线程必须已持有该mutex，且该锁之前由[ffrt_mutex_lock](capi-mutex-h.md#ffrt_mutex_lock)或[ffrt_mutex_trylock](capi-mutex-h.md#ffrt_mutex_trylock)获取。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_mutex_t](capi-ffrt-ffrt-mutex-t.md)* mutex | 指向mutex的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FFRT_C_API int | mutex解锁成功时返回`ffrt_success`；<br>         否则返回`ffrt_error_inval`。 |

### ffrt_mutex_trylock()

```c
FFRT_C_API int ffrt_mutex_trylock(ffrt_mutex_t* mutex)
```

**描述**

尝试加锁mutex。该接口为非阻塞操作：若mutex已被其他线程持有，则立即返回错误码。成功时，调用线程持有该mutex，直至通过[ffrt_mutex_unlock](capi-mutex-h.md#ffrt_mutex_unlock)释放。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_mutex_t](capi-ffrt-ffrt-mutex-t.md)* mutex | 指向mutex的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FFRT_C_API int | mutex加锁成功时返回`ffrt_success`；<br>         否则返回`ffrt_error_inval`或`ffrt_error_busy`。 |

**参考：**

[ffrt_mutex_lock](capi-mutex-h.md#ffrt_mutex_lock)


### ffrt_mutex_destroy()

```c
FFRT_C_API int ffrt_mutex_destroy(ffrt_mutex_t* mutex)
```

**描述**

销毁mutex。调用成功后，mutex占用的资源被释放，该mutex对象不可再使用。该mutex必须已通过[ffrt_mutex_init](capi-mutex-h.md#ffrt_mutex_init)初始化，且在调用本接口时不得被任何线程持有。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_mutex_t](capi-ffrt-ffrt-mutex-t.md)* mutex | 指向mutex的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FFRT_C_API int | mutex销毁成功时返回`ffrt_success`；<br>         否则返回`ffrt_error_inval`。 |


