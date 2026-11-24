# OH_AVDataSource

```c
typedef struct OH_AVDataSource {...} OH_AVDataSource
```

## Overview

The struct describes a user-defined data source.

<!--Device-struct OH_AVDataSource {...}--><!--Device-struct OH_AVDataSource {...}-End-->

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 12

**Related module**: [CodecBase](capi-avcodec-kit-codecbase.md)

**Header file**: [native_avcodec_base.h](capi-native-avcodec-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int64_t size | Total size of the data source, in bytes.<br>**Since**: 12<br><!--Device-int64_t size--><!--Device-int64_t size-End--> |
| [OH_AVDataSourceReadAt](capi-native-avcodec-base-h.md#oh_avdatasourcereadat) readAt | Callback for reading data from the data source.<br>**Since**: 12<br><!--Device-OH_AVDataSourceReadAt readAt--><!--Device-OH_AVDataSourceReadAt readAt-End--> |


