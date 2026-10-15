# HiAppEvent_AppEventGroup

```c
struct HiAppEvent_AppEventGroup {...}
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
| /* The name of the event. */
    const char* name |  |
| /* The event array which is grouped by the name. */
    const struct HiAppEvent_AppEventInfo* appEventInfos |  |
| /* The length of appEventInfos array. */
    uint32_t infoLen |  |


