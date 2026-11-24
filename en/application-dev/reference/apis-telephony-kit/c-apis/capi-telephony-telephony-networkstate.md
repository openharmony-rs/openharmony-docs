# Telephony_NetworkState

```c
typedef struct Telephony_NetworkState {...} Telephony_NetworkState
```

## Overview

Defines network status information.

<!--Device-typedef struct Telephony_NetworkState {...} Telephony_NetworkState--><!--Device-typedef struct Telephony_NetworkState {...} Telephony_NetworkState-End-->

**System capability**: SystemCapability.Telephony.CoreService

**Since**: 13

**Related module**: [Telephony](capi-telephony-kit-telephony.md)

**Header file**: [telephony_radio_type.h](capi-telephony-radio-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char longOperatorName_[TELEPHONY_MAX_OPERATOR_LEN] | Long carrier name of the registered network<br><!--Device-char longOperatorName_[TELEPHONY_MAX_OPERATOR_LEN]--><!--Device-char longOperatorName_[TELEPHONY_MAX_OPERATOR_LEN]-End--> |
| char shortOperatorName_[TELEPHONY_MAX_OPERATOR_LEN] | Short carrier name of the registered network<br><!--Device-char shortOperatorName_[TELEPHONY_MAX_OPERATOR_LEN]--><!--Device-char shortOperatorName_[TELEPHONY_MAX_OPERATOR_LEN]-End--> |
| char plmnNumeric_[TELEPHONY_MAX_PLMN_NUMERIC_LEN] | PLMN code of the registered network<br><!--Device-char plmnNumeric_[TELEPHONY_MAX_PLMN_NUMERIC_LEN]--><!--Device-char plmnNumeric_[TELEPHONY_MAX_PLMN_NUMERIC_LEN]-End--> |
| bool isRoaming_ | Whether in roaming<br><!--Device-bool isRoaming_--><!--Device-bool isRoaming_-End--> |
| [Telephony_RegState](capi-telephony-radio-type-h.md#telephony_regstate) regState_ | Network registration status<br><!--Device-Telephony_RegState regState_--><!--Device-Telephony_RegState regState_-End--> |
| [Telephony_RadioTechnology](capi-telephony-radio-type-h.md#telephony_radiotechnology) cfgTech_ | Radio technology.<br><!--Device-Telephony_RadioTechnology cfgTech_--><!--Device-Telephony_RadioTechnology cfgTech_-End--> |
| [Telephony_NsaState](capi-telephony-radio-type-h.md#telephony_nsastate) nsaState_ | NSA state<br><!--Device-Telephony_NsaState nsaState_--><!--Device-Telephony_NsaState nsaState_-End--> |
| bool isCaActive_ | Whether Carrier Aggregation(CA) is active<br><!--Device-bool isCaActive_--><!--Device-bool isCaActive_-End--> |
| bool isEmergency_ | Whether in emergency call only<br><!--Device-bool isEmergency_--><!--Device-bool isEmergency_-End--> |


