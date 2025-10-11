# App Killed Detection

## Overview

An application crash refers to the unexpected exit of the application during use. When an app behaves abnormally, for example, consuming too many system resources such as CPU and memory, the system selects the app for control according to rules to keep the device in a healthy state. Generally, the system sends the SIGKILL signal (signal value: 9) to the app through the service process to terminate the app. By default, the OS does not generate maintenance and debugging information such as stack logs for the **SIGKILL** behavior. As a result, no log is generated in the faultLogger when the application crashes.

## Basic Concepts

An application exits in the following scenarios:

1. When an application is abnormal or throws an exception, for example, the **CPP_CRASH** exception triggered by **SIGSEGV** or **SIGABRT**, the system monitors the exception and record maintenance and debugging logs.

2. When a user manually terminates an application, for example, by clicking the clear button in the task list to clear all applications or swiping up to clear an application, no stack or other maintenance and debugging logs are generated.

3. When **exit** is called, maintenance and debugging logs such as stack logs are not generated.

4. When the application main thread is blocked, the UI freezes and the **APP_FREEZE** log is generated.

5. If resources are overused, the system controls the app and provides detailed maintenance and test information. For example, when memory leaks occur in an application, the corresponding maintenance and debugging logs are generated. You can subscribe to RESOURCE_OVERLIMIT through HiAppEvent to obtain the corresponding events and logs.

6. When the system controls an app, detailed maintenance and test information cannot be provided in some scenarios, for example, LowMemoryKiller, RSS memory of the app exceeds 4 GB, and quick leakage.

This section describes the app termination caused by the SIGKILL signal in scenarios 5 and 6.

## Implementation Principles

1. Both the kernel and service processes monitor system resources.

2. After detecting an exception, the system selects an app for control.

3. When the system triggers control and terminates an app, it adds system event dotting.

4. The dotting event contains the UID, package name, foreground/background information, termination cause, and maintenance and test information.

## Constraints

1. An app can receive termination events only after subscribing to HiAppEvent.

2. Termination events are sent to the app asynchronously. The app can receive the events only when it is started next time.

3. The system management and control behavior will be continuously added with the version evolution. The current management and control mechanism may not be the complete one.

## Triggering Scenario

The system stops an application in the following scenarios:

1. The memory, CPU, and I/O load of the application exceeds the specified limit, and the number of file handles and threads exceeds the threshold.

2. When the memory of the entire system is low, the system stops the application based on the memory usage and priority.

3. Power-consuming scenarios include frequent wake-ups caused by Binder calls, system freezes during audio playback or recording, and abnormal use of peripherals such as GPS or Bluetooth.

## Detection Methods

An application can detect that it is abnormally stopped in either of the following ways:

1. Obtain the termination cause from the onCreate callback parameter of the ability. Specifically, set the **LastExitReason** parameter in **LaunchParam**. For details, see [LastExitReason](../reference/apis-ability-kit/js-apis-app-ability-abilityConstant.md#lastexitreason).

2. Subscribe to the **APP_KILLED** event through HiAppEvent. For details, see [HiAppEvent](hiappevent-watcher-app-killed-events.md).

## Analysis Method and Procedure

1. Obtain the termination cause from the onCreate callback parameter of the ability.

    For details, see the following table.

    | lastExitReason(enum) | lastExitMessage(string)  | Causes                                            | Handling Policy                                                    |
    | -------------------- | ------------------------ | ---------------------------------------------------- | ------------------------------------------------------------ |
    | APP_FREEZE           | APP_FREEZE               | The application exits because watchdog detects that the application is frozen.| Subscribe to the **APP_FREEZE** event through HiAppEvent and match its fault types.|
    | RESOURCE_CONTROL     | CPU Highload             | The CPU load is high.                                         | Reduce the CPU load of the application.                                 |
    | RESOURCE_CONTROL     | CPU_EXT Highload         | Fast CPU load detection.                                   | Reduce the CPU load of the application.                                 |
    | RESOURCE_CONTROL     | IO Manager Control       | I/O manager control.                                           | Reduce the I/O of the application.                                     |
    | RESOURCE_CONTROL     | App Memory Deterioration | The application memory usage exceeds the threshold.                                  | Subscribe to **RESOURCE_OVERLIMIT** through HiAppEvent to obtain more logs.      |
    | RESOURCE_CONTROL     | Temperature Control      | Temperature control.                                          | Reduce the CPU load of the application.                                 |
    | RESOURCE_CONTROL     | Memory Pressure          | The low memory of the device triggers the termination. The app is terminated based on the priority from low to high.                | Reduce the memory usage of the app to reduce the probability of being selected by the device management policy.|

2. Subscribe to the **APP_KILLED** event through HiAppEvent.

    Obtain key information such as the termination cause and app foreground/background status based on the APP_KILLED event. Handle the event according to the following table.

    | reason(string)                | Causes                                                    | Handling Policy                                                    | Whether Control Is Triggered by Application Exceptions| Whether There Are Associated Events|
    | ----------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------ | -------------- |
    | LowMemoryKill                 | Same as the scenario where the value of lastExitMessage is Memory Pressure. That is, the low memory of the device triggers the termination. The app is terminated based on the priority from low to high.| Reduce the memory usage of the app to reduce the probability of being selected by the device termination policy.| No                      | No            |
    | SwapFull                      | The swap space is almost used up, which may be caused by memory leaks of some processes or too many background processes.| Reduce the memory usage of the app to reduce the probability of being selected by the device management policy.| No                      | No            |
    | ResourceLeak(IonLeak)         | The ION memory used by the application exceeds the threshold.                                     | Subscribe to **RESOURCE_OVERLIMIT** through HiAppEvent to obtain more ION memory logs. After finding the leak point, reduce the ION memory usage of the application. Generally, the leak is caused by the **Image** component or pixmap.| Yes                      | Yes            |
    | ResourceLeak(GpuRsLeak)       | The GPU memory used by the ArkUI component of the application in the **render_service** process exceeds the threshold.  | Reduce the GPU memory usage of the ArkUI component of the application.                        | Yes                      | No            |
    | ResourceLeak(GpuLeak)         | The GPU memory used by the application in the process (that is, the GPU memory generated by self-rendering) exceeds the threshold.  | Subscribe to **RESOURCE_OVERLIMIT** through HiAppEvent to obtain more GPU memory logs, find the leak point, and reduce the GPU memory usage of the application self-rendering (using the **XComponent** component).| Yes                      | Yes            |
    | ResourceLeak(AshmemLeak)      | The ashmem memory used by the application exceeds the threshold.                                  | Subscribe to **RESOURCE_OVERLIMIT** through HiAppEvent to obtain more ashmem memory logs. After finding the leak point, reduce the ashmem memory usage of the application. Generally, the leak is caused by the **Image** component or pixmap.| Yes                      | Yes            |
    | IllegalAudioRendererBySuspend | No proper background task is applied, but a large amount of audio is played in the background.              | When the application is switched to the background, unnecessary background audio playback should be avoided or the background task should be properly used. For details, see [Background Tasks Kit](../task-management/background-task-overview.md).| Yes                      | No            |
    | PowerSaveClean                | The device is switched to the power saving mode or emergency mode.                              | No operation is required.                                                  | No                      | No            |
    | RssThresholdKiller            | The RSS memory of the application exceeds the threshold.                                   | Reduce the RSS memory usage of the application. | Yes                      | No            |
    | OomKiller                     | The device memory is low, and the kernel control is triggered. The app is terminated based on certain policies.                | Reduce the memory usage of the app to reduce the probability of being selected by the device control policy.| No                      | No            |
    | CpaKiller                     | When the memory requested by the Digital Right Management (DRM) service is insufficient, processes are terminated based on certain policies to reclaim memory.| Reduce the memory usage of the app to reduce the probability of being selected by the device control policy.| No                      | No            |
