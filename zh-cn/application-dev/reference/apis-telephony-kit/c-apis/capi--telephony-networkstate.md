# Telephony_NetworkState

## 概述

网络状态信息。

**起始版本：** 13

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char longOperatorName_[TELEPHONY_MAX_OPERATOR_LEN] | Long carrier name of the registered network |
| char shortOperatorName_[TELEPHONY_MAX_OPERATOR_LEN] | Short carrier name of the registered network |
| char plmnNumeric_[TELEPHONY_MAX_PLMN_NUMERIC_LEN] | PLMN code of the registered network |
| bool isRoaming_ | Whether in roaming |
| [Telephony_RegState](capi-telephony-radio-type-h.md#telephony_regstate) regState_ | Network registration status |
| [Telephony_RadioTechnology](capi-telephony-radio-type-h.md#telephony_radiotechnology) cfgTech_ | Radio technology. |
| [Telephony_NsaState](capi-telephony-radio-type-h.md#telephony_nsastate) nsaState_ | NSA state |
| bool isCaActive_ | Whether Carrier Aggregation(CA) is active |
| bool isEmergency_ | Whether in emergency call only |


