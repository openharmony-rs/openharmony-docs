# task.h

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->

## 概述

声明FFRT任务的C接口，提供任务属性的初始化与销毁、任务QoS设置与获取、任务延迟时间管理、并发队列任务优先级管理、任务栈大小管理、任务提交调度执行、任务句柄引用计数管理以及任务等待等功能。

**引用文件：** <ffrt/task.h>

**库：** libffrt.z.so

**系统能力：** SystemCapability.Resourceschedule.Ffrt.Core

**起始版本：** 10

**相关模块：** [FFRT](capi-ffrt.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [FFRT_C_API int ffrt_task_attr_init(ffrt_task_attr_t* attr)](#ffrt_task_attr_init) | 初始化任务属性。调用成功后，任务属性将被设置为默认值（如默认QoS为[ffrt_qos_default](capi-type-def-h.md#ffrt_qos_default_t)）。使用完毕后须调用[ffrt_task_attr_destroy](capi-task-h.md#ffrt_task_attr_destroy)释放任务属性。 |
| [FFRT_C_API void ffrt_task_attr_set_name(ffrt_task_attr_t* attr, const char* name)](#ffrt_task_attr_set_name) | 设置任务属性的名称。 |
| [FFRT_C_API const char* ffrt_task_attr_get_name(const ffrt_task_attr_t* attr)](#ffrt_task_attr_get_name) | 获取任务属性的名称。 |
| [FFRT_C_API void ffrt_task_attr_destroy(ffrt_task_attr_t* attr)](#ffrt_task_attr_destroy) | 销毁任务属性。必须在已通过[ffrt_task_attr_init](capi-task-h.md#ffrt_task_attr_init)初始化的任务属性上调用本接口，用于释放属性持有的资源。销毁后该任务属性不可再使用。 |
| [FFRT_C_API void ffrt_task_attr_set_qos(ffrt_task_attr_t* attr, ffrt_qos_t qos)](#ffrt_task_attr_set_qos) | 设置任务属性的QoS。QoS用于控制任务的调度优先级。例如，对用户交互型任务配置高QoS以保证响应速度，对后台或维护型任务配置低QoS以减少其对系统资源的占用。 |
| [FFRT_C_API ffrt_qos_t ffrt_task_attr_get_qos(const ffrt_task_attr_t* attr)](#ffrt_task_attr_get_qos) | 获取任务属性的QoS。 |
| [FFRT_C_API void ffrt_task_attr_set_delay(ffrt_task_attr_t* attr, uint64_t delay_us)](#ffrt_task_attr_set_delay) | 设置任务属性的延迟时间。 |
| [FFRT_C_API uint64_t ffrt_task_attr_get_delay(const ffrt_task_attr_t* attr)](#ffrt_task_attr_get_delay) | 获取任务属性的延迟时间。 |
| [FFRT_C_API void ffrt_task_attr_set_queue_priority(ffrt_task_attr_t* attr, ffrt_queue_priority_t priority)](#ffrt_task_attr_set_queue_priority) | 设置任务属性的优先级。 |
| [FFRT_C_API ffrt_queue_priority_t ffrt_task_attr_get_queue_priority(const ffrt_task_attr_t* attr)](#ffrt_task_attr_get_queue_priority) | 获取任务属性的优先级。 |
| [FFRT_C_API void ffrt_task_attr_set_stack_size(ffrt_task_attr_t* attr, uint64_t size)](#ffrt_task_attr_set_stack_size) | 设置任务属性的栈大小。 |
| [FFRT_C_API uint64_t ffrt_task_attr_get_stack_size(const ffrt_task_attr_t* attr)](#ffrt_task_attr_get_stack_size) | 获取任务属性的栈大小。 |
| [FFRT_C_API int ffrt_this_task_update_qos(ffrt_qos_t qos)](#ffrt_this_task_update_qos) | 更新当前任务的QoS。在任务执行过程中需要根据运行阶段动态调整调度优先级时使用本接口。例如，一个后台同步任务在用户触发相关操作后，可通过本接口提升QoS等级以加快处理速度。 |
| [FFRT_C_API ffrt_qos_t ffrt_this_task_get_qos(void)](#ffrt_this_task_get_qos) | 获取当前任务的QoS。 |
| [FFRT_C_API uint64_t ffrt_this_task_get_id(void)](#ffrt_this_task_get_id) | 获取当前任务的ID。 |
| [FFRT_C_API void *ffrt_alloc_auto_managed_function_storage_base(ffrt_function_kind_t kind)](#ffrt_alloc_auto_managed_function_storage_base) | 申请函数执行结构体的内存。申请的内存用作任务执行体封装，在通过[ffrt_submit_base](capi-task-h.md#ffrt_submit_base)或[ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base)提交任务时传入。该内存在所提交任务执行完成后由FFRT运行时自动释放，调用方无需手动释放。 |
| [FFRT_C_API void ffrt_submit_base(ffrt_function_header_t* f, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)](#ffrt_submit_base) | 提交任务调度执行。任务执行体、输入依赖、输出依赖和任务属性被一同提交到FFRT调度器，调度器根据依赖关系和任务QoS确定任务的执行时机并选择工作线程执行该任务。本接口为底层提交接口，若任务不需要销毁回调，可使用简化接口[ffrt_submit_f](capi-task-h.md#ffrt_submit_f)。与[ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base)的区别在于本接口不返回任务句柄，适用于不需要对已提交任务进行后续依赖管理或等待的场景。若任务属性中已通过[ffrt_task_attr_set_delay](capi-task-h.md#ffrt_task_attr_set_delay)设置延迟时间，则输入输出依赖关系不再生效，任务在延迟结束后被调度。 |
| [FFRT_C_API ffrt_task_handle_t ffrt_submit_h_base(ffrt_function_header_t* f, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)](#ffrt_submit_h_base) | 提交任务调度执行并返回任务句柄。任务执行体、输入依赖、输出依赖和任务属性被一同提交到FFRT调度器，调度器根据依赖关系确定任务的执行时机。返回的任务句柄可用于通过[ffrt_wait_deps](capi-task-h.md#ffrt_wait_deps)等待任务完成，或作为其他任务的输入依赖以构建任务间的依赖关系。本接口为返回任务句柄的底层提交接口，若任务不需要销毁回调，可使用简化接口[ffrt_submit_h_f](capi-task-h.md#ffrt_submit_h_f)。返回的任务句柄需通过[ffrt_task_handle_destroy](capi-task-h.md#ffrt_task_handle_destroy)销毁，引用计数可通过[ffrt_task_handle_inc_ref](capi-task-h.md#ffrt_task_handle_inc_ref)和[ffrt_task_handle_dec_ref](capi-task-h.md#ffrt_task_handle_dec_ref)管理。 |
| [FFRT_C_API void ffrt_submit_f(ffrt_function_t func, void* arg, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)](#ffrt_submit_f) | 提交任务调度执行，是[ffrt_submit_base](capi-task-h.md#ffrt_submit_base)接口的简化形式。该接口将给定的任务函数及其参数包装为通用任务结构体（`ffrt_function_kind_general`），其中用于处理执行后清理的任务销毁回调（after_func）会被设为NULL，因而省略任何额外清理动作。封装后的任务结构体随后通过[ffrt_submit_base](capi-task-h.md#ffrt_submit_base)接口提交。若任务属性中已通过[ffrt_task_attr_set_delay](capi-task-h.md#ffrt_task_attr_set_delay)设置延迟时间，则输入输出依赖关系不再生效，任务在延迟结束后被调度。 |
| [FFRT_C_API ffrt_task_handle_t ffrt_submit_h_f(ffrt_function_t func, void* arg, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)](#ffrt_submit_h_f) | 提交任务调度执行并返回任务句柄，是[ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base)接口的简化形式。该接口将给定的任务函数及其参数包装为通用任务结构体（`ffrt_function_kind_general`），其中用于处理执行后清理的任务销毁回调（after_func）会被设为NULL，因而省略任何额外清理动作。封装后的任务结构体随后通过[ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base)接口提交。若任务属性中已通过[ffrt_task_attr_set_delay](capi-task-h.md#ffrt_task_attr_set_delay)设置延迟时间，则输入输出依赖关系不再生效，任务在延迟结束后被调度。返回的任务句柄需通过[ffrt_task_handle_destroy](capi-task-h.md#ffrt_task_handle_destroy)销毁。 |
| [FFRT_C_API uint32_t ffrt_task_handle_inc_ref(ffrt_task_handle_t handle)](#ffrt_task_handle_inc_ref) | 增加任务句柄的引用计数。任务句柄的引用计数加一，并返回增加前的引用计数值。 |
| [FFRT_C_API uint32_t ffrt_task_handle_dec_ref(ffrt_task_handle_t handle)](#ffrt_task_handle_dec_ref) | 减少任务句柄的引用计数。任务句柄的引用计数减一，并返回减少前的引用计数值。本接口应与[ffrt_task_handle_inc_ref](capi-task-h.md#ffrt_task_handle_inc_ref)配对使用，句柄不再使用时需通过[ffrt_task_handle_destroy](capi-task-h.md#ffrt_task_handle_destroy)销毁。 |
| [FFRT_C_API void ffrt_task_handle_destroy(ffrt_task_handle_t handle)](#ffrt_task_handle_destroy) | 销毁任务句柄。调用后，任务句柄被销毁并释放关联的资源，句柄不可再使用。 |
| [FFRT_C_API void ffrt_wait_deps(const ffrt_deps_t* deps)](#ffrt_wait_deps) | 阻塞当前任务，等待依赖任务完成后再继续执行。 |
| [FFRT_C_API void ffrt_wait(void)](#ffrt_wait) | 阻塞当前任务，等待所有已提交任务完成后再继续执行。 |

## 函数说明

### ffrt_task_attr_init()

```c
FFRT_C_API int ffrt_task_attr_init(ffrt_task_attr_t* attr)
```

**描述**

初始化任务属性。调用成功后，任务属性将被设置为默认值（如默认QoS为[ffrt_qos_default](capi-type-def-h.md#ffrt_qos_default_t)）。使用完毕后须调用[ffrt_task_attr_destroy](capi-task-h.md#ffrt_task_attr_destroy)释放任务属性。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | 指向任务属性的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FFRT_C_API int | 任务属性初始化成功时返回`0`；<br>         否则返回`-1`。 |

### ffrt_task_attr_set_name()

```c
FFRT_C_API void ffrt_task_attr_set_name(ffrt_task_attr_t* attr, const char* name)
```

**描述**

设置任务属性的名称。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | 指向任务属性的指针。 |
| const char* name | 指向任务名称的指针。 |

### ffrt_task_attr_get_name()

```c
FFRT_C_API const char* ffrt_task_attr_get_name(const ffrt_task_attr_t* attr)
```

**描述**

获取任务属性的名称。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | 指向任务属性的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FFRT_C_API const char* | 任务名称获取成功时返回非空的任务名称指针；<br>         否则返回空指针。 |

### ffrt_task_attr_destroy()

```c
FFRT_C_API void ffrt_task_attr_destroy(ffrt_task_attr_t* attr)
```

**描述**

销毁任务属性。必须在已通过[ffrt_task_attr_init](capi-task-h.md#ffrt_task_attr_init)初始化的任务属性上调用本接口，用于释放属性持有的资源。销毁后该任务属性不可再使用。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | 指向任务属性的指针。 |

### ffrt_task_attr_set_qos()

```c
FFRT_C_API void ffrt_task_attr_set_qos(ffrt_task_attr_t* attr, ffrt_qos_t qos)
```

**描述**

设置任务属性的QoS。QoS用于控制任务的调度优先级。例如，对用户交互型任务配置高QoS以保证响应速度，对后台或维护型任务配置低QoS以减少其对系统资源的占用。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | 指向任务属性的指针。 |
| [ffrt_qos_t](capi-type-def-h.md#变量) qos | 待设置的QoS等级，取值参考{@link ffrt_qos_t}。 |

### ffrt_task_attr_get_qos()

```c
FFRT_C_API ffrt_qos_t ffrt_task_attr_get_qos(const ffrt_task_attr_t* attr)
```

**描述**

获取任务属性的QoS。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | 指向任务属性的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FFRT_C_API [ffrt_qos_t](capi-type-def-h.md#变量) | QoS等级，默认返回`ffrt_qos_default`。 |

### ffrt_task_attr_set_delay()

```c
FFRT_C_API void ffrt_task_attr_set_delay(ffrt_task_attr_t* attr, uint64_t delay_us)
```

**描述**

设置任务属性的延迟时间。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | 指向任务属性的指针。 |
| uint64_t delay_us | 任务延迟时间，单位是微秒。 |

### ffrt_task_attr_get_delay()

```c
FFRT_C_API uint64_t ffrt_task_attr_get_delay(const ffrt_task_attr_t* attr)
```

**描述**

获取任务属性的延迟时间。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | 指向任务属性的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FFRT_C_API uint64_t | 任务延迟时间，单位是微秒。 |

### ffrt_task_attr_set_queue_priority()

```c
FFRT_C_API void ffrt_task_attr_set_queue_priority(ffrt_task_attr_t* attr, ffrt_queue_priority_t priority)
```

**描述**

设置任务属性的优先级。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | 指向任务属性的指针。 |
| [ffrt_queue_priority_t](capi-type-def-h.md#ffrt_queue_priority_t) priority | 并发队列任务的执行优先级，取值参考[ffrt_queue_priority_t](capi-type-def-h.md#ffrt_queue_priority_t)；在同一并发队列内，高优先级任务优先于低优先级任务被调度。超出合法范围的值会被静默忽略。 |

### ffrt_task_attr_get_queue_priority()

```c
FFRT_C_API ffrt_queue_priority_t ffrt_task_attr_get_queue_priority(const ffrt_task_attr_t* attr)
```

**描述**

获取任务属性的优先级。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | 指向任务属性的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FFRT_C_API [ffrt_queue_priority_t](capi-type-def-h.md#ffrt_queue_priority_t) | 并发队列任务的优先级。 |

### ffrt_task_attr_set_stack_size()

```c
FFRT_C_API void ffrt_task_attr_set_stack_size(ffrt_task_attr_t* attr, uint64_t size)
```

**描述**

设置任务属性的栈大小。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | 指向任务属性的指针。 |
| uint64_t size | 任务栈大小，单位是字节。需大于系统支持的最小栈大小，否则可能导致栈溢出；设置过大时可能导致内存分配失败。 |

### ffrt_task_attr_get_stack_size()

```c
FFRT_C_API uint64_t ffrt_task_attr_get_stack_size(const ffrt_task_attr_t* attr)
```

**描述**

获取任务属性的栈大小。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | 指向任务属性的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FFRT_C_API uint64_t | 任务栈大小，单位是字节。 |

### ffrt_this_task_update_qos()

```c
FFRT_C_API int ffrt_this_task_update_qos(ffrt_qos_t qos)
```

**描述**

更新当前任务的QoS。在任务执行过程中需要根据运行阶段动态调整调度优先级时使用本接口。例如，一个后台同步任务在用户触发相关操作后，可通过本接口提升QoS等级以加快处理速度。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_qos_t](capi-type-def-h.md#变量) qos | 任务待更新的QoS等级，取值参考{@link ffrt_qos_t}。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FFRT_C_API int | QoS更新成功，或新QoS与当前QoS相同时返回`0`；<br>         QoS映射未注册、当前任务为空，或当前任务非通用类型任务（即非通过[ffrt_submit_base](capi-task-h.md#ffrt_submit_base)或[ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base)提交的任务）时返回`1`。 |

**参考：**

[ffrt_this_task_get_qos](capi-task-h.md#ffrt_this_task_get_qos)


### ffrt_this_task_get_qos()

```c
FFRT_C_API ffrt_qos_t ffrt_this_task_get_qos(void)
```

**描述**

获取当前任务的QoS。

**起始版本：** 12

**返回：**

| 类型 | 说明 |
| -- | -- |
| FFRT_C_API [ffrt_qos_t](capi-type-def-h.md#变量) | 任务QoS。 |

### ffrt_this_task_get_id()

```c
FFRT_C_API uint64_t ffrt_this_task_get_id(void)
```

**描述**

获取当前任务的ID。

**起始版本：** 10

**返回：**

| 类型 | 说明 |
| -- | -- |
| FFRT_C_API uint64_t | 当前运行任务的唯一任务ID。 |

### ffrt_alloc_auto_managed_function_storage_base()

```c
FFRT_C_API void *ffrt_alloc_auto_managed_function_storage_base(ffrt_function_kind_t kind)
```

**描述**

申请函数执行结构体的内存。申请的内存用作任务执行体封装，在通过[ffrt_submit_base](capi-task-h.md#ffrt_submit_base)或[ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base)提交任务时传入。该内存在所提交任务执行完成后由FFRT运行时自动释放，调用方无需手动释放。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_function_kind_t](capi-type-def-h.md#ffrt_function_kind_t) kind | 函数执行结构体类型。通用类型适用于通过[ffrt_submit_base](capi-task-h.md#ffrt_submit_base)或[ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base)提交的任务，队列类型适用于通过并发队列提交接口提交的任务。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FFRT_C_API void * | 内存申请成功时返回非空指针；<br>         否则返回空指针。 |

**参考：**

[ffrt_submit_base](capi-task-h.md#ffrt_submit_base)
[ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base)


### ffrt_submit_base()

```c
FFRT_C_API void ffrt_submit_base(ffrt_function_header_t* f, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)
```

**描述**

提交任务调度执行。任务执行体、输入依赖、输出依赖和任务属性被一同提交到FFRT调度器，调度器根据依赖关系和任务QoS确定任务的执行时机并选择工作线程执行该任务。本接口为底层提交接口，若任务不需要销毁回调，可使用简化接口[ffrt_submit_f](capi-task-h.md#ffrt_submit_f)。与[ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base)的区别在于本接口不返回任务句柄，适用于不需要对已提交任务进行后续依赖管理或等待的场景。若任务属性中已通过[ffrt_task_attr_set_delay](capi-task-h.md#ffrt_task_attr_set_delay)设置延迟时间，则输入输出依赖关系不再生效，任务在延迟结束后被调度。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_function_header_t](capi-ffrt-ffrt-function-header-t.md)* f | 任务执行体封装的指针，需通过[ffrt_alloc_auto_managed_function_storage_base](capi-task-h.md#ffrt_alloc_auto_managed_function_storage_base)申请内存，且必须包含任务销毁回调函数。 |
| [const ffrt_deps_t](capi-ffrt-ffrt-deps-t.md)* in_deps | 指向输入依赖的指针。 |
| [const ffrt_deps_t](capi-ffrt-ffrt-deps-t.md)* out_deps | 指向输出依赖的指针。 |
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | 指向任务属性的指针。 |

**参考：**

[ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base)


### ffrt_submit_h_base()

```c
FFRT_C_API ffrt_task_handle_t ffrt_submit_h_base(ffrt_function_header_t* f, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)
```

**描述**

提交任务调度执行并返回任务句柄。任务执行体、输入依赖、输出依赖和任务属性被一同提交到FFRT调度器，调度器根据依赖关系确定任务的执行时机。返回的任务句柄可用于通过[ffrt_wait_deps](capi-task-h.md#ffrt_wait_deps)等待任务完成，或作为其他任务的输入依赖以构建任务间的依赖关系。本接口为返回任务句柄的底层提交接口，若任务不需要销毁回调，可使用简化接口[ffrt_submit_h_f](capi-task-h.md#ffrt_submit_h_f)。返回的任务句柄需通过[ffrt_task_handle_destroy](capi-task-h.md#ffrt_task_handle_destroy)销毁，引用计数可通过[ffrt_task_handle_inc_ref](capi-task-h.md#ffrt_task_handle_inc_ref)和[ffrt_task_handle_dec_ref](capi-task-h.md#ffrt_task_handle_dec_ref)管理。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_function_header_t](capi-ffrt-ffrt-function-header-t.md)* f | 任务执行体封装的指针，需通过[ffrt_alloc_auto_managed_function_storage_base](capi-task-h.md#ffrt_alloc_auto_managed_function_storage_base)申请内存，且必须包含任务销毁回调函数。 |
| [const ffrt_deps_t](capi-ffrt-ffrt-deps-t.md)* in_deps | 指向输入依赖的指针。 |
| [const ffrt_deps_t](capi-ffrt-ffrt-deps-t.md)* out_deps | 指向输出依赖的指针。 |
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | 指向任务属性的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FFRT_C_API [ffrt_task_handle_t](capi-ffrt-ffrt-task-handle-t.md) | 任务提交成功时返回非空的任务句柄；<br>         否则返回空指针。 |

**参考：**

[ffrt_submit_base](capi-task-h.md#ffrt_submit_base)


### ffrt_submit_f()

```c
FFRT_C_API void ffrt_submit_f(ffrt_function_t func, void* arg, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)
```

**描述**

提交任务调度执行，是[ffrt_submit_base](capi-task-h.md#ffrt_submit_base)接口的简化形式。该接口将给定的任务函数及其参数包装为通用任务结构体（`ffrt_function_kind_general`），其中用于处理执行后清理的任务销毁回调（after_func）会被设为NULL，因而省略任何额外清理动作。封装后的任务结构体随后通过[ffrt_submit_base](capi-task-h.md#ffrt_submit_base)接口提交。若任务属性中已通过[ffrt_task_attr_set_delay](capi-task-h.md#ffrt_task_attr_set_delay)设置延迟时间，则输入输出依赖关系不再生效，任务在延迟结束后被调度。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_function_t](capi-type-def-h.md#ffrt_function_t) func | 待执行的任务函数。 |
| void* arg | 指向传递给任务函数的参数或闭包数据的指针。 |
| [const ffrt_deps_t](capi-ffrt-ffrt-deps-t.md)* in_deps | 指向输入依赖的指针。 |
| [const ffrt_deps_t](capi-ffrt-ffrt-deps-t.md)* out_deps | 指向输出依赖的指针。 |
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | 指向任务属性的指针。 |

**参考：**

[ffrt_submit_base](capi-task-h.md#ffrt_submit_base)


### ffrt_submit_h_f()

```c
FFRT_C_API ffrt_task_handle_t ffrt_submit_h_f(ffrt_function_t func, void* arg, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)
```

**描述**

提交任务调度执行并返回任务句柄，是[ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base)接口的简化形式。该接口将给定的任务函数及其参数包装为通用任务结构体（`ffrt_function_kind_general`），其中用于处理执行后清理的任务销毁回调（after_func）会被设为NULL，因而省略任何额外清理动作。封装后的任务结构体随后通过[ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base)接口提交。若任务属性中已通过[ffrt_task_attr_set_delay](capi-task-h.md#ffrt_task_attr_set_delay)设置延迟时间，则输入输出依赖关系不再生效，任务在延迟结束后被调度。返回的任务句柄需通过[ffrt_task_handle_destroy](capi-task-h.md#ffrt_task_handle_destroy)销毁。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_function_t](capi-type-def-h.md#ffrt_function_t) func | 待执行的任务函数。 |
| void* arg | 指向传递给任务函数的参数或闭包数据的指针。 |
| [const ffrt_deps_t](capi-ffrt-ffrt-deps-t.md)* in_deps | 指向输入依赖的指针。 |
| [const ffrt_deps_t](capi-ffrt-ffrt-deps-t.md)* out_deps | 指向输出依赖的指针。 |
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | 指向任务属性的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FFRT_C_API [ffrt_task_handle_t](capi-ffrt-ffrt-task-handle-t.md) | 任务提交成功时返回非空的任务句柄；<br>         否则返回空指针。 |

**参考：**

[ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base)


### ffrt_task_handle_inc_ref()

```c
FFRT_C_API uint32_t ffrt_task_handle_inc_ref(ffrt_task_handle_t handle)
```

**描述**

增加任务句柄的引用计数。任务句柄的引用计数加一，并返回增加前的引用计数值。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_task_handle_t](capi-ffrt-ffrt-task-handle-t.md) handle | 任务句柄，由[ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base)或[ffrt_submit_h_f](capi-task-h.md#ffrt_submit_h_f)返回。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FFRT_C_API uint32_t | 任务句柄增加前的引用计数值；若`handle`为null则返回`UINT_MAX`。 |

### ffrt_task_handle_dec_ref()

```c
FFRT_C_API uint32_t ffrt_task_handle_dec_ref(ffrt_task_handle_t handle)
```

**描述**

减少任务句柄的引用计数。任务句柄的引用计数减一，并返回减少前的引用计数值。本接口应与[ffrt_task_handle_inc_ref](capi-task-h.md#ffrt_task_handle_inc_ref)配对使用，句柄不再使用时需通过[ffrt_task_handle_destroy](capi-task-h.md#ffrt_task_handle_destroy)销毁。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_task_handle_t](capi-ffrt-ffrt-task-handle-t.md) handle | 任务句柄。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FFRT_C_API uint32_t | 任务句柄减少前的引用计数值；若`handle`为null则返回`UINT_MAX`。 |

### ffrt_task_handle_destroy()

```c
FFRT_C_API void ffrt_task_handle_destroy(ffrt_task_handle_t handle)
```

**描述**

销毁任务句柄。调用后，任务句柄被销毁并释放关联的资源，句柄不可再使用。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ffrt_task_handle_t](capi-ffrt-ffrt-task-handle-t.md) handle | 任务句柄。 |

### ffrt_wait_deps()

```c
FFRT_C_API void ffrt_wait_deps(const ffrt_deps_t* deps)
```

**描述**

阻塞当前任务，等待依赖任务完成后再继续执行。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ffrt_deps_t](capi-ffrt-ffrt-deps-t.md)* deps | 指向依赖任务列表的指针。阻塞当前任务，直到该依赖列表引用的所有任务执行完毕。 |

### ffrt_wait()

```c
FFRT_C_API void ffrt_wait(void)
```

**描述**

阻塞当前任务，等待所有已提交任务完成后再继续执行。

**起始版本：** 10


