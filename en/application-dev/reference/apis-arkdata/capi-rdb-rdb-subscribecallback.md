# Rdb_SubscribeCallback
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=1054d8b030836fe58bcf3a3108bf6f34b102d289 translatedAt=2026-09-15T10:54:36.556Z pushedAt=2026-09-16T07:50:15.690Z -->

```c
typedef union Rdb_SubscribeCallback {...} Rdb_SubscribeCallback
```

## Overview

Defines a callback used to return the subscribed event.

**Since**: 11

**Related module**: [RDB](capi-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member Variables

| Name                                                        | Description                              |
| ------------------------------------------------------------ | ---------------------------------- |
| [Rdb_DetailsObserver](capi-relational-store-h.md#rdb_detailsobserver) detailsObserver | Callback used to return the details about the device-cloud data change.|
| [Rdb_BriefObserver](capi-relational-store-h.md#rdb_briefobserver) briefObserver | Callback used to return the device-cloud data change event.      |

