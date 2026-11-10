# OH_AVSamplesBuffer
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @wang-haizhou6-->
<!--Designer: @HmQQQ-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=d13f78fa774ee685b08ad91f89f8e048b9fe11b4 translatedAt=2026-11-10T08:38:49.621Z pushedAt=2026-11-10T10:46:08.043Z nl=1 -->

```c
typedef struct OH_AVSamplesBuffer OH_AVSamplesBuffer
```

## Overview

Describes the input data of the LowPowerAVSink. After receiving the **DataNeeded** callback, the app must pack data into an **OH_AVSamplesBuffer** instance and pass it to the corresponding LowPowerAVSink.

**Since**: 20

**Related module**: [AVSinkBase](capi-avsinkbase.md)

**Header file**: [lowpower_avsink_base.h](capi-lowpower-avsink-base-h.md)

