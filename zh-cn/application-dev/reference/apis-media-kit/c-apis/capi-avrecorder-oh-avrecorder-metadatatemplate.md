# OH_AVRecorder_MetadataTemplate

```c
typedef struct OH_AVRecorder_MetadataTemplate {...} OH_AVRecorder_MetadataTemplate
```

## 概述

定义音视频录制过程中元数据的基本模板，通过键值对（key-value）形式组织元数据，适用于需要在录制输出中附加自定义元数据（如标题、作者、描述等）的场景，便于对录制文件进行分类、检索和管理。开发者可通过AVRecorder的{@link OH_AVRecorder_Prepare}接口将该结构体中的元数据设置到录制输出文件中。

**起始版本：** 18

**相关模块：** [AVRecorder](capi-avrecorder.md)

**所在头文件：** [avrecorder_base.h](capi-avrecorder-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char *key | 元数据的键。 |
| char *value | 元数据的值。 |


