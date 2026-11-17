---
kits: ["ArkTS / Ark Programming Language"]
description: "Overview of task classification and selection for multithreaded application development: business is divided into three categories, namely time-consuming tasks, long-running tasks, and resident tasks. Time-consuming tasks are further subdivided into CPU-intensive, I/O-intensive, and synchronous tasks, guiding developers to choose TaskPool or Worker based on the scenario."
keywords: [multithreaded development overview, time-consuming task, long-running task, resident task, CPU-intensive, I/O-intensive, synchronous task, concurrency selection]
doctype: guide
status: active
---

# Overview of Multithreaded Development
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @huanghello-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=f8431cb42cf0d545a37a384860003cd8449b0b43 translatedAt=2026-11-06T10:39:34.629Z pushedAt=2026-11-12T08:41:40.672Z nl=1 -->

In ArkTS application development, different service scenarios require different concurrency capabilities and task types.

There are three types of concurrent tasks in common service scenarios:

[Time-consuming tasks](time-consuming-task-overview.md): These involve significant computation or multiple I/O operations and take a long time to execute.

[Continuous tasks](long-time-task-overview.md): These include tasks like listening or periodically collecting data that need to run continuously over extended periods.

[Resident tasks](resident-task-overview.md): These are bound to the lifecycle of the main thread or closely integrated with it.

Different task types can be further classified. For example, time-consuming tasks can be CPU intensive, I/O intensive, or synchronous, each corresponding to different service scenarios. TaskPool and Worker both support multithreaded concurrency. You can select the concurrency capability as required. For details, see [Use Case Comparison](taskpool-vs-worker.md#use-case-comparison).

The following sections will list common scenarios and examples in multithreaded development.
