# FFRT

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1c82fe64143ca179b80fafe272ca5a84323e9159 translatedAt=2026-11-13T03:05:18.770Z pushedAt=2026-11-13T08:30:08.488Z nl=1 -->

## Overview

Provides the Function Flow Runtime (FFRT) C interface. FFRT is a task-based concurrent runtime library that automatically schedules tasks based on task dependencies, freeing developers from manual thread management.

**Since**: 10
## Files

| Name| Description|
| -- | -- |
| [condition_variable.h](capi-condition-variable-h.md) | Declares the condition variable APIs in C.|
| [fiber.h](capi-fiber-h.md) | Declares the C APIs of fibers.<br>A fiber is a lightweight user-mode thread used to implement efficient task scheduling and context switching in user space. |
| [loop.h](capi-loop-h.md) | Declares the C APIs of the event loop. |
| [mutex.h](capi-mutex-h.md) | Declares the C APIs of mutex, which are used to provide mutually exclusive access between concurrent tasks and protect shared resources from race conditions. |
| [queue.h](capi-queue-h.md) | Declares the queue APIs in C.|
| [shared_mutex.h](capi-shared-mutex-h.md) | Declares the C APIs of the read-write lock (rwlock). |
| [sleep.h](capi-sleep-h.md) | Declares the C APIs of [ffrt_usleep](capi-sleep-h.md#ffrt_usleep) and [ffrt_yield](capi-sleep-h.md#ffrt_yield). |
| [task.h](capi-task-h.md) | Declares the C APIs of FFRT tasks, providing functions such as initialization and destruction of task attributes, setting and obtaining of task QoS, task delay management, priority management of concurrent queue tasks, task stack size management, task submission and scheduled execution, task handle reference count management, and task waiting. |
| [timer.h](capi-timer-h.md) | Declares the C APIs of timers.<br>This module provides timer capabilities based on QoS levels, supports executing a callback after a specified timeout, and can be used in scenarios such as delayed task scheduling. |
| [type_def.h](capi-type-def-h.md) | Declares the common types.|
