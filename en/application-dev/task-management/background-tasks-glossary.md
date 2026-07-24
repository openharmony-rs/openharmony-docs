# Background Tasks Kit Glossary

<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=084bf627297e60b1f406ce34f5b473174466f7b3 translatedAt=2026-07-15T02:43:05.136Z pushedAt=2026-07-15T03:40:51.481Z -->

## C

### ContinuousTask

A type of long-running, user-perceptible background tasks, such as background music playback, navigation, and device connection. Use a continuous task to prevent the app process from being suspended.

## T

### Transient Task

A type of tasks that require high real-time performance and are not time-consuming, such as state saving and message sending. A transient task can be requested to extend the running time of an app in the background.

### Transparency Quota

A time quota management mechanism for transient tasks. An app is allocated a certain transient task quota, and once the quota is exhausted, no further transient task requests are allowed.

## W

### WorkScheduler

A deferred task scheduling mechanism provided by the system for tasks that do not require high real-time performance and can be executed with a delay. When conditions are met, the system schedules and launches the app based on factors such as memory and power consumption.

### WorkSchedulerExtensionAbility

The callback extension capability for deferred tasks, which implements the [onWorkStart](../reference/apis-backgroundtasks-kit/js-apis-WorkSchedulerExtensionAbility.md#onworkstart) and [onWorkStop](../reference/apis-backgroundtasks-kit/js-apis-WorkSchedulerExtensionAbility.md#onworkstop) methods to handle the start and end callbacks of deferred tasks.