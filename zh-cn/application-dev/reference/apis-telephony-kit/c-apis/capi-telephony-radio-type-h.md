# telephony_radio_type.h

## 概述

Provides the data structures for the C APIs of the the telephony radio.

**库：** libtelephony_radio.so

**系统能力：** SystemCapability.Telephony.CoreService

**起始版本：** 13

**相关模块：** [Telephony](capi-telephony-kit-telephony.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [Telephony_NetworkState](capi-telephony-telephony-networkstate.md) | Telephony_NetworkState | 网络状态信息。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [Telephony_RadioResult](#telephony_radioresult) | Telephony_RadioResult | 错误码类型枚举。 |
| [Telephony_RegState](#telephony_regstate) | Telephony_RegState | 设备的网络注册状态类型。 |
| [Telephony_RadioTechnology](#telephony_radiotechnology) | Telephony_RadioTechnology | 设备的无线接入技术类型。 |
| [Telephony_NsaState](#telephony_nsastate) | Telephony_NsaState | 设备的NSA网络注册状态类型。 |

### 宏定义

| 名称 | 描述 |
| -- | -- |
| TELEPHONY_MAX_OPERATOR_LEN 64 | Max operator name length.<br>**起始版本：** 13 |
| TELEPHONY_MAX_PLMN_NUMERIC_LEN 6 | Max plmn numeric length.<br>**起始版本：** 13 |

## 枚举类型说明

### Telephony_RadioResult

```c
enum Telephony_RadioResult
```

**描述：**

错误码类型枚举。

<!--Device-enum Telephony_RadioResult--><!--Device-enum Telephony_RadioResult-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**起始版本：** 13

| 枚举项 | 描述 |
| -- | -- |
| TEL_RADIO_SUCCESS = 0 | &nbsp;success<br><!--Device-TEL_RADIO_SUCCESS = 0--><!--Device-TEL_RADIO_SUCCESS = 0-End--> |
| TEL_RADIO_PERMISSION_DENIED = 201 | &nbsp;permission denied<br><!--Device-TEL_RADIO_PERMISSION_DENIED = 201--><!--Device-TEL_RADIO_PERMISSION_DENIED = 201-End--> |
| TEL_RADIO_ERR_INVALID_PARAM = 401 | &nbsp;invalid parameter<br><!--Device-TEL_RADIO_ERR_INVALID_PARAM = 401--><!--Device-TEL_RADIO_ERR_INVALID_PARAM = 401-End--> |
| TEL_RADIO_ERR_MARSHALLING_FAILED = 8300001 | &nbsp;marshalling failed, this is a low probability error, try again later when get this error<br><!--Device-TEL_RADIO_ERR_MARSHALLING_FAILED = 8300001--><!--Device-TEL_RADIO_ERR_MARSHALLING_FAILED = 8300001-End--> |
| TEL_RADIO_ERR_SERVICE_CONNECTION_FAILED = 8300002 | &nbsp;unable to connect to telephony service, try again later when get this error<br><!--Device-TEL_RADIO_ERR_SERVICE_CONNECTION_FAILED = 8300002--><!--Device-TEL_RADIO_ERR_SERVICE_CONNECTION_FAILED = 8300002-End--> |
| TEL_RADIO_ERR_OPERATION_FAILED = 8300003 | &nbsp;operation failed in telephony service, try again later when get this error<br><!--Device-TEL_RADIO_ERR_OPERATION_FAILED = 8300003--><!--Device-TEL_RADIO_ERR_OPERATION_FAILED = 8300003-End--> |

### Telephony_RegState

```c
enum Telephony_RegState
```

**描述：**

设备的网络注册状态类型。

<!--Device-enum Telephony_RegState--><!--Device-enum Telephony_RegState-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**起始版本：** 13

| 枚举项 | 描述 |
| -- | -- |
| TEL_REG_STATE_NO_SERVICE = 0 | can not use any services<br><!--Device-TEL_REG_STATE_NO_SERVICE = 0--><!--Device-TEL_REG_STATE_NO_SERVICE = 0-End--> |
| TEL_REG_STATE_IN_SERVICE = 1 | can use services properly<br><!--Device-TEL_REG_STATE_IN_SERVICE = 1--><!--Device-TEL_REG_STATE_IN_SERVICE = 1-End--> |
| TEL_REG_STATE_EMERGENCY_CALL_ONLY = 2 | can use emergency call only<br><!--Device-TEL_REG_STATE_EMERGENCY_CALL_ONLY = 2--><!--Device-TEL_REG_STATE_EMERGENCY_CALL_ONLY = 2-End--> |
| TEL_REG_STATE_POWER_OFF = 3 | radio power off<br><!--Device-TEL_REG_STATE_POWER_OFF = 3--><!--Device-TEL_REG_STATE_POWER_OFF = 3-End--> |

### Telephony_RadioTechnology

```c
enum Telephony_RadioTechnology
```

**描述：**

设备的无线接入技术类型。

<!--Device-enum Telephony_RadioTechnology--><!--Device-enum Telephony_RadioTechnology-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**起始版本：** 13

| 枚举项 | 描述 |
| -- | -- |
| TEL_RADIO_TECHNOLOGY_UNKNOWN = 0 | Unknown radio technology<br><!--Device-TEL_RADIO_TECHNOLOGY_UNKNOWN = 0--><!--Device-TEL_RADIO_TECHNOLOGY_UNKNOWN = 0-End--> |
| TEL_RADIO_TECHNOLOGY_GSM = 1 | Global System for Mobile Communication (GSM)<br><!--Device-TEL_RADIO_TECHNOLOGY_GSM = 1--><!--Device-TEL_RADIO_TECHNOLOGY_GSM = 1-End--> |
| TEL_RADIO_TECHNOLOGY_1XRTT = 2 | Single-Carrier Radio Transmission Technology (1XRTT)<br><!--Device-TEL_RADIO_TECHNOLOGY_1XRTT = 2--><!--Device-TEL_RADIO_TECHNOLOGY_1XRTT = 2-End--> |
| TEL_RADIO_TECHNOLOGY_WCDMA = 3 | Wideband Code Division Multiple Access (WCDMA)<br><!--Device-TEL_RADIO_TECHNOLOGY_WCDMA = 3--><!--Device-TEL_RADIO_TECHNOLOGY_WCDMA = 3-End--> |
| TEL_RADIO_TECHNOLOGY_HSPA = 4 | High Speed Packet Access (HSPA)<br><!--Device-TEL_RADIO_TECHNOLOGY_HSPA = 4--><!--Device-TEL_RADIO_TECHNOLOGY_HSPA = 4-End--> |
| TEL_RADIO_TECHNOLOGY_HSPAP = 5 | Evolved High Speed Packet Access (HSPA+)<br><!--Device-TEL_RADIO_TECHNOLOGY_HSPAP = 5--><!--Device-TEL_RADIO_TECHNOLOGY_HSPAP = 5-End--> |
| TEL_RADIO_TECHNOLOGY_TD_SCDMA = 6 | Time Division-Synchronous Code Division Multiple Access(TD-SCDMA)<br><!--Device-TEL_RADIO_TECHNOLOGY_TD_SCDMA = 6--><!--Device-TEL_RADIO_TECHNOLOGY_TD_SCDMA = 6-End--> |
| TEL_RADIO_TECHNOLOGY_EVDO = 7 | Evolution-Data Optimized (EVDO)<br><!--Device-TEL_RADIO_TECHNOLOGY_EVDO = 7--><!--Device-TEL_RADIO_TECHNOLOGY_EVDO = 7-End--> |
| TEL_RADIO_TECHNOLOGY_EHRPD = 8 | Evolved High Rate Package Data (EHRPD)<br><!--Device-TEL_RADIO_TECHNOLOGY_EHRPD = 8--><!--Device-TEL_RADIO_TECHNOLOGY_EHRPD = 8-End--> |
| TEL_RADIO_TECHNOLOGY_LTE = 9 | Long Term Evolution (LTE)<br><!--Device-TEL_RADIO_TECHNOLOGY_LTE = 9--><!--Device-TEL_RADIO_TECHNOLOGY_LTE = 9-End--> |
| TEL_RADIO_TECHNOLOGY_LTE_CA = 10 | Long Term Evolution_Carrier Aggregation (LTE_CA)<br><!--Device-TEL_RADIO_TECHNOLOGY_LTE_CA = 10--><!--Device-TEL_RADIO_TECHNOLOGY_LTE_CA = 10-End--> |
| TEL_RADIO_TECHNOLOGY_IWLAN = 11 | Industrial Wireless LAN (IWLAN)<br><!--Device-TEL_RADIO_TECHNOLOGY_IWLAN = 11--><!--Device-TEL_RADIO_TECHNOLOGY_IWLAN = 11-End--> |
| TEL_RADIO_TECHNOLOGY_NR = 12 | New Radio (NR)<br><!--Device-TEL_RADIO_TECHNOLOGY_NR = 12--><!--Device-TEL_RADIO_TECHNOLOGY_NR = 12-End--> |

### Telephony_NsaState

```c
enum Telephony_NsaState
```

**描述：**

设备的NSA网络注册状态类型。

<!--Device-enum Telephony_NsaState--><!--Device-enum Telephony_NsaState-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**起始版本：** 13

| 枚举项 | 描述 |
| -- | -- |
| TEL_NSA_STATE_NOT_SUPPORTED = 1 | The device is in idle or connected state in an LTE cell that does not support NSA<br><!--Device-TEL_NSA_STATE_NOT_SUPPORTED = 1--><!--Device-TEL_NSA_STATE_NOT_SUPPORTED = 1-End--> |
| TEL_NSA_STATE_NO_DETECTED = 2 | The device is in the idle state in an LTE cell that supports NSA but not NR coverage detection<br><!--Device-TEL_NSA_STATE_NO_DETECTED = 2--><!--Device-TEL_NSA_STATE_NO_DETECTED = 2-End--> |
| TEL_NSA_STATE_CONNECTED_DETECTED = 3 | The device is connected to the LTE network in an LTE cell that supports NSA and NR coverage detection<br><!--Device-TEL_NSA_STATE_CONNECTED_DETECTED = 3--><!--Device-TEL_NSA_STATE_CONNECTED_DETECTED = 3-End--> |
| TEL_NSA_STATE_IDLE_DETECTED = 4 | The device is in the idle state in an LTE cell that supports NSA and NR coverage detection<br><!--Device-TEL_NSA_STATE_IDLE_DETECTED = 4--><!--Device-TEL_NSA_STATE_IDLE_DETECTED = 4-End--> |
| TEL_NSA_STATE_DUAL_CONNECTED = 5 | The device is connected to the LTE/NR network in an LTE cell that supports NSA<br><!--Device-TEL_NSA_STATE_DUAL_CONNECTED = 5--><!--Device-TEL_NSA_STATE_DUAL_CONNECTED = 5-End--> |
| TEL_NSA_STATE_SA_ATTACHED = 6 | The device is idle or connected to the NG-RAN cell when being attached to the 5G Core<br><!--Device-TEL_NSA_STATE_SA_ATTACHED = 6--><!--Device-TEL_NSA_STATE_SA_ATTACHED = 6-End--> |


