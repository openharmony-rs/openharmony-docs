# Rdb_DistributedConfig
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @widecode; @htt1997-->
<!--Tester: @yippo; @logic42-->
<!--Adviser: @ge-yafang-->

```c
typedef struct Rdb_DistributedConfig {...} Rdb_DistributedConfig
```

## Overview

Defines a struct for distributed configuration of a table.

**Since**: 11

**Related module**: [RDB](capi-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member Variables

| Name           | Description                                         |
| --------------- | --------------------------------------------- |
| int version     | Version of the **Rdb_DistributedConfig** struct.|
| bool isAutoSync | Whether the table supports auto sync. The value **true** indicates that both auto sync and manual sync are supported, and the value **false** indicates that only manual sync is supported.|
