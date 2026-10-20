# Telephony_NetworkState
<!--Kit: Telephony Kit-->
<!--Subsystem: Telephony-->
<!--Owner: @Terence_Super-->
<!--Designer: @Terence_Super-->
<!--Tester: @jiang_99-->
<!--Adviser: @zhang_yixin13-->

```c
typedef struct {...} Telephony_NetworkState
```

## Overview

Defines network status information. This method can be used to obtain the carrier name, PLMN code, roaming status, network registration status, and radio access technology of the network with which the device is currently registered. It is applicable to scenarios where the current network status needs to be displayed or service logic needs to be determined based on the network status.

**Since**: 13

**Related module**: [Telephony](capi-telephony.md)

**Header file**: [telephony_radio_type.h](capi-telephony-radio-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| char longOperatorName_[TELEPHONY_MAX_OPERATOR_LEN] | Long carrier name of the registered network.|
| char shortOperatorName_[TELEPHONY_MAX_OPERATOR_LEN] | Short carrier name of the registered network.|
| char plmnNumeric_[TELEPHONY_MAX_PLMN_NUMERIC_LEN] | PLMN code of the registered network.|
| bool isRoaming_ | Whether the user is roaming. The value **true** indicates that the user is roaming, and the value **false** indicates that the user is not roaming.|
| Telephony_RegState regState_ | Network registration status of the device.|
| Telephony_RadioTechnology cfgTech_ | RAT of the device.|
| Telephony_NsaState nsaState_ | NSA network registration status of the device.|
| bool isCaActive_ | Whether carrier aggregation (CA) is activated. **true** if CA is activated, and **false** otherwise.|
| bool isEmergency_ | Whether only emergency calls are allowed. The value **true** indicates that only emergency calls are allowed, and the value **false** indicates that all calls are allowed.|
