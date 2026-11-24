# OH_Huks_Result

```c
typedef struct OH_Huks_Result {...} OH_Huks_Result
```

## Overview

Defines the returned data, including a status code and related description.

<!--Device-struct OH_Huks_Result {...}--><!--Device-struct OH_Huks_Result {...}-End-->

**System capability**: SystemCapability.Security.Huks.Core

**Since**: 9

**Related module**: [HuksTypeApi](capi-universal-keystore-kit-hukstypeapi.md)

**Header file**: [native_huks_type.h](capi-native-huks-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t errorCode | Status code. For details, see [OH_Huks_ErrCode](capi-native-huks-type-h.md#oh_huks_errcode).<br><!--Device-int32_t errorCode--><!--Device-int32_t errorCode-End--> |
| const char *errorMsg | Description of the status code.<br><!--Device-const char *errorMsg--><!--Device-const char *errorMsg-End--> |
| uint8_t *data | Other data.<br><!--Device-uint8_t *data--><!--Device-uint8_t *data-End--> |


