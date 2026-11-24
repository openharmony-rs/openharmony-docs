# OH_HiAppEvent_ExternalLog

```c
typedef struct OH_HiAppEvent_ExternalLog {...} OH_HiAppEvent_ExternalLog
```

## Overview

This structure is used to describe external log information, including the file path, generation timestamp, file size, and system event type.

<!--Device-struct OH_HiAppEvent_ExternalLog {...}--><!--Device-struct OH_HiAppEvent_ExternalLog {...}-End-->

**System capability**: SystemCapability.HiviewDFX.HiAppEvent

**Since**: 26.0.1

**Related module**: [HiAppEvent](capi-performance-analysis-kit-hiappevent.md)

**Header file**: [hiappevent.h](capi-hiappevent-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char* filePath | Log file path.<br>**Since**: 26.0.1<br><!--Device-const char* filePath--><!--Device-const char* filePath-End--> |
| long long generationTs | Timestamp when a file is generated, in ms.<br>**Since**: 26.0.1<br><!--Device-long long generationTs--><!--Device-long long generationTs-End--> |
| long fileSize | File size in KB.<br>**Since**: 26.0.1<br><!--Device-long fileSize--><!--Device-long fileSize-End--> |
| [OH_HiAppEvent_SysEvent](capi-hiappevent-h.md#oh_hiappevent_sysevent) event | System event type.<br>**Since**: 26.0.1<br><!--Device-OH_HiAppEvent_SysEvent event--><!--Device-OH_HiAppEvent_SysEvent event-End--> |


