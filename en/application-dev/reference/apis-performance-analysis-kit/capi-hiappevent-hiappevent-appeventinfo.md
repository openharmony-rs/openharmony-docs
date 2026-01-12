# HiAppEvent_AppEventInfo

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @liujiaxing2024-->
<!--Designer: @junjie_shi-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

```c
typedef struct HiAppEvent_AppEventInfo {...} HiAppEvent_AppEventInfo
```

## Overview

Defines a struct for the information about a single event, including the domain, name, type, and custom parameter list in JSON string format.

**Since**: 12

**Related module**: [HiAppEvent](capi-hiappevent.md)

**Header file**: [hiappevent.h](capi-hiappevent-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| const char* domain | Pointer to the event domain.|
| const char* name | Pointer to the event name.|
| enum [EventType](capi-hiappevent-h.md#eventtype) type | Event type.|
| const char* params | Event parameter list in JSON format.|
