---
kits: ["ArkTS"]
description: "Introduces the definition and characteristics of long-time task concurrency scenarios: tasks such as periodically collecting sensor data and listening on Socket ports that need to run continuously for a long time and interact simply with the outside world are recommended to be placed in a TaskPool queue for execution to simplify lifecycle management and avoid excessive threads."
keywords: [long-time task, sensor data collection, Socket port listening, TaskPool, background thread, lifecycle management]
doctype: guide
status: active
---

# Overview of Concurrency in Continuous Tasks
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @huanghello-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=f8431cb42cf0d545a37a384860003cd8449b0b43 translatedAt=2026-11-06T10:37:23.445Z pushedAt=2026-11-12T08:29:36.155Z nl=1 -->

During the implementation of application service logic, tasks that require extended and irregular execution periods are known as continuous tasks. Executing continuous tasks in the UI main thread may block the thread's normal operations, leading to performance issues such as freezing and frame loss, which degrade user experience. Therefore, it is common practice to run these independent continuous tasks in separate child threads.

The following describes typical service scenarios for continuous tasks.


| Service Scenario| Description| 
| -------- | -------- |
| Periodic sensor data collection| Regularly collecting data of sensors (such as location and speed) that run continuously throughout the application's operation without interruption.| 
| Listening for socket port information| Continuously monitoring socket data and responding to it at irregular intervals.| 

The above service scenarios are all independent long-time tasks with long execution cycles and simple interaction with the outside. After dispatching these tasks to background threads, you can obtain their execution results as needed. Using [TaskPool](taskpool-introduction.md) can simplify development workload, avoid managing complex lifecycles, and prevent an excessive number of threads. Developers only need to place the above independent long-time tasks into the [TaskPool](taskpool-introduction.md) queue and wait for the results.
