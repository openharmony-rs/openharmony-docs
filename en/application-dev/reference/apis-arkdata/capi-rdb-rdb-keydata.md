# Rdb_KeyData
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=81165a532e10b3d1517ed6f395ac6f3808130ce3 translatedAt=2026-09-15T10:52:10.494Z pushedAt=2026-09-16T07:50:15.683Z -->

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
| const char* text | Data of the string type.     |

