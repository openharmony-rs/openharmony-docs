# OH_AVDataSourceExt

```c
struct OH_AVDataSourceExt {...}
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
| int64_t size | Size of the data source.<br>**Since**: 20 |
| [OH_AVDataSourceReadAtExt](capi-native-avcodec-base-h.md#oh_avdatasourcereadatext) readAt | Callback of the data source.<br>**Since**: 20 |


