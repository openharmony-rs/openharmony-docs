# Hid_RelAxesArray
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=a30d46aa87725f954a8669c5a6106a0f5fa2de6d translatedAt=2026-06-22T10:48:11.329Z pushedAt=2026-06-22T11:21:11.386Z -->

```c
typedef struct Hid_RelAxesArray {...} Hid_RelAxesArray
```

## Overview

Defines an array of relative coordinates.

**Since**: 11

**Related module**: [HidDdk](capi-hidddk.md)

**Header file:** [hid_ddk_types.h](capi-hid-ddk-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| Hid_RelAxes* hidRelAxes | Array of relative coordinates.|
| uint16_t length | Valid length of an array.|