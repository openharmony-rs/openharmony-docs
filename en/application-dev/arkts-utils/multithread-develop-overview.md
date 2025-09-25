# Overview of Multithreaded Development

In ArkTS application development, different service scenarios require different concurrency capabilities and task types.

There are three types of concurrent tasks in common service scenarios:

[Time-consuming tasks](time-consuming-task-overview.md): These involve significant computation or multiple I/O operations and take a long time to execute.

[Continuous tasks](long-time-task-overview.md): These include tasks like listening or periodically collecting data that need to run continuously over extended periods.

[Resident tasks](resident-task-overview.md): These are bound to the lifecycle of the main thread or closely integrated with it.

Different task types can be further classified. For example, time-consuming tasks can be CPU intensive, I/O intensive, or synchronous, each corresponding to different service scenarios.

The following sections will list common scenarios and examples in multithreaded development.
