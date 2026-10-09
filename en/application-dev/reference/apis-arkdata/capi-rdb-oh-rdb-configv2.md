# OH_Rdb_ConfigV2
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=92fad92320c327a07cb31c689545113f874871a6 translatedAt=2026-06-26T06:34:49.080Z pushedAt=2026-06-29T02:15:43.553Z -->

```c
typedef struct OH_Rdb_ConfigV2 OH_Rdb_ConfigV2
```

## Overview

Defines a struct for the RDB store configuration. Different from [OH_Rdb_Config](capi-rdb-oh-rdb-config.md), this struct does not expose its member variables externally. Methods are used to configure the properties of this struct. It supports vector stores.

**Since**: 14

**Related module**: [RDB](capi-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)