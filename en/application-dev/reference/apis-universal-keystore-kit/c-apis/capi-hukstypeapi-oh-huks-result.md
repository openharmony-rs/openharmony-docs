# OH_Huks_Result

```c
typedef struct OH_Huks_Result {...} OH_Huks_Result
```

## Overview

Defines the returned data, including a status code and related description.

**Since**: 9

**Related module**: [HuksTypeApi](capi-hukstypeapi.md)

**Header file**: [native_huks_type.h](capi-native-huks-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t errorCode | Status code. For details, see [OH_Huks_ErrCode](capi-native-huks-type-h.md#oh_huks_errcode). |
| const char *errorMsg | Description of the status code. |
| uint8_t *data | Other data. |


