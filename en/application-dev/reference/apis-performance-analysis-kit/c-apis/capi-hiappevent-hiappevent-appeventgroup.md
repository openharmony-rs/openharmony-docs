# HiAppEvent_AppEventGroup

```c
typedef struct HiAppEvent_AppEventGroup {...} HiAppEvent_AppEventGroup
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
| const char* name | The same event name in the event array.<br>**Since**: 12<br><!--Device-const char* name--><!--Device-const char* name-End--> |
| [const struct HiAppEvent_AppEventInfo*](capi-hiappevent-hiappevent-appeventinfo.md) appEventInfos | Array of events with the same event name.<br>**Since**: 12<br><!--Device-const struct HiAppEvent_AppEventInfo* appEventInfos--><!--Device-const struct HiAppEvent_AppEventInfo* appEventInfos-End--> |
| uint32_t infoLen | Length of an array of events with the same event name.<br>**Since**: 12<br><!--Device-uint32_t infoLen--><!--Device-uint32_t infoLen-End--> |


