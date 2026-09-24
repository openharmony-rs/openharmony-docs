# FFRT

## Overview

Provides Function Flow Runtime (FFRT) C APIs.<br> FFRT is a task-based concurrent runtime library that automatically schedules tasks according to their dependencies, eliminating the need for manual thread management.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

## Files

| Name | Description |
| -- | -- |
| [condition_variable.h](capi-condition-variable-h.md) | Declares the condition variable interfaces in C. |
| [queue.h](capi-queue-h.md) | Declares the queue interfaces in C. |
| [loop.h](capi-loop-h.md) | Declares the event loop interfaces in C. |
| [type_def.h](capi-type-def-h.md) | Declares common types. |
| [task.h](capi-task-h.md) | Declares the FFRT task C APIs, including task attribute initialization and destruction, task QoS configuration, task delay time management, concurrent queue task priority management, task stack size management, task submission and scheduling, task handle reference counting, and task wait operations. |
| [mutex.h](capi-mutex-h.md) | Declares the mutex interfaces in C, which provide mutual exclusion between concurrent tasks to protect shared resources from race conditions. |
| [timer.h](capi-timer-h.md) | Declares the timer interfaces in C.<br> Provides timer capabilities based on QoS levels, supporting callback execution after a specified timeout. It can be used for delayed task scheduling and other scenarios. |
| [sleep.h](capi-sleep-h.md) | Declares the {@link ffrt_usleep} and {@link ffrt_yield} interfaces in C. |
| [shared_mutex.h](capi-shared-mutex-h.md) | Declares the shared mutex interfaces in C. |
| [fiber.h](capi-fiber-h.md) | Declares the fiber interfaces in C.<br> A fiber is a lightweight user-mode thread that enables efficient task scheduling and context switching in user space. |
