# Thread Model of the FA Model

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wkljy-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=72d653d33f4588226f36115e7b3ce3bd5dcf26b3 translatedAt=2026-11-23T08:43:25.490Z pushedAt=2026-11-24T09:08:01.727Z nl=1 -->

There are three types of threads in the [FA model](ability-terminology.md#fa-model):


- Main thread

  Manages other threads.

- Ability thread
  - One ability thread for each ability.
  - Distributes input events.
  - Draws the UI.
  - Invokes application code callbacks (event processing and lifecycle callbacks).
  - Receives messages sent by the worker thread.

- Worker thread

  Performs time-consuming operations.


Based on the thread model, different services run on different threads. Service interaction requires inter-thread communication. Threads can communicate with each other in [Emitter](../basic-services/common-event/itc-with-emitter.md) or [Worker](../arkts-utils/worker-introduction.md) mode. Emitter is mainly used for event synchronization between threads, and Worker is mainly used to execute time-consuming tasks.


> **NOTE**<br>
>
> The FA model provides an independent thread for each ability. Emitter is mainly used for event synchronization within the ability thread, between a pair of ability threads, or between the ability thread and worker thread.
