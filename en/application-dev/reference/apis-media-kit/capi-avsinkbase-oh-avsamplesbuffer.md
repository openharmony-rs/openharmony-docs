# OH_AVSamplesBuffer
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @wang-haizhou6-->
<!--Designer: @HmQQQ-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_AVSamplesBuffer OH_AVSamplesBuffer
```

## Overview

The struct describes the input data of the LowPowerAVSink. After receiving the DataNeeded callback, the application must pack data into an OH_AVSamplesBuffer instance and pass it to the corresponding LowPowerAVSink.

**Since**: 20

**Related module**: [AVSinkBase](capi-avsinkbase.md)

**Header file**: [lowpower_avsink_base.h](capi-lowpower-avsink-base-h.md)
