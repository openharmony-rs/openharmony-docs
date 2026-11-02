# OH_HiAppEvent_ExternalLog

```c
struct OH_HiAppEvent_ExternalLog {...}
```

## Overview

The OH_HiAppEvent_ExternalLog structure is used to describe external log information, including the file path, the generation timestamp, file size, and type of system event.

**System capability**: SystemCapability.HiviewDFX.HiAppEvent

**Since**: 26.0.1

**Related module**: [HiAppEvent](capi-others-hiappevent.md)

**Header file**: [hiappevent.h](capi-hiappevent-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char* filePath | The log file path.<br>**Since**: 26.0.1 |
| long long generationTs | The timestamp of the file generation in ms.<br>**Since**: 26.0.1 |
| long fileSize | The file size in kb.<br>**Since**: 26.0.1 |
| [OH_HiAppEvent_SysEvent](capi-hiappevent-h.md#oh_hiappevent_sysevent) event | The system event type.<br>**Since**: 26.0.1 |


