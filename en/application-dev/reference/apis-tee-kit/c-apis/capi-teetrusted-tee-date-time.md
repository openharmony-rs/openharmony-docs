# TEE_Date_Time

```c
typedef struct TEE_Date_Time {...} TEE_Date_Time
```

## Overview

Definitions the date time of TEE.

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

**Header file**: [tee_defines.h](capi-tee-defines-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t seconds | Seconds part of the date time. |
| int32_t millis | Milliseconds part of the date time. |
| int32_t min | Minutes part of the date time. |
| int32_t hour | Hours part of the date time. |
| int32_t day | Day part of the date time. |
| int32_t month | Month part of the date time. |
| int32_t year | Year part of the date time. |


