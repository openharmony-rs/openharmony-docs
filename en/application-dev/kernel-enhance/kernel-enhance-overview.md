# About This Kit

<!--Kit: Kernel Enhance Kit-->
<!--Subsystem: Kernel-->
<!--Owner: @gatieme; @fang-jinxu; @yzl-kongzhenhua-->
<!--Designer: @tanyihua; @lingminghw; @wangxiayang; @lizongfeng; @zzzuo-->
<!--Tester: @panny060; @RayShih; @lianxuanself; @laonie666-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=444d4b7458e1317b3c2f1a471488b9c4b8344c2e translatedAt=2026-06-03T06:18:46.199Z pushedAt=2026-06-03T09:55:56.953Z -->

## Feature Introduction

Kernel Enhance Kit provides kernel enhancement capabilities for developers, including Quality of Service (QoS) scheduling, Purgeable memory management, and Gewu service for on-device inference, helping developers optimize application performance, resource management, and user experience.

- **QoS**: Provides task priority scheduling capabilities. Developers can set different QoS levels for tasks based on their importance and relevance to user interaction. The system allocates CPU time and scheduling order according to the QoS level, optimizing application response speed and resource utilization.

- **Purgeable memory**: Provides a memory management mechanism that allows memory to be discarded at any time, used for storing data that can be easily reconstructed through recalculation. This mechanism can directly release such memory when the system is low on memory, and reconstruct it when the user accesses it again. It is suitable for storing large blocks of data with low reconstruction costs.

- **Gewu service**: Provides QoS-aware on-device inference acceleration and resource management optimization capabilities. Targeting challenges in on-device inference scenarios such as limited memory resources, constrained computing power, and sensitivity to power consumption, it offers features like dynamic on-demand resource loading and inference acceleration, ensuring a superior user experience while achieving efficient inference.

## Basic Concepts

### QoS

QoS (Quality of Service) refers to the priority scheduling attributes of tasks in OpenHarmony. Developers can use QoS to categorize the work to be performed, indicating its degree of relevance to user interaction; the system then arranges the execution time and order of each task based on the QoS set for the task.

OpenHarmony defines 6 QoS levels, with the degree of relevance to user interaction decreasing from high to low:

| QoS Level | Usage Scenario | Load Characteristics |
| -------- | -------- | -------- |
| QOS_BACKGROUND | Background tasks invisible to users, such as data synchronization and backup | Task completion takes minutes or even hours |
| QOS_UTILITY | Tasks that do not require immediate visible response, such as downloading or importing data | Task completion takes seconds to minutes |
| QOS_DEFAULT | Default | Task completion takes a few seconds |
| QOS_USER_INITIATED | Tasks triggered by users with visible progress, such as opening a document | Task is completed within seconds |
| QOS_DEADLINE_REQUEST | Critical tasks where faster is better, such as page loading | Task is completed almost instantly |
| QOS_USER_INTERACTIVE | User interaction tasks (UI thread, refreshing interface, animations) | Task is instantaneous |

### Purgeable Memory

Purgeable Memory refers to memory regions that can be discarded at any time, used to store data that can be easily reconstructed through recomputation. This data can be directly released when the system is low on memory and reconstructed when the user accesses it again. Purgeable Memory is suitable for storing large blocks (at least 4K) of data with low recovery cost. It is reclaimed with priority when the system is under high memory pressure (using a drop approach similar to file pages for anonymous pages, rather than compression), and users need to restore the data themselves before using it again.

### Gewu Service

Gewu Service is a QoS-aware inference acceleration and resource management optimization service for on-device inference scenarios. On-device inference scenarios offer advantages such as guaranteed user data privacy, low deployment costs, low latency, and high availability unaffected by network conditions, but they also face challenges including constrained memory resources, limited computing power, and sensitivity to power consumption. Gewu Service achieves efficient inference while ensuring user experience through optimization methods such as dynamic on-demand resource loading and QoS-aware scheduling.

## Feature Effects

### QoS Optimization Results

Proper use of QoS can significantly improve application performance:

- **Thread execution optimization**: By setting appropriate QoS levels for critical threads, you can reduce thread waiting time, increase the proportion of running time, and reduce the proportion of preemption.

- **RN framework optimization**: After properly marking the QoS levels of critical threads in the RN framework, the performance of open-source benchmark tests improved by approximately 13%.

### Purgeable Memory Optimization Results

Purgeable Memory is reclaimed first when the system is under high pressure, effectively alleviating memory pressure:

- Suitable for storing large blocks (at least 4K) of data with low recovery cost

- Directly released instead of compressed when the system is low on memory

- Data is reconstructed by the user when needed again

### Gewu Service Optimization Results

Gewu Service provides the following optimizations for on-device inference scenarios:

- **Resource management optimization**: Dynamically loads resources on demand to avoid resource waste

- **QoS-aware scheduling**: Schedules inference tasks based on their importance to ensure user experience

- **Inference acceleration**: Improves inference efficiency through optimized resource management and scheduling

## Constraints

### QoS Usage Constraints

- The QoS interface can only set the QoS level of the current task, not the QoS level of other tasks.

### Purgeable Memory Usage Constraints

- Purgeable Memory is suitable for storing large blocks (at least 4K) of data with low recovery cost

- When using it again, users need to restore the data themselves before use

### Gewu Service Usage Constraints

- Gewu Service is supported from API version 20

- Requires the relevant dynamic link library: libqos.so

## Reference

- [QoS Development](qos-guidelines.md)

- [Purgeable Memory Development](purgeable-memory-guidelines.md)

- [Gewu Development](gewu-ndk-api-guidelines.md)