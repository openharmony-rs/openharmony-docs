# Overview of Multithreaded Development
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @huanghello-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=ef97b4f4e99b757e3a4cb9958ae751b6d982f951 translatedAt=2026-11-04T09:25:30.388Z pushedAt=2026-11-04T09:36:46.013Z nl=1 -->

In ArkTS application development, different service scenarios require different concurrency capabilities and task types.

There are three types of concurrent tasks in common service scenarios:

[Time-consuming tasks](time-consuming-task-overview.md): These involve significant computation or multiple I/O operations and take a long time to execute.

[Continuous tasks](long-time-task-overview.md): These include tasks like listening or periodically collecting data that need to run continuously over extended periods.

[Resident tasks](resident-task-overview.md): These are bound to the lifecycle of the main thread or closely integrated with it.

Different task types can be further classified. For example, time-consuming tasks can be CPU intensive, I/O intensive, or synchronous, each corresponding to different service scenarios. TaskPool and Worker both support multithreaded concurrency. You can select the concurrency capability as required. For details, see [Use Case Comparison](taskpool-vs-worker.md#use-case-comparison).

The following sections will list common scenarios and examples in multithreaded development.
