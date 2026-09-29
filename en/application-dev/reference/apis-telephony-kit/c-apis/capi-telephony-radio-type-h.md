# telephony_radio_type.h

## Overview

Provides the data structures for the C APIs of the the telephony radio.

**Library**: libtelephony_radio.so

**Since**: 13

**Related module**: [](capi-.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Telephony_NetworkState](capi--telephony-networkstate.md) | Telephony_NetworkState | Defines network status information. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Telephony_RadioResult](#telephony_radioresult) | Telephony_RadioResult | Result codes. |
| [Telephony_RegState](#telephony_regstate) | Telephony_RegState | Network registration status of the device. |
| [Telephony_RadioTechnology](#telephony_radiotechnology) | Telephony_RadioTechnology | RAT type of the device. |
| [Telephony_NsaState](#telephony_nsastate) | Telephony_NsaState | NSA network registration status of the device. |

### Macro

| Name | Description |
| -- | -- |
| TELEPHONY_MAX_OPERATOR_LEN 64 | Max operator name length.<br>**Since**: 13 |
| TELEPHONY_MAX_PLMN_NUMERIC_LEN 6 | Max plmn numeric length.<br>**Since**: 13 |

## Enum type description

### Telephony_RadioResult

```c
enum Telephony_RadioResult
```

**Description**

Result codes.

**Since**: 13

| Enum item | Description |
| -- | -- |
| TEL_RADIO_SUCCESS = 0 | @error success |
| TEL_RADIO_PERMISSION_DENIED = 201 | @error permission denied |
| TEL_RADIO_ERR_INVALID_PARAM = 401 | @error invalid parameter |
| TEL_RADIO_ERR_MARSHALLING_FAILED = 8300001 | @error marshalling failed, this is a low probability error, try again later when get this error |
| TEL_RADIO_ERR_SERVICE_CONNECTION_FAILED = 8300002 | @error unable to connect to telephony service, try again later when get this error |
| TEL_RADIO_ERR_OPERATION_FAILED = 8300003 | @error operation failed in telephony service, try again later when get this error |

### Telephony_RegState

```c
enum Telephony_RegState
```

**Description**

Network registration status of the device.

**Since**: 13

| Enum item | Description |
| -- | -- |
| TEL_REG_STATE_NO_SERVICE = 0 | can not use any services |
| TEL_REG_STATE_IN_SERVICE = 1 | can use services properly |
| TEL_REG_STATE_EMERGENCY_CALL_ONLY = 2 | can use emergency call only |
| TEL_REG_STATE_POWER_OFF = 3 | radio power off |

### Telephony_RadioTechnology

```c
enum Telephony_RadioTechnology
```

**Description**

RAT type of the device.

**Since**: 13

| Enum item | Description |
| -- | -- |
| TEL_RADIO_TECHNOLOGY_UNKNOWN = 0 | Unknown radio technology |
| TEL_RADIO_TECHNOLOGY_GSM = 1 | Global System for Mobile Communication (GSM) |
| TEL_RADIO_TECHNOLOGY_1XRTT = 2 | Single-Carrier Radio Transmission Technology (1XRTT) |
| TEL_RADIO_TECHNOLOGY_WCDMA = 3 | Wideband Code Division Multiple Access (WCDMA) |
| TEL_RADIO_TECHNOLOGY_HSPA = 4 | High Speed Packet Access (HSPA) |
| TEL_RADIO_TECHNOLOGY_HSPAP = 5 | Evolved High Speed Packet Access (HSPA+) |
| TEL_RADIO_TECHNOLOGY_TD_SCDMA = 6 | Time Division-Synchronous Code Division Multiple Access(TD-SCDMA) |
| TEL_RADIO_TECHNOLOGY_EVDO = 7 | Evolution-Data Optimized (EVDO) |
| TEL_RADIO_TECHNOLOGY_EHRPD = 8 | Evolved High Rate Package Data (EHRPD) |
| TEL_RADIO_TECHNOLOGY_LTE = 9 | Long Term Evolution (LTE) |
| TEL_RADIO_TECHNOLOGY_LTE_CA = 10 | Long Term Evolution_Carrier Aggregation (LTE_CA) |
| TEL_RADIO_TECHNOLOGY_IWLAN = 11 | Industrial Wireless LAN (IWLAN) |
| TEL_RADIO_TECHNOLOGY_NR = 12 | New Radio (NR) |

### Telephony_NsaState

```c
enum Telephony_NsaState
```

**Description**

NSA network registration status of the device.

**Since**: 13

| Enum item | Description |
| -- | -- |
| TEL_NSA_STATE_NOT_SUPPORTED = 1 | The device is in idle or connected state in an LTE cell that does not support NSA |
| TEL_NSA_STATE_NO_DETECTED = 2 | The device is in the idle state in an LTE cell that supports NSA but not NR coverage detection |
| TEL_NSA_STATE_CONNECTED_DETECTED = 3 | The device is connected to the LTE network in an LTE cell that supports NSA and NR coverage detection |
| TEL_NSA_STATE_IDLE_DETECTED = 4 | The device is in the idle state in an LTE cell that supports NSA and NR coverage detection |
| TEL_NSA_STATE_DUAL_CONNECTED = 5 | The device is connected to the LTE/NR network in an LTE cell that supports NSA |
| TEL_NSA_STATE_SA_ATTACHED = 6 | The device is idle or connected to the NG-RAN cell when being attached to the 5G Core |


