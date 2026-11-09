# HiAppEvent_AppEventGroup

```c
struct HiAppEvent_AppEventGroup {...}
```

## Overview

Defines the information of an event group, including its name, the array of event information grouped by name, and the length of the event array.

<!--Device-struct HiAppEvent_AppEventGroup {...}--><!--Device-struct HiAppEvent_AppEventGroup {...}-End-->

**System capability**: SystemCapability.HiviewDFX.HiAppEvent

**Since**: 12

**Related module**: [HiAppEvent](capi-performance-analysis-kit-hiappevent.md)

**Header file**: [hiappevent.h](capi-hiappevent-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char* name | The name of the event.<br>**Since**: 12 |
| [const struct HiAppEvent_AppEventInfo*](capi-hiappevent-hiappevent-appeventinfo.md) appEventInfos | The event array which is grouped by the name.<br>**Since**: 12 |
| uint32_t infoLen | The length of appEventInfos array.<br>**Since**: 12 |


