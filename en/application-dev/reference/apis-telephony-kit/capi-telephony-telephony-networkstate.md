# Telephony_NetworkState
<!--Kit: Telephony Kit-->
<!--Subsystem: Telephony-->
<!--Owner: @Terence_Super-->
<!--Designer: @Terence_Super-->
<!--Tester: @jiang_99-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=c5fbe5a461143268927de8d2f2a9feadfc68a0f1 translatedAt=2026-11-03T03:43:45.416Z pushedAt=2026-11-03T08:25:59.942Z nl=1 -->

```c
typedef struct {...} Telephony_NetworkState
```

## Overview

Describes the network status information. This method can be used to obtain the carrier name, PLMN code, roaming status, network registration status, and radio access technology of the registered network of the device. It applies to scenarios where the current network status needs to be displayed or where service logic decisions need to be made based on the network status.

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
| bool isRoaming_ | Whether the device is in roaming status. The value **true** indicates that the device is in roaming status, and **false** indicates the opposite. |
| Telephony_RegState regState_ | Network registration status of the device.|
| Telephony_RadioTechnology cfgTech_ | RAT of the device.|
| Telephony_NsaState nsaState_ | NSA network registration status of the device.|
| bool isCaActive_ | Whether Carrier Aggregation (CA) is active. The value **true** indicates that CA is active, and **false** indicates that CA is inactive. |
| bool isEmergency_ | Whether this device is allowed to make emergency calls only. The value **true** indicates that only emergency calls are allowed, and **false** indicates that all calls are allowed. |


