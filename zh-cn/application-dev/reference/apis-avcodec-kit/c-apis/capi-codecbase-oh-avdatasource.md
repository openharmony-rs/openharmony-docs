# OH_AVDataSource

```c
typedef struct OH_AVDataSource {...} OH_AVDataSource
```

## 概述

用户自定义数据源。

<!--Device-struct OH_AVDataSource {...}--><!--Device-struct OH_AVDataSource {...}-End-->

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 12

**相关模块：** [CodecBase](capi-avcodec-kit-codecbase.md)

**所在头文件：** [native_avcodec_base.h](capi-native-avcodec-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int64_t size | 数据源的总大小，单位为字节。<br>**起始版本：** 12<br><!--Device-int64_t size--><!--Device-int64_t size-End--> |
| [OH_AVDataSourceReadAt](capi-native-avcodec-base-h.md#oh_avdatasourcereadat) readAt | 数据源的数据读取回调。<br>**起始版本：** 12<br><!--Device-OH_AVDataSourceReadAt readAt--><!--Device-OH_AVDataSourceReadAt readAt-End--> |


