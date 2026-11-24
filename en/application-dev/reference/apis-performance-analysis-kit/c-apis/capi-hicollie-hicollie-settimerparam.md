# HiCollie_SetTimerParam

```c
typedef struct HiCollie_SetTimerParam {...} HiCollie_SetTimerParam
```

## Overview

Defines the input parameters of the **OH_HiCollie_SetTimer** function.

<!--Device-struct HiCollie_SetTimerParam {...}--><!--Device-struct HiCollie_SetTimerParam {...}-End-->

**System capability**: SystemCapability.HiviewDFX.HiCollie

**Since**: 18

**Related module**: [HiCollie](capi-performance-analysis-kit-hicollie.md)

**Header file**: [hicollie.h](capi-hicollie-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char *name | The timer name<br>**Since**: 18<br><!--Device-const char *name--><!--Device-const char *name-End--> |
| unsigned int timeout | Task timeout threshold, in seconds.<br>**Since**: 18<br><!--Device-unsigned int timeout--><!--Device-unsigned int timeout-End--> |
| [OH_HiCollie_Callback](capi-hicollie-h.md#oh_hicollie_callback) func | Callback executed when a timeout occurs.<br>**Since**: 18<br><!--Device-OH_HiCollie_Callback func--><!--Device-OH_HiCollie_Callback func-End--> |
| void *arg | The callback function's parameter.<br>**Since**: 18<br><!--Device-void *arg--><!--Device-void *arg-End--> |
| [HiCollie_Flag](capi-hicollie-h.md#hicollie_flag) flag | Action performed when a timeout occurs. For details, see [HiCollie_Flag](capi-hicollie-h.md#hicollie_flag).<br>**Since**: 18<br><!--Device-HiCollie_Flag flag--><!--Device-HiCollie_Flag flag-End--> |


