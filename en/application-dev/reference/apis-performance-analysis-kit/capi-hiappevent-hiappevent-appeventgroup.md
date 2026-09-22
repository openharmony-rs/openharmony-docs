# HiAppEvent_AppEventGroup

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @liujiaxing2024-->
<!--Designer: @jiangwenhao-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=7addffc63d219ad1e54baac60e90c00085674e53 translatedAt=2026-09-21T02:20:09.369Z pushedAt=2026-09-22T01:29:30.353Z -->

```c
typedef struct HiAppEvent_AppEventGroup {...} HiAppEvent_AppEventGroup
```

## Overview

Defines a group of event information used to manage and organize event information with the same name. This structure contains the name of the event group, an array of individual event information grouped by name, and the length of the event array.

**Since**: 12

**Related module**: [HiAppEvent](capi-hiappevent.md)

**Header file**: [hiappevent.h](capi-hiappevent-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| const char* name | Pointer to the event name.|
| const struct HiAppEvent_AppEventInfo* appEventInfos | Pointer to the array of events with the same event name.|
| uint32_t infoLen | Length of the event array.|


