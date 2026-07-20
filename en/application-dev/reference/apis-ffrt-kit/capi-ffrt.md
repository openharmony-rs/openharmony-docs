# FFRT

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1bd5d6cdd22374b2fc7c67ab365167018faf622f translatedAt=2026-07-20T01:58:51.762Z pushedAt=2026-07-20T09:49:21.279Z -->

## Overview

This module provides the C APIs of Function Flow Runtime (FFRT). FFRT is a task-based concurrency runtime library that automatically schedules tasks based on their dependency relationships, eliminating the need for you to manually manage threads.

**Since**: 10

## Files

| Name| Description|
| -- | -- |
| [condition_variable.h](capi-condition-variable-h.md) | Declares the C APIs for condition variables.|
| [fiber.h](capi-fiber-h.md) | Declares the C APIs for fibers.<br>A fiber is a lightweight user-mode thread used to implement efficient task scheduling and context switching in the user space. |
| [loop.h](capi-loop-h.md) | Declares the C APIs for event loops. |
| [mutex.h](capi-mutex-h.md) | Declares the C APIs for mutexes, which provide mutually exclusive access between concurrent tasks and protect shared resources from race conditions. |
| [queue.h](capi-queue-h.md) | Declares the queue APIs in C.|
| [shared_mutex.h](capi-shared-mutex-h.md) | Declares the C APIs for read-write locks (`rwlock`). |
| [sleep.h](capi-sleep-h.md) | Declares the C APIs for [ffrt_usleep](capi-sleep-h.md#ffrt_usleep) and [ffrt_yield](capi-sleep-h.md#ffrt_yield). |
| [task.h](capi-task-h.md) | Declares the C APIs for FFRT tasks, providing functionalities including task attribute initialization and destruction, task QoS setting and retrieval, task execution submission and scheduling, task waiting, as well as management of the task delay time, concurrent queue task priorities, task stack size, and task handle reference counting. |
| [timer.h](capi-timer-h.md) | Declares the C APIs for timers.<br>They provide QoS-based timer capabilities, supporting callback execution after a specified timeout interval. The APIs are applicable to scenarios such as delayed task scheduling. |
| [type_def.h](capi-type-def-h.md) | Declares the common types.|