# Rdb_ProgressDetails

```c
typedef struct Rdb_ProgressDetails {...} Rdb_ProgressDetails
```

## 概述

描述数据库整体执行端云同步任务上传和下载的统计信息。

<!--Device-struct Rdb_ProgressDetails {...}--><!--Device-struct Rdb_ProgressDetails {...}-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**起始版本：** 11

**相关模块：** [RDB](capi-arkdata-rdb.md)

**所在头文件：** [relational_store.h](capi-relational-store-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int version | 表示Rdb_ProgressDetails结构体的版本。<br><!--Device-int version--><!--Device-int version-End--> |
| int schedule | 表示端云同步过程。<br><!--Device-int schedule--><!--Device-int schedule-End--> |
| int code | 表示端云同步过程的状态。<br><!--Device-int code--><!--Device-int code-End--> |
| int32_t tableLength | 表示端云同步的表的数量。<br><!--Device-int32_t tableLength--><!--Device-int32_t tableLength-End--> |


