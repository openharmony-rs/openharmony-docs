# HiCollie_SetTimerParam

```c
struct HiCollie_SetTimerParam {...}
```

## Overview

Defines the input parameters of the **OH_HiCollie_SetTimer** function.

**System capability**: SystemCapability.HiviewDFX.HiCollie

**Since**: 18

**Related module**: [HiCollie](capi-others-hicollie.md)

**Header file**: [hicollie.h](capi-hicollie-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char *name | The timer name<br>**Since**: 18 |
| unsigned int timeout | Task timeout threshold, in seconds.<br>**Since**: 18 |
| [OH_HiCollie_Callback](capi-hicollie-h.md#oh_hicollie_callback) func | Callback executed when a timeout occurs.<br>**Since**: 18 |
| void *arg | The callback function's parameter.<br>**Since**: 18 |
| [HiCollie_Flag](capi-hicollie-h.md#hicollie_flag) flag | Action performed when a timeout occurs. For details, see [HiCollie_Flag](capi-hicollie-h.md#hicollie_flag).<br>**Since**: 18 |


