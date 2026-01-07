# hiappevent_event.h

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @liujiaxing2024-->
<!--Designer: @junjie_shi-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

## Overview

Defines the names of all predefined events. In addition to custom events associated with specific applications, you can use predefined events for logging.

**File to include**: <hiappevent/hiappevent_event.h>

**Library**: libhiappevent_ndk.z.so

**System capability**: SystemCapability.HiviewDFX.HiAppEvent

**Since**: 8

**Related module**: [HiAppEvent](capi-hiappevent.md)

## Summary

### Macros

| Name| Description|
| -- | -- |
| [EVENT_USER_LOGIN](#event_user_login) "hiappevent.user_login"                                              | User login event.<br>**Since**: 8       |
| [EVENT_USER_LOGOUT](#event_user_logout) "hiappevent.user_logout"                                           | User logout event.<br>**Since**: 8       |
| [EVENT_DISTRIBUTED_SERVICE_START](#event_distributed_service_start) "hiappevent.distributed_service_start" | Distributed service event.<br>**Since**: 8      |
| [EVENT_APP_CRASH](#event_app_crash) "APP_CRASH"                                                            | Crash event.<br>**Since**: 12      |
| [EVENT_APP_FREEZE](#event_app_freeze) "APP_FREEZE"                                                         | Application freeze event.<br>**Since**: 12      |
| [EVENT_APP_LAUNCH](#event_app_launch) "APP_LAUNCH"                                                         | Time-consuming launch event.<br>**Since**: 12      |
| [EVENT_SCROLL_JANK](#event_scroll_jank) "SCROLL_JANK"                                                      | Scrolling frame loss event.<br>**Since**: 12    |
| [EVENT_CPU_USAGE_HIGH](#event_cpu_usage_high) "CPU_USAGE_HIGH"                                             | High CPU usage event.<br>**Since**: 12|
| [EVENT_BATTERY_USAGE](#event_battery_usage) "BATTERY_USAGE"                                                | Battery usage statistics event.<br>**Since**: 12   |
| [EVENT_RESOURCE_OVERLIMIT](#event_resource_overlimit) "RESOURCE_OVERLIMIT"                                 | Resource leak event.<br>**Since**: 12    |
| [EVENT_ADDRESS_SANITIZER](#event_address_sanitizer) "ADDRESS_SANITIZER"                                    | Address sanitizer event.<br>**Since**: 12     |
| [EVENT_MAIN_THREAD_JANK](#event_main_thread_jank) "MAIN_THREAD_JANK"                                       | Main thread jank event.<br>**Since**: 12   |
| [EVENT_APP_HICOLLIE](#event_app_hicollie) "APP_HICOLLIE"                                                   | Task execution timeout event.<br>**Since**: 18  |
| [EVENT_APP_KILLED](#event_app_killed) "APP_KILLED"                                                         | Application killed event.<br>**Since**: 20     |
| [EVENT_AUDIO_JANK_FRAME](#event_audio_jank_frame) "AUDIO_JANK_FRAME"                                       | Audio jank event.<br>**Since**: 21     |
| [DOMAIN_OS](#domain_os) "OS"                                                                               | OS scope.<br>**Since**: 12       |
| [EVENT_MAIN_THREAD_JANK_V2](#event_main_thread_jank_v2) "MAIN_THREAD_JANK_V2"                              | Sets the main thread jank event configuration policy.<br>**Since**: 22   |

## Macro Description

### EVENT_USER_LOGIN

```c
#define EVENT_USER_LOGIN "hiappevent.user_login"
```

**Description**

User login event.

**Since**: 8

### EVENT_USER_LOGOUT

```c
#define EVENT_USER_LOGOUT "hiappevent.user_logout"
```

**Description**

User logout event.

**Since**: 8

### EVENT_DISTRIBUTED_SERVICE_START

```c
#define EVENT_DISTRIBUTED_SERVICE_START "hiappevent.distributed_service_start"
```

**Description**

Distributed service event.

**Since**: 8

### EVENT_APP_CRASH

```c
#define EVENT_APP_CRASH "APP_CRASH"
```

**Description**

Crash event.

**Since**: 12

### EVENT_APP_FREEZE

```c
#define EVENT_APP_FREEZE "APP_FREEZE"
```

**Description**

Application freeze event.

**Since**: 12

### EVENT_APP_LAUNCH

```c
#define EVENT_APP_LAUNCH "APP_LAUNCH"
```

**Description**

Time-consuming launch event.

**Since**: 12

### EVENT_SCROLL_JANK

```c
#define EVENT_SCROLL_JANK "SCROLL_JANK"
```

**Description**

Scrolling frame loss event.

**Since**: 12

### EVENT_CPU_USAGE_HIGH

```c
#define EVENT_CPU_USAGE_HIGH "CPU_USAGE_HIGH"
```

**Description**

High CPU usage event.

**Since**: 12

### EVENT_BATTERY_USAGE

```c
#define EVENT_BATTERY_USAGE "BATTERY_USAGE"
```

**Description**

Battery usage statistics event.

**Since**: 12

### EVENT_RESOURCE_OVERLIMIT

```c
#define EVENT_RESOURCE_OVERLIMIT "RESOURCE_OVERLIMIT"
```

**Description**

Resource leak event.

**Since**: 12

### EVENT_ADDRESS_SANITIZER

```c
#define EVENT_ADDRESS_SANITIZER "ADDRESS_SANITIZER"
```

**Description**

Address sanitizer event.

**Since**: 12

### EVENT_MAIN_THREAD_JANK

```c
#define EVENT_MAIN_THREAD_JANK "MAIN_THREAD_JANK"
```

**Description**

Main thread jank event.

**Since**: 12

### EVENT_APP_HICOLLIE

```c
#define EVENT_APP_HICOLLIE "APP_HICOLLIE"
```

**Description**

Task execution timeout event.

**Since**: 18

### EVENT_APP_KILLED

```c
#define EVENT_APP_KILLED "APP_KILLED"
```

**Description**

Application killed event.

**Since**: 20

### EVENT_AUDIO_JANK_FRAME

```c
#define EVENT_AUDIO_JANK_FRAME "AUDIO_JANK_FRAME"
```

**Description**

Audio jank event.

**Since**: 21

### DOMAIN_OS

```c
#define DOMAIN_OS "OS"
```

**Description**

OS scope.

**Since**: 12

### EVENT_MAIN_THREAD_JANK_V2

```c
#define EVENT_MAIN_THREAD_JANK_V2 "MAIN_THREAD_JANK_V2"
```

**Description**

Sets the main thread jank event configuration policy.

**Since**: 22
