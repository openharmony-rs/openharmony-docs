# Rdb_SubscribeCallback
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=92fad92320c327a07cb31c689545113f874871a6 translatedAt=2026-06-26T06:35:43.342Z pushedAt=2026-06-29T02:15:43.572Z -->

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