# HiAppEvent_AppEventInfo

```c
typedef struct HiAppEvent_AppEventInfo {...} HiAppEvent_AppEventInfo
```

## Overview

Defines a struct for the information about a single event, including the domain, name, type, and custom parameter list in JSON string format.

**System capability**: SystemCapability.HiviewDFX.HiAppEvent

**Since**: 12

**Related module**: [HiAppEvent](capi-hiappevent.md)

**Header file**: [hiappevent.h](capi-hiappevent-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char* domain | The domain of the event. |
| const char* name | The name of the event. |
| enum [EventType](capi-hiappevent-h.md#eventtype) type | The type of the event. |
| const char* params | The JSON string of the parameter. |


