# DisplaySoloist_ExpectedRateRange

```c
typedef struct DisplaySoloist_ExpectedRateRange {...} DisplaySoloist_ExpectedRateRange
```

## Overview

This struct describes the expected frame rate range.

**Since**: 12

**Related module**: [NativeDisplaySoloist](capi-nativedisplaysoloist.md)

**Header file**: [native_display_soloist.h](capi-native-display-soloist-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t min | Minimum value of the expected frame rate range. The value range is [0,120]. |
| int32_t max | Maximum value of the expected frame rate range. The value range is [0,120]. |
| int32_t expected | Expected frame rate. The value range is [0,120]. |


