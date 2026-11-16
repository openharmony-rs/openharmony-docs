---
kits: ["ArkTS"]
description: "Introduces the definition and selection of concurrency scenarios for resident tasks: a resident task can run for more than 3 minutes, is bound to a thread, and has a small concurrency volume. Typical scenarios include the main logic thread of a game middleware, background model prediction, and hardware testing. It is recommended to use Worker to execute tasks in a background thread."
keywords: [resident task, Worker, game middleware, model prediction, hardware testing, background thread, task selection]
doctype: guide
status: active
---

# Overview of Concurrency in Resident Tasks
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @huanghello-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=f8431cb42cf0d545a37a384860003cd8449b0b43 translatedAt=2026-11-06T10:41:59.733Z pushedAt=2026-11-12T09:10:09.557Z nl=1 -->

In application service development, time-consuming tasks (those lasting over 3 minutes) with low concurrency are best handled in background threads using Worker. This approach prevents such tasks from blocking the UI main thread, which could otherwise lead to performance issues such as frame loss and freezing, ultimately degrading user experience.

Persistent tasks are those that last significantly longer than transient tasks and may share the same lifecycle as the UI main thread. Unlike continuous tasks, persistent tasks are more tightly bound to their threads and typically have longer single-run durations (for example, over 3 minutes).

The following describes typical service scenarios for resident tasks.

| Service Scenario| Description|
| -------- | -------- |
| Game platform scenario| A child thread is launched to serve as the main logic thread for gaming services, whereas the UI thread is only responsible for rendering.|
| Long-duration task scenario | Long-running model prediction tasks in the background, hardware testing, and so on. |
