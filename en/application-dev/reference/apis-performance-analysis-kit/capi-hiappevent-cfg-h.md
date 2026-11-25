# hiappevent_cfg.h

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @liujiaxing2024-->
<!--Designer: @jiangwenhao-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=aa50fb20815b673a2511068ebba01f5993136d88 translatedAt=2026-09-16T09:47:54.710Z pushedAt=2026-09-20T09:01:52.214Z -->

## Overview

Defines the configuration items of the event logging configuration function. To configure the application event logging functionality, you can directly use configuration item constants.

**File to include**: <hiappevent/hiappevent_cfg.h>

**Library**: libhiappevent_ndk.z.so

**System capability**: SystemCapability.HiviewDFX.HiAppEvent

**Since**: 8

**Related module**: [HiAppEvent](capi-hiappevent.md)

## Summary

### Macros

| Name| Description|
| -- | -- |
| [DISABLE](#disable) "disable" | Event logging switch. Default value: **false**. **true**: disables the logging function; **false**: enables the logging function.<br>**Since:** 8 |
| [MAX_STORAGE](#max_storage) "max_storage" | Event file directory storage quota size. Default value: "10MB".<br>**Since:** 8 |


## Macro Description

### DISABLE

```c
#define DISABLE "disable"
```

**Description**

Whether to disable event logging. The default value is **false**. The value **true** means to disable the event logging function, and the value **false** means the opposite.

**Since**: 8

### MAX_STORAGE

```c
#define MAX_STORAGE "max_storage"
```

**Description**

Storage quota of the event file directory. Default value: "10MB".

**Since**: 8



