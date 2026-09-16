# ffrt_function_header_t

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct {...} ffrt_function_header_t
```

## 概述

任务执行体，用于定义任务的执行和销毁回调。`exec`回调在任务被调度时调用，`destroy`回调在任务完成后被调用以释放任务相关资源。两者共同管理FFRT任务的完整生命周期。

**起始版本：** 10

**相关模块：** [FFRT](capi-ffrt.md)

**所在头文件：** [type_def.h](capi-type-def-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [ffrt_function_t](capi-type-def-h.md#ffrt_function_t) exec | 执行任务的函数。在任务被调度时由框架调用。 |
| [ffrt_function_t](capi-type-def-h.md#ffrt_function_t) destroy | 销毁任务的函数。在任务执行完毕后由框架调用以释放资源。 |
| uint64_t reserve[2] | 保留字段。需设置为0。 |


