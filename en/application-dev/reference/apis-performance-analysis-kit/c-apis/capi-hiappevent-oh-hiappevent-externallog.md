# OH_HiAppEvent_ExternalLog

```c
typedef struct OH_HiAppEvent_ExternalLog {...} OH_HiAppEvent_ExternalLog
```

## Overview

The OH_HiAppEvent_ExternalLog structure is used to describe external log information, including the file path, the generation timestamp, file size, and type of system event.

**Since**: 26.1.0

**Related module**: [HiAppEvent](capi-hiappevent.md)

**Header file**: [hiappevent.h](capi-hiappevent-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char* filePath |  |
| long long generationTs |  |
| long fileSize |  |
| [OH_HiAppEvent_SysEvent](capi-hiappevent-h.md#oh_hiappevent_sysevent) event |  |


