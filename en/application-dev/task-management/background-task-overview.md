# About This Kit

<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=2f4b89223ea807a0581c60a9a81b8de70ba28fa9 translatedAt=2026-10-08T08:57:21.302Z pushedAt=2026-10-08T09:16:42.786Z -->

## Introduction

Operations such as returning to the home screen, locking the screen, and switching applications cause an application to move to the background. After an application moves to the background, if it continues running in the background, it may cause the device to consume power quickly and the UI to become sluggish. To reduce power consumption and ensure a smooth user experience, the system manages applications that have moved to the background, including [process](../application-models/process-model-overview.md) suspension and process termination. Typical scenarios include: after an application moves to the background for a period of time, its application process is suspended; when resources are insufficient, the system terminates some application processes (that is, reclaims all resources of those processes). After an application process is suspended, it cannot use software resources (such as common events and timers) or hardware resources (such as the CPU, network, GPS, and Bluetooth).<!--RP2--><!--RP2End-->

To ensure that background functionalities such as music playback and calendar reminders can be used properly, Background Tasks Kit provides some background tasks within the specifications, extending the running time of applications in the background. <!--Del-->For system applications, Background Tasks Kit also supports [device usage statistics](../device-usage-statistics/device-usage-statistics-overview-sys.md), including statistics on the application usage duration.<!--DelEnd-->

## Constraints
Resource usage: The system provides resource quotas for running processes, including the memory usage and <!--RP3-->CPU usage<!--RP3End--> in a continuous period of time, and disk write I/O volume in 24 hours. When the quota is reached, the system generates a warning-level log if the process is running in the foreground, and terminates the process if it is running in the background.


## Background Task Types

Background Tasks Kit provides the following types of constrained background tasks: transient tasks, continuous tasks, deferred tasks, agent-powered reminders<!--Del-->, and efficiency resources<!--DelEnd-->.

You can select a proper background task type to ensure that your application can continue running after switching to the background.

- **Transient tasks**: suitable for tasks that require high real‑time performance and are short in duration, for example, quickly saving a note that the user is editing.

- **Continuous task**: suitable for user‑perceivable tasks that need to run for an extended period in the background, such as background music playback, navigation, and device connection. These tasks prevent the application process from being suspended.

- **Deferred tasks**: suitable for tasks that do not have high requirements on real-time performance and can be executed at a later time. The system enqueues these tasks and schedules them in a unified manner based on the memory and power consumption.

- **Agent-powered reminders**: After an application is switched to the background or an application process is terminated, the system sends a reminder on behalf of the application. You can create scheduled reminders for countdown timers, calendar events, and alarm clocks.

<!--Del-->
For system applications that provide basic capabilities, the system provides an API for [energy resource request](efficiency-resource-request-sys.md). After an application calls the API, the system exempts the application from management.<!--DelEnd-->

  **Figure 1** Selecting a type of background task
![bgtask_choice](figures/bgtask_choice.png)


> **NOTE**
>
> 1. The system supports only constrained background tasks. If an application does not use a constrained background task or selects an inappropriate type of background task after switching to the background, its process will be suspended or terminated.
> 
> 2. For an application that requests a constrained background task, only the priority of reclaiming the application process is increased. If system resources are severely insufficient, the application process may still be terminated.

<!--RP4--><!--RP4End-->