# ffrt_mutex_t

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung; @yanleo-->
<!--SE: @geoffrey_guo; @huangyouzhong-->
<!--TSE: @lotsof; @sunxuhao-->

## Overview

The **ffrt_mutex_t** struct describes an FFRT mutex.

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

**Header file**: [type_def.h](capi-type-def-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t storage[(ffrt_mutex_storage_size + sizeof(uint32_t) - 1) / sizeof(uint32_t)] | Storage size of a mutex.|
