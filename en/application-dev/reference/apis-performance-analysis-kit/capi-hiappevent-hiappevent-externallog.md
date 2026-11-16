# OH_HiAppEvent_ExternalLog

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @liujiaxing2024-->
<!--Designer: @jiangwenhao-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=5c6e03ec7cfff0172ce10c87fa36d9c242ac74fb translatedAt=2026-11-03T06:08:35.157Z pushedAt=2026-11-03T12:08:25.595Z nl=1 -->

```c
typedef struct OH_HiAppEvent_ExternalLog {...} OH_HiAppEvent_ExternalLog
```

## Overview

The OH_HiAppEvent_ExternalLog struct describes the external_log fault file information, including the file path, file generation timestamp, file size, and system event type.

**Since:** 26.0.1

**Related module:** [HiAppEvent](capi-hiappevent.md)

**File to include:** [hiappevent.h](capi-hiappevent-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| const char* filePath | Path of the fault file. |
| long long generationTs | Timestamp when the fault file is generated. |
| long fileSize | Size of the fault file, in KB. |
| [OH_HiAppEvent_SysEvent](./capi-hiappevent-h.md#oh_hiappevent_sysevent) event | System event type. |
