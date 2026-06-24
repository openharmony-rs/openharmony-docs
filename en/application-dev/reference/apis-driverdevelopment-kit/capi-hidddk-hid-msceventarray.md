# Hid_MscEventArray
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=a30d46aa87725f954a8669c5a6106a0f5fa2de6d translatedAt=2026-06-22T10:48:12.944Z pushedAt=2026-06-22T11:21:11.391Z -->

```c
typedef struct Hid_MscEventArray {...} Hid_MscEventArray
```

## Overview

Defines an array of miscellaneous events.

**Since**: 11

**Related module**: [HidDdk](capi-hidddk.md)

**Header file:** [hid_ddk_types.h](capi-hid-ddk-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| Hid_MscEvent* hidMscEvent | Miscellaneous event.|
| uint16_t length | Valid length of an array.|