# Application Killed Event Overview

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @xuxinao-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

## Overview

Since API version 20, HiAppEvent provides APIs for subscribing to application killed events.

The killed event refers to a phenomenon that an application is forced to exit by the system. Unlike an application crash, an application killed event is triggered not by an exception in the application's own code, but by the system's resource-management policy.

HiAppEvent APIs for subscribing to application killed events:

- [Subscribing to Application Killed Events (ArkTS)](hiappevent-watcher-app-killed-events-arkts.md)
- [Subscribing to Application Killed Events (C/C++)](hiappevent-watcher-app-killed-events-ndk.md)

> **NOTE**
>
> Application killed events can be subscribed to using HiAppEvent in [application clones](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/app-clone) and atomic services. Since API version 22, application killed events can be subscribed to using HiAppEvent in [input method applications](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/inputmethod-application-guide).

The **params** attribute in the application killed event is described as follows.

## Field Description

### params

The **params** attribute in the application killed event is described as follows.

| Name   | Type  | Description                      |
| ------- | ------ | ------------------------- |
| time     | number | Event triggering time, in ms.|
| reason  | string | Killed reason. For details, see [reason](#reason).|
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
