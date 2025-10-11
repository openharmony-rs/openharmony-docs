# Application Killed Event Overview

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @shead-master-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

## Overview

From API version 20, HiAppEvent provides APIs for subscribing to app termination events.

App termination refers to the phenomenon that an app is forcibly exited by the system. Different from app crashes, app termination is not caused by exceptions in the service code of the app, but is caused by the termination behavior implemented by the system based on the resource management and control policy.

HiAppEvent provides APIs for subscribing to app termination events.

- [Subscribing to Application Killed Events (ArkTS)](hiappevent-watcher-app-killed-events-arkts.md)
- [Subscribing to Application Killed Events (C/C++)](hiappevent-watcher-app-killed-events-ndk.md)

The **params** attribute in the application termination event is described as follows:

## Field Description

### params

The **params** parameter in the event information is described as follows.

| Name   | Type  | Description                      |
| ------- | ------ | ------------------------- |
| time     | number | Event triggering time, in ms.|
| reason  | string | Termination reason. For details, see [reason](#reason).|
| foreground | boolean | Whether the application is in the foreground. The value **true** indicates that the application is in the foreground, and the value **false** indicates the opposite.|

### reason

| Type  | Description                      |
| ------- | ------------------------- |
| IllegalAudioRendererBySuspend | No proper background task is applied for the application, but a large amount of audio is played in the background.|
| LowMemoryKill | Low system memory.|
| OomKiller | The system memory is used up and cannot be allocated.|
| PowerSaveClean | The device is switched to the power saving mode or emergency mode.|
| ResourceLeak(AshmemLeak) | The Ashmem memory usage of the application exceeds the threshold.|
| ResourceLeak(GpuLeak) | The GPU memory usage of the application exceeds the threshold.|
| ResourceLeak(GpuRsLeak) | The GPU memory usage of the application in the Render Service process exceeds the threshold.|
| ResourceLeak(IonLeak) | The ION memory usage of the application exceeds the threshold.|
| RssThresholdKiller | The Resident Size Set (RSS) usage of the application exceeds the threshold.|
| SwapFull | The swap space of the system is used up.|
