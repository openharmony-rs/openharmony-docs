# HiAppEvent_AppEventInfo

```c
typedef struct HiAppEvent_AppEventInfo {...} HiAppEvent_AppEventInfo
```

## Overview

Defines a struct for the information about a single event, including the domain, name, type, and custom parameter list in JSON string format.

<!--Device-struct HiAppEvent_AppEventInfo {...}--><!--Device-struct HiAppEvent_AppEventInfo {...}-End-->

**System capability**: SystemCapability.HiviewDFX.HiAppEvent

**Since**: 12

**Related module**: [HiAppEvent](capi-performance-analysis-kit-hiappevent.md)

**Header file**: [hiappevent.h](capi-hiappevent-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char* domain | The domain of the event.<br>**Since**: 12 |
| const char* name | The name of the event.<br>**Since**: 12 |
| enum [EventType](capi-hiappevent-h.md#eventtype) type | The type of the event.<br>**Since**: 12 |
| const char* params | The JSON string of the parameter.<br>**Since**: 12 |


