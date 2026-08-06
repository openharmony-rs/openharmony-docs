# OH_AVRecorder_Metadata

```c
typedef struct OH_AVRecorder_Metadata {...} OH_AVRecorder_Metadata
```

## 概述

元数据信息数据结构。

**起始版本：** 18

**相关模块：** [AVRecorder](capi-avrecorder.md)

**所在头文件：** [avrecorder_base.h](capi-avrecorder-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char *genre | The metadata to retrieve the content type or genre of the data source |
| char *videoOrientation | The metadata to retrieve the information about the video orientation |
| [OH_AVRecorder_Location](capi-avrecorder-oh-avrecorder-location.md) location | The geographical location info of the video |
| [OH_AVRecorder_MetadataTemplate](capi-avrecorder-oh-avrecorder-metadatatemplate.md) customInfo | Custom parameter key-value map read from moov.meta.list |


