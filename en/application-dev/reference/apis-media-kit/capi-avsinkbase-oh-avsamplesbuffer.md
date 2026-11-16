# OH_AVSamplesBuffer
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @wang-haizhou6-->
<!--Designer: @HmQQQ-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=54832c55a10bd12f43b0e327d20ef90222e0156f translatedAt=2026-11-09T06:27:53.729Z pushedAt=2026-11-09T08:40:35.097Z nl=1 -->

```c
typedef struct OH_AVSamplesBuffer OH_AVSamplesBuffer
```

## Overview

Describes the input data of the **LowPowerAVSink**. After receiving the **DataNeeded** callback, the app must pack data into an **OH_AVSamplesBuffer** instance and pass it to the corresponding **LowPowerAVSink**.

**Since**: 20

**Related module**: [AVSinkBase](capi-avsinkbase.md)

**Header file**: [lowpower_avsink_base.h](capi-lowpower-avsink-base-h.md)

