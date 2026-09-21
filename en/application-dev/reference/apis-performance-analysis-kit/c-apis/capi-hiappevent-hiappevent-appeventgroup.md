# HiAppEvent_AppEventGroup

```c
typedef struct HiAppEvent_AppEventGroup {...} HiAppEvent_AppEventGroup
```

## Overview

Defines the information of an event group, including its name, the array of event information grouped by name, and the length of the event array.

**System capability**: SystemCapability.HiviewDFX.HiAppEvent

**Since**: 12

**Related module**: [HiAppEvent](capi-hiappevent.md)

**Header file**: [hiappevent.h](capi-hiappevent-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char* name | The name of the event. |
| const struct HiAppEvent_AppEventInfo* appEventInfos | The event array which is grouped by the name. |
| uint32_t infoLen | The length of appEventInfos array. |


