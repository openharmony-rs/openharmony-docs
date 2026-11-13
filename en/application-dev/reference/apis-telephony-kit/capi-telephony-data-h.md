# telephony_data.h

<!--Kit: Telephony Kit-->
<!--Subsystem: Telephony-->
<!--Owner: @k_lee9575-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=e0f5681a2ac907ad9e838f9af462e381b55646ee translatedAt=2026-11-03T03:42:43.438Z pushedAt=2026-11-03T08:14:19.107Z nl=1 -->

## Overview

Defines C APIs for cellular data module.

**File to include**: <telephony/cellular_data/telephony_data.h>

**Library**: libtelephony_data.so

**System capability**: SystemCapability.Telephony.CellularData

**Since**: 13

**Related module**: [Telephony](capi-telephony.md)


## Summary

### Functions

| Name| Description|
| -- | -- |
| [int32_t OH_Telephony_GetDefaultCellularDataSlotId(void)](#oh_telephony_getdefaultcellulardataslotid) | Obtains the default SIM card used for mobile data.|

## Function Description

### OH_Telephony_GetDefaultCellularDataSlotId()

```c
int32_t OH_Telephony_GetDefaultCellularDataSlotId(void)
```

**Description**

Obtains the default SIM card used for mobile data.

**System capability**: SystemCapability.Telephony.CellularData

**Since**: 13

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Default cellular data slot (**0** indicates slot 1, and **1** indicates slot 2). |


