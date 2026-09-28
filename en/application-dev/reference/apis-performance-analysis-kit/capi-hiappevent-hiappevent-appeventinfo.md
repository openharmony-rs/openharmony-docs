# HiAppEvent_AppEventInfo

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @liujiaxing2024-->
<!--Designer: @jiangwenhao-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=2f60b87a09259ca058c0c6434a21fab631b01f26 translatedAt=2026-09-21T02:20:56.688Z pushedAt=2026-09-22T01:29:30.356Z -->

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
| const char* domain | Event domain. It indicates the business domain or functional module to which the event belongs, used for event classification and management. |
| const char* name | Event name. It is used together with **domain** to uniquely identify a specific event. |
| enum [EventType](capi-hiappevent-h.md#eventtype) type | Event type.|
| const char* params | Event parameter list in JSON format string. |


