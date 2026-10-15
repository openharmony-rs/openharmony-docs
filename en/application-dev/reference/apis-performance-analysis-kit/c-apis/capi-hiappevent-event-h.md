# hiappevent_event.h

## Overview

Defines the event names of all predefined events.<br> In addition to custom events associated with specific apps, you can also use predefined events for logging.<br> Sample code: <pre> ParamList list = OH_HiAppEvent_CreateParamList(); OH_HiAppEvent_AddInt32Param(list, PARAM_USER_ID, 123); int res = OH_HiAppEvent_Write("user_domain", EVENT_USER_LOGIN, BEHAVIOR, list); OH_HiAppEvent_DestroyParamList(list); </pre>

**Library**: libhiappevent_ndk.z.so

**System capability**: SystemCapability.HiviewDFX.HiAppEvent

**Since**: 8

**Related module**: [HiAppEvent](capi-hiappevent.md)

## Summary

### Macro

| Name | Description |
| -- | -- |
| HIVIEWDFX_HIAPPEVENT_EVENT_H | Defines the event names of all predefined events.<br> In addition to custom events associated with specific apps, you can also use predefined events for logging.<br> Sample code: <pre> ParamList list = OH_HiAppEvent_CreateParamList(); OH_HiAppEvent_AddInt32Param(list, PARAM_USER_ID, 123); int res = OH_HiAppEvent_Write("user_domain", EVENT_USER_LOGIN, BEHAVIOR, list); OH_HiAppEvent_DestroyParamList(list); </pre><br>**Since**: 8<br>**System capability**: SystemCapability.HiviewDFX.HiAppEvent |
| EVENT_USER_LOGIN "hiappevent.user_login" | user login event.<br>**Since**: 8 |
| EVENT_USER_LOGOUT "hiappevent.user_logout" | user logout event.<br>**Since**: 8 |
| EVENT_DISTRIBUTED_SERVICE_START "hiappevent.distributed_service_start" | distributed service event.<br>**Since**: 8 |
| EVENT_APP_CRASH "APP_CRASH" | app crash event.<br>**Since**: 12 |
| EVENT_APP_FREEZE "APP_FREEZE" | app freeze event.<br>**Since**: 12 |
| EVENT_APP_LAUNCH "APP_LAUNCH" | app launch event.<br>**Since**: 12 |
| EVENT_SCROLL_JANK "SCROLL_JANK" | app scroll jank event.<br>**Since**: 12 |
| EVENT_CPU_USAGE_HIGH "CPU_USAGE_HIGH" | app cpu usage high event.<br>**Since**: 12 |
| EVENT_BATTERY_USAGE "BATTERY_USAGE" | app battery usage event.<br>**Since**: 12 |
| EVENT_RESOURCE_OVERLIMIT "RESOURCE_OVERLIMIT" | app resource overlimit event.<br>**Since**: 12 |
| EVENT_ADDRESS_SANITIZER "ADDRESS_SANITIZER" | app address sanitizer event.<br>**Since**: 12 |
| EVENT_MAIN_THREAD_JANK "MAIN_THREAD_JANK" | app main thread jank event.<br>**Since**: 12 |
| EVENT_MAIN_THREAD_JANK_V2 "MAIN_THREAD_JANK_V2" | app main thread jank event with extended params.<br>**Since**: 22 |
| EVENT_APP_HICOLLIE "APP_HICOLLIE" | app hicollie event.<br>**Since**: 18 |
| DOMAIN_OS "OS" | OS domain.<br>**Since**: 12 |
| EVENT_APP_KILLED "APP_KILLED" | app killed event.<br>**Since**: 20 |
| EVENT_AUDIO_JANK_FRAME "AUDIO_JANK_FRAME" | audio jank frame event.<br>**Since**: 21 |
| OH_EVENT_APP_FREEZE_WARNING "APPFREEZE_WARNING" | appfreeze warning event.<br>**Since**: 26.0.0 |

