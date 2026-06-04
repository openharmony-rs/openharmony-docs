# QoS Development

<!--Kit: Kernel Enhance Kit-->
<!--Subsystem: Kernel-->
<!--Owner: @yzl-kongzhenhua; @Leibobo-->
<!--Designer: @wangxiayang; @lizongfeng; @zzzuo-->
<!--Tester: @lianxuanself; @laonie666-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=444d4b7458e1317b3c2f1a471488b9c4b8344c2e translatedAt=2026-06-03T06:21:07.928Z pushedAt=2026-06-03T09:55:42.275Z -->

## When to Use

Since the advent of multiprogramming and multitasking operating systems, limited system resources such as CPU and memory have become the objects of competition among all tasks in the system. Properly arranging the response speed and resource consumption of each task is of great significance to the system. Compared with the operating system, developers are more aware of the importance of each task in an application. Classifying application tasks based on their importance can help the system better schedule tasks. Through this guide, developers can learn how to use QoS features and related interfaces in the OpenHarmony system to adjust the allocation of task runtime in the system.

This document guides developers on how to customize the priority scheduling attributes of application tasks based on QoS features.

## Basic Concepts

### QoS

QoS (Quality of Service) refers to the priority scheduling attributes of tasks in OpenHarmony. Developers can use QoS to categorize the work to be performed, indicating its degree of relevance to user interaction. The system can then schedule the execution time and order of tasks based on their assigned QoS. For example, when multiple tasks need to be executed simultaneously in the system, some background download tasks with low relevance to user interaction can be postponed to a later time and allocated less time per execution, while tasks with obvious user perception, such as animation rendering, need to be executed immediately and allocated more execution time.

### QoS Level Definition

Currently, the OpenHarmony system defines the following six QoS levels. From top to bottom, the degree of relevance to user interaction increases progressively, making them suitable for various application scenarios and load characteristics.

| QoS Level                                                       | Application Scenario                                                         | Load Characteristics                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| QOS_BACKGROUND | Background tasks invisible to the user, such as data synchronization and backup. | Task completion takes minutes or even hours. |
| QOS_UTILITY | Tasks that do not require an immediate response effect, such as downloading or importing data. | Task completion takes seconds to minutes. |
| QOS_DEFAULT | Default. | Task completion takes a few seconds. |
| QOS_USER_INITIATED | Tasks triggered by the user with visible progress, such as opening a document. | Task is completed within a few seconds. |
| QOS_DEADLINE_REQUEST | Critical tasks where faster is better, such as page loading. | Task is completed almost instantly. |
| QOS_USER_INTERACTIVE | User interaction tasks (UI thread, refreshing the interface, animations). | Task is instantaneous. |

The QoS level is defined as the enum type QoS_Level, as shown in the table above; the enum values are defined as follows.

### QoS_Level Declaration

```{.c}
typedef enum QoS_Level {
    /**     * Applicable to background tasks that are invisible to users, such as data synchronization.
     */
    QOS_BACKGROUND,
    /**     * Applicable to tasks that do not require immediate response effects, such as downloads.
     */
    QOS_UTILITY,
    /**     * Default QoS level.
     */
    QOS_DEFAULT,
    /**     * Applies to tasks that are user-triggered and whose progress is visible, such as opening a document.
     */
    QOS_USER_INITIATED,
    /**     * Applies to tasks where faster completion is better, such as page loading.
     */
    QOS_DEADLINE_REQUEST,
    /**     * Applies to user interaction tasks, such as animation rendering.
     */
    QOS_USER_INTERACTIVE,
} QoS_Level;

```

## Functional Effects

Tasks with a higher QoS level may be allocated more CPU time than those with a lower level.

The following demonstrates the optimization effect of properly using QoS on program execution.

### QoS Optimization for Thread Execution

**Before Optimization**



Thread 1 and Thread 2 are two critical threads of a program. During execution, Thread 1 triggers a new task, Thread 2. After Thread 2 completes execution, it wakes up Thread 1 to continue. Before the QoS levels of these two threads were marked, their execution priority was lower than that of Thread 3 and Thread 4. At this point, the execution of Thread 1 and Thread 2 is shown in the figure above:

1. Thread 1 waits to be woken up by Thread 2, but Thread 2 has low priority and is preempted for a long time, causing Thread 1 to sleep for an extended period;

2. Thread 1 has low priority, and after being woken up, it waits a long time to run;

3. Thread 1 has low priority and is preempted by other threads for a long time during its execution.

**After Optimization**



After properly marking the QoS levels of Thread 1 and Thread 2, the execution optimization effect of the two threads is shown in the figure above:

1. The proportion of Thread 2's running time increases, and the waiting time of Thread 1 decreases;

2. After Thread 1 is woken up by Thread 2, its waiting time decreases;

3. The actual running proportion of Thread 1 increases, and the preemption ratio decreases.

### QoS Optimization for the RN Framework

After properly marking the QoS levels of key threads in the RN framework, as shown in the table below, the performance of the open-source benchmark test improved by approximately 13%.

| Verification Scenario      | Verification Environment | Total Rendering Time |
| ----------- | ----------- | ----------- |
| benchmark<br>1500view      | Without QoS optimization       | 270.8 ms       |
| benchmark<br>1500view   | With QoS optimization        | 236.6 ms       |

## Available APIs

| Name                                                       | Description                                                         | Parameter                                                         | Return Value                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| OH_QoS_SetThreadQoS(QoS_Level level) | Sets the QoS level of the current task. | QoS_Level level | 0 or -1 |
| OH_QoS_ResetThreadQoS() | Cancels the QoS level set for the current task. | None | 0 or -1 |
| OH_QoS_GetThreadQoS(QoS_Level *level) | Gets the QoS level of the current task. | QoS_Level *level | 0 or -1 |

### Usage Restrictions

* The QoS interface can only set the QoS level of the current task.

## Function Introduction

### OH_QoS_SetThreadQoS

**Declaration**

```{.c}
int OH_QoS_SetThreadQoS(QoS_Level level);
```

**Parameters**

QoS_Level level

* This parameter is used to describe the QoS level to be set for the task.

**return value**

* Returns 0 if successful, and -1 if failed.

**Description**

Sets a specified QoS level for a task. Developers can mark different QoS levels for a task based on its importance, thereby obtaining different scheduling supplies. For details, see [QoS Practice Guidance](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-thread-priority-setting).

**Sample**

```c++
#include <stdio.h>
#include "qos/qos.h"

int func()
{
    // Set the QoS level of the current task to QOS_USER_INITIATED
    int ret = OH_QoS_SetThreadQoS(QoS_Level::QOS_USER_INITIATED);
    
    if (!ret) { // ret equal to 0 indicates that the setting is successful.
        printf("set QoS Success.");
    } else { // ret not equal to 0 indicates that the setting fails.
        printf("set QoS failed.");
    }

    return 0;
}
```

### OH_QoS_ResetThreadQoS

**Declaration**

```{.c}
int OH_QoS_ResetThreadQoS();
```

**Parameters**

* None.

**Return value**

* Returns 0 if successful, and -1 if failed.

**Description**

Cancels the QoS level set for a task. For details, see [QoS Practice Guidance](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-thread-priority-setting).

**Sample**

```c++
#include <stdio.h>
#include "qos/qos.h"

int func()
{
    // Resets the QoS level of the current task
    int ret = OH_QoS_ResetThreadQoS();
    
    if (!ret) { // If ret equals 0, the reset is successful.
        printf("reset QoS Success.");
    } else { // If ret is not equal to 0, the reset has failed.
        printf("reset QoS failed.");
    }

    return 0;
}
```

### OH_QoS_GetThreadQoS

**Declaration**

```{.c}
int OH_QoS_GetThreadQoS(QoS_Level *level);
```

**Parameters**

QoS_Level *level

* This parameter is used to store the QoS level that has been set for the task.

**return value**

* Returns 0 if successful, and -1 if failed.

**Description**

Gets the QoS level most recently set for a task. If no QoS level has been set before, -1 is returned. Checks the QoS level of the current task. For details, see [QoS Practice Guidance](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-thread-priority-setting).

**Sample**

```c++
#include <stdio.h>
#include "qos/qos.h"

int func()
{
    // Obtain the QoS level of the current task
    QoS_Level level = QoS_Level::QOS_DEFAULT;
    int ret = OH_QoS_GetThreadQoS(&level);

    if (!ret) { // If ret equals 0, the QoS level is obtained successfully.
        printf("get QoS level %d Success.", level);
    } else { // If ret is not equal to 0, the QoS level fails to be obtained.
        printf("get QoS level failed.");
    }

    return 0;
}
```

## How to Develop

The following steps describe how to use the Native API interfaces provided by the QoS feature to adjust or query the QoS level of a task.

### Adding Dynamic Link Libraries

Using the QoS feature depends on the related dynamic link library: **libqos.so**, which needs to be added to the compilation environment of the target application or program.

**Sample**

For a template NDK project created with DevEco Studio, a CMakeLists.txt script is generated by default. An example of adding the QoS-related dynamic link library to it is as follows:

```txt
# the minimum version of CMake.
cmake_minimum_required(VERSION 3.4.1)
project(qos)

set(NATIVERENDER_ROOT_PATH ${CMAKE_CURRENT_SOURCE_DIR})

include_directories(${NATIVERENDER_ROOT_PATH}
                    ${NATIVERENDER_ROOT_PATH}/include)

add_library(entry SHARED hello.cpp)

# Reason for directly referencing libqos.so: It is located in the NDK that is already in the link search path, so no additional declaration is required.
target_link_libraries(entry PUBLIC libqos.so)
```

### Referencing Header Files

The relevant header files need to be referenced in the source code that uses the QoS feature.

```c
#include "qos/qos.h"
```

### Calling QoS APIs

Developers can call the corresponding QoS interfaces based on their own needs to adjust the QoS level of a task or query the QoS level of a task.