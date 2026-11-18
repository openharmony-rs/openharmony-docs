# Introduction to external_log

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @liujiaxing2024-->
<!--Designer: @jiangwenhao-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=5c6e03ec7cfff0172ce10c87fa36d9c242ac74fb translatedAt=2026-10-31T06:41:24.028Z pushedAt=2026-10-31T06:41:24.028Z nl=1 -->

## Overview

Starting from API version 26.0.1, you can register an external_log manager so that the application is notified to clean up external_log files when a fault log directory in the sandbox reaches its capacity threshold.

**external_log** specifies the path of a fault log file in the application sandbox. After an application subscribes to system events through HiAppEvent, the **params** object of a triggered event contains the **external_log** field. You can use this path to read the fault log file.

A system event can have multiple subscribers. Each subscriber receives a different **external_log** path so that their operations do not affect one another. Independent log paths are provided for the first 100 subscribers. Subscribers beyond this limit share the same log path.

You can register an external_log manager using either ArkTS or C/C++ APIs.

- [Cleaning Up external_log Files (ArkTS)](external-log-arkts.md)

- [Cleaning Up external_log Files (C/C++)](external-log-ndk.md)

## Working Principles
An application subscribes to system events to obtain the corresponding external_log fault logs when those events occur. The following figure illustrates how this works:

![external-log](figures/external_log.png)

The process is as follows:
1. A system event occurs while the application is running. The DFX fault detection module triggers fault log collection.
2. The DFX system writes the generated external_log file to the application sandbox directory.
3. HiAppEvent detects the new fault log in the application sandbox directory.
4. HiAppEvent adds the **external_log** field to the system event's **params** object and returns it to the application's watcher through a callback.
5. The application uses the **external_log** field to read the fault log file.

## Log Specifications

The external_log directories include **/data/storage/el2/log/hiappevent**, **/data/storage/el2/log/watchdog**, and **/data/storage/el2/log/resourcelimit**.

For log specifications, see [System Event Fault Log Directory Specifications](./hiappevent-intro.md#system-event-fault-log-directory-specifications).

The sandbox fault log directory capacity thresholds are as follows:

1. When **/data/storage/el2/log/hiappevent/** reaches 4 MB, the application is notified to clean up external_log files.

2. When **/data/storage/el2/log/resourcelimit/** reaches 1500 MB, the application is notified to clean up external_log files.

## Constraints

Only one external_log manager can be registered. Attempting to register another manager after successful registration fails.

Registration is not persistent. The application does not retain the registration state from its previous run and must register the manager again after startup.