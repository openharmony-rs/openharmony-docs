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
| const char* domain | Event domain: indicates the service domain or functional module to which an event belongs, which is used for event classification and management.<br>**Since**: 12 |
| const char* name | Event name, which is used together with domain to uniquely identify an event.<br>**Since**: 12 |
| enum [EventType](capi-hiappevent-h.md#eventtype) type | Indicates the type of the event.<br>**Since**: 12 |
| const char* params | List of event parameters in JSON string format.<br>**Since**: 12 |


