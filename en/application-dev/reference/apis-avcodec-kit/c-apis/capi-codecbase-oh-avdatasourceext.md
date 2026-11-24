# OH_AVDataSourceExt

```c
typedef struct OH_AVDataSourceExt {...} OH_AVDataSourceExt
```

## Overview

The struct describes a user-defined data source. User-defined data can be passed to its callback functions through the **userData** parameter.

<!--Device-struct OH_AVDataSourceExt {...}--><!--Device-struct OH_AVDataSourceExt {...}-End-->

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 20

**Related module**: [CodecBase](capi-avcodec-kit-codecbase.md)

**Header file**: [native_avcodec_base.h](capi-native-avcodec-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int64_t size | Total size of the data source, in bytes.<br>**Since**: 20<br><!--Device-int64_t size--><!--Device-int64_t size-End--> |
| [OH_AVDataSourceReadAtExt](capi-native-avcodec-base-h.md#oh_avdatasourcereadatext) readAt | Callback for reading data from the data source.<br>**Since**: 20<br><!--Device-OH_AVDataSourceReadAtExt readAt--><!--Device-OH_AVDataSourceReadAtExt readAt-End--> |


