# Rdb_KeyData
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=92fad92320c327a07cb31c689545113f874871a6 translatedAt=2026-06-26T06:35:26.655Z pushedAt=2026-06-29T02:15:43.566Z -->

```c
union Rdb_KeyData { ... }
```

## Overview

Stores the changed data.

**Related module**: [RDB](capi-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member Variables

| Name            | Description                    |
| ---------------- | ------------------------ |
| uint64_t integer | Data of the uint64_t type.|
| double real      | Data of the double type.  |
| const char* text | Data of the char\* type.    |