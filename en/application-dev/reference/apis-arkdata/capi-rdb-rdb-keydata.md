# Rdb_KeyData
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=a344fa18476f0d16c0d531be44b7138a04f15161 translatedAt=2026-11-16T01:34:23.719Z pushedAt=2026-11-20T07:27:04.060Z nl=1 -->

```c
union Rdb_KeyData { ... } *data
```

## Overview

Stores the changed data.

**Since**: 11

**Related module**: [RDB](capi-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member Variables

| Name            | Description                    |
| ---------------- | ------------------------ |
| uint64_t integer | Data of the uint64_t type.|
| double real      | Data of the double type.  |
| const char* text | Data of the string type. |

