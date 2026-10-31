# Rdb_KeyData
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=4b1c0990e7305766fe10024f567b18e463a94205 translatedAt=2026-09-04T03:04:18.806Z pushedAt=2026-09-09T09:11:03.678Z -->

```c
union Rdb_KeyData { ... }
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

