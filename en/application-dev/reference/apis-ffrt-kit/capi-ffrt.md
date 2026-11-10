# FFRT

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1c82fe64143ca179b80fafe272ca5a84323e9159 translatedAt=2026-11-10T03:17:43.182Z pushedAt=2026-11-10T04:56:53.256Z nl=1 -->

## Overview

Provides the Function Flow Runtime (FFRT) C interface. FFRT is a task-based concurrent runtime library that automatically schedules tasks based on task dependencies, freeing developers from manual thread management.

**Since**: 10
## Files

| Name| Description|
| -- | -- |
| [condition_variable.h](capi-condition-variable-h.md) | Declares the condition variable APIs in C.|
| [fiber.h](capi-fiber-h.md) | Declares the C interfaces of fibers.<br>A fiber is a lightweight user-mode thread used to implement efficient task scheduling and context switching in user space. |
| [loop.h](capi-loop-h.md) | Declares the C interfaces of the event loop. |
| [mutex.h](capi-mutex-h.md) | Declares the C interfaces of mutexes, which are used to provide mutually exclusive access between concurrent tasks and protect shared resources from race conditions. |
| [queue.h](capi-queue-h.md) | Declares the queue APIs in C.|
| [shared_mutex.h](capi-shared-mutex-h.md) | Declares the C interfaces of read-write locks (rwlock). |
| [sleep.h](capi-sleep-h.md) | Declares the C interfaces of [ffrt_usleep](capi-sleep-h.md#ffrt_usleep) and [ffrt_yield](capi-sleep-h.md#ffrt_yield). |
| [task.h](capi-task-h.md) | Declares the C interfaces of FFRT tasks, providing functions such as initialization and destruction of task attributes, setting and obtaining of task QoS, management of task delay time, priority management of concurrent queue tasks, management of task stack size, task submission and scheduling execution, reference count management of task handles, and task waiting. |
| [timer.h](capi-timer-h.md) | Declares the C interfaces of timers.<br>Provides timer capabilities based on QoS levels, supports executing a callback function after a specified timeout, and can be used in scenarios such as delayed task scheduling. |
| [type_def.h](capi-type-def-h.md) | Declares the common types.|
